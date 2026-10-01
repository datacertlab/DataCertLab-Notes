# Domain 2 — Secure and govern Unity Catalog objects

Microsoft publishes this skill area at 15–20% of the exam, the same band as domain 1. What makes it
harder than its weight suggests is that several of its controls overlap. The questions rarely ask
what a control does; they describe a requirement and ask which control fits it.

## What this domain actually asks

Two halves, and the guide separates them cleanly.

**Securing** is about who may reach the data. Privileges granted to a principal, access controlled
down to individual rows and columns, and the identities that jobs and services run as.

**Governing** is about what the organisation can see and enforce around that data. Descriptions
that make objects findable, tags and policies that classify and protect at scale, lineage, audit
logs, retention, and sharing with people outside the organisation.

The overlap is the difficulty. Row-level protection can be done on one table directly or through a
policy that follows a tag across thousands. Comments can be written by hand or generated. Audit
data reaches you through two surfaces that do not cover the same events. In each case both options
are real and one fits the requirement better, so read for the condition that separates them.

## Who can grant what

A privilege on a Unity Catalog object can be granted by the object's owner — and also by the owner
of the catalog or schema that **contains** it. Containment carries authority downward, which is
consistent with privileges themselves being inherited downward. Account admins can additionally
grant privileges directly on a metastore.

That is worth pausing on, because a plausible-sounding tightening is wrong: it is not true that
only the direct owner can grant.

Three admin roles exist and the exam moves them around freely.

| Role | Scope | Owns |
|---|---|---|
| Account admin | The whole account | Metastores, workspaces, admin roles |
| Workspace admin | One workspace | Membership, jobs, workspace objects |
| Metastore admin | One metastore | Data access, ownership, top-level securables |

The metastore admin is **optional**, and it is the data governance role. A candidate who assumes
the workspace admin governs data will misread a whole category of question.

Privileges are managed from four surfaces: SQL commands, the command-line interface, the Terraform
provider, and Catalog Explorer. In a `GRANT` statement the securable name is omitted when the type
is `METASTORE`, because it is assumed to be the metastore attached to the workspace.

Two privileges behave in ways worth knowing precisely.

`MANAGE` is a visibility privilege as well as a powerful one: a user holding it can view all grants
on an object, through SQL or Catalog Explorer. And `BROWSE` is the discovery privilege — a user
holding it can discover and view metadata **without** holding usage privileges such as
`USE CATALOG` or `USE SCHEMA`. That deliberate bypass is what makes catalog-wide discoverability
possible without granting anyone access to data.

Finally, `APPLY TAG` on a table or view also enables column-level tagging, and on a registered
model it enables version-level tagging. One privilege, two granularities — and it is the bridge
into the governance half of this domain.

| Privilege | What it is really for |
|---|---|
| `MANAGE` | Control, and seeing every grant on the object |
| `BROWSE` | Discovery without any usage privilege |
| `APPLY TAG` | Classification, at object and column level |
| `MODIFY` | Changing contents, including most comments |

A service credential is worth separating from a storage credential, because the names are close
enough to swap under time pressure. A service credential lets a user reach external services and is
governed by its own privilege; a storage credential is what stands behind access to cloud storage,
and you will meet it again when managed identities come up.

<details>
<summary><b>Self-check — the privilege model</b></summary>

A user needs to find out which tables exist in a catalog, but must not be able to read any of them.
Which privilege, and what makes it unusual?

`BROWSE`. It is unusual because it bypasses the usage chain — the user does not need `USE CATALOG`
or `USE SCHEMA` to discover and view metadata.
</details>

## Protecting rows and columns, one table at a time

The guide's wording for this sub-bullet is "table- and column-level access control and
**row-level security**", and it is worth keeping those three phrases distinct. Table-level access
control is the ordinary grant: you either have a privilege on the table or you do not. Column-level
access control hides or transforms particular columns. Row-level security restricts *which rows* a
given user sees. The first is the privilege model from the previous section; the second and third
are what row filters and column masks implement.

