\pagestyle{chapter}
\singlespacing
\setlength{\parindent}{0.0in}
\addthumb{Chapter \thechapter}{\Large{\thechapter}}{white}{gray}

\chapter{Forever together: One \emph{Nostoc azollae} is symbiont to all Azolla species}
\label{forever_together}

\footnotesize

Laura W Dijkhuizen^1^,
Michelle Verstraaten^1^,,
Henriette Schluepmann^1^.

\scriptsize

1. Molecular Plant Physiology Department, Utrecht University, Utrecht 3584CH, The Netherlands

\newpage
\resetlinenumber
\linenumbers
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

<!-- have a mini table of contents -->
\minitoc

\section*{Abstract}

this is where the abstract goes

\newpage

# Introduction

<!-- 
1: 
mitochondrial genome for filiculoides
all cyanobiont genomes
This was a bit of a manual search, hence it's a result.

2: All N. azollae are the same


 -->

*Azolla* is a genus of aquatic ferns.
_Azolla_ forms a symbiotic relationship with the cyanobacterium *Trichormus azollae*, which resides within specialised leaf cavities [@Campbell1893].
All _Azolla_ species have a symbiosis with _T. azollae_, but other ferns in the Salviniaceae family do not.
*T. azollae* fixes atmospheric nitrogen, providing a vital nutrient to its host, while *Azolla* offers a protective environment and presumably access to photosynthetic products and other nutrients [@Ran2010].
The naming of the cyanobacterial symbiont has been subject to change.
Here I use _T. azollae_, as I explain in the general introduction of this thesis on page \pageref{t_azollae_debate}.

The *Azolla*-*Nostoc* symbiosis is unique due to its mode of transmission.
Most plant-microbe associations are acquired horizontally from the environment.
Contrastingly, *T. azollae* is vertically transmitted across generations of *Azolla* inside reproductive structures known as megasporocarps [@Perkins1993; @Zheng2009].
This strict vertical transmission ensures that each new generation of *Azolla* is pre-inoculated with its symbiotic cyanobacterium, maintaining the partnership across evolutionary timescales.
_T azollae_ DNA is as strictly inherited as plastid DNA.

High genetic similarity across *T. azollae* strains found in different *Azolla* species suggests a single evolutionary origin of this symbiosis [@Dijkhuizen2021].
Some studies theorised multiple Cyanobacteria are part of the symbiosis [@Papaefthimiou2008], but in Chapter \ref{hidden_treasures} we found this to not be the case.
Alternatively, some cyanobacteria may be closely associated with _Azolla_ externally [@Pratte2021].

The relationship between *Azolla* and *T. azollae* has evolved under selective pressures that have shaped the genome of the cyanobiont [@Ran2010].
_T azollae_'s life cycle is tightly integrated with and adapted to that of its host fern [@Zheng2009].
The genome of *T. azollae* has undergone significant reductive evolution, characterised by a high number of pseudogenes and the presence of numerous insertion sequences (IS elements) [@Ran2010].
This genome reduction is indicative of *T. azollae*’s adaptation to an obligate symbiotic lifestyle [@Ran2010;@Warshan2018].
For many functions necessary for free-living cyanobacteria have been lost, relying instead on the host plant for certain metabolic needs.
Similar patterns of genome degradation are observed in other obligate symbionts [@Keeling2010; @Wernegreen2002].
Additionally, certain are enriched in to symbiotic cyanobacteria like transport, chemotaxis and nutrient uptake [@Warshan2018].

Recent genomic studies have sought to unravel the complexities of this symbiosis by examining the genomes of *Azolla* and its associated microbial community.
Advances in sequencing technologies have allowed researchers to not only sequence the genome of *T. azollae* but also to explore the broader metagenomic context of *Azolla*’s microbiome [@Li2018; @Dijkhuizen2018].
In particular, efforts have been made to reconstruct microbial genomes from publicly available sequencing data, highlighting the diverse bacterial communities that coexist with *T. azollae* within the *Azolla* holobiont (Chapter \ref{hidden_treasures}) [@Dijkhuizen2018; @Banach2019].
This broader view of the *Azolla* microbiome provides insights into how various microbial partners might contribute to the overall functionality of the symbiosis.

