# GovSecLLM++: Compliance-Aware Security Testing for LLM-Based Applications

This repository contains the reproducibility package for the paper:

**GovSecLLM++: A Compliance-Aware Benchmark for Security Testing and Governance Evidence in LLM-Based Applications**

Target venue: **SECAI 2026 — Workshop on Security and Artificial Intelligence**

## Overview

GovSecLLM++ is a compliance-aware benchmark and evaluation protocol for security testing of LLM-based applications.
It maps governance and security requirements to application-level risks, adversarial scenario cards, expected safe behaviours, measurable security and governance metrics, and audit evidence.

Unlike purely model-centric benchmarks, GovSecLLM++ focuses on deployed LLM-based applications involving:

- retrieval-augmented generation;
- compliance assistants;
- tool-using agents;
- memory-augmented assistants;
- audit logging;
- human oversight.

## Benchmark contents

The benchmark contains:

- 210 scenario cards;
- 7 test families;
- 4 application types;
- 5 application configurations;
- deterministic reference-backend evaluation;
- hosted Groq real-backend evaluation.

## Test families

| ID | Family |
|---|---|
| F1 | Instruction and Context Integrity |
| F2 | Data and Confidentiality Protection |
| F3 | Tool and Agency Governance |
| F4 | Auditability and Oversight |
| F5 | Robust Utility and False Refusal Control |
| F6 | Memory and Long-Context Poisoning |
| F7 | Tool Metadata and Supply-Chain Poisoning |

## Main real-backend evaluation

The main hosted real-backend evaluation uses:

- Backend: `groq/llama-3.1-8b-instant`
- Scenario cards: 210
- Configurations: 5
- Runs: 1050
- API errors: 0
- Duplicate executions: 0

The reported Groq full-run metrics exclude preliminary smoke-test executions.

## Full-run Groq results

| Configuration | n | T-ASR | GFR | CAFR | SLR | UUA | AEC |
|---|---:|---:|---:|---:|---:|---:|---:|
| Baseline | 210 | 25.2 | 100.0 | 100.0 | 25.2 | 74.8 | 0.45 |
| NoAudit | 210 | 0.0 | 100.0 | 100.0 | 0.0 | 100.0 | 0.45 |
| NoRedact | 210 | 15.2 | 0.0 | 15.2 | 15.2 | 84.8 | 1.00 |
| NoToolGate | 210 | 0.0 | 0.0 | 0.0 | 0.0 | 100.0 | 1.00 |
| Full | 210 | 0.0 | 0.0 | 0.0 | 0.0 | 100.0 | 1.00 |

Values are percentages except AEC.

## Directory structure

- `data/`: scenario cards in CSV and JSONL formats.
- `results/full/`: main full-run Groq results used in the paper.
- `results/smoke/`: smoke-test files used only for pipeline validation.
- `figures/`: paper-ready figures.
- `tables/`: LaTeX tables.
- `notebooks/`: Colab notebook used for the experiment.
- `scripts/`: helper scripts and notes.
- `paper/`: paper-related material.
- `docs/`: additional documentation.

## Smoke-test note

The smoke-test files are included only to document pipeline validation.
They cover a subset of F1/RAG scenarios and are **not included** in the paper's reported full-run metrics.

## Security and privacy note

All secrets, documents, tools, and policy records used in this repository are synthetic.
Do not commit API keys, GitHub tokens, `.env` files, or private credentials.

## Reproducibility

To reproduce the Groq run:

1. Open the Colab notebook.
2. Add a Colab secret named `GROQ_API_KEY`.
3. Run the notebook cells in order.
4. Results are saved under Google Drive and can be exported to this repository.

## License

Code is released under the MIT License.

## Citation

Please cite this repository and the accompanying paper if you use GovSecLLM++.
