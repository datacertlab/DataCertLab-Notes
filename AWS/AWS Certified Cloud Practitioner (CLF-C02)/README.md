# Exam overview: AWS Certified Cloud Practitioner (CLF-C02)

This page is the one you read before you start studying, and again the week before you sit. It
covers what the exam is, how it is scored, what the questions look like, and where candidates
studying from older material reliably go wrong.

Two kinds of thing are on this page, and they are kept apart. **Facts about the exam** come from
AWS's published material: the exam guide, the certification page, and AWS's own practice questions.
**Advice about preparing** — what to study first, how to spend the clock — is ours, and is labelled
where it appears.

This course tracks the exam guide on AWS's documentation site: unversioned live guide, checked 1 October 2026.
That guide carries no version number and no date, and it has changed more than once without the
exam code changing. The section on what changed explains why that matters to you.

---

## What the exam is

CLF-C02 is AWS's foundational certification. It tests whether you can explain the AWS Cloud — its
value, its security model, its core services and how it is billed — not whether you can build on
it. AWS designs it for people who are new to the cloud, including people without an IT background:
sales, marketing, product and project roles as much as engineers.

AWS describes the target candidate as having up to six months of exposure to AWS Cloud design,
implementation or operations, and its certification page adds that this exposure is not required.
The guide also lists what you are *not* expected to do: coding, designing cloud architecture,
troubleshooting, implementation, and load and performance testing. If a question seems to want any
of those, you have misread it.

| | |
|---|---|
| Questions | **65** in total: **50** scored and 15 unscored |
| Duration | **90** minutes |
| Formats | multiple-choice and multiple-response |
| Delivery | A Pearson VUE test centre, or online with a remote proctor |
| Cost | 100 USD; AWS's exam pricing page gives local-currency prices |
| Prerequisites | None |