This chapter aims to extend our understanding of the *Azolla*-*Nostoc* symbiosis by exploring the genetic diversity and evolutionary history of *T. azollae* across different *Azolla* species.
We compare the diversity and evolution of the symbiont, to that of the ferns plastids.

Not all cyanobiont or plastid genomes are publicly available.
So here we gather and supplement data of _T. azollae_ and _Azolla_ plasmids associated with the _Azolla_ genus and study their evolution in context of other cyanobacterial symbioses.
We add long-read data to further resolve the structure of the fragmented _T. azollae_ genome assembly associated with _A. filiculoides_ as sequenced in chapter \ref{hidden_treasures}.
We also add long read data of _A. pinnata_, the only Azolla species that has not been sequenced yet.
Finally, we add sequencing data of an Azolla strain of unknown taxonomy to us namded Bordeaux after its sampling location.

With this data on _T. azollae_ and the _Azolla_ genus plastids, we describe the genomic variety of the main symbiont and its co-evolution with its host.
We assess the degradation that _T. azollae_ underwent in becoming a obligate symbiont, how this degradation diversified in the various host species, and we attempt to time degradation in the _T. azollae_ phylogeny.
Finally, we aim to embed the _T. azollae_ evolution in a broader perspective of Nostocales taxonomy, hopefully solving the issue of the _T. azollae_ genus name.
Within this broader perspective of Nostocales genomes, some symbiotic, some not, we hope to identify clusters of genes shared by symbiotic Nostocales Cyanobacteria and perhaps shared by T. azollae specifically.

Through this analysis, we aim to understand better the genomic and evolutionary dynamics that underlie the *Azolla*-*Nostoc* symbiosis, shedding light on the processes that govern symbiotic interactions and the co-evolution of plants and their microbial partners.
By doing so, we hope to contribute to a deeper understanding of the role of obligate cyanobacterial symbiosis in plant evolution.
_Azolla_-_Trichormus_ understanding may positively impact future _Azolla_-based agriculture and biotechnology.

# Methods

## Data Collection and Sequencing

We collected samples from three *Azolla* species: *A. filiculoides*, *A. pinnata*, and an unknown *Azolla* strain named 'Bordeaux.'
Genomic DNA was extracted from whole plant fronds using the nanopore community protocol.
Samples were sequenced using nanopore long-read sequencing technology, and data were basecalled with Guppy software.
Sequencing data was uploaded to EBI ENA under accession `EBI accession`.

## read baiting
Baited reads, selected based on homology to known reference genomes, were used to reduce assembly size and possibly enhance accuracy.
Nanopore sequencing reads were by mapping against this reference a with minimap2 [@Li2018a] and samtools [@Li2009] and then assembled with flye [@Kolmogorov2019].

## Genome Assembly

Long-read sequencing data were processed using de novo assembly techniques.
We utilised Flye for genome assembly, focusing on reconstructing chromosome-length assemblies of *Nostoc azollae* genomes and *Azolla* chloroplast and mitochondrial genomes.

Anvio pangenomics
IQtree

R & ggplot2

Mauve

Github

## nanopore sequencing
flowcells,
postprocessing

## data
table on the mags we have from chapter \ref{hidden treasures}

read data, same as chap3, but skipping Afiliculoides since that is the reference already.
When multiple samples are available, taking the longest insert size.

# Results

## De novo assembly of missing _T. azollae_ strains and _Azolla_ plastids.

We aim to to perform comparative genomes and study co-evolution of _T. azollae_ and its host via host plasmids.
To achieve this, we must first acquire all _T. azollae_ and _Azolla_ plastid genomes that are not available publicly yet.
These genomes were assembled either from public _Azolla_ sequencing data, or newly acquired nanopore data with assemblers appropriate for either a bacterial or plastid genomes and the right data type (+@fig:fig4_assembly_stats).

