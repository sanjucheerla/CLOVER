# CLOVER: Chemical-gene LLM benchmark for Obtaining Valid Entity Relationships for the Comparative Toxicogenomics Database

CLOVER is a systematic benchmarking framework for evaluating large language models (LLMs) on **full-text chemical–gene interaction extraction** using the complete CTD chemical–gene classification schema. 

---

## Pipeline

CLOVER runs in four stages:

1. **LLM Extraction** — one-shot and few-shot prompting to extract chemical–gene interactions from full-text article sections
2. **LLM Validation** — a second LLM pass to confirm and revise extracted interactions *(note: empirically shown to reduce performance — see paper)*
3. **Rule-based Refinement** — standardizes interaction terminology and eliminates unsupported or malformed interactions
4. **Human Review** — expert oversight of final extracted interactions

---

CLOVER uses 50 full-text PubMed Central articles

Full results are reported in the paper.

---

## Requirements

- Python 3.10+
- PubMed Central full-text access or local article downloads
- CTD data files (see [https://ctdbase.org/downloads/](https://ctdbase.org/downloads/))

---

## Running CLOVER

Update the path constants to point to your local data directories before running. The pipeline is designed to be run stage by stage — extraction, validation, refinement, and review outputs are saved as intermediary files between stages.

---

## Citation

If you use CLOVER in your work, please cite: TBD, submitted to PlosONE

---

## License

This project is licensed under the MIT License. CTD data is subject to the [CTD data use policy](https://ctdbase.org/about/dataUsePolicy.jsp).
