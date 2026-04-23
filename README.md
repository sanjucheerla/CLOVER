# CLOVER: Chemical-gene LLM benchmark for Obtaining Valid Entity Relationships for the Comparative Toxicogenomics Database

CLOVER is a systematic benchmarking framework for evaluating large language models (LLMs) on **full-text chemical–gene interaction extraction** using the complete CTD chemical–gene classification schema. The framework supports 47 base interaction types with directional modifiers (increase, decrease, affects), yielding 136 possible interaction classes.

---

## Pipeline

CLOVER runs in four stages:

1. **LLM Extraction** — one-shot and few-shot prompting to extract chemical–gene interactions from full-text article sections
2. **LLM Validation** — a second LLM pass to confirm and revise extracted interactions *(note: empirically shown to reduce performance — see paper)*
3. **Rule-based Refinement** — standardizes interaction terminology and eliminates unsupported or malformed interactions
4. **Human Review** — expert oversight of final extracted interactions

---

## Data

CLOVER uses 23 full-text PubMed Central articles (582 sections). Articles are grounded using:

- **PubTator3** annotations for entity recognition — [https://www.ncbi.nlm.nih.gov/research/pubtator3/](https://www.ncbi.nlm.nih.gov/research/pubtator3/)
- **CTD** chemical–gene interaction schema — [https://ctdbase.org/downloads/](https://ctdbase.org/downloads/)

> **Note:** File paths in the CLOVER code are set to local development paths and will need to be updated before running. Additional intermediary files are generated during the pipeline — ensure you have sufficient disk space.

---

## Benchmarked Models

| Model | Recall | Precision |
|---|---|---|
| Claude Sonnet 4.5 | 72% | 66% |
| GPT-4.1 | 69% | 42% |
| GPT-4o | 55% | 44% |
| DeepSeek-V3 | 45% | 53% |
| Naive baseline | 9% | 28% |

Full results are reported in the paper.

---

## Requirements

- Python 3.10+
- PubMed Central full-text access or local article downloads
- CTD data files (see [https://ctdbase.org/downloads/](https://ctdbase.org/downloads/))

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## Running CLOVER

Update the path constants at the top of each script to point to your local data directories before running. The pipeline is designed to be run stage by stage — extraction, validation, refinement, and review outputs are saved as intermediary files between stages.

---

## Citation

If you use CLOVER in your work, please cite: TBD, submitted to Journal of Bioinformatics

---

## License

This project is licensed under the MIT License. CTD data is subject to the [CTD data use policy](https://ctdbase.org/about/dataUsePolicy.jsp).
