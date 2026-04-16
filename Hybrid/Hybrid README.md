# Hybrid Workflow 
This hybrid workflow was developed to process Illumina and Nanopore sequencing data into a complete bacterial genome assembly in a standardized, efficient, and reproducible manner. By combining short reads and long reads, the workflow leverages the high accuracy of Illumina and the long fragments of Nanopore, resulting in much better assembly quality than when using either technology separately. The workflow automates all steps required to move from raw sequencing files to a fully annotated and biologically interpretable end result, thereby preventing manual errors and enabling consistent analysis.

The processing begins with unpacking compressed files and performing quality control on both the Illumina and Nanopore reads. FastQC and NanoPlot provide insight into the quality, length distribution, and any issues in the raw data. Next, the Illumina reads are prepared by interlacing them to make them suitable for hybrid assembly. The core of the workflow is Unicycler, which combines the short and long reads into a high-quality assembly. The structure of this assembly is then visually represented using Bandage, making features such as plasmids or complex regions visible.
Following the assembly, annotation is performed using Prokka, which identifies genes, coding sequences, and other functional elements in the genome. Additionally, the workflow performs resistance and virulence analysis using staramr and Kleborate, automatically detecting key traits such as AMR genes, MLST profiles, and virulence factors. Finally, QUAST assesses the quality of the assembly by reporting statistics such as N50, contiguity count, and total genome length.
By integrating all these steps into a single workflow, a complete, clear, and reproducible analysis process is created that is suitable for both education and research. The workflow yields not only a reliable assembly but also all relevant quality reports, annotations, and biological interpretations necessary for further study of the genome



This is done by using the following workflow:

![Hybrid Workflow figure](Hybrid/Screenshot_of_Hybrid_Workflow.png)
