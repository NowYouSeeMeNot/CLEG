# CLEG: Chinese Litigation Evidence Generation Benchmark

> A large-scale benchmark (107,227 cases) for the task of Litigation Evidence Generation (LEG) in Chinese judicial scenarios.

---

## Table of Contents
- [Overview](#overview)
- [Key Features](#key-features)
- [Task Definition](#task-definition)
- [Why This Matters](#why-this-matters)
- [Dataset Construction Pipeline](#dataset-construction-pipeline)
- [Key Finding](#Key-Finding)
- [Changelog](#changelog)

---

## Overview
CLEG is the first publicly released benchmark dedicated to the **Litigation Evidence Generation** task in Chinese judicial practice.  
Given a plaintiff’s claims and factual statements, a system must output a structured list of evidence items, each paired with a refined, legally grounded purpose (i.e., what specific legal element or factual assertion it helps establish).

The benchmark enables evaluation of:
- Legal causal reasoning
- Evidence planning (beyond QA or classification)
- Purpose alignment with legal elements
- Robustness across civil vs. criminal cases
- Retrieval-augmented generation strategies

---

## Key Features
- 107,227 curated samples (50,645 civil / 56,582 criminal)
- Four-stage construction ensuring legal authenticity
- Evidence items include both raw and refined (canonical) purposes
- Tripartite Adversarial Scrutiny (TAS) scoring (Plaintiff vs. Defendant vs. Judge simulation)
- Rich metadata for research on scaling, complexity, and retrieval
- Benchmarked with 23 models (open-source, commercial, legal-domain, SFT, and RAG variants)

---

## Task Definition
Input:
- Plaintiff’s claim(s) + factual narrative (in Chinese)

Output:
- A list of evidence items:
  - evidence_name
  - refined legal purpose (concise & element-focused)
  - (optionally) raw purpose
  - (optionally) verification score

Objective:
Generate a *complete, precise, non-redundant* evidence plan supporting each asserted legal element.  
This differs from generic judgment prediction or legal QA because it demands proactive planning rather than reactive extraction.

---

## Why This Matters
Traditional legal AI benchmarks (e.g., judgment prediction, QA, statute retrieval) test *reactive understanding*.  
Evidence generation requires:
- Multi-hop factual decomposition
- Legal element mapping
- Anticipation of adversarial rebuttals
- Chain completeness (especially in criminal matters)

CLEG aims to push LLM research toward **strategy-level legal reasoning**.

---

## Dataset Construction Pipeline
1. **Semi-Structured Parsing**  
   Regex-based segmentation of Chinese judgments (claims, facts, evidence narratives).

2. **LLM-Based Evidence Extraction**  
   Extract plaintiff-submitted evidence with role-focused prompts, producing (name, purpose_raw).

3. **Purpose Refinement via Legal Element Deconstruction**  
   Chain-of-thought prompts canonicalize vague descriptions into concise, element-linked purposes.

4. **Tripartite Adversarial Scrutiny (TAS)**  
   Simulated Plaintiff–Defendant–Judge debate assigns \[1–5\] validation scores; low-score samples are filtered.

---

## Key Finding
**Similar-case retrieval (hybrid) outperforms both large proprietary and pure fine-tuning approaches.**

---


## Changelog
| Version | Date | Notes |
|---------|------|-------|
| 1.0.0 | 2025-08-16 | Initial public release |

---


## Disclaimer
This resource is for research. Do not rely on automated outputs for actual litigation strategy without licensed counsel review.

---

Happy researching! Feel free to open issues for feature requests (evaluation scripts, additional metadata, etc.).
