# Exam overview: AWS Certified Data Engineer - Associate (DEA-C01)

This page is the one you read before you start studying, and again the week before your exam. It
covers what the exam is, how it is scored, what the questions look like, and what changed in the
guide that much study material was written against.

Two kinds of thing are on this page, and they are kept apart. **Facts about the exam** come from
AWS's published material: the exam guide, the certification page, and AWS's own practice questions.
**Advice about preparing** — what to study first, how to spend the clock — is ours, and is labelled
where it appears.

This course tracks version 1.1 of the exam guide, published 12 December 2025. The exam code did not
change, but version 1.1 added eight skills. The section on what changed lists them.

---

## What the exam is

DEA-C01 is AWS's associate-level data engineering certification. It tests whether you can build and
run data pipelines on AWS: ingest and transform data, orchestrate the steps, choose and model the
data stores, monitor and troubleshoot the pipelines, check data quality, and secure and govern the
data throughout.

AWS describes the target candidate as having the equivalent of two to three years of data
engineering experience and at least one to two years of hands-on experience with AWS services. The
guide also expects working knowledge of ETL pipelines, data lakes, Git, SQL and general networking,
storage and compute, and, new in version 1.1, general concepts of vectors.

The guide also lists three job tasks that are out of scope for the exam: *"Perform ML training and
inferences"*, *"Demonstrate knowledge of programming language-specific syntax"* and *"Draw business
conclusions based on data"*. Two of them shape how you study:

- **Analysing data is in scope; interpreting it for the business is not.** You are expected to query,
  aggregate, clean and quality-check data (Task 3.2, *Analyze data by using AWS services*). You are not
  expected to decide what the results mean for the company.
- **Reading code is in scope; syntax trivia is not.** You will read SQL and policy documents in
  questions, but you are tested on what they do, not on syntax details.

| | |
|---|---|
| Questions | **65** in total: **50** scored and 15 unscored |
| Duration | **130** minutes |
| Formats | multiple-choice and multiple-response |
| Delivery | A Pearson VUE test centre, or online with a remote proctor |
| Cost | 150 USD; AWS's exam pricing page gives local-currency prices |
| Prerequisites | None |
| Languages | English, Japanese, Korean and Simplified Chinese |

