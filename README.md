# Galaxy_NGS
This repository features the Galaxy workflows used for the NGS project.
In this project 3 different workflows were used for: short reads, long reads and a hybrid workflow using both long and short reads. 

Collective tools used in all three workflows:

FastQC - (Galaxy Version 0.74+galaxy1) – default parameters 

FastQC is a tool used to check the quality of raw sequencing data. It analyses FASTQ files before further bioinformatics processing. The program evaluates factors like base quality, GC content, duplication levels, and adapter contamination. It summarizes the results in an easy-to-read HTML report with graphs and warnings. Its goal is to detect problems early so poor-quality data can be filtered or corrected before analysis.

BUSCO - (Galaxy Version 5.8.0+galaxy2) – default parameters

BUSCO is a tool used to evaluate how complete a genome assembly, transcriptome, or gene set is. It works by searching for a set of highly conserved single-copy genes that are expected to be present in nearly all organisms of a given lineage. The tool classifies these genes as complete, duplicated, fragmented, or missing. It then summarizes the results as a percentage-based score of genome completeness. The main goal of BUSCO is to provide a biological measure of assembly quality, helping researchers judge whether their data is complete enough for further analysis.

Quast - (Galaxy Version 5.3.0+galaxy1) – default parameters

QUAST is a tool used to evaluate the quality of genome assemblies by calculating a wide range of assembly statistics. It does not build or improve assemblies, but instead checks how good an existing assembly is. It measures features such as contig count, total assembly length, and N50 values to describe how fragmented or continuous the assembly is. If a reference genome is available, QUAST can also detect misassemblies, structural errors, and alignment accuracy. It then compares these metrics across one or multiple assemblies to help identify which assembly is best. The final output is a detailed report with tables and plots summarizing assembly quality and completeness.

Staramr - (Galaxy Version 0.12.1+galaxy0) – default parameters

staramr is a bioinformatics tool used to detect antimicrobial resistance (AMR) genes in bacterial genome assemblies. It works by scanning assembled contigs against curated databases such as ResFinder, PlasmidFinder, and PointFinder to identify known resistance genes and mutations. The tool then combines these findings to predict the organism’s resistance profile and possible antibiotic resistance phenotype. It also generates a structured report summarizing detected genes, plasmids, and sequence typing information. The main goal of staramr is to quickly and accurately determine antimicrobial resistance patterns from genome data to support clinical and research analysis.

Kraken2 - (Galaxy Version 2.17.1+galaxy0) – default parameters

Kraken2 is a tool used to classify sequencing reads by identifying which organisms they come from. It is mainly used in metagenomics to analyze mixed microbial samples. It works by matching short DNA k-mers from each read against a reference database of known genomes. Based on these matches, it assigns each read a taxonomic label such as species or genus. The goal of Kraken2 is to quickly determine the composition of organisms in a sequencing sample.

Prokka - (Galaxy Version 1.14.6+galaxy1) – default parameters

Prokka is a tool used to rapidly annotate prokaryotic genomes from assembled DNA sequences. It takes contigs (FASTA files) from a genome assembly and identifies genes such as protein-coding sequences (CDS), tRNA, and rRNA. It then assigns putative functions to these genes by comparing them to reference databases. The output includes standard files like GFF and GenBank formats that can be used for visualization or further analysis. The goal of Prokka is to convert a raw genome assembly into a biologically meaningful, annotated genome in a fast and automated way.


Tools used in both the short reads and hybrid workflow:

MultiQC - (Galaxy Version 1.33+galaxy3) – default parameters

MultiQC is a tool that combines results from many bioinformatics QC and analysis programs into one single report. It does not analyze raw sequencing data itself, but instead collects outputs from tools like FastQC, BUSCO, QUAST, and others. It scans a directory of analysis results, extracts key statistics from different files, and merges them into a unified overview. This allows users to compare multiple samples and multiple tools side by side in one place. The final output is an interactive HTML report with graphs, tables, and summaries.

Create assemblies with Unicycler - (Galaxy Version 0.5.1+galaxy0) – default parameters

This tool assembles bacterial genomes from sequencing reads into longer DNA sequences called contigs. It can use short paired-end reads and optionally long reads to improve assembly quality. Short reads provide accuracy, while long reads help connect fragmented regions and resolve repeats. The tool produces a draft or sometimes complete circular genome assembly. Its goal is to reconstruct the original genome as accurately and completely as possible for further analysis.

Bandage Image - (Galaxy Version 2022.09+galaxy4) – default parameters

Bandage Image is a tool used to visualize genome assembly graphs created during de novo genome assembly. It does not assemble or analyze DNA itself, but instead turns the assembly structure into a clear image. It takes graph-based assembly output (for example from SPAdes) and displays how contigs (nodes) are connected through overlaps (edges). This helps you see repeats, branching structures, and whether the genome is fragmented or circular. The visualization makes it much easier to understand complex assembly graphs than raw text files.


Tools used in both the long reads and hybrid workflow:

Filtlong - (Galaxy Version 0.3.1+galaxy0) – default parameters

Filtlong is a tool used to filter and improve long-read sequencing data by keeping the best-quality reads and removing low-quality ones. It works on long reads (for example Nanopore or PacBio) and ranks them based on read length and sequence quality, where longer and more accurate reads are preferred. The tool then selects a high-quality subset of reads, often keeping only a percentage or target amount of data. This reduces noise and improves downstream analyses like genome assembly. The main goal of Filtlong is to produce a smaller but higher-quality long-read dataset, making assemblies more accurate and efficient.

Nanoplot - (Galaxy Version 1.46.2+galaxy0) – default parameters
\
NanoPlot is a tool used to visualize and summarize long-read sequencing data (such as Nanopore or PacBio reads). It focuses on quality control by turning raw sequencing data into clear graphs and statistics. It takes input like FASTQ, BAM, or sequencing summaries and calculates key metrics such as read length distribution, quality scores, and yield. It then converts this information into multiple plots (for example histograms, scatter plots, and boxplots) that describe the overall sequencing run. This helps you quickly understand the characteristics and quality of your long-read dataset.


Tool used in only the hybrid workflow:

Roary - (Galaxy Version 3.13.0+galaxy3) – default parameters

Roary is a tool used to build a bacterial pangenome from multiple annotated genomes. It does not work on raw reads, but on gene annotations from assemblies (usually GFF files). It compares genes across many bacterial isolates and groups them into core genes (shared by all genomes) and accessory genes (present in some but not all). This allows researchers to study genetic differences, evolution, and diversity within a species. The tool is designed to handle large datasets efficiently, making it possible to analyze hundreds or even thousands of genomes.


Tool used in only the long reads workflow:

Flye - (Galaxy Version 2.9.6+galaxy0) – default parameters

Flye is a de novo genome assembler designed for long-read sequencing data such as Oxford Nanopore or PacBio. It reconstructs genomes by finding overlaps between long, error-prone reads and building an assembly graph. It does not require a reference genome and is able to resolve many repetitive regions using long reads that span them. After building the initial assembly graph, Flye refines it and produces contiguous DNA sequences (contigs), often representing near-complete genomes.

