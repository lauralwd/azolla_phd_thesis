# One two, tree! A JuPyter based workflow for creating state of the art phylogenies.
\label{phylogeny_workflow}

## Abstract

## Introduction
Life Sciences entered a big-data age.
Sequencing of DNA, RNA and protein has become increasingly cheaper over the years.
Consequently, the challenges we deal with as biologist are less centered around acquiring data, and more about how to process it.
Phylogenetics is one such answer.
Phylogenetics can organise sequences by their hypothesised evolution, in phylogenetic trees.
Afteral, how does anything in biology make sense except in the light of evolution.

In principle, two types of phylogenetic trees exist.
These are gene trees, and species trees.
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
Hence, no gene's function in Azolla was ever verified, hence homology and comparative genomics are essential in assigning meaning to the genome sequences we have acquired in @Li2018.
While often, gene function is attributed on mere homology, there are cases where several homologs are present in a genome.
We used gene trees to attribute these homologs to any one orthologous group via gene trees.
One examples was included in this thesis before in chapter \ref{it_takes_two} in +@fig:fig6_8.
A second example can be found in the supplemental material of the same publication.

Given the increasing intrest in phylogeny in our lab, and inspired by my previous endavours to make my scientific practice more reproducible, I created a workflow to create phylogenetic trees.
With this workflow, I aim to circumvent limitations of other existing all-in-one or web based solutions
This chapter shortly summarises these existing tools and their limitations, and my design considerations in making my own workflow.
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
