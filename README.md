# mpileup2stats 

This code takes samtools mpileup format and extracts per-site information. 

Uses third-party code (e.g. pileup2base) to extract some of its features 

# Comparison to EpiNano
EpiNano computes per-read statistics and then per-site, using the per-read files.

This software computes per-site stats directly from samtools mpileup.

# When to use EpiNano or this code?
This code is better suited for the analysis of RNA modifications in cDNA datasets, where the per-read information is more irrelevant. Also, this code provides information both on mismatches as well as on RT drop-offs. 

# Disclaimers
I believe that if it has a part of the gene without coverage, it may fail. 
Please let me know if this is the case (Eva)

# Author
Written by Eva Novoa (2017). 
Last updated: April 2020. 

 
