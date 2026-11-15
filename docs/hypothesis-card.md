# Hypothesis Card

## Title
Investigating the Cellular Origins of Altered Signaling-Related Gene Expression in Early-Onset Preeclampsia
## Clinical/Biological Problem
Preeclampsia (PE) is a pregnancy complication involving high blood pressure and often abnormal placental function. Early-onset PE occurs before 34 weeks of gestation and can have serious consequences for both mother and fetus. Changes in angiogenic regulation, including the balance of sFlt-1 and PlGF, are important in PE (Burwick & Rodriguez, 2024).
Bulk placental RNA sequencing measures gene expression across mixed cell populations. Differences between PE and control tissue could reflect changes within cells, changes in cell-type proportions, or both (Campbell et al., 2023). We investigated which signaling-related genes differed in early-onset PE and whether their expression patterns pointed toward particular placental cell types.

## Dataset(s) and Relevant Cells

We analyzed bulk placental RNA-seq data from GSE203507: 15 early-onset PE and 15 non-PE placentas. We used DESeq2 to compare the groups while adjusting for gestational age at delivery and fetal growth restriction (FGR) (Ackerman et al., 2023).
For cell-type analyses, we used the Admati/Skarbianskis single-cell dataset, containing 26 donors (17 PE and 9 controls) across 14 placental cell classes, along with the Zeisel Lab placental gene browser (Admati et al., 2023). We examined syncytiotrophoblasts, villous cytotrophoblasts, extravillous trophoblasts, endothelial cells, stromal/fibroblast populations, Hofbauer cells, and other placental populations. Syncytiotrophoblasts were our main population of interest because they are at the maternal–fetal interface.

## Observed Result

