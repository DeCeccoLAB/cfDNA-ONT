# Fragmenting the Future: Development of a Comprehensive Fragmentomics Pipeline Powered by Nanopore Sequencing Data
After sequencing, the raw signal data were used for basecalling with the Dorado 
basecaller, and the resulting reads were aligned to the human reference genome 
(hg38) using minimap2. Tumor fraction and copy number variations (CNVs) were 
estimated using the HMMcopy and ichorCNA packages from Bioconductor/R. 

For motif analysis, we extracted the first four nucleotides at the 5′ end of each 
aligned read using a method based on that described in Katsman et al., 2022. To 
reduce complexity and identify recurring patterns among samples, Non-negative 
Matrix Factorization (NMF) was applied to the matrix of motif frequencies. This 
approach allowed the extraction of three main profiles, each characterized by a 
specific set of dominant motifs, representing underlying patterns that explain 
the variability observed among the samples.

## Basecalling and Alignment

### Command

```bash
/path/to/dorado/bin/dorado basecaller hac \
  --modified-bases 5mCG_5hmCG \
  --emit-moves \
  --device cuda:all \
  --no-trim \
  --reference /path/to/reference/genome.fa \
  /path/to/input_fast5_directory \
  | samtools view -b -o /path/to/output/output_pass.bam

Description

This command performs basecalling of raw Nanopore signal data using the Dorado basecaller with detection of modified bases (5mC and 5hmC). The reads are aligned to a specified reference genome, and the resulting output is converted into a BAM file using Samtools for downstream analysis.
Requirements

    Dorado ≥ 0.8

    Samtools ≥ 1.10

    CUDA enabled GPU for acceleration

    Reference genome in FASTA format

    Raw Nanopore FAST5 files

Reference

    Dorado basecaller: https://github.com/nanoporetech/dorado



