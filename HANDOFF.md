# Handoff: consistency audit and fix plan

**Read this first if you are an AI assistant (or teammate) picking up this repository.**

> **What this repository is:** a **concept presentation** for Wendy's DSV 2026 group. The group will decide whether to adopt one of these concepts, change it, or choose a better idea, which may come from someone else. It is **not a build plan**. "Fixes" in this file mean making the presentation consistent, not preparing an implementation. Write and edit the content as proposals for discussion: no roadmaps, commitments, or "next version" language.

| | |
|---|---|
| Last updated | 2026-10-22 |
| Owner / approver | Wendy (repository owner). Do not commit, push, or publish without her approval. |
| Status | **Audit fixes executed on 2026-10-22.** The owner approved D1–D3 = A. All findings F0–F8 are resolved (see section 6), and the changes are committed and pushed to `main`. |
| Live site | https://wendylj-bai.github.io/school-day-agent-concepts/index.html (published from `docs/` on `main`) |
| Next step for a new contributor | Nothing from this audit is still open. Read sections 1–4 before changing content, and keep the vocabulary in section 4. |

---

## 1. Start here (reading order)

1. This file: what is done, what is open, what needs a decision.
2. [`README.md`](README.md): purpose of the repository and the decisions made so far.
3. [`docs/concepts/family-school.md`](docs/concepts/family-school.md) and [`docs/concepts/study-buddy.md`](docs/concepts/study-buddy.md): plain-text versions of the two concept pages. They are the fastest way to understand each concept.
4. [`specifications/*.coordination.workflow.json`](specifications/): source specs for the two interactive diagrams.

## 2. Repository map and source of truth

| Path | What it is | Notes |
|---|---|---|
| `docs/index.html` | Homepage comparing both concepts | Published |
| `docs/concepts/<concept>.html` | Full concept pages | Published. **These are the primary text.** |
| `docs/concepts/<concept>.md` | Plain-text briefs written as "faithful summaries" of the HTML pages | Must be kept in sync with the HTML whenever the HTML changes |
| `specifications/<concept>.coordination.workflow.json` | **Current** Archify specs for the diagrams | Edit these, then regenerate the diagrams |
| `specifications/<concept>.workflow.json` | Older drafts | Not used. Do not edit. |
| `specifications/<concept>.visual-check.json` | Older visual-check output | Not used for the current diagrams |
| `docs/diagrams/<concept>.html` | Generated interactive diagrams, embedded in the concept pages | **Generated from the specs. Never hand-edit.** Currently out of date (see F0). |
| `docs/diagrams/<concept>.visual-check.json` | Archify validation output for the current diagrams | Regenerated together with the diagram |
| `../dsv-agentic-ai-concept-gallery/` | Earlier, separate concept gallery | **Keep untouched** (README decision) |

## 3. Ground rules (from README and team decisions)

- Both concepts are **hypotheses for team discussion**. Never write anything that claims validated demand, school approval, a working system, or measured impact.
- **Fictional data only** in demos and examples.
- Educators and parents keep authority. Agents never change records, grade, diagnose, or message someone on an educator's behalf without approval.
- Each concept has **two agent roles**. Every other diagram box is fixed application rules, a tool or data source, or a person.
- Keep the plain-language register from the latest pass: short sentences and no jargon such as "deterministic", "bounded", or "orchestration".

## 4. Agreed vocabulary

The latest working-tree pass already uses these terms. Keep them consistent everywhere, including diagram labels.

| Use | Instead of |
|---|---|
| fixed rules / fixed answer rules / fixed application rules | deterministic |
| limited, controlled | bounded |
| first prototype | MVP |
| fictional data | synthetic data |
| Learning Review Agent | Learning-State Agent |
| Evidence Agent, Coordination Agent | "response agent" |
| Teaching Agent | (unchanged) |
| Try Another Method | Strategy Retry |
| Permission Check / Privacy and Source Check | Access Check / Privacy and Citation Gate |

## 5. Already done in the working tree (uncommitted)

These items from the audit are already fixed in the working tree. Do not redo them.

- Plain-language rewrite of `docs/index.html`, both concept pages, both `.md` briefs, and README.
- "Evidence and response agents" changed to "Evidence and Coordination Agents" in the Family-School criteria table.
- Data wording changed to "fictional" in the status labels and concept footers.
- Agent and node renames applied in the concept pages, briefs, and both specs (see vocabulary table).

## 6. Findings (all resolved on 2026-10-22)

