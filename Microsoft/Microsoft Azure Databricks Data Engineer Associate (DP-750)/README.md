# Exam overview: Microsoft Certified: Azure Databricks Data Engineer Associate (DP-750)

This page is the one you read before you start studying, and again the week before you sit. It
covers what the exam is, how it is scored, what the questions look like, and where candidates
reliably guess wrong.

Two kinds of thing are on this page, and they are kept apart. **Facts about the exam** come from
Microsoft's published material — the study guide, the certification page, and its scoring and exam
experience documentation. **Advice about preparing** — what to study first, how to spend the clock,
what candidates get wrong — is ours, and is labelled where it appears.

This course tracks the study guide marked **Skills measured as of March 11, 2026**.
*Last verified against the live guide: 17 September 2026 — unchanged.* DP-750 is a new certification
rather than a revision, so the guide carries no change log yet; when it gains one, that is the first
thing to re-read.

---

## What the exam is

DP-750 is an intermediate, role-based certification. It is Microsoft's exam, delivered through
Pearson VUE, over a product that is mostly Databricks: you are tested on Unity Catalog, Lakeflow,
Delta, Auto Loader and Photon, with a real ring of Azure services around them — Microsoft Entra,
Azure Key Vault, Azure Data Factory, Azure Event Hubs and Azure Monitor.

| | |
|---|---|
| Duration | **120** minutes |
| Delivery | Proctored, through Pearson VUE, online or at a test centre |
| Languages | English only, at the time of writing |
| Prerequisites | None published |
| Cost | Varies by the country or region in which you are proctored |

Microsoft does not publish a question count for DP-750, and says outright that counts vary between
exams. Across its portfolio it says most exams carry roughly forty to sixty questions. Plan your
pacing on the clock, not on a count.

Book more than two hours. The 120 minutes is *exam duration* — the time you have to answer. Seat
time is longer, because it also covers the instructions, the candidate agreement and the comment
screen at the end. Microsoft does not publish which exams contain interactive components such as
labs, by policy; you are told when you register, and again on the screens before the exam starts.

---

## How it is scored

This is the section most candidates get wrong, and it is worth two minutes.

Your result is reported as a **scaled** score from 1 to 1,000. A score of **700** or greater passes.

**700 out of 1,000 is not "70% correct."** Microsoft states it plainly: *"As this is a scaled score,
it may not equal 70% of the points."* The passing bar is set from the knowledge and skills needed to
show competence and from the difficulty of the questions you were actually served. Microsoft is
explicit about that last part: *"For easier sets of questions, more points are required to pass. For
more difficult sets of questions, fewer points are required to pass."* Any source telling you to aim
for 70% of the questions is guessing, and guessing low.

Scoring is **compensatory**: there is one bar, for the whole exam. Microsoft publishes no per-domain
minimum, and the per-skill bar chart on your score report exists for feedback only — Microsoft says
it "can't be used to calculate the number of questions answered correctly in a section or on the
exam as a whole." You cannot fail on one weak area alone. That does not make it safe to write a
domain off: the two heaviest areas are published at 30–35% each, so most of the paper sits in
two of the four.

There is **no penalty for guessing.** An incorrect answer simply earns no point; nothing is
deducted. An unanswered question and a wrong answer score identically, so never leave one blank.

Some questions are worth more than one point, and Microsoft does not say which.

---

## What is on it

Four skill areas. Microsoft publishes each as a range; this course apportions its practice questions
using the midpoint, which is why you will see both numbers.

| # | Skill area | Microsoft's published weight | Used here |
|---|---|---|---|
| 1 | Set up and configure an Azure Databricks environment | 15–20% | 17.5% |
| 2 | Secure and govern Unity Catalog objects | 15–20% | 17.5% |
| 3 | Prepare and process data | 30–35% | 32.5% |
| 4 | Deploy and maintain data pipelines and workloads | 30–35% | 32.5% |

**Prepare and process data** and **Deploy and maintain data pipelines and workloads** are published
at 30–35% each — so between them they are most of the paper. Microsoft publishes no combined figure,
so add the ranges yourself rather than trusting anyone's round number, including ours. If your time
is short, that is where it goes.

