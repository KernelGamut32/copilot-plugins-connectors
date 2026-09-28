# Mini Design Activity - Map the Workflow
## Detailed Activity Definition (Slide 38, Module 3.6)

**Course:** Extend Copilot with Plugins & Connectors (Day 6)
**Module:** 3 - Plugins, Actions & Workflows: Extending What Copilot Can Do
**Slide:** 38 - Mini Design Activity - Map the Workflow
**Scenario thread:** Federal Publication Production Coordination Office (synthetic)
**Tenant context:** Microsoft 365 GCC

---

## 1. Purpose of the Activity

This is the first moment in the course where participants stop watching and start designing. Every prior module handed them a piece of the model:

- Module 1 gave them KNOW vs DO.
- Module 2 gave them synced vs federated connectors.
- Module 3.1 through 3.5 gave them plugins, actions, Power Platform connectors, and the eight-step workflow orchestration pattern.

This activity forces them to combine those pieces on a realistic requirement before Module 4 formalizes the design sequence and before the capstone asks for a full integration canvas.

The activity is intentionally small. Participants are not designing a solution from scratch. They are decomposing one sentence into workflow steps and labeling each step with the correct extensibility element.

### Learning objectives served

| Course objective | How this activity supports it |
|---|---|
| 2 - Distinguish knowledge extension from action extension | Each workflow step must be classified as a knowledge step, an action step, or a control step |
| 4 - Explain how plugins and actions extend declarative agents | Participants must name the specific action an agent would invoke |
| 5 - Recognize the role of Power Platform connectors and workflows | Participants must decide where Power Automate participates and where the agent participates |
| 7 - Identify identity, permissions, and governance considerations | Participants must place human checkpoints and justify them |
| 8 - Design a practical Copilot-enabled integration scenario | This is a compressed rehearsal of the capstone |

---

## 2. Timing Note for the Instructor

The course outline allocates **5 minutes** to Module 3.6. Slide 38 currently reads **"approximately 15 minutes per group, then rapid debrief."** These do not agree.

Two run modes are defined below so the activity works either way:

| Mode | Design time | Debrief | Total | When to use |
|---|---|---|---|---|
| **Compressed** | 4 min | 3 min | 7 min | Outline timing; Module 3 stays on schedule with a small overrun |
| **Extended** | 10 min | 5 min | 15 min | Slide timing; borrow the extra time from Module 3.5 discussion and Module 4.6 |

Recommendation: run **Compressed** unless the class is small (three or fewer groups) and the room is moving quickly. Correct the slide text to match whichever mode you settle on so the slide and the outline agree.

---

## 3. The Scenario (Expanded)

Read this aloud or display it as a handout. The one-sentence version on the slide stays on screen; this expanded version gives participants enough detail to make real design decisions instead of guessing.

### 3.1 Organizational context

The **Federal Publication Production Coordination Office** coordinates the production of agency publications from submission through final delivery. Production work is tracked in the **Publication Production Tracking System (PPTS)**, a line-of-business system that lives outside Microsoft 365. Policy, guidance, and responsibility documents live in a SharePoint site named **Publication Program Office - Policy Library**.

Employees currently switch among Microsoft 365, PPTS, the production support ticketing system, the policy library, an approval process that runs mostly over email, and Teams.

### 3.2 The requirement

Leadership has stated the requirement in one sentence:

> **"When a production job becomes critically overdue, summarize the history, compare it to escalation policy, prepare an escalation, obtain supervisor approval, and route it."**

Participants must turn that sentence into an architecture.

### 3.3 The job at the center of the scenario

Do not reuse FP-2026-1048 from Demo 3. Participants have already seen that job resolved on screen. Give them a fresh record so they must reason rather than recall.

| Field | Value (synthetic) |
|---|---|
| Job ID | FP-2026-1163 |
| Requesting office | Office of Regulatory Affairs |
| Publication type | Agency annual report - print and digital |
| Submission date | 21 business days ago |
| Requested completion date | 6 business days ago |
| Production phase | Proof correction (cycle 3 of a permitted 2) |
| Assigned group | Composition and Proofing Group |
| Risk level | Critical |
| Delay code | PRF-04 - Proof correction cycle limit exceeded |
| Issue status | Open - awaiting corrected source files from requesting office |
| Current owner | Composition Lead |
| Last update | 2 business days ago |
| Escalation status | None |
| Source record URL | ppts.internal/jobs/FP-2026-1163 |

### 3.4 Definitions the office already uses

These two documents exist in the SharePoint policy library. Participants are told they exist and what they say. They are not asked to write policy.

