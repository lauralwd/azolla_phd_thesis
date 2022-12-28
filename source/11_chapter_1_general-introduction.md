\part{Chapters}
\setcounter{page}{1}
\pagenumbering{arabic}

\pagestyle{chapter}
\onehalfspacing
\setlength{\parindent}{0.5in}

\resetlinenumber
\linenumbers

\chapter{General introduction}
\label{introduction}

## Plant biology for the twentyfirst century
These days, scientists, -humanity itself- is challenged with the advent of climate change, dramatic global population growth, and major loss of rurable land.
The field of plant biology plays a particularly important role securing a sustainable and healty future for humanity on plant earth.
IPCC
IPCC
FAO

Challenges that plant biologist may tackle


Efforts include improving existing crops

Novel crops

### Azolla
Ferns of the genus _Azolla_ have several key advantages

_Nostoc azollae_ Nitrogen independence

## Establishing the genetics of a novel crop symbiosis

### Domestication

### Breeding arrearage

### Breeding a symbiosis

### Challenges of Azolla

#### framework
1. ~~Plant biology: Food, Novel crops, Azolla symbiosis
  - X challenges, solutions in novel crops
  - opportunities Azolla~~
2. ~~Genetics of a novel crop, breeding a Symbiosis
  - What questions need to be answered for novel crop
  - and for a symbiosis specifically
  - Challenges Azolla, fern life cycle, heterospory, nostocs~~
3. Bioinformatics and plant biology
  - The study of information in biological systems
  - Comparative genomics to speed-up breeding arrearage
  - Elucidating the plant's second genome:
4. Open science, share and re-use resources, how to bring a small field forward
  - share methods, data, workflows
  - Collaboration and outreach
  - Societial solutions vs. technology solutions
  - Teaching?
5. Key advances...

#### H framework
1. Why you are so motivated to study a symbiosis
2. In particular Azolla
3. You personal development in this field using bioinformatic approaches
4. One key development during the short time of your activity: How to document reproducibility in bio informatic studies


