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


