# TCGA-Differential-Expression-Pathway-Enrichment-Analysis-LUAD-
This project performs a complete RNA-seq analysis pipeline for TCGA-LUAD (Lung Adenocarcinoma) using R. It includes data preprocessing, quality control, differential expression (DE) analysis, visualization, and pathway enrichment to identify biologically meaningful gene expression changes between tumor and normal tissues.


This repository contains an **end-to-end RNA-seq analysis pipeline** for **TCGA-LUAD (Lung Adenocarcinoma)** using R.  
It performs data preprocessing, quality control, differential expression (DE) analysis, visualization, and pathway enrichment to identify biologically meaningful gene expression changes between **tumor** and **normal** tissues.

---

##  Overview

This workflow was built using:

- **DESeq2** – for differential expression analysis  
- **edgeR** – for normalization and filtering  
- **EnhancedVolcano / pheatmap** – for visualizing DE results  
- **clusterProfiler / ReactomePA** – for functional and pathway enrichment  
- **org.Hs.eg.db** – for human gene annotation  

All steps were chosen to ensure **biological accuracy**, **reproducibility**, and **clarity of interpretation** for TCGA transcriptomic data.

---

## Workflow Summary
**1. Data Extraction and Cleaning**

Expression counts and clinical metadata are extracted from TCGA, cleaned, and matched by sample ID. A grouping variable (Tumor vs Normal) is created for downstream analysis.
This ensures the DESeq2 model can properly compare tumor and normal samples.

**2. Quality Control and Normalization**

edgeR is used to filter out low-expression genes and perform TMM normalization to correct for differences in library sizes.
PCA (Principal Component Analysis) is then run to check clustering of samples and detect outliers.

**3. Differential Expression (DESeq2)**

DESeq2 models gene counts using a negative binomial distribution. It identifies genes that are significantly up- or down-regulated in tumors while controlling for multiple testing (Benjamini–Hochberg correction).

**4. Visualization**

Plots such as PCA, volcano plots, and heatmaps are created to visualize sample separation, highlight top DEGs, and show expression patterns of significant genes.

## Pathway Enrichment and Annotation

After identifying significant DEGs (adjusted p-value < 0.05), the next step is to understand their biological relevance using GO (Gene Ontology), KEGG, and Reactome pathway enrichment.

**Step 1 – Filter Significant DEGs**

Genes with adjusted p-values below 0.05 are retained. This filters out non-significant results and reduces false positives.

**Step 2 – Convert Ensembl IDs to Entrez IDs**

Most pathway databases use Entrez Gene IDs rather than Ensembl IDs, so ID conversion is performed using the mapIds() function. This ensures compatibility with enrichment functions.

**Step 3 – Create Ranked Gene List (for GSEA)**

A ranked list of all genes by log2 fold change is created. This is used for Gene Set Enrichment Analysis (GSEA) to detect subtle, coordinated changes in gene expression across pathways.

**Step 4 – Gene Ontology (GO) Enrichment**

GO enrichment analysis identifies biological processes (BP) that are overrepresented among significant DEGs, such as cell cycle regulation or immune response.

**Step 5 – KEGG Pathway Enrichment**

KEGG analysis identifies altered signaling and metabolic pathways in tumors, for example, PI3K-Akt, MAPK, or p53 signaling.

**Step 6 – Reactome Pathway Enrichment**

Reactome provides more detailed molecular pathway maps and complements KEGG by offering a more curated and interactive perspective of gene function.

## Output Files

All key results are saved for easy access and reproducibility:

-  deseq2_results.csv → differential expression table

-  GO_BP.csv → GO Biological Process enrichment results

-  KEGG.csv → KEGG pathway enrichment results

-  Reactome.csv → Reactome pathway enrichment results

## Key Takeaways

-  DESeq2 identifies statistically significant DEGs between tumor and normal samples.

-  Visualizations (PCA, volcano, heatmap) provide intuitive summaries of the data.

-  Pathway enrichment translates gene-level results into biological meaning.

-  The pipeline is fully reproducible and suitable for portfolio use, research reports, or publication.
