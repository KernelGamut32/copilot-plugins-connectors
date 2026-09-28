# Which Extension Would You Choose?
## Participant Scenario Pack - Module 4 (Slides 39 to 45)

| | |
|---|---|
| **Course** | Extend Copilot with Plugins & Connectors (Day 6) |
| **Module** | Module 4 - Designing Practical Enterprise Integration Scenarios |
| **Activity** | "Which Extension Would You Choose?" (Slide 45) |
| **Format** | One scenario per table. Design as a team. Present in two minutes. |
| **Environment** | Microsoft 365 Copilot running in a GCC tenant |
| **Pack date** | September 28, 2026 |

> **Everything in this pack is synthetic.** The business units, systems, people, job numbers, and data were created for this class. They do not describe any real agency system, vendor, or record.

---

## Why this activity exists

In Modules 1 through 3 you learned the pieces: connectors expand what Copilot can know, actions expand what an agent can do, and workflows connect those capabilities into business outcomes. Module 4 is where you practice the decision.

Each table receives one scenario written the way integration requests actually arrive: a business unit with a real problem, a few facts about the systems involved, and at least one complication that could pull you toward the wrong answer.

Your job is not to pick a Microsoft product. Your job is to name the requirement that forced the choice.

---

## Your toolkit from the slides

### The reusable design sequence (Slide 40)

Walk these five steps in order before you touch a technology name.

| Step | Question to answer |
|---|---|
| **1. Outcome** | What must become easier? What does success look like for the user and the organization? |
| **2. Knowledge + Source + Freshness** | What information is needed? Where is it authoritative? How current must it be? |
| **3. Skill** | What must the solution actually do? Read-only, or transactional? |
| **4. Identity + Control** | Who is performing the operation? What permissions and approvals apply? |
| **5. Experience** | Where should the user interact with the solution? Copilot Chat, Teams, a custom agent surface? |

### The four integration patterns (Slides 41 to 44)

| Pattern | Shape | Best when |
|---|---|---|
| **1. Enterprise Knowledge Assistant** | Copilot + synced connector | Information is stable, searchable, and does not need to be real time |
| **2. Live Operational Assistant** | Copilot or agent + federated connector | Data changes frequently and must remain authoritative in the source system |
| **3. Workflow Agent** | Knowledge + declarative agent + action + Power Platform workflow | Users must move from insight to controlled action with human approval checkpoints |
| **4. Cross-System Assistant** | Multiple connectors + declarative agent + API actions + approval workflow | One conversation must span several systems the employee would otherwise navigate individually |

There is a fifth possibility that is not on a pattern slide, and it is a legitimate answer: **Native Copilot only.** If the information already lives in Microsoft 365, the right extension may be no extension at all.

### The extension menu (Slide 45)

| Option | What it is | Reach for it when | Notes for a GCC tenant (as of September 28, 2026) |
|---|---|---|---|
| **Native Copilot only** | Copilot working over Microsoft 365 content the user already has access to | The content is already in SharePoint, OneDrive, Exchange, or Teams and the real problem is permissions, search visibility, or content quality | Optionally add a focused agent built with Agent Builder (available in GCC) |
| **Synced connector** | A Microsoft 365 Copilot connector that indexes external content into Microsoft Graph, with metadata, ACLs, and semantic indexing | Stable content, large corpus, historical search, results wanted in Microsoft Search as well as Copilot | Copilot connectors are documented as available in GCC, GCC High, and DoD |
| **Federated connector** | An MCP-based Copilot connector that fetches data at query time under the user's identity, with no indexing | Rapidly changing operational data that must remain in the source system | Read-only today. Write, update, and delete begin rolling out in early October 2026 and are not something to design on yet. Confirm any specific federated connector in your tenant before depending on it |
| **Declarative agent** | A specialized Copilot experience built from instructions, knowledge, and actions, running on the Microsoft 365 Copilot orchestrator | The user needs a focused job description, a specific knowledge scope, or actions | Full declarative agent support and Agent Builder are documented for GCC |
| **API plugin / action** | An OpenAPI or MCP based capability that a declarative agent can call to read or change data in an external system | The solution must perform an operation, not just answer | Plugins are supported only as actions inside declarative agents. They are not enabled standalone in Microsoft 365 Copilot. Actions that send data prompt the user for confirmation |
| **Power Platform connector** | A wrapper around an API that Copilot Studio, Power Automate, and Power Apps can use | A Power Platform connector already exists, or the solution lives in Copilot Studio and needs tools | Copilot Studio is available in GCC with generative orchestration and the Teams and Microsoft 365 Copilot channel |
| **Workflow** | A sequence of operations with approvals, notifications, and records, typically in Power Automate | Multiple steps, human approval, unattended or scheduled processing | Copilot Studio triggers and autonomous agents are not available in GCC. Scheduled or unattended work belongs in Power Automate flows |
| **Combination** | Any of the above working together | Most real requirements | Justify every component. A component you cannot justify is a component you should remove |