Before the mechanics, get the shape right, because it decides which limitation applies to what.
Unity Catalog has **three** mechanisms for row- and column-level control, not one.

| Mechanism | What it applies to | How it is managed |
|---|---|---|
| Table-level row filters and column masks | Individual tables and columns | `ALTER TABLE`, by the owner or `MANAGE` |
| ABAC policies | Tables and columns matched by tag conditions | `CREATE POLICY`, attached to a catalog, schema or table |
| Dynamic views | A view built from one or more base tables | SQL logic in the view definition |

This section is the first of the three. Row filters and column masks attach to a table and restrict
what a querying user sees. A row filter is a function the platform applies to every query against
the table, returning only the rows that function admits. A column mask transforms a column's value
on the way out — showing the last four digits of an identifier, say, rather than the whole thing.
Learn the limitations before the mechanics, because the limitations are what the exam asks about.

**Table-level filters and masks cannot be applied to a view.** Note which of the three that limit
belongs to: it is a property of this mechanism, not of row-level security in general. The answer for
protecting something exposed as a view is a **dynamic view** — a SQL view that filters rows, masks
columns or reshapes data, usually gated by `is_account_group_member()`. Its particular strength is
exposing a curated version of data to users who have no access to the underlying tables at all.
Candidates who treat a view as just another table walk into the limitation; candidates who know only
the limitation are stuck at it.

**Old runtimes fail securely.** Databricks Runtime versions below 12.2, which carries long-term
support (LTS), do not support row filters or column masks. Accessing such a table from those
runtimes returns *no data at all*. The symptom is an empty result — not an error, and not
unfiltered rows. That is exactly the confusing signal a troubleshooting question describes, and it
connects this domain back to the runtime version you chose in domain 1.

That 12.2 figure belongs to this mechanism alone. ABAC policies have their own, much higher floor —
covered below — and the two numbers are the single most mixable pair in the domain. Read which
mechanism a stem names before you reach for a version.

**Two access paths are closed.** Tables carrying row filters or column masks cannot be reached
through the Iceberg REST catalog or the Unity REST APIs. That is a real limit on the
interoperability managed tables otherwise offer.

Two pieces of guidance shape how you write them. Each distinct column mask is evaluated during
queries, so masks are applied only to genuinely sensitive columns and masking functions are reused
where possible. And SQL user-defined functions are preferred to Python ones, because Python is less
performant and offers fewer optimisation opportunities — a preference, not a prohibition.

> **Trap.** "Fail securely" is a specific behaviour, not a general reassurance. On an unsupported
> runtime the query succeeds and returns nothing. If a stem describes a user seeing an empty table
> they believe has data, check the runtime before you check the grants.

<details>
<summary><b>Self-check — table-level protection</b></summary>

A team reports that a table looks empty to one analyst and populated to another, with identical
grants. What is worth checking first?

The runtime each is using. Below 12.2 LTS, row filters and column masks are unsupported and the
table returns no data rather than erroring.
</details>

## Rules that follow the tag

Attribute-based access control (ABAC) determines access by evaluating **attributes** on securable
objects. Those attributes are carried as governed tags and used in **policy conditions** — which is
exactly the guide's phrasing, "by using tags and policies".

The structural fact that makes this scale: **governed tags are defined at the account level.** One
tag taxonomy covers an entire data estate, across multiple metastores. That is a level above where
the objects themselves live. A metastore is associated with a region, and a catalog belongs to one
metastore. A single tag vocabulary, and the policies written against it, can therefore apply
consistently across a broader estate than any one metastore contains.

A policy's conditions are tag-based expressions deciding which tables or columns it targets. A policy
is attached at a catalog, a schema or a table, and Databricks recommends the highest applicable level
— usually the catalog — to maximise governance efficiency. The payoff is coverage you do not have to
maintain: a new table tagged appropriately is protected without anyone editing a policy. Its reach is
wider than the table-level mechanism in a second way too. For row filter and column mask policies the
supported securable type is *tables* — and that includes streaming tables and materialized views, not
just ordinary tables. Read "tables" as the category rather than the narrow object.

