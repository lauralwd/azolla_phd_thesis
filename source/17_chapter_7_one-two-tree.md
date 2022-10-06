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
\resetlinenumber
\linenumbers

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

## Workflow
The workflow consists of 6 Major steps.
The software choices are tailored to strike a balance between relavitvelly big datasets and userfriendlyness.
These steps are:

1. Acquiring data and optional subsetting
    - Via blast or 1kP
    - optional subsetting of data
    - Adding guide sequences; sequences who have their function verified.
2. Aligning sequences
    - mafft
3. Alignment trimming
    - trimAL
4. Fasttree building
    - IQTree "fast" or via fasttree
5. Tree building
    - IQTree with model fitting
6. Tree visualisation with iToL

`Should this be a figure`

For each of these step, I will highlight some design choices and indicate if these can be done online as well as in the workflow.

### Acquiring data
The workflow examplifies two specific datasources.
In the use by the _Azolla_ lab, we have employed the 1kP dataset intensivelly, however we also examplify blast searchers as an input.
For phylogenies spanning all land plants -the Viridiplantae- we exclusively use amino acid sequences.
The 1kP orthogroup extractor specifically is a great resource to acquire many related sequences of seed and seed-free plants alike.
In the workflow, I highly the importance of selecting all sequences of a species and provide quick instructions on how to use ncbi blastp to search in specific species.
Within the 1kP project, there is no web interface to easily select per species.
Therefore I provide some pre-written BASH code to subset 1kP orthogroup files per species.

To attribute functional annotation to any clade or orthologous genes, we use what we term 'guide sequences.'
These are sequences that we manually select from literature for their verified functionality.
Ideally, these guide sequences represent multiple of the major landplant clades, but in reality they are mostly found in angiosperms.

Finally, we also add sequences of inquiry, those that we'd like to place in context of evolution of landplants (i.e. the 1kP data) and assign some function to via guide sequences.

Acquiring data from NCBI blastP can be done online completely, subsetting orthorgroups of the 1kP has no online alternatives.

### Aligning the dataset
Now that we have a collection of homologous sequences, the next step is to align these to each other.
Two of the famous tools to this end are ClustalOMAGA (previously known as clustalW) and MUSCLE [@Sievers2014; @Edgar2004].
Both tools however, are single-threaded; meaning they can use only one CPU cores where modern computers often have several.
They are outperformed in most cases by more modern tools, espicially for big or gappy datasets [@Pais2014].
The transcriptome data of the 1kP occasionally contains mis-assemblies that cause such big gaps in an MSA.
Given the size of the datasets we work with in the _Azolla_ lab and the size of the 1kP orthogroups we have worked with, I chose to use MAFFT [@Katoh2013].
MAFFT is a multiple sequence alligner that can make use of additional CPU cores, and can deal well with big gaps in allignments.
In my limited testing, MAFFT was easier and more reliable to run than another modern candidate: T-coffee [@Notredame2000].

MAFFT has multiple configurations with each their own use-fase.
For big datasets, the algorithm defaults to fast progressive alignment methods.
Automatic choice of algorithm is based on the count of sequences only, and not on biological information.
Hence I recommend to specifically choose the slower iterative refining methods based on the nature of the gene.
Naturally, it is good practice to try multiple methods and compare the alignments by eye to see how they perform.
The iterative methods require considerable more compute time compared to the fast methods.
I consider this investment justified for the quality of allingment is determining for the quality of the phylogeny.
The MAFFT manual and online tool explains my 3 favourite presents that we have used succesfully in the _Azolla_ lab.

* E-INS-i: For sequences with multiple conserved domains and long gaps.
* L-INS-i: For sequences with one conserved domain and longs gaps.
* G-INS-i: For sequences with global homology.

