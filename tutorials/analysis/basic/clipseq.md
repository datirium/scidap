## Cross-Linking Immunoprecipitation

### From Wikipedia

[Detailed information on wikipedia.](https://en.wikipedia.org/wiki/Cross-linking_immunoprecipitation)

`CLIP` (`cross-linking immunoprecipitation`) is a method used in molecular biology that combines UV cross-linking with
immunoprecipitation in order to analyse protein interactions with RNA or to precisely locate RNA modifications (e.g. m6A).
CLIP-based techniques can be used to map RNA binding protein binding sites or RNA modification
sites of interest on a genome-wide scale, thereby increasing the understanding of post-transcriptional regulatory networks.

The identification of sites where RNA-binding proteins (RNABPs) interact with target RNAs opens the door to understanding
the vast complexity of RNA regulation. UV cross-linking and immunoprecipitation (CLIP) is a transformative technology in which RNAs
purified from _in vivo_ cross-linked RNA-protein complexes are sequenced to reveal footprints of RNABP:RNA contacts.
CLIP combined with high-throughput sequencing (HITS-CLIP) is a generalizable strategy to produce transcriptome-wide maps of RNA
binding with higher accuracy and resolution than standard RNA immunoprecipitation (RIP) profiling or purely computational approaches.

The application of CLIP to Argonaute proteins has expanded the utility of this approach to mapping binding sites for microRNAs
and other small regulatory RNAs. Finally, recent advances in data analysis take advantage of cross-link–induced mutation sites
(CIMS) to refine RNA-binding maps to single-nucleotide resolution. Once IP conditions are established, HITS-CLIP takes ~8 d to prepare
RNA for sequencing. Established pipelines for data analysis, including those for CIMS, take 3–4 d.

### Workflow

CLIP begins with the in-vivo cross-linking of RNA-protein complexes using ultraviolet light (UV).
Upon UV exposure, covalent bonds are formed between proteins and nucleic acids that are in close proximity.
The cross-linked cells are then lysed, and the protein of interest is isolated via immunoprecipitation.
In order to allow for sequence specific priming of reverse transcription, RNA adapters are ligated to the 3' ends,
while radiolabeled phosphates are transferred to the 5' ends of the RNA fragments.
The RNA-protein complexes are then separated from free RNA using gel electrophoresis and membrane transfer.
Proteinase K digestion is then performed in order to remove protein from the RNA-protein complexes.
This step leaves a peptide at the cross-link site, allowing for the identification of the cross-linked nucleotide.
 After ligating RNA linkers to the RNA 5' ends, cDNA is synthesized via RT-PCR.
High-throughput sequencing is then used to generate reads containing distinct barcodes that identify the last cDNA nucleotide.
Interaction sites can be identified by mapping the reads back to the transcriptome.