*Verified on 2 October 2026 against the [exam guide](https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01.html)
and the [certification page](https://aws.amazon.com/certification/certified-data-engineer-associate/).*

The certification is valid for three years. AWS's [recertification page](https://aws.amazon.com/certification/recertification/)
lists more than one way to keep it: pass the latest version of this exam, pass the AWS Certified
Generative AI Developer - Professional exam, or extend it by a year through a maintenance option on
AWS Skill Builder. Check that page for the current rules before you plan around them. Once you hold
one AWS certification, AWS's certification page says you get a discount of half the price of your
next AWS exam, claimed through your AWS Certification Account.

**Some services may appear under short names.** AWS uses official short names for well-known
services whose full names contain initials or a parenthetical, and a list of short and full names is
available behind the Help button during the exam. AWS publishes [the same list](https://aws.amazon.com/certification/policies/general-information/)
in advance. For example, *Amazon EKS* may appear instead of *Amazon Elastic Kubernetes Service*, and
*Amazon Keyspaces* instead of *Amazon Keyspaces (for Apache Cassandra)*.

---

## How it is scored

**The 15 unscored questions are hidden among the rest.** AWS uses them to trial questions for future
exams and does not mark which they are. Treat every question as one that counts.

Your result is reported as a **scaled** score from 100 to 1,000, and **720** passes. A scaled score
is not a percentage. AWS uses scaling to equate results across versions of the exam that may differ
slightly in difficulty, so 720 does not mean seventy-two per cent correct, and AWS publishes no
conversion from correct answers to the scaled score. Any source that tells you to aim for a
particular percentage is guessing.

Scoring is **compensatory**. In AWS's words, *"you do not need to achieve a passing score in each
section. You need to pass only the overall exam."* There is one bar, for the whole exam. Your score
report may show how you did in each section, and the guide itself warns you to use caution when
reading that feedback.

**Unanswered questions are scored as incorrect, and there is no penalty for guessing.** A blank and
a wrong answer score the same, so never leave a question blank.

---

## What is on it

Four content domains, each with a published weight of the **scored** content.

| # | Domain | Weight | DataCertLab mock allocation (65 questions, all scored) |
|---|---|---|---|
| 1 | Data Ingestion and Transformation | 34% | 22 |
| 2 | Data Store Management | 26% | 17 |
| 3 | Data Operations and Support | 22% | 14 |
| 4 | Data Security and Governance | 18% | 12 |

The last column is how this course splits each practice mock: a design choice of ours, rounded from
the weights, not a distribution AWS prescribes. It is not a prediction of the real exam: AWS's
weights apply to the 50 scored questions, AWS publishes no per-domain count, and you cannot tell
which questions are unscored.

The domain summaries below are orientation, not a complete list. The guide's own task and skill
list is the full statement of scope, and the services named here are examples drawn from it.

The domains overlap more than the weights suggest. A question filed under ingestion can turn on an
IAM role, and a storage question can turn on a lifecycle cost. Expect services to appear in more
than one domain.

### 1. Data Ingestion and Transformation

The largest domain. Reading from streaming sources (Amazon Kinesis Data Streams, Amazon MSK,
Amazon DynamoDB Streams, AWS DMS) and batch sources (Amazon S3, AWS Glue, Amazon EMR, Amazon
AppFlow). Schedulers and event triggers with Amazon EventBridge and Apache Airflow, invoking Lambda
from Kinesis, throttling and rate limits, fan-in and fan-out, and replaying an ingestion pipeline.
Transformation with Amazon EMR, AWS Glue, AWS Lambda and Amazon Redshift, converting formats such as
CSV to Apache Parquet, containers on Amazon EKS and Amazon ECS, JDBC and ODBC connections, and, new
in version 1.1, using large language models in data processing. Orchestration with Lambda,
EventBridge, Amazon MWAA, AWS Step Functions and AWS Glue workflows, with alerts through Amazon SNS
and Amazon SQS. And the programming side of the job: Lambda concurrency and storage, infrastructure
as code with AWS CloudFormation, AWS CDK and AWS SAM, CI/CD, and distributed computing.

### 2. Data Store Management

Choosing a store for a cost, performance and access pattern: Amazon Redshift, Amazon RDS and Amazon
Aurora, Amazon DynamoDB, Amazon MemoryDB, Amazon EMR, AWS Lake Formation. Remote access and
migration methods such as Redshift federated queries, materialized views and Redshift Spectrum, and
locks. New in version 1.1: open table formats such as Apache Iceberg, and vector index types (HNSW,
IVF). Catalogs: the AWS Glue Data Catalog and Apache Hive metastore, crawlers, partition
synchronisation, and, new, business data catalogs in Amazon SageMaker Catalog. The data lifecycle:
loading and unloading between Amazon S3 and Redshift, S3 Lifecycle policies, S3 versioning,
DynamoDB TTL, and deleting data to meet legal requirements. Data models: schema design for
Redshift, DynamoDB and Lake Formation, schema evolution and conversion, data lineage, partitioning
and compression, and, new, vectorization concepts such as Amazon Bedrock knowledge bases.

### 3. Data Operations and Support

Automating processing with Amazon MWAA, Step Functions, Lambda and EventBridge, calling AWS SDKs,
and preparing data with AWS Glue DataBrew and Amazon SageMaker Unified Studio. Analysing data:
SQL in Amazon Redshift and Amazon Athena, Athena notebooks with Apache Spark, visualisation, the
tradeoff between provisioned and serverless services, and aggregation, rolling averages, grouping
and pivoting. Monitoring: logs for audit, Amazon CloudWatch Logs, AWS CloudTrail, alerts, and
troubleshooting AWS Glue and Amazon EMR. Data quality: checks during processing, DataBrew quality
rules, consistency, sampling and data skew.

### 4. Data Security and Governance

Authentication: VPC security groups, IAM groups and roles, credential rotation with AWS Secrets
Manager, roles for Lambda, API Gateway and CloudFormation, policies on S3 Access Points and AWS
PrivateLink, and, new, domains, domain units and projects in SageMaker Unified Studio.
Authorization: custom IAM policies, least privilege, database users and roles in Redshift,
permissions through Lake Formation, and role-based, tag-based and attribute-based access.
Encryption and masking: AWS KMS, encryption across accounts and in transit, and data masking and
anonymisation. Audit logging with CloudTrail, CloudTrail Lake and CloudWatch Logs. Privacy and
governance: data sharing in Redshift, PII identification with Amazon Macie, keeping data in allowed
Regions, AWS Config, data sovereignty, and, new, access through SageMaker Catalog projects and data
sharing patterns.

---

## What changed: version 1.1 of the guide

AWS publishes two editions of the DEA-C01 guide. Both keep the four domains, their weights and the
17 tasks.

| Edition | What it is |
|---|---|
| Version 1.0 | The guide that accompanied the exam's launch, still served as a PDF on AWS's site |
| Version 1.1 | The current guide on AWS's documentation site, published 12 December 2025 |

The live guide's own [Revisions page](https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/dea-01-revisions.html)
lists the changes, and we checked the guide against the version 1.0 PDF line by line. AWS says exam
guide revisions are published at least one month before the changes appear on the exam. Version 1.1
was published on 12 December 2025, so prepare for its added content. AWS does not say exactly when
those changes began appearing on live exams.

Study resources written before December 2025 describe version 1.0. They will not cover the eight new
skills below, so check any resource's coverage against the live guide before you rely on it.

### Eight new skills

| Skill | What it adds |
|---|---|
| 1.2.10 | Integrate large language models (LLMs) for data processing |
| 2.1.7 | Manage open table formats, for example Apache Iceberg |
| 2.1.8 | Describe vector index types, for example HNSW and IVF |
| 2.2.6 | Create and manage business data catalogs, for example Amazon SageMaker Catalog |
| 2.4.6 | Describe vectorization concepts, for example Amazon Bedrock knowledge bases |
| 4.1.7 | Use domains, domain units and projects in SageMaker Unified Studio |
| 4.5.6 | Manage data access through Amazon SageMaker Catalog projects |
| 4.5.7 | Describe a governance data framework and data sharing patterns |

Together they add three themes: SageMaker Unified Studio and SageMaker Catalog for governance,
vectors and LLMs, and Iceberg tables. The out-of-scope list moved with them. Version 1.0 put
"artificial intelligence and machine learning (AI/ML) tasks" out of scope. Version 1.1 narrows that
to "ML training and inferences", so using AI in a pipeline is now in scope while training models
still is not.

### Skills reworded

Version 1.1 merged the guide's separate *Knowledge of* and *Skills in* lists into one numbered list of
skills per task, removing knowledge items that repeated a skill. Several skills gained new
examples worth noticing:

- **2.1.3** now names HNSW indexing in Amazon Aurora PostgreSQL and Amazon MemoryDB for fast
  key-value access.
- **2.4.4** adds SageMaker Catalog to data lineage, alongside SageMaker ML Lineage Tracking.
- **3.1.6** adds SageMaker Unified Studio to data preparation, alongside AWS Glue DataBrew.
- **3.2.3** covers SQL in Amazon Redshift as well as Amazon Athena.
- **4.3.4** covers encryption *before* transit as well as in transit.
- **4.2.5** lists role-based, tag-based and attribute-based authorization.

### Services in and out of scope

**Added to the in-scope list:** Amazon Aurora, Amazon Bedrock, Amazon Kendra, Amazon Q, AWS Data
Exchange and Amazon S3 Tables.

**Removed from the in-scope list:** AWS Cloud9, AWS CodeCommit and the AWS Schema Conversion Tool (AWS
SCT). The schema conversion skill (2.4.3) still names AWS SCT and AWS DMS Schema Conversion as
examples, so know what schema conversion does even though the tool left the list.

### Names that have moved

The guide is not consistent with itself on some names, and AWS's service documentation has moved on
from others. Recognise every form; questions test what the service does. The right-hand column is
what AWS's own documentation called each service on 2 October 2026.

| In the guide | In AWS's current documentation |
|---|---|
| Amazon QuickSight (skills 3.2.1 and 3.2.2); Amazon Quick (in-scope list) | Amazon Quick Sight, the visualisation feature of Amazon Quick |
| Amazon Kinesis Data Firehose (in-scope list) | Amazon Data Firehose, which AWS's official practice questions also use |
| Amazon MemoryDB for Redis (in-scope list); Amazon MemoryDB (skill 2.1.3) | Amazon MemoryDB, compatible with Valkey and Redis OSS |
| Amazon SageMaker AI (in-scope list) | Unchanged; older material says Amazon SageMaker |
| Amazon SageMaker Catalog, Amazon SageMaker Unified Studio (skills only) | Not on the guide's in-scope list, but named in five of the skills, so study them |

---

## What the questions look like

There are two formats, and AWS defines both.

| Format | What you do |
|---|---|
| `multiple-choice` | Pick the **1** correct answer from **4** options |
| `multiple-response` | Pick **2** or more correct answers from **5** or more options |

AWS's published guide does not say whether multiple-response questions receive partial credit. Our
practice tests score them all-or-nothing: you get the mark only for selecting exactly the correct
set. Our practice questions also state how many to pick — "(Select TWO.)" or "(Select THREE.)" — so
you practise reading for the count.

**What AWS says.** The guide describes wrong answers as *"plausible responses that match the content
area"*, ones *"a candidate with incomplete knowledge or skill might choose"*.

**What we observed.** The rest of this section comes from AWS's 20-question Official Practice
Question Set, not from an AWS rule. These observations describe that 20-question set only. They are
useful practice signals, not guarantees about how often anything appears on a live exam.

- **Every question is a scenario.** A company or a data engineer has an existing setup and a
  problem, stated in four to seven sentences, then the question. None of the 20 asked for a bare
  definition.
- **Every option is a complete design.** Options are two or three sentences that name services and
  say how to configure them. Most wrong options would work. They fail one stated requirement.
- **The qualifier decides.** Nine of the 20 questions end with a capitalised qualifier: *LEAST
  operational overhead* (the commonest), *MOST cost-effective*, *MOST performance-optimized* or
  *LOWEST latency*. When two options both work, the qualifier picks the answer, and it usually
  favours the managed service over the self-built one.
- **Service limits catch people out.** Several wrong options describe something a service cannot
  do: Redshift unloading straight to a Glacier storage class, Redshift `COPY` reading data encrypted
  with customer-provided keys, Parameter Store rotating credentials. Knowing what a service *won't*
  do is worth as much as knowing what it does.
- **Some questions show configuration.** One of the 20 printed an IAM policy and asked how to correct
  it. The guide names SQL in Redshift and Athena as a skill, so expect to read a short query or policy
  and judge what it does.
- **Multiple-response questions can have six options and three answers.** Two of the four in AWS's
  set did.
- **The answer is not reliably the longest option.** In AWS's set the correct answer was strictly the
  longest option only once in 16 single-answer questions.

---

## Timing and pacing

You have 130 minutes for 65 questions, which is two minutes each.

*DataCertLab preparation guidance.* The questions are long, and reading is most of the time. Two
minutes is enough for most questions if you read with a purpose:

- **Read the question line first**, then the stem. Knowing that the question asks for *LEAST
  operational overhead* tells you what to look for in the scenario.
- **Underline the constraints as you go**: every number and every *must*. In AWS's practice questions,
  each one rules an option out.
- **Answer everything on the first pass**, even where you are unsure, and flag it. A blank scores the
  same as a wrong answer.
- **On multiple-response questions, count your selections** against the number asked for.
- **On the second pass**, re-read only the flagged stems. Change an answer only when you can name the
  requirement your first choice misses.

---

## Study strategy

*DataCertLab preparation guidance. AWS publishes the exam guide and a four-step exam prep plan on
AWS Skill Builder, but does not set a study order. The sequence below is ours.*

1. **Start with Domain 1, Data Ingestion and Transformation.** It is the largest domain and the
   vocabulary the other three assume: streams and shards, batch and event-driven ingestion, Glue jobs,
   EMR, Lambda and orchestration.
2. **Then Domain 2, Data Store Management.** Study it as decisions: for each store, the access pattern
   and cost profile it fits, and the lifecycle each tier of data should follow.
3. **Then Domain 3, Data Operations and Support**: monitoring, troubleshooting, SQL analysis and data
   quality. Many of its questions reuse services from the first two domains, now asking how to run them.
4. **Then Domain 4, Data Security and Governance.** IAM roles, Lake Formation permissions, KMS and
   Macie appear across every domain, so the earlier domains give you a head start.
5. **Give the version 1.1 additions their own time.** SageMaker Catalog and Unified Studio, vectors
   and Iceberg are where older material is thinnest.
6. **Take AWS's official practice questions** on AWS Skill Builder (sign-in required). They are written
   by AWS and show the real style. AWS's certification page also lists an Official Pretest for finding
   gaps and an Official Practice Exam for checking readiness.

If you already work as a data engineer on AWS, you may not need this order. Start instead with a
diagnostic, such as the AWS Certification Official Pretest or one of this course's full mocks, then
spend your time on the domains where you scored lowest.

Two habits worth forming early. For every pair of services that do neighbouring jobs (Firehose and
Kinesis Data Streams, Athena and Redshift Spectrum, Secrets Manager and Parameter Store), learn the
one requirement that separates them. And for every service, learn one thing it cannot do.

### Hands-on practice

AWS expects one to two years of hands-on experience, and the questions read like it: they describe
configurations, not definitions. If you have an AWS account, building small versions of these is the
fastest way to make the scenarios familiar. Some of these need IAM permissions or setup beyond a
new account, and several incur charges while they run. Delete what you create when you finish:
streams, clusters, crawlers, jobs and stored objects.

- Send records into a Kinesis data stream and read them with a Lambda function; then deliver the same
  data to S3 as Parquet with Firehose.
- Crawl an S3 prefix with an AWS Glue crawler, query the table in Athena, and run a small Glue job.
- Load data from S3 into Redshift with `COPY`, unload it back, and query S3 from Redshift with
  Spectrum.
- Write an S3 Lifecycle rule that transitions and then expires objects.
- Register an S3 location in Lake Formation and grant column-level access to a role.
- Store a database credential in Secrets Manager and turn on rotation.

---

## How this course maps to the exam

One notes file and one cheatsheet per domain, in the guide's own order, and a practice bank weighted
to the table above. Every full mock has 65 questions in 130 minutes, matching the real sitting, and
every question in a mock is scored.

Difficulty labels on practice questions compare each question with AWS's own official practice
questions. Easy turns on one stated requirement. Medium uses the stated qualifier to choose between
designs that both work. Hard needs several constraints at once, or rejects a near-miss on a specific
service limit. They describe the question, not your chance of passing. AWS sets the passing standard
and reports a scaled score, so no practice score converts directly to an exam result.

---

## The last 24 hours

- Re-read the separating-requirement pairs and the "cannot do" lists in each domain's cheatsheet, not
  the notes.
- Look over AWS's list of short service names so none of them surprises you.
- Check your booking: the time zone, and for an online exam, the system check and a clear room.
- Bring the identification your booking confirmation asks for.
- Do not learn anything new. If one topic still feels weak, review its traps and stop.
- On the day: read the question line first, one pass to answer everything, a second pass for the
  flagged ones, and no blanks.

---

## Official sources

Everything factual on this page traces to one of these. Check them rather than trusting any summary,
including this one.

- [AWS Certified Data Engineer - Associate (DEA-C01) exam guide](https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/data-engineer-associate-01.html) — domains, tasks and skills, in-scope and out-of-scope services, scoring
- [Exam guide revisions](https://docs.aws.amazon.com/aws-certification/latest/data-engineer-associate-01/dea-01-revisions.html) — what changed in version 1.1
- [AWS Certified Data Engineer - Associate certification page](https://aws.amazon.com/certification/certified-data-engineer-associate/) — duration, cost, languages, delivery, validity, short service names
- [AWS Skill Builder](https://skillbuilder.aws/) — the official practice question set, pretest, practice exam and exam prep plan
