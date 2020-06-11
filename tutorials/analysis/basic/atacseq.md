## Assay for Transposase-Accessible Chromatin using sequencing

### ATAC-Sequencing

ATAC-Sequencing is an assay for the identification of open chromatin regions[[1](#references)]. The Assay for Transposase Accessible Chromatin (ATAC) can identify open chromatin in a large number of cell types, and at very low cell numbers. Open chromatin refers to areas of DNA that are not protectedby nucleosomes or other proteins making them accessible to DNase or Tn5 transposase. Open chromatin often accompany sites of TF binding, enhancers and active promoters and is associated with gene activation [[2](#references)]. ATAC-Seq improves the sensitivity and input requirements of historical methods for identifying open chromatin including DNAseI Hypersensitivy Assays and FAIRE-Seq, and in can be used single cells methods[[3](#references)]. Omni-ATAC is a modified ATAC procedure which reduces mitochondrial background reads, and is preferred by the Barski laboratory for its consistent and favorable results with 50,000 cells[[4](#references)].

### Method:

ATAC-Seq utilizes a Tn5 transposase enzyme which has been modified for hyperactivity to insert sequencing adapters directly onto double stranded DNA fragments. Cells are first washed, then permeabilized with digitonin to allow for transposase diffusion. During incubation with Tn5 (commercially available or lab purified), the Illumina sequencing adapters are tagged to DNA within accessible regions. The DNA is purified, and PCR extension and amplification is performed to craete an NGS library.

[Detailed ATAC-Seq method on Active Motif site](https://www.activemotif.com/blog-atac-seq)


### Data Analysis
SciDAP starts from the .fastq files which most DNA cores and commercial NGS companies return. Starting from raw data allows us to ensure that all experiments have been processed in the same way and simplifies the deposition of data to GEO upon publication. The data can be uploaded from users computer, downloaded directly from an ftp server of the core facility by providing a URL or from GEO by providing SRA accession number.
Our current pipelines include the following steps:
1. Trimming the adapters with TrimGalore. This step is particularly important when the reads are long and the fragments are short as in ATAC -resulting in sequencing adapters at the end of read. If adapter is not removed the read will not map. TrimGalore can recognize standard adapters, such as Nexterra/Tn5 adapters.
2. QC
3. (Optional) trimming adapters on 5' or 3' end by the specified number of bases.
4. Mapping reads with BowTie. Only uniquely mapped reads with less than 3 mismatches are used in the downstream analysis. Results are saved as a .bam file.
5. Reads mapping to chromosome M are removed. Since there are many copies of chromosome M in the cell and it is not protected by histones, some ATAC libraries have up to 50% of reads mapping to chrM. We recommend using OMNI-ATAC protocol that reduces chrM reads and provides better specificity. 
6.  (Optional) Removal of duplicates (reads/pairs of reads mapping to exactly same location). This step is used to remove reads overamplified in PCR. Unfortunately, it may also remove "good" reads. We usually do not remove duplicates unless the library is heavily duplicated. Please note that MACS2 will remove 'excessive' duplicates during peak calling ina smart way (those not supported by other nearby reads).
7.  Peakcalling by MACS2. (Optionally), it is possible to specify read extension length for MACS2 to use if the length determined automatically is wrong. 
8.  Generation of BigWig coverage files for display on the browser. Since the cuts by the Tn5 transposome are 9bp apart, we show coverage by 9bp reads rather than fragments as in ChIP-Seq. The coverage shows the number of fragments at each base in the genome normalized to the number of millions of mapped reads. This way the peak of coverage will be located at the most accessible site. 

[![ATAC-Seq](https://img.youtube.com/vi/nsTgTe6fe9c/0.jpg)](https://www.youtube.com/watch?v=nsTgTe6fe9c "ATAC-Seq")


### References

1. Buenrostro JD, Giresi PG, Zaba LC, Chang HY, Greenleaf WJ. Transposition of native chromatin for fast and sensitive epigenomic profiling of open chromatin, DNA-binding proteins and nucleosome position. Nat Methods. 2013 Dec;10(12):1213–8. PMID: 24097267
2. Daugherty AC, Yeo RW, Buenrostro JD, Greenleaf WJ, Kundaje A, Brunet A. Chromatin accessibility dynamics reveal novel functional enhancers in C. elegans. Genome Res [Internet]. 2017/11/15. Cold Spring Harbor Laboratory Press; 2017 Dec;27(12):2096–2107. Available from: https://pubmed.ncbi.nlm.nih.gov/29141961
3. Cusanovich DA, Hill AJ, Aghamirzaie D, Daza RM, Pliner HA, Berletch JB, Filippova GN, Huang X, Christiansen L, DeWitt WS, Lee C, Regalado SG, Read DF, Steemers FJ, Disteche CM, Trapnell C, Shendure J. A Single-Cell Atlas of in vivo Mammalian Chromatin Accessibility. Cell [Internet]. Elsevier; 2018 Aug 23;174(5):1309-1324.e18. Available from: https://doi.org/10.1016/j.cell.2018.06.052
4. Corces MR, Trevino AE, Hamilton EG, Greenside PG, Sinnott-Armstrong NA, Vesuna S, Satpathy AT, Rubin AJ, Montine KS, Wu B, Kathiria A, Cho SW, Mumbach MR, Carter AC, Kasowski M, Orloff LA, Risca VI, Kundaje A, Khavari PA, Montine TJ, Greenleaf WJ, Chang HY. Omni-ATAC-seq: Improved ATAC-seq protocol. Nature Publishing Group; 2017 Aug 29; Available from: http://dx.doi.org/10.1038/protex.2017.096