**ABAC has its own compute requirement, and it is the other half of the 12.2 pair above.** Policies
need serverless compute, standard compute on Databricks Runtime 16.4 or above, or dedicated compute
on 16.4 or above with fine-grained access control filtering enabled. Below 16.4, standard and
dedicated compute cannot access an ABAC-secured table at all. The documented way to keep an old
workload running is not to weaken the policy but to scope it to a group and exclude that principal
with `EXCEPT` — the same exemption route described below, used for a different reason.

One more boundary, and it is the cleanest distractor generator in the section: **a row filter or
column mask policy does not grant anything.** A user must already hold `SELECT` on the table through
a direct grant. The policy only filters or masks what they could already reach. So an option that
offers an ABAC policy as the way to *give* a group access to data is wrong. `GRANT` policies are the
exception, and that is precisely why they are named separately.

Attribute-based access control is not only about hiding data. It supports row filter policies and
column mask policies, and also **dynamic privilege grants** through `GRANT` policies. A fourth type,
`DENY`, is in Beta and currently reaches one privilege only — worth recognising for one reason, which
is that a `DENY` beats *every* grant of the same privilege, including one held through ownership.

An `EXCEPT` clause is the exemption route for an administrator or a pipeline, and the documented list
of what it unblocks is longer than it first looks: time travel, cloning, OpenSharing and full query
optimisation. Note the third of those, because it is the hinge between this domain's two halves — a
table under an ABAC policy can be shared at all only if the share owner sits in the `EXCEPT` clause.

Tags come in two families, and the second has a predefined variety inside it. Microsoft names three
jobs for the governed kind, and they are worth holding because a stem usually describes one of them
rather than naming the feature: enforcing standardised tagging for **sensitive data**, for
**regulatory compliance**, and for **business domains**.

| Tag kind | Who sets the values | Who can assign |
|---|---|---|
| Free-form | Anyone with the privilege | Anyone with the privilege |
| Governed | The tag policy | Named users and groups only |
| System | Azure Databricks, fixed | Permissioned like any governed tag |

System tags are a *special type of governed tag* rather than a third independent kind. What is fixed
is the definition: you cannot modify or delete a system tag's keys or values. Who may assign and
unassign them is yours to control, through the same governed-tag permission settings. Do not read
"predefined" as "untouchable".

> **Trap.** A **tag policy** and an **ABAC policy** are different objects, and the naming invites
> the confusion. A tag policy belongs to a governed tag and enforces that tag's rules — which
> values are allowed, and who may assign it. An ABAC policy uses those tags in its conditions to
> decide who sees what. One governs vocabulary, the other governs access. Swap them and every
> attribute-based question becomes unanswerable.

A second boundary is just as sharp. **Tag inheritance is implicit when evaluating ABAC policies
only** — it does not apply generally. Privileges inherit downward as a rule of the model; tags do
not. The two sit side by side and look alike, which is precisely why this gets stated wrong.

And inside policy evaluation, inheritance has one exception that decides whether a policy works at
all: **column tags do not inherit from the parent table.** Tag a catalog and its schemas and tables
inherit; tag a table and its columns do not. A column mask policy matching on a column tag needs that
tag applied to the column directly, so an author who tagged the table and expected the sensitive
column to be masked has built a policy that quietly does nothing.

Tagging is therefore a permission worth getting right, because **tagging is a security boundary** — a
user who can change tags can change which policies apply. Adding a tag needs ownership of the object,
or all three of `APPLY TAG` on it, `USE SCHEMA` on its schema and `USE CATALOG` on its catalog. A
*governed* tag needs one more: the `ASSIGN` permission on the tag itself. A scenario in which someone
holds `APPLY TAG` and still cannot apply the classification is not describing a bug.

