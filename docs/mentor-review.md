# Team 4 Mentor Review: Two Agentic AI Directions

Short review prepared for mentor guidance. These are working hypotheses, not final team selections, implemented products, or claims of measured impact.

## Concept 1: School-Guided Learning Support

### The shared problem

Students already use general AI and other resources for schoolwork, but support may not follow the teacher's curriculum, may reveal answers instead of teaching, and may give parents and educators little appropriate visibility into the learner's progress. Students may also struggle to plan for an exam or find available academic support.

### Three team contributions being consolidated

1. **Personalized Study Buddy** - reviews a practice attempt, chooses a teacher-approved hint, asks a fresh question, adjusts once when the learner remains stuck, and uses a no-hint check before producing role-appropriate progress summaries. [Review the detailed public brief](concepts/study-buddy.html).
2. **Teacher's Assistant AI** - lets a teacher set an AI-use level and upload a rubric. Three proposed agents coach without rewriting, record assignment-specific drafts and AI interactions, and flag process-to-final-work differences for teacher review. The teacher makes every final decision. [View the original team submission (PDF)](team-ideas/teachers-assistant-ai.pdf).
3. **StudyLadder** - starts with a student's exam date, goal, availability, and budget. It proposes a study plan that checks free campus support first, study groups second, and paid tutors last. The broader plan also includes tutor matching, tutor-reviewed live quizzes, and anonymized demand insights for campuses. [View the original team submission (PDF)](team-ideas/studyladder-project-plan.pdf).

### Consolidated four-week demonstration

A teacher sets one approved learning goal, content source, and AI-use boundary. A fictional student enters an exam or assignment goal, receives a short plan, and works through one guided practice activity. The agent gives questions, explanations, and hints without completing the work. A no-hint check records observable progress. The learner sees the next task, an authorized parent sees a high-level status, and the teacher sees the learning evidence and decides whether follow-up or mastery confirmation is appropriate.

### Keep outside the first prototype

Tutor marketplace, payments, campus-wide demand forecasting, full parent and teacher portals, automated misconduct judgments, class analytics, and unnecessary multi-agent complexity.

### Mentor guidance requested

- Is the combined problem still narrow enough for four weeks?
- Which learner age, subject, and single skill should the demonstration use?
- Is the teacher-boundary and progress-accountability layer more valuable than a simpler tutoring flow?
- What evidence or user validation should we gather first?

## Concept 2: Family-School Communication Coordinator

### The problem

Families may receive school information through separate notices, emails, messages, calendars, and verbal updates. Busy parents can miss changes or encounter incomplete or apparently conflicting details, while educators spend time repeating information or correcting misunderstandings.

### Proposed agentic response

The system checks the family's permission, retrieves only approved school information, compares sources and dates, then provides a cited answer when the evidence is clear. If information is missing or conflicting, it does not guess; it prepares a clarification request for an authorized educator. [Review the detailed public brief](concepts/family-school.html).

### Consolidated four-week demonstration

A fictional parent receives two school notices with different event times. The agent retrieves the approved notices, identifies the conflict, explains what is confirmed, cites both sources, and sends the unresolved question to an educator. After the educator confirms the correct information, the family receives a clear response and the clarification is recorded.

### Why this is a strong four-week candidate

- **Documented problem context:** published evidence and lived school-community experience support that families and educators face fragmented communication, platform overload, unclear information, and response pressure. This validates the problem context, not demand for our exact solution.
- **Clear problem-to-solution fit:** the proposed agent retrieves approved information, reconciles sources, explains what is confirmed, and asks an educator when the evidence is incomplete or conflicting.
- **Small, visible demonstration:** one parent question, two conflicting notices, one clarification request, and one educator-confirmed answer form a complete end-to-end story.
- **Practical build scope:** the demonstration can use fictional notices and fixed permissions without integrating real student records or replacing an existing school platform.
- **Defensible agentic behavior:** the next action depends on the retrieved evidence. The agent can answer, identify uncertainty, or request human clarification while fixed application rules control access and privacy.
- **Clear four-week delivery path:** the team can build and test the core communication loop first, then treat broader integrations and communication channels as future possibilities.
- **Human authority remains clear:** educators confirm unresolved information, and the agent never invents school policy or send unapproved decisions.

