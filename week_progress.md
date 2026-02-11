# Student Research Repository: Transfer Learning of Pluripotency TF

**Researcher:** Paula Martín Cabezas

**Project Lead:** Paula Martín Cabezas, Undergraduate

**Status:** Active

## 1. Project Objective
Provide a brief (200-word) summary of the specific research question you are addressing this semester.
This study proposes to evaluate the evolutionary conservation of regulatory logic by deploying deep learning models, trained on human genomic data, to predict Transcription Factor (TF) binding sites across a diverse phylogenetic spectrum ranging from non-human primates to distant mammals. By leveraging the predictive power of human-centric models on non-human genomes, we aim to quantify the "decay" of predictive accuracy as genetic distance increases. To validate these computational inferences, we will integrate species-specific ATAC-seq (chromatin accessibility) and RNA-seq (transcriptional output) datasets, providing a multi-omic ground truth to determine if predicted binding sites correlate with open chromatin and functional gene expression. Ultimately, this research will reveal the extent to which human-derived regulatory motifs remain functional across species and identify where lineage-specific innovations break the standard predictive rules.

## 2. Laboratory Notebook (The "Log")
To ensure research continuity, you are required to maintain a chronological log of your work below. Update this weekly.

### Week 1 -> Date: 2026-02-11
* **Objectives:** What was the goal for this week?

  - Read the [paper](https://www.nature.com/articles/s41586-025-10014-0) about AlphaGenome
  - Know more about the concepts of LiftOver, HALper, Synteny Blocks, TFBS i TF footprint
  - Set up jupyter-lab, python, R... all the tools we are going to use during the following weeks
  
* **Methods:** Which scripts or notebooks were used?
  
  We only used the paper which we have saved in `/lab-notebooks` [View AlphaGenome paper(PDF)](lab-notebooks/alphagenome.pdf)
  
* **Results:** Briefly state findings or attach a small figure.

  Understad of all the concepts
  
* **Blockers:** Any technical or theoretical issues encountered.

---

### Week 2 -> Date: 2026-02-xx

---

### Week 3 -> Date: 2026-02-xx

---

### Week 4 -> Date: 2026-02-xx

---

### Week 5 -> Date: 2026-02-xx

---

## 3. Directory Protocol

All work must be organized according to the following structure:

| Directory | Content Type |
| :--- | :--- |
| `/lab-notebooks` | Drafts, exploratory analysis, and visualization. |
| `/src` | Modularized, commented code and final pipelines. |
| `/results` | Significant figures, p-values, and processed outputs. |
| `/data` | Small reference files only (e.g., sample manifests). |

## 4. Handover Checklist
Before the conclusion of your term, ensure:
1. All scripts in `/src` run without errors.
2. The `environment.yml` or `requirements.txt` is updated.
3. All primary figures in your final report are linked to the specific notebook that generated them.
