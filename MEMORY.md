# Project Memory

Corrections and learned facts that persist across sessions.
When a mistake is corrected, append a `[LEARN:category]` entry below.

---

<!-- Append new entries below. Most recent at bottom. -->

## Workflow Patterns

[LEARN:workflow] Requirements specification phase catches ambiguity before planning → reduces rework 30-50%. Use spec-then-plan for complex/ambiguous tasks (>1 hour or >3 files).

[LEARN:workflow] Spec-then-plan protocol: AskUserQuestion (3-5 questions) → create `quality_reports/specs/YYYY-MM-DD_description.md` with MUST/SHOULD/MAY requirements → declare clarity status (CLEAR/ASSUMED/BLOCKED) → get approval → then draft plan.

[LEARN:workflow] Context survival before compression: (1) Update MEMORY.md with [LEARN] entries, (2) Ensure session log current (last 10 min), (3) Active plan saved to disk, (4) Open questions documented. The pre-compact hook displays checklist.

[LEARN:workflow] Plans, specs, and session logs must live on disk (not just in conversation) to survive compression and session boundaries. Quality reports only at merge time.

## Stata Conventions

[LEARN:stata] Stata connects via MCP (stata-mcp). Use `stata_do` to run code, `write_dofile` / `append_dofile` to create do-files, `read_log` to check output, `get_data_info` for descriptive statistics.

[LEARN:stata] Every do-file must start with: `set seed YYYYMMDD`, `log using "Output/logs/filename.log", replace text`, and load global paths from `00_setup.do`.

[LEARN:stata] All paths in do-files are relative to project root. Set globals in `00_setup.do`: `global root "..."`, `global data "$root/Data"`, `global output "$root/Output"`, etc.

[LEARN:stata] Document all user-written packages in `00_setup.do` with `ssc install` commands. Common packages: `reghdfe`, `estout`, `ftools`, `coefplot`, `binscatter`, `did`, `csdid`, `eventstudyinteract`, `hdfe`.

[LEARN:stata] Use `esttab` (from `estout`) for regression tables → export to `.csv` or `.rtf`. Use `graph export` for figures → `.png` at 300dpi. All raw output goes to `Output/tables/` or `Output/figures/`.

[LEARN:stata] Always check log files after running do-files. Search for `error`, `r(...)`, `no observations`, `variable not found` — silent failures in Stata are common and dangerous.

## Word Document Standards

[LEARN:docx] Paper output is Word (.docx). Use python-docx for programmatic generation when needed. Manual editing in Word is also fine — .docx is the authoritative prose file.

[LEARN:docx] Default formatting: Times New Roman 12pt, 1.5 line spacing, 1-inch margins. Tables use three-line format (AER/QJE style). SE in parentheses, significance stars with footnote.

[LEARN:docx] Standard paper structure: Introduction → Literature Review → Institutional Background/Data → Empirical Strategy → Results → Robustness → Conclusion. Adjust per target journal.

[LEARN:docx] Every table and figure in the paper must reference the exact do-file and output file that produced it. Traceability is non-negotiable.

## Research Design

[LEARN:research] Before running regressions, write down the estimating equation, identify the variation, and state the identification assumption. Code follows theory, not the other way around.

[LEARN:research] Replication-first: when working with an existing paper's data, replicate the original results EXACTLY before extending. Tolerance: <0.01 for point estimates, <0.05 for SEs. Mismatch → stop and investigate.

## Documentation Standards

[LEARN:documentation] When adding new features, update BOTH README and guide immediately to prevent documentation drift.

[LEARN:documentation] Guide must be generic (framework-oriented) not prescriptive. Provide templates with examples, let users customize.

## Design Philosophy

[LEARN:design] Framework-oriented > Prescriptive rules. Constitutional governance works as a TEMPLATE with examples users customize to their domain.

[LEARN:design] Quality standard for additions: useful + pedagogically strong + drives usage + leaves great impression + improves upon starting fresh + no redundancy + not slow. All 7 criteria must hold.

## File Organization

[LEARN:files] Specifications go in `quality_reports/specs/YYYY-MM-DD_description.md`. Templates in `templates/`. Do-files in `Code/` by stage (00-04). Raw data never modified in `Data/raw/`.

[LEARN:files] Output separation: `Output/tables/` for raw Stata table exports, `Output/figures/` for graphs, `Output/logs/` for Stata logs. `Paper/tables/` and `Paper/figures/` for final publication-ready versions inserted into the paper.

## Constitutional Governance

[LEARN:governance] Constitutional articles distinguish immutable principles from flexible preferences. Keep to 3-7 articles max.

[LEARN:governance] Example articles for this workflow: Primary Artifact (Stata .do for analysis, .docx for prose), Plan-First Threshold (when to plan), Quality Gate (minimum score), Verification Standard (Stata runs clean + docx opens), File Organization (where files live).

## Skill Creation

[LEARN:skills] Effective skill descriptions use trigger phrases users actually say: "run my regression", "format this table", "check my do-file", "draft the introduction" → Claude knows when to load skill.

[LEARN:skills] Skills need 3 sections minimum: Instructions (step-by-step), Examples (concrete scenarios), Troubleshooting (common errors).

## Memory System

[LEARN:memory] Two-tier memory: MEMORY.md (generic patterns, committed), personal-memory.md (machine-specific paths, Stata version, gitignored) → cross-machine sync + local privacy.

## Current Papers

<!-- When starting a new paper, add an entry here with:
     - Paper title / working title
     - Research question (1 sentence)
     - Data source
     - Identification strategy
     - Current status
     This section is your quick-reference for active projects. -->
