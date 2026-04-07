# Assignment Rubric: User Stories

**Course:** CS 340-26  
**Assignment:** Sprint 3 — User Story Submission  
**Total Points:** 100 (50 per story; minimum 2 stories required)  
**Evaluated in:** `us_grade.md` in each project repository

---

## Overview

A user story is the team's commitment to the customer: a concrete description of one thing a real person wants to do, why they want to do it, and what "done" looks like. The discipline of writing user stories forces the team to think from the user's perspective before writing a single line of code.

This assignment has two parts that are graded together:
1. **The `.md` file** — the user story document committed to your repository
2. **The GitHub issue** — a Sprint 3 issue whose title is a Markdown hyperlink pointing to the `.md` file

Both must be present for full credit on a story.

---

## Required Format

### Issue Title Format

The issue title must be a Markdown hyperlink in exactly this format:

```
[<Story Title>](<URL to .md file on GitHub>)
```

**Example (correct):**
```
[User Story: Withdraw Cash from ATM](https://github.com/cs340-26/MyProject/blob/main/UserStoryWithdrawCash.md)
```

**Example (incorrect — link present but wrong format):**
```
[User Story Withdraw Cash] https://github.com/cs340-26/MyProject/blob/main/UserStoryWithdrawCash.md
```

The URL must point to a file that exists on the `main` branch of your repository.

### User Story File Format

Each `.md` file must follow this template:

```markdown
# Feature: <Name>

As a <kind of stakeholder>,
I want to <do some task>,
so that <I can achieve some benefit>.

## Acceptance Criteria

Given <some precondition>,
  And <additional context if needed>,
When <an event occurs>,
Then <ensure some outcome>,
  And <another outcome if needed>.
```

---

## Scoring: Per Story (50 points each)

Each story is scored independently. The final grade is the average of your two highest-scoring stories, scaled to 100.

### Part A — GitHub Issue (20 points)

| Points | Criteria |
|--------|----------|
| 18–20 | Issue exists in the Sprint 3 milestone. Title is a fully-formed Markdown hyperlink `[Story Title](URL)`. The URL resolves to an existing `.md` file on `main`. Issue is assigned to a team member. |
| 13–17 | Issue exists. Link is present in the title but not in the correct `[text](URL)` hyperlink format (e.g., URL is pasted raw next to the title). |
| 7–12 | Issue exists with a title that names the user story, but no link to a `.md` file is present anywhere in the title. |
| 2–6 | Issue exists but the title is a generic placeholder (`"User Stories NEEDED"`, `"Sprint 3 task"`) or the title is an unfilled template (`"As a [kind of stakeholder]"`). |
| 0–1 | No issue exists in the Sprint 3 milestone for this story. |

### Part B — `.md` File Exists (10 points)

| Points | Criteria |
|--------|----------|
| 10 | A `.md` file is committed to the `main` branch and accessible at the URL in the issue title. |
| 5 | A `.md` file exists on a feature branch but was never merged to `main`. |
| 0 | No `.md` file found anywhere in the repository. |

### Part C — As a / I want / so that Template (20 points)

All three clauses of the user story sentence must be present and meaningful.

| Points | Criteria |
|--------|----------|
| 18–20 | All three clauses present and meaningful. Stakeholder is a real, specific person (not `"a user"` or `"someone"`). The task is concrete and observable. The benefit is a genuine value the stakeholder receives — not a restatement of the task. |
| 13–17 | All three clauses present. Minor quality issue — e.g., the stakeholder is slightly generic, or the benefit is close to restating the task rather than describing the value. |
| 8–12 | Two of the three clauses present and meaningful. The "so that" clause is missing or uses placeholder text. Or all three clauses are present but so brief (< 1 sentence each) that they carry no information. |
| 3–7 | Only one clause present (usually "As a … I want …" with no benefit). Story reads as a feature request, not a user narrative. |
| 0–2 | No template present, or the file contains only unfilled placeholder text (`As a [kind of stakeholder]`). |

**Good vs. poor example:**

| Clause | Poor | Good |
|---|---|---|
| As a | *As a user,* | *As a college student tracking my grocery budget,* |
| I want to | *I want to add items,* | *I want to add items to a digital pantry list with quantities,* |
| so that | *so that it works.* | *so that I know what I already have before buying duplicates.* |

### Part D — Acceptance Criteria (Given/When/Then) (25 points)

Acceptance criteria define what "done" means in a testable, unambiguous way.

| Points | Criteria |
|--------|----------|
| 22–25 | One or more scenarios using the Given/When/Then structure. Each scenario is specific enough to be executed as a manual test right now. `Given` states a concrete precondition. `When` describes a single event or action. `Then` describes an observable, verifiable outcome. Covers at least one success path and one failure/edge path. |
| 16–21 | Given/When/Then structure present. Scenarios are mostly specific and testable. Missing a failure path, or one step is slightly ambiguous (e.g., `Then the system responds appropriately` instead of `Then an error message is displayed`). |
| 9–15 | Acceptance criteria present but not in Given/When/Then format (e.g., a bulleted list of requirements). Or the structure is present but too vague to act on. |
| 3–8 | A single generic statement of expected behavior (`"The feature should work correctly"`). No structure. |
| 0–2 | No acceptance criteria of any kind. |

**Example (good):**
```
Given the user is logged in and has an existing pantry,
  And the pantry contains "Eggs (6)"
When the user taps "Eggs" and updates the quantity to 12,
Then the pantry shows "Eggs (12)"
  And the change is persisted after the user closes and reopens the app.

Given the user is not logged in,
When the user navigates to the pantry page,
Then they are redirected to the login screen.
```

---

## Penalty: SMART Quality (-10 points, applied once per story)

A story that is technically complete (all four parts present) but fails to be Specific, Measurable, and Achievable in any meaningful sense loses 10 points.

**Signs that the SMART penalty applies:**
- The "want" is so vague it could mean anything (`I want to use the app`)
- The benefit is completely disconnected from the task (`so that it is good`)
- The acceptance criteria describe a behavior that cannot be observed or measured

---

## Summary Score Sheet (per story)

| Part | Max | Score |
|---|---|---|
| A — Issue with linked title | 20 | |
| B — `.md` file on `main` | 10 | |
| C — As a / I want / so that | 20 | |
| D — Acceptance criteria | 25 | |
| SMART quality (penalty) | −10 max | |
| **Story Total** | **75** max → scaled to **50** | |

Final grade = (Story 1 score + Story 2 score) / 100 × 100

---

## Common Issues and Their Impact

| Issue | Points Lost |
|---|---|
| Issue title has URL but not in `[text](URL)` format | −7 on Part A |
| `.md` file exists but on a branch never merged to `main` | −5 on Part B |
| "So that" clause is missing | −8 on Part C |
| "So that" clause restates the task (`so that I can add items`) | −5 on Part C |
| No Given/When/Then; replaced by a bulleted list | −12 on Part D |
| Given/When/Then present but only happy path (no failure scenario) | −5 on Part D |
| Story is 3 lines total (no substance) | SMART penalty −10 |
| Issue not in Sprint 3 milestone | −10 on Part A |
| Issue is assigned to no one | −3 on Part A |

---

## Letter Grade Conversion

| Score | Grade |
|-------|-------|
| 93–100 | A |
| 90–92 | A− |
| 87–89 | B+ |
| 83–86 | B |
| 80–82 | B− |
| 77–79 | C+ |
| 73–76 | C |
| 70–72 | C− |
| 60–69 | D |
| < 60 | F |
