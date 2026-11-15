# Investigating Differential Gene Expression, Cell-Type-Specific Signaling and Potential Intercellular Communication in Early-Onset Preeclampsia

OpenBio 2026 Datathon, Track 1: Maternal-Fetal Cell Communication in Preeclampsia


## Team
- Aditi Chaudhari
- Christine Yao
- Jason Liu
- Ruchika Mudraganam


## Research Question
Starter Question 8: What might gene activity reveal about communication between placental cells in preeclampsia?

Which genes encoding signaling ligands or receptors differ between PE and control placentas?
In which placental cell types do these differences occur?
Exploratory: which ligand–receptor pairs between cell types change in PE?

## Data Used

[x] GSE203507 bulk RNA-seq (required)
[x] Zeisel/Admati gene browser, for at least three genes (required)
[x] Admati/Skarbianskis single-cell pseudobulk files (optional)
[x] LIANA consensus ligand–receptor resource (LIANA [1.10.0])

## How to Run

1. The data package is in [`track-01/data`](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/tree/main/track-01/data) of the datathon repository. On Colab the first notebook cell downloads it.
2. Install packages by following [Track 1 Setup](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/track-01/1-setup.md).
3. Run `notebooks/track01_workflow.ipynb` top to bottom.

Reproducibility details:

Notebook: Brownian_Huskey.ipynb
Where we ran it: our own computer (macOS, Python 3.11.15, conda environment); the notebook also runs on Google Colab
Package versions: PyDESeq2 [version], LIANA [1.10.0]
Random seeds: [random_state=0 for PCA; all other steps are deterministic]

## Files

| Path | Contents |
|---|---|
| `notebooks/` | The analysis notebook or script |
| `figures/` | Exported graphs, including `headline.png` |
| `docs/article.md` | Science communication article, following the [HUDP article guide](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/docs/article-guide.md) |
| `docs/analysis-plan.md` | The comparison, model and thresholds we chose |
| `docs/hypothesis-card.md` | Our hypothesis and how to test it |

## Key Findings
Differential expression: after adjusting for gestational age and FGR, 348 genes pass padj < 0.05 and |log2 fold change| ≥ 1 (258 higher in PE, 90 lower). ENG is the most significant (padj 2.1 × 10⁻¹⁶). Directions are unchanged in five sensitivity analyses.
Signaling genes: 65 of the 348 genes encode ligands or receptors, more than expected (18.7% vs 7.7%; odds ratio 2.86). All 11 that pass every robustness check, including ENG, FLT1, LEP and INHBA, are higher in PE.
Cell types: in single-cell pseudobulk data, these genes change in the same direction as in bulk in syncytiotrophoblast, but none is significant within any cell class. Deconvolution estimates a lower Hofbauer cell proportion in PE; the data cannot separate a change in cell behavior from a change in cell mix.
Ligand–receptor pairs: no pair has both partners significantly changed, so no specific cell-to-cell interaction is supported.
Hypothesis: in early-onset PE, syncytiotrophoblast expresses more ENG, FLT1, LEP and INHBA per cell than in gestational-age-matched controls.


## Limitations

This study is limited by its small sample size (30 placentas), restriction to early-onset PE, and uneven distribution of clinical groups and gestational ages. The absence of control samples below 30 weeks makes it difficult to distinguish disease-associated expression changes from those related to gestational age. Additionally, batch information was unavailable, and potential confounders such as magnesium sulfate treatment and FGR may influence observed gene expression differences. Incomplete clinical metadata, varying PE diagnostic definitions across datasets, and reliance on a single-cell dataset for cell-type-specific analyses further limit the generalizability and validation of findings.

## Presentation

Video link: [add your unlisted YouTube link]