### The justification criteria (Slide 45)

Every decision must be defended on these five criteria, not on product preference.

| Criterion | The question |
|---|---|
| **Knowledge** | What does the solution need to know that Copilot does not already know? |
| **Freshness** | How old can the answer be before it is wrong? |
| **Action** | Does anything need to be created, updated, submitted, or routed? |
| **Identity** | On whose authority does the solution read or act? |
| **Governance** | What permissions, approvals, audit, and data-handling rules must survive the integration? |

---

## Instructions

**Total time:** Your facilitator will announce the design time. Plan on 15 minutes of design and a two-minute debrief per table.

1. **Read the scenario together.** One person reads it aloud. Do not skip the complications section. It is there on purpose.
2. **Classify the request.** Is this KNOW, DO, or KNOW + DO? If the scenario contains more than one request, classify each one.
3. **Walk the design sequence.** Answer all five steps from Slide 40 in writing before you name a technology.
4. **Choose a pattern.** Pattern 1, 2, 3, 4, or Native Copilot only. If you believe the request should not be built at all, say so and say why.
5. **Choose the components.** Select from the extension menu. Assign each information need and each operation in the scenario to a specific component.
6. **Justify on the five criteria.** Write one sentence for each of Knowledge, Freshness, Action, Identity, and Governance.
7. **Place the human checkpoints and the failure path.** Where must a person approve? What should the user see when the external system is unavailable?
8. **Prepare the two-minute debrief.** Use the debrief card below.

### Ground rules

- Assume a GCC tenant. If a feature is not available in GCC today, design around it, and say that you did.
- Federated connectors are read-only today. If your scenario needs an update, that update needs an action.
- "It depends" is only an answer if you finish the sentence: "It depends on X, and X in this scenario is Y, so we chose Z."
- Do not choose a component because someone at the table likes it. Choose it because a requirement demands it.
- You may propose a phased design. If you do, state what ships first and what gates the second phase.

---

## Decision worksheet (one per table)

| Layer | Your team's decision |
|---|---|
| Table number and scenario | |
| Classification (KNOW / DO / KNOW + DO) | |
| 1. Outcome | |
| 2. Knowledge + Source + Freshness | |
| 3. Skill (read-only or transactional) | |
| 4. Identity + Control | |
| 5. Experience | |
| Pattern selected | |
| Components selected (and what each one handles) | |
| Justification - Knowledge | |
| Justification - Freshness | |
| Justification - Action | |
| Justification - Identity | |
| Justification - Governance | |
| Human checkpoints | |
| Failure handling | |
| The one requirement that drove the decision | |
| The biggest risk in our design | |

---

## Two-minute debrief card

When your table presents, cover these six points in this order. Practice once before you stand up.

1. **Classification:** "This was a KNOW / DO / KNOW + DO request because..."
2. **Pattern:** "We chose Pattern N (or Native Copilot only) because..."
3. **Components:** "Information X comes from component A. Operation Y runs through component B."
4. **The deciding requirement:** "The single requirement that forced this design was..."
5. **The human checkpoint:** "A person approves at this point because..."
6. **The failure path:** "If the external system is down, the user sees..."

