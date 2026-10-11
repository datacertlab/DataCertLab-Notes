# Exam overview: Microsoft Certified: Azure Fundamentals (AZ-900)

This page is the one you read before you start studying, and again the week before you sit. It
covers what the exam is, how it is scored, what the questions look like, and where candidates
studying from older material reliably go wrong.

Two kinds of thing are on this page, and they are kept apart. **Facts about the exam** come from
Microsoft's published material: the study guide, the certification page, its scoring and exam
experience pages, and Microsoft's own free practice assessment. **Advice about preparing** (what to
study first, how to spend the clock) is ours, and is labelled where it appears.

This course tracks the study guide marked **Skills measured as of July 20, 2026**, checked on
10 October 2026. The guide has changed three times since January 2024 without the exam code
changing, and the section on what changed explains why that matters to you.

---

## What the exam is

AZ-900 is Microsoft's entry-level Azure certification. It tests whether you can describe cloud
computing and Azure: the cloud models and service types, Azure's building blocks and core services,
and the tools for securing, governing, costing and monitoring them. It does not test whether you can
build anything. Every objective in the guide starts with *describe*, *define*, *compare* or
*identify*.

Microsoft writes the audience as a technology professional who wants to show foundational knowledge
of cloud concepts and of Azure, with experience in some area of IT such as infrastructure
management, database management or software development. Nothing in the guide assumes you have
used Azure before.

| | |
|---|---|
| Duration | **45** minutes to answer; 65 minutes seat time |
| Questions | Not published by Microsoft |
| Delivery | Proctored, through Pearson VUE, or Certiport for students and educators |
| Languages | 13: English, Japanese, Chinese (Simplified), Chinese (Traditional), Korean, Spanish, German, French, Italian, Indonesian (Indonesia), Arabic (Saudi Arabia), Portuguese (Brazil) and Russian |
| Prerequisites | None |
| Cost | Varies by the country or region in which you are proctored |
| Validity | Fundamentals certifications do not expire |

*Verified on 10 October 2026 against the [study guide](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900),
the [certification page](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/)
and Microsoft's [exam duration and exam experience](https://learn.microsoft.com/en-us/credentials/support/exam-duration-exam-experience) page.*

**Book more than 45 minutes.** The 45 minutes is exam time, the time you have to answer. Seat time is
65 minutes, because it also covers the instructions, the candidate agreement and the comments
screen at the end.

**This exam is closed book.** Microsoft lets candidates open Microsoft Learn during its associate and
expert exams. In its own words, *"access to Learn is NOT available on Fundamentals exams"*. Anything
you have seen elsewhere about looking things up mid-exam does not apply here.

Microsoft does not publish a fixed question count for AZ-900. Its exam experience page says most
Microsoft Certification exams *"typically contain between 40-60 questions"* and that the number can
vary by exam. Use that range for rough planning, and plan on the clock, not on a count.

---

## How it is scored

This is the section most candidates get wrong, and it is worth two minutes.

Your result is reported as a **scaled** score from 1 to 1,000. A score of **700** or greater passes.

**700 out of 1,000 is not "70% correct."** Microsoft states it plainly: *"As this is a scaled score,
it may not equal 70% of the points."* The bar is set from the skills needed to show competence and
from the difficulty of the questions you were actually given: for an easier set of questions, more
points are needed to pass. Any source telling you to aim for a percentage of correct answers is
guessing.

Scoring is **compensatory**: one bar, for the whole exam. Microsoft publishes no per-domain minimum,
so a weak area alone does not fail you. Your score report shows a bar for each skill area, but that
is feedback, not a pass mark per section.

There is **no penalty for guessing.** A wrong answer earns no point and loses nothing, so a blank
and a wrong answer score the same. Never leave a question blank.

**Some questions are not scored.** Microsoft uses them to trial new questions, and you cannot tell
which they are. Treat every question as one that counts.

**Questions with several parts can earn partial credit.** Microsoft says that on most multi-part
questions you receive one point for each correctly answered component, and that a question worth
more than one point says so.

