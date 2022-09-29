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

NJ, ML and Baysian. What and why
I consider Baysian approaches too advanced for the audience that this workflow is aimed at.

Phylogenetics is in the first place a comparative exercise, hence to gain insight in the evolution of any protein sequence, one must compare it to related sequences.
As plant biologists studying ferns, we are challenged by a lack of non-seed plant genomes available to us.
Luckily, the recent 1kP project [@Leebens-Mack2019] provides solution by collecting the genomes and assembled transcriptomes of 1000 plant species.
The 1kP effort fills a gap in reference databases, providing protein coding sequences for a large number of seed-free plants.
As fern researchers, we make intensive use of the 1kP project and we use it in the examples included here.

Given the increasing intrest in phylogeny in our lab, and inspired by my previous endavours to make my scientific practice more reproducible, I created a workflow to create phylogenetic trees.
With this workflow, I aim to circumvent limitations of other existing all-in-one or web based solutions.
By providing this workflow openly, and by documenting my own use of it on GitHub and Zenodo, I aim to inspire other reseachers to also make their analyses more reproducible and share their coding towards more reproducible research.

This chapter shortly summarises data and software tools used for the workflow, alternative tools and their limitations, and my design considerations in making my own workflow.
This workflow includes gathering data from the 1kP project [@Leebens-Mack2019], alignment of protein sequences, trimming of this allignment and tree inference via frequentist methods.
Additionally, several examples of the workflow in practice are included to demonstrate its application in tackling biological questions of the _Azolla_ lab.
This workflow is openly available and usable under a Creative Commons License at [GitHub.com/lauralwd/lauras_phylogeny_wf](https://github.com/lauralwd/lauras_phylogeny_wf)

## Methods
The state of the art tools required for phylogenetics are often desgined for Linux systems.
Using BASH scripts -BASH being the Linux-native programming language- can be a steep learning curve for novice users.
Therefor I use JuPyuter notebooks to supply the user of the workflow with written instructions and pre-written BASH code.
A JuPyter notebook is an interacive document in which the user can run said code, as well as journal their decissions and observations

Software installation on Linux can be challenging, especially if certain versions of software may be incompatible.
Therefore I make use of the conda or miniconda frameworks `cite` to supply any user with a ready made software environment that has all the required tools available.
This environment also contains the software required to run the JuPyuter notebooks.
Conda environments contain a list of all the software and the specific versions of that software, so future users may reproduce any analysis with the exact same software version.
The recommended route is to install git and miniconda3 following the miniconda3 instructions (https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html) on your system.
For Linux and MacOS systems, this runs natively.
For Windows systems, we have had good experience useing the Windows Sublayer for Linux (WSL).
In our experience, these three systems all run miniconda3 without any issue.
When git and miniconda3 are installed on your system, the required software may be installed via the following BASH commands:
```
git clone https://github.com/lauralwd/lauras_phylogeny_wf.git
cd lauras_phylogeny_wf
conda env create -f conda_environment.yaml
conda activate phylogenetics
```
A small snippit of the `conda_environment.yaml` file is included below.
It details the relevant software and exact version and build so any future researcher may reproduce results exacly.
```
name: phylogenetics
channels:
  - conda-forge
  - bioconda
  - defaults
dependencies:
  - _libgcc_mutex=0.1=conda_forge
  - _openmp_mutex=4.5=1_gnu
  - alsa-lib=1.2.3=h516909a_0
  - ca-certificates=2021.5.30=ha878542_0
  - cairo=1.16.0=h6cf1ce9_1008
  - certifi=2021.5.30=py39hf3d152e_0
  - fasttree=2.1.10=h779adbc_5
  - iqtree=2.1.2=h56fc30b_0
  - jalview=2.11.1.4=hdfd78af_
  - jpeg=9d=h36c2ea0_0
  - mafft=7.480=h779adbc_0
  - python=3.9.4=hffdb5ce_0_cpython
```
Finally, a user may make use of Git versioning software to document progress of their workflow, and possiblly maintain multiple versions thereoff.
The JuPyter notebooks, some -but not all- data files, and the conda environment can be stored in Git.
Whenever any file is changed, i.e. a analysis step is done successfully, this change can be appended to the Git history (+@fig:fig7_git_zenodo A).
When done well, this 'commit' to the Git history contains a very short written explanation of the added history.
This might be a short line like `added raw data from 1kP project`, or `trimmed alligned fasta file and document parameter choice`.

![Online documentation of the phylogeny workflow on R2R3 MYB phylogeny in chapter \ref{it_takes_two}. The Git history shown on GitHub (A) details steps taken in finalising the phylogeny and the resulting figure. The finalised Git repository and all imortant files are archived on zenodo (B) with a DOI ([zenodo.org/badge/latestdoi/283424814](https://zenodo.org/badge/latestdoi/283424814)) ](source/figures/fig7_git_zenodo.pdf){#fig:fig7_git_zenodo}

A Git repository containing the workflow may be uploaded online to services like GitHub or GitLab or a self-hosted Git server.
This does not only provide instant back-ups of the workflow but also facilitates collaboration on the project with state-of-the art versioning software.
Indeed, using Git for this purpose could be considered relativelly advanced and one may argue that users of this level may not need the guidance that this workflow is designed to provide.
Even without collaboration, the back-up function is worth using.
Additionally, a GitHub repository can be directly linked to Zenodo and archived with a DOI for reference in future work. (+@fig:fig7_git_zenodo B)

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
