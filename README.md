# R-Studio-for-extracting-cancer-dataset-from-TCGA
if (!require("BiocManager", quietly = TRUE))
  install.packages("BiocManager")
BiocManager::install(version = "3.18")

BiocManager::install("TCGAbiolinks")
BiocManager::install("SummarizedExperiment")

library(TCGAbiolinks)
library(SummarizedExperiment)

listSamples <- c(
  "TCGA-19-0957-10B-01D-2366-09","TCGA-14-1034-01A-01D-0518-04",
  "TCGA-06-0152-02A-01R-2005-01","TCGA-06-0125-01A-01T-0213-07",
  "TCGA-14-0736-02A-01D-2280-08","TCGA-06-0211-01A-01D-0242-05",
  "TCGA-06-0210-01A-01R-0233-01","TCGA-06-0190-01A-01D-0234-02",
  "TCGA-19-4065-02A-11R-2005-01","TCGA-06-0171-02A-11D-2366-09",
  "TCGA-06-0221-02A-11R-2005-01","TCGA-19-1389-10C-01D-0591-01",
  "TCGA-14-1402-01A-01D-0521-05"
)
query <- GDCquery(
  project = "TCGA-GBM", 
  data.category = "Transcriptome Profiling",
  data.type = "Gene Expression Quantification",
  experimental.strategy = "RNA-Seq",
  barcode = listSamples
)
GDCdownload(query)
