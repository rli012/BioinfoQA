# BioinfoQA

## RNAseq

1. [Question: Differential expression of FPKM from RNA-seq data using limma and voom()](https://support.bioconductor.org/p/56275/)
Three options:
(1) Get the actual integer counts from which the FPKM were computed and do a proper analysis, for example using voom or edgeR.
(2) Get the gene lengths and library sizes used to compute the FPKM and convert the FPKM back to counts.
(3) If FPKM is really all you have, then convert the values to a log2 scale (y = log2(FPKM+0.1) say) and do an ordinary limma analysis as you would for microarray data, using eBayes() with trend=TRUE. Do not use voom, do not use edgeR, do not use DESeq. (Do not pass go and do not collect $200.) This isn't 100% ideal, but is probably the best analysis available.