![Assembly statistics of all newly acquired cyanobiont and plastid genomes.](source/figures/fig4_chloroplast_nanopore_assemblies.pdf){#fig:fig4_assembly_stats short-caption="Assembly statistics of all newly acquired cyanobiont and plastid genomes."}

### _T.azollae_ genomes

The nanopore sequencing and assembly protocol was new to the lab so we sought some measure of verification.
As a first experiment, nanopore sequencing was used to assemble chromosome length assemblies of _T. azollae_ taken the from the _A. filiculoides_ Galgenwaard strain.
Sequencing produced sufficient reads of sufficient length to proceed with assembly (+@fig:fig4_assembly_stats; Sequencing input and read N50).
This initial nanopore assembly produced a perfect round assembly with two plasmids for the _A. filiculoides_ strain of the cyanobiont (+fig:fig4_Nazollae_nanopore_assemblies; _Azolla filiculoides_ 'lab').
Succesfull sequencing and assembly established the sequencing and assembly protocol in our lab.

Armed with a working protocol, we sequenced _A. pinnata_; the one _Azolla_ species that has not been subjected to whole genome sequencing yet..
_A pinnata_ is the only _Azolla_ species that has not been sequenced yet, and it is relatively far removed from _A. filiculoides_ in the _Azolla_ genus phylogeny (+@fig:fig3_data_overview).
The same protocol was applied to an _Azolla_ strain indicated as 'Bordeaux', and another indicated as 'Anzali'.
Both are named after their sampling location in France and Iran respectively.
However, the 'Anzali' strains DNA extractions and library preparations were unsuccessful.
Presumably, secondary metabolites in this particular strain inhibit one of the molecular steps in the protocols.
Sequencing did succeed for _A. pinnata_ and to a lesser extent for _A sp._ Bordeaux (+@fig:fig4_assembly_stats; Sequencing input and read N50).

_T. azollae_ reads from the _A. pinnata_ and _A. sp._ 'Bordeaux were baited and assembled.
The _A pinnata_ assembly turned out high quality and single chromosome in addition to some fragmented plasmids.
The _A. sp._ Bordeax assembly turned out highly fragmented and low quality due to low sequencing depth. (+fig:fig4_Nazollae_nanopore_assemblies).

![Assembly summary of _T. azollae_ flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_Nazollae_nanopore_assemblies.pdf){#fig:fig4_Nazollae_nanopore_assemblies short-caption="Graphical assembly summary of Flye assemblies"}

### The _Azolla_ chloroplast

### The Azolla mitochondrium

Azolla's mitochondrial sequence remains unknown despite the _A. filiculoides_ chloroplast reference genome being available at fernbase [@Li2018] and the _T. azollae_ genome being published by @Ran2010.
Baiting mitochondrium DNA reads of all _Azolla_ species requires a mitochodrium draft genome.
The mitochodrium genome sequence is likely assembled in bulk DNA assemblies from previous studies.
It did however, not appear in the metagenome analysis of chapter \ref{hidden_treasures}, hence we start looking for it in the latest _A. filiculoides_ genome assembly.

The persuit of the mitochondrial genome started with the _A filiculoides_ genome assembly version 2 [@gungur2022].
We alligned _A.filiculoides_ Illumina reads to it [@Li2018] and performed metagenomic binning on this assembly with metabat2 `cite metabat2`.
Contigs of these bins were mapped with blastn to known fern mitochondrial genomes of _Ophioglossum californicum_ and _Psilotum nudum_ `ref`.
One bin stood out in particular but was many times the expected size of a mitochondrium: near 4.2M instead of between 400kb and 300kb.
Contigs of this bin were highly redudant, and the bin likely contained various configurations of the mitochondrial genome.

Since assembly of PacBio RSII reads with canu had been unsuccessful in resolving the mitochodrium structure, we opted to use the newly acquired nanopore reads of _A. filiculoides_.
The bin was subsetted based on blastn bitscores to _O californicum_ and _P nudum_ mitochondrial genomes, and this subset was used to bait nanopore reads.
These nanopore reads were then assembled with flye [@Kolmogorov2019] and the assembly graph was inspected in Bandage `cite bandage`.
The assembly totalled at 3.2Mbase, and contained various subgraphs that showed homology to _T. azollae_ and the _A. filiculoides_ chloroplast.
One circular subgraph showed homology to the _O californicum_ and _P nudum_ mitochondria (+@fig:fig4_mitochondrium_assembly_selection A).
This mitochodrium subgraph contained 188kb of DNA, more than half in a single contig.
Smaller redundant contigs were idintified via blast all-vs-all (+@fig:fig4_mitochondrium_assembly_selection B) and then removed.
Six contigs remained with minimal redundancy (+@fig:fig4_mitochondrium_assembly_selection C), together constituting the first draft genome of an _Azolla_ mitochondrium of 141kb in total.
The mitochondria assembly was polished twice with pilon using Illumina reads of the same _Azolla filiculoides_ lab strain, and then annotated using the chlorobox online interface `chlorobox`.


flye

These de-novo assemblies were then examined in Bandage `bandage` for homology to their reference.
The amount of DNA per genome differed substantially in the bulk nanopore library.
_T. azollae_ sequencing was the most abundant, ranging between 65Mbase and 2.7Gbase (+@fig:fig4_assembly_stats; Sequencing input; _T. azollae_).
Chloroplast DNA was the second most abundant, ranging between 24 and 240Mbase (+@fig:fig4_assembly_stats; Sequencing input; chloroplast) but still amounting to over 100x coverage over the short genome (+@fig:fig4_assembly_stats; Coverage; chloroplast).
Mitochondrial DNA however, was very sparse in the DNA extraction ranging between ,3 and 3Mbase (+@fig:fig4_assembly_stats; Sequencing input; mitochondrium), ammounting to no more than 1.5% compared to the _T. azollae_ and nomore than 10x Coverage (+@fig:fig4_assembly_stats; Coverage; mitochondrium).
Nanopore reads had an N50 between 7 and 13kb, except for the _A. sp._ 'Bordeaux' sample.
These long reads wil aid in resolving the fragmented assemblies as seen in chapter \ref{hidden_treasures}.

insert table with
* strain
* Nanopore sequencing yield
* Nazollae/chlorplast/mito
* Assembly Contigs
* length
* N50
* hits to reference
* coverage min,mean,max?

Next, we assemble the _Azolla_ chloroplast and mitochondrium genomes from nanopore data.
The _A. filiculoides_ chloroplast reference sequence was taken from fernbase.
Chloroplasts of other _Azolla_ species were assembled by @Li2018 for comparative phylogenomics of fern and _T. azollae_, but these are not publicly available.
Therefore, we set out to assemble these de-novo with nanopore first, and then with Illumina reads.
Nanopore reads were processed as for _T. azollae_.
Chloroplast nanopore assemblies were resolved to no more than 9 fragments, and to chromosome scale only in the case of _A. sp._ 'Bordeaux' (+@fig:fig4_assembly_stats; chloroplast ; Assembled contig count & Assembled N50).
Despite being fragmented, these assembly graphs were circular and have a size approximate to that of the reference.
This indicates some repetitive regions are not resolved propperly in the assembly process, but the draft genomes are most likely complete (+@fig:fig4_chloroplast_nanopore_assemblies).
Nanopore read coverage exceeds any minimum threshold for trusting these assemblies (+@fig:fig4_assembly_stats; chloroplast; Coverage).
Mitochondrium nanopore assemblies are troubled by very limited data input and hence insufficient coverage for assembly (+@fig:fig4_assembly_stats; mitochondrium; Sequencing input & Coverage).
Still, nanopore assemblies of the mitochondrial genome are resolved to no more than 8 contigs (+@fig:fig4_assembly_stats; mitochondrium; Assembled contig count) although these are not interconnected (+@fig:fig4_mitochondrium_nanopore_assemblies).
The low coverage and noisy character of nanopore reads suggests that these assemblies may contain a substantial amount of errors.
We assess the chloroplast assemblies as sufficient and proceed to assemble Illumina assemblies as well.
In the process, we will also attempt to assemble the mitochondrial genome from Illumina data and compare it to the nanopore assembled mitochondrial genomes.

In the final genome assembly effort, we attempt to assemble the plastids' genomes from Illumina data.
Plastid Illumina reads were baited in a similar fashion as the nanopore reads but using BWA [@Li2009a] rather than minimap2 and then assembled with SPAdes [@Nurk2017].
De-novo assemblies of plastids turned out to be highly fragmented and too big compared to the reference, even when reference sequences were taken into account during assembly using the SPAdes `--trusted-contigs` option (+@fig:fig4_chloroplast_spades_assemblies).
The de-novo SPAdes algorithm seemed to be too cautious in collapsing similar contigs into one, and hence created bubbles in the assembly graph.
The resulting fragmented assembly contains gene fragments and duplicates and hence is unsuited for phylogenomic analyses as we aim to perform here.
SPAdes assemblies of the mitochondrium were plagued by similar issues (data not shown).
Hence, we resorted to an alternative method for assembling plastid genomes: NOVOplasty `NOVOplasty`.
NOVOplasty is not a graph assembler but itteratively extends a seed sequence known to be from a plastid; a Rubisco DNA sequence in the case of the chloroplast.
It does not rely on baiting reads, but can work with bulk DNA from a WGS project.
This method resulted in chloroplast assemblies of appropriate length for all _Azolla_ species included here (+@fig:fig4_assembly_stats; chloroplast; Assembled length) and the majority of these assemblies was contained within a single contig in all cases (+@fig:fig4_assembly_stats; chloroplast; Assembled N50).
Two novoplasty chloroplast assemblies were succesfully circularised, namely: _A. caroliniana_ '2' and _A. rubra_.
Mitochondrial assembly proved to more elusive however.
A seed sequence for maturase K (MatK) yieded in assemblies shorter than 1kb (data not shown).
An alternative seed sequence was found in cox1, taken directly from the draft mitochondrial genome assembly of _A. filiculoides_.
Using this seed sequence, assemblies were acquired with similar lengths as the nanopore mitchondrium reference, except for _A. nilotica_ (+@fig:fig4_assembly_stats; mitochondrium; Assembled length).
The assembly sizes remained stable even when the expected genome size was increased in NOVOplasty settings.
This indicates that likely the _A. filiculoides_ mitochodrium sequence is substantially shorter than that of _P nudum_ and _O californicum_.
The mitochondrium Illumina assemblies are still quite fragmented compared to their nanopore counterparts (+@fig:fig4_assembly_stats; mitochondrium; Assembled contig count & Assembled N50).
Overall, the chloroplast assemblies of nanopore and Illumina origin are of high quality, near complete and suitable for futher analyses.
The mitochodrium genomes assembled here are likely incomplete and fragmented.
Still, these are the very first Azolla mitochondrial draft genomes now publicly available.

insert table with Illumina assembly stats
* strain
* Nazollae/chlorplast/mito
* Illumina read pairs
* Assembly Contigs
* length
* (N50)
* hits to reference
* coverage min,mean,max?

## All _T. azollae_ are highly similar in terms of ANI and gene content but have some unique features

<!-- 
The original genome assembly of _T. azollae_ from _A. filiculoides_ was based on 454 sequencing data and was assembled with CAP5 [@Ran2010].
In previous attempts we failed to assemble a closed _T. azollae_ genome with this data, or with illumina data with various fragment lengths. 
-->

Armed with _T. azollae_ of all known _Azolla_ strains, we wonder how similar these genomes are in gene content, and if they can be considered separate species or if they are the same.
All available _T. azollae_ genomes and the reference from @Ran2010 were processed in an Anvi'o pangenomics workflow [GitHub page].
This workflow finds ORFs, tries to functionally annotate these via either NCBI COGs or KEGG KOFAMS, and then maps all ORFs to all ORFs with blastp to then cluster these genes in gene clusters that systematically co-occur in the various genomes.
Additionally, Average Nucleotide Identity (ANI) was determined over all regions of the entire genomes that mapped to each other.

![Pangenome summary of _Nostoc azollae_ strains representative of the entire _Azolla_ genus. _T. azollae_ genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. These barplots are log10 transformed due to high differences in copy numbers, the y-axes range from 0 to 100 copies. Outside the frequency barplots, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. ANI values in the heatmap range from 90% to 100%. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Nostoc_azollae_pangenome.pdf){#fig:fig4_Nazollae_pangenome short-caption="Pangenome summary of Nostoc azollae strains"}

All genomes of _T. azollae_ taken from various _Azolla_ hosts are highly similar both in ANI and in gene content but have some unique features. 
All genomes count similar amount of gene clusters except the Bordeaux strain.
The Euazolla section is very similar in ANI `over ...%` but both rhizosperma species are no more than `...%` similar to any other _T. azollae_.
Strictly speaking, this means that the _T. azollae_ from _A. pinnata_ and _A. nilotica_ are separate species from the _T. azollae_ in the Eukazolla section.
For the manuscript, we chose not do make this disctinction.
The Bordeaux strain genome assembly stands out for it misses many of the genes shared by other _T. azollae_.
These are likely missing due to the poor assembly quality, data input was minimal in this assembly and well below the recommended coverage for assembly with flye (10x vs 40x minimum).
Regardless, all genomes show low redundancy and high completion scores. 
A big majority of genes is shared amongst all T. azollae. (T. azollae core), not regarding any genes missing in the Bordeaux strain.
Within this core genome, a substantial amount of genes has functional annotation (ncbi COG or KEGG KOFAM). `count percentage`
Outside this group, the frequency of functional annotation is less. `count percentage`

![Pangenome summary of _Azolla_ chloroplasts. Chloroplast genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. These barplots their y-axes range from 0 to 4 copies. Outside the frequency barplots, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. ANI values in the heatmap range from 80% to 100%. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Azolla_chloroplast_pangenome.pdf){#fig:fig4_chloroplast_pangenome short-caption="Pangenome summary of Azolla chloroplasts"}

<!---
80%/90% fafa8e
100% 007872
--->

```
The same analysis is running over the weekend of the chloroplast and mitochondrium, trees should mirror. That will be the next results sub-section. Do these trees mirror.

![Comparative phylogenimcs on _Azolla_ associated _T. azollae and chloroplasts. Phylogenomic trees were infered on a manually selected set of single copy genes with good allignement scores in the pangenomc analyses (+@fig:fig4_Nazollae_pangenome) and +@fig:fig4_chloroplast_pangenome). Partitioned allignments were processed in IQtree, performing model selection and maximum likelihood tree inference. Matching host species are connected by green ribons; matching samples by blue ones. Inconsistencies in the speciation pattern are indicated by coloured circles.](source/figures/fig4_coevolution_trees.pdf){#fig:fig4_coevolution_trees short-caption="Comparative phylogenomics of Nostoc azollae and Azolla chloroplasts"}

**co-evolution**
* Wierd co-evolution tree in @Li2018. Let's do this again and assembly the chloroplasts anew. (and mito to get rid of that too...)

## genomics/synteny
whole genome alignment figure:

* Sync and scaffold assemblies to reference.
* How similar are they genomically
  * single introduction in Azolla genus
* Is the published structure correct, complete, and unchanged
  * Giulio's figure, yes the structure is unchanged but two plasmids are actually one.

**genomics/pseudogenes & transpons**

* which genes are functional in all species?
  * pseudogenation master table

About pseudogenes and transposons:

* Are pseudogenes shared?: shared transposons by Giulio
  * which genes are functional in all species?
  * pseudogenation master table

* When did the transposons move (shown in the tree)
  * tricky...
  * single introduction in Azolla genus and rapid degradation before Azolla speciations!

Transposon position is conserved and the symbiosis formed rapidly in the common ancestor of all Azolla species, after which evolution of the symbiont came to a standstill and the different azolla strains speciated.

```note
Likely to be skipped
**genomics Dual RNAseq data**
About genomics of a symbiont:
* RNAseq data, compared to gene models, expression data.
   - mRNAseq, gene expression from none-gene model regions?
   - sRNAseq,
     - CAS targetted phosphate transporter...?

**Other stuff:**
* Sufficient data for puryfying selection? Likely not.
* Crispr: lacking immunity in T. azollae -> plant must keep its house clean
```

**Evolution**

* Is the gene content of T. azollae special, symbiotic toolkit?
   - pangenomics multiple nostocs

* So much debate about which species it is, can we sovle that here?
  * phylogenomic tree nostoc, trichormus, anabaena.

```
Likely to be skipped:
**Morphology**
* encapsulating from the meristem colony --?
* pictures from Erbil

* Confocal images of Anna in which the microsporocarps lose the Cyano's
while the megasporocarps keep these.
  - both sporocarps gaining the Nostocs was published [@Perkins1993],
  but nog the losing part.
```

# Discussion

## Acquiring genomes

protocol is not robust yet. Plant DNA extraction remains a challenge, even within a genus results may vary.
But we do now have _T azollae_ genomes of alle species!


## bal bla bla

_Nostoc azollae_ main symbiont of _Azolla_
 * cap exchange experiments



Symbiosis co-evolution. How does _T. azollae_ compare to other known examples.
 * Exception in Li et al tree?
   - compare to chloroplast, how about mitochondrium?
 * Common introduction in the genus.


 * Symbiosis bottleneck, did this occur in _Azolla's_  main symbiont? At what stage in the symbiosis.

**Nostoc in the Azolla symbiosis**
T. azollae rappid introduction and degradation solidified its presence in the Azolla symbiosis.

* Co-evolution is ... awaiting trees ...
* T. azollae is basically one species, except for pinnata and nilotica, but what does that even mean...
* Pseudogenation has come to a standstill


beta-lactam antibiotic genes, rhizosperma may have different way of keeping their leafpocket clean and this is aided by T. azollae. Nazollae defends its niche?

DNA repair and maintainance enriched in rhizosperma --> diversified degradation bewteen rhizosperma and Eukazolla?

How does the symbiont remain stable

* bottleneck effect, Muellers ratchet?
  * might polyploidy be involved.

conservedness --> selection presure of presumable symbiosis important genes


**nostocales**
Embed in nostoc/trichormus/anabaena tree for more definitive placing.
Single introduction, this is a ... genus ...
Symbiotic gene kit

**future work**
is there restructuring in the resting stages of *Nostoc azollae*

```note
skipped
* Do we find more expressed regions with the RNAseq data
   - We do, needs propper annotation.
```

\newpage
\null
\newpage
\null
\newpage

# Supplemental figures

![Assembly and subsetting of _A. filiculoides_ mitochodrium genome. (A) Flye assembly graph of nanopore reads suspected to be mitocondrial. The assembly graph visualisation was made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches colour coded by blast hits and connections between these contigs as grey transparent lines. Blast hits of the _Psilotum nudum_ and _Ophioglossum californicum_ mitocondrial genomes (orange and red), the _Azolla filiculoides_ chloroplast (green) and _Nostoc azollae_ (cyan blue) are indicated in the assembly graph. A mitocondrial subgraph (indicated in red square) was selected for futher processing. B Blast all-vs-all visualisation with circo's of the mitocondrial subgraph. Several contigs are fully represented in contig 11. (C) Mitocondrial draft assembly manually rid of redundancy. Blast all-vs-all visualisation with circos.](source/figures/fig4_mitochondrium_assembly_selection.pdf){#fig:fig4_mitochondrium_assembly_selection short-caption="Assembly of Azolla filiculoides mitochondrial genomes"}



![Assembly summary of chloroplast flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_chloroplast_nanopore_assemblies.pdf){#fig:fig4_chloroplast_nanopore_assemblies short-caption="Assembly summary of chloroplast flye assemblies"}

![Assembly summary of mitochondrium flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_mitochondrium_nanopore_assemblies.pdf){#fig:fig4_mitochondrium_nanopore_assemblies short-caption="Assembly summary of mitochondrium flye assemblies"}

![Assembly graphs of chloroplast SPAdes assemblies with baited Illumina reads. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Illumina reads of serveral _Azolla_ species were selected based on homology to the _Azolla_ filiculoides_ draft mitochondrium and assembled with SPAdes. These species are _A. nilotica_, _A. caroliniana_ 1 & 2, _A. microphylla_, _A. mexicana_ and _A. rubra_. Species names are indicated above snapshots of the assembly graph, as well as the total assembly size and amount of contigs.](source/figures/fig4_chloroplast_spades_assemblies.pdf){#fig:fig4_chloroplast_spades_assemblies short-caption="Assembly summary of T. azollae flye assemblies"}

![Pangenome summary of _Azolla_ mitochondria. Mitochondrial genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. Outside the frequency barplots, functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, genes per kb, Singleton gene clusters and total number of gene clusters.](source/figures/fig4_Azolla_mitochondrium_pangenome.pdf){#fig:fig4_mitochondrium_pangenome short-caption="Pangenome summary of Azolla mitochondria"}

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
