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
Life Sciences has entered the big-data age; we have an unprecedented detailed view on the storage and processing of information within biological systems.
This view is possible due to the ever decreasing prices of sequencing of DNA, RNA and protein.
Consequently, biologist are challenged less with acquiring data, and more with its organising, processing and gaining insight from it.
Phylogenetics is one answer to that challenge.
Phylogenetics organises sequences by their hypothesised evolution: in phylogenetic trees.
Afteral, how does anything in biology make sense except in the light of evolution.

This chapter accompanies a practical workflow to infer phylogenetic trees.
It is an interactive document on GitHub which I made and used during my PhD and may be used by others as well.
This work does not try to sumarise the background needed to propperly read trees and collect data as @VanHooff2019, nor does it summarise recent technological advantages in the field as @Kapli2020.
Hence, consider these two works as essential reading before bringing this workflow into practice.
I do include a basic introduction of phylogeny: the bare minimum to understand the choices made and use-cases examplified.

With my phylogeny workflow, I aim to provide a practical guide aiding novice users in making phylogenies.
In this document I summarise the workflow, the choices I made in designing it, and examples of its implementation.
The workflow itself, may be considered similar to @Hall2013, who presents a step by step guide for infering phylogeny in MEGA5.
This work differentiates itself by using commandline tools only, emphasising documentation of intermediate files, and using only open source algorithms.
By using the Command Line tools (CML), I aim to circumvent limitations of other existing all-in-one or web based solutions.
This presents a steeper learning curve for a novice user, but increased freedom to implement any other tool of choice and to log and share analyses with peers via Git or other means.
The workflow is openly available online and I have documented my use of it on GitHub and Zenodo.
Via this route I aim to inspire other reseachers to also make their analyses more reproducible and share their code towards more reproducible research.

### Key concepts in Phylogeny
In principle, two types of phylogenetic trees exist: gene trees, and species trees.
Gene trees depict the hypothetical pattern in which several sequences are related to each other.
This organisation will remain hypothetical for one can not observe how proteins or species have evolved in the past.
If a single organism contains two copies of a gene, the organism's name will appear twice in the tree.
Hence the tree nodes, the bifurcations, may represent speciations as well as gene duplications.
Species trees depict speciations only.
When novices think of phylogenetic trees, they often think of species trees.
However, in practice, researchers often make gene trees instead.
Gene trees may seem inconsistent with with species trees due to gene duplications or losses.
The relation between gene an species trees as well as how to read them is excelently explained in @VanHooff2019.

`dummy figure species vs gene trees and orthology and paralogy, `

Gene trees allow us to answer basic but important questions in comparative genomics.
When presented with many gene sequences that are similar (homologs), we may use gene trees to see if these sequences are a result of a gene duplication (paralogs) or a speciation (orthologs).
Orthology is a key concept for reading phylogenetic trees and in detail explained in @VanHooff2019.
If two sequences were separated because of speciation, and we assume they are the only copies both species their genomes, we may conclude that selection presure has occured on this particular gene.
Hence, when reading a phylogenetic gene tree, we often assume that orthologous genes are functionally similar.
Orthology inference is an invaluable tool in transfering biological meaning from one biological sequence with a validated function, to another, with no such validation and inherently different from "mere" homology.

The _Azolla_ lab has particular interest in such a tool.
We are not only involved in the genomics of a novel crop but more specifically of the very first genome of a fern ever sequenced.
No gene's function in Azolla was ever verified and we have no close relative to compare _Azolla_ sequences with.
Hence, homology and comparative genomics are essential in assigning meaning to the genome sequences we have acquired in @Li2018.
While often, gene function is attributed on mere homology, there are cases where several homologs are present in a genome.
We used gene trees to attribute these homologs to any one orthologous group via gene trees.
One examples was included in this thesis before in chapter \ref{it_takes_two} in +@fig:fig6_8.
A second example can be found in the supplemental material of the same publication.

