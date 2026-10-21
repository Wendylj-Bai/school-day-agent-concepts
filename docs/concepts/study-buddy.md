# Personalized Study Buddy · Concept Brief

Working hypothesis for team discussion, not proven learning impact or a built product. Faithful summary of the existing [HTML brief](study-buddy.html) and [workflow diagram](../diagrams/study-buddy.html).

## Value proposition (one sentence)

Help a student move forward after a practice mistake while keeping parents, teachers, and advisers involved in encouragement, content guidance, and follow-up.

## Plausible recurring problem

A child answers ½ + ¼ as ²⁄₆. They may keep trying without knowing why their method fails. A static answer key reveals the result, not the misunderstanding; a parent may not know which explanation to try next. The child loses momentum during a recurring study session. This is a plausible scenario, not measured learning data.

## Problem-to-solution map

- **Core problem:** a student may need timely learning support when a teacher or a parent with subject knowledge is unavailable.
- **Pain experienced:** repeated mistakes can become frustration; a generic explanation may not address the misunderstanding, and an unrestricted AI tutor may reveal the answer instead of supporting learning.
- **Agentic response:** the Learning-State Agent identifies a possible misconception from practice attempts. The Teaching Agent selects a vetted strategy, presents a fresh question, and adapts when deterministic checking shows that the learner is still struggling.
- **Why agents:** the workflow must observe the attempt, choose a teaching strategy, check whether it worked, adapt within a retry limit, and involve an authorized adult when needed.

## Intended value

- **Student:** get a hint matched to the attempt, practice independently, and ask for help without receiving the answer.
- **Parent:** see a concise, authorized progress and support summary, then encourage practice or help arrange follow-up.
- **Teacher and adviser:** approve learning activities, guide lesson review, and receive a useful signal when persistent difficulty needs human attention.

## Agent's job and why agentic

The agent considers a possible misconception, chooses a vetted visual or exercise through a content tool, gives a hint instead of the answer, then asks a fresh question. It uses the new response to choose the next step on a small learning roadmap; after bounded retries it suggests a parent or teacher check-in.

A fixed quiz cannot change its teaching strategy after an unsuccessful explanation. A generic chatbot may answer the homework outright. The agent's bounded observe → select → check → adapt loop is the feature to demonstrate; voice and avatars are optional, not the core innovation.

## Normal flow and exception / handoff

Normal: learner attempt → possible misconception → choose a vetted activity → visual hint → different check question → next-step roadmap.

Exception: if the child is still stuck, the agent tries another bounded approach; after a retry limit it asks for human help. The diagram shows the exception branch, not an automatic diagnosis of a child.

## Suggested buildathon-sized MVP (suggested / not implemented)

No part of this stack is built or integrated yet; a stack to propose to the group, not a requirement or a claim that these integrations already work.

- **Two bounded roles** - a Learning-State Agent records a possible misconception and next objective; a Teaching Agent selects a vetted strategy and fresh practice question. Retain the split only if it improves results over a simpler flow.
- **LangGraph (workflow/orchestration option)** - track current skill, attempt evidence, possible misconception, hint strategy, and retry count; route attempt → interpret → choose activity → give hint → check a new question → adjust or stop.
- **Local MCP tools (exact names)** - a local MCP server backed by synthetic exercises exposing `get_practice_activity`, `get_visual_hint`, and `check_practice_answer`. The answer check is deterministic for a new practice question; the agent chooses which tool and strategy to use next. The agent gives hints, not homework answers - every check question is a different example.
- **Application-enforced boundaries** - the app/server controls approved content, session length, retries, answer leakage, and what progress information each adult may view. Parents and educators, not the agent, make educational decisions.
- **Base44 (optional UI)** - a simple learner screen could show the fraction visual and a small roadmap; Base44 is an option if integration is viable.
- **Antigravity (development-only)** - can assist development, not serve as the runtime agent.
- **ArgosX** - run the required security scan on the eventual build. Use fictional learner profiles, test answer leakage and retry limits, and log the choices.

## Illustrative synthetic-data demo

Uses fictional learner profiles only - not real childhood student data.

1. A fictional learner makes a common mistake in an equivalent-fractions exercise.
2. The agent selects a vetted explanation and fraction-bar visual, then asks a different check question without revealing the assignment answer.
3. The learner still struggles; the agent switches strategy within a retry limit and updates the visible roadmap.
4. A new question checks transfer. The system produces a concise support summary so a parent can encourage review and a teacher or adviser can guide the next lesson.

## Measures

Success on a different post-hint problem, wrong-answer leakage, appropriate strategy changes, retry compliance, useful support signals, and timely human follow-up. Compare against a fixed explanation on the same synthetic mistakes; do not claim learning outcomes from a scripted demo.

## Assumptions / questions

Target age and curriculum, how to distinguish practice from assessed work, what information is useful without becoming surveillance, how to test genuine learning, and what student-data safeguards a real deployment would require.

## Links

- [HTML concept brief](study-buddy.html)
- [Interactive workflow diagram](../diagrams/study-buddy.html)
- [Concept homepage](../index.html)
- [Family-School Coordinator comparison](family-school.md)
