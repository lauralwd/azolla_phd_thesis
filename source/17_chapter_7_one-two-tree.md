\pagestyle{chapter}
\singlespacing
\setlength{\parindent}{0.0in}
\addthumb{Chapter \thechapter}{\Large{\thechapter}}{white}{gray}

\chapter{One two, tree! A workflow for creating state-of-the-art phylogenies designed for reproducibility with JuPyter, conda and git.}
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

<!-- have a mini table of contents -->
\minitoc

\section*{Abstract}

This chapter presents a reproducible workflow for constructing phylogenetic trees using open-source tools within a JuPyter notebook environment.
Aimed at novices, the workflow includes command-line-based steps for data acquisition, sequence alignment, multiple sequence alignment (MSA) trimming, tree inference, and visualization.
By integrating best practices and state-of-the-art software, the workflow addresses challenges in phylogenetic analysis, such as managing large datasets whilst ensuring reproducibility.
Three case studies from the Azolla lab demonstrate its application, highlighting phylogenetic inference to address evolutionary and functional questions in non-model plant species.
This workflow offers an accessible yet rigorous approach to phylogenetic research, promoting transparency and reproducibility in comparative genomics.

\newpage

<!--
General todo stuff:
- go over all comments.
- nice code highlighting for bash, yaml, etc blocks?
- Spellcheck
- Make Orthology figure
- Make workflow figures
- Rens
- Erbil
- Henriette
- Sjef
- Run Orthofinder anew on 1kP data...
-->

# Introduction

Life Science has entered the big-data age; we have an unprecedented detailed view on the storage and processing of information within biological systems.
This view is possible due to the ever decreasing prices of sequencing of DNA, RNA and protein.
Consequently, biologist are challenged less with acquiring data and more with its organising, processing and interpreting.
Phylogenetics is one answer to that challenge.
Phylogenetics organises sequences by their inferred evolution: in phylogenetic trees.
After all, how does anything in biology make sense except in the light of evolution.

This chapter accompanies a practical workflow to infer phylogenetic trees.
It is an interactive document on GitHub which I made and used during my PhD and may be used and improved by others as well.
This work does not try to summarise the background needed to properly read trees and collect data as @VanHooff2019 does, nor does it summarise recent technological advantages in the field as @Kapli2020.
Hence, consider these two works as essential reading before bringing this workflow into practice.
I do include a basic introduction of phylogeny: the bare minimum to understand the design choices made and use cases exemplified.

With my phylogeny workflow, I aim to provide a practical guide aiding novice users in making phylogenies with state-of-the-art tools.
In this document I summarise the workflow, the choices I made in designing it, and examples of its implementation.
The workflow itself, may be considered similar to @Hall2013, who presents a step by step guide for inferring phylogeny in MEGA5.
This work differentiates itself by using command line (CML) tools only, emphasising documentation of intermediate files, and using only open source algorithms.
By using CML tools , I aim to circumvent limitations of other existing all-in-one or web based solutions.
This presents a steeper learning curve for a novice user, but increased freedom to implement any other tool of choice and to log and share analyses with peers via Git or other means.
The workflow is openly available online and I have documented my use of it on GitHub and Zenodo, as summarised  here in the 'Use cases' section.
Via this route I aim to inspire other researchers to also make their analyses more reproducible and share their code towards more reproducible research.

## Key concepts in Phylogeny

In principle, two types of phylogenetic trees exist: gene trees, and species trees.
These will remain hypothetical for one can not observe how proteins or species have evolved in the past.
Gene trees depict the hypothetical pattern in which several sequences are related to each other.
If a single organism contains two copies of a gene, the organism's name will appear twice in the tree.
Hence the tree nodes, the bifurcations, may represent speciations as well as gene duplications.
Species trees depict speciations only.
When novices think of phylogenetic trees, they often think of species trees.
However, in practice, researchers often make gene trees instead.
Gene trees may seem inconsistent with with species trees due to gene duplications or losses.
Occasionally, horizontal gene transfer might even occur.
Gene trees can be reconciled into species trees to infer such events.
The relation between gene an species trees as well as how to read them is excellently explained in @VanHooff2019.

`dummy figure species vs gene trees and orthology and paralogy,`

Gene trees allow us to answer basic but important questions in comparative genomics.
When presented with many gene sequences that are similar (analogs), we should only work with sequences that share a common ancestor (homologs).
We may use gene trees to see if these homologs are a result of a gene duplication (paralogs) or a speciation (orthologs).
Orthology is a key concept for reading phylogenetic trees and in detail explained in @VanHooff2019.
If two sequences were separated because of speciation, we then assume they are the only copies both species their genomes.
Consequently, we conclude that selection pressure has occurred on this particular gene in both separate genomes.
Hence, when reading a phylogenetic gene tree, we often assume that orthologous genes are functionally similar.
Orthology inference is an invaluable tool in transferring biological meaning from one biological sequence with a validated function, to another, with no such validation.
It is inherently different from "mere" homology or even analogy.

The _Azolla_ lab has particular interest in such a tool.
We are not only involved in the genomics of a novel crop but more specifically of the very first genome of a fern ever sequenced.
Until recently, no gene its function in Azolla was ever verified and we have no close relative to compare _Azolla_ sequences with.
Hence, homology and comparative genomics are invaluable in assigning meaning to the genome sequences we acquired in @Li2018 and @gungor2024.
While often, gene function is attributed on mere homology, there are cases where several homologs are present in a genome.
We used gene trees to attribute these homologs to any one orthologous group.
One examples was included in this thesis before in chapter \ref{it_takes_two} in @fig:fig6_8.
A second example can be found in the supplemental material of the same publication and in figure @fig:fig7_MIKCc_phylogeny.

There are several ways to infer trees from sequences, here I categorise them in three groups.
These methods and other key concepts in modern day phylogenetics are excellently reviewed in @Kapli2020.
Almost all methods involve aligning sequences ---often amino acid sequences--- to each other.
These alignments of multiple sequences are called Multiple Sequence Alignments or MSAs.
All methods then use synapomorphies in these MSAs ---shared differences--- to group sequences together.
The first group of methods is the simplest: Neighbour Joining (NJ).
NJ methods create a distance matrix from this MSA, and a tree from this distance matrix.
NJ methods are akin to hierarchical clustering methods and incredibly efficient.
The method is however not very robust for sequences that are more divergent from the majority of the data or when sequences are distantly related.
Consequently, NJ is rarely used and not considered a state-of-the-art method in most use-cases.
The second group of methods concerns Maximum Likelihood tree inference (ML).
These methods do not infer distance matrices, but infer trees directly from the MSA.
Then it calculates the likelihood of this tree (a hypothesis) given the MSA (the data).
This likelihood is calculated given a certain model of evolution [@Sullivan2005; @Felsenstein2004].
Next, ML methods search through a virtual space of possible trees (tree space), and returns the tree with the best likelihood.
A third group builds forth on the advances of ML tree inference but within a Bayesian framework of statistics.
I consider Bayesian approaches too advanced for the audience that this workflow is aimed at, hence I won't discuss them or include them in the workflow.
In the workflow presented here, I use ML tree inference with IQTree [@Nguyen2015].
One of the main advantages of IQtree is that it includes software to find an appropriate model of evolution given an input MSA [@Kalyaanamoorthy2017].