| ID | Resolution |
|---|---|
| F0 | Both diagrams regenerated with Archify `deliver` (showcase profile: 9/9 checks, 0 errors, 0 warnings) and passed `visual-check` in a browser. |
| F1 | D1 = A: Request Sorter removed. The Coordination Agent sends questions to Educator Follow-up and receives the educator's clarification back. Facts return to the Evidence Agent. |
| F2/F3 | D2 = A: retry happens before the mock quiz. A new **New Answer Check** node (fixed rules) checks the fresh question; Try Another Method loops back to the Teaching Agent. The Teaching Agent now fetches the approved hint from Vetted Activities and presents the fresh question itself, which avoids a crossing arrow and matches the text. |
| F4 | One sentence added on both pages explaining the two ways the mock quiz is used. |
| F5 | No change needed. Codex's pass removed the example tool names from both HTML agent cards, so the two pages are consistent; the tool names remain in the `.md` briefs. |
| F6 | D3 = A: the subtraction example replaced the fractions example in the HTML page and the brief. The "content correction" note became a "Design note". |
| F7 | The study-buddy spec lane and group labels now use the plain-language terms. |
| F8 | Gallup dates, criteria table headings, MCP mention on the index, section shading, and the remaining "MVP" and "Runtime trace" wording are fixed. The footer wording was left as is (optional). |

The original findings are kept below for reference.

**How these were checked:** live site downloaded and read in full; diagram nodes and arrows extracted from the generated files; local working tree inspected; cited statistics checked against the source pages (J-PAL figure not yet checked; see section 10).

### F0. Diagrams are out of date (blocker for everything diagram-related)
The specs were edited after the diagrams were generated (spec timestamps 13:57, diagram 13:51 on 2026-10-22, and `docs/diagrams/` has no uncommitted changes). The published diagrams still show the old labels: "Request Router", "Learning-State Agent", "Strategy Retry", "Access Check", "Privacy and Citation Gate", and "Answer Checker".
**Fix:** regenerate both diagrams with Archify after F1–F3 are applied to the specs.

### F1. Family-School: the diagram gives the Coordination Agent's job to the Request Sorter. Decision D1.
- **Text** (HTML page and brief): the Coordination Agent decides whether to answer or to prepare an educator follow-up, and owns `create_educator_followup`.
- **Spec:** `request_router` ("Request Sorter", agent-colored `backend` node, not marked as fixed rules) branches to `followup_draft`. `coordination_agent` has no arrow to `followup_draft`. A reader can count three agents, while the pages say two.
- Also: facts flow `school_info → request_router` and skip the Evidence Agent, which the text says gathers and checks them.
- Also: the educator's reply goes straight to `privacy_gate`, so the diagram never shows "continues after clarification", which the criteria table claims.

### F2. Study Buddy: "Try Another Method" is a dead end. Decision D2.
`strategy_retry` has an incoming arrow but nothing leaving it, and the spec lists it in `semanticChecks.allowedTerminals`, which is why validation never flagged it. The retry loop is the main evidence for the 20% Autonomy and Self-correction criterion, so it must visibly loop back.

### F3. Study Buddy: the step order disagrees across files. Decision D2.
| Source | Order |
|---|---|
| Diagram spec; `study-buddy.md` walkthrough steps 4–5 | fresh question → mock quiz → retry |
| Index concept card; HTML demo; `study-buddy.md` demo | fresh question → still stuck → retry → mock quiz → adult |

Related wording issue: "How to read this flow" step 2 in both the HTML page and the brief says the fixed rules check the "new" answer, but in the diagram the Answer Check checks the *first* attempt, and nothing checks the fresh question.

### F4. Study Buddy: the mock quiz is described in two ways
The "Practice and mock-test mode" section describes it as a standalone mode (learner picks the skill and difficulty). The diagram and demo show it as the last step of the hint cycle. **Fix:** add one sentence saying it works both ways.

### F5. Study Buddy HTML is missing the example tools that the brief already names
`study-buddy.md` names `get_practice_activity`, `get_visual_hint`, and `check_practice_answer`. The HTML agent cards name only `check_practice_answer`. Family-School names one tool per agent. **Fix:** copy the brief's tool names into the HTML Teaching Agent card. Do not invent new names.

### F6. The math example is too advanced and has a "content correction" note left in. Decision D3.
`½ + ¼ = ²⁄₆` is grade 4–5 math, and the published page still carries a reviewer-style "Content correction" box. Replacing the example resolves both. The new example and every location to change are listed in section 8.

### F7. Remaining old terms in the study-buddy spec
`specifications/study-buddy.coordination.workflow.json`: lane "Student Practice and **Deterministic** Checks" (line 6) and group "**Learning-state** and teaching responsibilities" (line 16). Rename them, for example to "Student Practice and Fixed Checks" and "Learning review and teaching responsibilities".