---

# The scenarios

Each scenario includes the business situation, the prompts users want to type, facts about the information and systems involved, identity and governance facts, complications, and your table's task.

---

## Scenario 1 - Twenty Years of Standards, Zero Copilot Answers

**Business unit:** Composition and Production Standards Branch
**Primary users:** Approximately 140 composition specialists, prepress technicians, and agency publishing liaisons

### Situation

The branch maintains the organization's authoritative production standards in a legacy on-premises document management system called **DocVault**. DocVault holds roughly 185,000 documents accumulated over 20 years: typographic standards, binding and finishing specifications, paper specifications, job-ticket templates, historical guidance memos, and every superseded version of every standard, retained for records purposes.

Specialists say the same thing in every interview: "The answer exists. Finding it takes 20 minutes, and half the time I find the superseded version first."

Copilot currently has no visibility into DocVault at all.

### What users want to ask

> "What are the current binding specifications for perfect-bound publications over 400 pages, and what changed from the 2022 version?"

> "Which paper specifications apply to a saddle-stitched publication with a four-color cover, and which guidance memo introduced them?"

> "Show me every standard that references coated stock and whether each one is current or superseded."

Users have also asked that DocVault content appear in Microsoft Search results, not only in Copilot Chat.

### Information and system facts

| Fact | Detail |
|---|---|
| Volume | About 185,000 documents, 6 TB total |
| Change rate | Quarterly publication cycle. A few hundred documents change per quarter. Emergency updates are rare |
| Structure | Every document carries metadata: document type, product category, effective date, status (Current or Superseded), and a "supersedes" reference to the prior version |
| Interface | DocVault exposes a REST API that lists documents, returns content and metadata, and provides a change log endpoint (changes since a timestamp) |
| Restricted content | Security-printing specifications are restricted to members of the Security Printing group |
| Retention | Superseded versions must remain available to authorized users and must be clearly labeled as superseded |

### Operations involved

None. Every request is read and search. Nobody has asked to create or change a standard from Copilot.

### Identity and permission facts

- All users sign in with their Microsoft Entra ID accounts.
- DocVault has its own permission groups, maintained by a records librarian. Those groups are not synchronized with Entra ID today.
- The Security Printing group in DocVault has 22 members. The equivalent Entra security group has 24 members. The librarian is not sure why they differ.

### Governance and constraints

- Restricted content must never surface to unauthorized users, in Copilot or in Microsoft Search.
- Superseded content must be distinguishable from current content in any answer.
- The records office wants a single source of truth. They have rejected past proposals to copy standards into SharePoint.

### Complications to consider

- A well-liked administrator has proposed "just export everything to a SharePoint library so Copilot can see it."
- A developer on the team argues for a federated connector "because then it is always current."
- A specialist points out that 185,000 documents is a lot, and asks whether all of it needs to be connected.

### Your table's task

1. Classify the request and choose a pattern.
2. Decide what gets connected and how, including what metadata must travel with the content.
3. Explain how the DocVault permission model is preserved in Copilot and Microsoft Search, given that the groups do not match.
4. Explain how a user will know whether an answer came from a current or a superseded standard.
5. Name the refresh cadence and the requirement that justifies it.

---

## Scenario 2 - Where Is My Job Right Now?

**Business unit:** Agency Publishing Services (customer-facing liaison team)
**Primary users:** 60 internal liaisons who answer status calls from agency customers

### Situation

The **Production Job Tracking System (PJTS)** is the system of record for about 12,000 active publication jobs. A job moves through nine production phases: intake, preflight, composition, proof, plate, press, bindery, quality review, and shipping. Status changes every few minutes across the floor. PJTS records about 40,000 status events per business day.

When an agency customer calls, the liaison needs the current status, the last status change, and the responsible group. Today the liaison keeps PJTS open in a second window and copies information into Teams or Outlook by hand.

### What users want to ask