There is a ceiling: a maximum of 1,000 governed tags per account.

Now the comparison the exam actually tests.

| Reach for a policy when | Reach for a table-level rule when |
|---|---|
| Rules must be consistent across many tables | Logic is specific and does not generalise |
| Policy authors and data stewards are separate roles | Table owners manage their own rules |
| New tables should be covered automatically once tagged | The set of tables is small and stable |
| Named principals need an `EXCEPT` exemption | No central tag system exists |

<details>
<summary><b>Self-check — which control</b></summary>

A growing estate must ensure that any table with a column tagged as personal data is masked, without
anyone editing a rule each time a table is added. Which control, and why?

An attribute-based access control column mask policy. Coverage follows the tag, so newly tagged
tables are protected automatically — table-level masks would each have to be written by hand.

The same team runs one nightly job on classic compute at Databricks Runtime 15.4 LTS. What breaks,
and what is the documented fix?

The job. Below 16.4, standard and dedicated compute cannot access an ABAC-secured table. The fix is
not to drop the policy but to scope it to a group and exclude the job's principal with `EXCEPT` while
the runtime is upgraded. Note that 15.4 is comfortably above the 12.2 LTS floor for *table-level*
filters — which is exactly why the two numbers have to stay attached to their own mechanisms.
</details>

## Who is acting

The objective splits identity deliberately: service principals authenticate **data** access,
managed identities authenticate **resource** access.

A service principal is either an Azure Databricks managed service principal or a Microsoft Entra ID
managed one. Its creator automatically becomes its manager, which is the same creator-owns-it rule
you met on compute and on catalog objects in domain 1. Account admins and workspace admins can add
service principals through the account console or workspace admin settings.

How those identities arrive is worth one paragraph, because it changed recently. **Automatic
identity management** adds users, service principals and groups from Microsoft Entra ID into Azure
Databricks, with Entra ID as the source of record, so a change to a group's membership is respected
here rather than needing to be copied across. It is on by default for accounts created after
1 August 2025. When it is enabled, everything syncs from the identity provider and **System for
Cross-domain Identity Management (SCIM) provisioning is not necessary** — Databricks recommends the automatic route. The sharpest difference
between the two, and the one most likely to decide a question: SCIM provisioning does not support
syncing service principals, and automatic identity management does.

The role that matters most is **Service Principal User**. It lets workspace users run jobs *as* the
service principal, so the job runs with the service principal's identity rather than the job
owner's. That identity substitution is the whole mechanism behind the rule that production jobs run
as service principals — it is what stops a departing employee's permissions from deciding whether
production keeps working.

> **Trap.** Azure Databricks service principal roles **do not overlap** with Azure roles or
> Microsoft Entra ID roles. They span only the Azure Databricks account. Granting someone an Azure
> role does not confer the matching rights inside Azure Databricks, and this is the most frequently
> crossed boundary in the Azure half of this exam.

**Managed identities** connect to storage on behalf of Unity Catalog users — to the metastore's
managed storage accounts, and to other external storage accounts for file access or external
tables. The reason to choose one is stated plainly: managed identities do not require credentials
to be maintained or secrets to be rotated. If a requirement names credential rotation as a burden,
it is pointing here.

There is a second, sharper reason, and it is the one to reach for when rotation is not mentioned. A
storage credential can hold *either* a managed identity or a service principal — so the split above
is about which identity a scenario is reasoning about, not a product restriction. Within that
storage-credential case, the documented difference is reach: a managed identity lets Unity Catalog
access storage accounts protected by network rules, and a service-principal-based storage credential
does not. Read it as a statement about this credential path rather than about every Azure
authentication route. A stem naming a storage firewall has still settled the question without using
the word "credential".

Setting that up crosses into Azure. The documented route runs through an access connector for Azure
Databricks, and its three prerequisites sit on three different resources — and, more usefully, belong
to three different *steps*.

