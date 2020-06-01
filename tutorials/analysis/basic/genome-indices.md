## Reference genome indexing

### Description

Mapping of large sets of high-throughput sequencing reads to a reference genome is one of the foundational steps in RNA-seq/ChIP-Seq data analysis. The mapping software e.g. [STAR](https://github.com/alexdobin/STAR), [bowtie](http://bowtie-bio.sourceforge.net/bowtie2/index.shtml), [kallisto](https://pachterlab.github.io/kallisto/manual) packages perform this task with high levels of accuracy and speed. To achieve that mapping tools at first have to build indices of reference genomes and than use pre-computed indices for aligning short reads utilize the index as a guide. This is the first step of many comparative genomics workflows, including variant detection and digital gene expression. In what follows, the term read refers to a short DNA sequence, typically as output by a sequencing instrument.

In SciDAP this task runs once for each genome of interest, it creates indices and annotations for all downstream tools that are used in later analyses such as transcript/gene expression quantification, chromatin enrichment.

### Details

Creates indices for:
* [STAR](https://github.com/alexdobin/STAR) v2.5.3a (03/17/2017) PMID: [23104886](https://www.ncbi.nlm.nih.gov/pubmed/23104886)
* [bowtie](http://bowtie-bio.sourceforge.net/tutorial.shtml) v1.2.0 (12/30/2016)

It performs the following steps:

1. `STAR --runMode genomeGenerate` to generate indices, based on [FASTA](http://zhanglab.ccmb.med.umich.edu/FASTA/) and [GTF](http://mblab.wustl.edu/GTF2.html) input files, returns results as an array of files
2. Outputs indices as [Direcotry](http://www.commonwl.org/v1.0/CommandLineTool.html#Directory) data type
3. Separates *chrNameLength.txt* file from Directory output
4. `bowtie-build` to generate indices requires genome [FASTA](http://zhanglab.ccmb.med.umich.edu/FASTA/) file as input, returns results as a group of main and secondary files