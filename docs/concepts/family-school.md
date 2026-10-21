# Family-School Communication Coordinator · Concept Brief

Working hypothesis for team discussion, not a validated school need or a built product. Faithful summary of the existing [HTML brief](family-school.html) and [workflow diagram](../diagrams/family-school.html).

## Value proposition (one sentence)

Give parents and students one authorized place to review important school information, ask questions, and coordinate follow-up with teachers or advisers.

## Plausible recurring problem

This concept is informed by my own experience as a parent navigating school communication during my children's primary-school years in the Philippines. I later served for two years as PTA president and then as a school board member, which gave me another view of communication between families and schools. More recently, I observed a parent friend in the United States navigating similar communication for her children.

Some families may still need to piece together handwritten notebook entries, individual text messages, emails, assignments, projects, events, results, or lessons that need follow-up. These experiences provide a credible starting point, but they are not evidence that every school has the same problem or current validation across US primary schools.

## Problem-to-solution map

- **Core problem:** parents, students, and educators may not have one reliable and authorized place for school information, questions, and follow-up.
- **Pain experienced:** messages can be missed, repeated, misunderstood, or contradicted. Families piece together updates while educators answer repeated questions and correct misunderstandings.
- **Agentic response:** the Evidence Agent retrieves approved information with its source and date. The Coordination Agent gives a cited routine answer or prepares an educator clarification request rather than guessing.
- **Why agents:** the workflow must interpret a request, compare several authorized records, recognize uncertainty, and choose between answering and handing control to an educator.

## Intended value

- **Parent:** review authorized school updates and teacher-provided performance information, then ask a focused question or coordinate follow-up.
- **Student:** see upcoming responsibilities and receive consistent support from home and school.
- **Teacher and adviser:** share an approved update once, answer clearer questions, and retain authority over official records and guidance.

## Agent's job and why agentic

For an authorized family, the Evidence Agent retrieves approved notes, assignments, projects, events, and educator-provided results. The Coordination Agent uses those verified facts to answer a routine question, highlight a teacher-marked area needing attention, or prepare a focused follow-up for a teacher or adviser.

Fixed reminders work for uncomplicated updates. The agents earn their place when a request requires checking several authorized sources, distinguishing information from a need for attention, and routing consequential guidance to an educator rather than inventing an answer.

## Normal flow and exception / handoff

Normal: family opens hub or asks a question → app-enforced access check → approved school-information lookup → request routing → privacy and citation check → sourced answer or next step.

Exception: if information is missing, sensitive, or needs educational judgment, the agent holds the answer and prepares a teacher or adviser follow-up. The educator's response becomes the authoritative source; the diagram does not claim this handoff is automatic.

## Plain-English diagram walkthrough

1. A parent or student asks about an assignment, event, educator-provided result, or teacher-marked review need.
2. Application code checks identity and record-level permission before an agent sees information.
3. The Evidence Agent retrieves approved facts with their source and date.
4. The Coordination Agent provides a cited routine answer or prepares a focused clarification request when information conflicts, is missing, or needs judgment.
5. A teacher or adviser provides official guidance. The AI does not change records or speak for the educator.

Not every diagram box is an AI agent. The flow also includes deterministic application controls, approved information tools, and people with authority.

## Suggested buildathon-sized MVP (suggested / not implemented)

No part of this stack is built or integrated yet; a stack to propose to the group, not a requirement or a claim that these integrations already work.

- **Two bounded roles** - an Evidence Agent retrieves permitted school information; a Coordination Agent creates a sourced answer or educator follow-up. Retain the split only if it adds testable value over a simpler flow.
- **LangGraph (workflow/orchestration option)** - keep the request, access scope, evidence packet, citations, and decision in state; route retrieve → classify → coordinate → verify; pause when an educator must review.
- **Local MCP tools (illustrative names)** - a local MCP server backed by synthetic records exposing `get_authorized_school_updates` and `create_educator_followup`. The agents gather information and prepare a review item; they do not modify school records or publish teacher messages.
- **Application-enforced boundaries** - the app/server authenticates each person and applies student and record-level permissions before the agents see data. Never accept a model-supplied student ID as authorization. No invented grades, private AI assessment, record changes, or messages sent on an educator's behalf without approval.
- **Base44 (optional UI)** - a small parent view and teacher review queue could be prototyped in Base44 if integration is viable; a simple custom UI is also fine.
- **Antigravity (development-only)** - can help develop the prototype; it is not a runtime agent.
- **ArgosX** - run the required security scan on the eventual build. Log tool calls and handoffs; test conflicting notices and denied access.

## Illustrative synthetic-data demo

Uses fictional parents, families, and notices only.

1. A fictional parent reviews a project deadline, school event, and teacher-provided test result.
2. The application verifies permitted access before retrieving synthetic school information.
3. The parent asks which lesson needs attention; the system surfaces only the teacher-marked topic and source, not an AI diagnosis.
4. The Coordination Agent prepares a focused educator follow-up, and the teacher or adviser provides the authorized next step.

## Measures

Source accuracy; unauthorized-access denials; unsupported inferences blocked; useful educator follow-up requests; and educator review time. Compare against the existing notebook, text, or portal workflow; do not claim measured outcomes from a scripted demo.

## Assumptions / questions

Which communication problems remain after existing school portals, which records families may access, who controls permissions, and what must always go to a teacher or adviser.

## Links

- [HTML concept brief](family-school.html)
- [Interactive workflow diagram](../diagrams/family-school.html)
- [Concept homepage](../index.html)
- [Study Buddy comparison](study-buddy.md)