> "What is the current status of job FP-2026-1048, when did it last change, and which group owns it now?"

> "Which jobs for my assigned agencies moved into bindery today?"

> "Is anything in my agency portfolio stuck in preflight for more than two days?"

### Information and system facts

| Fact | Detail |
|---|---|
| Volume | 12,000 active jobs plus 300,000 closed jobs |
| Change rate | Minutes. A status shown 30 minutes ago is frequently wrong |
| Interface | PJTS exposes a REST API. The PJTS team has already built an MCP server exposing three tools: search_jobs, get_job, and list_status_events. All three tools are read-only |
| Authentication | The MCP server is protected with Microsoft Entra ID. PJTS enforces record-level permissions: a liaison sees only jobs for agencies assigned to them |
| Hosting | The MCP server is reachable over HTTPS from the internet through the organization's application gateway |

### Operations involved

The liaison requests above are read-only.

However, see the complications.

### Identity and permission facts

- Every liaison has an Entra ID account and a PJTS account linked to it.
- PJTS authorization is per record and is evaluated on every API call.
- Agency customers are external and will not use Copilot in this tenant.

### Governance and constraints

- The PJTS system owner has issued a written rule: "No copies of live production data outside PJTS."
- Status information is not sensitive, but agency assignment data is considered internal.
- The organization's search team maintains the Copilot connector catalog and prefers connectors they can manage centrally.

### Complications to consider

- A program manager has added a second request: "While we are at it, let me bump a job's priority from Copilot too."
- The search team asks: "Can we just index PJTS? We already run six connectors and our users love unified search."
- Nobody has yet confirmed which connector capabilities are turned on in the GCC tenant.

### Your table's task

1. Classify the liaison requests and the program manager's request separately.
2. Choose a pattern and components for the read requests. Explain what the "no copies" rule and the change rate each rule out.
3. Explain how the priority update must be delivered given what is available today, and what you would say to the program manager about timing.
4. Describe how user identity flows from Copilot to PJTS so that record-level permissions still hold.
5. List what must be verified in the GCC tenant before this design is promised to anyone.

---

## Scenario 3 - The Report Was in SharePoint the Whole Time

**Business unit:** Congressional Publishing Support
**Primary users:** 25 staff members who prepare and consume the Weekly Production Readiness Report

### Situation

The team has filed a formal request: "Copilot cannot see our Weekly Production Readiness Reports. We need a connector to our shared drive."

The integration team investigated and found the following.

- The "shared drive" is a SharePoint site named **CPS-Readiness**, created three years ago.
- Site permissions are limited to the six people who originally set it up. The other 19 team members have never had access and have been receiving the reports as email attachments.
- Roughly 40 percent of the historical reports are image-only PDFs produced at a print-and-scan station. The most recent 18 months are Word documents.
- The document library setting that allows items to appear in search results was turned off during a cleanup two years ago. Nobody remembers why.
- The team also keeps its procedures library, **CPS-Procedures**, on a separate SharePoint site that is correctly permissioned and searchable.

### What users want to ask

> "Summarize the readiness risks called out in the last four weekly reports."

> "Which production lines were flagged as at risk more than twice this quarter?"

> "Based on our procedures, what is the standard response when a line is flagged in consecutive weeks?"

The team lead would also like a focused assistant that answers only from the readiness reports and the procedures library, without pulling in unrelated content.

### Information and system facts

| Fact | Detail |
|---|---|
| Volume | About 160 weekly reports, plus 300 procedure documents |
| Change rate | One new report per week |
| Location | Entirely within Microsoft 365 (two SharePoint sites) |
| Format issue | 40 percent of historical reports are image-only PDFs with no text layer |

### Operations involved

None. Summarize, compare, and explain.

### Identity and permission facts

- All 25 team members have Entra ID accounts and Copilot licenses.
- No Entra security group exists for the team today. Membership has been managed by individual email distribution.

### Governance and constraints

- Readiness reports are internal and should not be visible to the whole organization.
- The organization has been sensitized to oversharing by the earlier Security and Governance course and has a standing rule that broad "Everyone" permissions require review.