### F8. Minor polish
- **Gallup date:** "A 2025 Gallup survey" appears in `family-school.html` and `family-school.md`. The survey ran Dec 2–6, 2024 and was published Apr 23, 2025. Suggested wording: "A Gallup survey (Dec 2024, published April 2025)…"
- **Criteria table headings:** the index uses "Proposed evidence in the design / What the team must prove"; the concept pages use "Design fit / Evidence still required". Use one pair.
- **MCP:** both concept pages mention MCP, but the index's shared design section does not. Add it to the "Participation by design" card or a stack card.
- **Section shading:** in both concept pages, `validation` and `criteria` are consecutive `section` blocks with no `alt` between them, and so are the blocks just before `#workflow`. Alternate the backgrounds.
- **Footer wording:** the Study Buddy footer says "…learning-impact claim, or school endorsement."; the others say "…school endorsement claimed." Optional to align.

## 7. Decisions needed from the owner before executing

| ID | Question | Options | Assistant recommendation |
|---|---|---|---|
| D1 | Request Sorter in the Family-School diagram | **A.** Remove it. The Coordination Agent decides between "cited answer" and "needs educator". **B.** Keep it, retag it as `fixed rules` (security-colored), describe it in the text as fixed routing, and still move follow-up creation to the Coordination Agent. | **A**: it matches the HTML text, which never mentions a sorter. If A is chosen, also update the "question is sorted" wording in `family-school.md` (Normal flow). |
| D2 | Study Buddy step order | **A.** Demo order: retry happens before the mock quiz. **B.** Diagram order: mock quiz, then retry. | **A**: the index card, the HTML demo, and the brief's demo already use it. |
| D3 | Practice example | **A.** Grade 2–3 subtraction with regrouping. **B.** High-school distributive property. **C.** Keep fractions. | **A** in the demo; mention B under future skills. |

### Spec changes if D1 = A (`family-school.coordination.workflow.json`)
- Delete the `request_router` node and its edges `school_router`, `router_coordination`, and `router_followup`.
- Add these edges:
  - `school_info → evidence_agent` "approved facts"
  - `evidence_agent → coordination_agent` "facts + sources"
  - `coordination_agent → followup_draft` "needs educator" (branch, security)
  - `educator → coordination_agent` "clarification" (return, security), replacing `educator_gate`
- Keep `coordination_agent → privacy_gate` and relabel it "cited answer".
- Update `mainPath` to `family_hub, access_check, evidence_agent, school_info, coordination_agent, privacy_gate, family_view`.
- In `requiredPaths`, change `{from: request_router, to: educator}` to `{from: coordination_agent, to: educator}`.

### Spec changes if D2 = A (`study-buddy.coordination.workflow.json`)
- Replace `question_transfer` and `check_retry` with these edges:
  - `fresh_question → answer_check` "check new answer"
  - `answer_check → strategy_retry` "still incorrect" (branch, dashed)
  - `strategy_retry → teaching_agent` "new approved method" (return, dashed)
  - `answer_check → transfer_check` "correct → no-hint quiz"
  - `strategy_retry → support_summary` "retry limit reached" (security)
- Remove `strategy_retry` from `semanticChecks.allowedTerminals`.
- Then reword "How to read this flow" step 2 so it says the fixed rules check **every** answer, in both the HTML page and the brief.

## 8. Replacement example (D3 = A): subtraction with regrouping

| Element | Content |
|---|---|
| Mistake | A learner answers **52 − 27 = 35** (correct: 25) |
| Possible difficulty | "Smaller-from-larger": did 7 − 2 = 5 in the ones place instead of regrouping. **Ask before labeling:** "How did you get the 5 in the ones place?" |
| Method 1 (place value) | "Can you take 7 ones from 2 ones? Trade one ten for ten ones." Base-ten blocks or a place-value chart. |
| Fresh check question | 61 − 38 = 23 (same mistake gives 37) |
| Method 2 (Try Another Method: number line) | Count up from 27: +3 → 30, +20 → 50, +2 → 52, so 25 |
| No-hint mock quiz | 43 − 19 = 24 · 70 − 26 = 44 · 85 − 47 = 38 · **58 − 23 = 35** (needs no regrouping; catches over-regrouping) |
| Future-skills mention (option B) | 2(x + 3) = 14 → x = 4 (common mistake: 2x + 3 = 14 → x = 5.5) |

