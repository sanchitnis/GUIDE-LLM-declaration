# GUIDE-LLM Checklist — Full Item Reference

Source: Feuerriegel et al. (2026). *A reporting checklist for LLMs in behavioural science.*  
Nature Human Behaviour. DOI: 10.1038/s41562-026-02492-7  
Version: 1.1 | https://llm-checklist.com

---

## Section A — Scope of LLM Use

### Item A.1 — Purposes of LLM use
Briefly describe how and for what purposes LLMs were used in the study. This may include one or multiple stages of the research workflow:
- **Research design** (e.g., hypothesis generation, literature search, or creating surveys/stimuli)
- **Data processing** (e.g., transcription, translation, data extraction, or data cleaning)
- **Analysis** (e.g., data labeling, summarization, pattern detection, statistical analysis, or code generation)
- **LLM as research object** (e.g., studying LLM behavior, benchmarking LLMs, or bias assessment of LLMs)
- **Participant-facing settings** (e.g., LLM used as an intervention, studying human interactions with LLM chatbots)
- **Communication** (e.g., paper writing, editing, or reviewing)

Depending on the specific use case, different checklist items may later be relevant. It may be necessary that later items are reported separately for each use case.

### Item A.2 — Degree of automation
Indicate how much human oversight was involved. Specify whether each output was reviewed, edited, or approved by a person, or whether outputs were used automatically without supervision. For participant-facing tasks, state whether humans checked outputs before showing them to participants or whether participants interacted with the LLM directly. Specify who provided oversight (e.g., student assistant, expert, PI).

---

## Section B — Model / System Details

### Item B.1 — Model identification
Report the exact model names including provider, version, and date accessed. Avoid generic labels like "ChatGPT" or "GPT-4"; instead use detailed model names such as:
- "GPT-4o-mini-2024-12-17 (OpenAI)"
- "Llama-3.1-8B (Meta; accessed via HuggingFace in May 2025)"
- "claude-sonnet-4-20250514 (Anthropic; accessed via Claude.ai web interface)"

For locally deployable models, also enter a source link (e.g., HuggingFace URL). If multiple models were tested, name them and explain which was used in the final study and why. When multiple models served different purposes, specify their respective roles consistent with A.1.

### Item B.2 — Access mode and context mode
Note how you accessed the models (API, web interface, local installation) and whether you used LLMs in chat mode (ongoing conversation) or stateless mode (separate prompts). Mention the exact API name and version, since different access modes may influence responses.

### Item B.3 — Relevant configurations
List any configuration settings that may affect outputs:
- **Temperature** — controls randomness of output
- **Sampling parameters** — top_k, top_p, max tokens
- **Penalties** — frequency penalty, presence penalty
- **Stop sequences** — e.g., ["\n\n", "END"]
- **Number of completions or runs** — used to capture output variability
- **Quantization level** — e.g., FP16, INT8, INT4
- **Reasoning-related settings** — structured reasoning, reasoning effort level, inference budget constraints

### Item B.4 — Customization
Check and describe modifications beyond standard inference:
- Fine-tuning (e.g., via LoRA)
- Retrieval-augmented generation (RAG)
- Automated prompt optimization (e.g., DSPy)
- Web search integration
- Agentic workflows (e.g., LangChain, AutoGPT, CrewAI)
- Post-training refinements (RLHF, DPO)

**Checkbox options:** Base model / Fine-tuning / RAG / Automated prompt optimization / Tool/function calling / Web search / Agentic workflows / Other adaptations

### Item B.5 — Persistent memory
Indicate whether the LLM could "remember" previous conversations. Unless memory is disabled, there may be spillover effects from other chat windows or prior conversations, which can influence outputs even when not intended.

**Options:** Yes / No / N/A

---

## Section C — Prompts

### Item C.1 — Exact prompts
Whenever possible, include the exact text of prompts used, including in-context examples or demonstrations. Even small wording changes can substantially affect outputs. If full prompts cannot be shared (privacy/length), include a redacted or representative example or link to a repository (OSF, GitHub).