**Job_Risk_Criteria.docx** defines **critically overdue** as either of the following:

1. The job is more than 5 business days past its requested completion date and has at least one open production issue, or
2. The job carries a Critical risk level and the requesting office has a fixed or statutory publication date within 10 business days.

**Publication_Escalation_Policy.docx** states that:

- An escalation is required when a job meets the critically overdue definition and the open issue has not been updated within 3 business days.
- Every escalation must be approved by the Production Supervisor before it is submitted.
- The escalation record must reference the job ID, the delay code, the policy criterion that was met, the responsible group, and a recommended next step.
- The Program Office Liaison and the responsible group must be notified when the escalation is created.
- The outcome of the escalation must be recorded on the job.

### 3.5 Personas

| Persona | Role in the scenario | Name (synthetic) |
|---|---|---|
| Production Coordinator | Monitors jobs, initiates escalations, primary user of the solution | Dana Whitfield |
| Production Supervisor | Approves or rejects escalations | Marcus Bell |
| Program Office Liaison | Represents the requesting office, must be notified | Priya Raman |
| Composition Lead | Owner of the responsible group, must be notified | Tomas Ortega |

### 3.6 Systems and sources available

| System or source | What it holds | Where it lives |
|---|---|---|
| Publication Production Tracking System (PPTS) | Current status, history, delay codes, owners, escalation records | External - REST API with an OpenAPI description |
| Production Support Ticketing System | Historical support tickets, resolution notes | External - large historical archive |
| Publication Program Office - Policy Library | Escalation policy, risk criteria, program office responsibilities, production guidelines | SharePoint (Microsoft 365) |
| Approval process | Supervisor approvals, currently informal over email | Nowhere authoritative today |
| Teams and Outlook | Coordination conversations, notifications | Microsoft 365 |

### 3.7 The Publication Operations API (synthetic)

The PPTS team has published a REST API. Participants may use any of these operations. They may also decide that an operation is unnecessary or that a missing operation should be requested.

| Operation | Type | Description |
|---|---|---|
| GetJob | Read | Returns the current record for a job ID |
| GetJobHistory | Read | Returns the status and comment history for a job ID |
| ListJobsAtRisk | Read | Returns jobs matching risk level and overdue filters |
| CreateEscalation | Write | Creates an escalation record linked to a job |
| AddComment | Write | Adds a comment to a job's history |
| UpdatePriority | Write | Changes the job priority |
| NotifyGroup | Write | Sends a notification to a named production group |

### 3.8 Constraints participants must respect

Display these as ground rules. They are what make the design realistic for a GCC tenant.

1. Microsoft 365 Copilot in this tenant runs in GCC. Design only with capabilities documented as available in GCC, or say explicitly which step would need verification in the tenant.
2. Federated Copilot connectors are read-only. They can search and fetch, they cannot create, update, or delete. Transactional operations must go through a declarative agent action, an API plugin, or a Power Platform connector.
3. API plugins run only as actions inside a declarative agent. They are not enabled directly in Microsoft 365 Copilot.
4. Copilot Studio in GCC does not currently offer triggers or autonomous agents. Anything that must start without a person asking for it needs a different mechanism.
5. No policy may be copied out of SharePoint into the external system. SharePoint stays the source of truth for policy.
6. No escalation may be created without a supervisor decision recorded somewhere auditable.
7. Every step must run under a clear identity. "The system does it" is not an acceptable identity answer.

---

## 4. The Task

Each group produces one completed worksheet.

### 4.1 Step one - decompose the sentence

Break the requirement into discrete steps. The eight-step pattern from slide 37 is the expected decomposition, but groups may merge or split steps if they can justify it.

The reference decomposition is:

1. Identify the problem (the job becomes critically overdue)
2. Retrieve the record and its history
3. Check the situation against escalation policy
4. Generate the escalation request
5. Request human approval
6. Create the escalation record
7. Notify the responsible group and the program office liaison
8. Record the result on the job

### 4.2 Step two - label each step

For every step, the group fills in five columns:

| Column | Question the group must answer |
|---|---|
| **Knowledge source** | What information does this step need, and where does it authoritatively live? Microsoft 365, a synced connector, a federated connector, or an API read? |
| **Agent** | Does a declarative agent perform or coordinate this step, or does something else? |
| **Action** | Which specific operation, if any, is invoked? Name it from the API list or from a Power Platform connector. |
| **Workflow step** | Does this step live inside a Power Automate flow, inside the agent conversation, or in a person's hands? |
| **Human checkpoint** | Does a person confirm, approve, review, or get notified here? If so, who and why? |

