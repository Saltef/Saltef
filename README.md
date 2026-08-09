# Hi, I'm Safea

## Applied AI · LLM evaluation · retrieval · Arabic NLP · healthcare data · Canada

I work on machine learning, NLP, and LLM evaluation, mostly on problems where the data is messy, the labels are debatable, and someone is going to make a real decision based on what I say.

I'm an **AI Data Trainer and Evaluator at Cohere**, scoring model outputs against rubrics for accuracy, instruction adherence, safety, and information quality, and writing the annotation guidelines that keep those judgments consistent across reviewers. Before that I was a **Machine Learning Associate at the Vector Institute**, where I took a retrieval-augmented teaching agent from an open business question to a deployed system on GCP.

Most of my public work is about the same problem from different angles: how do you tell whether a language model is actually doing the thing you think it's doing, when the output looks correct either way.

---

## Projects

### CANON

**[Repository](https://github.com/Saltef/canon)** · `Python` `FastAPI` `Qdrant` `Docker` `Render` `Prometheus` `OpenTelemetry` `pytest` `BEIR`

A human-in-the-loop evidence briefing workbench. It ingests a controlled corpus, runs a five-stage retrieval pipeline of BM25, embedding, reciprocal rank fusion, reranking, and synthesis, and produces cited evidence packets a reviewer can inspect for where support is weak, missing, or contested. The core package is stdlib-first; hosted model calls go through HTTP APIs when keys are configured.

The interesting part is what the benchmarking said.

**Negative result.** Benchmarked against BEIR SciFact and NFCorpus qrels under a fixed protocol, with a strong encoder, single-stage dense retrieval outperformed the full five-stage pipeline. The added stages did not earn their keep once the encoder was good enough.

**Withdrawn result.** An earlier run favoured the full pipeline. It had a confound: the two arms used different encoders. I found it, reran the comparison properly, and published what came back rather than the version I preferred.

**Reproducibility control.** The default `hashed-semantic-v1` encoder is a deterministic lexical hash, not a neural model, and is documented as such. It exists so pipeline effects can be separated from encoder effects.

**Review boundary.** Automated judge output stays provisional until a human reviews it. Automated checks can say "ready for human review." They are not used to claim final quality or unsupported-claim rates.

### HandoffLens

**[Repository](https://github.com/Saltef/handofflens)** · `Python` `multi-provider LLM APIs` `Node` `Docker Compose` `pytest` · browser review interface

Source-grounded extraction from hospital discharge-summary-style text. The question it asks: how do you make an LLM extraction system prove where its claims came from, and fail visibly when it cannot.

**Structured output is not the same thing as grounded output.** In a 400-case engineering run, roughly 88% of baseline outputs passed JSON schema validation, but only a small minority survived an exact-source provenance check. Schema validity carried almost no information about whether a field had an auditable source anchor. A pipeline gated only on structure would have shipped blind to grounding.

**It is not a hallucination rate.** A miss taxonomy separates exact-match failures into normalization artifacts, non-contiguous quotations, pointer drift, label-supported unresolved quotes, weak-overlap review cases, and low-overlap possible fabrication. Most misses were quote assembly across non-contiguous spans, not invented content. That changes the fix from hallucination control to span handling.

**Provider interaction, against prediction.** A cross-provider ablation tested replacing free-text quotes with constrained source-span IDs. Cohere Command A+ improved from 64.5% to 88.3% supported items. Anthropic Claude Haiku 4.5 went the other way, from 93.6% down to 67.0%, mostly over-selecting spans after hosted schemas stripped a local cap. A pre-registered prediction said the schema would help both. It didn't.

**Labelled by construction.** The `compact_extractive` repair reaches 1.0000 lexical source support. That is expected by construction, since the repair emits source spans. It is reported as a gate diagnostic, not as proof of semantic factuality.

**Architecture.** Candidate-first: deterministically identify source candidates, preserve exact quotations and stable IDs, ask the model only to classify ambiguous ones, apply provenance and consistency gates, abstain when evidence is insufficient, and materialize labels only from accepted evidence. An archived appendix runs conformal selective routing on BioScope at alpha 0.10 using proxy labels, as escalation-policy research rather than a safety mechanism.

### DermaLens

**[Repository](https://github.com/Saltef/DermaLens)** · `Python` `FastAPI` `ONNX` `Docker`

A local-first facial skin screening prototype. Inference runs on localhost, EXIF metadata is stripped on upload, and images are not retained by default.

The application is straightforward. The methodological record is the substance of the project.

**Case-level leakage.** The original preparation code could split multiple images from the same patient case across train and validation, inflating validation scores. Case-grouped splitting is now the default, with an overlap assertion and a `split_audit.json` written for every prepared dataset.

**Rejected result.** A validation-tuned ensemble reached 81.4% accuracy and did not reproduce under fresh holdout testing, at 64.0% to 73.0% across four split seeds. It is retained as a diagnostic upper bound, not a performance claim.

**Negative result.** A probe using Google's `derm-foundation` embeddings as a frozen representation underperformed the deployed baseline. Domain-specific pretraining did not compensate for noisy label mapping.

**Subgroup reporting.** Fitzpatrick and Monk skin-tone metrics are reported across the same grouped split seeds. The darker Monk buckets are underpowered, and the audit is described as a process demonstration rather than a fairness claim.

Macro recall was tracked alongside accuracy throughout, since accuracy alone rewards majority-class collapse on imbalanced data. **[Full write-up](https://github.com/Saltef/DermaLens/blob/main/PORTFOLIO_WRITEUP.md)**

---

## In progress

**Kinera.** A sensor framework for detecting functional decline in older adults ageing in place, connecting IoT architecture to geriatric care research. MSc capstone, presented at the Vector Institute's *Remarkable 2026* showcase. Not yet public.

**CareGap.** Modelling healthcare access and system capacity in Ontario, aiming to identify where demand is emerging and where capacity gaps produce delays and unmet need. Not yet public.

---

## What I'm good at

**Specifying ambiguous problems.** Turning "is the program working" or "is the model good" into taxonomies, rubrics, classification schemas, and defined metrics. Applied to monitoring and evaluation across a $45M USAID-funded portfolio, and to LLM classification pipelines at the Vector Institute.

**Evaluating LLMs honestly.** Benchmarks plus human judgment. Building the rubric out of expert feedback rather than imposing it upfront, and reporting the results that contradict what I expected.

**Retrieval systems.** RAG pipelines, hybrid lexical and dense retrieval, reranking, embeddings. The kind that can show its work.

**Healthcare data.** EMRs under real privacy constraints, cohort and longitudinal models, dementia care pathways. This is where my domain knowledge is deepest.

**Arabic NLP.** Transformer modelling, annotation pipelines, corpus building for a language that most tooling treats as an afterthought.

---

## Methods and tools

```
Python · R · SQL
PyTorch · scikit-learn · transformers · sentence-transformers · ONNX Runtime · Argilla
RAG and embedding pipelines · Qdrant · BM25 and hybrid retrieval · reranking · BEIR
FastAPI · Docker · Render · Git · GitHub Actions · pytest · ruff · GCP
Longitudinal and time series analysis · regression · cohort modelling · segmentation · Power BI · Tableau
```

---

## Education

M.Sc. Big Data Analytics, **Trent University**
M.A. Media and Cultural Studies, **Doha Institute for Graduate Studies**
B.S. Economics, **Lebanese American University**

Arabic (native), English (full professional), Spanish (limited working).

---

## Publications

Economics, then media and cultural studies, then big data analytics. Two master's degrees and a period working in Arabic computational linguistics.

The practical effect of that path is that I treat problem specification as the substantive step rather than a preliminary one. Method selection is usually the easier decision, and it depends on getting the prior question right: what is being asked, what would count as an answer, and what the available data can bear.

The published work spans four domains, and the recurring pattern is the same each time. Enter an unfamiliar field, learn it to the standard the field requires for publication, work out what in it can be measured, and then apply quantitative methods inside those constraints rather than imported from outside them. Situational judgement testing, dementia referral pathways, Arab news media, and Libyan visual art each needed a different definition of what counts as evidence before any method was appropriate. That is the transferable skill, more than any individual technique.

**MacIntosh A, Henning C, Altef S, et al.** Validity of constructed-response situational judgement tests in health professions education: a systematic review and meta-analysis. *Medical Education*, 2026. [doi:10.1111/medu.70245](https://doi.org/10.1111/medu.70245)
Systematic review methodology and meta-analysis across a heterogeneous assessment literature. The hard part was construct definition: deciding what counted as the same instrument across studies that measured it differently.

**Jebril N, Altef S.** Perceptions of data journalism and its impact on democratising Arab news media. *Journalism*, 2024;25(7):1500 to 1518.
Qualitative study of practitioner perceptions across Arab newsrooms. Not a computational paper, and I don't present it as one.

**Altef S.** Cultural identity in Libyan and Yemeni social media visual art. In *Media and Democracy in the Middle East*, pp. 100 to 117. Routledge, 2023.
Book chapter from my MA thesis. Visual and discourse analysis of Arabic-language social media during and after conflict.

**Ingram KJ, Carr D, Arsenault-Lapierre G, Altef S.** Impact of an embedded memory team in primary care. *Alzheimer's and Dementia*, 2025;21(Suppl 4):e103774.
Conference abstract presented at AAIC. Full manuscript in preparation. Three years of longitudinal EMR analysis comparing referral rates and diagnostic timelines between intervention and control groups.

ORCID: [0000-0002-8916-5738](https://orcid.org/0000-0002-8916-5738)

---

**Open to applied AI, LLM evaluation, and data science roles.**
[LinkedIn](https://www.linkedin.com/in/safea-altef)