### Item C.2 — System-wide instructions
Note any system-level instructions that guide the model's general behavior (e.g., "You are a helpful assistant."). These may not be directly visible but can be accessed through the API.

---

## Section D — Data Inputs & Privacy

### Item D.1 — Handling of personal or sensitive data
If any personal, sensitive, or identifiable data were processed, describe:
- Whether participants explicitly consented to their data being analyzed with an LLM
- De-identification, anonymization, or masking steps taken
- Whether the LLM provider offers safeguards (e.g., excluding inputs from training)
- Where data were stored or processed
- Cross-border transfer implications (GDPR, HIPAA, DPDPA 2023, etc.)

Note: Some providers (e.g., OpenAI) may log or inspect prompts even when data are not used for training. For sensitive datasets, zero-retention configurations may be required.

---

## Section E — Validation & Interpretation

### Item E.1 — Human validation
Describe whether and how human reviewers examined model outputs:
- Reviewers' roles and expertise
- Number of reviewers
- Dimensions examined (accuracy, hallucination detection, citation correctness, inter-rater reliability)
- Selection procedure for reviewed outputs (all, random sample, oversampled cases)
- Reviewer training, instructions, rating scales
- How disagreements were resolved
- Cohen's κ or Krippendorff's α if applicable
- Whether reviewer feedback was used for validation or also to refine prompts

**Options:** Yes / No / N/A

### Item E.2 — Post-processing
Describe any steps taken to clean or reformat LLM outputs:
- Converting outputs to numeric codes
- Handling missing values or malformed entries
- Parsing embedded values from free text
- Whether automated scripts or manual corrections were used
- Whether any data were excluded or reinterpreted

---

## Section F — Reproducibility

### Item F.1 — Code/notebooks/scripts shared
Indicate whether you have shared materials such as code, prompts, logs, or transcripts. Remove sensitive information (API keys, private data). For code, add a README file.

**Options:** Yes / No / N/A — Link/DOI: [value]

---

## Section G — Competing Interests

### Item G.1 — Funding, support, affiliations
Disclose any current or past funding, support, or other relevant relationships with entities that have a financial interest in LLMs. This includes:
- Research funding from AI companies (OpenAI, Anthropic, Google, Meta, Microsoft)
- In-kind access to compute or models
- Current or former professional affiliations
- Personal investments (stocks) in AI companies
- Familial relationships with AI company employees

Disclose regardless of whether you believe they impacted the research.

**Options:** Yes (Description) / No — Link/DOI: [value]

---

## Optional Items

### Justification for LLM choice
Explain why this model was chosen:
- **Performance** — suited to research needs
- **Transparency** — open/closed-weight, training data availability
- **Reproducibility** — determinism, version stability
- **Ethical considerations** — data privacy, safety
- **Cost or ease-of-use**

### Rationale for prompt design
Explain how prompts were designed:
- Structured format (task description, definitions, step-by-step instructions, output constraints)
- Established prompt engineering guidelines
- Adapted from earlier studies
- Automated prompt optimization
- Iterative refinement (pilot testing, error analysis)
- Few-shot examples and selection criteria
- Standardization across models for comparability

### Comparison against other methods/LLMs
If comparisons were made, describe: comparison methods, metrics, fairness of inputs, and why alternatives were excluded.

### Training data leakage risks
Note whether risks of evaluation materials appearing in model training data were considered. Describe mitigation steps (novelty checks, item restructuring).

### Potential risk of bias or systematic differences
Reflect on whether the model may perform differently across groups, languages, or contexts. Describe any bias checks or mitigation.

### Conversation transcripts
For studies involving direct researcher/participant LLM interaction, provide anonymized transcripts or representative examples.

### Relevant ethical implications
Discuss broader ethical considerations: participant well-being, fairness, safety, autonomy, dual-use risks.

### Computational resources
Report: API call counts, total tokens processed, financial costs, runtime, number and type of GPUs/CPUs, and other relevant compute metrics.