When comparing alingment configurations to each other visualy, we aim to maximise for structure or patterns (+@fig:fig7_align_examples).
The various fast or slow configurations produce overall quite similar results at first sight.
Espicially the most conserved regions are near identical for each algorithm
(+@fig:fig7_align_examples A, B, C).
The regions with barely any sequence content will be filtered out in a later step, this is typically quite a proportion of an alignment with many sequences (+@fig:fig7_align_examples D).
Hence, were 'eyeballing' those columns with substantial sequence content that are not extremely conserved and see how they align.
Ideally, by optimisting this step, some extra phylogenetic signal might be gained from these medium-conserved regions.
At worst, we might erroneously align regions that are not homologous to each other.

In the example alingments in +@fig:fig7_align_examples, the 'auto' alingment was discarded first due to lack of structure in gappy regions.
The linsi and einsi alingments were assessed as near equal in quality; we proceded with the einsi version.
Regardless, both alignments performed insufficiently in the gap regions.
We estimated by studying various versions of similar MIKCc alignments, that some structure may be hidden in those regions and was not uncovered by the MAFFT alingment.

For alignments of reasonable size, no more than a couple of hundreds of sequences, these medium-conserved gappy INDEL regions may be re-aligned with a dedicated INDEL realigner such as prank [@Loytynoja2014].
In our experience, this can help in reducing noise from such regions and provide some extra signal to solve relations between specific groups.
This does not work for alignments with several hundreds to thousands of sequences.
When succesful, INDEL realignment can bring structure into medium-conserved regions for correct phylogenetic inference.
In the _Azolla_ lab we used this proces for optimising a MIKCc MSA (+@fig:fig7_align_trimprank A & B).
A MAFFT alignment that was trimmed for a minimum of 10% sequence content per column shows clear structure in conserved domains (+@fig:fig7_align_trimprank A).
However medium-conserved regions contain little structure and non-homologous residues may be aligned to each other.
Realignment of INDELs via prank was supported by an ML guide tree of a more strict trim of the same alignment.
The result was trimmed for 10% collumn content as well and shows clear structure in the medium-conserved regions.
After realingment, the region contains multiple INDELS unqiue to specific groups of sequences(+@fig:fig7_align_trimprank B).
Before realignment these regions seemed forced together and would have diluted the phylogenetic signal.
All MSAs and png snapshots of the MIKCc phylogeny work of the _Azolla_ lab can be found in aGitHub repository..
These file can be found at [github.com/lauralwd/MIKC_tree/tree/master/data/alignments_raw](https://github.com/lauralwd/MIKC_tree/tree/master/data/alignments_raw).

MAFFT also has an online version that is very user friendly: [mafft.cbrc.jp/alignment/server/](https://mafft.cbrc.jp/alignment/server/) [@Katoh2019].
It is however limited in its performace when using the three configurations mentioned above.
For big datasets, it pays off to run the alignment locally.

<!---
make jalview alingment svgs smaller by removing all text fields:

expanding the svg to a long format:
xmlstarlet ed -d text jalview.svg > intermediate.svg

cat intermediate.svg | grep -v '<g transform' | grep -v 'sans-serif' | grep -v 'Arial' | grep -v '</g>' > small_jallview.svg


Actually, just do this in the jalview format and view menu's that makes life a lot easier!
--->

![Multiple Sequence Alignments by MAFFT. A dataset of MIKCc sequences from the 1kP project was subsetted and then alinged with mafft auto (A) linsi (B) and einsi (C). Panels A, B and C depict sections of the original MSA, panel D depicts the full einsi alingment. MSAs were visualised with jalview and coloured via the clustal colouring scheme. Only the colouring scheme is retained in this figure. The four bar graps underneath each MSA depict Conservation, Quality, Consensus and Occupancy from top to bottom.](source/figures/fig7_align_examples.pdf){#fig:fig7_align_examples}

### Trimming
Big MSAs, especially those based on transcriptome data, are not optimal for phylogeny inference.
Phylogeny inference is driven by synapomorphies, shared diferences between a majority of sequences.
The inference is hampered whenever a major fraction of sequences contains no content at all (gaps), or when a conserved region is missing from a particular sequence.
Therefore, we trim the MSA to remove data that is not aligned well, and may disrupt the evolutionary signal we attempt to uncover.

The simplest and perhaps most effective trimming method is removing columns -removing shared amino acid residues- in the MSA that contain little sequence content.
These regions often represent INDELs in specific taxa or misassemblies.
Regardless the INDELs contain little to no phylogenetic informatice information.
Gap regions are easily identified in a visualised MSA as a blocky pattern (+@fig:fig7_align_examples)
Collumn filtering is easy and can be done in visually in tools like jalview, or even directly when aligning in the online version of MAFFT [@Katoh2019].

A second filter concerns that of rows, of sequences in the MSA, that allign poorly to the bulk of sequences.
When a sequence contains many fragments not shared by the majority of sequences, this creates gaps in the MSA that are filtered out in the column filter.
Alternativelly, a sequence may mis substantial parts of conserved domains are absent.
Such a fragmented sequence misses important synapomorphy information to correctly place it in a phylogeny.
A sequence fragment can be seen in an MSA visualisation as light horizontal banding (+@fig:fig7_align_examples; +@fig: fig7_align_trimprank C).
Regardless the reason, it may be wise to filter these sequences out conservatively.
When removing entire sequences from a dataset, one risks to also remove essential information with which speciation and duplication nodes are distinghuised.
This is another reason we often make relativelly large trees in the _Azolla_ lab when we maken use of the 1kP data, by inlcuding more species we hope to add a certain robustness to this risk.

![Optimisation of MAFFT MSAs. An overview of a MAFFT MSA of the MIKCc ortogroup subset trimmed for column content (A) versus an MAFFT MSA of the same data that was realigned with prank and then trimmed for column content. In the bottom two pannels two MSA overviews are displayed of a subset of 2OGD enzyme sequences from transcriptome data. One alignment was made with MAFFT and then trimmed for column content only (C) and the other was trimmed for both column and sequence content (D). MSAs were visualised with jalview and coloured via the clustal colouring scheme. Only the colouring scheme is retained in panels C & D. The four bar graps underneath panels A & B depict Conservation, Quality, Consensus and Occupancy from top to bottom.](source/figures/fig7_align_trimprank.pdf){#fig:fig7_align_trimprank}

The tool of choice to tackle both filters at once, is trimAL [@Capella-Gutierrez2009].
TrimAL allows to set a gap threshold, as well as parameters to filter out sequences.
There is no single rule for good thresholds, we encourage experimentation and re-evaluation to find a good setting for any particular dataset.
As a gap threshold we typically start with a value of 40% and explore further from there on out.
Filtering sequences is less straight forward.
This works by setting a threshold for determining conserved amino acid residues first.
The second threshold determines how much of these conserved sites must be present in any sequence of the dataset.
When done well, the major conserved regions are present in the vast majority of sequences and the horizontal bandig is absent (+fig:fig7_align_trimprank C vs. +fig:fig7_align_trimprank D).
In the section on 2 OGD phylogeny, we demonstrate a visual exploration to sumarise the behaviour of these parameters for the alignments shown in pannels C & D of +fig:fig7_align_trimprank.

To our knowledge there are no online tools that achieve a similar finesse of filtering MSAs as trimAL does.
When restricted to online tools, the column occupancy filter in the online version of MAFFT is an obvious and convenient choice.

### Fast phylogeny inference
Full phylogeny inference and non-parametric bootstrapping can take a considerable amount of time.
Therefore, it is wise to explore the likely outcome tree with a fast tree inference program that does not perform bootstrapping.
This allows for a preliminary view into the final result and observe potential mistakes, remove or add sequences of interest.
Conveniently, the calculation time for a final tree may then be used to test final visualisation.
The field standard towards fast preliminary tree inference could be considered to be be FastTree.
In our workflow however, we use IQTree's 'fast' setting for it produces an output file structure nearly identical to the final tree inference.
The FastTree software is included in the conda environment and can be used as an alternative.

To our knowledge, no online fast tree inference algorithm is available.
However, a regular tree inference without bootstrapping would be a reasonably fast alternative when restricted to online tools.
Regular tree inference is described in the next section.

### Full phylogeny inference
In this workflow we use IQTree for modelfitting, phylogenetic tree inference, and calculating bootstrap support.
These are three distinct steps, especially the first often is not included in phylogeny software.
The details of fitting a model of evolution to an alignment are beyong the scope of this manuscript.
The basics include fitting a substitution matrix of amino acid exchange rates of nucleotide exchange rates to those observed in an alignment.
Additionally, more advanced paramters are assessed such as heterogeneity of the speed in which traits evolve over time amongst the entries in the MSA: Rate heterogeneity.
For the audience of this workflow, we recommend to use IQtree's build in extended model fitter by using the option `-m MFP` short for Model Finder and Phylogeny.

For phylogeny inference, we supply a ML option only for we see very few good arguments to resort to NJ or MP methods instead.
A major propperty of interpreting phylogenies, is support values.
These support values, often called boostrap values, can be determined in several ways.
Next we'll discuss three support estimation methods.
Firstly, the slow and simple but time-tested method of Felsensteins bootstrap, or 'regular bootstraps'.
Second, we'll discuss an uqualy slow alternative that is more suited to bigger trees: transfer bootstrap [@Lemoine2018].
These fist two methods are slow, but behave reasonably linear and are easily interpretable.
They are often indicated as non-parametric methods.
Thirdly, we'll discuss faster parametric options such as IQTree's UltraFastBootstrap.
These methods behave non-linearly and are harder to interpret but find a use case in estimating support of very big trees or of preliminary small trees.

Support estimation by bootstrapping is an important step in assessing reliability of any phylogeny.
After the main phylogeny is established, one can choose to bootstrap it for $b$ times, often $b=100$.
Bootstrapping in phylogeny is a process in which a fraction MSA columns is removed and replaced by a random subset of the remaining fraction.
The phylogeny inference is then repeated.
After repeating this proces for $b$ times, the nodes in the final tree get a support score based on the similarity of these nodes in the bootstrapped repetitions.
The most used and most conservative approach is felsensteins bootstrap.
This approach is a binary one.
It counts those repititions in which the bootstrap node is identical to the reference node: $i$.
In other words, the nodes for which the devision of leaves left and right of that node is identical regardles their exact topoloy beyond that node.
The support value is a simple percentage of those nodes over the total amount of bootstraps done: $(\frac{i}{b}) 100\%$.
This method is easily interpretable, and standardised in the field.

Felsensteins BootStrap (FBS) does have drawbacks, especially for bigger trees.
In the _Azolla_ lab we experienced that nodes deep in a big phylogeny, those nodes that typically represent ancestral states, receive very low support values.
Yet, when repeating the tree inferences with modified datasets, these nodes appeared highly robust.
If a single sequence its placement is highly variable -a rogue taxon- it will have huge impact on the support values of deep nodes despite the placement of the majority of taxa being highly reliable.
We observe that for big trees, FBS is often uninformative for deeper nodes.

TransferBootStraps (TBS) present an alternative support criterion that was designed to circumvent this exact issue found in bigger phylogenies [@Lemoine2018].
When calculating TBS for any node, it takes a non-binary approach.
A node's bootstrap isn't regarded as either good $i=1$ or false $i=0$ as in FBS.
Instead, a continous citerion is used: distance metric $\phi$.
It is based on the minimum amount of leaves that must be transfered from one side of a node to the other for a bootstrap tree to represent the main tree.
Finally this metric is corrected for any proportion difference $p$ between the left and right side of that node.
The method is further detailed in @Lemoine2018.

$(TBS= 1- \frac{\phi}{p-1})$

We have used TBS with success and in the _Azolla_ lab and recommend its usage in big phylogenies; those of several hundreds of sequences.
TBS values of shallow nodes typically represent those of FBS, and TBS values of deep nodes typically read as if they are shallow nodes.
We found that TBS assigns more meaningful support values to deep nodes.
The method is however not wide spread in the field, and its usage should be clearly stated for correct interpretation of phylogny support values.

Both FBS and TBS are slow methods for they require to redo a full phylogenetic inference $b$ times.
Modern phylogeny inference tools often have faster parametric methods that calculate support.
IQTree has such a method called UltraFastBootstrap (UFB) [@Hoang2018], which the authors recommend to pair with the Shimodaira-Hasegawa aproximate Likelihood Ratio Test (SH-aLRT) [@Guindon2010].
the IQTree manual suggests to trust any node if it has over 95% UFB and over 80% SH-aLRT confidence.

We use UFB for preliminary trees, or those that are too big to produce FBS or TBS support within weeks of time.
Confusingly, the values that UFB produces are not to be compared with those of TBS and FBS.
Per the IQTree manual, a UFB support of 95% corresponds to a 95% probability that this node is a "true node".
One might be inclined to think a 90% UFB support is also quite believable.
In our use however, we have observed 90% UFB nodes that became 20%FBS nodes once non-parametric bootstrapping was done.

Support estimation comes in phylogeny comes in many shapes and forms with their own pro's and cons.
We recommend to use non-parametric methods such as FBS and TBS in final results for ease of interpretation and reliability.
We resort to UFB and SH-aLRT for very big phylogenies only.
Regardless the method, we emphasise the importance of clearly indicating the support estimation method used with any phylogeny.

Online phylogeny inference is freely available and makes the methods accessible to all.
IQtree can be used online although with limitations ([iqtree.cibiv.univie.ac.at](http://iqtree.cibiv.univie.ac.at/)) [@Trifinopoulos2016].
Additionally, all these steps can also be done in PHYML, an alternative tool with the same use case, on [atgc-montpellier.fr/phyml/](http://www.atgc-montpellier.fr/phyml/).

### Visualisation

For visualisation of the phylogeny, we recommend working in iToL [@Letunic2019] [itol.embl.de](https://itol.embl.de/).
Like the JuPyter notebook, iToL works in an internet browser.
Unfortunately the free version of iToL does not allow to save the layout of a phylogeny anymore, but a paid version allows you to do so.
When uploading a treefile into iToL, we take several steps to turn it into a final figure.
First is rooting the tree, when working with land-plants, we typically root an algae sequences.
Second is colouring the major clades as in +@tbl:tbl7_1kP_sample_counts: clade, and adjusting any text size and colour.
We recommend doing so by using annotation files rather than doing it manually.
These annotation files can also be shared in a Git repository for reproducibility.
Optionally, more data can be added onto the tree, such as the MSA, RNA-seq data, certain groupings, protein domains, etcetera.
We discuss these options further in the Usecases section.

## Usecases
In this section, I discuss several use cases of this phylogeny workflow in the _Azolla_ lab.
Firstly, that of several leucoanthocyanidin reductase (LAR) homologs found in _Azolla_.
This was actually the inspiration for creating this workflow.
Second a 2-OGD phylogeny inference with several _Azolla_ sequences added.
The 2-OGD family is one of the biggest enzyme families in land plants.
We wanted to study how ferns have developed differently from land plants, and infer the functionality of a specific fern 2-OGD gene that was differentially expressed in an RNA-seq experiment.
Thirdly, a MIKCc phylogeny.
With this phylogeny of MIKCc transcription factors we attempted to elucidate the evolution of fern sexual reproduction in context of all of land plants.

### LAR

![](source/figures/fig7_LAR_phylogeny.pdf){#fig:fig7_LAR_phylogeny}

### 2OGD

![](source/figures/fig7_2OGD_phylogeny_small.pdf){#fig:fig7_2OGD_phylogeny_small width=50%}

![](source/figures/fig7_2OGD_phylogeny.pdf){#fig:fig7_2OGD_phylogeny}

### MYB & MIKc
prank indel-realignment

![](source/figures/fig7_MIKCc_phylogeny.pdf){#fig:fig7_MIKCc_phylogeny}

## discussion

phylogenomics

SNPhylo, trees on snips of whole genomes

\nolinenumbers
