# mpileup2stats 

This code takes *samtools mpileup format* (generated from a BAM) and extracts per-site information, specifically: 
* mismatches (with proportion of bases: A,C,G,T), in addition to the mismatch frequency
* insertions
* deletions 
* coverage
* reference base (A,C,G,T)
* position in transcript
* RT drop-off.

## What can I use this code for? 
* It was written for the **RNA modifications in cDNA sequencing data** coming from Illumina RNAseq
* It can be used also for the analysis of **nanopore cDNA sequencing data**, and will be specially useful if using the CUSTOM protocol (first-strand only), because RT drop-offs will appear 
* It can also be used for the analysis of **direct RNA sequencing data**, however please consider checking EpiNano in that case, as 5mer information is not given as output here, whereas EpiNano will give you that.
* You might find this code useful to use the RT drop-off to predict isoforms from dRNAseq data, based on where you observe a big drop of coverage along your transcripts (not tested)

## Dependencies
Uses third-party code (e.g. pileup2base) to extract some of its features 

## Whats the difference between mpileup2stats and HAMR?
It does pretty much what HAMR did, but with some additional info (RT drop off and indels.
Also this code does not compute pvalues, whereas HAMR does. 

This code is MUCH MORE EFFICIENT than HAMR and takes MUCH LESS TIME to compute, and requires much FEWER RESOURCES. That's why I wrote, it, because HAMR kept failing all the time due to memory issues. 

##  Whats the difference between mpileup2stats and EpiNano?

### 1) Per-site vs per-read
- EpiNano computes per-read statistics and then per-site, using the per-read files.
- This software computes per-site stats directly from samtools mpileup.

### 2) 5mer vs 1mer
- This software will not provide output per 5mer, whereas EpiNano reports both 1mer (per-site) and 5mer

### 3) RT stops
- This code gives info about RT stops whereas EpiNano doesn't

### 4) Relative mismatch frequency
- This code will tell you the relative frequency of A:C:G:T at each site (not just the global mismatch frequency),which is important to identify the underlying RNA modification identity, as these seem to cause different "error signatures". EpiNano doesn't give this info. 
- This feature is also important for comparing different RT enzymes, they tend to change their relative misincorporation rates, in an RNA modification-dependent manner.

So: mismatch signatures depend BOTH on RT enzyme and RNA modification. Take that into account! :-)

## When to use EpiNano or this code?
This code is better suited for the analysis of RNA modifications in cDNA datasets, where the per-read information is more irrelevant. Also, this code provides information both on mismatches as well as on RT drop-offs. 

If you are analyzing direct RNA nanopore sequencing data, EpiNano typically be a better choice. 

## Disclaimers
I believe that if it has a part of the gene without coverage, it may fail. 
Please let me know if this is the case (Eva)

## Author
Written by Eva Novoa (2017). 
Last updated: April 2020. 

 
