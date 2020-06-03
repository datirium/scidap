## Assay for Transposase-Accessible Chromatin using sequencing

### ATAC-Sequencing

ATAC-Sequencing is an assay for the identification of open chromatin regions[[1](#references)]. The Assay for Transposase Accessible Chromatin (ATAC) can identify open chromatin in a large number of cell types, and at very low cell numbers. Open chromatin is a clearing of nucleosomes from the DNA, mainly believed to accompany gene activation and regions with regulatory activity[[2](#references)]. ATAC-Seq improves the sensitivity and input requirements of historical methods for identifying open chromatin including DNAseI Hypersensitivy Assays and FAIRE-Seq, and in can be used single cells methods[[3](#references)]. Omni-ATAC is a modified ATAC procedure which reduces mitochondrial background reads, and is preferred by the Barski laboratory for its consistent and favorable results with 50,000 cells[[4](#references)].

### Method:

ATAC-Seq utilizes a Tn5 transposase enzyme which has been modified for hyperactivity to insert sequencing adapters directly onto double stranded DNA fragments. Cells are first washed, then permeabilized with digitonin to allow for transposase diffusion. During incubation with Tn5 (commercially available or can be grown from bacterial plasmid expression and purified), the illumine sequencing adapters are tagged to DNA within accessible regions. The DNA is purified, and PCR extension and amplification is performed before NGS.

[Detailed ATAC-Seq method on Active Motif site](https://www.activemotif.com/blog-atac-seq)


### ATAC-Seq analysis in SciDAP

[![ATAC-Seq](https://i9.ytimg.com/vi/nsTgTe6fe9c/mqdefault.jpg?sqp=CJCC3fYF&rs=AOn4CLCiSsv6vUAd9NQcAN6VOz_N7DfEPA)](http://www.youtube.com/watch?v=nsTgTe6fe9c "ATAC-Seq")


### References

1. Buenrostro JD, Giresi PG, Zaba LC, Chang HY, Greenleaf WJ. Transposition of native chromatin for fast and sensitive epigenomic profiling of open chromatin, DNA-binding proteins and nucleosome position. Nat Methods. 2013 Dec;10(12):1213–8. PMID: 24097267
2. Daugherty AC, Yeo RW, Buenrostro JD, Greenleaf WJ, Kundaje A, Brunet A. Chromatin accessibility dynamics reveal novel functional enhancers in C. elegans. Genome Res [Internet]. 2017/11/15. Cold Spring Harbor Laboratory Press; 2017 Dec;27(12):2096–2107. Available from: https://pubmed.ncbi.nlm.nih.gov/29141961
3. Cusanovich DA, Hill AJ, Aghamirzaie D, Daza RM, Pliner HA, Berletch JB, Filippova GN, Huang X, Christiansen L, DeWitt WS, Lee C, Regalado SG, Read DF, Steemers FJ, Disteche CM, Trapnell C, Shendure J. A Single-Cell Atlas of in vivo Mammalian Chromatin Accessibility. Cell [Internet]. Elsevier; 2018 Aug 23;174(5):1309-1324.e18. Available from: https://doi.org/10.1016/j.cell.2018.06.052
4. Corces MR, Trevino AE, Hamilton EG, Greenside PG, Sinnott-Armstrong NA, Vesuna S, Satpathy AT, Rubin AJ, Montine KS, Wu B, Kathiria A, Cho SW, Mumbach MR, Carter AC, Kasowski M, Orloff LA, Risca VI, Kundaje A, Khavari PA, Montine TJ, Greenleaf WJ, Chang HY. Omni-ATAC-seq: Improved ATAC-seq protocol. Nature Publishing Group; 2017 Aug 29; Available from: http://dx.doi.org/10.1038/protex.2017.096
