# Personalized Study Buddy · Concept Brief

Working hypothesis for team discussion, not proven learning impact or a built product. Faithful summary of the existing [HTML brief](study-buddy.html) and [workflow diagram](../diagrams/study-buddy.html).

## Value proposition (one sentence)

Help a student move forward after a practice mistake while keeping parents, teachers, and advisers involved in encouragement, content guidance, and follow-up.

## Plausible recurring problem

A child answers 52 − 27 as 35, subtracting the smaller digit from the larger one in each place instead of regrouping. They may keep trying without knowing why their method fails. A static answer key reveals the result, not the misunderstanding; a parent may not know which explanation to try next. The child loses momentum during a recurring study session. This is a plausible scenario, not measured learning data.

## Problem-to-solution map

- **Core problem:** a student may need timely learning support when a teacher or a parent with subject knowledge is unavailable.
- **Pain experienced:** repeated mistakes can become frustration; a generic explanation may not address the misunderstanding, and an unrestricted AI tutor may reveal the answer instead of supporting learning.
- **How the AI could help:** the Learning Review Agent notices a possible learning difficulty from the practice attempts. The Teaching Agent selects a teacher-approved method, presents a new question, and tries another method when the answer check shows that the learner is still struggling.
- **Why agents:** the workflow must observe the attempt, choose a teaching strategy, check whether it worked, adapt within a retry limit, and involve an authorized adult when needed.

## Intended value

- **Student:** get a hint matched to the attempt, practice independently, and ask for help without receiving the answer.
- **Parent:** see a concise, authorized progress and support summary, then encourage practice or help arrange follow-up.
- **Teacher and adviser:** approve learning activities, guide lesson review, and receive a useful signal when persistent difficulty needs human attention.

## What the AI agents would do

The agents consider where the learner may be confused, choose a teacher-approved visual or exercise, give a hint instead of the answer, then ask a new practice question that fixed rules check again. If the answer is still incorrect, the Teaching Agent tries one different approved teaching method. Once the learner answers correctly, a short mock quiz without hints checks whether they can work independently. After the mock quiz, or when the retry limit is reached, the system suggests a parent or teacher check-in.

A fixed quiz cannot change its teaching method after an unsuccessful explanation. A general chatbot may give away the homework answer. The key feature is a controlled cycle that reviews the attempt, chooses a method, checks progress, and adjusts. Voice and avatars are optional.

## Normal flow and exception / handoff

Normal: learner attempt → answer check → identify a possible learning difficulty → choose an approved activity → hint → new practice question → new answer check → mock quiz without hints → support summary → next practice steps.

Exception: if the new answer is still incorrect, Try Another Method sends the Teaching Agent back with one other approved approach. When the retry limit is reached, it asks for human help. The diagram shows this alternative path, not an automatic diagnosis of a child.

## Practice and mock-test mode

The Study Buddy can also generate a short quiz or mock test from a teacher-approved question bank for test preparation. During the mock attempt, hints and answers stay locked so the result reflects independent practice rather than assisted performance. The mock quiz works in two ways: as the final check at the end of a practice cycle, as shown in the workflow diagram, or as a standalone mode the learner starts on their own.

After submission, fixed answer rules score questions with clear right or wrong answers. The agents then explain missed topics using approved material, recommend focused practice, and create a new follow-up quiz. The system reports topics for review and practice readiness, not an official grade or a prediction of the student's real test score.

This mode is for preparation and formative practice only. It must not provide help during a live, graded, or restricted assessment.

## Plain-English diagram walkthrough

1. The learner attempts a practice question instead of asking for a homework answer.
2. Fixed answer rules check every response, both the first attempt and each new practice answer.
3. The Learning Review Agent records a possible learning difficulty supported by the attempts, not a diagnosis or unofficial grade.
4. The Teaching Agent selects an approved hint or activity and asks a different practice question, which fixed rules check again.
5. If the new answer is still incorrect, the Try Another Method step sends the Teaching Agent back with one different approved method. Once the learner answers correctly, a short mock quiz without hints checks whether they can work independently. After the mock quiz, or when the retry limit is reached, the system prepares a short summary for an authorized parent, teacher, or adviser, who decides the appropriate follow-up.

The agents choose explanations and next steps. Application code controls correctness, retries, approved content, and authorized sharing.

## Suggested buildathon-sized first prototype (suggested / not implemented)

None of these technical options has been built or connected yet. They are suggestions for the group, not requirements or claims that the system already works.

- **Two limited roles** - a Learning Review Agent records a possible learning difficulty and the next practice goal; a Teaching Agent selects an approved method and a new question. Keep two agents only if testing shows that they work better than one simpler flow.
- **LangGraph (possible workflow manager)** - could manage the steps, saved practice information, retry limit, and handoff to an adult.
- **Local MCP tools (controlled connections)** - could give the agents limited access to fictional exercises through developer tools such as `get_practice_activity`, `get_visual_hint`, and `check_practice_answer`. Fixed rules check the answer; the agent chooses which approved activity to use next. It gives hints, not homework answers.
- **Application-enforced boundaries** - the app/server controls approved content, session length, retries, answer leakage, and what progress information each adult may view. Parents and educators, not the agent, make educational decisions.
- **Base44 (optional screen builder)** - could create a simple learner screen showing the place-value or number-line visual and next practice steps.
- **Antigravity (development tool)** - can help us build and test the prototype; it would not be the tutor used by students.
- **ArgosX** - run the required security scan on the eventual build. Use fictional learner profiles, test answer leakage and retry limits, and log the choices.

