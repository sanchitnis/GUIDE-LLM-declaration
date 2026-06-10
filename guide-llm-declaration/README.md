# guide-llm-declaration

An agentic skill for building and finalising an **AI usage declaration** for research papers, based on the [GUIDE-LLM checklist](https://llm-checklist.com) (Feuerriegel et al., 2026, *Nature Human Behaviour*).

---

## What it does

- Interviews you about your LLM usage and generates a **partial declaration immediately** — you don't need all the answers upfront
- Supports **progressive updates** across the research lifecycle — invoke it again after each phase (data collection, analysis, writing) to fill in new fields
- Accepts prior drafts in any format (Markdown, PDF, DOCX, LaTeX) and merges new answers in
- Runs a **completeness check** before finalising, flagging any missing required fields
- Outputs a **submission-ready Markdown appendix** (`GUIDE-LLM-Declaration-[Title]-[Date].md`) to attach as supplementary material

---

## Installation

This is a skill for [Claude](https://claude.ai) or similar platform. To install:

1. Download [`guide-llm-declaration.skill`](./guide-llm-declaration.skill) *(if using Claude desktop or Cowork)*
2. Or copy the contents of `SKILL.md` into your Claude skill library manually

Once installed, trigger it with phrases like:
- *"Fill in my GUIDE-LLM declaration"*
- *"Document how I used GPT-4 in my study"*
- *"Prepare my AI usage appendix for submission"*
- *"Update my LLM declaration — I've finished the analysis phase"*

---

## Checklist coverage

Covers all mandatory and optional items from GUIDE-LLM v1.1:

| Section | Items |
|---------|-------|
| A — Scope of LLM use | A.1, A.2 |
| B — Model / system details | B.1–B.5 |
| C — Prompts | C.1, C.2 |
| D — Data inputs & privacy | D.1 |
| E — Validation & interpretation | E.1, E.2 |
| F — Reproducibility | F.1 |
| G — Competing interests | G.1 |
| Optional | Justification, prompt design rationale, comparisons, bias, transcripts, ethics, compute |

---

## Files

```
guide-llm-declaration/
├── SKILL.md                              ← skill instructions for Claude
├── references/
│   └── checklist-items.md               ← full item text and guidance
└── assets/
    └── blank-declaration-template.md    ← starter template
```

---

## Cite

If you use this skill in your research workflow, please cite the underlying checklist:

> Feuerriegel, S., Barrie, C., Crockett, M. J., et al. (2026). *A reporting checklist for LLMs in behavioural science.* Nature Human Behaviour. DOI: [10.1038/s41562-026-02492-7](https://doi.org/10.1038/s41562-026-02492-7)

---

## License

MIT — use freely, adapt openly.