| Step | Prerequisite | Where it applies |
|---|---|---|
| Register the credential in Unity Catalog | `CREATE STORAGE CREDENTIAL` | The metastore |
| Create the access connector | Contributor or Owner | The Azure resource group |
| Grant the identity access to storage | Owner or User Access Administrator | The storage account |

Account admins and metastore admins hold the first by default — the workspace admin does not. That
asymmetry is easy to miss and it decides questions: a scenario in which a workspace admin cannot
complete a storage setup is not describing a bug.

Notice the shape of the whole arrangement. Two of the three prerequisites live in Azure rather than
in Azure Databricks, on two different Azure resources, and each has its own role name. A question
can turn on which one is missing, so read a failing-setup scenario for *where* the permission gap
is before deciding what it is.
Granting read and write access across a storage account is done with the Storage Blob Data
Contributor role, which is narrower than the general Contributor role and is the one candidates
guess wrong. One more practical note: the storage account should sit in the same region as the
workspace using it, to avoid egress charges.

<details>
<summary><b>Self-check — identities</b></summary>

A nightly job writes to a production table. The team wants it to keep running when its author
leaves, and wants no secret to rotate. What two things are they describing?

A service principal running the job, granted through the Service Principal User role so the job
runs under that identity — and a managed identity for the storage access, since it needs no
credential maintenance.
</details>

## Secrets, and reaching Key Vault

A secret scope is a named collection of secrets. Databricks recommends aligning scopes to roles or
applications rather than to individuals — the same shape as the groups-not-users rule elsewhere in
the platform.

There are two kinds. A **Databricks-backed** scope stores its secrets in an encrypted database that
Azure Databricks owns and manages. An **Azure Key Vault-backed** scope is the one this objective
names, and it is a **read-only interface** to the vault. You create and rotate the secret in Azure;
Databricks only reads it. Creating the scope requires the Key Vault Contributor, Contributor or
Owner role on the key vault instance, which is an Azure-side prerequisite rather than a Databricks
one.

**Check the permission model before the role.** Azure Key Vault-backed secret scopes support the
**Vault access policy** model only, and Azure role-based access control (RBAC) is not supported. A vault on
Azure RBAC has to switch models first. That ordering matters in a stem: if the vault is on RBAC, the
Contributor-versus-Owner argument is not the obstacle, and an option that resolves it is the wrong
answer to a question about why scope creation failed.

Reading is the half the objective actually names, and it is one line in a notebook: the Secrets
utility, `dbutils.secrets.get(scope = "...", key = "...")`. Values read that way are redacted on display and appear as `[REDACTED]`, and the same happens to a
secret referenced in a Spark configuration property. Read redaction as a guard against accidental
printing, not as access control. It covers literal values only, and workspace admins, the scope's
creator and anyone granted permission can read the secret regardless.

> **Trap.** Secret scope *names* are treated as non-sensitive and are readable by every user in the
> workspace. Only the contents are protected. Do not put anything revealing in a scope name.

## Making data findable

Descriptions are a governance act, not decoration. Once a comment is added to a securable object,
any user holding `BROWSE` can view it — which is what turns a comment into discoverability across
the catalog, and why the two features belong in the same thought.

Three details carry real weight.

**Ownership beats `MANAGE` on views.** Adding or editing a comment on a view or materialized view
requires being the **owner**, and the documentation says outright that `MANAGE` is insufficient.
Everywhere else `MANAGE` is the powerful privilege, which is exactly what makes this inversion
examinable. The table below carries the rest — and read it as the bar for a comment you write by
hand, because the generated surface further down has a different one.

**Saving a comment triggers an `ALTER` statement**, which can disrupt pipelines and jobs. A
governance action with an operational side effect is unusual, and it is why bulk-commenting a
production catalog gets scheduled rather than done casually. It is also a good illustration of why
this domain is not simply a list of features: the right answer to "how should we document this
catalog" depends on when, not only on how.

