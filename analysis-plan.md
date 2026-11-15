# Analysis Plan
## Team 
Brownian Huskey
## Track
01 — Placental cell communication in preeclampsia 
## Project 
Investigating Differential Gene Expression, Cell-Type-Specific Signaling and Potential Intercellular Communication in Early-Onset Preeclampsia
## Timeline
Our original proposal focused on whether syncytiotrophoblast abundance remains relatively unchanged while anti-angiogenic signaling-related gene expression increases in early-onset preeclampsia (EOPE). The plan below documents the methods implemented in our final analysis, including extensions and sensitivity checks. Findings are reported separately from the hypotheses.

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

1. Data loading and checks
- Match bulk count-table sample IDs to metadata. Check for duplicates, missing values, and non-negative integer counts. The analyzed bulk matrix contained 26,485 genes × 30 samples.
- Summarize cohort composition: 8 EOPE, 7 EOPE+FGR, 5 FGR controls, 5 indicated preterm-birth controls, and 5 term-birth controls.
- Inspect principal component analysis (PCA), gestational age, fetal sex, FGR, total counts, and the potential outlier S01.
- Load pseudobulk counts and metadata. Verify donor-to-cell-class mapping. The pseudobulk matrix contained 33,660 genes × 362 donor–cell-class samples.
2. Comparison and rationale
- Primary bulk comparison: 15 PE vs 15 non-PE placentas, retaining all 30 samples.
- Primary bulk model: PE status + gestational age at delivery + FGR status. Gestational age and FGR were included because both may influence placental expression and differ across groups.
- Compare PE and control donors within each of 14 cell classes in the pseudobulk extension. Donors, not individual cells, are the independent biological replicates. Interpret this extension cautiously because the single-cell cohort includes both early- and late-onset PE.
3. Statistical model, thresholds, and sensitivity analyses
- Use PyDESeq2, a Python implementation of DESeq2, for negative binomial differential-expression analysis of raw counts.
- Main bulk DEG definition: Benjamini–Hochberg adjusted p < 0.05 and |log2 fold change| ≥ 1. A positive fold change means higher expression in PE.
- Inspect results under alternative cutoffs, low-count genes, and uncertainty in estimated effect sizes.
- Run five sensitivity checks: (1) remove S01; (2) EOPE vs indicated preterm-birth controls; (3) remove samples whose blood-pressure records conflict with their PE labels; (4) add fetal sex; and (5) remove FGR from the model.
- Annotate differential genes against the ligand–receptor resource. Use Fisher's exact test to assess whether signaling-related genes are overrepresented among DEGs.
4. Gene browser and cell-type follow-up
- Examine placental cell-marker patterns and use the gene browser for FLT1, ENG, LEP, INHBA, and CADM3 (exceeding the three-gene minimum).
- Compare bulk and cell-class pseudobulk log2 fold changes, including their direction and Spearman correlation. Do not equate concordant direction with statistical significance.
- Focus interpretation on syncytiotrophoblasts, while considering villous and extravillous cytotrophoblasts, endothelial cells, stromal/fibroblast cells, Hofbauer cells, and other classes.
5. Optional extension analyses performed
- Cell-composition deconvolution: construct a pseudobulk-derived reference, test it on synthetic mixtures, estimate each bulk sample's relative cell-class RNA contribution, and compare estimates between groups with clinical covariates. These are not measured cell counts or validated abundance estimates.
- Exploratory ligand–receptor scoring: assess possible sender–receiver combinations using cell-class expression profiles. Treat any candidate interaction as exploratory unless it meets the notebook's statistical criteria. RNA co-expression alone cannot establish physical signaling.
6. Interpretation and figures
- Distinguish bulk expression differences from within-cell-type expression changes, changes in cellular composition, and inferred signaling.
- Present the five-gene evidence alongside sensitivity checks and pseudobulk results. Explicitly report negative or nonsignificant results.

## Confounders and Controls

List potential confounders and how you will address them.

## Expected Figures
1. PCA of bulk placental samples: PC1 and PC2, colored by PE status, with clinical groups or covariates identified where useful.
2. Volcano plot of bulk differential expression: log2 fold change vs −log10 adjusted p value, marking thresholds and highlighting FLT1, ENG, LEP, INHBA, and CADM3.
3. Signaling-related DEG summary: higher/lower expression counts and enrichment among significant genes, with denominators and significance clearly labeled.
4. Five-gene bulk vs pseudobulk comparison: per-gene fold-change direction by cell class, emphasizing syncytiotrophoblasts and clearly marking which within-cell-class tests were not significant.
5. Exploratory cell-composition or ligand–receptor figure (optional): show uncertainty and avoid implying validated changes in cell counts or communication.

