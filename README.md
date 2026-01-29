# TermGuard-Terminology-Consistency-Checker-NLP-IR-Python-
TermGuard is a modular NLP/IR system that detects **terminology inconsistency** in bilingual translation data (EN→ZH) and generates a **consistency report** plus an optional **patched translation** using a preferred glossary.

This project emphasizes:
- pipeline architecture and modular design
- algorithmic term extraction + alignment
- measurable evaluation hooks
- reproducible CLI and Streamlit demos

---

## What it does

**Inputs**
- English source text (document or aligned segments)
- Chinese translation text
- Optional glossary CSV (EN term → preferred ZH term)

**Outputs**
- `report.csv` / `report.json`: inconsistent terms and evidence contexts
- `zh_patched.txt`: translation patched to preferred glossary (optional)

---

## System overview

Pipeline:
1) preprocess + sentence segmentation
2) term candidate extraction (EN n-grams + TF-IDF)
3) bilingual term mapping (sentence-pair co-occurrence + scoring)
4) inconsistency detection (1-to-many / many-to-1) + severity scoring
5) optional patching using preferred glossary
6) reporting and export

---

## Quickstart (CLI)

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

python cli.py \
  --en data/demo_en.txt \
  --zh data/demo_zh.txt \
  --glossary data/demo_glossary.csv \
  --out outputs/demo_run