### 4.3 Step three - answer three design questions

Below the table, each group writes one line for each of the following:

1. **Trigger:** The requirement says "when a production job becomes critically overdue." What actually detects that moment, given the GCC constraint on triggers?
2. **Identity:** On whose authority does the CreateEscalation call run, and why does that matter?
3. **Failure:** If PPTS is unavailable in the middle of the workflow, what should the user experience be?

---

## 5. Worksheet Template

Print one per group or provide it as a shared OneNote page or a Loop component in the class Teams channel.

```text
GROUP: ______________________     JOB: FP-2026-1163

+---+---------------------------+------------------+---------+----------+---------------+------------------+
| # | Workflow step             | Knowledge source | Agent   | Action   | Workflow step | Human checkpoint |
+---+---------------------------+------------------+---------+----------+---------------+------------------+
| 1 | Identify the problem      |                  |         |          |               |                  |
| 2 | Retrieve record + history |                  |         |          |               |                  |
| 3 | Check against policy      |                  |         |          |               |                  |
| 4 | Generate escalation       |                  |         |          |               |                  |
| 5 | Request human approval    |                  |         |          |               |                  |
| 6 | Create escalation record  |                  |         |          |               |                  |
| 7 | Notify group + liaison    |                  |         |          |               |                  |
| 8 | Record the result         |                  |         |          |               |                  |
+---+---------------------------+------------------+---------+----------+---------------+------------------+

TRIGGER:  How is "becomes critically overdue" detected? ______________________________________

IDENTITY: Whose identity runs CreateEscalation? Why? _________________________________________

FAILURE:  PPTS is down mid-workflow. What does the user see? _________________________________
```

Groups may write in shorthand. A completed row might read:

`3 | Check against policy | SharePoint policy library (M365 native) | Publication Risk Agent reasons | none (read via agent knowledge) | agent conversation | coordinator reviews the agent's policy conclusion`

---

## 6. Facilitation Flow

### Compressed mode (7 minutes)

| Time | Instructor action |
|---|---|
| 0:00 | Display slide 38. Read the requirement sentence aloud once. Hand out the expanded scenario and worksheet. State the two most important constraints: federated connectors are read-only, and Copilot Studio in GCC has no triggers. |
| 0:30 | Say: "You have four minutes. Fill in the eight rows first. If you run out of time, the three questions at the bottom are optional, but the trigger question is the one that separates a good answer from a great one." |
| 0:30 - 4:30 | Circulate. Do not correct. Ask one probing question per group: "What detects step 1?" or "Who approves step 5, and where is that recorded?" |
| 4:30 | Call time. Ask two groups to read their rows for steps 1, 5, and 6 only. Those three rows expose the trigger decision, the approval decision, and the write decision. |
| 5:30 | Run the debrief using the questions in Section 7. |
| 7:00 | Transition to Module 4: "You just did the design sequence by instinct. Module 4 gives you the same sequence as a repeatable method." |

### Extended mode (15 minutes)

| Time | Instructor action |
|---|---|
| 0:00 - 1:00 | Same setup as compressed mode. |
| 1:00 - 11:00 | Groups complete all eight rows and all three questions. At the 6-minute mark, announce: "Check your row 1. If it says the agent detects the problem on its own, revisit constraint 4." |
| 11:00 - 14:00 | Each group presents one row they are proud of and one row they argued about. Limit to 45 seconds per group. |
| 14:00 - 15:00 | Instructor reveals the representative answer (see the companion facilitator answer document) and names the two or three design choices that most groups got right. |

### Group formation

- Three to five people per group.
- Mix roles where possible. A group with one business analyst, one administrator, and one developer will argue productively about identity and approvals.
- If the class is very small, run it as one group with the instructor as scribe.

### Materials

- Slide 38 on screen
- Expanded scenario handout (Sections 3.1 through 3.8 of this document)
- Worksheet (Section 5), printed or as a shared editable page
- Companion document: Slide38_Mini_Design_Activity_Facilitator_Answer.md (instructor only)

---

## 7. Debrief Questions

Ask these in order. Each one targets a specific misconception.

1. **"Who said the agent detects the overdue job by itself?"**
   Targets the trigger misconception. Copilot Studio triggers are not available in GCC. A scheduled Power Automate cloud flow, a user-initiated prompt, or a notification that invites the coordinator to engage the agent are all valid. An agent that "watches" PPTS is not.

2. **"Where did you put the policy check, and did anything copy policy text into PPTS?"**
   Targets the source-of-truth principle from Module 2.1. Policy stays in SharePoint. The agent reads it as knowledge. Nothing copies it.