There are several ways to infer trees from sequences, here I categorise them in three groups.
These methods and other key concepts in modern day phylogenetics are excelently reviewed in @kapli2020.
Almost all methods involve alligning sequences, often amino acid sequences, to each other.
The first group is methodically the simplest: Neighbour Joining (NJ).
NJ methods create a distance matrix from this allignment, and a tree from this distance matrix.
NJ methods are akin to hierarchical clustering methods and incredibly efficient.
The method is however not very robust for sequences that are more divergent from the majority of the data or when sequences are distantly related.
Consequently, NJ is rarely used and not considered a state-of-the-art method in most use-cases.
The second group of methods concerns Maximum Likelihood tree inference (ML).
These methods do not infer distance matrices, but infer trees directly from the sequence allignment and then calculate the likelihood of this tree (a hypothetical evolution) given the alignment (the data).
This likeihood is calculated given a certian model of evolution `find good review for this`.
Next, the methods searches through a virtual space of posible trees (treespace), and returns the tree with the best likelihood.
A third group builds forth on the advances of ML tree inference but within a Baysian framework of statistics.
I consider Baysian approaches too advanced for the audience that this workflow is aimed at, hence I won't discuss them or include them in the workflow.
In the workflow presented here, I use ML tree inference with IQTree [@Nguyen2015].
One of the main advantages of IQtree is that it includes software to find an appropriate model of evolution given an input allignment.

### Availability
This remainder of this chapter shortly summarises data and software tools used for the workflow, alternative tools and their limitations, and my design considerations in making my own workflow.
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
Even without collaboration, the back-up functionality is valuable.
Uploading to a closed GitHub repository keeps the unpublished work private.
At time of publication, a GitHub repository can be made public and linked to Zenodo.
Zenodo then archives the work and provides a citableDOI reference. (+@fig:fig7_git_zenodo B)

### Data
Phylogenetics is in the first place a comparative exercise, hence to gain insight in the evolution of any protein sequence, one must compare it to related sequences.
As plant biologists studying ferns, we are challenged by a lack of non-seed plant genomes available to us.
Luckily, the recent 1kP project [@Leebens-Mack2019] provides solution by collecting the genomes and assembled transcriptomes of 1000 plant species.
The 1kP effort fills a gap in reference databases, providing protein coding sequences for a large number of seed-free plants.
As fern researchers, we make intensive use of the 1kP project and we use it in the examples included here._

The 1kP project [@Leebens-Mack2019] published assembled transcriptomes for over 1000 plant species (+@tbl:tbl7_1kP_sample_counts) and included 26 species with sequenced genomes in their dataset as well.
Genome assembly based data can be assumed to be complete.
In phylogenetics, this is relevant for all paralogs that a species may contain will be present in the dataset.
For transcriptome assembled data, this assumption does not hold.
Paralogs may not be simultaneously expressed and therefore absent from the dataset.
Alternativelly, paralogs may be assembled as a single sequence.
Absence of paralogs in the dataset and the phylogeny infered thereoff is relevant for it may cause wrong inference of speciation and duplication nodes.
Consequently, orthlogy inference may be faulty as well.
To somewhat mitigate this shortcomming, we chose to include a substantial amount of species in our phylogenies.
We argue that if one species does not express both paralogs simultaneously, then maybe another will.
To make our trees and the orthology and paralogy patterns easier interpretable, we colour code six main clades of the Viridiplantae in our trees.
These are the Algae, Bryophytes, Lycophytes, Monilophytes, Gymnosperms and Angiosperms (+@tbl:tbl7_1kP_sample_counts).

| Clade        | Lineage                        | Sample count |
| ------------ | ----------------       	      |    ---       |
| Algae        | Chloranthales                 	|            2 |
| Algae        | Chromista (Algae)             	|           35 |
| Algae        | Glaucophyta (Algae)           	|            5 |
| Algae        | Green Algae                   	|          171 |
| Algae        | Red Algae                     	|           28 |
| Bryophytes   | Hornworts                     	|           14 |
| Bryophytes   | Liverworts                    	|           29 |
| Lycophytes   | Lycophytes                    	|           22 |
| Bryophytes   | Mosses                        	|           41 |
| Monilophytes | Eusporangiate Monilophytes    	|           12 |
| Monilophytes | Leptosporangiate Monilophytes 	|           68 |
| Gymnosperms  | Conifers                      	|           76 |
| Gymnosperms  | Cycadales                     	|            4 |
| Gymnosperms  | Ginkgoales                    	|            1 |
| Gymnosperms  | Gnetales                      	|            3 |
| Angiosperms  | Basal Eudicots                	|           58 |
| Angiosperms  | Basalmost angiosperms         	|            8 |
| Angiosperms  | Core Eudicots                 	|          119 |
| Angiosperms  | Core Eudicots/Asterids        	|          248 |
| Angiosperms  | Core Eudicots/Rosids          	|          257 |
| Angiosperms  | Magnoliids                    	|           27 |
| Angiosperms  | Monocots                      	|           66 |
| Angiosperms  | Monocots/Commelinids          	|           45 |
|              |                        	      |              |
|              | **Grand Total**               	|     **1339** |