| Object family | What commenting by hand requires |
|---|---|
| Catalogs, schemas, volumes, models, shares, credentials | Ownership or `MANAGE` |
| Tables and columns | Ownership, or `MODIFY` and `SELECT` plus both `USE` privileges |
| Views and materialized views | Ownership only — `MANAGE` is not enough |

Read the three rows as three different rules rather than one with an exception. Most top-level
securables take owner-or-`MANAGE`. Tables and columns are the outlier in the other direction. There
`MANAGE` is not what is asked for at all, but `MODIFY` *and* `SELECT`, plus `USE CATALOG` and
`USE SCHEMA` on the parents. A commenter needs to be able to read the table they are describing.

**Generated comments have their own surface, and their own privilege bar.** AI-generated comments
give a quick way to help users discover data managed by Unity Catalog, and Catalog Explorer must be
used to view suggested comments, edit them and add them. That is a surface constraint rather than a
privilege one: this particular task has no SQL path.

The bar moves with the surface, which is the part worth carrying into the exam. For most objects —
catalogs, schemas, tables, functions, models and volumes — an AI-generated comment needs ownership
or `MODIFY`. Views and materialized views still need ownership. So the same catalog takes `MANAGE`
by hand and `MODIFY` through the generated surface, and the two rules are published on two different
pages. Read the verb in the stem. "Runs `COMMENT ON`" and "clicks **AI generate**" are not the same
question, and the privilege that answers one is a distractor in the other.

## Lineage: where data came from and where it went

**Data lineage** shows where data came from and where it goes: which queries and files populate a
table, which jobs and notebooks transform it, and which dashboards consume the results. The breadth
is wider than most candidates assume, and it extends to user-defined functions as well as tables.

Data lineage is what turns a governance question from an opinion into an answer. "Can we drop this
column?" is unanswerable by inspection and trivial once you can see what depends on it. That is
also why the objective pairs lineage with owner, history and dependencies — together they describe
an object well enough to make a decision about it.

The guide names owner, history, dependencies and lineage, viewed through Catalog Explorer. Three
uses map onto the shapes a question takes.

| Use | The question it answers |
|---|---|
| Impact analysis | What breaks if I change or delete this |
| Root cause investigation | Where did this wrong number come from |
| Sensitive data flow | Where does regulated data originate and end up |

One prerequisite decides several questions: **tables must be registered in a Unity Catalog
metastore** for lineage to track them. Registration has two forms, though, and knowing only the first
will cost you a mark. Assets that live outside the metastore — a Salesforce source upstream, a
Power BI report downstream — are brought into the same graph by registering them as *external
metadata* objects with relationships to your registered securables. So the rule is that lineage needs
registration, not that lineage stops at the platform boundary.

Retention is the third place in this domain where the answer depends on which surface you are
reading through. Lineage shown in **Catalog Explorer** is kept indefinitely for anything captured
since September 2024 — but the time-range dropdown *defaults* to one year, which is the trap, because
a learner reads the default as the limit. The **lineage system tables** genuinely do keep only a
rolling one-year window. Same pattern as the audit surfaces and the two retention clocks: ask which
surface before answering how long.

Two limits are worth carrying. Lineage is **not preserved when you rename** a catalog, schema, table,
view or column, which is a governance surprise with an operational cause and exactly the shape a
troubleshooting stem takes. And resilient distributed datasets are not captured at all — the third
place in this certification where RDDs are excluded from something, after standard access mode and
volumes. Viewing any of this needs at least `BROWSE` on the parent catalog, which is now the third
job that one privilege does in this domain.

## Audit logging, and what it does not cover

Two surfaces deliver audit data and they are **not** equivalent. This divergence is the whole point
of the section.

| | Audit log system table | Azure Monitor diagnostic settings |
|---|---|---|
| Event coverage | All audited events and services | Not all of them |
| Account-level events | Included | Not included |

The workspace-level and account-level designations apply only to the system table. So a requirement
naming complete coverage, or naming account-level activity, resolves to the system table rather
than to the Azure-side surface — which is the opposite of what an Azure-focused candidate expects.

