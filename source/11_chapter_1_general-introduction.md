\setcounter{page}{1}
\pagenumbering{arabic}
\onehalfspacing
\setlength{\parindent}{0.5in}

# General introduction
\label{introduction}

## basically: food

* current challenges
  - Nitrogen
* the case for novel crops

### Societial solutions and technology solutions

### Novel crops as solutions
* breeding, how novel crops lag behind


## Making a case for Azolla

### Azolla symbiosis life cycle

* fern, heterospory
* nostocs general
  - nostocs in fern

![Illustration of the _Azolla_ symbiosis life cycle by Erbil Güngör](source/figures/fig1_life-cycle.png){#fig:fig1_life-cycle width=100%}

### breeding a Symbiosis

### establishing the genetics

## fundamental scope?
* study of symbioses in general with meta-omics
* study of ferns in general

\newpage

<!---
label sections with LaTeX:
`\label{hidden treasures}`
or with markdown:
`{#sec:foul-play-in-the-pocket}`

Then referece to the full chapter name:
\nameref{hidden treasures}

the specific page:
\pageref{hidden treasures}

the chapter number:
\ref{hidden treasures}

with markdown if the ref contains no spaces:
+@sec:hidden-treasures

and for a markdown label only markdown refs work:
+@sec:foul-play-in-the-pocket
--->
## Outline of this thesis.
__Chapter \ref{foul play}__ (\nameref{foul play} on page \pageref{foul play}) details the initial discovery of prokaryotic DNA sequencing data in the initial _A. filiculoides_ genome assembly and includes the work that inspired this PhD project.
We identify near complete genomes as whole contigs in this assembly, and study these further.
These contigs are confirmed to be present in _A. filiculoides_ taken from the wild, as well as other _Azolla_ species for which WGS data is available.
Non-cyanobacterial prokaryotes are confirmed to be associated with all _Azolla_ species, and these may be the same or very similar microbes.
Finally, we study the metabolic pathways encoded within these genomes and hypothesise they might denitrify Nitrogen rich compounds within the _A. filiculoides_ leaf pocket.
This hypothesis is falsified however, denitrification occors only in microbes living epiphitically on _A. filiculoides_.

In __chapter \ref{hidden treasures}__ (\nameref{hidden treasures} on page \pageref{hidden treasures}), I build further on the work of chapter \ref{foul play}.
This chapter details a workflow to enrich and study the genome sequencing of bacterial contaminants in all sequenced _Azolla_ species.
This work aims to remove plant DNA sequencing only, and then assemble DNA of all _Azolla_ associated microbes present.
The process of separating disctint microbial genomes (binning) required extra binningsignals and manual curation.
Each respresented species of the _Azolla_ genus yielded between 12 and 22 associated bacterial genomes.
The majority of these genomes belong only to six taxonomical orders present in the majority of the entire _Azolla_ genus.
The systematic presence of these taxonomic groups suggests they be selected for in the _Azolla_ symbiosis and they may be vertically transfered over host generations as is the main symbiont _N. azollae_.

__\nameref{metagenomics practical}__ on page \pageref{metagenomics practical} illustrates a educational practical based on these first two chapters.
I designed a practical to teach the basic metagenomics principles and techniques to Life Sciences students with some form of coding experience.
The practical introduces the Bash language and tries to learn the main concepts behind metagenomics through a hands-on approach.
It starts with a metagenome assembly, and guides the students through DNA mapping, binning, quality control, gene annotation and finally plotting of metabolic pathways.
Exercises are implemented in JuPyter notebooks, combining code-writing with text instructions.
The practical is freely available on GitHub here [github.com/lauralwd/metagenomicspractical](https://github.com/lauralwd/metagenomicspractical)

__Chapter \ref{forever together}__ (\nameref{forever together} on page \pageref{forever together}) describes the genomics of the main _Azolla_ symbiont: _N. azollae_, using the genomes assembled in chapter \ref{hidden treasures}.
All _N. azollae_ share near identical genomes and gene content, indicating they are the same species of _N. azollae_, hosted in various _Azolla_ species.
Their phylogeny confirms they have co-evolved with their hosts.
The _N. azollae_ genome is degraded due to high pseudogene content.
Pseudogenation is caused by high transposon activity early in the symbiosis, but has since then slowed down.

__Chapter \ref{partners and passengers}__ (\nameref{partners and passengers} on page \pageref{partners and passengers}) is likely not going to happen...

__Chapter \ref{it takes two}__ (\nameref{it takes two} on page \pageref{it takes two}) provides building blocks for understanding and regulating the sexual reproduction and mode of transmission of the _Azolla_ & _N. azollae_ symbiosis; a pre-requisite for agricultural application of a novel crop symbiosis.
We found that FR light and sporophyte density were main initiators of sexual reproduction while nitrogen availiblity was an inhibitor.
Several _Azolla_ specimens collected all over the Netherlands produced viable offspring.
FR-responsive transcripts included MIKCC homologues of CMADS1 and miR319-controlled GAMYB transcription factors in the fern, transporters in _N. azollae_, and ycf2 in chloroplasts.
Phylogenomic analyses of MIKCC transcription factors suggested that control of flowering and flower organ specification may have originated from the diploid to haploid phase transition in the homosporous common ancestor of ferns and seed plants.

Sexual reproduction of the symbiosis requires that the symbiont is systematically stored in dissemination stages to reinnoculate the next generation of hosts.
Contrasting earlier theories, we propose that _N. azollae_ does not colonise developing megasporocarps travelling from leaf pockets to megasporocarps via small channels.
Instead, we theorise that they colonise early sporocarp initials, but are only retained in megasporocarps.
This method of transmission is identical to colonisation of leaf primordia, hence requires no separate machinery and explains consistent observation of _N. azollae_ in very young microsporocarps.

In __chapter \ref{phylogeny workflow}__ (\nameref{phylogeny workflow} on page \pageref{phylogeny workflow}) describes a workflow for creating large and state-of-the-art phylogentic trees of gene families in landplants.
Studying fern genetics, the _Azolla_ lab often deals with fern genes homologous (similar in sequence) to a seedplant gene.
With phylogeny, we aim to assess the evolution of a gene family and orthology/paralogy of _Azolla_ genes to model species their genes.
While many user friendly methods exist to create phylogenetic trees, these are often either closed-source, or their performance is limited.
Here I created a workflow for basic phylogeny inference with state-of-the-art tools, unlimitted in their performance.
This workflow is aimed at user skilled in reading a phylogeny, but not in using the CML tools to use the latest software to build them.
It covers data-selection, Multiple Sequences Alignment, Alignment trimming, and tree inference.
Additionally, it provides tools to create semi-automatic mark-up for phylogenetic trees in the iToL webinterface.