---

## What is on it

Three skill areas. Microsoft publishes each weight as a range, and the three ranges do not centre on
100, so this course divides the midpoints by their total to get a share for each. That is why you
see two numbers.

| # | Skill area | Microsoft's published weight | Used here | Our mock allocation, of 50 |
|---|---|---|---|---|
| 1 | Describe cloud concepts | 25–30% | 28.2% | 14 |
| 2 | Describe Azure architecture and services | 35–40% | 38.5% | 19 |
| 3 | Describe Azure management and governance | 30–35% | 33.3% | 17 |

The last column is how this course splits a practice mock: the normalised midpoints applied to 50
questions. It is a practice-design choice, not a prediction of your exam. Microsoft publishes weight
ranges, not a number of questions per area. (When we took Microsoft's practice assessment on 10 October
2026, its results page grouped the 50 questions 14, 19 and 17 by skill area. That is a dated
observation of one version of the assessment, not a Microsoft blueprint.)

**Describe Azure architecture and services** is the largest area and the most concrete: it is where
most service names live. **Describe cloud concepts** is the smallest, but every other area assumes
its vocabulary.

### 1. Describe cloud concepts

What cloud computing is, and the shared responsibility model: what Microsoft manages, what you
manage, and how that split moves between on-premises, infrastructure as a service (IaaS), platform
as a service (PaaS) and software as a service (SaaS). The public, private and hybrid cloud models and
when each fits. The consumption-based model, cloud pricing models and serverless. The benefits the
cloud is sold on, and the differences between them: high availability, scalability, reliability,
predictability, security, governance and manageability.

### 2. Describe Azure architecture and services

Azure's physical and logical structure: regions, region pairs, sovereign regions, availability
zones, datacenters, and the hierarchy of resources, resource groups, subscriptions and management
groups. Compute: containers, virtual machines and functions; Azure Virtual Machine Scale Sets,
availability sets and Azure Virtual Desktop; what a virtual machine needs; and application hosting
with web apps, containers and virtual machines. Networking: virtual networks, subnets, peering,
Azure DNS, Azure VPN Gateway, ExpressRoute, and public against private endpoints. Storage: the Azure
Storage services, access tiers, redundancy options and storage account types; moving files with
AzCopy, Azure Storage Explorer and Azure File Sync; migrating with Azure Migrate and Azure Data Box.
Identity, access and security: Microsoft Entra ID and Microsoft Entra Domain Services; single
sign-on (SSO), multifactor authentication (MFA) and passwordless sign-in; external identities;
Microsoft Entra Conditional Access; Azure role-based access control (RBAC); Zero Trust;
defence in depth; and Microsoft Defender for Cloud.

### 3. Describe Azure management and governance

Cost: what affects Azure costs, the pricing calculator, cost management capabilities, and tags.
Governance and compliance: Microsoft Purview, Azure Policy and resource locks. Managing and
deploying: the Azure portal, Azure Cloud Shell, the Azure CLI and Azure PowerShell, Azure Arc,
infrastructure as code (IaC), and Azure Resource Manager (ARM) with ARM templates. Monitoring:
Azure Advisor, Azure Service Health, and Azure Monitor, including Log Analytics, Azure Monitor
alerts and Azure Monitor Application Insights.

---

## What changed: three revisions, and much study material has not caught up

Microsoft has revised the AZ-900 study guide three times since January 2024. The exam code, the three
skill areas and their weights have stayed the same throughout, which is exactly why older material
still looks current. Microsoft's own change log names only the latest revision and calls it
"Minor"; the table below comes from comparing four archived editions of the guide line by line. Each
edition is named by the date Microsoft prints at its top, "Skills measured as of".

