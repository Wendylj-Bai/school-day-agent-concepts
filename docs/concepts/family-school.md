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
- **How the AI could help:** the Evidence Agent finds approved information with its source and date. The Coordination Agent gives an answer supported by those sources or prepares a question for an educator rather than guessing.
- **Why agents:** the workflow must interpret a request, compare several authorized records, recognize uncertainty, and choose between answering and handing control to an educator.

**Opportunity hypothesis:** schools are already willing to use technology for communication. The unmet need may be a more reliable and coordinated approach that fits the school's actual process, rather than another disconnected app. The research supports technology adoption and problems with fragmented tools; it does not yet prove that schools want this specific platform.

## Intended value

- **Parent:** review authorized school updates and teacher-provided performance information, then ask a focused question or coordinate follow-up.
- **Student:** see upcoming responsibilities and receive consistent support from home and school.
- **Teacher and adviser:** share an approved update once, answer clearer questions, and retain authority over official records and guidance.

## What the AI agents would do

For an authorized family, the Evidence Agent retrieves approved notes, assignments, projects, events, and educator-provided results. The Coordination Agent uses those verified facts to answer a routine question, highlight a teacher-marked area needing attention, or prepare a focused follow-up for a teacher or adviser.

Fixed reminders work for uncomplicated updates. The agents earn their place when a request requires checking several authorized sources, distinguishing information from a need for attention, and routing consequential guidance to an educator rather than inventing an answer.

## Normal flow and exception / handoff

Normal: family opens the hub or asks a question → the app checks permission → the Evidence Agent finds approved school information → the Coordination Agent decides whether it can answer → privacy and sources are checked → the family receives an answer or next step.

Exception: if information is missing, sensitive, or needs educational judgment, the Coordination Agent holds the answer and prepares a teacher or adviser follow-up. The educator's clarification returns to the Coordination Agent and becomes the authoritative source; the diagram does not claim this handoff is automatic.

## Plain-English diagram walkthrough

1. A parent or student asks about an assignment, event, educator-provided result, or teacher-marked review need.
2. Application code checks identity and record-level permission before an agent sees information.
3. The Evidence Agent retrieves approved facts with their source and date.
4. The Coordination Agent provides a cited routine answer or prepares a focused clarification request when information conflicts, is missing, or needs judgment.
5. A teacher or adviser provides official guidance. The reply returns to the Coordination Agent as the authoritative source, and the answer passes through a final privacy and source check before the family receives a clear next step. The AI does not change records or speak for the educator.

Not every diagram box is an AI agent. Some steps are fixed rules in the application, approved information sources, or decisions made by people with authority.

## Suggested buildathon-sized first prototype (suggested / not implemented)

None of these technical options has been built or connected yet. They are suggestions for the group, not requirements or claims that the system already works.

- **Two limited roles** - an Evidence Agent finds permitted school information; a Coordination Agent prepares a source-supported answer or educator follow-up. Keep two agents only if testing shows that they work better than one simpler flow.
- **LangGraph (possible workflow manager)** - could manage the steps, saved information, retry limits, and handoff to an educator.
- **Local MCP tools (controlled connections)** - could give the agents limited access to fictional school records through developer tools such as `get_authorized_school_updates` and `create_educator_followup`. The agents gather information and prepare a review item; they do not change school records or send messages as a teacher.
- **Application-enforced boundaries** - the app/server authenticates each person and applies student and record-level permissions before the agents see data. Never accept a model-supplied student ID as authorization. No invented grades, private AI assessment, record changes, or messages sent on an educator's behalf without approval.
- **Base44 (optional screen builder)** - could create a simple parent view and teacher review list. A basic custom screen would also work.
- **Antigravity (development tool)** - can help us build and test the prototype; it would not be one of the agents used by families.
- **ArgosX** - run the required security scan on the eventual build. Log tool calls and handoffs; test conflicting notices and denied access.

## Example demo using fictional data

Uses fictional parents, families, and notices only.

1. A fictional parent reviews a project deadline, school event, and teacher-provided test result.
2. The application verifies permission before retrieving fictional school information.
3. The parent asks which lesson needs attention; the system surfaces only the teacher-marked topic and source, not an AI diagnosis.
4. The Coordination Agent prepares a focused educator follow-up, and the teacher or adviser provides the authorized next step.

## Research validation and evidence limits

**Current judgment:** published research supports the underlying communication problem and shows that some targeted parent-information interventions can affect specific outcomes. It does not prove demand for this coordinator, that generative AI is necessary, or that the proposed two-agent design will save educators time.

