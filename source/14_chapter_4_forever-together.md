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
*Azolla_ forms a symbiotic relationship with the cyanobacterium *Trichormus azollae*, which resides within specialised leaf cavities [@Campbell1893].
All *Azolla* species have a symbiosis with *T. azollae*, but other ferns in the Salviniaceae family do not.
*T. azollae* fixes atmospheric nitrogen, providing a vital nutrient to its host, while *Azolla* offers a protective environment and presumably access to photosynthetic products and other nutrients [@Ran2010].
The naming of the cyanobacterial symbiont has been subject to change.
Here I use *T. azollae*, as I explain in the general introduction of this thesis on page \pageref{t_azollae_debate}.

The *Azolla*-*Nostoc* symbiosis is unique due to its mode of transmission.
Most plant-microbe associations are acquired horizontally from the environment.
Contrastingly, *T. azollae* is vertically transmitted across generations of *Azolla* inside reproductive structures known as megasporocarps [@Perkins1993; @Zheng2009].
This strict vertical transmission ensures that each new generation of *Azolla* is pre-inoculated with its symbiotic cyanobacterium, maintaining the partnership across evolutionary timescales.
*T azollae* DNA is as strictly inherited as plastid DNA.

High genetic similarity across *T. azollae* strains found in different *Azolla* species suggests a single evolutionary origin of this symbiosis [@Dijkhuizen2021].
Some studies theorised multiple Cyanobacteria are part of the symbiosis [@Papaefthimiou2008], but in Chapter \ref{hidden_treasures} we found this to not be the case.
Alternatively, some cyanobacteria may be closely associated with *Azolla* externally [@Pratte2021].

The relationship between *Azolla* and *T. azollae* has evolved under selective pressures that have shaped the genome of the cyanobiont [@Ran2010].
*T azollae*'s life cycle is tightly integrated with and adapted to that of its host fern [@Zheng2009].
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
So here we gather and supplement data of *T. azollae* and *Azolla* plasmids associated with the *Azolla* genus and study their evolution in context of other cyanobacterial symbioses.
We add long-read data to further resolve the structure of the fragmented *T. azollae* genome assembly associated with *A. filiculoides* as sequenced in chapter \ref{hidden_treasures}.
We also add long read data of *A. pinnata*, the only Azolla species that has not been sequenced yet.
Finally, we add sequencing data of an Azolla strain of unknown taxonomy to us namded Bordeaux after its sampling location.

With this data on *T. azollae* and the *Azolla* genus plastids, we describe the genomic variety of the main symbiont and its co-evolution with its host.
We assess the degradation that *T. azollae* underwent in becoming a obligate symbiont, how this degradation diversified in the various host species, and we attempt to time degradation in the *T. azollae* phylogeny.
Finally, we aim to embed the *T. azollae* evolution in a broader perspective of Nostocales taxonomy, hopefully solving the issue of the *T. azollae* genus name.
Within this broader perspective of Nostocales genomes, some symbiotic, some not, we hope to identify clusters of genes shared by symbiotic Nostocales Cyanobacteria and perhaps shared by T. azollae specifically.

Through this analysis, we aim to understand better the genomic and evolutionary dynamics that underlie the *Azolla*-*Nostoc* symbiosis, shedding light on the processes that govern symbiotic interactions and the co-evolution of plants and their microbial partners.
By doing so, we hope to contribute to a deeper understanding of the role of obligate cyanobacterial symbiosis in plant evolution.
*Azolla*-*Trichormus* understanding may positively impact future *Azolla*-based agriculture and biotechnology.

<!-- 
section on plastids 
 - they can change their configuration.
 - 

-->

# Methods

## Data Collection and Sequencing

We collected samples from three *Azolla* species: *A. filiculoides*, *A. pinnata*, and an unknown *Azolla* strain named 'Bordeaux.'
Genomic DNA was extracted from whole plant fronds using the nanopore community protocol.
Samples were sequenced using nanopore long-read sequencing technology, and data were basecalled with Guppy software.
Sequencing data was uploaded to EBI ENA under accession `EBI accession`.