## Example demo using fictional data

Uses fictional learner profiles only - not real childhood student data.

1. A fictional learner answers 52 − 27 as 35, a common mistake when subtracting two-digit numbers that need regrouping.
2. Fixed answer rules mark it incorrect. The Learning Review Agent records a possible regrouping difficulty and asks how the learner got the 5 in the ones place before labeling it.
3. The Teaching Agent selects a teacher-approved place-value activity (trade one ten for ten ones), then asks a different check question, 61 − 38, without revealing the answer.
4. The learner answers 37, so the fixed rules mark it incorrect. Try Another Method sends the Teaching Agent back to a number-line approach (count up from 38: +2 to 40, +20 to 60, +1 to 61, so 23) within the one-retry limit.
5. The learner answers correctly, then takes a short mock quiz without hints, such as 43 − 19, 70 − 26, 85 − 47, and 58 − 23 (which needs no regrouping). After submission, the system produces a short support summary so a parent can encourage review and a teacher or adviser can guide the next lesson.

## Research validation and evidence limits

**Current judgment:** the need for additional learning support is well documented, and research supports tutoring as a type of learning support. There is no measured learning benefit yet for this product, how it interprets learner mistakes, or its two-agent design.

- J-PAL's review of experimental PreK–12 tutoring studies reported an overall pooled learning effect of 0.37 standard deviations. That result concerns the tutoring programs studied; it is not an expected effect size for an AI tutor.
- A 2026 Pew Research Center survey found that 54% of US teens ages 13 to 17 had used AI chatbots for schoolwork, and one in ten said chatbots helped with all or most of their schoolwork. This shows that AI-assisted schoolwork is already common among teens. It does not describe younger children or prove that students are learning from the assistance.
- A Penn/Wharton experiment with nearly 1,000 high-school mathematics students in Turkey found that general-purpose GPT improved assisted practice but students performed 17% worse than the control group when AI was removed. A teacher-informed, guarded GPT tutor mitigated that harm but did not outperform the control group on the independent exam. This supports hints, safeguards, and checks without assistance; it does not establish effectiveness for US elementary subtraction.
- Stanford's Tutor CoPilot trial involved more than 700 tutors and 1,000 students. Students whose human tutors used the AI support were 4 percentage points more likely to master math topics. The tool also increased probing questions and reduced generic praise. This supports AI assisting a person who teaches, but it does not test a child using an AI tutor alone at home.
- Guided AI tutoring already exists. Hints alone are not a meaningful difference. The question to test is whether a tutor that changes among teacher-approved methods after an unsuccessful attempt improves performance on a new problem and produces useful human follow-up.

**Smallest credible test:** use one skill (two-digit subtraction with regrouping), fixed answer checks, two teacher-approved teaching methods, and a clear retry limit. Compare the adjustable workflow with one fixed approved explanation using different but comparable questions before support, immediately afterward, and later without hints.

**Design note:** an answer such as `52 − 27 = 35` suggests, but does not prove, a regrouping difficulty; it could also be a simple slip. Ask the learner about their reasoning before deciding what caused the error. The same idea could also apply to a high-school skill such as the distributive property (for example, `2(x + 3) = 14` answered as x = 5.5 instead of x = 4).

**What would weaken the concept:** independent performance does not improve over a fixed explanation, the agent repeatedly misreads student reasoning, or the experience encourages answer dependence.

### Research sources

- [J-PAL: The Transformative Potential of Tutoring for Pre K–12 Learning Outcomes](https://www.povertyactionlab.org/publication/transformative-potential-tutoring-pre-k-12-learning-outcomes-lessons-randomized), 2020.
- [Pew Research Center: How Teens Use and View AI](https://www.pewresearch.org/internet/2026/02/24/how-teens-use-and-view-ai/), February 24, 2026.
- [Knowledge at Wharton: Without Guardrails, Generative AI Can Harm Education](https://knowledge.wharton.upenn.edu/article/without-guardrails-generative-ai-can-harm-education/), August 27, 2024.
- [Stanford National Student Support Accelerator: Tutor CoPilot](https://nssa.stanford.edu/studies/tutor-copilot-human-ai-approach-scaling-real-time-expertise), 2025.

## Measures

Success on different post-hint and mock-test questions without hints, wrong answers revealed by mistake, appropriate teaching-method changes, retry limits followed, useful support signals, and timely human follow-up. Compare against a fixed explanation using the same fictional mistakes; do not claim learning outcomes from a scripted demo.

## Assumptions / questions

Target age and curriculum, how to distinguish practice from assessed work, what information is useful without becoming surveillance, how to test genuine learning, and what student-data safeguards a real deployment would require.

## Links

- [HTML concept brief](study-buddy.html)
- [Interactive workflow diagram](../diagrams/study-buddy.html)
- [Concept homepage](../index.html)
- [Family-School Coordinator comparison](family-school.md)
