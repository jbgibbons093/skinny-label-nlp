# Skinny Label NLP

Three-way semantic similarity analysis of pharmaceutical skinny labels using NLP.

**Research Question**: How has the scope and content of skinny labels changed over time, and what is the semantic relationship between patent claims, Orange Book use codes, and approved label indications?

## Pipeline Diagram

Open [`pipeline_diagram.html`](pipeline_diagram.html) in a browser for the full interactive pipeline visualization, or view it via GitHub Pages:

**[View Pipeline Diagram](https://jbgibbons093.github.io/skinny-label-nlp/pipeline_diagram.html)**

## Method

For each NDA with method-of-use patents, we compute three cosine similarity scores in a shared embedding space (S-PubMedBert-MS-MARCO, 768-dim):

1. **Claim ↔ Use Code** — Do patent claims match what's listed in the Orange Book?
2. **Claim ↔ Indication** — Do patent claims match the approved label?
3. **Indication ↔ Use Code** — Do use codes match the approved label?

A derived **trap score** = claim↔usecode − indication↔usecode measures whether patents cover scope beyond approved indications.

## Cohort

- **2,927 NDAs** (1,966 treatment, 961 control) from 1998–2024
- **214,278 patent claims** (independent + dependent)
- **4,421 use codes** with FDA descriptions
- Labels from Drugs@FDA API for all NDAs

## Data Sources

- FDA Orange Book (NBER 1985–2016, Arnold Ventures 2017–2018, Modern 2019–2024)
- Drugs@FDA API — label PDFs and NDA metadata
- USPTO PatentsView — patent claim full text
- FDA Use Code Descriptions — official crosswalk
