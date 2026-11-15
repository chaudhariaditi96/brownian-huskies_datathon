# Investigating Differential Gene Expression, Cell-Type-Specific Signaling and Potential Intercellular Communication in Early-Onset Preeclampsia

OpenBio 2026 Datathon, Track 1: Maternal-Fetal Cell Communication in Preeclampsia


## Team
- Aditi Chaudhari
- Christine Yao
- Jason Liu
- Ruchika Mudraganam


## Research Question
After adjusting for gestational age and FGR, which genes are differentially expressed in PE placentas, and which cell types are they associated with?

## Data Used

- [-] GSE203507 bulk RNA-seq (required)
- [-] Zeisel/Admati gene browser, for at least three genes (required)
- [-] Admati/Skarbianskis single-cell pseudobulk files (optional)
- [ ] Other public data: [name and link]

## How to Run

1. The data package is in [`track-01/data`](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/tree/main/track-01/data) of the datathon repository. On Colab the first notebook cell downloads it.
2. Install packages by following [Track 1 Setup](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/track-01/1-setup.md).
3. Run `notebooks/track01_workflow.ipynb` top to bottom.

Reproducibility details:

- Notebook or script files:
- Where we ran it (Colab or our own computer): Google Colab
- Random seeds, if any: 

## Files

| Path | Contents |
|---|---|
| `notebooks/` | The analysis notebook or script |
| `figures/` | Exported graphs, including `headline.png` |
| `docs/article.md` | Science communication article, following the [HUDP article guide](https://github.com/Harvard-Undergraduate-OpenBio/openbio-datathon-2026/blob/main/docs/article-guide.md) |
| `docs/analysis-plan.md` | The comparison, model and thresholds we chose |
| `docs/hypothesis-card.md` | Our hypothesis and how to test it |

## Key Findings
Using an adjusted p-value (padj) < 0.05 and an absolute log2 fold change (|log2FC|) ≥ 1, we identified 348 differentially expressed genes between preeclampsia (PE) and non-PE placentas after adjusting for gestational age and fetal growth restriction (FGR). Of these, 258 genes were upregulated and 90 were downregulated in PE placentas.
Several genes associated with PE, including FLT1, ENG, HTRA4, SERPINA3, and KIT, showed increased expression in the bulk RNA-seq analysis. However, cell-type-specific analyses did not identify statistically significant differences in FLT1 expression in any individual cell type.


## Limitations

This study is limited by its small sample size (30 placentas), restriction to early-onset PE, and uneven distribution of clinical groups and gestational ages. The absence of control samples below 30 weeks makes it difficult to distinguish disease-associated expression changes from those related to gestational age. Additionally, batch information was unavailable, and potential confounders such as magnesium sulfate treatment and FGR may influence observed gene expression differences. Incomplete clinical metadata, varying PE diagnostic definitions across datasets, and reliance on a single-cell dataset for cell-type-specific analyses further limit the generalizability and validation of findings.

## Presentation

Video link: [add your unlisted YouTube link]