| Skills measured as of | What changed |
|---|---|
| [January 23, 2024](https://web.archive.org/web/20250124215534/https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900) | The edition most courses and question banks were written against |
| [October 30, 2025](https://web.archive.org/web/20251201193037/https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900) | **The TCO Calculator was removed.** "Compare the pricing calculator and the Total Cost of Ownership (TCO) Calculator" became "Explore the pricing calculator". |
| [January 14, 2026](https://web.archive.org/web/20260528173216/https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900) | **B2B and B2C were removed** from "Describe external identities in Azure". |
| [July 20, 2026](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900) (current) | Wording only: "subnets" for "Azure virtual subnets"; Cloud Shell, the Azure CLI and Azure PowerShell listed side by side; "Azure Monitor Application Insights" in full. |

**The TCO Calculator is gone, and not just from the guide.** Microsoft's AZ-900 training unit
[Explore the pricing calculator](https://learn.microsoft.com/en-us/training/modules/describe-cost-management-azure/3-compare-pricing-total-cost-of-ownership-calculators)
now says *"The Total Cost of Ownership (TCO) calculator has been retired."* Older practice questions that
ask you to choose between it and the pricing calculator are testing a tool that no longer exists.
For estimating Azure costs, the answer is the pricing calculator.

**External identities are no longer framed as B2B against B2C.** The objective now reads simply
"Describe external identities in Azure". Learn what external identities are for: letting people
outside your organisation, such as partners and customers, sign in to your apps. Do not spend time
on the old B2B/B2C split. One related fact helps you read older material: Microsoft's renaming page
says Azure AD B2C was not renamed, and that it stopped being sold to new customers on May 1, 2025.
Microsoft points to Microsoft Entra External ID as its next-generation solution.

**There is no AI section.** Some third-party guides describe an AI refresh in early 2026 with Azure AI
services and Copilot. The current guide has no AI objective. Microsoft retired its separate AI
fundamentals exam, AI-900, on June 30, 2026.

### Names that have moved

Recognise the left column when you meet it in older material. The right column is what the guide
and the exam say.

| Older name, still widely written | Current name |
|---|---|
| Azure Active Directory (Azure AD, AAD) | Microsoft Entra ID |
| Azure AD Domain Services | Microsoft Entra Domain Services |
| Azure AD Conditional Access | Microsoft Entra Conditional Access |
| Application Insights | Azure Monitor Application Insights |
| TCO Calculator | Retired; use the pricing calculator |

Even Microsoft's own practice assessment has not fully caught up. One of its explanations still says
"Azure AD", and two of its questions are tagged with the January 2026 wording of the objectives. When
a study resource and the current guide disagree, the guide is what the exam is written from.

---

## What the questions look like

### Examples of formats in Microsoft's exam experience

**These are examples of the formats in Microsoft's exam experience, not a list of what AZ-900
contains.** Microsoft does not say which formats appear on a given exam; that is a stated security
policy. The list is here so the interface is familiar, not as a prediction. You can try every one of
them in the free **exam sandbox** at `aka.ms/examdemo`. Do it once before you
sit, so the first time you meet a format is not under the clock.

| Format | What you do |
|---|---|
| `multiple-choice` | Select **1** correct answer, usually from four choices. No **partial credit**. |
| `multiple-response` | Select a stated number of correct answers, usually two from five. The question tells you how many. |
| `build-list` | Move the required items into the answer area and put them in order. |
| `drag-and-drop` | Drag answer choices onto labelled targets. |
| `hot-area` | Click the required number of elements on an image. |
| `active-screen` | Set dropdowns, option buttons or spin boxes on a screenshot, as instructed. |
| `active-screen-dropdown` | The same without a screenshot: complete a statement from inline dropdowns. |
| `yes-no-statement-grid` | Answer Yes or No to each statement in a table, independently. |
| `problem-solution-set` | Several questions share one problem; each proposes a solution, and you answer from exactly **2** choices (Yes or No), **1** correct. **You cannot go back** to these. |
| `case-study` | A scenario with documents and several questions. Microsoft does not say whether AZ-900 uses them. |
| `lab` | Tasks in a live environment. Microsoft's duration table lists labs only for associate and expert exams. |
| `interlinear-dropdown` | Complete a sentence from dropdowns. Microsoft calls this experimental. |

*Microsoft does not publish which of these formats appear on AZ-900. A format being in the sandbox
does not confirm it appears on this exam.*

### What Microsoft's practice assessment shows

The rest of this section describes Microsoft's free 50-question practice assessment for AZ-900,
as we took it on 10 October 2026. It describes that assessment, not a Microsoft rule about the
exam. Microsoft says its practice assessments show *"the style, wording, and
difficulty"* of exam questions, and that the questions are not the ones on the exam.

- **Short, plain questions.** Most of its questions are a single sentence asking which service or concept does a
  stated job: *Which Azure service evaluates Azure resources and makes recommendations...?* A
  smaller group starts with a short situation (*You have on-premises servers. You need to...*) and
  then asks what you should use. That version had no code, no diagrams and no long scenarios.
- **Short answers.** Most options are two or three words: a service name, a tier, a concept.
- **Two-answer questions say so.** Nine of the fifty ask *Which two...?* and add *"Each correct
  answer presents a complete solution."* Every one needs exactly two answers.
- **Fill-the-blank sentences.** Six begin *"Select the answer that correctly completes the
  sentence."*, then give a sentence with a blank to fill.
- **Neighbours as wrong answers.** The wrong options are real services that do a nearby job: Log
  Analytics where the answer is Azure Advisor or Azure Service Health, resource locks or tags where
  the answer is Azure Policy, SSO where the answer is Conditional Access. Telling neighbours apart is
  a recurring pattern in the assessment, and a useful way to organise revision.
- **No shouting.** Microsoft does not capitalise words like *most* or *not*. The deciding phrase
  sits in ordinary lower-case text, so read every word of the question.

Microsoft also says the practice assessment is not illustrative of the exam's length or
complexity, and that you may see additional question types. Use it to find gaps in what you know, not
to predict exactly what your exam will look like.

---

## Timing and pacing

You have 45 minutes and no published question count. Against the 40 to 60 questions Microsoft gives as
typical for its exams, that is roughly 45 seconds to a minute each. This course's mocks give you 50 questions in
45 minutes, which is 54 seconds each.

Three rules from Microsoft's exam experience page change how you spend that time:

- **Breaks run on the exam clock.** Five minutes of break time are built into the 45, but the clock
  keeps running while you are away.
- **A break locks what you have already seen.** Once you start a break, you cannot return to earlier
  questions, even ones you marked for review or left unanswered. Clear them first.
- **A problem-solution set cannot be revisited.** If you meet one, decide each answer before moving
  on.

*DataCertLab preparation guidance.* The questions may be short, but the avoidable risk is misreading
a constraint and picking the familiar neighbour. Practise at the real time limit and keep time to
review the questions you mark.

- **Go through once and answer everything**, marking anything you are unsure of. A blank scores the
  same as a wrong answer.
- **On two-answer questions, count your selections** before moving on.
- **On the second pass, re-read only the marked questions** and find the phrase that decides each
  one. Change an answer only when you can name the phrase that proves your first choice wrong.

---

## Study strategy

*DataCertLab preparation guidance. Microsoft publishes the study guide and free training, but does
not recommend an order. The sequence below is ours.*

1. **Start with Describe cloud concepts.** Shared responsibility, the cloud models and IaaS/PaaS/SaaS
   are the vocabulary the other two areas assume. Learn the responsibility split cold: it comes back
   in questions far beyond its own objective.
2. **Then Describe Azure architecture and services**, the largest area. Study it as decisions, not as a
   catalogue. For each pair that sounds alike (VPN Gateway against ExpressRoute, Azure Files against
   Blob storage, Microsoft Entra ID against Microsoft Entra Domain Services), write down the one
   requirement that separates them.
3. **Then Describe Azure management and governance.** Most of its questions are *which tool for which
   job*: Advisor recommends, Service Health reports Azure's own incidents, Monitor collects your
   metrics and logs, Policy enforces rules, locks stop deletion, tags organise, Arc reaches beyond
   Azure.
4. **Take Microsoft's free practice assessment** on the certification page (Microsoft sign-in
   required). Its results page advises: *"aim to achieve a score of 80% or higher in multiple
   attempts."* That is a readiness signal, not a conversion to the scaled score. Read the
   explanation for every question you miss.
5. **Take this course's mocks**, then go back to the notes for the areas you scored lowest in.

If you already work with Azure, start with a mock instead, and spend your time where you scored
lowest. Check your knowledge against the "What changed" section above whichever route you take:
experienced candidates are the most likely to answer from habits that predate the current guide.

Microsoft's free AZ-900 training on Microsoft Learn has one learning path per skill area, module by
module, each ending in a short knowledge check.

### Optional hands-on checklist

Nothing below is required: the exam asks you to describe, not to build. If you have access to Azure,
seeing these for yourself makes them easier to recall:

- Create a resource group, then look at where it sits under your subscription.
- Open the pricing calculator and estimate one virtual machine.
- Start Azure Cloud Shell from the Azure portal and switch between Bash and PowerShell.
- Find Azure Advisor's recommendations and the Service Health page.
- Look at the policy definitions in Azure Policy and the lock options on a resource.

---

## How this course maps to the exam

One notes file and one cheatsheet per skill area, in the guide's own order, and a practice bank
weighted to the table above. Every full mock has 50 questions in 45 minutes.

Our practice questions are single-answer or two-answer. Where Microsoft would use a drag-and-drop or
a dropdown, we ask the same decision as a choice question. Two-answer questions are scored
all-or-nothing in our mocks, which is stricter than the partial credit Microsoft gives on most
multi-part questions.

Difficulty labels are our editorial judgement of the reasoning a question needs, using
Microsoft's practice assessment as a reference point. They are not Microsoft classifications or
measured difficulty. Easy needs one definition. Medium separates two neighbouring services on one stated detail. Hard turns on
a short situation with a constraint you could miss. They describe the question, not your chance of
passing: Microsoft reports a scaled score, so no practice score converts directly to an exam result.

---

## The last 24 hours

- Re-read the neighbour pairs in each cheatsheet, not the notes.
- Check the names table above, so an older name in your memory does not cost you a mark.
- Check your booking: the time zone, and for an online exam, the system check and a clear room.
- Do not learn anything new. If one topic still feels weak, review its traps and stop.
- On the day: one pass to answer everything, a second pass for the ones you marked, and no blanks.

---

## Official sources

Everything factual on this page traces to one of these. Check them rather than trusting any summary,
including this one.

- [Study guide for Exam AZ-900](https://learn.microsoft.com/en-us/credentials/certifications/resources/study-guides/az-900): skills measured, weights, change log
- [Microsoft Certified: Azure Fundamentals](https://learn.microsoft.com/en-us/credentials/certifications/azure-fundamentals/): duration, languages, delivery, practice assessment, exam sandbox
- [Exam scoring and score reports](https://learn.microsoft.com/en-us/credentials/certifications/exam-scoring-reports): scaled score, unscored questions, partial credit, guessing
- [Exam duration and exam experience](https://learn.microsoft.com/en-us/credentials/support/exam-duration-exam-experience): exam and seat time, typical question count, breaks, no Learn access on Fundamentals exams
- [Renew your Microsoft Certification](https://learn.microsoft.com/en-us/credentials/certifications/renew-your-microsoft-certification): Fundamentals certifications do not expire
- [New name for Azure Active Directory](https://learn.microsoft.com/en-us/entra/fundamentals/new-name): the Microsoft Entra renames
- [Explore the pricing calculator](https://learn.microsoft.com/en-us/training/modules/describe-cost-management-azure/3-compare-pricing-total-cost-of-ownership-calculators): the TCO Calculator retirement
- [Exam sandbox](https://aka.ms/examdemo): every question format, interactively