### Complications to consider

- A well-meaning administrator has offered to grant "Everyone except external users" access to the CPS-Readiness site "so we can close the ticket today."
- A developer proposes building a Copilot connector that points at the SharePoint site.
- The team lead asks whether the focused assistant requires Copilot Studio.

### Your table's task

1. Classify the request and choose a pattern. Be prepared to defend a choice that involves building nothing new.
2. List, in order, what must be fixed for Copilot to answer the first two prompts, and explain why each fix is necessary.
3. Explain why the administrator's offer creates a governance problem and what to do instead.
4. Explain whether the developer's connector proposal adds value, and why.
5. Describe how you would deliver the focused assistant and which tool you would use in a GCC tenant.

---

## Scenario 4 - Reprint Requests Without the Swivel Chair

**Business unit:** Agency Publishing Services - Reprint Desk
**Primary users:** 30 order specialists and 4 supervisors

### Situation

Reprint requests arrive by email from agency customers. For each request, a specialist:

1. Finds the original job in the **Order Management System (OMS)**.
2. Verifies that the agency's authorization code is still valid in OMS.
3. Confirms the requested quantity and unit against the original.
4. Creates a reprint order in OMS.
5. If the quantity exceeds 5,000 copies, obtains supervisor approval before the order is released.
6. Emails the requester with the order number and estimated completion.

Specialists call this "the swivel chair": Outlook, OMS, the SOP in SharePoint, the supervisor in Teams, and back to Outlook. The average request takes 22 minutes of handling time, most of it switching and re-keying.

### What users want to ask

> "Look up original job FP-2025-7731, confirm the authorization code is still valid, create a reprint order for 7,500 copies, and route it for approval."

> "What did the SOP say about reprints when the original stock is discontinued?"

> "Show me my reprint orders waiting on supervisor approval."

### Information and system facts

| Fact | Detail |
|---|---|
| OMS interface | REST API with operations for order lookup, authorization validation, reprint creation, and order notes |
| Existing asset | A **Power Platform custom connector for OMS already exists.** It was built last year for a Power App and exposes GetOrder, SearchOrders, ValidateAuthorization, CreateReprintOrder, and UpdateOrderNote. It authenticates each user individually against Entra ID |
| SOP | The Reprint Standard Operating Procedure lives in SharePoint and is updated twice a year |
| Change rate | Order data changes as specialists work. Freshness matters at the moment of action, not for analysis |

### Operations involved

- Validate an authorization code (read)
- Create a reprint order (write, financial consequence)
- Route for supervisor approval when quantity exceeds 5,000 (workflow, human decision)
- Add a note recording the outcome (write)
- Notify the requester (communication)

### Identity and permission facts

- OMS must record which specialist created each order. Orders created under a shared or service identity are unacceptable to the audit team.
- Supervisors must approve in their own identity; a specialist may not approve their own order.

### Governance and constraints

- A complete audit trail is required: who requested, who created, who approved, and when.
- Orders above 5,000 copies must never be released without supervisor approval.
- The desk works primarily in Microsoft Teams and wants the solution there.

### Complications to consider

- The desk manager wants a second capability: "Let the agent process the reprint mailbox overnight with nobody watching, and just leave the orders for us in the morning."
- A developer suggests rebuilding everything as a pro-code declarative agent with a brand new OpenAPI plugin, setting the existing connector aside.
- A supervisor asks what stops the agent from creating an order the specialist did not intend.

### Your table's task

1. Classify the request and choose a pattern.
2. Assign each of the five operations to a specific component and name where the human checkpoints sit.
3. Explain how identity is preserved so that the audit team's requirement is met.
4. Decide whether to reuse the existing Power Platform connector or build a new plugin, and justify the decision on requirements rather than preference.
5. Address the overnight processing request in a GCC tenant and recommend a position on it.

---

## Scenario 5 - The Depository Library Inquiry

**Business unit:** Library Services Support Desk
**Primary users:** 18 support desk staff who serve partner libraries that receive shipped publications

