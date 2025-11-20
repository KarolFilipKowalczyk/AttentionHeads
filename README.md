# Attention Head Naming Convention for Large Language Models (LLMs)

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: RFC](https://img.shields.io/badge/Status-Request%20For%20Comments-blue)]()

A unified, descriptive, and scalable naming convention for attention heads in transformer models. [cite_start]This repository serves as a "living standard" to help researchers communicate clearly, map circuits across architectures, and solve the fragmentation of terminology in mechanistic interpretability[cite: 9, 29].

> **Read the full paper:** [PDF Link](./paper/Attention_Head_Naming_Convention.pdf)

## 🚨 The Problem
[cite_start]As mechanistic interpretability matures, informal naming conventions have emerged: induction heads, name mover heads, refusal heads, and many others. [cite_start]However, these names are often inconsistent (the same head appearing under multiple names), ambiguous, or unscalable across different model sizes[cite: 27, 28, 30].

[cite_start]This fragmentation makes replication difficult, hinders cross-paper comparison, and complicates the annotation of interpretability datasets[cite: 31].

## 💡 The Solution
[cite_start]This project proposes a unified taxonomy [cite: 33] consisting of:

1.  [cite_start]**A Four-Level Depth Model:** Normalizing layers into **Early (E)**, **Middle (M)**, **Late (L)**, and **Final (F)** to allow comparison between 12-layer and 96-layer models[cite: 10, 55].
2.  [cite_start]**9 Functional Stacks:** Grouping heads by their higher-level capability rather than just local mechanics[cite: 70].
3.  **Canonical Names:** A standardized vocabulary (e.g., `(M) Induction Head` instead of "pattern head" or "ICL head").

## 📚 The Stacks (Functional Taxonomy)

Heads are organized into functional stacks. [cite_start]Within each stack, heads are ordered by depth (`Early -> Middle -> Late -> Final`)[cite: 81].

| Stack Name | Core Function | Examples |
| :--- | :--- | :--- |
| **Reasoning & Algorithmic** | [cite_start]Pattern matching, sequence continuation, and strategic planning[cite: 92]. | `(M) Induction Head`, `(L) Strategy Head` |
| **Memory & Dependency** | [cite_start]Tracking references, resolving coreferences, and bridging dependencies[cite: 208]. | `(M) Coreference Head`, `(M) Bridging Head` |
| **Instruction & Intent** | [cite_start]Processing user instructions and switching task modes[cite: 256]. | `(E) Instruction Head`, `(M) Task-Mode Head` |
| **Knowledge Retrieval** | [cite_start]Retrieving factual info and moving it to output[cite: 301]. | `(M) Fact Head`, `(L) Name-Mover Head` |
| **Safety** | [cite_start]Content filtering, policy enforcement, and refusal[cite: 359]. | `(E) Content-Detection Head`, `(F) Refusal Head` |
| **Routing & Relevance** | [cite_start]Filtering context and managing attention focus[cite: 425]. | `(M) Topic-Relevance Head`, `(L) Router Head` |
| **Structural & Boundary** | [cite_start]Detecting delimiters, sections, and hierarchy[cite: 480]. | `(E) Delimiter Head`, `(L) Sectioning Head` |
| **Output Formatting** | [cite_start]Enforcing schemas (JSON/Lists) and style consistency[cite: 532]. | `(L) Output-Schema Head`, `(F) Format-Consistency Head` |
| **Stylistic & Persona** | [cite_start]Shaping tone, narrative voice, and pedagogical approach[cite: 594]. | `(L) Persona Head`, `(F) Step-by-Step Head` |

## 🗿 The Rosetta Stone (Cross-Reference)
*For a machine-readable version, see [`data/cross_reference.yaml`](./data/cross_reference.yaml).*

[cite_start]This project maps informal literature names to canonical names[cite: 686].

| Literature Name | Canonical Name | Stack |
| :--- | :--- | :--- |
| **Anti-copy head** | `(L) Copy-Suppression Head` | Knowledge Retrieval |
| **Copy head** | `(M) Duplicate-Token Head` OR `(L) Name-Mover Head`* | *Context Dependent* |
| **ICL head** | `(M) Induction Head` | Reasoning & Algorithmic |
| **Inhibition head** | `(L) S-Inhibition Head` | Knowledge Retrieval |
| **Mentions head** | `(E) Reference Resolution Head` | Memory & Dependency |
| **Previous token head** | `(E) Previous-Token Head` | Reasoning & Algorithmic |
| **Toxicity head** | `(E) Content-Detection Head` | Safety |

*(See Appendix A of the paper for the full table of 50+ mappings [cite: 686-695])*

## 📐 The Depth Model
To make this taxonomy scale-free (working for GPT-2 Small and Llama-3 70B), we use relative depth[cite: 64]:

* [cite_start]**Early (E):** 0.00 - 0.15 (Surface processing, syntax) [cite: 58, 64]
* [cite_start]**Middle (M):** 0.15 - 0.52 (Reasoning primitives, induction) [cite: 59, 64]
* [cite_start]**Late (L):** 0.52 - 0.88 (Semantic integration, routing) [cite: 59, 64]
* [cite_start]**Final (F):** 0.88 - 1.00 (Safety, formatting, output) [cite: 60, 64]

## 🤝 How to Contribute
[cite_start]This taxonomy is **descriptive, not prescriptive**[cite: 11]. It captures how heads tend to behave today. As new architectures emerge, this list must evolve.

1.  **Add a Head:** Submit a PR to `data/heads.json` with the citation where the head was observed.
2.  **Discuss:** Open an Issue to debate the categorization of specific heads.

## 📝 Citation
If you use this naming convention in your research, please cite the catalog:

```bibtex
@article{kowalczyk2025attention,
  title={Attention Head Naming Convention for Large Language Models (LLMs)},
  author={Kowalczyk, Karol},
  journal={arXiv preprint},
  year={2025}
}