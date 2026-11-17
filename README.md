# Mitigating Hallucination in Abstractive Text Summarization using Entity-Aware PMIDC

### Research Internship | National Forensic Sciences University (NFSU), Dharwad

This repository contains the implementation of **Entity-Aware PMIDC (EA-PMIDC)** and **EA-PMIDC Clean**, developed during a research internship at the National Forensic Sciences University (NFSU), Dharwad.

The project builds upon the research paper *"Mitigating Hallucination in Abstractive Summarization with Domain-Conditional Mutual Information"* and explores entity-aware prompting to improve the factual consistency of abstractive text summaries.

## 1. Project Overview

Abstractive text summarization generates concise summaries by understanding and rephrasing the original document. However, neural summarization models may produce **hallucinations**, introducing information that is inaccurate, unsupported, or absent from the source text.

The PMIDC approach addresses this problem using domain-conditional mutual information and keyword-based prompting.

This project extends PMIDC by incorporating named entities alongside important keywords, providing additional contextual information during summary generation.

## 2. Objectives

- Study and reproduce the PMIDC approach for hallucination mitigation.
- Identify limitations of keyword-only prompting.
- Develop an entity-aware extension using named entity recognition (NER).
- Implement and compare EA-PMIDC and EA-PMIDC Clean.
- Evaluate summary quality and factual consistency using multiple evaluation metrics.

## 3. Proposed Methodology

The proposed approach extends the original PMIDC framework through two implementations.

### EA-PMIDC (Entity-Aware PMIDC)

EA-PMIDC enhances the original keyword-based prompting mechanism by combining:

- **KeyBERT:** Extracts the top three relevant keywords from the source document.
- **SpaCy NER:** Identifies important named entities belonging to three categories:
  - PERSON – Names of individuals
  - ORG – Organizations
  - GPE – Countries, cities, and geopolitical locations

The extracted keywords and entities are combined to create an enriched contextual prompt for the summarization model.

### EA-PMIDC Clean

EA-PMIDC Clean further refines the entity-aware prompting approach by removing redundant or unnecessary contextual terms before constructing the prompt.

This aims to provide cleaner contextual information while retaining important entities and keywords.

**Note:** Both implementations retain the underlying PMIDC decoding framework and pretrained summarization model. The primary modification is in contextual prompt construction.

## 4. Dataset and Models

**Dataset:** XSUM (Extreme Summarization)

XSUM contains news articles paired with concise, single-sentence summaries and is commonly used to evaluate abstractive summarization systems.

**Models and Tools:**

- BART-large-XSUM – Pretrained abstractive summarization model
- GPT-2 – Language model used within the PMIDC framework
- KeyBERT – Keyword extraction
- SpaCy – Named entity recognition
- Hugging Face Transformers – Model implementation
- PyTorch – Deep learning framework
- Google Colab – Experimental environment

## 5. Evaluation Metrics

The implementations were evaluated using the following metrics:

| Metric | Purpose |
|---|---|
| ROUGE-1, ROUGE-2, ROUGE-L | Lexical overlap with reference summaries |
| BERTScore | Semantic similarity |
| BARTScore | Model-based summary quality assessment |
| BS-FACT | Factual consistency assessment |
| FactCC | Factual consistency classification |


### Key Observations

- EA-PMIDC improved BS-FACT and BARTScore compared with the replicated PMIDC baseline.
- EA-PMIDC Clean achieved further improvements in factual consistency metrics.
- Small reductions were observed in ROUGE-L and BERTScore.
- The results demonstrate a trade-off between reference-summary similarity and factual consistency.

These findings suggest that incorporating named entities into contextual prompting can help improve certain factual consistency measures without modifying the underlying summarization model.

## 7. Technologies Used

Python | PyTorch | Hugging Face Transformers | SpaCy | KeyBERT | BART | GPT-2 | Google Colab

## 8. Research Contribution

The primary contribution of this project is an **entity-aware prompting extension of PMIDC** that combines keyword extraction and named entity recognition.

Rather than retraining the summarization model or changing the decoding algorithm, the proposed approach enhances the contextual information supplied during generation.

The experiments investigate whether entity-aware prompting can improve factual consistency while maintaining competitive summarization quality.

## 9. Acknowledgement

This work was carried out as part of a research internship at the **National Forensic Sciences University (NFSU), Dharwad**.

The project builds upon the original research on hallucination mitigation using domain-conditional mutual information in abstractive summarization.

## 10. Disclaimer

This repository contains research implementations developed for academic and experimental purposes. The observed improvements are metric-dependent and do not guarantee the elimination of hallucinations from generated summaries.
