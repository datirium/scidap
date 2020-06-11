## Chromatin Immunoprecipitation- Sequencing (ChIP-Seq) assay


### ChIP-Sequencing

Chromatin Immuno-precipitation and Sequencing (ChIP-Seq)[[1](#references)] is widely used in the study of DNA-protein interactions. This method is used to identify the DNA binding targets of transcription factors across the genome, providing the researcher with a catalogue of DNA elements regulated by the protein of interest. Histone modifications are also widely assayed using this technique, and give insight into the structure and activation status of nearby genes. Many variations of this technique are available, and may be more suitable depending on the research question at hand and material availability.

ChIP-Seq has provided landmark insights in genome biology and understanding of gene regulation. A large database of ChIP-Sequencing experiments is available through the ENCODE project. Dr. Barski’s longstanding interest in methods development and DNA-protein interactions has yielded numerous publications utilizing this technology[[2–5](#references)].

### Method:

ChIP-Sequencing begins with the harvesting and fixation of the cell type of interest. Fixation using formaldehyde will cross-link the DNA with histones and trans-factors, capturing the complexes and conformations in one moment of time. Samples are then sonicated to shear DNA fragments to be immunoprecipitated. Samples may be manually Immunoprecipitated, or handled using one of the many automated robotics systems overnight. Both procedures will enrich your molecule of interest using antibody pulldown with protein A/G magnetic beads. Samples are de-crosslinked to release the DNA from the complexes with proteins, and DNA is amplified using a library preparation kit for NGS sequencing. We recommend Chipmentation procedure due to its simplicity and low input requirements [[6](#references)]. Libraries can be sequenced as single or paired reads at core facilities or commercial providers. The number of reads needed for successful peak calling depends on the the size of genome, efficiency of pull-down and the area of the genome covered by the modification or TF[[2](#references)]. We recommend at least 10M for transcription factors or H3K4me3 histone mark and 50-100M for H3K27me3.

### Data Analysis
SciDAP starts from the .fastq files which most DNA cores and commercial NGS companies return. Starting from raw data allows us to ensure that all experiments have been processed in the same way and simplifies the deposition of data to GEO upon publication. The data can be uploaded from users computer, downloaded directly from an ftp server of the core facility by providing a URL or from GEO by providing SRA accession number.
Our current pipelines include the following steps:
1. Trimming the adapters with TrimGalore. This step is particularly important when the reads are long and the fragments are short-resulting in sequencing adapters at the end of read. If adapter is not removed the read will not map. TrimGalore can recognize standard adapters, such as Illumina or Nexterra/Tn5 adapters.
2. QC
3. (Optional) trimming adapters on 5' or 3' end by the specified number of bases.
4. Mapping reads with BowTie. Only uniquely mapped reads with less than 3 mismatches are used in the downstream analysis. Results are saved as a .bam file.
5.  (Optional) Removal of duplicates (reads/pairs of reads mapping to exactly same location). This step is used to remove reads overamplified in PCR. Unfortunately, it may also remove "good" reads. We usually do not remove duplicates unless the library is heavily duplicated. Please note that MACS2 will remove 'excessive' duplicates during peak calling ina smart way (those not supported by other nearby reads).
6.  Peakcalling by MACS2. (Optionally), it is possible to specify read extension length for MACS2 to use if the length determined automatically is wrong. 
7.  Generation of BigWig coverage files for display on the browser. The coverage shows the number of fragments at each base in the genome normalized to the number of millions of mapped reads. In the case of PE sequencing the fragments are real, but in the case of single reads the fragments are estimated by extending reads to the average fragment length found by MACS2 or specified by the user in 6.


### ChIP-Seq analysis in SciDAP

[![ChIP-Seq](https://img.youtube.com/vi/6Fs3xb9fXII/0.jpg)](https://www.youtube.com/watch?v=6Fs3xb9fXII "ChIP-Seq analysis in SciDAP")


### View ChIP-Seq results in SciDAP

[![ChIP-Seq](https://img.youtube.com/vi/K7b7ieJlol4/0.jpg)](https://www.youtube.com/watch?v=K7b7ieJlol4 "View ChIP-Seq results in SciDAP")

### References

1. Barski A, Cuddapah S, Cui K, Roh T-Y, Schones DE, Wang Z, Wei G, Chepelev I, Zhao K. High-resolution profiling of histone methylations in the human genome Cell. 2007 May;129(4):823–37. PMID: 17512414
2. Barski,A. and Zhao,K. (2009) Genomic location analysis by ChIP-Seq. J. Cell. Biochem., 107, 11–8.
3. Wang Z, Zang C, Cui K, Schones DE, Barski A, Peng W, Zhao K. Genome-wide mapping of HATs and HDACs reveals distinct functions in active and inactive genes. Cell. United States; 2009 Sep;138(5):1019–1031. PMID: 19698979
4. Barski A, Jothi R, Cuddapah S, Cui K, Roh T-Y, Schones DE, Zhao K. Chromatin poises miRNA- and protein-coding genes for expression. Genome Res. 2009;19(10).
5. Yukawa M, Jagannathan S, Vallabh S, Kartashov A V, Chen X, Weirauch MT, Barski A. AP-1 activity induced by co-stimulation is required for chromatin opening during T cell activation. J Exp Med. 2019 Oct 25;jem.20182009. Available from: http://jem.rupress.org/content/early/2019/10/24/jem.20182009.abstract
6. Schmidl,C., Rendeiro,A.F., Sheffield,N.C. and Bock,C. (2015) ChIPmentation: fast, robust, low-input ChIP-seq for histones and transcription factors. Nat. Methods, 12, 963–5.