Two practical figures. Azure Databricks retains a copy of audit logs for up to **one year** for
security and fraud analysis. And system tables themselves are free to use; you are charged only for
the compute used to query them, which removes the cost objection a distractor might raise.

Audit log delivery requires the Premium plan. Learn that a plan requirement exists rather than
memorising what any tier contains.

<details>
<summary><b>Self-check — audit coverage</b></summary>

A compliance team needs a record of account-level administrative activity. Which surface, and why
not the other?

The audit log system table. Azure diagnostic logs do not include account-level events at all, and
do not cover every audited service.
</details>

## Retention is a governance decision

`VACUUM` looks like a cleanup job and is also a compliance control. Read it the second way and the
questions become easy.

Files removed by `VACUUM` may contain records that have been modified or deleted, so removing them
permanently ensures those records are no longer accessible. That is how a deletion becomes real
rather than merely logical.

The default retention threshold for data files after running `VACUUM` is **seven days**. The cost
is stated just as plainly: the ability to query table versions older than the retention period is
lost once it has run. Retention is therefore a trade between the right to be forgotten and the
ability to look backwards, and the exam frames it that way.

Seven days is also a floor, not just a default. Databricks strongly recommends a retention interval
of at least seven days, and the reason is nameable: a job running for several days writes files that
are not yet committed, and too short a window lets `VACUUM` delete them before the job finishes. An
option that shortens retention to satisfy a deletion deadline is offering a data-loss bug.

> **Trap.** `VACUUM` alone does not always make a deletion physical. Where deletion vectors or column
> mapping are in use, a delete is a *soft* delete: the old values stay in the current data files and
> only metadata marks them gone. Removing them takes two steps in order. First reorganise the table
> to rewrite its files, with `REORG TABLE ... APPLY (PURGE)`. Then run `VACUUM` to delete the older
> files once they have expired. A
> compliance requirement met with `VACUUM` by itself, on a table with deletion vectors enabled, has
> not been met.

Retention has a second surface too, on the other side of a drop rather than an update. A dropped
managed table stays recoverable with `UNDROP` before its files are purged, which you met in domain 1.
Keep the two mechanisms apart: `VACUUM`'s seven-day threshold governs historical *file versions* of a
table that still exists, while the recovery window governs a *table that no longer exists*. They are
different clocks on different things, and an answer that applies one figure to the other is wrong
even when the figure is right.

> **A note on that second number.** Microsoft's pages disagree on the dropped-table window — the
> managed-tables page says seven days in three places, the managed-versus-external comparison says
> eight. Do not memorise it. `VACUUM`'s seven days, by contrast, is stated consistently, so that is
> the figure worth holding.

Predictive optimization runs `ANALYZE`, `OPTIMIZE` and `VACUUM` operations using serverless compute
for jobs, billed at a serverless jobs rate. That is the mechanism behind managed tables maintaining
and optimising themselves, which you met in domain 1.

## Sharing outside the organisation

> **A note on names.** The exam guide's objective for this topic uses one name for the platform —
> *Delta Sharing* — while the current Azure Databricks documentation calls the same platform
> *OpenSharing* throughout. The concepts are unchanged. Recognise both names, and answer on the
> mechanics rather than the label.

Three concepts underlie it, and a question will usually name at least two of them.

| Concept | What it is |
|---|---|
| Share | The collection of data being made available |
| Provider | The organisation making it available |
| Recipient | The organisation receiving it |

A provider creates a share and grants a recipient access to it. Designing a *secure* strategy — the
guide's own word — means deciding which protocol fits, how the recipient authenticates, and how
access will be withdrawn when it ends.

Two protocols, and the choice between them is the strategy question.

| | Open sharing | Databricks-to-Databricks |
|---|---|---|
| Recipient needs Azure Databricks | No | Yes |
| Typical use | External partners, any platform | Organisations already on the platform |

