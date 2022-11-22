# HSPC-Circadian-Rhythm-Gene-Expression-Variation

## Samples
- RNA from 4000 HSCs, 2000 Flk2- MPPs, 2000 Flk2+ MPPs, 4000 CLPs and 4000 ckit+sca- cells per sample were submitted for scRNAseq.

## Data Preprocessing
- Samples are combined before any pre-processing.
- Ambient RNA removal was determined to not affect downstream analysis and was therefore removed from the pipeline.
- Remove genes expressed in less than 3 cells and remove cells with less than 200 genes expressed.
- Remove cells with mitochondrial gene percentage higher than 10% and cells with ribosomal gene percentage las than 5%.
- Remove mitochondrial, HBB genes and Malat1 as these are all the most highly expressed genes and are only used for previous QC steps and not necessary for downstream steps.
- Identify highly variable genes and use these genes to perform multiple nearest neighbor(MNN) batch correction using Time as the batch key (yielded best results in terms of UMAP and downstream DGEA).
- Use raw reacds for cell annotation with SingleR.

## Data Analysis and Visualization
- Compute tSNE plot and UMAP using raw counts.
- Determine known circadian gene expression using raw counts.
- Use a 1 UMI in 2% percent of cell gene filter for DGEA.
- Perform one vs the rest DGEA.
- Perform pairwise DGEA between 7am and 11pm, 11am and 7am, 7pm and 11am and 11pm and 7pm.
- Use pairwise DGEA results to find genes that are present in all pairwise comparisons and change over time.
- Perform Gene Ontology analysis on upregulated and downregulated genes from the pairwise DGEA.
