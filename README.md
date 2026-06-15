# Demonstrated Skills Signal Extractor

**Type:** People Analytics Portfolio Project | NLP + HRIS  
**Author:** Annwesha Chakrabarty   
**Tools:** Python, spaCy, pandas, O*NET Content Model v30.3

---

## What this project does

Most HRIS platforms capture job titles and credentials — not the actual competencies employees demonstrate. This project builds a Python NLP pipeline that reads unstructured professional profile text, extracts skill signals, and maps them to official O*NET codes to surface competencies that are invisible to the employer's talent system.

Across 5 simulated profiles, the pipeline detected an average of **8.4 skills per profile** versus an estimated 3 captured by a standard HRIS — a **2.8× gap**.

---

## How to run it

1. Clone this repo
2. Install dependencies:
pip install spacy pandas matplotlib
python -m spacy download en_core_web_sm
3. Open `notebooks/skills_extractor.ipynb` in Jupyter
4. Run all cells in order
5. Outputs saved to `output/`

---

## What O*NET is and why it's used

The O*NET Content Model is a free, open skills framework published by the U.S. Department of Labor. It provides standardised skill names and element codes (e.g. `2.C.3.b` for Programming) that are system-agnostic — meaning skills data mapped to O*NET codes can be consumed by any HRIS platform without losing fidelity. This project uses a curated 15-skill subset of the full 277-skill taxonomy, sourced from O*NET v30.3 (onetcenter.org).

---

## HRIS integration path

In production, this pipeline would run as a microservice triggered when an employee updates their profile. Extracted skills would be staged in a validation queue, confirmed by the employee, then written to the HRIS skills record with source = `pipeline-confirmed`. The O*NET-coded output is compatible with Workday Skills Cloud and SAP SuccessFactors Opportunity Marketplace. Full integration path documented in `report/`.

---

## Output

- `output/extracted_skills.json` — structured skills JSON per profile with O*NET codes
- `output/skills_summary.csv` — flat table of all skill matches
- `output/skills_gap_chart.png` — bar chart: detected skills vs. HRIS-captured
- `report/skills_signal_extractor_report.pdf` — full consulting-style report
