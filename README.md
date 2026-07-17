# Hi, I'm Safea
## Applied Data Scientist — ML · NLP · LLM Evaluation · RAG
## Healthcare & real-world data | Arabic-language NLP | Canada


I'm an applied data scientist in Canada. I work on machine learning, NLP, and LLM evaluation, mostly on problems where the data is messy, the labels are debatable, and someone is going to make a real decision based on what I say.

Right now I'm building and evaluating a RAG-based AI system on GCP: retrieval pipelines, prompt design, embeddings, and a lot of careful work on how you actually *measure* whether an LLM is doing what you think it's doing. I'm also an **AI Data Trainer at Cohere**, scoring model outputs against rubrics for accuracy, safety, and alignment.

---

## Background and cross-domain research
 
Economics, then media and cultural studies, then big data analytics. Two master's degrees and a period working in Arabic computational linguistics.
 
The practical effect of that path is that I treat problem specification as the substantive step rather than a preliminary one. Method selection is usually the easier decision, and it depends on getting the prior question right: what is being asked, what would count as an answer, and what the available data can bear.
 
Published or presented work spans four domains:
 
| Domain | Work |
| --- | --- |
| Cultural studies | Transcultural identity in Libyan and Yemeni social media visual art |
| Media and democracy | Perceptions of data journalism and its impact on democratising Arab news media |
| Clinical research | Peer-reviewed work from EMR analysis. Second paper on dementia screening in primary care in preparation |
| Machine learning | Kinera, a sensor framework for detecting functional decline in older adults. Presented at Vector Institute's *Remarkable 2026* showcase |
 
The recurring pattern is entering an unfamiliar domain, learning it to the standard required for publication, and applying quantitative methods within it.
 
---
 
## Applied work
 
**Specification of ambiguous problems.** Converting underdetermined questions ("is the program working", "is the model good") into taxonomies, rubrics, classification schemas, and defined metrics. Applied to monitoring and evaluation for $45M in USAID-funded programs, and to LLM classification pipelines at the Vector Institute.
 
**Reporting for decision timelines.** At Chemonics International I analyzed 240,000+ survey responses across four programs and built the Power BI reporting layer, reducing reporting time by roughly 50% and shortening the interval between analysis and leadership review by about two weeks.
 
**Applied settings with real consequences.** Dementia care pathways, healthcare capacity, and program evaluation in conflict-affected countries.
 
---

## What I'm good at

**Evaluating LLMs honestly.** Benchmarks plus human judgment, rubrics, taxonomies, and turning "we'll know it when we see it" into something you can actually audit.

**Retrieval systems.** RAG pipelines, embeddings, semantic search. The kind that can show its work.

**Healthcare data.** EMRs under real privacy constraints, cohort and longitudinal models, dementia care pathways. This is where my domain knowledge is deepest.

**Arabic NLP.** Transformer modeling, annotation pipelines, corpus building for a language that most tooling treats as an afterthought.

---

## DermaLens
 
**[Repository](https://github.com/Saltef/DermaLens)** · `Python` `FastAPI` `ONNX` `Docker`
 
A local-first facial skin screening prototype. Inference runs on localhost, EXIF metadata is stripped on upload, and images are not retained by default. Stack is FastAPI, ONNX Runtime, and Docker, with CI running lint and tests.
 
The application is straightforward. The methodological record is the substance of the project:
 
**Case-level leakage.** The original preparation code could split multiple images from the same patient case across train and validation, inflating validation scores. I made case-grouped splitting the default and added an overlap assertion plus a `split_audit.json` written for every prepared dataset.
 
**Rejected result.** A validation-tuned ensemble reached 81.4% accuracy. It did not reproduce under fresh holdout testing (64.0% to 73.0% across four split seeds). It is retained in the write-up as a diagnostic upper bound, not as a performance claim.
 
**Negative result.** A probe using Google's `derm-foundation` embeddings as a frozen representation underperformed the deployed baseline (66.8% ± 6.9 accuracy, 33.8% ± 5.9 macro recall, against 86.2% ± 1.2 and 63.1% ± 10.1). Domain-specific pretraining did not compensate for noisy label mapping.
 
**Subgroup reporting.** Fitzpatrick and Monk skin-tone metrics are reported across the same grouped split seeds. The darker Monk buckets are underpowered, and the audit is described as a process demonstration rather than a fairness claim.
 
Macro recall was tracked alongside accuracy throughout, since accuracy alone rewards majority-class collapse on imbalanced data. The conclusion supported by the experiments is that the limiting factor is label quality and face-specific data availability, not classifier architecture. **[Full write-up](https://github.com/Saltef/DermaLens/blob/main/PORTFOLIO_WRITEUP.md)**
 
---
 
## In progress
 
**CareGap.** Modelling healthcare access and system capacity in Ontario, with the aim of identifying where demand is emerging and where capacity gaps produce delays and unmet need.
 
---
 
## Methods and tools
 
```
Python · R · SQL
PyTorch · scikit-learn · transformers · ONNX Runtime · RAG and embedding pipelines
Docker · Git · GitHub Actions · pytest · ruff · GCP
Longitudinal and time series analysis · regression · cohort modelling · segmentation · Power BI
```
 
---
 
## Education
 
M.Sc. Big Data Analytics, **Trent University**
M.A. Media & Cultural Studies, **Doha Institute for Graduate Studies**
B.S. Economics, **Lebanese American University**
 
Arabic (native), English (professional), Spanish (limited working).
 
---
 
Open to applied data science, machine learning, and analytics roles.
[LinkedIn](https://www.linkedin.com/in/safea-altef) · safia.altef@gmail.com
**Open to applied data science, ML, and LLM evaluation roles.**
[LinkedIn](https://www.linkedin.com/in/safea-altef) · safia.altef@gmail.com
