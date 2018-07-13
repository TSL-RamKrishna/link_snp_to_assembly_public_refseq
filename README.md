## Introduction

There are very few plant species that are highly annotated. Often biologists work with a closely related species to those annotated species. Let's say, I work on a species closely related to Arabidopsis thaliana. I have an incomplete assembly with contigs/scaffolds. I have done SNP analysis and filtered out only the interested SNPs from the species of my interest. I want to know the subsequence containing a SNP of interest comes from which chromosome, but the problem is, my assembly has contig/scaffold numbering, not chromosome information. I can blast the subsequence with SNP to the public reference to get the chromosome info and to the assembly to get the contigs/scaffold number, but they are in separate output files. I want to have SNP chromome (from public reference) and contigs/scaffold name in one file to make links. This program tries to make that link.

## Method

1) blasts the SNP subsequence to public reference obtaining only the best number of hits user specified (e.g. top 3 hits).
2) from the blast output, extract the start and end position of the reference sequence where the SNP subsequence mapped. Using the start and end positions, the subsequence is extracted from the reference sequence. This can be done for the subsequence with SNP too.
3) the extracted sequences in FASTA format now has combined sequence identifiers containing both sequence identifiers from public reference and SNP subsequence. This way it links the sequences.
4) The extracted sequences are then mapped to the assembly of your species. The blast output now has sequence identifiers from all three datasets.

## Requirements

1) Blast+
2) python, biopython
3) ruby, rake

## usage

rake -f rakefile input=reference/testinput.fasta reference=reference/test_public_reference.fasta reference2=reference/myassembly.fasta num_alignments=2 
