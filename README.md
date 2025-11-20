# Attention Head Naming Convention for Large Language Models (LLMs)

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)
[![Status: RFC](https://img.shields.io/badge/Status-Request%20For%20Comments-blue)]()

A unified, descriptive, and scalable naming convention for attention heads in transformer models. This repository serves as a "living standard" to help researchers communicate clearly, map circuits across architectures, and solve the fragmentation of terminology in mechanistic interpretability.

> **Read the full paper:** [PDF Link](./paper/Attention_Head_Naming_Convention.pdf)

## 🚨 The Problem
As mechanistic interpretability matures, informal naming conventions have emerged: induction heads, name mover heads, refusal heads, and many others. However, these names are often inconsistent (the same head appearing under multiple names), ambiguous, or unscalable across different model sizes.

This fragmentation makes replication difficult, hinders cross-paper comparison, and complicates the annotation of interpretability datasets.

## 💡 The Solution
This project proposes a unified taxonomy consisting of:

1.  **A Four-Level Depth Model:** Normalizing layers into **Early (E)**, **Middle (M)**, **Late (L)**, and **Final (F)** to allow comparison between 12-layer and 96-layer models.
2.  **9 Functional Stacks:** Grouping heads by their higher-level capability rather than just local mechanics.
3.  **Canonical Names:** A standardized vocabulary (e.g., `(M) Induction Head` instead of "pattern head" or "ICL head").

## 📚 The Stacks (Functional Taxonomy)

Heads are organized into functional stacks. Within each stack, heads are ordered by depth (`Early -> Middle -> Late -> Final`).

| Stack Name | Core Function | Examples |
| :--- | :--- | :--- |
| **Reasoning & Algorithmic** | Pattern matching, sequence continuation, and strategic planning. | `(M) Induction Head`, `(L) Strategy Head` |
| **Memory & Dependency** | Tracking references, resolving coreferences, and bridging dependencies. | `(M) Coreference Head`, `(M) Bridging Head` |
| **Instruction & Intent** | Processing user instructions and switching task modes. | `(E) Instruction Head`, `(M) Task-Mode Head` |
| **Knowledge Retrieval** | Retrieving factual info and moving it to output. | `(M) Fact Head`, `(L) Name-Mover Head` |
| **Safety** | Content filtering, policy enforcement, and refusal. | `(E) Content-Detection Head`, `(F) Refusal Head` |
| **Routing & Relevance** | Filtering context and managing attention focus. | `(M) Topic-Relevance Head`, `(L) Router Head` |
| **Structural & Boundary** | Detecting delimiters, sections, and hierarchy. | `(E) Delimiter Head`, `(L) Sectioning Head` |
| **Output Formatting** | Enforcing schemas (JSON/Lists) and style consistency. | `(L) Output-Schema Head`, `(F) Format-Consistency Head` |
| **Stylistic & Persona** | Shaping tone, narrative voice, and pedagogical approach. | `(L) Persona Head`, `(F) Step-by-Step Head` |

## 🗿 The Rosetta Stone (Cross-Reference)
*For a machine-readable version, see [`data/cross_reference.yaml`](./data/cross_reference.yaml).*

This project maps informal literature names to canonical names.

| Literature Name | Canonical Name | Stack |
| :--- | :--- | :--- |
| **Anti-copy head** | `(L) Copy-Suppression Head` | Knowledge Retrieval |
| **Copy head** | `(M) Duplicate-Token Head` OR `(L) Name-Mover Head`* | *Context Dependent* |
| **ICL head** | `(M) Induction Head` | Reasoning & Algorithmic |
| **Inhibition head** | `(L) S-Inhibition Head` | Knowledge Retrieval |
| **Mentions head** | `(E) Reference Resolution Head` | Memory & Dependency |
| **Previous token head** | `(E) Previous-Token Head` | Reasoning & Algorithmic |
| **Toxicity head** | `(E) Content-Detection Head` | Safety |

*(See Appendix A of the paper for the full table of 50+ mappings)*

## 📏 The Depth Model
To make this taxonomy scale-free (working for GPT-2 Small and Llama-3 70B), we use relative depth:

* **Early (E):** 0.00 - 0.15 (Surface processing, syntax)
* **Middle (M):** 0.15 - 0.52 (Reasoning primitives, induction)
* **Late (L):** 0.52 - 0.88 (Semantic integration, routing)
* **Final (F):** 0.88 - 1.00 (Safety, formatting, output)

## 🤝 How to Contribute
This taxonomy is **descriptive, not prescriptive**. It captures how heads tend to behave today. As new architectures emerge, this list must evolve.

1.  **Add a Head:** Submit a PR to `data/heads.json` with the citation where the head was observed.
2.  **Discuss:** Open an Issue to debate the categorization of specific heads.

## 📄 Citation
If you use this naming convention in your research, please cite the catalog:

```bibtex
@article{kowalczyk2025attention,
  title={Attention Head Naming Convention for Large Language Models (LLMs)},
  author={Kowalczyk, Karol},
  journal={Zenodo},
  year={2025}
}
```
