# Forever together: One nostoc azollae is symbiont to all Azolla species
\label{forever together}

### Introduction
Cyanobacterial symbiosis in general.

_Nostoc azollae_ main symbiont of _Azolla_
 * Main symbiont, N-fixation.
 * present in All _Azolla_

Symbiosis co-evolution. How does _N. azollae_ compare to other known examples.
 * very strict inheritance
 * Exception in Li et al tree?
   - compare to chloroplast, how about mitochondrium?
 * Common introduction in the genus.

_N. azollae_ was first sequenced by @Ran2010, taken from _Azolla filiculoides_.
 * Its genome is heavily degraded
 * Symbiosis bottleneck, did this occur in _Azolla's_  main symbiont? At what stage in the symbiosis.

Here we gather and supplement data of N. azollae and plasmids assocated with the entire Azolla genus.
We add long-read data to further resolve the structure of the fragmented _N. azollae_ genome assembly associated with _A. filiculoides_.
We also add long read data of _A. piniata_, the only Azolla species that has not been sequenced yet.
Add long read data of Azolla anzali, taken from the Anzali lake and suspected to be a new species.
Finally, we add sequencing data of an Azolla strain of unknown taxonomy to us but likely rubra: Bordeaux after its sampling location.

### Results
**Get more data**
Let's get more info with nanopore Sequencing
 * Nostoc: We have single chromosomes and single plasmids!
   - except for Bordeaux, not sufficient data
 * assemble all chloroplasts for comparative trees co-evolution
 * assemble all mitochondria too
   - find mito scaffolds in Azfi assembly
   - recruit nanopore reads
   - assemble, reduce, assemble

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

**genomics Dual RNAseq data**
About genomics of a symbiont:
* RNAseq data, compared to gene models, expression data.
   - mRNAseq, gene expression from none-gene model regions?
   - sRNAseq,
     - CAS targetted phosphate transporter...?

**Other stuff:**
* Sufficient data for puryfying selection? Likely not.
* Crispr: lacking immunity in N. azollae -> plant must keep its house clean

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
* Pseudogenation has come to a standstill

* bottleneck effect, Muellers ratchet?
   - might polyploidy be involved.

polyploidy in *N. azollae*

is there restructuring in the resting stages of *Nostoc azollae*

A new co-evolution tree between nostoc and chloroplast with the two novel species nicely separate and based on several SCMG

conservedness --> selection presure of presumable symbiosis important genes

embed in nostoc/trichormus/anabaena tree for more definitive placing.

* Do we find more expressed regions with the RNAseq data
   - We do, needs propper annotation.

How does it retain genome stability with (plant) generation bottleneck

Are cyanobacteria often polyploïd,  
