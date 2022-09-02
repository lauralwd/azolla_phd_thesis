# Forever together: One nostoc azollae is symbiont to all Azolla species
\label{forever together}

\footnotesize

Laura W Dijkhuizen^1^,
Michelle Verstraaten^1^,,
Henriette Schluepmann^1^.

\scriptsize

1. Molecular Plant Physiology Department, Utrecht University, Utrecht 3584CH, The Netherlands

\newpage
\linenumbers
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

## Introduction
Cyanobacterial symbiosis in general.

_Nostoc azollae_ main symbiont of _Azolla_
 * Main symbiont, N-fixation.
 * present in All _Azolla_
 * cap exchange experiments
 * genus name debate

Symbiosis co-evolution. How does _N. azollae_ compare to other known examples.
 * very strict inheritance
 * Exception in Li et al tree?
   - compare to chloroplast, how about mitochondrium?
 * Common introduction in the genus.

_N. azollae_ was first sequenced by @Ran2010, taken from _Azolla filiculoides_.
 * Its genome is heavily degraded
 * Symbiosis bottleneck, did this occur in _Azolla's_  main symbiont? At what stage in the symbiosis.

Here we gather and supplement data of _N. azollae_ and _Azolla_ plasmids associated with the _Azolla_ genus and study their evolution.
We add long-read data to further resolve the structure of the fragmented _N. azollae_ genome assembly associated with _A. filiculoides_ as sequenced in chapter \ref{hidden treasures}.
We also add long read data of _A. pinnata_, the only Azolla species that has not been sequenced yet.
Finally, we add sequencing data of an Azolla strain of unknown taxonomy to us namded Bordeaux after its sampling location.
With this data on _N. azollae_ and the _Azolla_ genus plastids, we describe the genomic variety of the main symbiont and its co-evolution with its host.
We assess the degradation that _N. azollae_ underwent in becoming a obligate symbiont, how this degradation diversified in the various host species, and we attempt to time degradation in the _N. azollae_ phylogeny.
Finally, we aim to embed the _N. azollae_ evolution in a broader perspective of Nostocales taxonomy, hopefully solving the issue of the _N. azollae_ genus name.
Within this broader perspective of Nostocales genomes, some symbiotic, some not, we hope to identify clusters of genes shared by symbiotic Nostocales Cyanobacteria and perhaps shared by N. azollae specifically.

## Methods
Anvio pangenomics
IQtree
all scripts, snakemake on github

### nanopore sequencing
flowcells,
postprocessing

### data
table on the mags we have from chapter \ref{hidden treasures}

read data, same as chap3, but skipping Afiliculoides since that is the reference already.
When multiple samples are available, taking the longest insert size.

## Results

### De novo assembly of missing _N. azollae_ strains and _Azolla_ chloroplasts and mitochondria.
We aim to study co-evolution of _N. azollae_ and its host via comparative genomics.
To achieve this, we gather all _N. azollae_ and _Azolla_ plastid genomes that are not available publicly yet.
We build further upon the _N. azollae_ Metagenome Assembled Genomes (MAGs) assembled in \ref{hidden treasures}.
Then, we use nanopore sequencing to assemble chromosome length assemblies of _N. azollae_ taken the from: the _A. filiculoides_ Galgenwaard strain, from _A. pinnata_, and from _A. sp_ indicated as Bordeaux.
_A pinnata_ is the only _Azolla_ species that has not been sequenced yet, and it is relativelly far removed from _A. filiculoides_ in the _Azolla_ genus phylogeny (+@fig:fig3_data_overview) [@Metzgar2007].
We extracted DNA of whole plant fronts using procol `nanopore community protocol`.
DNA was made into a library with protocol `protocol` and sequenced on a `flowcell` flowcell.
Sequencing data was basecalled with guppy `guppy version` and uploaded to EBI ENA under accession `EBI accession`.