*Verified on 1 October 2026 against the [exam guide](https://docs.aws.amazon.com/aws-certification/latest/cloud-practitioner-02/cloud-practitioner-02.html)
and the [certification page](https://aws.amazon.com/certification/certified-cloud-practitioner/).*

The exam is offered in Arabic, English, French (France), German, Italian, Japanese, Korean,
Portuguese (Brazil), Spanish (Latin America), Spanish (Spain), Simplified Chinese and Traditional
Chinese. AWS's certification page states that the Italian and German versions will be retired after
31 December 2026.

The certification is valid for three years. AWS's certification page also notes that once you hold
one AWS certification, you get half off the price of your next AWS exam.

---

## How it is scored

This is the section most candidates get wrong, and it is worth two minutes.

**The 15 unscored questions are hidden among the rest.** AWS uses them to trial questions for future
exams and does not mark which they are. You cannot tell an unscored question from a scored one, so
treat every question as one that counts.

Your result is reported as a **scaled** score from 100 to 1,000, and **700** passes. A scaled score
is not a percentage. AWS uses scaling to equate results across versions of the exam that
may differ slightly in difficulty. So 700 does not mean seventy per cent correct, and AWS publishes no
conversion from correct answers to the scaled score. Any source that tells you to aim for a particular
percentage is guessing.

Scoring is **compensatory**. In AWS's words, *"you do not need to achieve a passing score in each
section. You need to pass only the overall exam."* There is one bar, for the whole exam. Your score
report may show how you did in each section, and the guide itself warns you to use caution when
reading that feedback.

**Unanswered questions are scored as incorrect, and there is no penalty for guessing.** A blank and
a wrong answer score the same, so never leave a question blank.

---

## What is on it

Four content domains, each with a published weight of the **scored** content.

| # | Domain | Weight | Our mock allocation, of 65 |
|---|---|---|---|
| 1 | Cloud Concepts | 24% | 16 |
| 2 | Security and Compliance | 30% | 19 |
| 3 | Cloud Technology and Services | 34% | 22 |
| 4 | Billing, Pricing, and Support | 12% | 8 |

The last column is how this course splits each practice mock, rounded from the weights. It is not a
prediction of the real exam: AWS's weights apply to the 50 scored questions, AWS publishes no
per-domain count, and you cannot tell which questions are unscored.

**Cloud Technology and Services** and **Security and Compliance** together carry most of the scored
content. Domain 4 is the lightest, but it is also where older study material is most out of date —
read the next section before you decide to skim it.

### 1. Cloud Concepts

The benefits of the AWS Cloud: global infrastructure, speed of deployment, high availability,
elasticity and agility. The AWS Well-Architected Framework and the differences between its six
pillars: operational excellence, security, reliability, performance efficiency, cost optimisation
and sustainability. Migration: cloud adoption strategies, the AWS Cloud Adoption Framework (AWS CAF)
and the resources that support a migration. Cloud economics: fixed against variable cost, the costs
of running on premises, Bring Your Own License (BYOL) against included licences, rightsizing, the
benefits of automation and economies of scale.

### 2. Security and Compliance

The AWS shared responsibility model — what AWS does, what you do, what you share, and how the split
moves between a service like Amazon EC2, Amazon RDS and AWS Lambda. Compliance and governance:
where to find compliance reports (AWS Artifact), encryption in transit and at rest, and which
services monitor (Amazon CloudWatch), audit (AWS CloudTrail and AWS Config) and report. Access
management: IAM users, groups, roles and policies, least privilege, protecting the root user and the
tasks only the root user can do, multi-factor authentication (MFA), AWS IAM Identity Center,
federation, and storing credentials with AWS Secrets Manager and AWS Systems Manager. Security
services and resources: AWS WAF, AWS Firewall Manager, AWS Shield, Amazon GuardDuty, Amazon
Inspector, AWS Security Hub, AWS Trusted Advisor, AWS Marketplace for third-party security
products, and where AWS publishes security information.

### 3. Cloud Technology and Services

The largest domain, and the one that is mostly *which service for which need*. Ways to provision and
operate: the AWS Management Console, APIs, SDKs, the AWS CLI and infrastructure as code; cloud,
hybrid and on-premises deployment. Global infrastructure: Regions, Availability Zones and edge
locations, and when to use more than one Region. Compute: Amazon EC2 instance types, containers
(Amazon ECS, Amazon EKS), serverless (AWS Fargate, AWS Lambda), auto scaling and load balancers.
Databases: relational (Amazon RDS, Amazon Aurora), NoSQL (Amazon DynamoDB), in-memory (Amazon
ElastiCache) and the migration tools AWS DMS and AWS SCT. Networking: the parts of a VPC, security
groups against network ACLs, Amazon Route 53, AWS VPN and AWS Direct Connect. Storage: Amazon S3 and
its storage classes, block storage (Amazon EBS, instance store), file services (Amazon EFS, Amazon
FSx), AWS Storage Gateway, lifecycle policies and AWS Backup. AI/ML and analytics, such as Amazon
SageMaker AI, Amazon Lex, Amazon Athena, Amazon Kinesis, AWS Glue and Amazon Quick Sight. And a
spread of other categories: messaging (Amazon EventBridge, Amazon SNS, Amazon SQS), business
applications (Amazon Connect, Amazon SES), developer tools (AWS CodeBuild, AWS CodePipeline, AWS
X-Ray), end-user computing (Amazon AppStream 2.0, Amazon WorkSpaces, Amazon WorkSpaces Secure
Browser), AWS Amplify and AWS IoT Core.

### 4. Billing, Pricing, and Support

Compute purchasing options — On-Demand Instances, Reserved Instances, Spot Instances, Savings
Plans, Dedicated Hosts, Dedicated Instances and Capacity Reservations — and when each fits, including
how Reserved Instances behave across AWS Organizations. Data transfer costs in and out, between
Regions and within one. Storage pricing tiers. Cost tools: AWS Budgets, AWS Cost Explorer, AWS
Pricing Calculator, consolidated billing in AWS Organizations, cost allocation tags and the AWS Cost
and Usage Report. And help: AWS Support plans, AWS Support Center, AWS re:Post, AWS Knowledge Center,
AWS Prescriptive Guidance, AWS Trusted Advisor, AWS Health Dashboard, the AWS Trust and Safety team,
AWS Professional Services, solutions architects, and the AWS Partner Network.

---

## What changed: the guide has moved twice, and much study material has not

AWS has revised the CLF-C02 exam guide more than once without changing the exam code, the four
domains or their weights. This course compares three official editions:

| Edition | What it is |
|---|---|
| Version 1.0 | The PDF guide that accompanied the exam's launch on 19 September 2023 |
| Version 1.2, May 2025 | A later PDF edition of the same guide |
| Live guide | The current guide on AWS's documentation site, checked 1 October 2026, showing no version number or date |

We can tell what changed between these editions. We cannot tell exactly when each change reached
the live exam, because the live guide carries no revision date. Study resources written before a
change may still describe the earlier version, so check support-plan names and service scope
against the live guide before you rely on any other source. That includes AWS's own official
practice questions: their support-plan question still uses the older plan names.

### Since the May 2025 edition

**AWS Support plans.** This is the largest change. The live guide names Basic Support, AWS Business
Support+, AWS Enterprise Support and AWS Unified Operations. Version 1.2 named Developer, Business,
Enterprise On-Ramp and Enterprise. AWS's live Support plans page confirms the current paid plans are
Business Support+, Enterprise Support and Unified Operations.

> **Which one to pick.** The guide is the authority for what the exam asks, and it names the current
> plans, so learn those. Plan names are the part that moves; the decision the exam tests does not. It
> is always the least expensive plan that delivers what the question states — phone access, a
> response time, a designated contact. If you meet an older plan name in a question, answer on what
> the question says the plan must provide.

**Services no longer listed as in scope:** Amazon Kendra, AWS Audit Manager, AWS AppSync and AWS
Snow Family. AWS Audit Manager has also gone from the Domain 2 auditing example, which now names
AWS CloudTrail and AWS Config only.

**Renamed:** Amazon QuickSight is now Amazon Quick Sight.

### Between the 2023 and May 2025 editions

These changes are already in the May 2025 edition. Material written before 2025 may still miss them.

**Developer tools narrowed.** Version 1.0 listed ten developer tools. The later editions name three:
AWS CodeBuild, AWS CodePipeline and AWS X-Ray. AWS CodeDeploy, AWS CloudShell and AWS CodeArtifact
are now on the guide's *out-of-scope* list, and AWS Cloud9, AWS CodeCommit and AWS CodeStar are not
mentioned at all.

**Services added to the in-scope list:** Amazon DocumentDB, Amazon ElastiCache, Service Quotas,
Migration Evaluator, AWS PrivateLink, AWS Transit Gateway, AWS Site-to-Site VPN and AWS Client VPN.

**Services removed:** AWS Local Zones, AWS Resource Groups and Tag Editor, and AWS Activate for
Startups. AWS Billing Conductor moved to the out-of-scope list.

**Bullet changes worth knowing.** Security services in Domain 2 name AWS Firewall Manager, AWS
Shield and Amazon GuardDuty alongside AWS WAF. VPC security in Domain 3 includes Amazon Inspector.
The AWS CAF bullet asks for its *components* rather than its benefits. And "understand the AWS
Well-Architected Framework" is one of the exam's headline tasks.

### Names that have moved

Recognise the left column when you meet it in older material; the right column is what the guide
says now.

| Older name, still widely written | Name in the current guide |
|---|---|
| Developer, Business, Enterprise On-Ramp support | Business Support+, Enterprise Support, Unified Operations |
| Amazon QuickSight | Amazon Quick Sight |
| Amazon SageMaker | Amazon SageMaker AI |
| Amazon WorkSpaces Web | Amazon WorkSpaces Secure Browser |
| AWS Single Sign-On | AWS IAM Identity Center |
| AWS Application Migration Service (still the guide's name) | AWS Transform MGN in AWS's own documentation, since June 2026 |

Learn the current names used in the live guide, and recognise the older names when you meet them in
other resources. In a question, focus on what the service does and what the requirement asks for.

---

## What the questions look like

There are two formats, and AWS defines both.

| Format | What you do |
|---|---|
| `multiple-choice` | Pick the **1** correct answer from **4** options |
| `multiple-response` | Pick **2** or more correct answers from **5** or more options |

AWS's published guide does not say whether multiple-response questions receive partial credit. Our
practice tests score them all-or-nothing: you get the mark only for selecting exactly the correct
set, so you learn to identify every correct option. Our practice questions also state how many to
pick — "(Select TWO.)" — so you practise reading for the count.

**What AWS says.** The guide describes wrong answers as *"plausible responses that match the content
area"*, ones *"a candidate with incomplete knowledge or skill might choose"*.

**What we observed.** The rest of this section comes from AWS's 20-question official practice set,
not from an AWS rule. Three patterns stood out:

- **Short stems in plain language.** Some questions are a single line — which service does this?
  Others set up one sentence of situation, then ask. There is no long case study, no code, and no
  architecture diagram.
- **Options that are mostly service names**, all of the same kind. The work is telling apart two
  services that sound alike or do neighbouring jobs: AWS Direct Connect against AWS Site-to-Site
  VPN, Amazon SNS against Amazon SQS, Amazon Inspector against Amazon Macie.
- **One phrase that carries the constraint.** "Consistent and private", "the existing internet
  connection", "the MINIMUM plan" — in the practice set, the deciding requirement was stated
  plainly in the stem. Read for what it requires, not for how it is typed.

---

## Timing and pacing

You have 90 minutes for 65 questions, which is about 83 seconds each.

*DataCertLab preparation guidance.* The questions are short, so most candidates should have time for
a second pass. The bigger risk is reading too fast. Use the spare time like this:

- **Go through once and answer everything**, even where you are unsure. A blank scores the same as a
  wrong answer.
- **On multiple-response questions, count your selections** against the number the question asks
  for. It is the cheapest mark to lose.
- **On the second pass, re-read only the stems** of the questions you were unsure about and find the
  one phrase that decides it. Change an answer only when you can name the phrase that proves your
  first choice wrong.

---

## Study strategy

*DataCertLab preparation guidance. AWS publishes the exam guide and training, but does not recommend
an order. The sequence below is ours.*

1. **Start with Domain 1, Cloud Concepts.** It is the vocabulary the other three assume: Regions and
   Availability Zones, elasticity, pay-as-you-go, the six pillars. It is also a quarter of the exam.
2. **Then Domain 2, Security and Compliance.** The shared responsibility model is the single idea
   most worth knowing cold, because it reappears in questions well beyond its own domain.
3. **Then Domain 3, Cloud Technology and Services**, the largest. Study it as decisions, not as a
   catalogue: for each pair of services that sound alike, write down the one requirement that
   separates them.
4. **Then Domain 4, Billing, Pricing, and Support.** It is the lightest, but study it from current
   material: the support plans changed after the May 2025 edition of the guide.
5. **Take AWS's official practice questions** on AWS Skill Builder (sign-in required). They
   are written by AWS and show the real style. Bear in mind that the support-plan question in that
   set still uses the older plan names.

If you already work with AWS, you may not need this order. Start instead with a diagnostic: the
AWS Certification Official Pretest, which AWS's certification page recommends for finding the areas
you need to refresh, or one of this course's full mocks. Then spend your time on the domains where
you scored lowest.

Two habits worth forming early. Read each stem for its deciding phrase before you look at the
options. And when two services overlap, learn the condition that separates them; that boundary is
what gets tested, not the definitions.

### Optional hands-on checklist

Coding and implementation are out of scope, so you do not need to build anything, and nothing below
is required. If you have access to an AWS account, opening the AWS Management Console and seeing
these things for yourself makes them easier to recall:

- Find the Billing and Cost Management console, AWS Cost Explorer and AWS Budgets.
- Open AWS Pricing Calculator and estimate one small workload.
- In IAM, look at how users, groups, roles and policies relate, and where MFA is turned on.
- Open AWS Trusted Advisor and AWS Health Dashboard and see what each one reports.
- Pick a Region and look at its Availability Zones.
- In Amazon S3, look at the storage classes offered when you upload an object.

---

## How this course maps to the exam

One notes file and one cheatsheet per domain, in the guide's own order, and a practice bank
weighted to the table above. Every full mock has 65 questions in 90 minutes, matching the real
sitting, and every question in a mock is scored.

Difficulty labels on practice questions compare each question with AWS's own official practice
questions. Easy needs one fact. Medium separates two similar services on one stated requirement.
Hard turns on a qualifier you could miss, or combines two topics. They describe the question, not
your chance of passing. AWS sets the passing standard and reports a scaled score, so no practice
score converts directly to an exam result.

---

## The last 24 hours

- Re-read the deciding-phrase pairs in each domain's cheatsheet, not the notes.
- Check your booking: the time zone, and for an online exam, the system check and a clear room.
- Bring the identification your booking confirmation asks for.
- Do not learn anything new. If one topic still feels weak, review its traps and stop.
- On the day: one pass to answer everything, a second pass for the ones you were unsure of, and no
  blanks.

---

## Official sources

Everything factual on this page traces to one of these. Check them rather than trusting any summary,
including this one.

- [AWS Certified Cloud Practitioner (CLF-C02) exam guide](https://docs.aws.amazon.com/aws-certification/latest/cloud-practitioner-02/cloud-practitioner-02.html) — domains, task statements, in-scope and out-of-scope services, scoring
- [AWS Certified Cloud Practitioner certification page](https://aws.amazon.com/certification/certified-cloud-practitioner/) — duration, cost, languages, delivery, validity
- [AWS Support plans](https://aws.amazon.com/premiumsupport/plans/) — the current plan lineup
- [AWS Skill Builder](https://skillbuilder.aws/) — the official practice question set and exam prep training