The secure end of open sharing is federation. Open ID Connect (OIDC) federation grants short-lived
OAuth tokens to a recipient in exchange for tokens issued by the recipient's own identity provider
— short-lived and federated, rather than a long-lived credential sitting in someone's config file.

> **Trap.** Revocation is blunter than people expect. If a provider deletes a recipient from their
> Unity Catalog metastore, that recipient loses access to **every** share it could previously
> access — not just the one you had in mind. When a scenario describes revoking access to one
> dataset among several, deleting the recipient is the wrong instrument.

Sharing and fine-grained security interact, and the interaction depends on *which* mechanism you
chose back in the first half of this domain. A provider **cannot share a table carrying table-level
row filters or column masks** at all. A table protected by an ABAC policy *can* be shared — but only
if the share owner is exempt from that policy, named in its `EXCEPT` clause. So a requirement that
combines external sharing with row-level protection is not answered by picking a protection
mechanism and then arranging the share: the choice of mechanism has already decided whether the share
is possible.

<details>
<summary><b>Self-check — sharing</b></summary>

A partner organisation that does not use Azure Databricks needs access to one dataset, with no
long-lived credential. What does that describe?

Open sharing, secured with identity provider federation so the recipient receives short-lived
tokens rather than a standing credential. Had the recipient been another organisation already on the
platform with Unity Catalog, Databricks-to-Databricks would be the protocol instead — the recipient's
environment is what settles that pair, not the sensitivity of the data.

The dataset in question is a table with a column mask on it. Does that change the answer?

It may remove it. A table-level column mask cannot be shared at all. If the masking came from an ABAC
policy, the share is possible provided the share owner is in the policy's `EXCEPT` clause.
</details>

## Traps worth carrying into the exam

- **Containment grants authority.** The owner of a containing catalog or schema can grant on the
  objects inside it, so "only the direct owner" is wrong.
- **`BROWSE` bypasses the usage chain.** Discovery without `USE CATALOG` is the point of it.
- **Table-level row filters and column masks cannot go on a view.** The answer for a view is a
  dynamic view, and the limitation belongs to the table-level mechanism, not to row-level security.
- **Below 12.2 LTS, protected tables return nothing.** Empty results, not errors — and that floor is
  the table-level one. ABAC needs 16.4 or serverless.
- **A row filter policy grants nothing.** The user needs `SELECT` already; the policy only narrows.
- **Column tags do not inherit.** Tagging the table leaves the column unmatched and the policy inert.
- **A tag policy is not an ABAC policy.** Vocabulary against access.
- **Tags inherit only inside policy evaluation.** Privileges inherit downward; tags do not.
- **Governed tags are account-level.** That is what lets a policy reach across metastores.
- **Databricks roles and Azure roles do not overlap.** A grant in one is not a grant in the other.
- **Managed identity means no secret to rotate.** That phrase in a stem is the whole answer.
- **On views, ownership beats `MANAGE` for comments.** The one place `MANAGE` is not enough.
- **`COMMENT ON` and AI generate are different privilege bars.** The same catalog takes `MANAGE`
  by hand and `MODIFY` through Catalog Explorer. Read the verb in the stem.
- **Permission model before role on a Key Vault-backed scope.** A vault on Azure RBAC is blocked
  whatever the role; Vault access policy is the only supported model.
- **`[REDACTED]` is a print guard, not a permission.** Admins, the creator and any grantee read
  the secret anyway.
- **Diagnostic settings miss account-level events.** Completeness means the system table.
- **Deleting a recipient revokes everything.** Not one share — all of them.
- **A table-level mask blocks sharing entirely.** With ABAC it is shareable if the share owner is
  in `EXCEPT`.
- **`VACUUM` alone may not delete anything physically.** With deletion vectors, `REORG ... APPLY
  (PURGE)` comes first.
- **Lineage needs registration, not Databricks.** External assets join the graph as external
  metadata objects.
- **System tags are governed tags.** Their definition is fixed; who assigns them is yours to set.
