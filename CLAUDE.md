# CLAUDE.MD -- Economics Research Paper Workflow

<!-- HOW TO USE: This is a general-purpose economics paper writing agent.
     Paper-specific details (title, data, hypotheses) go in MEMORY.md.
     Keep this file under ~150 lines — Claude loads it every session.
     See the guide at docs/workflow-guide.html for full documentation. -->

**Domain:** Economics Research (Empirical & Applied)
**Econometrics Software:** Stata (connected via MCP)
**Output Format:** Word (.docx)
**Branch:** main

---

## Core Principles

- **Plan first** -- enter plan mode before non-trivial tasks; save plans to `quality_reports/plans/`
- **Verify after** -- run Stata code and confirm output at the end of every task
- **Single source of truth** -- Stata `.do` files are authoritative for analysis; Word `.docx` is authoritative for prose
- **Quality gates** -- nothing ships below 80/100
- **[LEARN] tags** -- when corrected, save `[LEARN:category] wrong → right` to MEMORY.md
- **Reproducibility** -- every result in the paper must trace back to a specific `.do` file and log

---

## Folder Structure

```
project/
├── CLAUDE.MD                    # This file
├── .claude/                     # Rules, skills, agents, hooks
├── Paper/                       # Word .docx drafts (main output)
│   ├── main.docx                # Current working draft
│   ├── tables/                  # Formatted tables (.docx or .rtf from Stata)
│   └── figures/                 # Figures (.png, .pdf from Stata)
├── Code/
│   ├── master.do                # Master do-file (runs everything in order)
│   ├── 00_setup.do              # Paths, packages, settings
│   ├── 01_dataprep/             # Data cleaning and variable construction
│   ├── 02_analysis/             # Main regressions and estimation
│   ├── 03_robustness/           # Robustness checks and sensitivity
│   └── 04_appendix/             # Appendix results
├── Data/
│   ├── raw/                     # Source data (never modified)
│   └── derived/                 # Processed datasets
├── Output/
│   ├── tables/                  # Raw Stata output (.csv, .tex, .rtf)
│   ├── figures/                 # Graphs (.png, .pdf)
│   └── logs/                    # Stata .log files
├── Literature/                  # Reference papers and notes
├── quality_reports/             # Plans, session logs, merge reports
├── explorations/                # Research sandbox (see rules)
├── templates/                   # Session log, quality report templates
└── References/                  # Bibliography files (.bib or reference lists)
```

---

## Commands

```bash
# Stata execution via MCP
# Use stata-mcp tools: stata_do, write_dofile, append_dofile, read_log, get_data_info

# Run a do-file
stata_do: "do Code/master.do"

# Check data structure
get_data_info: "Data/derived/analysis_sample.dta"

# Read Stata log for errors
read_log: "Output/logs/analysis.log"

# Word document generation
# Use python-docx via bash for programmatic .docx creation
python3 scripts/generate_paper.py
```

---

## Quality Thresholds

| Score | Gate | Meaning |
|-------|------|---------|
| 80 | Commit | Good enough to save |
| 90 | PR | Ready for co-author review |
| 95 | Excellence | Ready for submission |

---

## Skills Quick Reference

| Command | What It Does |
|---------|-------------|
| `/run-stata [file]` | Execute do-file via MCP, check log for errors |
| `/create-docx [section]` | Generate or update Word document section |
| `/format-table [file]` | Convert Stata output to publication-ready Word table |
| `/proofread [file]` | Grammar/typo/consistency review |
| `/review-paper [file]` | Full manuscript review with referee objections |
| `/review-stata [file]` | Stata code quality and reproducibility review |
| `/validate-references` | Cross-reference citations in paper |
| `/devils-advocate` | Challenge identification strategy and research design |
| `/commit [msg]` | Stage, commit, PR, merge |
| `/lit-review [topic]` | Literature search + synthesis |
| `/research-ideation [topic]` | Research questions + strategies |
| `/interview-me [topic]` | Interactive research interview |
| `/data-analysis [dataset]` | End-to-end Stata analysis pipeline |
| `/learn [skill-name]` | Extract discovery into persistent skill |
| `/context-status` | Show session health + context usage |
| `/deep-audit` | Repository-wide consistency audit |

---

## Stata Conventions (Summary)

| Convention | Rule |
|------------|------|
| Random seed | `set seed YYYYMMDD` at top of every do-file |
| Logging | `log using "Output/logs/filename.log", replace text` |
| Paths | All relative to project root; set in `00_setup.do` via globals |
| Packages | Document all `ssc install` in `00_setup.do` |
| Output | `esttab` / `outreg2` → `.csv` or `.rtf` in `Output/tables/` |
| Figures | `graph export` → `.png` (300dpi) in `Output/figures/` |

---

## Word Document Standards (Summary)

| Element | Standard |
|---------|----------|
| Font | Times New Roman 12pt, 1.5 line spacing |
| Margins | 1 inch all sides |
| Tables | AER/QJE style: three-line format, SE in parentheses |
| Figures | Centered, numbered, descriptive titles below |
| Citations | Author-year format (APA/AER style) |
| Sections | Introduction, Literature, Data, Method, Results, Robustness, Conclusion |

---

## Current Paper State

<!-- Update this table as you work on specific papers.
     For a new paper, add a row. Move details to MEMORY.md. -->

| Paper | Status | Key Files | Notes |
|-------|--------|-----------|-------|
| [Paper 1 Title] | [Draft/Analysis/Revision] | `Code/02_analysis/main_reg.do` | [Brief note] |