**Every location to change** (line numbers refer to the working tree on 2026-10-22):
- `docs/concepts/study-buddy.html`
  - L13: problem paragraph (`½ + ¼ as ²⁄₆`)
  - L21: demo steps ("adding fractions with unlike denominators", "fraction-bar hint", "number-line approach"). Method 1 becomes place-value blocks; method 2 stays the number line.
  - L23: "Smallest credible test" ("adaptive fractions workflow") and the **"Content correction" box**. Replace the box with a short design note: "Ask about the learner's reasoning before labeling a difficulty."
  - L33: first-prototype card ("Adding fractions with unlike denominators")
- `docs/concepts/study-buddy.md`
  - L11: problem
  - L64: "fraction visual"
  - L72–73: demo
  - L82: "US elementary fractions" becomes "US elementary subtraction"
  - L85: "one fractions skill"
  - L87: **"Important content correction"** paragraph; replace it with the design note
- Diagram labels contain no fraction wording, so no spec change is needed for D3.

## 9. Execution checklist (after D1–D3 are decided)

1. [x] Apply the D1 and D2 spec changes, plus F7 (old terms in the spec).
2. [x] Regenerate both diagrams with Archify from the `*.coordination.workflow.json` specs into `docs/diagrams/`, including the `.visual-check.json` files. Confirm validation passes.
3. [x] Update the HTML pages to match the new diagrams: F1 and F3 text, F4 sentence, F5 tools.
4. [x] Apply D3 (section 8).
5. [x] Apply F8 polish.
6. [x] Re-sync both `.md` briefs with their HTML pages (they are summaries and must not drift).
7. [x] Run the verification below.
8. [x] Show Wendy the diff. Commit and push **only with her approval**. Afterwards, compare the live site with the working tree.
9. [x] Update the change log in this file.

### Verification
```bash
# Print every arrow in a generated diagram (repeat for study-buddy)
python3 -c "import re,sys;s=open(sys.argv[1]).read();print('\n'.join(sorted(set(' -> '.join(m) for m in re.findall(r'data-edge-from=\"([^\"]+)\" data-edge-to=\"([^\"]+)\" data-edge-label=\"([^\"]*)\"',s)))))" docs/diagrams/family-school.html
# No old vocabulary left in the content (expect no output). The diagram HTML is excluded
# because Archify's own code comments use words such as "deterministic" and "fraction".
grep -rnE "Learning-State|Learning-state|[Dd]eterministic|Request Router|Request Sorter|Strategy Retry|Content correction|²⁄₆|\bMVP\b" docs/index.html docs/concepts specifications/*.coordination.workflow.json
# Archify specs: validate before delivering (run from the archify skill folder)
node bin/archify.mjs validate workflow <spec.json> --quality showcase --json
```
Expected after D1 = A and D2 = A:
- Family-School has `coordination_agent -> followup_draft` and no `request_router`.
- Study Buddy has `strategy_retry -> teaching_agent`, and no node is a dead end except `support_team`.

Also check every link, view each page at phone width (about 375 px), and confirm the diagrams load inside the concept pages.

## 10. Verified vs. still to verify

- **Verified against the source pages:**
  - Gallup: 808 K–12 parents; 25% "not much" + 17% "nothing" = 42%; fielded Dec 2024; published Apr 23, 2025.
  - IES: about 26,000 students; lower chronic absence, no gain in achievement; Sept 2020.
  - Knowledge at Wharton: nearly 1,000 students in Turkey; 17% worse without AI; guarded tutor about even with the control group; Aug 27, 2024.
  - All external links returned HTTP 200 on 2026-10-22.
- **Not yet verified:** the J-PAL pooled effect of 0.37 SD (from memory of Nickow, Oreopoulos and Quan 2020; the link works but the number was not checked on the page). The grade-level claims (fractions with unlike denominators around grade 4–5; two-digit subtraction with regrouping around grade 2–3) are from memory of the US Common Core standards.
- **Judgment, not fact:** the D1–D3 recommendations and the vocabulary choices.

## 11. Change log

| Date | Who | What |
|---|---|---|
| 2026-10-21 → 22 | Commits on `main` (see `git log`) | Initial concepts → problem framing → plain-English workflows → founder context → sources → research validation → mock-test mode → "Align concept briefs with workflow diagrams" (`229189f`, current `HEAD`) |
| 2026-10-22 | Codex (uncommitted) | Plain-language pass across 8 files: index, both concept pages, both briefs, README, both coordination specs. Diagrams were **not** regenerated afterwards (F0). |
| 2026-10-22 | Claude Code | Consistency audit of the live site and working tree; this handoff file. |
| 2026-10-22 | Claude Code (approved by Wendy: D1–D3 = A) | Executed F0–F8: revised both specs and regenerated both diagrams; updated both concept pages, both briefs, and the index. Committed together with Codex's plain-language pass and pushed to `main`. Browser screenshots were kept out of `docs/` so they are not published. |