## Availability

This remainder of this chapter summarises relevant data and software, my design considerations in making this workflow, and finally three use cases of the _Azolla_ lab.
This workflow includes gathering data from the 1kP project [@Leebens-Mack2019], MSA of protein sequences, trimming of this MSA and tree inference via frequentist methods.
Additionally, several examples of the workflow in practice are included to demonstrate its application in tackling biological questions of the _Azolla_ lab.
This workflow is openly available and usable under a Creative Commons License at [GitHub.com/lauralwd/lauras_phylogeny_wf](https://github.com/lauralwd/lauras_phylogeny_wf)

# Methods

The state-of-the-art tools required for phylogenetics are often designed for Linux systems.
Using BASH scripts ---BASH being the Linux-native programming language--- can be a steep learning curve for novice users.
Therefore I use JuPyter notebooks [@Ragan-Kelley2014] to supply the user of the workflow with written instructions and pre-written BASH code.
A JuPyter notebook is an interactive document in which the user can run said code, as well as journal their decisions and observations

<!-- Consider shortening the explanation on conda and providing a visual reference (e.g., a brief command flow diagram for installing dependencies) to enhance readability. -->

Software installation on Linux can be challenging, especially if certain versions of software may be incompatible.
Therefore I make use of the conda or miniconda frameworks ([conda.io](www.conda.io)) to supply any user with a ready made software environment that has all the required tools available.
This environment also contains the software required to run the JuPyter notebooks.
Conda environments contain a list of all the software and the specific versions of that software.
New users can install all required software this way, and readers of their work may reproduce any analysis with the exact same software versions.
The recommended route is to install git and miniconda3 following the miniconda3 instructions (<https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html>) on your system.
For Linux and MacOS systems, this runs natively.
For Windows systems, we have had good experience using the Windows Sublayer for Linux (WSL).
In our experience, these three systems all run miniconda3 without any issue.
When Git and miniconda3 are installed on your system, the required software may be installed via the following BASH commands:

```shell
git clone https://github.com/lauralwd/lauras_phylogeny_wf.git
cd lauras_phylogeny_wf
conda env create -f conda_environment.yaml
```

The virtual environment that contains the installed software can then be activated via

```shell
conda activate phylogenetics
```

A small snippet of the `conda_environment.yaml` file is included below.
It details the relevant software and exact version and build so any future researcher may reproduce results exactly.

```yaml
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

Finally, a user may make use of Git versioning software to document progress of their workflow, and possibly maintain multiple versions thereof.
Git can store and tracks changes in the JuPyter notebooks, some ---but not all--- data files, and the conda environment specification.
Whenever any file is changed; i.e. an analysis step is done, this change can be appended to the Git history (@fig:fig7_git_zenodo A).
When done well, this 'commit' to the Git history contains a very short written explanation of the added history.
This might be a short line like `added raw data from 1kP project`, or `trimmed aligned fasta file and document parameter choice`.

![Online documentation of the phylogeny workflow on R2R3 MYB phylogeny in chapter \ref{it_takes_two} figure @fig:fig6_8. The Git history shown on GitHub (A) details steps taken in finalising the phylogeny and the resulting figure. The finalised Git repository and all important files are archived on zenodo (B) with a DOI ([https://doi.org/10.5281/zenodo.3959056](https://doi.org/10.5281/zenodo.3959056)) ](source/figures/fig7_git_zenodo.pdf){#fig:fig7_git_zenodo short-caption="Online phylogeny workflow documentation"}

<!-- 	3.	Git Workflow Discussion:
	•	Splitting this into smaller sections might improve clarity:
	•		1.	Explaining Git and GitHub functionality briefly.
	•		2.	Detailing the benefits for version control and reproducibility in phylogenetics.
-->

A Git repository containing the workflow may be uploaded online to services like GitHub or GitLab or a self-hosted Git server.
This does not only provide instant back-ups of the workflow but also facilitates collaboration on the project with state-of-the-art versioning software.
Indeed, using Git for this purpose could be considered relatively advanced and one may argue that users of this level may not need the guidance that this workflow is designed to provide.
Even without collaboration, the back-up functionality is valuable.
Uploading to a closed GitHub repository keeps the unpublished work private but backed up online.
At time of publication, a GitHub repository can be made public and linked to Zenodo.
Zenodo then archives the work and provides a citable DOI reference. (@fig:fig7_git_zenodo B)

## Data

Phylogenetics is in the first place a comparative exercise, hence to gain insight in the evolution of any protein sequence, one must compare it to related sequences with a shared origin.
As plant biologists studying ferns, we are challenged by a lack of seed-free plant genomes available to us.
Luckily, the recent 1kP project [@Leebens-Mack2019] provides solution by collecting the genomes and assembled transcriptomes of 1000 plant species.
The 1kP effort fills a gap in reference databases, providing coding sequences for a large number of seed-free plants.
As fern researchers, we make intensive use of the 1kP project and we use it in the examples included here.
Alternatively, one can search for homologs in the non-redundant protein database of NCBI (nr) with blastP as explained in @VanHooff2019.

| Clade        | Lineage                        | Sample count |
| ------------ | ----------------               |    ---       |
| Algae        | Chloranthales                  |            2 |
| Algae        | Chromista (Algae)              |           35 |
| Algae        | Glaucophyta (Algae)            |            5 |
| Algae        | Green Algae                    |          171 |
| Algae        | Red Algae                      |           28 |
| Bryophytes   | Hornworts                      |           14 |
| Bryophytes   | Liverworts                     |           29 |
| Bryophytes   | Mosses                         |           41 |
| Lycophytes   | Lycophytes                     |           22 |
| Monilophytes | Eusporangiate Monilophytes     |           12 |
| Monilophytes | Leptosporangiate Monilophytes  |           68 |
| Gymnosperms  | Conifers                       |           76 |
| Gymnosperms  | Cycadales                      |            4 |
| Gymnosperms  | Ginkgoales                     |            1 |
| Gymnosperms  | Gnetales                       |            3 |
| Angiosperms  | Basal Eudicots                 |           58 |
| Angiosperms  | Basalmost angiosperms          |            8 |
| Angiosperms  | Core Eudicots                  |          119 |
| Angiosperms  | Core Eudicots/Asterids         |          248 |
| Angiosperms  | Core Eudicots/Rosids           |          257 |
| Angiosperms  | Magnoliids                     |           27 |
| Angiosperms  | Monocots                       |           66 |
| Angiosperms  | Monocots/Commelinids           |           45 |
|              |                               |              |
|              | **Grand Total**                |     **1339** |

Table: Transcriptome sample counts per clade of the Viridiplantae. {#tbl:tbl7_1kP_sample_counts}

Transcriptome assembled coding sequences do present a set of challenges that one must be aware of when doing phylogenetic work.
The 1kP project [@Leebens-Mack2019] published assembled transcriptomes for over 1000 plant species (@tbl:tbl7_1kP_sample_counts) and included 26 species with sequenced genomes in their dataset as well.
Genome assembly based data can reasonably be assumed to be complete.
In phylogenetics, this is relevant for all homologs that a species may contain will be present in the dataset.
For transcriptome assembled data, this assumption does not hold.
Homologs may not be simultaneously expressed and therefore absent from the dataset.
Alternatively, homologs may be assembled as a single sequence.
Absence of paralogs or orthologs in the dataset and the phylogeny inferred thereof is relevant for it may cause wrong inference of speciation and duplication nodes.
Consequently, orthology inference may be faulty as well.
To somewhat mitigate this shortcoming, we chose to include a substantial amount of species in our phylogenies.
I argue that if one species does not express both paralogs simultaneously, then maybe another will.
To make our trees and the orthology and paralogy patterns easier interpretable, I colour code six main clades of the Viridiplantae in my trees.
These are the Algae, Bryophytes, Lycophytes, Monilophytes, Gymnosperms and Angiosperms (@tbl:tbl7_1kP_sample_counts; @tbl:tbl7_clade_colours).

| Clade        | Colour code |
| ------------ | -------- |
| Algae        | 7635a5ff |
| Bryophytes   | ec7505ff |
| Lycophytes   | 00b4f1ff |
| Monilophytes | 00b456ff |
| Gymnosperms  | ff0000ff |
| Angiosperms  | 3a58d6ff |

Table: Colour coding used by the _Azolla_ lab for easing interpretation of land-plant phylogenies. {#tbl:tbl7_clade_colours}

This vast dataset of plant coding sequences, or any set of sequences, must still be searched for homologous sequences.
One would typically use blast for these homologs in either the 1kP data, or in NCBI blast, or both.
However, the work done by the 1kP authors already includes big orthogroups made with Orthofinder [@Emms2019].
These orthogroups contain whole gene families and perhaps counter-intuitively includes paralogous groups within that gene family.
We may use these orthogroups as starting points for our own phylogenetic inferences.
These orthogroups are more reliable than blast searches and hence provide an improved starting point.
Unfortunately, the orthogroups created by the 1kP project are not publicly available any more.
They are not included in the data-uploads to the usual repositories but instead hosted at a separate link.
The original link ([jlmwiki.plantbio.uga.edu/onekp/v2/](http://jlmwiki.plantbio.uga.edu/onekp/v2/)) at the Leebens-Mack lab is no longer available.
The authors were made aware of this early 2022 but as of yet there is no alternative way to access this data.

## Alternative tools

Existing tools that house a complete workflow from gathering sequences up to inferring a ML tree are rare.
The one tool that is best known for this purpose is MEGA X [@Kumar2016].
MEGA X is often found in literature and has substantially contributed to making phylogenic tools available to the broad public.
The software is especially attractive to novice users for it runs on Windows, has a graphical user interface, and includes all steps from beginning to end.
I find it especially useful for smaller phylogenies, no more than 50 sequences.

My main criticism on the MEGA software is that inferior NJ based methods are presented as equally good options to ML methods and the exact method in which MEGA X implements the ML methodology is unknown to the public.
A search of recent literature shows that MEGA X users often employ the fast but inferior NJ method where reasonably an ML tree should be have been created.
I did a short inquiry into citations of @Kumar2016 sorted by date in google scholar so google algorithms do not play into sampling bias.
Out of the 50 most recent citations, 40 publications were publicly accessible and contained a phylogeny.
Of these, 17 contained a ML tree, 22 a NJ tree, and one a maximum parsimony tree .
None of these phylogenetic studies were of such a size that ML methods could not have been used.
A secondary objection to the use of proprietary software, is the use of proprietary file formats where the field typically employs standardized file formats.

Using the state-of-the-art tools in the Linux CML is a steep learning curve, explaining and validating the niche of a tool like MEGA X.
This workflow aims to improve on MEGA X shortcomings by providing all the state-of-the-art CML tools at a reduced learning curve.
Doing so in a JuPy notebook makes it easy to document and journal while doing the analysis.
Finally, it eases to transition to bigger datasets that GUI desktop software often is not tailored to.

# Workflow

The workflow consists of 6 Major steps.
The software choices are tailored to strike a balance between relatively big datasets and user-friendliness.
These steps are:

  \begin{enumerate}
  \item Acquiring data and optional subsetting
      \begin{itemize}
      \item Via blast or 1kP
      \item optional subsetting of data
      \item Adding guide sequences; sequences who have their function verified.
      \end{itemize}
  \item Aligning sequences
      \begin{itemize}
      \item mafft
      \end{itemize}
  \item MSA trimming
      \begin{itemize}
      \item trimAL
      \end{itemize}
  \item Fasttree building
      \begin{itemize}
      \item IQTree "fast" or via fasttree
      \end{itemize}
  \item Tree building
      \begin{itemize}
      \item IQTree with model fitting
      \end{itemize}
  \item Tree visualisation with iToL
  \end{enumerate}

`Should this be a figure`
<!-- Yes it should be a figure -->

For each of these step, I will highlight some design choices and indicate if these can be done online as well as in the workflow.

## Acquiring data

The workflow exemplifies two specific data sources.
In the use by the _Azolla_ lab, we have employed the 1kP dataset intensively, however we also exemplify blast searches as an input.
For phylogenies spanning all land plants ---the Viridiplantae--- we exclusively use amino acid sequences.
The 1kP orthogroup extractor specifically is a great resource to acquire many related sequences of seed and seed-free plants alike.
In the workflow, I highly the importance of selecting all sequences of a species and provide quick instructions on how to use ncbi blastp to search in specific species.
Within the 1kP project, there is no web interface to easily select per species.
Therefore I provide some pre-written BASH code to subset 1kP orthogroup files per species.

To attribute functional annotation to any clade or orthologous genes, we use what we term 'guide sequences.'
These are sequences that we manually select from literature for their verified functionality.
Ideally, these guide sequences represent multiple of the major land plant clades, but in reality they are mostly found in angiosperms.

Finally, we also add sequences of inquiry, those that we'd like to place in context of evolution of land plants (i.e. the 1kP data) and assign some function to via guide sequences.

Acquiring data from NCBI blastP can be done online completely, subsetting orthogroups of the 1kP has no online alternatives.

## Aligning the dataset

Now that we have a collection of homologous sequences, the next step is to align these to each other.
Two of the famous tools to this end are ClustalOMEGA (previously known as clustalW) and MUSCLE [@Sievers2014; @Edgar2004].
Both tools however, are single-threaded; meaning they can use only one CPU cores where modern computers often have several.
They are outperformed in most cases by more modern tools, especially for big or gappy datasets [@Pais2014].
The transcriptome data of the 1kP occasionally contains mis-assemblies that cause such big gaps in an MSA.
Given the size of the datasets we work with in the _Azolla_ lab and the size of the 1kP orthogroups we have worked with, I chose to use MAFFT [@Katoh2013].
MAFFT is a multiple sequence aligner that can make use of additional CPU cores, and can deal well with big gaps in alignments.
In my limited testing, MAFFT was easier and more reliable to run than another modern candidate: T-coffee [@Notredame2000].

MAFFT has multiple configurations with each their own use case.
For big datasets, the algorithm defaults to fast progressive alignment methods.
Automatic choice of algorithm is based on the count of sequences only, and not on biological information.
Hence I recommend to specifically choose the slower iterative refining methods based on the nature of the gene.
Naturally, it is good practice to try multiple methods and compare the MSAs by eye to see how they perform.
The iterative methods require considerable more compute time compared to the fast methods.
I consider this investment justified for the quality of MSA is determining for the quality of the phylogeny.
The MAFFT manual explains my 3 favourite presents that we have used successfully in the _Azolla_ lab.

* E-INS-i: For sequences with multiple conserved domains and long gaps.
* L-INS-i: For sequences with one conserved domain and longs gaps.
* G-INS-i: For sequences with global homology.

When comparing alignment configurations to each other visually, I aim to maximise for structure or patterns (@fig:fig7_align_examples).
The various fast or slow configurations produce overall quite similar results at first sight.
Especially the most conserved regions are near identical for each algorithm
(@fig:fig7_align_examples A, B, C).
The regions with barely any sequence content will be filtered out in a later step, this is typically quite a proportion of an MSA with many sequences (@fig:fig7_align_examples D).
Hence, I'm searching by eye those columns with substantial sequence content that are not extremely conserved and see how they align.
Ideally, by optimising this step, some extra phylogenetic signal might be gained from these medium-conserved regions.
At worst, one might erroneously align regions that are not homologous but analogous to each other.

In the example MSAs in @fig:fig7_align_examples, the 'auto' MSA was discarded first due to lack of structure in gappy regions.
The linsi and einsi MSAs were assessed as near equal in quality; we preceded with the einsi version.
Regardless, both MSAs performed insufficiently in the gap regions.
I estimate, by studying various versions of similar MIKC^C^ MSAs, that some structure may be hidden in those regions and was not uncovered by the MAFFT MSA.

For MSAs of reasonable size, no more than a couple of hundreds of sequences, these medium-conserved gappy INDEL regions may be re-aligned with a dedicated INDEL realigner such as prank [@Loytynoja2014].
When successful, INDEL realignment can bring structure into medium-conserved regions for correct phylogenetic inference.
In my experience, this can help in reducing noise from such regions by separating non-homologous residues into separate sections.
This clears up the phylogenetic signal between groups that don't share INDELs and may improve the signal within these groups.
INDEL realignment does not work for MSAs with several hundreds to thousands of sequences for the software cannot handle these numbers.

In the _Azolla_ lab I used INDEL realignment for optimising a MIKC^C^ MSA (@fig:fig7_align_trimprank A & B).
A MAFFT MSA that was trimmed for a minimum of 10% sequence content per column shows clear structure in conserved domains (@fig:fig7_align_trimprank A).
However medium-conserved regions contain little structure and non-homologous residues may be aligned to each other.
I realigned the MIKC^C^MSA with prank supported by an ML guide tree of a more strict trim of the same MSA.
The resulting MSA was trimmed for 10% column content as well and shows clear structure in the medium-conserved regions previously not seen (@fig:fig7_align_trimprank B).
After realignment, the region between the main conserved domains contains multiple INDELS unique to specific groups of sequences(@fig:fig7_align_trimprank B).
Before realignment these regions seemed forced together and would have diluted the phylogenetic signal with false synapomorphies
All MSAs and png snapshots of the MIKC^C^ phylogeny work of the _Azolla_ lab can be found in a GitHub repository.
These file can be found at [github.com/lauralwd/MIKC_tree/tree/master/data/alignments_raw](https://github.com/lauralwd/MIKC_tree/tree/master/data/alignments_raw).

MAFFT also has an online version that is very user friendly: [mafft.cbrc.jp/alignment/server/](https://mafft.cbrc.jp/alignment/server/) [@Katoh2019].
It is however limited in its performance when using the three configurations mentioned above.
For big datasets, it pays off to run the alignment locally.

<!---
make jalview MSA svgs smaller by removing all text fields:

expanding the svg to a long format:
xmlstarlet ed -d text jalview.svg > intermediate.svg

cat intermediate.svg | grep -v '<g transform' | grep -v 'sans-serif' | grep -v 'Arial' | grep -v '</g>' > small_jalview.svg

Actually, just do this in the jalview format and view menu's that makes life a lot easier!
--->

![Multiple Sequence Alignments by MAFFT. A dataset of MIKC^C^ sequences from the 1kP project was subsetted and then aligned with mafft auto (A) linsi (B) and einsi (C). Panels A, B and C depict sections of the original MSA, panel D depicts the full einsi MSA. MSAs were visualised with jalview and coloured via the clustal colouring scheme. Only the colouring scheme is retained in this figure. The four bar graphs underneath each MSA depict Conservation, Quality, Consensus and Occupancy from top to bottom.](source/figures/fig7_align_examples.pdf){#fig:fig7_align_examples height=90%  short-caption="MSA algorithms compared."}

## Trimming

Trimming optimizes MSA by removing noise from gapped regions and low-quality sequences.
Big MSAs, especially those based on transcriptome data, are not optimal for phylogeny inference.
Phylogeny inference is driven by synapomorphies, shared differences between a majority of sequences.
The inference is hampered whenever a major fraction of sequences contains no content at all (gaps), or when a conserved region is missing from a particular sequence.
Therefore, I trim the MSA to remove data that is not aligned well, and may disrupt the evolutionary signal we attempt to uncover.

### Column based trimming

The simplest and perhaps most effective trimming method is removing gaps by removing columns ---removing shared amino acid residues--- in the MSA that contain no content in the majority of sequences.
Gap regions are easily identified in a visualised MSA as a blocky pattern (@fig:fig7_align_examples)
These regions often represent insertions or mis-assemblies in specific taxa.
Regardless, gaps contain little to no phylogenetic informative information.
Column filtering is easy and can be done visually in tools like jalview, or even directly when aligning in the online version of MAFFT [@Katoh2019].

### Sequence based trimming

A second filter concerns that of rows, of sequences in the MSA, that align poorly to the bulk of sequences.
When a sequence contains insertions fragments not shared by the majority of sequences these are easily filtered out in the column filter.
Alternatively, a sequence may mis substantial parts of conserved domains.
Such a fragmented sequence misses important synapomorphy information to correctly place it in a phylogeny.
A sequence fragment can be seen in an MSA visualisation as light horizontal banding (@fig:fig7_align_examples; @fig:fig7_align_trimprank C).
Regardless the reason, it may be wise to filter these sequences out conservatively.
When removing entire sequences from a dataset, one risks to also remove essential information with which speciation and duplication nodes are distinguished.
This is another reason I often make relatively large trees in the _Azolla_ lab when we make use of the 1kP data.
By including more species I hope to add a certain robustness to this risk.

![Optimisation of MAFFT MSAs. The top two panels contain overviews of a MAFFT MSA of the MIKC^C^ orthogroup subset trimmed for column content (A) versus an MAFFT MSA of the same data that was realigned with prank and then trimmed for column content. In the bottom two panels two MSA overviews are displayed of a subset of 2OGD enzyme sequences from transcriptome data. One MSA was made with MAFFT and then trimmed for column content only (C) and the other was trimmed for both column and sequence content (D). MSAs were visualised with jalview and coloured via the clustal colouring scheme. Only the colouring scheme is retained in panels C & D. The four bar graphs underneath panels A & B depict Conservation, Quality, Consensus and Occupancy from top to bottom.](source/figures/fig7_align_trimprank.pdf){#fig:fig7_align_trimprank short-caption="MSA improvement via trimming and indel-realignment"}

### trimAL trims both columns and sequences

The tool of choice to tackle both filters at once, is trimAL [@Capella-Gutierrez2009].
TrimAL allows to set a gap threshold, as well as parameters to filter out sequences.
There is no single rule for good thresholds, we encourage experimentation and re-evaluation to find a good setting for any particular dataset.
As a gap threshold we typically start with a value of 40% and explore further from there on out.
Filtering sequences is less straight forward.
This works by setting a threshold for determining conserved amino acid residues first.
The second threshold determines how much of these conserved sites must be present in any sequence of the dataset.
When done well, the major conserved regions are present in the vast majority of sequences and the horizontal banding is absent (@fig:fig7_align_trimprank C vs. @fig:fig7_align_trimprank D).
In the section on 2 OGD phylogeny, we demonstrate a visual exploration to summarise the behaviour of these parameters for the MSAs shown in panels C & D of @fig:fig7_align_trimprank.

To our knowledge there are no online tools that achieve a similar finesse of filtering MSAs as trimAL does.
When restricted to online tools, the column occupancy filter in the online version of MAFFT is an obvious and convenient choice.

## Fast phylogeny inference

Full phylogeny inference and non-parametric bootstrapping can take a considerable amount of time.
Therefore, it is wise to explore the likely outcome tree with a fast tree inference program that does not perform bootstrapping.
This allows for a preliminary view into the final result and observe potential mistakes, remove or add sequences of interest.
Conveniently, the calculation time for a final tree may then be used to test final visualisation.
The field standard towards fast preliminary tree inference is considered to be FastTree.
In our workflow however, we use IQTree's 'fast' setting for it produces an output file structure nearly identical to the final tree inference.
The FastTree software is included in the conda environment and can be used as an alternative.

To our knowledge, no online fast tree inference algorithm is available.
However, a regular tree inference without bootstrapping would be a reasonably fast alternative when restricted to online tools.
Regular tree inference is described in the next section.

## Full phylogeny inference

For phylogeny inference, we supply a ML option only for we see very few good arguments to resort to NJ or MP methods instead.
In this workflow we use IQTree for model fitting, phylogenetic tree inference, and calculating bootstrap support [@Nguyen2015; @Kalyaanamoorthy2017].
These are three distinct steps, especially the first often is not included in phylogeny software.
The details of fitting a model of evolution to an MSA are beyond the scope of this manuscript.
The basics include fitting a substitution matrix of amino acid exchange rates of nucleotide exchange rates to those observed in an MSA [@Sullivan2005; @Felsenstein2004].
Additionally, more advanced parameters are assessed such as heterogeneity of the speed in which MSA positions evolve over time amongst the entries in the MSA: Rate heterogeneity.
For the audience of this workflow, we recommend to use IQtree's build in extended model fitter by using the option `-m MFP` --- short for Model Finder and Phylogeny.

### Phylogeny support valuesw

A major property of interpreting phylogenies, is support values.
These support values, often called bootstrap values, can be determined in several ways.
Next we'll discuss three support estimation methods.
Firstly, the slow and simple but time-tested method of Felsenstein's bootstrap, or 'regular bootstraps'.
Second, we'll discuss an equally slow alternative that is more suited to bigger trees: transfer bootstrap [@Lemoine2018].
These fist two methods are slow, but behave reasonably linear and are easily interpretable.
They are often indicated as non-parametric methods.
Thirdly, we'll discuss faster parametric options such as IQTree's UltraFastBootstrap.
These methods behave non-linearly and are harder to interpret but find a use case in estimating support of very big trees or of preliminary small trees.

### Felsenstein's bootstrap

Support estimation by bootstrapping is an important step in assessing reliability of any phylogeny.
After the main phylogeny is established, one can choose to bootstrap it for $b$ times, typically $b=100$.
Bootstrapping in phylogeny is a process in which a fraction MSA columns is removed and replaced by a random subset of the remaining fraction.
The phylogeny inference is then repeated.
After repeating this process for $b$ times, the nodes in the final tree get a support score based on the similarity of these nodes in the bootstrapped repetitions.
The most used and most conservative approach is Felsenstein's bootstrap.
This approach is a binary one.
It counts those repetitions in which the bootstrap node is identical to the reference node: $i$.
In other words, the nodes for which the division of leaves left and right of that node is identical regardless their exact topology beyond that node.
The support value is a simple percentage of those nodes over the total amount of bootstraps done: $(\frac{i}{b}) 100\%$.
This method is easily interpretable, and standardised in the field.

Felsenstein's BootStrap (FBS) does have drawbacks, especially for bigger trees.
In the _Azolla_ lab we experienced that nodes deep in a big phylogeny, those nodes that typically represent ancestral states, receive very low support values.
Yet, when repeating the tree inferences with modified datasets, these nodes appeared highly robust.
If a single sequence its placement is highly variable ---a rogue taxon--- it will have huge impact on the support values of deep nodes despite the placement of the majority of taxa being highly reliable.
We observe that for big trees, FBS is often uninformative for deeper nodes.

### Transfer Bootstrap

TransferBootStraps (TBS) present an alternative support criterion that was designed to circumvent this exact issue found in bigger phylogenies [@Lemoine2018].
When calculating TBS for any node, it takes a non-binary approach.
A node's bootstrap isn't regarded as either good $i=1$ or false $i=0$ as in FBS.
Instead, a continuous metric is used: distance criterion $\phi$.
This criterion is based on the minimum amount of leaves that must be _transferred_ from one side of a node to the other for a bootstrap tree to represent the main tree.
Finally this metric is corrected for any proportion difference $p$ between the left and right side of that node.
The method is further detailed in @Lemoine2018.

$(TBS= 1- \frac{\phi}{p-1})$

I have used TBS with success in big phylogenies and recommend its usage for large datasets; those of several hundreds of sequences.
TBS values of shallow nodes typically represent those of FBS, and TBS values of deep nodes typically read as if they are shallow nodes.
In the _Azolla_ lab we found that TBS assigns more meaningful support values to deep nodes.
The method is however not wide spread in the field, and its usage should be clearly stated for correct interpretation of phylogeny support values.

### Parametric support methods

Both FBS and TBS are slow methods for they require to redo a full phylogenetic inference $b$ times.
Modern phylogeny inference tools often have faster parametric methods that calculate support.
IQTree has such a method called UltraFastBootstrap (UFB) [@Hoang2018], which the authors recommend to pair with the Shimodaira-Hasegawa approximate Likelihood Ratio Test (SH-aLRT) [@Guindon2010].
The IQTree manual suggests to trust any node if it has over 95% UFB and over 80% SH-aLRT confidence.

I use UFB for preliminary trees, or those that are too big to produce FBS or TBS support within weeks of time.
Confusingly, the values that UFB produces are not to be compared with those of TBS and FBS.
Per the IQTree manual, a UFB support of 95% corresponds to a 95% probability that this node is a "true node".
One might be inclined to think a 90% UFB support is also quite believable.
In our use however, we have observed 90% UFB nodes that became 20%FBS nodes once non-parametric bootstrapping was done.

### Choosing a support method

<!-- A concise comparison table for FBS and TBS, with pros, cons, and recommended use cases, could improve clarity and user decision-making. -->
Support estimation in phylogeny comes in many shapes and forms with each their own pro's and cons.
We recommend to use non-parametric methods such as FBS and TBS in final results for ease of interpretation and reliability.
We resort to UFB and SH-aLRT for very big phylogenies only.
Regardless the method, we emphasise the importance of clearly indicating the support estimation method used with any phylogeny.

Online phylogeny inference is freely available and makes the methods accessible to all.
IQtree can be used online although with limitations ([iqtree.cibiv.univie.ac.at](http://iqtree.cibiv.univie.ac.at/)) [@Trifinopoulos2016].
Additionally, all these steps can also be done in PHYML, an alternative tool with the same use case, on [atgc-montpellier.fr/phyml/](http://www.atgc-montpellier.fr/phyml/).

## Visualisation

For visualisation of the phylogeny, I recommend working in iToL [@Letunic2019] [itol.embl.de](https://itol.embl.de/).
Like the JuPyter notebook, iToL works in an internet browser.
Unfortunately, the free version of iToL does not allow to save the layout of a phylogeny any more, but a paid version allows you to do so.

When uploading a tree file into iToL, I take several steps to turn it into a final figure.
First is rooting the tree.
When working with land-plants, I typically root on algae sequences.
Second is colouring the major clades as in @tbl:tbl7_clade_colours, and adjusting any text size and colour.
I recommend doing so by using annotation files rather than doing it manually.
These annotation files can also be shared in a Git repository for reproducibility.
For an example find the annotation file of the annotation file for @fig:fig7_2OGD_phylogeny_small online at [github.com/lauralwd/2OGD_phylogeny/blob/master/analyses/v2g5_JOX-ANS-FLS-subset_iTol-branch-labels_manual.txt](https://github.com/lauralwd/2OGD_phylogeny/blob/master/analyses/v2g5_JOX-ANS-FLS-subset_iTol-branch-labels_manual.txt).
For refined visualisation, one can download the tree as a `.svg` file and edit it further in InkScape.
InkScape is a free and open source vector image editor which houses all tools required for making high quality publication ready figures. Nearly all figures in this thesis were made with the software.

In interpreting the phylogeny, I critically interpret correct speciation patterns.
The order in which the 6 main land plant clades have evolved is not debated, and a phylogeny should not contain major violations of this order.
Next, orthologous groups can be inferred and annotated according to the guide sequences added earlier.
One may then see if any sequence of interest is reliably placed within such an orthologous clade.
Optionally, more data can be added onto the tree, such as the MSA, RNA-seq data, certain groupings, protein domains, etcetera.
We discuss these options further in the Usecases section.

# Usecases

In this section, I discuss several use cases of this phylogeny workflow in the _Azolla_ lab.
Firstly, that of several leucoanthocyanidin reductase (LAR) homologs found in _Azolla_.
This project was actually the inspiration for creating this workflow.
Second, a MIKC^C^ phylogeny.
With this phylogeny of MIKC^C^ transcription factors we attempted to elucidate the evolution of fern sexual reproduction in context of all of land plants.
This tree is part of the supplemental information of chapter \ref{it_takes_two}.
Thirdly, a 2-OGD phylogeny inference with several _Azolla_ sequences added.
The 2-OGD family is one of the biggest enzyme families in land plants.
We wanted to study how ferns have developed differently from land plants, and infer the functionality of a specific fern 2-OGD gene that was differentially expressed in an RNA-seq experiment.

## LAR

The LAR enzyme is member of the PIP family of enzymes.
In context of _Azolla_ biology, it is an interesting enzyme for it is a key enzyme in the production of both anthocyanidins, as well as epicatechin; a notorious digestion inhibiting polyphenol.
When pitching _Azolla_ as a future crop, digestion inhibition is an important trait for breeding efforts.
In this use-case, we identify and organise the LAR enzymes present in the _Azolla_ genome and infer their function for future experiments and possible breeding efforts.
Additionally, we identify two LAR-like groups (WLAR1 & WLAR2) which diverged specifically in ferns and have no seed-plant orthologs.

The _Azolla_ genome contains several LAR like enzymes (homologs) that may all play a role in anthocyan metabolism.
In this case-study, we use phylogeny to infer the relation of all _Azolla_ LAR homologs in the perspective of the entire PIP family of enzymes in land plants.
Elucidating the function of these homologs is a typical example of an orthology research question.

We used the 1kP orthogroup extractor [@Leebens-Mack2019] to acquire a PIP orthogroup, subsetted this to get a reasonable amount of all major land plant clades, and added characterised and PIP enzymes and _Azolla_ LAR homologs.
The data was aligned with MAFFT L-INSI-i and trimmed to reveal one major block of conserved residues.
The phylogeny was inferred with IQTree including automated model fitting and UFB+SH-aLRT.
Several optimisation rounds followed next, adapting the entries of the original dataset and testing reproducibility of the topology of important nodes.
The final tree was annotated in iToL, showing only sequence names of interest and colouring clades according to major land plant groups.
This tree is published in @Gungor2021 and the full analysis is openly available on Github (github.com/lauralwd/LAR_phylogeny_gungor-et-al-2020](<https://github.com/lauralwd/LAR_phylogeny_gungor-et-al-2020>)) and archived in Zenodo ([DOI:10.5281/zenodo.3959056](https://doi.org/10.5281/zenodo.3959056)).

![Phylogeny of LAR and other PIP-family enzymes across land plant lineages. Protein sequences were retrieved as a single orthogroup containing the _Vitis vinifera_ LAR from the 1KP orthogroup database2 [@Leebens-Mack2019], sub-sampled, and supplemented with guide- and _A. filiculoides_ LAR-like sequences. The 785 sequences were aligned with MAFFT-linsi [@Katoh2013], then trimmed using trimAL [@Capella-Gutierrez2009] and, using IQtree [@Nguyen2015], the phylogenetic tree computed with the resulting 305 parsimony informative sites. The best-fit substitution model was LG+R7 and bootstrap support was determined via SH-aLRT [@Guindon2010]. The tree was annotated in iTOL; highlighting characterized enzymes and sequences of particular interest [@Letunic2019]. Nodes with bootstrap support equal or greater than 80% SH-aLRT are indicated by circles. EGS and IGS clustered in two groups: IGS/EGS-I and IGS/EGS-II. PLR, pinoresinol-lariciresinol reductase; IFR, isoflavone reductase; PCBER, phenylcoumaran benzylic ether reductase; EGS, eugenol synthase; IGS, isoeugenol synthase; LAR, leucoanthocyanidin reductase; WLAR, fern specific LAR-like. Full phylogeny is available at [github.com/lauralwd/LAR_phylogeny_gungor-et-al-2020](https://github.com/lauralwd/LAR_phylogeny_gungor-et-al-2020)](source/figures/fig7_LAR_phylogeny.pdf){#fig:fig7_LAR_phylogeny short-caption="Phylogeny of LAR and other PIP-family enzymes across land plant lineages"}

The LAR phylogeny shows that the LAR enzyme is a fern invention also present in seed plants (@fig:fig7_LAR_phylogeny).
It is distinct from other groups of PIP enzymes such as PLR, IFR and PCBER.
LAR-like enzymes have radiated in ferns specifically, but not in seed plants.
These clades were termed WannabeLARs (WLAR) in @Gungor2021.
Any phylogeny is ultimately only an hypothesis of evolution.
The function of LAR homologs was verified via alternate methods.
WLARs differed substantially in their active sites, as indicated by structural modelling.
More importantly, _A. filiculoides_ LAR was confirmed to have LAR activity by an enzyme activity assay where WLARs did not show this activity.
The exact function of WLARs remains unknown, none of these sequences was ever categorised separately before.
Ostensibly, ferns have radiated their own set of unique PIP enzymes, as seed plants have uniquely radiated IFR and PCBER enzymes.

## MIKc

By definition, ferns and seed plants have different methods of sexual reproduction.
In chapter \ref{it_takes_two} we take interest in finding the fern transcription factors behind the transition to sexual reproduction.
The rationale here, is that we can infer the evolution of sexual reproduction of plants from the evolution of transcription factors controlling the reproductive organs of those plants.

We use RNAseq and homology searches to find transcription factors active in _A. filiculoides_ during sexual reproduction.
Then, we place these in a phylogeny with seed plant ABCDE genes responsible for flower organ identity.
The exact methods are detailed in chapter \ref{it_takes_two}.
I highlight it here for our use of prank INDEL realignment (as demonstrated in @fig:fig7_align_trimprank A vs. B) for this was a major step in acquiring a well supported phylogeny (@fig:fig7_MIKCc_phylogeny).

In this particular example, it is hard to extrapolate functional annotation from one seed plant clade to a fern clade.
The fern clades with sequences of interest often contain many gene duplications, and not all fern clades contain sequences of the same species.
Many genes may be missing from the 1kP dataset due to it being transcriptome based.
Genes involved in the transition to sexual reproduction are after all not ubiquitously expressed nor abundantly expressed when considering bulk tissue RNA extractions.
More genome based data of seed-free plants and functional characterisation of transcription factors may allow us to better interpret a phylogeny like this one.

![Azolla MIKC^C^ phylogenetic analysis and response to FR. The Azolla MIKCC gene model encoded by Azfi_s0028.g024032 was annotated manually. Sequences extracted from the genome browsers of each species were aligned with MAFFT E-INS-i [@Katoh2013], then trimmed with trimAl [@Capella-Gutierrez2009]. First a draft phylogeny was computed with IQTREE [@Nguyen2015], then this draft phylogeny served as a guide for alignment optimization with PRANK [@Loytynoja2014] of the untrimmed original MAFFT E-INS-i MSA. This optimized MSA was then trimmed again with trimAl and used for inference of the final phylogeny with IQTREE. Bootstrap values are transfer bootstraps calculated with 1000 non-parametric bootstrap trees [@Lemoine2018]. Transfer bootstrap assays similarity of nodes rather than binary identical or non-identical nodes in bootstrap trees: it therefore tends to be more informative for bigger trees. All code is deposited on github.com/lauralwd/MIKC_tree. The tree was rooted on a group of algal sequences. Nodes with bootstrap support equal or greater than 50% are indicated. Branches are color coded as per their plant lineage.](source/figures/fig7_MIKCc_phylogeny.pdf){#fig:fig7_MIKCc_phylogeny short-caption="Azolla MIKCc phylogenetic analysis and response to FR"}

## 2-OGD

In an RNAseq experiment in the _Azolla_ lab, several genes were significantly differentially regulated.
The functional annotation of these genes was doubtful.  Homology searches indicated it was a a 2-oxoglutarate dependent dioxygenase (2-OGD) enzyme [@gungor2024]; the biggest enzyme family in plants.
A phylogeny workflow was started to place the _Azolla_ genes of interest and homologs in context of all 2-OGD evolution.
Correct classification of these 2-OGD genes was key for proper interpretation of the RNAseq results.

An orthogroup of 2-OGD genes was obtained from the 1kP, subsetted and amended with sequences with their functions characterised.
The differentially expressed gene and other 2-OGD genes from _A. filiculoides_ genomes version 1 and version 2 were added as well.
Sequences were aligned with MAFFT L-INS-i, and trimmed with trimAL for columns and sequence content (@fig:fig7_align_trimprank C & D).
A first IQTree phylogeny with UFBootstrap was used to find the main clades in which the sequence of interest was placed (data not shown).
These clades, and an outcrop were extracted into a second subset from the former subset.
Then, a non-parametric phylogeny was inferred with TBS support.
The tree was coloured per clade (@tbl:tbl7_1kP_sample_counts) and we collapsed clades that were not of particular interest to this RNAseq experiment (@fig:fig7_2OGD_phylogeny_small).
Afterwards, the original subset was also used for a tree with TBS support values (@fig:fig7_2OGD_phylogeny).
This big tree provides an overview over all of 2-OGD evolution in land plants, with special interest for non-seed plants.
This tree is published in @gungor2024 and the full analysis is openly available on Github ([github.com/lauralwd/2OGD_phylogeny](https://github.com/lauralwd/2OGD_phylogeny)).

![Phylogeny of 2-OGD genes encoding FLS, ANS and JOX across land plant lineages. 2-OGD protein sequences were obtained from the 1kp orthogroup database [@Leebens-Mack2019], sub-sampled and supplemented with guide- and _A. filiculoides_ 2-OGD sequences. The former were used for clade annotation, the latter are indicated in green for _A. filiculoides_ genome version 1 [@Li2018] and version 2 (Afi_v2) [@gungor2024]). An initial phylogeny (@fig:fig7_2OGD_phylogeny) was computed to place _A. filiculoides_ genes in the broad 2-OGD phylogeny. From this broad phylogeny, FLS, ANS, JOX and out-group sequences were selected to compute a more accurate tree. Sequences were aligned with MAFFT-linsi [@Katoh2013], and then trimmed using trimAL [@Capella-Gutierrez2009]. The phylogeny was computed with IQtree [@Nguyen2015] with 200 non-parametric bootstraps and transfer-bootstrap values were calculated with booster [@Lemoine2018]. The tree was annotated in iTOL and Inkscape [@Letunic2019].  ](source/figures/fig7_2OGD_phylogeny_small.pdf){#fig:fig7_2OGD_phylogeny_small width=50% short-caption="Phylogeny of 2-OGD genes encoding FLS, ANS and JOX across land plant lineages."}

The 2-OGD subset phylogeny confirms that the sequences of interest are most related to Jasmonate Oxidase (JOX) in seed plants.
It seems that in ferns JOX have radiated as they have in seed plants; a case of many-to-many orthology.
Despite this within-clade radiation, all seed plant paralogs with known function JOX1,2,3,4 accept only Jasmonate as a substrate.
The amino acid residues in the active side that bind jasmonate are conserved in both seed plant and fern clades.
Therefore we conclude these sequences are most likely _A. filiculoides_ JOX1 and JOX2.
The specific site of expression hints that Jasmonate signalling may be important in _Azolla_ symbiosis communication.

# Discussion


```
RNAseq data for phylogeny such a good idea... waiting for the 1000 plant genomes!
https://academic.oup.com/aob/advance-article/doi/10.1093/aob/mcae110/7732916
```

This chapter and the corresponding workflow aim to provide novice users with a reproducible approach for inferring phylogeny.
Its use is demonstrated in three usecases from Azolla lab publications.
The workflow uses open-source and state-the-art tools that require expert knowledge for usage.
Usage of these tools is made feasible for novices by embedding the tools in structured coding notebook with pre-written code and instructions.
This way, I attempt to provide novices with the best tools available to work on comparative genomics and evolutionary biology questions.
This chapter outlines the step-by-step process, from data acquisition to tree visualization.
It is a companion piece to the workflow itself, explaining the steps and providing required background.
And finally, providing context and limitations of this workflow in a rapidly changing landscape of bioinformatics tools.

## Landscape of phylogeny workflows

Many phylogenetics tools exist, including tools and complete workflows that arguably are more user friendly than mine.
I think of these tools on a spectrum from user involvement, to automation.
Tools like MEGA X create single trees with some user refinement.
On the other side of the spectrum a tool like Orthofinder 2 generates trees of all genes in a genome automatically.
Additionally, databases of pre-computed trees are freely available.
One can wonder what warrants yet another phylogenetics tool.

It is tempting to think that if tools exist on a spectrum ranging from artisanal to automation, that the man-hour-costing variants are simply too costly, and prone to human error.
This might be true, but I would counter arguing the automated versions are unspecific and miss signal and nuance by using a one-for-all approach.
Automated tools are required when the size of a project demands so, and occasional wrong results are merely a statistic.
Visit a bioinformatics symposium or conference, and one will find several examples of interesting biological exceptions and curiosities not picked up by broad general algorithms.
Biology remains a human job.
It requires observation and consideration, to question and to second guess results.
Hence, whenever possible, I advocate the labour-intensive approach.

Here I present a workflow clearly on the artisanal side of the spectrum.
It requires careful selection, curation, iteration and interpretation.
I attempt to be more thorough than MEGA X, as explained in the introduction section of this chapter.
Yet, this workflow is not as thorough or as flexible as tools like ETE3 and GoToTree.
These tools I consider more powerful and appropriate for experts.
My work sits in between, providing tools and current best practices to novice users in a structured workflow.

## Workflow Efficacy and Limitations

This workflow is limited in that it tackles one use case, with one workflow with a certain start and end.
Another limitation is the steep learning curve for beginners in command-line-based tools, which limits accessibility for non-experts.
Advanced frameworks like ETE3 and GoToTree3 provide a much more flexible framework to achieve many more goals.
Overall, despite some technical limitations, the workflow provides a practical balance of accuracy and computational efficiency.
I attempt not to school a user to a fully equipped comparative genomics expert, but merely to guide the human-input process exploring the evolutionary context of ones favourite gene through phylogeny.

The use of command-line tools may still present a barrier for some users, who might find graphical user interfaces more intuitive.
Here, I chose not to compromise in using less than the state-of-the-art tools available, hence "condemning" my users to the command line.
For expert users, the workflow’s modularity allows them to adjust parameters or swap out tools based on specific research needs, providing flexibility and control over the analysis.
Using the command line interface in a notebook format also encourages documenting parameter choices and results.
I hope this helps novices to advance quickly while giving experts space to explore alternative configurations.

## Application to Biological Research Questions

<!-- talk about 1kP here for non model organisms -->

In this chapter I demonstrate the workflow on three biological questions from the _Azolla_-lab.
We were confronted with the need to generate our own trees due to working with a non-model organism whose genome is not available in the big databases.
Cloning and verification of genes from a fern is costly and very labour intensive.
Phylogenetic inquire guided selection of cloning candidates, by inferring a more precise function of many similar genes (analogs) into functional groups (orthologs).
Still, a manual phylogeny workflow is more time consuming than an automated one, or by even assuming function from a simple blast search.
But the high level of certainty warrants the time invested in a manual workflow, when one considers how much experimental time may be lost when cloning and verifying the wrong gene in the wet lab.
A workflow like this may be of use for labs who are not experienced in comparative genomics, but who can use similar insights when working with species with limited genomic resources available.

<!-- Functional verification is so important. Phylogenies remain hypothetical -->

## Future Directions and Potential Improvements

Future development of this workflow should not focus on automation, or reducing user input, but on guiding the process better and making it conceptually easier.
I want the workflow to be more professional and simple by moving advanced coding options to supplementary files, for occasional usage.
By increasing simplicity, I hope modularity may be increased; to make it easier to use one's own favourite aligning tool or trimming tool rather than those I suggest.
Finally, I hope to better guide the visualisation section of the workflow. This now happens mostly outside of the notebook in a web tool: iToL.
However, some of iToL its functionality has been hidden behind paywalls since I first used it.
Alternate visualisation tools should ideally stay on ones computer, without need for an internet connection, and be scriptable and reproducible.
Finally, in teaching I have discovered how effective video tutorials can be to educate students.
Ideally, this workflow is also accompanied by a video workflow.
The workflow's future development should continue to prioritize reproducibility, ease of use, and expandability, ensuring it meets evolving needs in phylogenetic research.

\newpage

# Supplemental

![Phylogeny of 2-OGD genes across land plant lineages. 2-OGD protein sequences were obtained from the 1kp orthogroup database (Ka-Shu Wong et al., 2019), sub-sampled and supplemented with guide- and A. filiculoides 2-OGD sequences. The former were used for clade annotation, the latter are indicated in green for A. filiculoides genome version 1 (Azfi; Li et al., 2018) and version 2 (Afi v2). Sequences were aligned with MAFFT-einsi (Katoh et al., 2019), and then trimmed using trimAL (Capella-Gutiérrez et al., 2009). The phylogeny was computed with IQtree (Nguyen et al.,2015) with 200 bootstraps. Bootstrap support shown here are transfer bootstraps (Lemoine et al, 2018). The tree was annotated in iTOL (Letunic and Bork, 2019) and Inkscape. All code and data can be found on www.github.com/LauraLWD/2OGD_phylogeny](source/figures/fig7_2OGD_phylogeny.pdf){#fig:fig7_2OGD_phylogeny short-caption="Phylogeny of 2-OGD genes across land plant lineages."}

\nolinenumbers

<!-- close the last page of this section as required for removing the thumb index on next "part page" -->
\newpage
\null
<!-- don't show page nrs on cleardouble page -->
\pagestyle{plain}
<!-- stop the thumbmarking scheme (partwise) and start it (chapterwise) in the next chapter -->
\stopthumb
<!-- clear double page so that the chapters start nicely on a new right page -->
\cleardoublepage
