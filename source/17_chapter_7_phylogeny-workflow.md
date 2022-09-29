\singlespacing
\setlength{\parindent}{0.0in}
# One two, tree! A workflow for creating state of the art phylogenies designed for reproducibility with JuPyter, conda and git.
\label{phylogeny_workflow}

\footnotesize
Laura W Dijkhuizen^1^
Erbil Güngör^1^
Henriette Schluepmann^1^

\scriptsize
1. Laboratory of Molecular Plant Physiology, Department of Biology, Utrecht University, Utrecht, The Netherlands

\newpage
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

## Abstract

## Introduction
Life Sciences has entered the big-data age; we have an unprecedented detailed view on the storage and processing of information in biological systems.
This view is possible due to the ever decreasing prices of sequencing of DNA, RNA and protein.
Consequently, biologist are challenged less with acquiring data, and more with its processing and gaining insight from it.
Phylogenetics is one answer to that challenge.
Phylogenetics can organise sequences by their hypothesised evolution, in phylogenetic trees.
Afteral, how does anything in biology make sense except in the light of evolution.

In principle, two types of phylogenetic trees exist: gene trees, and species trees.
Gene trees depict the hypothetical pattern in which several sequences are related to each other.
If a single organism contains two copies of a gene, the organism's name will appear twice in the tree.
Hence the tree nodes, the bifurcations, may represent speciations as well as gene duplications.
Species trees depict speciations only.
When novices think of phylogenetic trees, they often think of species trees.
However, in practice, researchers often make gene trees instead.

`dummy figure species vs gene trees and orthology and paralogy, `

Gene trees allow us to answer basic but important questions in comparative genomics.
When presented with many gene sequences that are similar (homologs), we may use gene trees to see if these sequences are a result of a gene duplication (paralogs) or a speciation (orthologs).
Orthology is a key concept for reading phylogenetic trees.
If two sequences were separated because of speciation, and we assume they are the only copies both species their genomes, we may conclude that selection presure has occured on this particular gene.
Hence, when reading a phylogenetic gene tree, we often assume that orthologous genes are functionally similar.

The _Azolla_ lab has particular interest in such a tool.
We are not only involved in the genomics of a novel crop but more specifically of the very first genome of a fern ever sequenced.
No gene's function in Azolla was ever verified and we have no close relative to compare _Azolla_ sequences with.
Hence, homology and comparative genomics are essential in assigning meaning to the genome sequences we have acquired in @Li2018.
While often, gene function is attributed on mere homology, there are cases where several homologs are present in a genome.
We used gene trees to attribute these homologs to any one orthologous group via gene trees.
One examples was included in this thesis before in chapter \ref{it_takes_two} in +@fig:fig6_8.
A second example can be found in the supplemental material of the same publication.

Phylogenetics is in the first place a comparative exercise, hence to gain insight in the evolution of any protein sequence, one must compare it to related sequences.
As plant biologists studying ferns, we are challenged by a lack of non-seed plant genomes available to us.
Luckily, the recent 1kP project [@1kp] provides solution by collecting the genomes and assembled transcriptomes of 1000 plant species.
The 1kP effort fills a gap in reference databases, providing protein coding sequences for a large number of seed-free plants.
As fern researchers, we make intensive use of the 1kP project and we use it in the examples included here.

Given the increasing intrest in phylogeny in our lab, and inspired by my previous endavours to make my scientific practice more reproducible, I created a workflow to create phylogenetic trees.
With this workflow, I aim to circumvent limitations of other existing all-in-one or web based solutions.
This chapter shortly summarises these existing tools and their limitations, and my design considerations in making my own workflow.
This workflow is openly available and usable under a Creative Commons License at [GitHub.com/lauralwd/lauras_phylogeny_wf](https://github.com/lauralwd/lauras_phylogeny_wf)
Finally, several examples of the workflow in practice are included to demonstrate its application in tackling biological questions of the _Azolla_ lab.

## Methods
JuPyter notebooks and GitHub

### data
1kP

### tools
MAFFT, trimAL, IQtree, iToL

## results

### Existing tools

MEGA Software

other workflows

### web based tools

### This workflow

### examples

#### LAR

#### 2OGD

#### MYB & MIKc

## discussion
