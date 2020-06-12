## RNA-sequencing

### Overview

RNA-seq (RNA-sequencing) is a technique that helps to quantify RNA in a sample using next generation sequencing (NGS). It analyzes the transcriptome or gene expression pattern within the cell population. Here, we look at why RNA-seq is useful, how the technique works, and the basic protocols which are commonly used today.
A typical RNA-seq experimental workflow involves the isolation of RNA from samples of interest, generation of sequencing libraries, use of a high-throughput sequencer to produce hundreds of millions of short paired-end reads, alignment of reads against a reference genome or transcriptome, and downstream analysis for expression estimation, differential expression, transcript isoform discovery, and other applications.

A typical gene expression and differential expression analysis has several common themes across different tool sets and RNA-seq analysis goals. RNA-seq analysis typically relies on inputs such as reference genome sequences, gene annotations, and raw sequence data. Working with these inputs requires familiarity with several standardized file formats such as FASTA (.fa), FASTQ, and gene transfer format (GTF). Typical RNA-seq analysis workflows start with raw data quality control (QC), then perform read trimming, alignment or assembly of reads, apply customized algorithms for a particular analysis goal (e.g., Cufflinks and Cuffdiff for gene expression analysis), and end with summarization and visualization of the results.

### SciDAP RNA-Seq workflow

Current workflow consist of the following steps:
1. Trim adapters from input FASTQ files.
2. Use STAR to align reads from input FASTQ files according to the predefined reference indices; generate unsorted BAM file and alignment statistics file.
3. Use fastx_quality_stats to analyze input FASTQ files and generate quality statistics files
4. Use samtools sort to generate coordinate sorted BAM(+BAI) file pair from the unsorted BAM file obtained on the step 1 (after running STAR).
5. Generate BigWig file based on the sorted BAM file. For the dUTP/strand-specific pipelines  bigwig files for each strand will be produced. Please note that the reads map to the _opposite strand_.
6. Map input FASTQ files to predefined rRNA reference indices using Bowtie to define the level of rRNA contamination; export resulting statistics to file.
7. Calculate isoform expression level for the sorted BAM file and GTF/TAB annotation file using GEEP reads-counting utility; export results to file.

### Video performing RNA-Seq analysis in SciDAP

[![RNA-Seq](https://img.youtube.com/vi/NI_pr5hxJdU/0.jpg)](https://youtu.be/NI_pr5hxJdU "RNA-Seq analysis in SciDAP")


### View RNA-Seq results in SciDAP

[![RNA-Seq](https://img.youtube.com/vi/hkdq9Cgcu2Q/0.jpg)](https://youtu.be/hkdq9Cgcu2Q "View RNA-Seq results in SciDAP")