## read baiting

Baited reads, selected based on homology to known reference genomes, were used to reduce assembly size and possibly enhance accuracy.
Nanopore sequencing reads were by mapping against this reference a with minimap2 [@Li2018a] and samtools [@Li2009] and then assembled with flye [@Kolmogorov2019].

<!-- Plastid Illumina reads were baited in a similar fashion as the nanopore reads but using BWA [@Li2009a] rather than minimap2 and then assembled with SPAdes [@Nurk2017]. -->

## Genome Assembly

Long-read sequencing data were processed using de novo assembly techniques.
We utilised Flye for genome assembly, focusing on reconstructing chromosome-length assemblies of *Nostoc azollae* genomes and *Azolla* chloroplast and mitochondrial genomes.

Anvio pangenomics
IQtree

R & ggplot2

Mauve

Github

## novoplasty

De-novo assemblies of plastids turned out to be highly fragmented and too big compared to the reference, even when reference sequences were taken into account during assembly using the SPAdes `--trusted-contigs` option (+@fig:fig4_chloroplast_spades_assemblies).
The de-novo SPAdes algorithm seemed to be too cautious in collapsing similar contigs into one, and hence created bubbles in the assembly graph.
The resulting fragmented assembly contains gene fragments and duplicates and hence is unsuited for phylogenomic analyses as we aim to perform here.
SPAdes assemblies of the mitochondrium were plagued by similar issues (data not shown).
Hence, we resorted to an alternative method for assembling plastid genomes: NOVOplasty `NOVOplasty`.
NOVOplasty is not a graph assembler but itteratively extends a seed sequence known to be from a plastid; a Rubisco DNA sequence in the case of the chloroplast.
It does not rely on baiting reads, but can work with bulk DNA from a WGS project.

## nanopore sequencing

flowcells,
postprocessing

## data

table on the mags we have from chapter \ref{hidden treasures}

read data, same as chap3, but skipping Afiliculoides since that is the reference already.
When multiple samples are available, taking the longest insert size.

# Results

## De novo assembly of missing *T. azollae* strains and *Azolla* plastids.

We aim to to perform comparative genomes and study co-evolution of *T. azollae* and its host via host plasmids.
To achieve this, we must first acquire all *T. azollae* and *Azolla* plastid genomes that are not available publicly yet.
These genomes were assembled either from public *Azolla* sequencing data, or newly acquired nanopore data with assemblers appropriate for either a bacterial or plastid genomes and the right data type (+@fig:fig4_assembly_stats).