![Illustration of the _Azolla_ symbiosis life cycle by Erbil Güngör](source/figures/fig1_life-cycle.png){#fig:fig1_life-cycle width=100%}


\newpage
\null
\newpage
\null
\newpage


<!---
label sections with LaTeX:
`\label{hidden_treasures}`
or with markdown:
`{#sec:foul-play-in-the-pocket}`

Then referece to the full chapter name:
\nameref{hidden_treasures}

the specific page:
\pageref{hidden_treasures}

the chapter number:
\ref{hidden_treasures}

with markdown if the ref contains no spaces:
+@sec:hidden-treasures

and for a markdown label only markdown refs work:
+@sec:foul-play-in-the-pocket
--->
## Outline of this thesis.
__Chapter \ref{foul_play}__ (\nameref{foul_play} on page \pageref{foul_play}) details the initial discovery of prokaryotic DNA sequences in the _A. filiculoides_ genome assembly and includes the work that inspired this PhD project.
We identify near complete bacterial genomes in whole contigs of this assembly and study these further.
These bacteria are confirmed to be present in _A. filiculoides_ taken from the wild as well as from the lab.
The Non-cyanobacterial prokaryotes are confirmed to be associated with all _Azolla_ species for which WGS data is available.
They may be the same or very related microbes.
Finally, we study the metabolic pathways encoded within these genomes and hypothesise they might denitrify Nitrogen rich compounds within the _A. filiculoides_ leaf pocket.
This hypothesis is falsified however, denitrification occors only in microbes living epiphytically on _A. filiculoides_.

In __chapter \ref{hidden_treasures}__ (\nameref{hidden_treasures} on page \pageref{hidden_treasures}), I build further on the work of chapter \ref{foul_play}.
This chapter details a workflow to enrich and study the genomes of bacteria associated with all sequenced _Azolla_ species.
The workflow thoroughly removes plant DNA reads, and then assembles those of the remaining microbes.
The process of separating disctint microbial genomes (binning) required extra binningsignals and manual curation for these were not part of the original experimental design.
Each respresented species of the _Azolla_ genus yielded between 12 and 22 associated bacterial genomes.
The majority of these genomes belong only to six taxonomical orders present in the majority of the entire _Azolla_ genus: Burkholderiales, Caulobacterales, Nevskiales, Nostocales, Rhizobiales and Sphingomonadales.
The systematic presence of these taxonomic groups suggests they be selected for in the _Azolla_ symbiosis and they may be vertically transfered over host generations as is the main symbiont _N. azollae_.

__Appendix \ref{metagenomics_practical}__ (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}) illustrates an educational practical based on these first two chapters.
I designed this practical to teach the basic metagenomics principles and techniques to Life Sciences students with minimal coding experience.
The practical introduces the Bash language and tries to learn the main concepts behind metagenomics through a hands-on approach.
It starts with a metagenome assembly, and guides the students through DNA mapping, binning, quality control, gene annotation and finally plotting of metabolic pathways.
Exercises are implemented in JuPyter notebooks, combining code-writing with text instructions.
The practical is freely available on GitHub here [github.com/lauralwd/metagenomicspractical](https://github.com/lauralwd/metagenomicspractical)

__Chapter \ref{forever_together}__ (\nameref{forever_together} on page \pageref{forever_together}) describes the genomics of the main _Azolla_ symbiont: _N. azollae_, using the genomes assembled in chapter \ref{hidden_treasures}.
All _N. azollae_ share near identical genomes and gene content, indicating they are the same species of _N. azollae_, hosted in various _Azolla_ species.
~~Their phylogeny confirms they have co-evolved with their hosts.~~
The _N. azollae_ genome is degraded due to high pseudogene content.
Pseudogenation is caused by high transposon activity early in the symbiosis, but has since then slowed down.
A _N. azollae_ specific gene set was identified comparing many near complete genomes in the Nostocales family.
A phylogenomics approach confirms that te organisation of genera in this family is paraphyletic, but places _N. azollae_ close to _Anabeana_ species.

__Chapter \ref{partners_and_passengers}__ (\nameref{partners_and_passengers} on page \pageref{partners_and_passengers}) is likely not going to happen...

__Chapter \ref{it_takes_two}__ (\nameref{it_takes_two} on page \pageref{it_takes_two}) provides building blocks for understanding and regulating the sexual reproduction and mode of transmission of the _Azolla_ & _N. azollae_ symbiosis.
Such understanding is a pre-requisite for agricultural application of a novel crop symbiosis.
Several _Azolla_ specimens collected all over the Netherlands were all the same species for they produced viable offspring.
We found that FR light and sporophyte density were main initiators of sexual reproduction while nitrogen availiblity was an inhibitor.
FR-responsive transcripts included MIKCC homologues of CMADS1 and miR319-controlled GAMYB transcription factors in the fern, transporters in _N. azollae_, and ycf2 in chloroplasts.
Phylogenomic analyses of MIKCC transcription factors suggested that control of flowering and flower organ specification may have originated from the diploid to haploid phase transition in the homosporous common ancestor of ferns and seed plants.

Sexual reproduction of the symbiosis requires that the symbiont is systematically stored in dissemination stages to reinnoculate the next generation of hosts.
Contrasting earlier theories, we propose that _N. azollae_ does not colonise developing megasporocarps travelling from leaf pockets to megasporocarps via small channels.
Instead, we theorise that they colonise early sporocarp initials of both typles, but are only retained in megasporocarps.
This method of transmission is identical to colonisation of leaf primordia, hence requires no separate machinery and explains consistent observation of _N. azollae_ in very young microsporocarps.

__Chapter \ref{phylogeny_workflow}__ (\nameref{phylogeny_workflow} on page \pageref{phylogeny_workflow}) describes a workflow for creating large and state-of-the-art phylogentic trees of gene families; examplified in landplants.
Studying fern genetics, the _Azolla_ lab often deals with fern genes that are homologous (similar in sequence) to a seedplant gene.
With phylogeny, we aim to assess the evolution of a gene family and orthology/paralogy of _Azolla_ genes to model species their genes.
While many user friendly methods exist to create phylogenetic trees, these are often either closed-source, or their performance is limited.
Here I created a workflow for basic phylogeny inference with state-of-the-art open source tools, unlimitted in their performance.
This workflow is aimed at user skilled in reading a phylogeny, but not in using the CML tools to use the latest software to build them.
It covers data-selection, multiple sequences alignment, alignment trimming, and tree inference.
Additionally, it provides tools to create semi-automatic mark-up for phylogenetic trees in the iToL webinterface.

### Appendeces
Academics are more than just scientitsts.
They are often also teachers on universities and leaders and administrators in academic organs.
During my PhD, I attempted to incorparate that broader academic experience in my work.
The doctorate remains intrinsically a scientific degree and this thesis is first and foremost a scientific document.
Still, I add three appendeces that give a glimpse in my "extracurricular" activities.
My thesis; the culmination of my PhD, simply would not be complete without them.

Firstly, __Appendix \ref{BKO}__ summarises my basic University Teaching Qualification (bUTQ or BKO) application.
About a quarter of My PhD I spend on teaching and developping myself as a Teacher.
This effort was rewarded with a bUTQ or BKO in Dutch.
The full portfolio is too lengthy to include, so this chapter sumarises the original document.
Secondly, an example of teaching material that is completely of my own design is included in __Appendix \ref{metagenomics_practical}__ (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}) as mentioned before.
Finally, I include a short narrative CV on my non-science and non-teaching activities during my PhD and what I gained from them.

\nolinenumbers
