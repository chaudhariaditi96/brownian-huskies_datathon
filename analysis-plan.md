# Analysis Plan
##Team 
Brownian Huskey
##Track
01 — Placental cell communication in preeclampsia 
## Research Question
**Starter Question 8:** What might gene activity reveal about communication between placental cells in preeclampsia?

- **Sub-question 1:** Which genes encoding signaling ligands or receptors differ between PE and control placentas? (bulk RNA-seq)
- **Sub-question 2:** In which placental cell types do these differences occur? (pseudobulk, gene browser)
- **Sub-question 3 (exploratory):** Which ligand–receptor pairs between cell types change in PE? (pseudobulk)

## Datasets

List the datasets you will use (see the data catalog).

| Dataset ID | Role | Why This Dataset |
|---|---|---|
| GSE203507 bulk RNA-seq | 30 villous tissue samples (15 early-onset PE, 15 no_PE); 26,485 genes | Main analysis |
| Admati/Skarbianskis single-cell | 26 donors (17 PE, 9 control), 14 cell classes; provided as pseudobulk and as the gene browser | Cell-level analysis (one source, not two independent datasets) |
| Marker table | 9 cell classes, 4 markers each | First assessment of cell mix vs behavior |
| LIANA consensus ligand–receptor resource (LIANA 1.10.0) | 4,620 ligand–receptor pairs | Defines signaling genes; ligand–receptor analysis |


GSE203507 bulk RNA-seq (core) and Admati/Skarbianskis single-cell data (pseudobulk extension and gene browser), provided by the OpenBio 2026 Datathon.



## Methods

Describe the analysis steps:

1. Data loading and checks
2. Comparison and why you chose it
3. Statistical model and thresholds
4. Gene browser lookups (at least three genes)
5. Optional extension analyses
6. Interpretation and figures

## Confounders and Controls

List potential confounders and how you will address them.

## Expected Figures

1.
2.
3.
4.