![Assembly statistics of all newly acquired cyanobiont and plastid genomes.](source/figures/fig4_assembly_stats.pdf){#fig:fig4_assembly_stats short-caption="Assembly statistics of all newly acquired cyanobiont and plastid genomes."}

### *T.azollae* genomes

As a first experiment, nanopore sequencing was used to assemble chromosome length assemblies of *T. azollae* taken the from the *A. filiculoides* Galgenwaard strain.
The original genome assembly of *T. azollae* from *A. filiculoides* was based on 454 sequencing data and was assembled with CAP5 [@Ran2010].
CAP5 was a pioneering program, but is known to handle repetition poorly; hence we sought to confirm the original *T azollae* genome assembly.
In previous attempts we failed to assemble a closed *T. azollae* genome with the original 454 data, or with illumina data with various fragment lengths (+@fig:fig4_assembly_stats; *Nostoc azollae*).
These assemblies were scattered of thousands of contigs.

The nanopore sequencing and assembly protocol was new to the lab so this experiment also served as a proof of concept of the technique in our hands.
Sequencing produced sufficient reads of sufficient length after baiting to proceed with assembly (+@fig:fig4_assembly_stats; Sequencing input and read N50).
This initial nanopore assembly produced a perfect round assembly with two plasmids for the *A. filiculoides* strain of the cyanobiont (+@fig:fig4_Nazollae_nanopore_assemblies; *Azolla filiculoides* 'lab').
Successful sequencing and assembly established the sequencing and assembly protocol in our lab.

Armed with a working protocol, we sequenced *A. pinnata*.
*A. pinnata* is the only *Azolla* species that has not been sequenced yet, and it is relatively far removed from *A. filiculoides* in the *Azolla* genus phylogeny (+@fig:fig3_data_overview).
The same protocol was applied to an *Azolla* strain indicated as 'Bordeaux', and another indicated as 'Anzali'.
Both are named after their sampling location in France and Iran respectively.
However, the 'Anzali' strains DNA extractions and library preparations were unsuccessful.
Presumably, secondary metabolites in this particular strain inhibit one of the molecular steps in the protocols.
Sequencing did succeed for *A. pinnata* and to a lesser extent for *A sp.* Bordeaux (+@fig:fig4_assembly_stats; Sequencing input and read N50).

*T. azollae* reads from the *A. pinnata* and *A. sp.* 'Bordeaux were baited and assembled.
The *A pinnata* assembly turned out high quality and single chromosome in addition to some fragmented plasmids.
The *A. sp.* Bordeax assembly turned out highly fragmented and low quality due to low sequencing depth. (+@fig:fig4_Nazollae_nanopore_assemblies).
With a complete collection of *Azolla* cyanobionts, we turn to the *Azolla* chloroplasts.

![Assembly summary of *T. azollae* flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_Nazollae_nanopore_assemblies.pdf){#fig:fig4_Nazollae_nanopore_assemblies short-caption="Graphical assembly summary of Flye assemblies"}

### The *Azolla* chloroplast

The *A. filiculoides* chloroplast reference genome is available at fernbase [@Li2018], and allows for baiting chloroplast reads of other *Azolla* species.
Chloroplasts of other *Azolla* species were also assembled by @Li2018 for comparative phylogenomics of fern and *T. azollae*, but we could not find these in the repositories.
First assembly attempts with SPAdes were not up to standard (+@fig:fig4_chloroplast_spades_assemblies), hence we proceeded with a plastid specific assembler: NOVOPlasty.
<!-- [CITE novoplasty] -->
This method resulted in chloroplast assemblies of appropriate length for all *Azolla* species included here (+@fig:fig4_assembly_stats; chloroplast; Assembled length) and the majority of these assemblies was contained within a single contig in all cases (+@fig:fig4_assembly_stats; chloroplast; Assembled N50).
Two novoplasty chloroplast assemblies were succesfully circularised, namely: *A. caroliniana* '2' and *A. rubra*.

For nanopore data, we used Flye as for the *T. azollae* genomes.
Assembly sizes were very similar for the entire genus with a median contig count of 3 and size of approximately 150kb (+@fig:fig4_assembly_stats; chloroplast) similar to the reference [@Li2018].
The assembly structure is rarely resolved to a single contig.
Instead the structure is resolved to a shape similar to two loops connected by a stick (+@fig:fig_chloroplast_nanopore_assemblies; +fig:fig4_chloroplast_spades_assemblies).
The actual chloroplast genome structure may be variable.
With all chloroplast and cyanobiont genomes, we finally set our sights to the *Azolla* mitochondrial genomes.

![Assembly summary of chloroplast flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_chloroplast_nanopore_assemblies.pdf){#fig:fig4_chloroplast_nanopore_assemblies short-caption="Graphic assembly summary of chloroplast flye assemblies"}

### The Azolla mitochondrium

Azolla's mitochondrial sequence remains unknown despite the *A. filiculoides* chloroplast reference genome being available at fernbase [@Li2018] and the *T. azollae* genome being published by @Ran2010.
This prevents us from baiting mitochondrium DNA reads of all *Azolla* species, since this requires a mitochodrium draft genome.
Yet, the mitochodrium genome sequence is likely assembled in some form in previous bulk DNA assemblies.
It did however, not appear in the metagenome analysis of chapter \ref{hidden_treasures}, hence we start looking for it in the latest *A. filiculoides* genome assembly.

Our pursuit of the mitochondrial genome started with the *A filiculoides* genome assembly version 2 [@gungur2022].
A newly made assembly of the PacBio RSII reads from @Li2018.
We aligned *A.filiculoides* Illumina reads to it and performed metagenomic binning on this assembly with metabat2 `cite metabat2`.
Contigs of these bins were mapped with blastn to known fern mitochondrial genomes of *Ophioglossum californicum* and *Psilotum nudum* `ref`.
One bin stood out in particular.
However, its size was many times the expected size of a mitochondrium: near 4.2M instead of between 400kb and 300kb.
When mapping the contigs to each other, they proved to be highly redudant (results not shown).
The bin likely contained various configurations of the mitochondrial genome.

Since assembly of PacBio RSII reads with canu had been unsuccessful in resolving the mitochodrium structure, we opted to use the newly acquired nanopore reads of *A. filiculoides*.
The bin was subsetted based on blastn bitscores to *O californicum* and *P nudum* mitochondrial genomes.
This subset was used to bait nanopore reads.
These nanopore reads were then assembled with flye [@Kolmogorov2019] and the assembly graph was inspected in Bandage `cite bandage`.
The assembly totalled at 3.2Mbase, and contained various subgraphs that showed homology to *T. azollae* and the *A. filiculoides* chloroplast.
One circular subgraph showed homology to the *O californicum* and *P nudum* mitochondria (+@fig:fig4_mitochondrium_assembly_selection A).
This mitochodrium subgraph contained 188kb of DNA, more than half in a single contig.
Smaller redundant contigs were identified via blast all-vs-all (+@fig:fig4_mitochondrium_assembly_selection B) and then removed.
Six contigs remained with minimal redundancy (+@fig:fig4_mitochondrium_assembly_selection C), together constituting the first draft genome of an *Azolla* mitochondrium of 141kb in total.
The mitochondria assembly was polished twice with pilon using Illumina reads of the same *Azolla filiculoides* lab strain, and then annotated using the chlorobox online interface `chlorobox`.

![Assembly and subsetting of *A. filiculoides* mitochodrium genome. (A) Flye assembly graph of nanopore reads suspected to be mitocondrial. The assembly graph visualisation was made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches colour coded by blast hits and connections between these contigs as grey transparent lines. Blast hits of the *Psilotum nudum* and *Ophioglossum californicum* mitocondrial genomes (orange and red), the *Azolla filiculoides* chloroplast (green) and *Nostoc azollae* (cyan blue) are indicated in the assembly graph. A mitocondrial subgraph (indicated in red square) was selected for futher processing. B Blast all-vs-all visualisation with circo's of the mitocondrial subgraph. Several contigs are fully represented in contig 11. (C) Mitocondrial draft assembly manually rid of redundancy. Blast all-vs-all visualisation with circos.](source/figures/fig4_mitochondrium_assembly_selection.pdf){#fig:fig4_mitochondrium_assembly_selection short-caption="Assembly of Azolla filiculoides mitochondrial genomes"}

With a first draft mitochondrial genome for *A. filiculoides*, we proceeded to gather the plastid genome for other *Azolla* species via the apropriate baiting methods.
Mitochondrial DNA however, was very sparse in all DNA extraction ranging between ,3 and 3Mbase (+@fig:fig4_assembly_stats; Sequencing input; mitochondrium).
The mitocondrial fractions thus amounts to no more than 1.5% compared to the *T. azollae* faction and nomore than 10x Coverage (+@fig:fig4_assembly_stats; Coverage; mitochondrium).
Nanopore experiments yielded more mitochondrial DNA reads with better N50 values between 7 and 13kb, except for the *A. sp.* 'Bordeaux' sample.
Despite the limited data input and consequential insufficient coverage for assembly, nanopore assemblies of the mitochondrial genome are resolved to no more than 8 contigs (+@fig:fig4_assembly_stats; mitochondrium).
However, these contigs are not interconnected (+@fig:fig4_mitochondrium_nanopore_assemblies).
More importantly, the low coverage and noisy character of nanopore reads suggests that these assemblies may contain a substantial amount of errors.

Mitochondrial genomes assembled from Illumina reads proved equeally ellusive.
The default NOVOPlasty algorithm uses the sequence of maturase K (MatK) to start the assembly.
These assemblies were unusable.
An alternative seed sequence was found in cox1, taken directly from the draft mitochondrial genome assembly of *A. filiculoides*.
Using this seed sequence, assemblies were acquired with similar lengths as the nanopore mitchondrium reference, except for *A. nilotica* (+@fig:fig4_assembly_stats; mitochondrium; Assembled length).
This indicates that likely the *A. filiculoides* mitochodrium sequence is substantially shorter than that of *P nudum* and *O californicum*.

The mitochondrium Illumina assemblies are still quite fragmented compared to their nanopore counterparts (+@fig:fig4_assembly_stats; mitochondrium; Assembled contig count & Assembled N50).
Overall, the chloroplast assemblies of nanopore and Illumina origin are of high quality, near complete and suitable for futher analyses.
The mitochodrium genomes assembled here are likely incomplete and fragmented.
Still, these are the very first Azolla mitochondrial draft genomes now publicly available.

## All *T. azollae* are extremely similar (but have some unique features)

Armed with *T. azollae* genomes of all known *Azolla* strains, we wonder how similar these genomes are in gene content, and if they can be considered separate species or if they are the same.
All available *T. azollae* genomes and the reference from @Ran2010 were processed in an Anvi'o pangenomics workflow [GitHub page].
This workflow finds ORFs, tries to functionally annotate these via either NCBI COGs or KEGG KOFAMS.
It then maps all ORFs to all ORFs with blastp and creates gene clusters of co-varying ORFs (@fig:fig4_Nostoc_azollae_pangenome).
Additionally, Average Nucleotide Identity (ANI) was determined over all regions of the entire genomes that mapped to each other.
All genomes show low redundancy and high completion scores except for the 'Bordeaux' strain.
A big majority of genes is shared amongst all *T. azollae*. (@fig:fig4_Nostoc_azollae_pangenome; core), not regarding any genes missing in the Bordeaux strain.
Within this core genome, a substantial amount of genes has functional annotation (@fig:fig4_Nostoc_azollae_pangenome; KOfam, KEGG, COG20).
Outside this group, the frequency of functional annotation is less.

![Pangenome summary of *Nostoc azollae* strains representative of the entire *Azolla* genus. *T. azollae* genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. These barplots are log10 transformed due to high differences in copy numbers, the y-axes range from 0 to 100 copies. Outside the frequency barplots, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. ANI values in the heatmap range from 90% to 100%. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Nostoc_azollae_pangenome.pdf){#fig:fig4_Nazollae_pangenome short-caption="Pangenome summary of *Trichormus azollae* strains"}

All genomes of *T. azollae* taken from various *Azolla* hosts are highly similar both in ANI and in gene content but have some unique features.
All genomes count similar amount of gene clusters except the Bordeaux strain, likely due to low assembly quality and completion.
The Euazolla section is very similar in ANI `over ...%` but both rhizosperma species are no more than `...%` similar to any other *T. azollae*.
Strictly speaking, this means that the *T. azollae* from *A. pinnata* and *A. nilotica* are separate species from the *T. azollae* in the Euazolla section.
This is consistent with these two speciations being relativelly old in the *Azolla* genus (@fig:fig3_data_overview; A)
For the manuscript, we chose not do reflect this disctinction in the nomenclature.
But one may consider adding subspecies indications, *T. azollae* subsp._ euazolla_, *T. azollae* subsp. *nilotica* and *T. azollae* subsp. *pinata*.

Some accessoiry gene sets can be identified, i.e. for the euazolla, rhizosperma, *Microphylla*+*Mexicana*, and *filiculoides*+*rubra*.
Enrichment analysis on these groups did not yield meaningful results, for these groups contain mostly genes of unknown function.
<!-- double check this -->

## *T. azollae* genome structure is identical for all species

Whole genome allignment figure

<!-- 
The original genome assembly of _T. azollae_ from _A. filiculoides_ was based on 454 sequencing data and was assembled with CAP5 [@Ran2010].
In previous attempts we failed to assemble a closed _T. azollae_ genome with this data, or with illumina data with various fragment lengths. 
-->

<!-- ### genomics/synteny
whole genome alignment figure:

* Sync and scaffold assemblies to reference.
* How similar are they genomically
  * single introduction in Azolla genus
* Is the published structure correct, complete, and unchanged
  * Giulio's figure, yes the structure is unchanged but two plasmids are actually one. 
  
-->


## *T. azollae* genome is most similar to anabaena genomes 

ANI of a bunch of Nostocaceae genomes place *T azollae* between anabaena genomes.
Returning to the original nomenclature?

![Average Nucleotide Idenity Heatmap of selected Nostocaceae species. This is a draft figure. The 6th and 7th column from the right are Nazollae, clustering with anabaena species (1st to 5th from the right. The "left" square is nostoc and the middle square is trichormus)](source/figures/fig4_nostocaceae_ANI_heatmap.pdf){#fig:fig4_nostocaceae_heatmap short-caption="Average Nucleotide Idenity Heatmap of selected Nostocaceae species."}

Do my own phylogenomics approach, perhaps ask Dani for some tips.

--> GoToTree approach with my mags and assemblies, and a GTDB background of nostocaceae.


## Host and cyanobiont phylogenies are reproducibly incongruent

Pangenome (dis)similarityWith the ANI clustering represents the nostoc tree.


![Pangenome summary of *Azolla* chloroplasts. Chloroplast genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. These barplots their y-axes range from 0 to 4 copies. Outside the frequency barplots, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. ANI values in the heatmap range from 80% to 100%. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Azolla_chloroplast_pangenome.pdf){#fig:fig4_chloroplast_pangenome short-caption="Pangenome summary of Azolla chloroplasts"}

<!---
80%/90% fafa8e
100% 007872
--->

Wierd co-evolution tree in @Li2018. 
@Metzgar2007 is also based on chloroplast markers.
chloroplast phylogeny mismatches with nostoc.

![Comparative phylogenomcs on *Azolla* associated *T. azollae* and chloroplasts. Phylogenomic trees were infered on a manually selected set of single copy genes with good allignement scores in the pangenomc analyses of *T.azollae* and the chloroplast genomes. Partitioned allignments were processed in IQtree, performing model selection and maximum likelihood tree inference. Matching host species are connected by green ribons; matching samples by blue ones. Inconsistencies in the speciation pattern are indicated by coloured circles.](source/figures/fig4_coevolution_trees.pdf){#fig:fig4_coevolution_trees short-caption="Comparative phylogenomics of *T azollae* and *Azolla* chloroplasts"}

## notes

### genomics/pseudogenes & transpons

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

<!--

**genomics Dual RNAseq data**
About genomics of a symbiont:
* RNAseq data, compared to gene models, expression data.
   - mRNAseq, gene expression from none-gene model regions?
   - sRNAseq,
     - CAS targetted phosphate transporter...?

**Other stuff:**
* Sufficient data for puryfying selection? Likely not.
* Crispr: lacking immunity in T. azollae -> plant must keep its house clean

**Evolution**

* Is the gene content of T. azollae special, symbiotic toolkit?
   - pangenomics multiple nostocs

* So much debate about which species it is, can we sovle that here?
  * phylogenomic tree nostoc, trichormus, anabaena.


**Morphology**
* encapsulating from the meristem colony --?
* pictures from Erbil

* Confocal images of Anna in which the microsporocarps lose the Cyano's
while the megasporocarps keep these.
  - both sporocarps gaining the Nostocs was published [@Perkins1993],
  but nog the losing part. 
  
  -->


# Discussion

## Acquiring genomes

DNA assembly has become easier but is still no trivial task.
Our efforts add to the publicly available collection of fern plastid and symbiont genomes.

protocol is not robust yet. Plant DNA extraction remains a challenge, even within a genus results may vary.
But we do now have *T azollae* genomes of alle species!

The actual chloroplast genome structure may be variable.

mitochondrial structure as well a variable structure?
Possibly with a special protocol or more nanopore sequencing a better genome can be retrieved.

## *T azollae* genome is near static since its introduction in the *Azolla* genus

Especially compared to microbes in general.
Challenges the idea of symbionts being a variable, interchangable section of a holobiont.

proportion of unknown genes is high, symbiosis specific genes maybe?

## co-evolution trees mismatch but ANI tree support coevolution tree (yes this is a horrible subtitle)

So the chloroplast phylogenies are systematically odd, placing *caroliniana* with *mexicana* and *microphylla*.
This was published by @Li2018 and @Metzgar2007 and reproduced by me.
All based on the chloroplast genome, via slightly different methods.
This indicates that there might have been symbiont or chloroplast transfer between ancestral *Azolla* species.

Alternativelly, there might be some corruption in the chloroplast phylogenetic signal.
The ANI dendrograms and heatmaps of the chloroplast and the cyanobiont do match.
Additionally, they match with the phylogeny of *T. azollae*.
Perhaps the phylogenetic signal from the chloroplast is not very good.
The node placing *A. caroliniana* with *A. mexicana* and *A. microphylla* does have relatively low support.
Another method would be to select certain marker genes from the plant genome, then de-novo assemble these for the other *Azolla* species, and use these for a phylogeny.
This effort is beyond the scope of this work, but could elucidate the topology of the *Azolla* phylogeny and the strictness of the symbiosis.


## bal bla bla

*Nostoc azollae* main symbiont of *Azolla*
 * cap exchange experiments



Symbiosis co-evolution. How does *T. azollae* compare to other known examples.
 * Exception in Li et al tree?
   - compare to chloroplast, how about mitochondrium?
 * Common introduction in the genus.


 * Symbiosis bottleneck, did this occur in *Azolla's*  main symbiont? At what stage in the symbiosis.

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

![Assembly summary of mitochondrium flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_mitochondrium_nanopore_assemblies.pdf){#fig:fig4_mitochondrium_nanopore_assemblies short-caption="Assembly summary of mitochondrium flye assemblies"}

![Assembly graphs of chloroplast SPAdes assemblies with baited Illumina reads. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Illumina reads of serveral *Azolla* species were selected based on homology to the *Azolla* filiculoides_ draft mitochondrium and assembled with SPAdes. These species are *A. nilotica*, *A. caroliniana* 1 & 2, *A. microphylla*, *A. mexicana* and *A. rubra*. Species names are indicated above snapshots of the assembly graph, as well as the total assembly size and amount of contigs.](source/figures/fig4_chloroplast_spades_assemblies.pdf){#fig:fig4_chloroplast_spades_assemblies short-caption="Graphic assembly summary of chloroplast SPAdes assemblies"}

![Pangenome summary of *Azolla* mitochondria. Mitochondrial genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. Outside the frequency barplots, functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, genes per kb, Singleton gene clusters and total number of gene clusters.](source/figures/fig4_Azolla_mitochondrium_pangenome.pdf){#fig:fig4_mitochondrium_pangenome short-caption="Pangenome summary of Azolla mitochondria"}

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