3. **"At which row did this stop being a knowledge problem and become an action problem?"**
   Same question as Demo 3. The answer is row 6, or row 5 if the group treats starting an approval as an action. Rows 1 through 4 are read and reason. Rows 6 through 8 are write.

4. **"Whose identity created the escalation?"**
   Targets identity. Acceptable answers: the coordinator's identity via the agent's action with a confirmation prompt, or a flow connection with the supervisor's approval decision recorded as the authorization. Unacceptable: "a service account, so no one has to log in."

5. **"What did you do with the read-only rule for federated connectors?"**
   Targets the September 2026 currency point. Groups that used a federated connector for reads and an agent action for writes have it right. Groups that used a federated connector to create the escalation need the correction.

6. **"How does Dana know which system supplied each piece of the answer?"**
   Targets verification. The agent should cite the PPTS source record URL for operational facts and the SharePoint document for policy facts.

---

## 8. Stretch Questions for Fast Groups

Offer any of these to a group that finishes early.

- Row 2 needs history. Would you retrieve it through a federated connector or through the GetJobHistory action? What changes if the history is 400 comments long?
- The Production Support Ticketing System holds ten years of tickets. Does this workflow need it at all? If yes, synced or federated, and why?
- Marcus is out of office. What does the approval step do, and where is that rule encoded?
- Dana asks the agent to "escalate all critically overdue jobs at once." Which of your rows becomes risky, and what checkpoint would you add?
- The requesting office, not the production group, caused the delay (they owe corrected source files). Does your notification step change?

---

## 9. Common Mistakes to Watch For

| Mistake | What it looks like on the worksheet | Redirect |
|---|---|---|
| Autonomous detection | Row 1 says "agent monitors PPTS" | Constraint 4. Ask what starts the process in GCC today. |
| Write through a federated connector | Row 6 says "federated connector creates escalation" | Constraint 2. Federated connectors are read-only. |
| Policy copied into the external system | Row 3 says "PPTS holds escalation rules" | Constraint 5. SharePoint is the policy source of truth. |
| No auditable approval | Row 5 says "supervisor says yes in Teams" | Constraint 6. Where is the decision recorded? Power Automate approvals produce a record. |
| Everything inside the agent | Rows 5 through 8 all say "agent" with no workflow | Ask what happens when the supervisor takes two days to respond. Conversations do not wait two days. Flows do. |
| Everything inside Power Automate | Rows 2 through 4 all say "flow" with no agent | Ask who reads the policy and reasons about whether the criterion is met. That is the agent's job. |
| Missing identity | Identity question says "system account" | Constraint 7. Ask who is accountable for the escalation. |
| Silent failure | Failure question says "retry later" with no user message | The agent must tell Dana the source was unavailable rather than answer from stale or missing data. |

---

## 10. Bridge to Module 4

Close with one sentence that connects the activity to the next module:

> "You just answered eight design questions by instinct. Module 4 turns that instinct into a sequence you can run on any requirement: outcome, knowledge, source, freshness, skill, identity, control, experience."

Then advance to slide 39.

---

## Appendix - Source Alignment (Instructor Reference)

The constraints in Section 3.8 align to current Microsoft Learn documentation as of September 2026:

- Federated Copilot connectors are read-only; write, update, and delete support begins rolling out in early October 2026 for worldwide standard multi-tenant. Treat write-back through federated connectors as future functionality for this course and do not demonstrate it. (Microsoft Learn: Federated connectors overview; Copilot connectors overview)
- API plugins and MCP plugins are supported only as actions within declarative agents and are not enabled directly in Microsoft 365 Copilot. Copilot asks the user before sending data to a plugin. (Microsoft Learn: Plugins for Microsoft 365 Copilot; Confirmation prompts)
- Declarative agents with actions are available in GCC, with availability extended to GCC High and DoD in May 2026. (Microsoft 365 Message Center)
- Copilot Studio in GCC: generative orchestration and the Teams and Microsoft 365 Copilot channel are available; triggers and autonomous agents are not. Third-party integration is provided through Power Automate cloud flows and connectors. (Microsoft Learn: Copilot Studio for US Government customers)
- Power Platform connectors wrap APIs for use by Copilot Studio, Power Automate, Power Apps, and Azure Logic Apps; they are distinct from Microsoft 365 Copilot connectors. (Microsoft Learn: Copilot extensibility FAQ)
- The Power Automate Approvals connector is a standard connector. Confirm it is enabled and functioning in the GPO training tenant before relying on it in a demo.
