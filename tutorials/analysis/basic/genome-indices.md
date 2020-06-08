## Reference genome indexing

### Description

Mapping of large sets of high-throughput sequencing reads to a reference genome is one of the foundational steps in RNA-seq/ChIP-Seq data analysis. The mapping software e.g. [STAR](https://github.com/alexdobin/STAR), [bowtie](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml), [kallisto](https://pachterlab.github.io/kallisto/manual) packages perform this task with high levels of accuracy and speed. To achieve it mapping tools at first have to build indices of reference genomes and than use pre-computed indices for aligning short reads utilizing the index as a guide. This is the first step of many comparative genomics workflows, including variant detection and digital gene expression. In what follows, the term read refers to a short DNA sequence, typically as output by a sequencing instrument.

In SciDAP this task runs once for each genome of interest. It creates indices and annotations for all downstream tools that are used in later analyses such as transcript/gene expression quantification, chromatin enrichment, etc.

### Details

Creates indices for:
* [STAR](https://github.com/alexdobin/STAR) PMID: [23104886](https://www.ncbi.nlm.nih.gov/pubmed/23104886)
* [bowtie](http://bowtie-bio.sourceforge.net/tutorial.shtml)

It performs the following steps:

1. `STAR --runMode genomeGenerate` generates indices, based on genome [FASTA](http://zhanglab.ccmb.med.umich.edu/FASTA/) and [GTF](http://mblab.wustl.edu/GTF2.html) input files
2. Separates *chrNameLength.txt* file from STAR output, to be used as input in downstream analysis
3. `bowtie-build` generates indices based on genome [FASTA](http://zhanglab.ccmb.med.umich.edu/FASTA/) file

As an example, for Human genome (hg38) we recommend generating indices based on the [FASTA](http://zhanglab.ccmb.med.umich.edu/FASTA/) files for the main chromosomes (chr1-22,X,Y,M) downloaded from
[ftp://hgdownload.cse.ucsc.edu/goldenPath/hg38/chromosomes](ftp://hgdownload.cse.ucsc.edu/goldenPath/hg38/chromosomes)
Annotation file can be fetched from
[http://hgdownload.cse.ucsc.edu/goldenPath/hg38/database/refGene.txt.gz](http://hgdownload.cse.ucsc.edu/goldenPath/hg38/database/refGene.txt.gz) (doesn’t include chrM) or [ftp://hgdownload.soe.ucsc.edu/goldenPath/hg38/database/wgEncodeGencodeBasicV28.txt.gz](ftp://hgdownload.soe.ucsc.edu/goldenPath/hg38/database/wgEncodeGencodeBasicV28.txt.gz)