### Situation

Partner libraries contact the desk about shipments that have not arrived, items that were damaged, and questions about program rules such as claim windows and selection changes. Resolving one inquiry touches four places:

1. The **Program Guidance Repository**, an external content management system holding 15 years of program handbooks, FAQs, and selection guidance. It changes monthly.
2. The **Shipment Portal**, a commercially hosted SaaS service used by the shipping contractor. It shows carrier scans and delivery status, updated hourly, and exposes a REST API.
3. **SharePoint**, which holds the desk's internal procedures and its escalation policy, including the rule that a missing shipment older than the claim window must be logged as a case.
4. The **Case Management System**, an external ticketing system with a REST API offering GetCase, CreateCase, and AddNote.

Staff describe the work as "four tabs and a prayer."

### What users want to ask

> "Library 0417 is asking why shipment S-88231 has not arrived. Check the shipment status, find the applicable claim policy, draft a response to the library, open a case if we are past the claim window, and notify the regional coordinator."

> "What does the guidance say about a library changing its selection profile mid-year?"

> "Which of my open cases involve shipments that now show as delivered?"

### Information and system facts

| Fact | Detail |
|---|---|
| Program guidance | 15 years, about 4,000 documents, monthly updates, needs strong search |
| Shipment data | Hourly updates, must remain authoritative in the portal, commercially hosted outside the government cloud |
| Procedures and escalation policy | SharePoint, already visible to Copilot for the desk staff |
| Case system | External, REST API, per-user authentication, every case must show which staff member created it |
| Notifications | Regional coordinators work in Teams |

### Operations involved

- Retrieve shipment status (read, live)
- Retrieve program guidance (read, stable)
- Apply the escalation policy (reason)
- Draft a response (generate)
- Create a case (write, with consequence)
- Notify the coordinator (communication)

### Identity and permission facts

- Desk staff authenticate to the case system individually.
- The Shipment Portal offers either per-user OAuth or a read-only service credential. The shipping contractor prefers the service credential because provisioning 18 user accounts costs them money.

### Governance and constraints

- Case creation must be confirmed by the staff member. Nobody wants a case opened because the model misread a date.
- Shipment IDs and library identifiers will be sent to a commercial SaaS API. The privacy office wants to know exactly what leaves the tenant.
- Library contact details are business contact information, not sensitive personal data, but the desk still treats them carefully.

### Complications to consider

- One proposal is to build a single connector "for everything."
- Another proposal is to skip the guidance repository and "just upload the handbooks to the agent."
- The contractor's preference for a service credential has to be reconciled with the identity criterion.

### Your table's task

1. Classify the request and choose a pattern.
2. Assign each of the six operations to a component. Explain why a single connector is the wrong shape.
3. Decide how live shipment status should reach Copilot and state the requirement that drove the choice.
4. Resolve the identity question for the Shipment Portal and for the case system, and explain why the answers may differ.
5. Name what the privacy office must review before this ships, and where the human checkpoints sit.

---

## Scenario 6 - Connect the Secure Production Line?

**Business unit:** Secure Document Production Unit
**Requester:** The production manager, on behalf of 20 managers who meet weekly

### Situation

The unit produces secure credentials on an isolated production line. Production tracking runs on **SDPU-Track**, a system inside a network enclave with no internet egress. Access requires a named account and a hardware token, and the system's Authority to Operate restricts data from leaving the enclave boundary without the system owner's approval.

The production manager has submitted a request: "Connect SDPU-Track to Copilot so my team can ask about batch status and defect rates instead of waiting for the weekly deck."

When the integration team asked what the managers actually need, the answer was: batch completion status by line and week, defect rate trends by category, and comparison against the prior quarter. They review this in a weekly meeting and occasionally between meetings.

### What users want to ask

> "What was the defect rate by category on Line 3 last week, and how does it compare with the quarter average?"

> "Which batches completed ahead of schedule this month?"

> "Summarize the top three quality trends I should raise at the weekly review."

### Information and system facts

