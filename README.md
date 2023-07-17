# Synthetic Genomics Data Generation and Evaluation for the Use Case of Benchmarking Somatic Variant Calling Algorithms


This is the repository for the analysis that was presented as poster in ISMB/ECCB23, Lyon, France.

All data are open and available [here](https://zenodo.org/record/8095898).



## Installation
1. To install NEAT follow the intructions [here](https://github.com/ncsa/NEAT/blob/master/README.md#installation).
2. To install GATK-Mutect2 follow the intructions [here](https://gatk.broadinstitute.org/hc/en-us/articles/360036194592-Getting-started-with-GATK4).
3. To install bam-readcount follow the instructions [here](https://github.com/genome/bam-readcount/tree/master#installation).
4. To create the conda environment that was used for the analysis run `conda env create -f environment.yml`


## Execution
Here follows the list of all scripts and their description:

`01_SynthDataGeneration.sh` - This bach script calls NEAT in order to generate 10 individual synthetic data datasets.

- Input: fasta reference file
							 
- Output: fastq files with pair end reads, "golden" bam file and bai index file, "golden" vcf file

`02_bam-readcount_reports.sh` - This bash script calls bam-readcount to produce the bam reports with the genomic content at certain chromosomal positions.

- Input: fasta reference file, "golden" bam file
							 
- Output: tsv file with the genomic content

`03_VariantCalling.sh` - This bash script takes the Merged bam file and performs some preprocess steps before using Mutect2 to implement somatic variant calling.

- Input: Merged bam file, fasta reference file
							 
- Output: processed bam files and vcf file with all variants that were detected

`04_load_bam_reports.R` - This R script compares the variants that Mutect2 reported against the ground truth. Firsty it identifies the variants with 100% Allele Frequency(AF) in the individual bam files and then caclulates their AF in the final Merged bam file.

- Input:  bam-readcount tsv reports, vcf file from Mutect2
							 
- Output: tsv file containing infrtomation regarding the ground truth variants

`05_clean_and_annotate.R` - 

`06_position_annotation.R` - 

`07_bar_plots.R` - 

`07_bubble_plots.R` - 

`07_density_plot.R` - 

`07_reference_barplot.R` - 

`08_mutation_overlap.R` - 

`09_patchwork.R` - 

(The first 3 steps of the pipeline are optional since all the files are provided either in this repository or in the zenodo link.)


## Contribute

We welcome any sort of contribution!
If you have any developer-related questions, please open an issue or write us at sfragkoul@certh.gr.


## Citation
Styliani-Christina Fragkouli and Nikolaos Pechlivanis and Andreas Agathangelidis and Fotis Psomopoulos, *Synthetic Genomics Data Generation and Evaluation for the Use Case of Benchmarking Somatic Variant Calling Algorithms*, 31st Conference in Intelligent Systems For Molecular Biology and the 22nd European Conference On Computational Biology (ISΜB-ECCB23), 2023, doi: TBA