Using an adjusted p-value below 0.05 and an absolute log2 fold change of at least 1, our bulk analysis identified 348 differentially expressed genes: 258 higher and 90 lower in PE. Sixty-five were annotated as ligands or receptors (48 higher and 17 lower). This represented enrichment relative to all tested genes (18.7% versus 7.7%; odds ratio = 2.86; one-sided Fisher's exact p = 1.3 × 10⁻¹¹).
We selected five genes for closer examination. FLT1, ENG, LEP, and INHBA were higher in PE and passed all five robustness checks. CADM3 was lower in PE, passed four checks, and retained the same direction of change in the fifth. All five passed the main bulk differential-expression thresholds.
In pseudobulk comparisons, all five genes changed in the same direction as in bulk within syncytiotrophoblasts. ENG and CADM3 retained their respective directions across all 14 cell classes. However, none of the five genes was statistically significant within an individual cell class. Bulk fold changes correlated most with syncytiotrophoblasts (Spearman's ρ = 0.33) and villous cytotrophoblasts (ρ = 0.31), although these correlations were modest.
Deconvolution estimated a higher relative RNA contribution from syncytiotrophoblasts and a lower contribution from villous cytotrophoblasts in PE, but neither difference was statistically significant in the main analysis. Hofbauer cells had a lower estimated RNA contribution in PE in the main setting (adjusted p = 0.0003), although this finding was not significant across all signature-size settings. The exploratory ligand–receptor analysis did not establish statistically supported changes involving the five genes. An exploratory CADM3–CADM1 stromal-to-NK-cell combination had a lower score in PE, but it was not statistically supported.


## Proposed Mechanism

Consistent with our original project proposal, we hypothesize that syncytiotrophoblast abundance is not substantially altered in early-onset PE, while ENG, FLT1, LEP, and INHBA are increased in this cell population and contribute to their higher bulk expression. Our deconvolution results do not establish unchanged abundance, so that part of the hypothesis remains to be tested. We also propose that the lower bulk expression of CADM3 may reflect changes in cell-adhesion-related regulation. Our results do not identify the responsible cell population.
The five-gene pattern may reflect changes in placental vascular and cell-interaction pathways. Alternatively, differences in the relative contributions of placental cell populations may drive some of the bulk expression differences. We cannot distinguish these explanations conclusively or identify a receiving cell type from our data.


## Why the Result Is Biologically Plausible

Syncytiotrophoblasts form the outer layer of placental villi and participate in exchange and signaling at the maternal–fetal interface. FLT1 is relevant because its soluble isoform, sFlt-1, can bind VEGF and PlGF, contributing to angiogenic imbalance in PE (Burwick & Rodriguez, 2024). ENG participates in vascular signaling, while LEP and INHBA are involved in placental or cellular regulation (Admati et al., 2023).
CADM3 differs from these four genes. It is a cell-adhesion molecule, not another established angiogenic factor. Its lower expression offers a contrasting signaling-related candidate, but our data do not establish its functional meaning.
Previous placental deconvolution research found that differences in cell proportions can influence apparent bulk expression differences for FLT1, ENG, and LEP (Campbell et al., 2023). This makes cell composition a major competing explanation, not a minor technical detail.


## Alternative Explanations/Confounders
Bulk differences may partly reflect cell composition rather than changes in expression within individual cell populations (Campbell et al., 2023). Our deconvolution estimates represent relative RNA contributions, not direct cell counts.
Gestational age is also important, and we adjusted for it. However, no control placenta was delivered before 29.9 weeks. Fetal sex was unevenly distributed. Sequencing batch was not included in the provided metadata, so we could not adjust for it. The original Ackerman study reports that preterm-birth and term-birth control samples were sequenced together with four EOPE samples (S16, S20, S21, and S22). This creates a potential overlap between sequencing batch and case–control status, making it difficult to distinguish technical batch effects from biological group differences with the supplied data (Ackerman et al., 2023; see also the 2023 medRxiv preprint, https://doi.org/10.1101/2023.03.08.23286998). The single-cell dataset included both early- and late-onset PE, unlike our bulk cohort. In that dataset, FGR and magnesium sulfate exposure were also unevenly distributed between PE and control donors. The two datasets came from different participants and protocols (Ackerman et al., 2023; Admati et al., 2023).


## Proposed Validation Experiment or Follow-up Analysis

A larger study with early-onset PE and gestational-age-matched preterm controls, sequenced across balanced batches with recorded batch metadata, could test the five genes within specific placental populations, treating each donor as a biological replicate. Single-nucleus RNA-seq may improve recovery of syncytiotrophoblast material, although single-nucleus and single-cell approaches have different detection limitations (Admati et al., 2025).
RNA in situ hybridization on placental sections could assess expression relative to syncytiotrophoblast area and help separate expression changes from differences in tissue composition. Protein measurements would be needed to investigate whether the RNA differences translate into functional changes.
The central syncytiotrophoblast hypothesis would be weakened if a sufficiently powered study found no increase in ENG, FLT1, LEP, and INHBA within that population, or if their bulk increases were explained entirely by cell composition. CADM3 would need a separate cell-localization test to identify the source of its lower bulk expression.


## Potential Intervention Relevance

FLT1 and ENG are relevant to established research on angiogenic dysfunction in PE. The sFlt-1/PlGF balance already has clinical biomarker relevance (Burwick & Rodriguez, 2024). Identifying the cellular origins of these expression patterns could help guide future mechanistic research. However, this analysis does not establish a new diagnostic marker, treatment, or therapeutic target. We cannot infer an intervention from the CADM3 result.

## Confidence Level and Limitations

Moderate confidence in the bulk expression findings. Low confidence in the proposed cell-specific mechanism.
The bulk differences for all five genes passed the main thresholds, and four genes passed every robustness check. CADM3 passed four of five. However, none of the five genes was statistically significant within any individual cell class. The cell-type correlations were modest, deconvolution did not resolve the source of the five-gene differences, and no ligand–receptor interaction involving the focus genes was statistically supported. The lower Hofbauer-cell estimate is exploratory because its significance depended on the deconvolution signature setting.
The unavailable batch covariate is an additional limitation. Robustness checks do not rule out technical variation that may overlap with case–control status. The single-cell analyses had limited donor numbers and included late-onset PE. RNA measurements cannot establish protein secretion, actual cell-to-cell communication, or causation. We therefore present the cell-specific mechanism as a hypothesis to test, not a conclusion from this two-day analysis.


##Citations
- Ackerman, W. E., IV, Buhimschi, C. S., Brown, T. L., Zhao, G., Summerfield, T. L., & Buhimschi, I. A. (2023). Transcriptomics-based subphenotyping of the human placenta enabled by weighted correlation network analysis in early-onset preeclampsia with and without fetal growth restriction. Hypertension, 80(6), 1363–1374. https://doi.org/10.1161/HYPERTENSIONAHA.122.20807
- Admati, I., Skarbianskis, N., Hochgerner, H., Ophir, O., Weiner, Z., Yagel, S., Solt, I., & Zeisel, A. (2023). Two distinct molecular faces of preeclampsia revealed by single-cell transcriptomics. Med, 4(10), 687–709.e7. https://doi.org/10.1016/j.medj.2023.07.005
- Admati, I., Skarbianskis, N., Hochgerner, H., Ophir, O., Yagel, S., Solt, I., & Zeisel, A. (2025). Single-nuclei RNA-sequencing fails to detect molecular dysregulation in the preeclamptic placenta. Placenta, 159, 170–179. https://doi.org/10.1016/j.placenta.2024.12.011
- Burwick, R. M., & Rodriguez, M. H. (2024). Angiogenic biomarkers in preeclampsia. Obstetrics & Gynecology, 143(4), 515–523. https://doi.org/10.1097/AOG.0000000000005532
- Campbell, K. A., Colacino, J. A., Puttabyatappa, M., Dou, J. F., Elkin, E. R., Hammoud, S. S., Domino, S. E., Dolinoy, D. C., Goodrich, J. M., Loch-Caruso, R., Padmanabhan, V., & Bakulski, K. M. (2023). Placental cell type deconvolution reveals that cell proportions drive preeclampsia gene expression differences. Communications Biology, 6, Article 264. https://doi.org/10.1038/s42003-023-04623-6

##Data Sources
- Ackerman et al. (2023), original medRxiv preprint reporting the sequencing batches: https://doi.org/10.1101/2023.03.08.23286998
- GSE203507 bulk RNA-seq: https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE203507
- Admati/Skarbianskis single-cell dataset: https://doi.org/10.6084/m9.figshare.23264102.v1
- Zeisel Lab placental gene browser: https://storage.googleapis.com/www_zeisellab/PE_web/pe_web_test_v1.html