| Fact | Detail |
|---|---|
| Data content | Batch records include serialized credential numbers, fields that link to personal data held elsewhere, and security-sensitive process parameters |
| Aggregates | Weekly aggregate reports (counts, rates, trends) contain none of the sensitive fields |
| Network | The enclave has no outbound internet connectivity. Nothing inside it can reach an endpoint on the Microsoft cloud, and nothing on the Microsoft cloud can reach it |
| Identity | Named accounts with hardware tokens, managed separately from Entra ID |
| Authorization | The system owner and Information System Security Officer must approve any new interface. A boundary change requires Authorizing Official sign-off |

### Operations involved

None requested. Read and summarize only.

### Identity and permission facts

- The 20 managers have Entra ID accounts and Copilot licenses.
- Only 8 of the 20 hold SDPU-Track accounts. The others receive the weekly deck.

### Governance and constraints

- Serialized credential numbers and personal-data linkage fields must not leave the enclave.
- The Authority to Operate does not currently include any connection to Microsoft 365 services.
- The privacy office and the records office both have equities.

### Complications to consider

- A vendor has offered to "build a Copilot connector in two weeks."
- A team member argues for a federated connector "because it does not copy the data anywhere."
- The production manager is frustrated and says the weekly deck is already emailed around, "so the data leaves the enclave anyway."

### Your table's task

1. Classify the request. Then decide the first question you must answer before choosing any technology.
2. Evaluate the synced connector and federated connector proposals against the facts. Explain specifically what each one would require and what each one would violate.
3. Recommend a design that meets the managers' stated need without moving the sensitive fields, and identify which component of the extension menu it uses.
4. Name who must approve your design and what they must approve.
5. State what would have to change before a direct connection could be reconsidered, and which connector model you would evaluate first at that point.

---

## Scenario 7 - The Nightly Export Debate

**Business unit:** Print Procurement Operations
**Primary users:** 85 contract specialists and 6 team leads

### Situation

The **Print Procurement Tracking System (PPTS)** tracks solicitations, bids, awards, vendor assignments, and delivery commitments for work placed with commercial printers. It holds about 60,000 historical records and adds about 8,000 per year. Bid status changes during the day. Award decisions land on specific award days.

For the last two years an analyst has exported a PPTS spreadsheet to SharePoint every night at 2 a.m. so that Copilot can answer questions about it. Specialists say the spreadsheet is stale by midday, but when pressed they agree that "as of this morning" is fine for about 90 percent of questions. The remaining 10 percent are award-day questions where the answer changes hour by hour.

### What users want to ask

> "Which solicitations for my agency customers are awaiting award this week?"

> "Show me the last three years of awards to vendor V-2210 for perfect-bound work and the typical lead time."

> "Has the award for solicitation 26-4471 posted yet?"

### Information and system facts

| Fact | Detail |
|---|---|
| Volume | 60,000 historical, 8,000 per year |
| Change rate | Most records: daily is fine. Award-day records: hourly |
| Interface | PPTS exposes a REST API with an incremental change feed (changes since a timestamp) and Entra ID based authentication |
| Sensitive records | During source selection, certain records are restricted to the evaluation team. The nightly spreadsheet drops these restrictions entirely because a spreadsheet has no record-level permissions |

### Operations involved

None. Search, filter, compare, and summarize.

### Identity and permission facts

- PPTS enforces record-level access. The evaluation team for a solicitation is defined in PPTS, not in Entra ID.
- The spreadsheet is readable by everyone with access to the SharePoint site, which is currently all 91 users.

### Governance and constraints

- Source-selection sensitive information must not be readable by anyone outside the evaluation team.
- The procurement lead has flagged the spreadsheet as an audit finding waiting to happen.
- Leadership wants the spreadsheet retired.
- The search team wants historical procurement content to appear in Microsoft Search for analysis and reporting.

### Complications to consider

- The search team's position: "Everything in one index."
- A specialist's position: "Award day is all that matters. Go real time or do not bother."
- The analyst who runs the export would like to stop running the export.