The first two areas are smaller but they are not easier: Unity Catalog's object model and privilege
model underpin the answers in the other two, so study them first even though they carry less
weight.

### What changed: the Lakeflow rename, and why most study material is behind

Databricks renamed a product family shortly before this exam published. The guide says **Lakeflow
Spark Declarative Pipelines** and **Lakeflow Connect**; almost everything written earlier — courses,
blogs, and a great deal of what you will find by searching — says **Delta Live Tables** and **DLT**.
Same family, current name. Older material is not wrong about how any of it works — a good DLT-era
tutorial still teaches the right mechanics — but the vocabulary has moved, and the exam uses the
current wording. Learn both names, recognise the old one when you meet it, and answer in the new
one.

Four other topics are recent enough that older material tends to skip them: attribute-based access
control using tags and policies, liquid clustering, deletion vectors, and Declarative Automation
Bundles.

---

## What each area actually covers

Enough to tell you what you are walking into. The full objective list is on Microsoft's study guide,
and each area gets its own notes file in this course.

### 1. Set up and configure an Azure Databricks environment

Choosing and configuring compute — job, serverless, warehouse, classic and shared — and the settings
that go with it: node type and count, autoscaling, termination, pooling, Photon, runtime version,
and access permissions. Installing libraries. Then creating and organising Unity Catalog objects:
catalogs, schemas, volumes, tables, views and materialized views, naming conventions that account for
isolation and external sharing, foreign catalogs and connections, DDL on managed and external
tables, and AI/BI Genie instructions for data discovery.

### 2. Secure and govern Unity Catalog objects

Granting privileges to users, service principals and groups. Table-level, column-level and row-level
access control. Reaching Azure Key Vault secrets from a workspace, and authenticating with service
principals and managed identities.

Then the governance half, which is easy to under-study: table and column definitions and
descriptions for discovery, **attribute-based access control using tags and policies**, **row filters
and column masks**, **data retention policies**, **data lineage** through Catalog Explorer — owner,
history, dependencies — **audit logging**, and designing a secure strategy for **Delta Sharing**.

### 3. Prepare and process data

The largest area, and it has four distinct halves.

**Modelling.** Extraction type and file type, and choosing a table format — Parquet, Delta, CSV,
JSON or Iceberg. Partitioning schemes. Slowly changing dimension types. Column and table granularity.
Temporal history tables. A clustering strategy across liquid clustering, Z-ordering and deletion
vectors. Managed against unmanaged tables.

**Ingestion.** Lakeflow Connect, notebooks and Azure Data Factory as the tool choice; batch against
streaming as the loading choice. SQL paths — CTAS, `CREATE OR REPLACE TABLE`, `COPY INTO`. Change
data capture feeds. Spark Structured Streaming, including from Azure Event Hubs. Lakeflow Spark
Declarative Pipelines with Auto Loader.

**Transformation.** Profiling data and reading its distribution. Choosing column data types. Finding
and resolving duplicates, missing values and nulls. Filtering, grouping and aggregating. Joins,
union, intersect and except. Denormalising, pivoting and unpivoting. Loading by merge, insert and
append.

**Data quality — an explicit exam area, not an implementation detail.** Validation checks for
nullability, data cardinality and range. Data-type checks. Schema enforcement and managing schema
drift. And managing quality with pipeline expectations in Lakeflow Spark Declarative Pipelines. If
you skip one thing on this page, do not let it be this one: it is named in the outline and it is
routinely missing from third-party material.

### 4. Deploy and maintain data pipelines and workloads

**Pipeline design.** Order of operations. Notebook against Lakeflow Spark Declarative Pipelines. Task
logic for Lakeflow Jobs. Error handling across pipelines, notebooks and jobs. Precedence constraints.

**Lakeflow Jobs.** Creating and configuring a job, triggers, scheduling, alerts, and automatic
restarts for a job or pipeline.

**Development lifecycle.** Git version control practices, branching, pull requests and conflict
resolution. A testing strategy spanning unit, integration, end-to-end and user acceptance testing.
Configuring and packaging Declarative Automation Bundles, and deploying a bundle through the
Databricks CLI or the REST API.