- A Gallup survey of 808 US K–12 parents (conducted December 2024, published April 2025) found that 42% said their school had shared little or nothing about the goals for their child's math learning. High-school parents reported less frequent lesson communication than elementary-school parents. This supports a need for clearer learning information, but it covers math communication rather than every school message.
- A separate 2023 Gallup and Learning Heroes survey found that 88% of parents believed their child was at or above grade level in reading and 89% believed the same for math. Gallup reported a clear difference between those beliefs and other achievement measures. This supports the need for clearer explanations of student progress, but it does not show that an AI coordinator is the best solution.
- OECD's TALIS 2024 results show that full-time lower-secondary teachers spend an average of 1.8 hours per week communicating and cooperating with parents or guardians. Around seven in ten teachers also reported using digital tools for parent communication "quite a bit" or "a lot." This shows that family communication is a regular part of teacher workload, though the international average may not describe every US school.
- A 2026 peer-reviewed review brought together 51 studies of parents' experiences with technology-based school communication. Parents valued speed and convenience but also reported overcommunication, access and cultural barriers, and privacy concerns. This supports the concern that digital communication can help while still creating friction.
- A 2025 North American survey funded in partnership with school-platform vendor Edsby included 109 teachers, 125 parents, and 58 curriculum leaders. Fifty-four percent of the curriculum leaders reported that their schools used 10 to 15 officially approved education apps. Teachers and parents reported more difficulty with the multi-app environment than administrators expected. This directly supports the fragmentation problem, but the small sample and vendor sponsorship mean it should remain supporting evidence rather than the main proof.
- An Institute of Education Sciences evaluation involving about 26,000 elementary students found that adaptive parent text messages reduced chronic absence but did not improve reading or mathematics achievement after one school year. This shows that communication can affect a specific outcome without proving broad academic impact.
- Existing products already answer school questions. Therefore, the useful hypothesis is narrower: permissioned, student-specific reconciliation of approved sources, explicit conflict handling, and an educator clarification loop.

**Stronger problem framing:** the opportunity is not to persuade schools to use technology. It is to test whether administrators, teachers, families, and students need a better-coordinated communication layer that fits their process. Families may struggle to determine which approved information is current, what action is required, and when an educator must clarify the situation. If useful information was never recorded, the coordinator can request clarification but cannot manufacture the missing answer.

**Smallest credible test:** use one fictional parent, student, class, revised deadline, and educator review queue. Plant an older notice that conflicts with a newer authoritative record. Compare the prototype with ordinary portal or message search on correct answers, time to find information, unsupported statements, clarification usefulness, and educator review effort.

**What would weaken the concept:** families already find reliable answers quickly, approved student-scoped access is impractical, or the workflow creates more educator review and data-entry work than it removes.

### Research sources

- [Gallup: School-to-Family Outreach on Math Varies by Grade Level](https://news.gallup.com/poll/658619/school-family-outreach-math-varies-grade-level.aspx), April 23, 2025.
- [Gallup: Should Parents Ask More Questions When Child Receives B's?](https://news.gallup.com/opinion/gallup/513947/parents-ask-questions-child-receives.aspx), November 14, 2023.
- [OECD: Professional Relationships in School Communities, TALIS 2024](https://www.oecd.org/en/publications/results-from-talis-2024_90df6235-en/full-report/professional-relationships-in-school-communities_b6ddef33.html), 2025.
- [Review of Education: Parents' Perspectives of Technology-Mediated Parent-School Communication](https://doi.org/10.1002/rev3.70137), 2026.
- [Cornerstone Communications and Edsby: App Overload](https://cornerstonepr.net/wp-content/uploads/2025/03/AppOverloadReport_bg.pdf.pdf), 2025.
- [Institute of Education Sciences: Can Texting Parents Improve Attendance in Elementary School?](https://ies.ed.gov/use-work/resource-library/report/evaluation-report/can-texting-parents-improve-attendance-elementary-school-test-adaptive-messaging-strategy), September 2020.

## Measures

Source accuracy; unauthorized-access denials; unsupported inferences blocked; useful educator follow-up requests; and educator review time. Compare against the existing notebook, text, or portal workflow; do not claim measured outcomes from a scripted demo.

## Assumptions / questions

Which communication problems remain after existing school portals, which records families may access, who controls permissions, and what must always go to a teacher or adviser.

## Links

- [HTML concept brief](family-school.html)
- [Interactive workflow diagram](../diagrams/family-school.html)
- [Concept homepage](../index.html)
- [Study Buddy comparison](study-buddy.md)
