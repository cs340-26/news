# Assignment Rubric: Collaboration & Version Control

**Course:** CS 340-26  
**Assignment:** Code Quality — Part 3 of 3  
**Total Points:** 100  
**Evaluated in:** `code_quality_grade.md` in each project repository

---

## Overview

This assignment evaluates whether the team worked together *as engineers*, not just as individuals who happened to commit to the same repository. Professional software development depends on distributed ownership, code review through pull requests, and a Git history that tells the story of how a project was built.

The three sub-criteria are evaluated independently and combined for a total score.

---

## Sub-Criterion 3a — Commit History (35 points)

A healthy commit history shows that every team member contributed meaningfully to the code, that work progressed incrementally (not in bulk uploads), and that commit messages explain *what changed and why*.

| Points | Criteria |
|--------|----------|
| 32–35 | Frequent commits with descriptive messages — each message says what changed and why in one clear sentence (`Fix null pointer when user has no prior session` not `fix`). Work is distributed across all team members. Commits are granular and tied to specific features or fixes, ideally referencing an issue number (`closes #12`). No bulk file uploads. Committer names are real GitHub usernames. |
| 26–31 | Generally good commit hygiene. Some vague messages or slight imbalance in contribution, but all members have meaningful commits and the history reads as a coherent timeline of work. |
| 16–25 | Commits are present but messages are routinely vague (`"update"`, `"fix"`, `"changes"`, `"stuff"`), or distribution is noticeably uneven — one member carries significantly more than their share, with others only contributing once or twice. |
| 7–15 | Large gaps between commits; bulk `"Add files via upload"` commits; one member doing nearly all the work (>70% of commits); unprofessional committer names (e.g., `"test"` or initials). |
| 0–6 | Almost no commits from most team members. The project is effectively a solo effort submitted as team work. No incremental development visible in the history. |

**Contribution balance benchmarks:**

| Team Size | Minimum per Member |
|-----------|-------------------|
| 2 members | ≥ 30% each |
| 3 members | ≥ 20% each |
| 4 members | ≥ 15% each |

Any member below **10%** of total commits in a 3–4 person team is flagged as a concern regardless of team size.

**How evaluators check contribution distribution:**
```
git log --pretty=format:"%an" | sort | uniq -c | sort -rn
```

**Message quality scale applied per commit:**

| Commit Message | Quality |
|---|---|
| `Fix null pointer when user session is missing (closes #14)` | Excellent |
| `Add login validation for empty username field` | Good |
| `Update auth module` | Poor — what changed? |
| `fix` | Unacceptable |
| `Add files via upload` | Unacceptable (bulk upload) |

---

## Sub-Criterion 3b — Branching Strategy (35 points)

Working directly on `main` eliminates code review and makes it impossible to isolate a broken feature. Professional teams use feature branches and pull requests so that every change is reviewed before it becomes the team's shared baseline.

| Points | Criteria |
|--------|----------|
| 32–35 | Feature branches used for every significant unit of work. Branches are named to describe their content (`feature/login-page`, `fix/null-crash-on-empty-input`, `chore/upgrade-dependencies`). Code reaches `main` only via pull request. Stale merged branches are deleted. PR descriptions explain what the branch does and why. |
| 26–31 | Feature branches used for most work. Occasional direct commit to `main` for trivial fixes. Pull-request-based integration is clearly the norm. Branch names are mostly descriptive. |
| 16–25 | Some feature branches and PRs exist, but significant work was done directly on `main`. Branch names may not match their contents (e.g., `mithun/unit-tests` for a branch that also adds UI components). |
| 7–15 | Feature branches exist but are rarely used in practice. Most code is committed directly to `main`. Branch names are inconsistent or meaningless (e.g., `test`, `branch1`, `temp`). |
| 0–6 | No feature branches. Only `main` exists. All development is directly on the main branch with no pull requests. |

**Branch naming convention:**

| Prefix | Usage |
|---|---|
| `feature/` | New capability or user-facing functionality |
| `fix/` or `bugfix/` | Bug fix |
| `chore/` | Dependency updates, config changes, refactors without behavior change |
| `docs/` | Documentation-only changes |
| `test/` | Adding or fixing tests only |

**How evaluators check branching:**
```
git branch -a --sort=-committerdate
git log --oneline --merges --all
```

---

## Sub-Criterion 3c — Integration (30 points)

A team that builds components in isolation but never connects them has not finished the project. This criterion rewards genuine cross-component integration: frontend talking to backend, hardware talking to the network, individual members' code merged into a coherent, working whole.

| Points | Criteria |
|--------|----------|
| 27–30 | All components (frontend, backend, database, hardware) are integrated and functional together. There is evidence of merge conflict resolution — the kind of conflict that only arises when two people work on the same files. Code from multiple team members appears in the same feature. The `main` branch reflects the full integrated product. |
| 21–26 | Components are integrated. One or two components may be incomplete or partially connected, but the integration story is clear and the primary flow works end-to-end. |
| 13–20 | Partial integration. Major components exist in the repo but one is missing or a branch was never merged into `main`. The app can be run but one key path (e.g., login, data fetch, save to database) does not work end-to-end. |
| 6–12 | Components coexist in the repository but do not interoperate. Frontend and backend are separate branches that were never integrated. Hardware module exists but is not wired to the network layer. |
| 0–5 | No integration. Only one component was ever built, or the repository contains work from one team member only. |

**What evaluators check for integration evidence:**
- API calls in the frontend match routes defined in the backend
- Database schema matches what the ORM/queries expect
- Merge commits in `git log --merges` that combine work from named contributors
- No component living only in a feature branch that was never merged to `main`
- For hardware projects: wiring diagram or protocol definition matches implementation

---

## Score Sheet

| Sub-Criterion | Max | Score |
|---|---|---|
| 3a — Commit History | 35 | |
| 3b — Branching Strategy | 35 | |
| 3c — Integration | 30 | |
| **Total** | **100** | |

**Letter grade conversion:**

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
