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

table on chloroplasts

read data, same as chap3, but skipping Afiliculoides since that is the reference already.
When multiple samples are available, taking the longest insert size.

**Get more data**
Let's get more info with nanopore Sequencing
 * Nostoc: We have single chromosomes and single plasmids!
   - except for Bordeaux, not sufficient data
 * assemble all chloroplasts for comparative trees co-evolution
 * assemble all mitochondria too
   - find mito scaffolds in Azfi assembly
   - recruit nanopore reads
   - assemble, reduce, assemble
## Results

**Azolla genus**
* How similar (dis)similar are all *Nostoc azollae* in all *azolla* species. We take the data of chapter 3 and start comparing them.
    - anvio pangenomics and ANI figure. Gene content is the same
    - phylogenomic tree Azolla genus Nostocs only
    - All the same except _A. nilotica_ and possibly _A. pinnata_.
      - long branches Nanopore assemblies, hard to say anything about phylogeny without polishing with illumina data.
        - Can I do some nanopore specific polishing? Didn't see much benefit from this in the anabaena project though...
      - nilotica is different OTU (stricly speaking)
      - Different in pangenomics as well?
        - Any enrichment in the specific clusters

All nostocs are alike in terms of genome structure and gene content. Being more than 99% similar, they are one species.  

**co-evolution**
* Wierd co-evolution tree in @Li2018. Let's do this again and assembly the chloroplasts anew. (and mito to get rid of that too...)

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
