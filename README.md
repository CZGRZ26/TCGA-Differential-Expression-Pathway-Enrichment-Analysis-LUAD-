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
