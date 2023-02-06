# HSPC Circadian Rhythm Gene Expression Variation

## Samples
- RNA from 4000 HSCs, 2000 Flk2- MPPs, 2000 Flk2+ MPPs, 4000 CLPs and 4000 ckit+sca- cells per sample were submitted for scRNAseq.

## Data Preprocessing Using Scanpy in Python
- Samples are combined before any pre-processing.
- Ambient RNA removal was determined to not affect downstream analysis and was therefore removed from the pipeline.
- Remove genes expressed in less than 3 cells and remove cells with less than 200 genes expressed.
- Remove cells with mitochondrial gene percentage higher than 10% and cells with ribosomal gene percentage las than 5%.
- Remove mitochondrial, HBB genes and Malat1 as these are all the most highly expressed genes and are only used for previous QC steps and not necessary for downstream steps.
- Identify highly variable genes and use these genes to perform multiple nearest neighbor(MNN) batch correction using Time as the batch key (yielded best results in terms of UMAP and downstream Differential Gene Expression Analysis (DGEA)).

## Cell Annotation Using SingleR in R
- Use raw reacds for transcription based cell annotation with SingleR package using R.

## Data Analysis and Visualization Using Scanpy in Python
- Compute tSNE plot and UMAP using raw counts on all cell types and on each cell types separately.
- Determine known circadian gene expression using raw counts.
- Use a 1 UMI in 2% percent of cell gene filter for DGEA.
- Perform one vs the rest DGEA.
- Perform pairwise DGEA between 7am and 11pm, 11am and 7am, 7pm and 11am and 11pm and 7pm.
- Use pairwise DGEA results to find genes that are present in all pairwise comparisons and change over time.
- Perform Gene Ontology (GO) analysis on upregulated and downregulated genes from the pairwise DGEA.
### All Cell Types tSNE
![image](https://user-images.githubusercontent.com/112181040/203353111-ef55f1ae-ab3e-44d1-8e1d-4543a44fe68e.png)
### All Cell Types UMAP
![image](https://user-images.githubusercontent.com/112181040/203353147-6316e9bb-2000-48a0-8f89-ce9e23f6e15e.png)
### Known Circadian Genes Expression Heatmap for All Cell Types
![image](https://user-images.githubusercontent.com/112181040/203354649-7c9e9f20-89a7-4c4b-b9a9-429d25d247fe.png)
### tSNE, UMAP and Known Circadian Genes Expression Heatmap were generated for each cell type (HSC, Flk2- MPP, Flk2+ MPP, CLP, CMP, GMP, MEP). Here are the HSC plots as example
#### HSC tSNE
![image](https://user-images.githubusercontent.com/112181040/203353991-ccc20473-7c12-41f0-ad79-b5ae13c3d0fc.png)
#### HSC UMAP
![image](https://user-images.githubusercontent.com/112181040/203354022-bd68352b-994a-42ac-ae85-978bc1159103.png)
#### HSC Known Circadian Genes Expression Heatmap
![image](https://user-images.githubusercontent.com/112181040/203354829-9ff5ad8d-ceba-4bfb-8953-40f00c474921.png)
### HSC All vs Rest DGEA (performed for each cell type)
![image](https://user-images.githubusercontent.com/112181040/203355560-73a5af08-b727-43c4-a8bd-49b462e99a38.png)
### Expression of HSC Differentially Expressed Genes (DEGs) Through Time (performed for each cell type)
![image](https://user-images.githubusercontent.com/112181040/203355825-dd3c0fb2-15eb-48b0-ae9c-61ec461d6b25.png)
### Volcano Plof of HSC DEGs between 7am and 11pm (performed between each time point for each cell type)
![image](https://user-images.githubusercontent.com/112181040/203356474-a246dea2-ac4a-45c4-8e91-ebc079aef9f4.png)
### GO Analysis of HSC Upregulated DEGs between 7am and 11pm (performed between each time point for each cell type against several databases)
![image](https://user-images.githubusercontent.com/112181040/203356830-1787c130-deae-4de7-b121-c6840549a975.png)
### GO Analysis of HSC Downregulated DEGs between 7am and 11pm (performed between each time point for each cell type against several databases)
![image](https://user-images.githubusercontent.com/112181040/203356929-30f7a92b-14c7-4bcd-8b3a-9b4127498580.png)
