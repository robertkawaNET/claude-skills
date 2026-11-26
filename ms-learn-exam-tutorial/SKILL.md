---
name: ms-learn-exam-tutorial
description: Builds a Polish exam-prep tutorial from ONE Microsoft Learn module of any Microsoft or GitHub certification (AZ-104, AZ-900, GH-200, SC-900, DP-203, MS-102 and similar), with source-tagged theory, exercises, quiz, control questions, a unit-by-unit coverage inventory and an exam gaps file for study-guide topics no module teaches. Use when the user gives an exam code or a Learn course, learning path, module or study guide URL and wants a tutorial, study notes, exercises or a quiz - "przygotuj tutorial", "notatki do egzaminu", "ćwiczenia", "moduł z Microsoft Learn", "przygotowanie do certyfikacji". Not for general docs questions (use microsoft-docs) or for creating skills (use microsoft-skill-creator).
argument-hint: "[exam code or Learn URL] [module name or number] [--out folder]"
compatibility: Uses the Microsoft Learn MCP Server (https://learn.microsoft.com/api/mcp); falls back to the mslearn CLI (mslearn or npx @microsoft/learn-cli). Uses WebFetch for the catalog API, study guides, lab READMEs and product docs.
allowed-tools: mcp__plugin_microsoft-docs_microsoft-learn__microsoft_docs_search mcp__plugin_microsoft-docs_microsoft-learn__microsoft_docs_fetch mcp__plugin_microsoft-docs_microsoft-learn__microsoft_code_sample_search WebFetch Read Write Edit Glob Grep AskUserQuestion Bash(npx @microsoft/learn-cli:*) Bash(mslearn:*)
---

# MS Learn exam tutorial

Turn one Microsoft Learn module into a Polish tutorial a candidate can trust on exam day: every fact traced to a source, every unit element covered, every exam topic either in a module tutorial or in the exam gaps file. One module per run. Run in the main conversation (no forked context): the workflow asks the user questions.

## Tools

| Short name | Full name (microsoft-docs plugin) | Use for |
|---|---|---|
| `microsoft_docs_search` | `mcp__plugin_microsoft-docs_microsoft-learn__microsoft_docs_search` | Candidate lookup (no URL filter) |
| `microsoft_docs_fetch` | `mcp__plugin_microsoft-docs_microsoft-learn__microsoft_docs_fetch` | Reading any Learn page or unit |
| `microsoft_code_sample_search` | `mcp__plugin_microsoft-docs_microsoft-learn__microsoft_code_sample_search` | Verified code for exercises |
| WebFetch | built-in | Catalog API, study guides, lab READMEs, product docs |

The prefix differs if the server is installed another way: use whichever `microsoft_docs_*` tools exist. CLI equivalents: `mslearn search|code-search|fetch` (or `npx @microsoft/learn-cli`, which may be blocked or unavailable). Saving order, formats and `tool:` values: style guide section 11. Search gives breadth, fetch gives depth; a search excerpt is never a source.

## References (read when the step needs them)

- `references/url-patterns.md`: catalog API, URL patterns, discovery rules, NN numbering. Steps 2-4.
- `references/tutorial-template.md`: skeleton of the tutorial and the gaps file, with exercise examples. Steps 9 and 11.
- `references/style-guide-pl.md`: the single owner of every format and rule (language, tags, flag/quiz/exercise/inventory/skill-map/coverage/gaps/source formats, mechanical checks). Read before step 7, keep open while writing.

## Workflow

1. **Parse the arguments:** exam code or Learn URL, module (name or number), optional `--out <folder>`. Ask (AskUserQuestion) for anything missing; offer `<cwd>/tutorial` as the `--out` default. **Non-interactive run:** use the arguments given; module = the one given, else the first of the course; `--out` = `<cwd>/tutorial`; list every assumed default in the report. Everything this run writes goes under `<out>`.
2. **Resolve the exam** with the discovery rules in `url-patterns.md`: certification, study guide, course, all learning paths. Never stop at the first path.
3. **List the modules** (number, title, path, in the course or not, exercise unit shown on the fetched module page or not). Ask which one.
4. **Settle file names:** tutorial `<out>/NN-<slug>.md` (overwrite or new name if it exists); gaps file per style guide section 6 (created only if step 9 finds an orphan). Never write outside `<out>`.
5. **Fetch the module page** and read the unit list from it.
6. **Fetch every unit in full** (introduction, exercise, assessment, summary) and lab READMEs on GitHub; save per style guide section 11. Assessment not fetchable: record `status: not-fetchable`, plan the author quiz (section 4.3), report it.
7. **Build `_inventory.md`:** one row per element of every unit, `gdzie w tutorialu` = `DO USTALENIA` (format: section 7).
8. **Map the exam skills.** Fetch the study guide; if it announces a change, ask for the exam date and record "as of". Build or reuse `skill-map.md` (section 8) with two-stage ownership evidence: (a) candidate lookup with `microsoft_docs_search` on 1-3 key terms per skill, results filtered by the course modules' URL prefix; (b) targeted learn-cli fetch of only the candidate modules' units to confirm the term. Record the evidence level per skill; never label a skill as owned on a module title alone. Expected cost: a few searches per skill plus a few fetches per candidate module, not every unit of every module. For large courses the user may accept `kandydat` evidence. Unmatched skill = orphan -> gaps file; a skill with an owning module never goes there.
9. **Fill the gaps.** Thin skills owned by this module: extra sections from other Learn pages or product docs, each tagged. Skills owned elsewhere: rows in the coverage table (section 9). Each orphan: a gaps-file section (section 6); no orphans: no gaps file, `n/a - no orphans` in skill-map. A gaps section whose skill now has an owner is reported, not deleted.
10. **Check currency.** Verify every version pin, runtime, SKU, API version and CLI flag, every `[autor]` technical claim and every example tag (style guide section 3); stamp date and source (4.6) or warn. *Why:* Learn units lag behind products.
11. **Write the tutorial** from the template, following the style guide. Exercise block, cost and cleanup, no-exercise-unit fallback and lab/unit mismatch: section 5. Fit exercises to the product (YAML/gh for GitHub; az CLI, portal, PowerShell or Bicep for Azure). The "Pokrycie egzaminu" table is generated from `skill-map.md` (section 9).
12. **Run the self-check** below. Fill `gdzie w tutorialu` for every inventory row (no `DO USTALENIA` or `DO DODANIA` may remain); a teachable fact the tutorial lacks is added, not skipped. Fix every failure.
13. **Report:** assumed defaults; files written; coverage map per unit with every skipped element and reason; orphans added or updated; inferred quiz answers or the author-quiz fallback; evidence levels that are `kandydat` or weak; anything unverified; `tool:` values that are not verbatim copies.

## Self-check (all must pass before step 13)

1. **Coverage:** every unit maps to a section; every `_inventory.md` row has a section ID or an allowed `pominięte` reason (section 7); every exam skill in this module's area is a row of the coverage table (from skill-map); every orphan is in the gaps file; no skill is in both.
2. **Inventory integrity:** the token check of section 7 passes (each covered row's `token` is found in its section).
3. **Mechanical checks:** run the commands of style guide section 12 (code fences, `<details>`, leftover markers, source files, version pins, nothing outside `<out>`).
4. **Sources:** every theory and gaps `##` section has `_Źródło:`; every author technical claim is `[docs: URL]` or `[autor: niezweryfikowane]`; every MS error is flagged in the standard format.
5. **Quiz and control questions:** inferred answers marked, author questions labelled; control answers agree with the theory (keys, counts, limits checked explicitly); numbering sequential.
6. **Exercises:** all fields present incl. a "zepsuj to" task, runnable code or numbered steps, no forward references; Koszt and a real Sprzątanie for cloud or paid resources.
7. **Currency:** version pins carry date and source, or a warning.
8. **Plain Polish for a beginner:** short sentences; every English term and jargon word explained at first use; Czas stated "orientacyjnie" from module durations and exercises.

## Rules that prevent the common failures

- Fetch, never guess: a fact without a fetched source is `[autor: niezweryfikowane]` or a warning.
- When Learn text and product docs disagree, follow the product docs and flag the Learn error.
- Scope: this module's units; other modules are pointers in the coverage table; orphans go to the gaps file.
- Ask rather than assume when discovery is ambiguous (several courses, several gaps files, unknown exam date).
