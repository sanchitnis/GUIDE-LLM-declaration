---
name: guide-llm-declaration
description: >
  Generate, progressively build, and finalize an AI usage declaration for a research paper using the GUIDE-LLM checklist (Feuerriegel et al., 2026, Nature Human Behaviour). Use this skill whenever a researcher needs to declare, document, or report AI/LLM usage in a study — even if they say "add AI disclosure", "write the AI section", "fill in the LLM checklist", "prepare my AI declaration", "document how I used Claude/GPT/Gemini in my research", or "append AI usage to my paper". The output is always a Markdown declaration appendix, suitable for direct inclusion in a manuscript. Supports incremental updates — the researcher can invoke this skill multiple times as their study progresses, updating fields as decisions are made. Accepts input in any format (PDF, DOCX, .tex, plain text, prior GUIDE-LLM draft).
---

# GUIDE-LLM Declaration Skill

This skill helps researchers build a complete, accurate GUIDE-LLM checklist declaration that can be appended as a supplementary section to any research paper. The declaration tracks AI/LLM usage across the full research lifecycle.

**Citation to embed in all outputs:**
> Feuerriegel, S., Barrie, C., Crockett, M. J., et al. (2026). *A reporting checklist for LLMs in behavioural science.* Nature Human Behaviour. DOI: [10.1038/s41562-026-02492-7](https://doi.org/10.1038/s41562-026-02492-7)

---

## Step 0 — Input Handling

Before doing anything else, check what the researcher has provided:

| Input type | Action |
|---|---|
| No prior draft | Proceed to Step 1 (Interview) |
| Prior Markdown draft | Load it, identify blank/N/A fields, proceed to Step 2 (Fill gaps) |
| DOCX / PDF / .tex file | Use the **file-reading** skill or **pdf-reading** skill to extract content, map to checklist fields, then proceed to Step 2 |
| Conversational description | Extract answers from conversation history, map to fields, confirm with researcher, then proceed to Step 2 |

If the input is a `.tex` file (such as GUIDE-LLM.tex), parse the `longtable` environments to extract item labels (A.1, B.1, etc.) and any existing answers in the second column.

---

## Step 1 — Interview (First Invocation)

If no prior draft exists, ask the researcher the following in a single message. Keep it conversational — do not ask all 30+ checklist items at once. Start with the high-level scope, then drill down.

### Opening questions (always ask these first)

1. **Paper title / working title** — for the declaration header
2. **Scope of LLM use** — which stages? (research design / data processing / analysis / LLM as object / participant-facing / writing & editing)
3. **Which LLM(s) were used?** — provider, model name, exact version if known, date accessed
4. **How were they accessed?** — API / web interface / local / other
5. **Were outputs reviewed by a human, or fully automated?**

After receiving answers, generate a **partial draft** immediately (Step 3), marking unknown fields as `<!-- TODO: fill in -->`. Tell the researcher which fields still need input and offer to collect them in follow-up turns.

---

## Step 2 — Progressive Update Mode

When the researcher returns with more information (e.g., "I finished the data collection phase"), or uploads a new version of their draft:

1. Load the existing Markdown declaration
2. Identify which fields have changed or were left as TODO
3. Ask targeted questions only for the new phase/fields
4. Merge answers into the declaration
5. Output the updated full declaration

This allows the declaration to grow organically as the research progresses.

---

## Step 3 — Generate the Declaration

Output the declaration as a Markdown document using the structure below. All fields map 1:1 to GUIDE-LLM checklist items. See `references/checklist-items.md` for full item text and guidance.

### Declaration template

````markdown
---
# AI Usage Declaration
**GUIDE-LLM Checklist** (v1.1)  
Feuerriegel et al. (2026). *A reporting checklist for LLMs in behavioural science.*  
Nature Human Behaviour. DOI: [10.1038/s41562-026-02492-7](https://doi.org/10.1038/s41562-026-02492-7)

**Paper:** [Paper title]  
**Prepared by:** [Author name(s)]  
**Date:** [Date of last update]

---

## Section A — Scope of LLM Use

| Item | Response |
|------|----------|
| **A.1** Purposes of LLM use | [e.g., "Research design (hypothesis generation), Analysis (data labeling), Communication (editing)"] |
| **A.2** Degree of automation | [e.g., "All outputs reviewed by PI; no automated pipeline"] |

---

## Section B — Model / System Details

| Item | Response |
|------|----------|
| **B.1** Model name, provider, version, date, source | [e.g., "claude-sonnet-4-20250514 (Anthropic); accessed via Claude.ai web interface, May 2025"] |
| **B.2** Access mode & context mode | [e.g., "Web interface, chat mode (persistent context window)"] |
| **B.3** Relevant configurations | [e.g., "Default settings; no custom temperature or sampling parameters"] |
| **B.4** Customization | ☐ Base model / ☐ Fine-tuning / ☐ RAG / ☐ Automated prompt optimization / ☐ Tool/function calling / ☐ Web search / ☐ Agentic workflows / ☐ Other — Description: [value] |
| **B.5** Persistent memory across sessions | ☐ Yes / ☑ No / ☐ N/A |

---

## Section C — Prompts

| Item | Response |
|------|----------|
| **C.1** Exact prompts reported | [Include verbatim prompts or link to repository] |
| **C.2** System-wide instructions | [e.g., "No system prompt used; default assistant mode"] |

---

## Section D — Data Inputs & Privacy

| Item | Response |
|------|----------|
| **D.1** Handling of personal/sensitive data | [e.g., "No personal data were processed. All inputs were anonymized research texts."] |

---

## Section E — Validation & Interpretation

| Item | Response |
|------|----------|
| **E.1** Human validation of LLM outputs | ☐ Yes / ☐ No / ☐ N/A — Description: [value] |
| **E.2** Post-processing steps | [e.g., "Outputs were manually reviewed and reformatted into CSV; no automated parsing"] |

---

## Section F — Reproducibility

| Item | Response |
|------|----------|
| **F.1** Code/scripts shared | ☐ Yes / ☐ No / ☐ N/A — Link/DOI: [value] |

---

## Section G — Competing Interests

| Item | Response |
|------|----------|
| **G.1** Funding, support, affiliations | ☐ Yes / ☑ No — Description: [value] |

---

## Optional Items

| Item | Response |
|------|----------|
| Justification for LLM choice | ☐ Performance / ☐ Transparency / ☐ Reproducibility / ☐ Ethical / ☐ Other |
| Rationale for prompt design | [value or N/A] |
| Comparison against other LLMs/methods | ☐ Yes / ☐ No / ☐ N/A |
| Training data leakage risks | ☐ Yes / ☐ No / ☐ N/A |
| Potential bias in LLM behavior | ☐ Yes / ☐ No |
| Conversation transcripts | ☐ Yes / ☐ No / ☐ N/A |
| Ethical implications | [value or N/A] |
| Computational resources | [value or N/A] |

---

*This declaration was prepared using the GUIDE-LLM checklist (v1.1). For the full checklist and guidance, see [llm-checklist.com](https://llm-checklist.com).*
````

---

## Step 4 — Finalisation Check

Before outputting the final declaration (when the researcher signals the paper is ready for submission), run through this checklist mentally:

- [ ] All A–G sections have responses (not `<!-- TODO -->`)
- [ ] Model name includes provider + exact version + date accessed
- [ ] Prompts are either included verbatim or a repository link is given
- [ ] B.4 checkboxes reflect actual customizations used
- [ ] Privacy handling is addressed (even if answer is "no personal data")
- [ ] If multiple LLMs were used for different purposes, each has its own Section B–C block
- [ ] Citation to Feuerriegel et al. (2026) is present

If any required fields are still blank, prompt the researcher to fill them before finalizing.

Flag optional items that are particularly relevant given the research context:
- If LLM was **participant-facing** → flag conversation transcripts and ethics
- If LLM was used for **data labeling** → flag human validation (E.1) and inter-rater reliability
- If **sensitive/personal data** → flag D.1 carefully; note applicable data protection frameworks (e.g., GDPR, HIPAA, or relevant national law)

---

## Step 5 — Output the Final Markdown File

When the researcher is satisfied, output the completed declaration as a standalone `.md` file named:

```
GUIDE-LLM-Declaration-[PaperShortTitle]-[YYYY-MM-DD].md
```

Include at the top:
- Paper title
- Date of declaration
- GUIDE-LLM version (1.1)
- Citation to Feuerriegel et al. (2026)

Tell the researcher: "Attach this file as a supplementary appendix to your manuscript submission."

---

## Reference files

- `references/checklist-items.md` — Full text of all GUIDE-LLM items A.1–G.1 plus all optional items, with explanations. Read this when the researcher asks about a specific item or when generating detailed guidance.
