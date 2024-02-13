We use Kallisto software to get the counts of each sequence variant from the raw sequencing data. 
https://pachterlab.github.io/kallisto/

For example, to get the counts of all variants in the deep mutational scan of the AAA+ module of the RR2/T4 chimeric clamp loader, this is split into two pools A and B, and subjected to the phage propagation assay.

The data is analyzed for each pool separately.
For processing the data from pool A, we first generate a fasta file of DNA sequences containing all the possible variants in the pool. This file, 1_kallisto_index_chim_AAA_poolA.fasta, is processed through Kallisto to generate an index file:
```
  kallisto index -i chim_AAA_poolA 1_kallisto_index_chim_AAA_poolA.fasta
```

The generated index file, chim_AAA_poolA, is then used to search the paired end reads as:
```
kallisto quant --fr-stranded -t 10 -i chim_AAA_poolA raw_data/D707-501_S49_L001_R1_001.fastq.gz  raw_data/D707-501_S49_L001_R2_001.fastq.gz -o chim_AAA_poolA_input.counts
```
