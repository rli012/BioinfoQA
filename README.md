# BioinfoQA

## RNAseq

[1. Question: Differential expression of FPKM from RNA-seq data using limma and voom()](https://support.bioconductor.org/p/56275/)  
Three options:  
(1) Get the actual integer counts from which the FPKM were computed and do a proper analysis, for example using voom or edgeR.  
(2) Get the gene lengths and library sizes used to compute the FPKM and convert the FPKM back to counts.  
(3) If FPKM is really all you have, then convert the values to a log2 scale (y = log2(FPKM+0.1) say) and do an ordinary limma analysis as you would for microarray data, using eBayes() with trend=TRUE. Do not use voom, do not use edgeR, do not use DESeq. (Do not pass go and do not collect $200.) This isn't 100% ideal, but is probably the best analysis available.  

[2. Question: Counting reads per gene using STAR](https://groups.google.com/forum/#!topic/rna-star/gZRJx3ElRNo)  
General Rule:  
(1) Compare the total counts over genes in the 3rd and 4th column, and select the column which has much larger total counts.  
(2) If the counts in two columns are not very different, the protocol is unstranded and you need to use the 2nd column.  
(3) Yet even an easier method is to look at the N_noFeature line for the 3rd and 4th column and pick the column with the lowest count.  

Other refrerences  
[STAR Manual](https://github.com/alexdobin/STAR/blob/master/doc/STARmanual.pdf)  
[HTSeq Manual](https://htseq.readthedocs.io/en/release_0.11.1/count.html)  
[Biostar: Explain STAR quantMode geneCounts values](https://www.biostars.org/p/218995/)  



## sratools

[1: fasterq-dump.2.9.6 err: unknown while writing file within file system module - unknown system error errno='Disk quota exceeded(122)']  
Reasons:  
Does not have enough space to store the temporary data. By default, the temporary data is downloaded in the home folder (($HOME/ncbi/public/sra).  

Solution:  
add the *-t* parameter, eg., *fasterq-dump $FILE -t tmp/*  

Other refrerences  
[The default path for downloading SRA data](http://databio.org/posts/downloading_sra_data.html)  
[HowTo: fasterq dump](https://github.com/ncbi/sra-tools/wiki/HowTo:-fasterq-dump)  