Table: Transcriptome sample counts per clade of the Viridiplantae. {#tbl:tbl7_1kP_sample_counts}

This vast dataset of plant coding sequences, or any set of sequences, must still be searched for homologous sequences.
One would typically use blast for these homologs in either the 1kP data, or in NCBI blast, or both.
However, the work done by the 1kP authors already includes big orthogroups made with Orthofinder [@Emms2019].
These orthogroups contain whole gene families and perhaps counter-intuitively includes paralogous groups within that gene family.
We may use these orthogroups as starting points for our own phylogentic inferences.
These orthogroups are more reliable than blast searches and hence provide an improved starting point.
Unfortunately, the orthogroups created by the 1kP project are not publicly available anymore.
They are not included in the data-uploads to the usual repositories but instead hosted at a separate link.
The original link ([jlmwiki.plantbio.uga.edu/onekp/v2/](http://jlmwiki.plantbio.uga.edu/onekp/v2/)) at the Leebens-Mack lab is no longer available.
The authors were made aware of this early 2022 but as of yet there is no alternative way to access this data.

## Results

### Existing tools
Existing tools that house a complete workflow from gathering sequences up to infering a ML tree are rare.
The one tool that is best known for this purpose is MEGA X [@Kumar2016].
MEGA X is often found in literature and has substantially contributed to making phylogenic tools available to the broad public.
The software is especially attractive to novice users for it runs on Windows, has a graphical user interface, and includes all steps from beginning to end.
We find it especially usefull for smaller phylogenies, no more than 50 sequences.
Our main critisism on the MEGA software is that inferior NJ based methods are presented as equally good options to ML methods and the exact method in which MEGA X implements the ML methodology is unknown to the public.
We observe in literature that novice users often employ the fast but inferior NJ method where reasonably an ML tree should be have been created.
I did a short inquiry into citations of @Kumar2016 sorted by date in google scholar so google algorithms do not play into sampling bias.
Out of the 50 most recent citations, 40 publications were publicly accessible and contained a phylogeny.
Of these, 17 contained a ML tree, 22 a NJ tree, and one a maximum parsimony tree .
A secondary objection to the use of propriatary software, is the use of propriatary file formats where the field typically employs standardized file formats.
Using the state-of-the-art tools in the Linux CML is a steep learning curve, explaining and validating the niche of a tool like MEGA X.
This workflow aims to improve on MEGA X shortcommings by reducing the steep learning curve to use the Linux CML tools used by experts.
Doing so in a JuPy notebook makes it easy to document and journal while doing the analysis.
Finally, it eases to transition to bigger datasets that GUI desktop software often is not tailored to.

### This workflow
The workflow consists of 6 Major steps.
The software choices are tailored to strike a balance between relavitvelly big datasets and userfriendlyness.
These steps are:

1. Acquiring data and optional subsetting
  - Via blast or 1kP
  - subsetting
  - guide sequences.
2. Aligning sequences (with MAFFT)
  - mafft
3. Alignment trimming
  - trimAL
4. Fasttree building
  - IQTree "fast" or via fasttree
5. Tree building
  - IQTree with model fitting
6. Tree visualisation with iToL

`Shoudl this be a figure`

#### 1 Acquiring data
In the use by the _Azolla_ lab, we have employed the 1kP dataset intensivelly, however we also examplify blast searchers as an input.

### Web based alternatives

IQTree & PHYML

### Examples

#### LAR

![](source/figures/fig7_LAR_phylogeny.pdf){#fig:fig7_LAR_phylogeny}


#### 2OGD

![](source/figures/fig7_2OGD_phylogeny_small.pdf){#fig:fig7_2OGD_phylogeny_small width=50%}

![](source/figures/fig7_2OGD_phylogeny.pdf){#fig:fig7_2OGD_phylogeny}

#### MYB & MIKc
prank indel-realignment

![](source/figures/fig7_MIKCc_phylogeny.pdf){#fig:fig7_MIKCc_phylogeny}

## discussion

phylogenomics

SNPhylo, trees on snips of whole genomes