The _A. filiculoides_ chloroplast reference genome is available at fernbase [@Li2018] and the _N. azollae_ genome was published by @Ran2010, but the mitochondrial sequence remains unknown.
Hence, we set out to assemble for the first time the _A. filiculoides_ mitochondrial genome.
The mitochondrial genome did not appear in the metagenome analysis of chapter \ref{hidden treasures}, hence we start looking for it in the latest _A. filiculoides_ genome assembly.
We took the _A filiculoides_ genome assembly version 2 [@gungur2022], alligned _A.filiculoides_ Illumina reads to it [@Li2018] and performed metagenomic binning on this assembly.
Contigs of these bins were mapped with blastn to known fern mitochondrial genomes of _Ophioglossum californicum_ and _Psilotum nudum_ `ref`.
One bin stood out in particular but was many times the expected size of a mitochondrium (`get nr`).
Since assembly with PacBio RSII reeds had been unsuccessful in assembling the _A. filiculoides_ mitochondrial genome, we now opted to use the newly acquired nanopore reads of _A. filiculoides_.
Nanopore reads were selected by mapping to the bin with suspected mitochondrial sequences with minimap2 [@Li2018a] and then assembled with flye [@Kolmogorov2019].
This assembly was much smaller `get nrs` than the PacBio RSII one, but still fragmented.
Redundant contigs were idintified via blast all-vs-all and then removed, resulting in `nr` contigs together constituting the first draft genome of an _Azolla_ mitochondrium.
The mitochondrial assembly was then annotated using the chlorobox online interface `chlorobox`.

The _A. filiculoides_ chloroplast reference sequence was taken from fernbase, but chloroplasts of other _Azolla_ species are not publicly available.
These sequences were assembled by @Li2018 for comparative phylogenomics of fern and _N. azollae_, but these are not publicly available via fernbase.
Therefore, we set out to assemble these de-novo with nanopore or Illumina reads.
Chloropast nanopore reads were baited in a similar fashion as the mitochondrial nanopore reads and assembled and filtered with flye and Bandage.
`something about the quality of these assemblies`
Chloroplast illumina reads were also baited and selected


```
Idea, I can make a many panel figure displaying the various bandage images
and their similarity to references, but I don't think it is important enough...
```

For efficient assembly, we aim to subdivide the nanopore reads by organellar genome, _N. azollae_ genome, or fern nuclear genome.
An extended _A filiculoides_ reference genome was constructed from the _A. filiculoides_ nuclear genome and chloroplast [@Li2018], _N. azollae_ [@Ran2010], and the draft mitochondrial genome constructed here.
Nanopore sequencing reads were selected by mapping against this reference a with minimap2 `ref minimap2` and samtools [@Li2009] and then assembled with flye `ref flye`.
These de-novo assemblies were then examined in Bandage for homology to their reference.
First assissing the cyanobacterial assemblies, the _A. filiculoides_ assembly consisted of a circular chromosome and two circular plasmids just as the @Ran2010 assembly.
The _A. pinnata_ assembly consisted of a circular chromosome and several small fragments.
The _A. sp._ genome assembly was highly fragmented due to low coverage, but still contained major parts of the _N. azollae_ genome.
`genome sizes in table`

insert table with
* strain
* Nanopore sequencing yield
* Nazollae/chlorplast/mito
* Assembly Contigs
* length
* N50
* hits to reference
* coverage min,mean,max?

Reads of the chloroplast and mitochondrial genomes were selected and assembled similarly.
These de-novo assemblies were then examined in Bandage too and rid of any contaminants.
The _A. filiculoides_ mitochondrium assembled into one linear piece, the _A sp._ in two, and the _A. pinnata_ in multiple smaller pieces.
The _A. sp._ chloroplast assembled into one circular piece, the _A. filiculoides_ chloroplast in three pieces interconnected in the assembly graph, and the _A. pinnata_ chloroplast into 4 bigger fragments and several small ones, also all interconnected in the assembly graph.
We assess these assemblies as sufficient and proceed to assembly Illumina assemblies as well.