**Evidence boundary:** current research supports the underlying communication problem. The team still needs current parent and educator feedback to establish frequency, priority, adoption, and whether this proposed workflow is preferable to improving existing tools.

### Keep outside the first prototype

Replacing the school's existing communication system, sending unsupervised mass messages, integrating real student records, collecting real family data, or attempting every communication channel at once.

### Mentor guidance requested

- Is conflicting or unclear school information a sufficiently specific starting problem?
- Who should be the first target user: parent, teacher, or school administrator?
- What evidence should establish frequency and remaining pain after existing school platforms?
- Is this workflow sufficiently agentic compared with a simpler search or messaging feature?

## Evidence so far

These sources show that the problems exist. They do not prove that either idea will work or that people will use it.

### Concept 1: Learning support

- **Mathematics support need:** the 2024 Nation's Report Card found that 24% of US fourth-grade students performed below NAEP Basic in mathematics, while 39% performed at or above NAEP Proficient. This documents uneven mathematics performance, not a universal need for an AI tutor. [Source: Nation's Report Card, 2024](https://www.nationsreportcard.gov/reports/mathematics/2024/g4_8/?grade=4).
- **Existing student AI use:** a 2026 Pew Research Center survey found that 54% of US teens ages 13 to 17 had used AI chatbots for schoolwork. This supports the need for appropriate boundaries, but does not prove improved learning. [Source: Pew Research Center, 2026](https://www.pewresearch.org/internet/2026/02/24/how-teens-use-and-view-ai/).
- **Human-supported AI:** Stanford's Tutor CoPilot trial involved more than 700 tutors and 1,000 students. Students whose human tutors used the AI support were 4 percentage points more likely to master mathematics topics. This supports keeping educators involved; it did not test a child using an AI tutor independently at home. [Source: Stanford National Student Support Accelerator, 2025](https://nssa.stanford.edu/studies/tutor-copilot-human-ai-approach-scaling-real-time-expertise).

**Evidence boundary:** these sources support the learning problem, existing AI adoption, and the value of human participation. They do not establish that the consolidated learning concept improves outcomes.

### Concept 2: Family-school communication

- **Digital communication friction:** a 2026 peer-reviewed review combined 51 studies of parents' experiences with technology-based school communication. Parents valued speed and convenience but also reported overcommunication, access and cultural barriers, and privacy concerns. [Source: Review of Education, 2026](https://doi.org/10.1002/rev3.70137).
- **Multiple approved applications:** in a 2025 North American survey, 54% of 58 curriculum leaders reported that their schools used 10 to 15 officially approved education applications. The modest, vendor-funded sample makes this supporting rather than conclusive evidence. [Source: Cornerstone and Edsby, 2025](https://cornerstonepr.net/wp-content/uploads/2025/03/AppOverloadReport_bg.pdf.pdf).
- **Recurring teacher workload:** OECD TALIS 2024 results show that full-time lower-secondary teachers spend an average of 1.8 hours per week communicating and cooperating with parents or guardians. The international average may not describe every US school. [Source: OECD TALIS 2024](https://www.oecd.org/en/publications/results-from-talis-2024_90df6235-en/full-report/professional-relationships-in-school-communities_b6ddef33.html).

**Evidence boundary:** these sources establish that communication friction, fragmented tools, and teacher communication work exist. They do not prove demand for this exact coordinator or that it will outperform improvements to existing school systems.

## Decision requested

Which concept gives the team the clearest four-week path to a safe, testable, and defensible agentic AI demonstration? After mentor guidance, the team will choose one concept, confirm the smallest working scope, and assign named owners and deadlines.
