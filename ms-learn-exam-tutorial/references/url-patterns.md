# URL patterns and discovery rules

Use this file in workflow steps 2-4 of SKILL.md: turn an exam code into a study guide, a course, its learning paths and its modules. Prefer the deterministic catalog API; fall back to search only when it returns nothing.

## Catalog API (fetch with WebFetch or curl; it returns JSON)

Base: `https://learn.microsoft.com/api/catalog/`

| Lookup | URL | Useful fields |
|---|---|---|
| Course by uid | `?type=courses&uid=course.<code>t00` | `study_guide` (list of `{uid, type: learningPath}`), `title`, `url`, `last_modified` |
| All courses | `?type=courses` | filter client-side by `uid` prefix `course.<code>` |
| Learning path | `?type=learningPaths&uid=<path uid>` | `modules` (list of module uids, in order), `title`, `url` |
| Module | `?type=modules&uid=<module uid>` | `title`, `url`, `units` (unit uids), `levels` |
| Exam | `?type=exams` | `uid` (`exam.<code>`), `courses`, `study_guide`, `url` |
| Certification | `?type=certifications` | `exams`, `study_guide`, `url` |

The `uid` filter works for one item. The full-type lists are large (100-300 KB); WebFetch summarises them, so use curl or filter by `uid` when you need raw fields.

### Result of the `type=exams` / `type=certifications` check (2026-11-21)

- `type=exams` returns 143 entries. Only 7 have `courses` filled and 14 have `study_guide` filled. Several common exams (see the two worked examples) are **not listed at all**.
- `type=certifications` returns 153 entries. The entries for "GitHub Actions" and "Azure Fundamentals" have `exams: []` and `study_guide: []`.
- Verdict: **not reliable as the primary route.** Try it as a bonus (if `exam.<code>` exists and `courses` is non-empty, use it), then go to the course uid rule below. Do not tell the user the exam was "not found" because of this lookup alone.
- The course lookup by uid works for the two worked examples below (2 and 3 learning paths).

## Page patterns (learn.microsoft.com, add `/en-us` if a fetch needs it)

| Object | Pattern |
|---|---|
| Certification | `/credentials/certifications/<slug>/` |
| Study guide | `/credentials/certifications/resources/study-guides/<exam-code-lowercase>` |
| Course | `/training/courses/<course-code>` (e.g. `<code>t00`) |
| Learning path | `/training/paths/<slug>/` |
| Module | `/training/modules/<slug>/` |
| Unit | `/training/modules/<slug>/<unit-slug>` |

A catalog module uid has the pattern `learn.<vendor>.<slug>` (e.g. `learn.github.<slug>`, `learn.wwl.<slug>`). First use the path and module uids returned by the course's `study_guide` and the path's `modules` fields instead of guessing. The page slug is the last part, but confirm it with the `url` field of the module lookup.

## Discovery rules

1. **Exam code to study guide.** Fetch the study-guide URL pattern. If the page announces an upcoming change, use the skills list in force on the user's exam date (ask if unknown) and record the "as of" date.
2. **Exam code to course.** Look up `course.<code>t00` (lowercase code). If found, use it. If not found, list `type=courses` and keep uids starting with `course.<code>`: one match, use it; several, ask the user. If none, use the study guide plus the training links on that page plus `microsoft_docs_search` ("<code> learning path"). The `type=exams` shortcut above is optional and never required.
3. **Course to learning paths.** Read `study_guide` of the course and enumerate every path (Part 1..n) in the listed order. Never stop at the first path.
4. **NN.** NN is the module's position in the chosen course, counted across its learning paths in order. A module that repeats keeps its first position. 00 is reserved for a start file. A module outside the course gets the next free number, and the report says so.
5. **When anything is ambiguous, ask the user** (AskUserQuestion) instead of guessing.

## Notes

- Labs often live outside Learn (a GitHub template repo or a hosted instructions site). Follow the link from the exercise unit and fetch the README or page with WebFetch.
- The assessment unit may be called "Knowledge check" or "Module assessment", may hide the answers, and may be interactive-only. Apply the assessment fallback from SKILL.md step 6.
- A unit page for an exercise is often only a short intro that points to the lab; the lab page holds the steps.
- A module may have no exercise unit at all, and the search index can still list old exercise units. Trust the fetched module page; style guide section 5 says what to do then.
- Fetch tooling order: `mslearn` / `npx @microsoft/learn-cli` if available (it may be blocked or unavailable; then it is simply absent from the path), else `microsoft_docs_fetch` plus Write. The MCP result is not a verbatim copy, so record `tool: microsoft_docs_fetch` (style guide section 11). `microsoft_docs_search` has no URL filter: when you use it to find which course module mentions a term, filter the results by the course modules' URL prefix yourself.
- Unit counts and `duration_in_hours` in the catalog are metadata and can disagree with the course page; do not quote them as facts without a check.

## Worked examples (examples only, not defaults)

**Example 1: GitHub exam GH-200.**
`course.gh-200t00` -> `study_guide` = `learn.github-actions` (Part 1 of 2, 4 modules) and `learn.github-actions-2` (Part 2 of 2, 3 modules) -> 7 modules, NN = 01..07 in that order. Module 1 = `/training/modules/github-actions-automate-tasks/` (7 units). The study guide is `/credentials/certifications/resources/study-guides/gh-200`. The exam is absent from `type=exams`.

**Example 2: Azure exam AZ-900.**
`course.az-900t00` (title "Introduction to Cloud Infrastructure") -> `study_guide` lists 3 learning paths (cloud concepts, Azure architecture and services, management and governance). List the modules of all three, ask for one, and check on the fetched module page whether it has an exercise unit (the live AZ-900 modules may have none; then the author exercises need Koszt and Sprzątanie for paid cloud resources). The study guide is `/credentials/certifications/resources/study-guides/az-900`. The exam is absent from `type=exams`.