Illumina sequencing based assemblies of _N. azollae were taken from chapter \ref{hidden treasures}, but those of the plasteds still have to be assembled.
Illumina reads were mapped to the combined reference genome with bwa [@Li2009a], selected with samtools [@Li2009, and then assembled with SPAdes.
De-novo assemblies of plastids turned out to be highly fragmented (over 300 contigs), even when reference sequences were taken into account during assembly using the SPAdes `--trusted-contigs` option.
We next resorted to assembly via NOVOplasty.
NOVOplasty itteratively extends a seed sequence known to be from a plastid.
For chloroplast assembly, a Rubisco DNA sequence was used to assemble chlotoplasts, resulting in circular de-novo chlorplast sequences in x cases namely: .
Mitochondrial assembly proved to more elusive.
A seed sequence for maturase K (MatK) yieded in assemblies shorter than 1kb.
An alternative seed sequence was found in cox1, taken directly from the draft mitochondrial genome assembly of _A. filiculoides_.
Using this seed sequence, assemblies of appropreate lengts were acquired, except for _A. nilotica_.

`external gene calls for mito?`

insert table with Illumina assembly stats
* strain
* Nazollae/chlorplast/mito
* Illumina read pairs
* Assembly Contigs
* length
* (N50)
* hits to reference
* coverage min,mean,max?

### All _N. azollae_ are highly similar in terms of ANI and gene content but have some unique features
Armed with _N. azollae_ of all known _Azolla_ strains, we wonder how similar these genomes are in gene content, and if they can be considered separate species or if they are the same.
All available _N. azollae_ genomes and the reference from @Ran2010 were processed in an Anvi'o pangenomics workflow [GitHub page].
This workflow finds ORFs, tries to functionally annotate these via either NCBI COGs or KEGG KOFAMS, and then maps all ORFs to all ORFs with blastp to then cluster these genes in gene clusters that systematically co-occur in the various genomes.
Additionally, Average Nucleotide Identity (ANI) was determined over all regions of the entire genomes that mapped to each other.

![Pangenome summary of _Nostoc azollae_ strains representative of the entire _Azolla_ genus. _N. azollae_ genomes were scanned for ORFs and clustered on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The presence/absence pattern of gene clusters is shown in a heatmap-like fashion as concentric semi-circles around the dendrogram. Outside the heatmap, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homeogenity of clusters is calculated as geometric (based on gaps), functional ( based on amino acid residues) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the genecluster heatmap, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Nostoc_azollae_pangenome.pdf){#fig:fig4_Nazollae_pangenome}

![Pangenome summary of _Azolla_ chloroplasts. Chloroplast genomes were scanned for ORFs and clustered on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The presence/absence pattern of gene clusters is shown in a heatmap-like fashion as concentric semi-circles around the dendrogram. Outside the heatmap, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homeogenity of clusters is calculated as geometric (based on gaps), functional ( based on amino acid residues) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the genecluster heatmap, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Azolla_chloroplast_pangenome.pdf){#fig:fig4_chloroplast_pangenome}


```
90% fafa8e
100% 007872
```

All genomes of _N. azollae_ taken from various _Azolla_ hosts are highly similar both in ANI and in gene content but have some unique features. 
All genomes count similar amount of gene clusters except the Bordeaux strain.
The Euazolla section is very similar in ANI `over ...%` but both rhizosperma species are no more than `...%` similar to any other _N. azollae_.
Strictly speaking, this means that the _N. azollae_ from _A. pinnata_ and _A. nilotica_ are separate species from the _N. azollae_ in the Eukazolla section.
For the manuscript, we chose not do make this disctinction.
The Bordeaux strain genome assembly stands out for it misses many of the genes shared by other _N. azollae_.
These are likely missing due to the poor assembly quality, data input was minimal in this assembly and well below the recommended coverage for assembly with flye (10x vs 40x minimum).
Regardless, all genomes show low redundancy and high completion scores. 
A big majority of genes is shared amongst all N. azollae. (N. azollae core), not regarding any genes missing in the Bordeaux strain.
Within this core genome, a substantial amount of genes has functional annotation (ncbi COG or KEGG KOFAM). `count percentage`
Outside this group, the frequency of functional annotation is less. `count percentage`

The _N. azollae_ genomes show some unique gene clusters (at least with these clustering parameters).
The Rhizosperma section does share a unique set of genes despite their relatively low ANI (+@fig:fig4_Nazollae_pangenome Rhizosperma accessory).
`functional enrichment?`
_N. azollae_ from _A. filiculoides_ and _A. rubra_ share some genes unique to them, and a smaller selection shared with microphylla/mexicana (+@fig:fig4_Nazollae_pangenome _mexicana_/_microphylla_ accessory).
`functional enrichment?`
Finally, the two _A. caroliniana_ strains are not identical, but do share their own specific subset of genes (+@fig:fig4_Nazollae_pangenome Caroliniana accessory)..
The Bordeaux strain clusters with these two _A. caroliniana_ strains in the phylogenomic tree.

From all genes in the pangenome, I select a subset of genes that occur in all genomes only once, that have no more than 10% gaps when aligned, and that are no more than 95% identical in sequence. The resulting 27 genes are used for a phylogenomic tree. The resulting phylogeny fits with that already published of the _Azolla_ genus [@Metzgar2007] and matches with the ANI of the pangenome.
The result then is (preliminary): All N. azollae are very similar, the pinnata and nilotica strain both are quite different (but still very similar). The difference is reflected in annotated genes, but no specific function can be attributed to these genes unique for a group.

```
The same analysis is running over the weekend of the chloroplast and mitochondrium, trees should mirror. That will be the next results sub-section. Do these trees mirror.

#todo still: 
  - Add colours/groupings to the different genomes for functional enrichment. 
  - long branches Nanopore assemblies, hard to say anything about phylogeny without polishing with illumina data.
```

**co-evolution**
* Wierd co-evolution tree in @Li2018. Let's do this again and assembly the chloroplasts anew. (and mito to get rid of that too...)

![Coevolution trees pased on phylogenomic core gene set determined in pangenomic analyses.](source/figures/fig4_coevolution_trees.pdf){#fig:fig4_coevolution_tree}

**genomics/synteny**
whole genome alignment figure:
* Sync and scaffold assemblies to reference.
* How similar are they genomically
   - single introduction in Azolla genus
* Is the published structure correct, complete, and unchanged
   - Giulio's figure, yes the structure is unchanged but two plasmids are actually one.

**genomics/pseudogenes & transpons**
* which genes are functional in all species?
   - pseudogenation master table

About pseudogenes and transposons:
* Are pseudogenes shared?: shared transposons by Giulio
  - which genes are functional in all species?
  - pseudogenation master table

* When did the transposons move (shown in the tree)
   - tricky...
   - single introduction in Azolla genus and rapid degradation before Azolla speciations!

Transposon position is conserved and the symbiosis formed rapidly in the common ancestor of all Azolla species, after which evolution of the symbiont came to a standstill and the different azolla strains speciated.

```
Likely to be skipped
**genomics Dual RNAseq data**
About genomics of a symbiont:
* RNAseq data, compared to gene models, expression data.
   - mRNAseq, gene expression from none-gene model regions?
   - sRNAseq,
     - CAS targetted phosphate transporter...?

**Other stuff:**
* Sufficient data for puryfying selection? Likely not.
* Crispr: lacking immunity in N. azollae -> plant must keep its house clean
```

**Evolution**
* Is the gene content of N. azollae special, symbiotic toolkit?
   - pangenomics multiple nostocs

* So much debate about which species it is, can we sovle that here?
   - phylogenomic tree nostoc, trichormus, anabaena.

```
Likely to be skipped:
**Morphology**
* encapsulating from the meristem colony --?
* pictures from Erbil

* Confocal images of Anna in which the microsporocarps lose the Cyano's while the megasporocarps keep these.
  - both sporocarps gaining the Nostocs was published [@Perkins1993], but nog the losing part.
```

## Discussion
**Nostoc in the Azolla symbiosis**
N. azollae rappid introduction and degradation solidified its presence in the Azolla symbiosis.
* Co-evolution is ... awaiting trees ...
* N. azollae is basically one species, except for pinnata and nilotica, but what does that even mean...
* Pseudogenation has come to a standstill

How does the symbiont remain stable
* bottleneck effect, Muellers ratchet?
   - might polyploidy be involved.

conservedness --> selection presure of presumable symbiosis important genes

**nostocales**
Embed in nostoc/trichormus/anabaena tree for more definitive placing.
Single introduction, this is a ... genus ...
Symbiotic gene kit

**future work**
is there restructuring in the resting stages of *Nostoc azollae*

```
skipped
* Do we find more expressed regions with the RNAseq data
   - We do, needs propper annotation.
```

## Supplemental

![Pangenome summary of _Azolla_ mitochondria. Mitochondrial genomes were scanned for ORFs and clustered on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The presence/absence pattern of gene clusters is shown in a heatmap-like fashion as concentric semi-circles around the dendrogram. Outside the heatmap, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homeogenity of clusters is calculated as geometric (based on gaps), functional ( based on amino acid residues) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the genecluster heatmap, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Azolla_mitochondrium_pangenome.pdf){#fig:fig4_mitochondrium_pangenome}