### Your table's task

1. Classify the request and choose a pattern.
2. Pick a freshness model and state the exact requirement that justifies it. Your answer must address both the 90 percent and the 10 percent.
3. Explain how record-level restrictions are restored in your design, given that the evaluation team is defined in PPTS and not in Entra ID.
4. Decide whether the spreadsheet can be retired on day one, and if not, what gates its retirement.
5. Identify what a phased design would look like if leadership funds only one component this year.

---

## Scenario 8 - Watch It for Me While I Sleep

**Business unit:** Program Office - Production Oversight
**Primary users:** 12 program managers

### Situation

A program manager has described what she wants in one breath:

> "Every morning at 6 a.m., I want Copilot to look at the tracking system, find every job that slipped past its requested completion date overnight, compare each one with the escalation policy, post a summary to our Teams channel, and have draft escalations ready for me to approve when I sit down. And during the day I want to ask it questions about any job."

The tracking system is the same **PJTS** from Scenario 2, with its REST API and read-only MCP server. PJTS also exposes a CreateEscalation API operation that is not part of the MCP server. The escalation policy lives in SharePoint. The Teams channel already exists.

### What users want to ask

> (Scheduled, no user present) Detect overnight slips, apply policy, post summary, stage escalations.

> (On demand) "Why is FP-2026-1048 at risk, and does it meet the escalation criteria?"

> (On demand) "Submit the escalation for FP-2026-1048."

### Information and system facts

| Fact | Detail |
|---|---|
| Detection window | Once per day at 6 a.m., plus on demand |
| Policy | SharePoint document, updated quarterly |
| Read access | PJTS API and MCP server (read-only tools) |
| Write access | CreateEscalation API operation, not currently exposed through MCP |
| Notification | Existing Teams channel |

### Operations involved

- Detect slipped jobs on a schedule (read, unattended)
- Evaluate against policy (reason)
- Post a summary (communication, unattended)
- Stage draft escalations (generate)
- Approve and create escalations (write, human decision)
- Answer ad hoc questions (read, interactive)

### Identity and permission facts

- The scheduled run happens when nobody is signed in. It cannot use an individual's interactive identity.
- Escalations must be created in the name of the program manager who approved them.

### Governance and constraints

- No escalation may be created without a named program manager's approval.
- The program office wants the design to work in the GCC tenant as it exists today, not as it may exist next year.

### Complications to consider

- A consultant recommends "a Copilot Studio autonomous agent with a scheduled trigger."
- A program manager says "just email the summary, we do not need any of this."
- The PJTS team asks whether they should add CreateEscalation to the MCP server.

### Your table's task

1. Separate the scheduled part of the request from the conversational part, and classify each.
2. Choose the components for each part. Identify the GCC constraint that rules out the consultant's proposal and name what replaces it.
3. Explain how identity works for the unattended run versus the approval and creation step.
4. Advise the PJTS team on whether CreateEscalation belongs in the MCP server, and why or why not, given what federated connectors can do today.
5. Place the human checkpoint and describe what happens at 6 a.m. if PJTS is unreachable.

---

## Appendix A - Blank worksheet

Copy this table for your notes if you prefer a clean sheet.

| Layer | Decision |
|---|---|
| Table number and scenario | |
| Classification | |
| Outcome | |
| Knowledge + Source + Freshness | |
| Skill | |
| Identity + Control | |
| Experience | |
| Pattern | |
| Components | |
| Knowledge justification | |
| Freshness justification | |
| Action justification | |
| Identity justification | |
| Governance justification | |
| Human checkpoints | |
| Failure handling | |
| Deciding requirement | |
| Biggest risk | |

## Appendix B - Quick reminders

- Connectors expand what Copilot can know. Actions expand what an agent can do. Workflows connect those capabilities into business outcomes.
- Synced: bring the knowledge closer to Copilot. Federated: bring Copilot to the knowledge.
- Connector = information. Action = capability.
- Not every step should be autonomous merely because it can be automated.
- Extending Copilot extends the security boundary.