**Monitoring and optimisation.** Managing cluster consumption for performance and cost.
Troubleshooting and repairing Lakeflow Jobs — repair, restart, stop and run. Diagnosing Spark jobs
and notebooks, including caching, skew, spill and shuffle, using the DAG, the Spark UI and the query
profile. Optimising Delta tables with `OPTIMIZE` and `VACUUM`. Log streaming through Log Analytics in
Azure Monitor, and configuring Azure Monitor alerts.

---

## Terminology that has moved

Recognise the left column when you meet it in older material; answer in the right.

| Older name, still widely written | Current name, used by the guide |
|---|---|
| Delta Live Tables, DLT | Lakeflow Spark Declarative Pipelines |
| Databricks ingestion connectors | Lakeflow Connect |
| Azure Active Directory, AAD | Microsoft Entra ID |
| Jobs / Workflows | Lakeflow Jobs |

## What candidates commonly confuse

*DataCertLab preparation guidance.* Each of these is a pair the exam can separate with a single
clause in the stem, so learn the condition that decides between them rather than the two features.

| Pair | What decides it |
|---|---|
| Serverless against classic compute | Startup time and management overhead — against needing RDD APIs, R, or JAR libraries. |
| Managed against external tables | Who owns the lifecycle, and whether the data must stay where it is. |
| Liquid clustering / Z-ordering / partitioning | The write pattern and the query shape, not the table's size. |
| Streaming tables against materialized views | Incremental append against full recomputation. |
| Row filters against column masks against ABAC | Whether the requirement names rows, columns, or both across many tables. |
| `OPTIMIZE` against `VACUUM` | Compacting files against physically removing unreferenced ones. |
| Delta Sharing against granting catalog access | Whether the recipient is outside the metastore. |
| Repair-and-rerun against full restart | Cost and time against determinism. |

## Possible question formats

**These are the formats Microsoft's exam platform supports, not a list of what DP-750 contains.**
Microsoft will not publish which formats appear on a specific exam — that is a stated security
policy, not an oversight — so treat the table below as the range of things you could meet, and do
not expect to meet all of them.

You can interact with every one of them in the free **exam sandbox** at `aka.ms/examdemo` before you
sit. Do that. Meeting a format for the first time under the clock costs marks that have nothing to
do with Azure Databricks.

| Format | What you do |
|---|---|
| `multiple-choice` | Select **1** correct answer from four choices. No **partial credit**. |
| `multiple-response` | Select a stated number of correct answers from five choices. The stem always tells you how many to pick. |
| `build-list` | Move the required items into the answer area and put them in the correct order. |
| `drag-and-drop` | Drag answer choices onto labelled targets. |
| `hot-area` | Click the required number of elements directly on an image. |
| `active-screen` | Configure interactive elements — dropdowns, option buttons, spin boxes — as the question instructs. |
| `active-screen-dropdown` | The same type without a screenshot: complete a statement using inline dropdowns. |
| `yes-no-statement-grid` | Judge each row of a table independently against shared source material. |
| `problem-solution-set` | Several questions share one scenario; each proposes a different solution and you answer whether it meets the goal, from exactly **2** choices, with **1** correct. **You cannot return to these**, so decide before moving on. |
| `case-study` | A scenario with supporting documents and several questions. Not timed separately. |
| `lab` | Perform tasks in a live environment. Not timed separately, and once you start one **you cannot go back** to earlier sections. |
| `interlinear-dropdown` | Complete a sentence from inline dropdowns. Microsoft describes this as experimental and intended to replace drag-and-drop for accessibility. |

Two of these change how you spend time rather than what you know. Anything marked as unreturnable —
`problem-solution-set` and `lab` — ends your chance to revise earlier answers, so clear your
marked-for-review questions before you commit.

---

## Timing and pacing

You have 120 minutes and no published question count, which makes pacing a judgement rather than a
formula. Against Microsoft's stated portfolio range of roughly forty to sixty questions, that is
somewhere between two and three minutes each. Budget on the low end and you will finish with room.

Four things distort that average, and knowing them beforehand is most of the benefit:

- **Case studies and labs are not timed separately.** They draw from the same 120 minutes. A lab can
  take several minutes on its own, so if one appears, your per-question budget on everything else is
  tighter than the arithmetic suggests.
- **Some sections cannot be revisited.** Once you leave a `problem-solution-set`, or start a lab, you
  cannot go back. Clear anything you marked for review before you move on, not at the end.
- **Taking a break ends your access to what you have seen.** If you use the break option, you are told
  how many questions are unanswered or marked first — answer them before you go.
- **Some questions are worth more than one point**, and you cannot tell which. Do not spend five
  minutes on a question because it looks heavy.

The practical rule: answer everything, since there is no penalty for guessing, and spend your saved
time on the two heavy skill areas rather than on any single question.

## How to study for this one

*DataCertLab preparation guidance. Microsoft publishes a study guide and training paths, but does not
recommend a study order — the sequencing below is ours, and it is a judgement, not a vendor rule.*

A preparation order that matches how the material actually depends on itself:

1. **Start with Unity Catalog**, even though areas 1 and 2 are the lightest. The object hierarchy —
   metastore, catalog, schema, table, volume — and the privilege model are assumed by the answers in
   the two heavy areas. Getting them late means relearning the heavy areas twice.
2. **Then ingestion and transformation**, area 3, the largest single block. Know which tool fits
   which source, and know the distinctions rather than the names: batch against streaming, managed
   against external, liquid clustering against Z-ordering against partitioning.
3. **Then pipelines and operations**, area 4. This is where the exam asks what you would do when
   something is already broken — a failed job, a skewed shuffle, a table of small files.
4. **Do the official training.** The DP-750T00-A learning paths on Microsoft Learn are free, map one
   path per skill area, and each module ends in a knowledge check. They are easier than the exam and
   are not a readiness test, but they are written by the people who write the exam, so the vocabulary
   and the phrasing are the real thing.
5. **Get hands-on.** This exam consistently asks which thing you would configure for a stated
   requirement, not what a feature is called. That is difficult to prepare for by reading.

Two habits worth forming early. Read every stem for the constraint that eliminates the obvious
answer — "without reprocessing files already ingested", "regardless of whether upstream tasks
succeeded" — because that clause is usually the whole question. And when you meet two features that
overlap, write down the one condition that separates them; that boundary is what gets tested, not
the features themselves.

## How this course maps to the exam

One notes file and one cheatsheet per skill area, in the guide's own order, plus a practice bank
weighted to the table above. The order matters: the material is written so that each area can assume
the vocabulary of the ones before it, which is why area 1 comes first despite being the lightest.

Difficulty labels on practice questions describe how hard an item is **relative to other items in
this course**. They are not a prediction of your exam score, and they cannot be — Microsoft sets its
cut score by statistical analysis and does not publish it as a percentage.

---

## Before you book

- Walk the exam sandbox at `aka.ms/examdemo`. Fifteen minutes, free, no sign-in, and it removes an
  entire category of surprise.
- Re-read the study guide the week you book, and check whether a change log has appeared.
- Have hands-on time in a workspace. This exam asks what you would configure, not what a feature is
  called, and that distinction is hard to fake.
- Check the current price for your region. Microsoft publishes it at booking, not on the
  certification page.

---

## Official sources

Everything factual on this page traces to one of these. Check them rather than trusting any summary,
including this one.

- [Study guide for Exam DP-750](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/dp-750) — the skills measured, and where a change log will appear
- [Microsoft Certified: Azure Databricks Data Engineer Associate](https://learn.microsoft.com/en-us/credentials/certifications/implementing-data-engineering-solutions-using-azure-databricks/) — duration, languages, booking
- [Exam scoring and score reports](https://learn.microsoft.com/en-us/credentials/certifications/exam-scoring-reports) — the scaled score, and why it is not a percentage
- [Exam duration and exam experience](https://learn.microsoft.com/en-us/credentials/support/exam-duration-exam-experience) — seat time, breaks, question formats
- [Exam sandbox](https://aka.ms/examdemo) — the formats, in the real interface
- [Azure Databricks documentation](https://learn.microsoft.com/en-us/azure/databricks/) — the product itself
