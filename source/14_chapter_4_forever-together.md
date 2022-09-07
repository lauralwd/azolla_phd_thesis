# Forever together: One _Nostoc azollae_ is symbiont to all Azolla species
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

### workflow management and documentation
snakemake & workflow overview

Anvio 7 pangenomics

IQtree

R & ggplot2

Mauve

Github

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
To achieve this, we gather _N. azollae_ and _Azolla_ plastid genomes of all _Azolla_ species
We build further upon the _N. azollae_ Metagenome Assembled Genomes (MAGs) assembled in chapter \ref{hidden treasures}.
Then, we use nanopore sequencing to assemble chromosome length assemblies of _N. azollae_ taken the from: the _A. filiculoides_ Galgenwaard strain, from _A. pinnata_, and from _A. sp_ indicated as Bordeaux.
_A pinnata_ is the only _Azolla_ species that has not been sequenced yet, and it is relativelly far removed from _A. filiculoides_ in the _Azolla_ genus phylogeny (+@fig:fig3_data_overview) [@Metzgar2007].
We extracted DNA of whole plant fronts using procol `nanopore community protocol`.
DNA was made into a library with protocol `protocol` and sequenced on a `flowcell` flowcell.
Sequencing data was basecalled with guppy `guppy version` and uploaded to EBI ENA under accession `EBI accession`.

Armed with sequencing data for all _Azolla_ species, we set out to reconstruct the genomes of _N. azollae_, and the _Azolla_ chloroplasts and mitochondria.
In doing so, we chose de-novo assembly algorithms and supply these with baited reads.
Baited reads are selected based on their homology to a reference genome of the cyanobacterium or a plastid.
The _A. filiculoides_ chloroplast reference genome is available at fernbase [@Li2018] and the _N. azollae_ genome was published by @Ran2010, but the mitochondrial sequence remains unknown.
In order to bait mitochondrium DNA reads of all _Azolla_ species, we first search for the _A. filiculoides_ mitochondrial genome in previous _Azolla_ studies.
The mitochondrial genome did not appear in the metagenome analysis of chapter \ref{hidden treasures}, hence we start looking for it in the latest _A. filiculoides_ genome assembly.
We took the _A filiculoides_ genome assembly version 2 [@gungur2022], alligned _A.filiculoides_ Illumina reads to it [@Li2018] and performed metagenomic binning on this assembly with metabat2 `cite metabat2`.
Contigs of these bins were mapped with blastn to known fern mitochondrial genomes of _Ophioglossum californicum_ and _Psilotum nudum_ `ref`.
One bin stood out in particular but was many times the expected size of a mitochondrium: near 4.2M instead of between 400kb and 300kb.
Contigs of this bin were highly redudant, and the bin likely contained various configurations of the mitochondrial genome.
Since assembly of PacBio RSII reads with canu had been unsuccessful in resolving the mitochodrium structure, we opted to use the newly acquired nanopore reads of _A. filiculoides_.
The bin was subsetted based on blastn bitscores to _O californicum_ and _P nudum_ mitochondrial genomes, and this subset was used to bait nanopore reads.
These nanopore reads were then assembled with flye [@Kolmogorov2019] and the assembly graph was inspected in Bandage `cite bandage`.
The assembly totalled at 3.2Mbase, and contained various subgraphs that showed homology to _N. azollae_ and the _A. filiculoides_ chloroplast.
One circular subgraph showed homology to the _O californicum_ and _P nudum_ mitochondria (+@fig:fig4_mitochondrium_assembly_selection A).
This mitochodrium subgraph contained 188kb of DNA, more than half in a single contig.
Smaller redundant contigs were idintified via blast all-vs-all (+@fig:fig4_mitochondrium_assembly_selection B) and then removed.
Six contigs remained with minimal redundancy (+@fig:fig4_mitochondrium_assembly_selection C), together constituting the first draft genome of an _Azolla_ mitochondrium of 141kb in total.
The mitochondria assembly was polished twice with pilon using Illumina reads of the same _Azolla filiculoides_ lab strain, and then annotated using the chlorobox online interface `chlorobox`.

![Sequencing and assembly summary of all _N. azollae_ and plastid genomes of the _Azolla_ genus.](source/figures/fig4_assembly_stats.pdf){#fig:fig4_assembly_stats}

With reference sequences available for all genomes of interest, we proceed in baiting nanopore reads by organellar genome, _N. azollae_ genome, or fern nuclear genome.
An extended _A. filiculoides_ reference genome was constructed from the _A. filiculoides_ nuclear genome and chloroplast [@Li2018], _N. azollae_ [@Ran2010], and the draft mitochondrial genome constructed here.
Nanopore sequencing reads were selected by mapping against this reference a with minimap2 [@Li2018a] and samtools [@Li2009] and then assembled with flye [@Kolmogorov2019].
These de-novo assemblies were then examined in Bandage `bandage` for homology to their reference.
The amount of DNA per genome differed substantially in the bulk nanopore library.
_N. azollae_ sequencing was the most abundant, ranging between 65Mbase and 2.7Gbase (+@fig:fig4_assembly_stats; Sequencing input; _N. azollae_).
Chloroplast DNA was the second most abundant, ranging between 24 and 240Mbase (+@fig:fig4_assembly_stats; Sequencing input; chloroplast) but still amounting to over 100x coverage over the short genome (+@fig:fig4_assembly_stats; Coverage; chloroplast).
Mitochondrial DNA however, was very sparse in the DNA extraction ranging between ,3 and 3Mbase (+@fig:fig4_assembly_stats; Sequencing input; mitochondrium), ammounting to no more than 1.5% compared to the _N. azollae_ and nomore than 10x Coverage (+@fig:fig4_assembly_stats; Coverage; mitochondrium).
Nanopore reads had an N50 between 7 and 13kb, except for the _A. sp._ 'Bordeaux' sample.
These long reads wil aid in resolving the fragmented assemblies as seen in chapter \ref{hidden treasures}.

With reads subdivided per genome, we set out to assemble the _N. azollae_ genomes first and compare these to earlier acquired _N. azollae_ MAGs.
the _A. filiculoides_ and _A. pinnata_ assembiles consisted of very few fragments and the majority of the assemblies were contained in one big scaffold for the N50 approached the full genome size (+@fig:fig4_assembly_stats; _N. azollae_ ; Assembled contig count & Assembled length & Assembled N50).
The _A. filiculoides_ 'lab' nanopore assembly consisted of a circular chromosome and two circular plasmids amounting to 5.5MB in total just as the @Ran2010 assembly (+@fig:fig4_Nazollae_nanopore_assemblies; _Azolla filiculoides_ 'lab').
The _A. pinnata_ assembly consisted of a circular chromosome and several small fragments (+@fig:fig4_Nazollae_nanopore_assemblies; _Azolla pinnata_).
The circular chromosome indicates however that this assembly is likely near complete, only missing partial plasmids.
The _A. sp._ 'Bordeaux' genome assembly was highly fragmented due to low coverage and input data, but still ammounts to 3Mbase and may thus contain half of the _N. azollae_ genome still.
The nanopore assemblies of _N. azollae_ were much smaller than the MAGs acquired from chapter \ref{hidden treasures}.
The latter were often between 6.4 and 8Mbase and had much lower N50 values; typically no more than 80kb.
The full chromosome length assembly of the _A. filiculoides_ lab strain of _N. azollae_ allows us to study chromosomal reconformation in _N. azollae_ on the short term.
The _A. pinnata_ strain of _N. azollae_ allows us to study the same phenomonen on a longer evolutionary time scale.

Next, we assemble the _Azolla_ chloroplast and mitochondrium genomes from nanopore data.
The _A. filiculoides_ chloroplast reference sequence was taken from fernbase.
Chloroplasts of other _Azolla_ species were assembled by @Li2018 for comparative phylogenomics of fern and _N. azollae_, but these are not publicly available.
Therefore, we set out to assemble these de-novo with nanopore first, and then with Illumina reads.
Nanopore reads were processed as for _N. azollae_.
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

### All _N. azollae_ are highly similar in terms of ANI and gene content but have some unique features
Armed with _N. azollae_ genomes of all known _Azolla_ strains, we wonder how similar these genomes are in gene content, and if they can be considered separate species or if they are the same.
These genomes and the reference from @Ran2010 were processed in an Anvi'o pangenomics workflow [github.com/lauralwd/Nostoc_azollae_pangenomics](https://github.com/lauralwd/Nostoc_azollae_pangenomics).
This workflow finds ORFs, tries to functionally annotate these via NCBI COGs and KEGG KOFAMS, and maps all ORFs to all ORFs with blastp to then cluster these genes in gene clusters that systematically co-occur in the various genomes with MCL clustering coefficient set at 7 `cite MCL threshold`.
Additionally, Average Nucleotide Identity (ANI) was determined over all regions of the entire genomes that mapped to each other.

![Pangenome summary of _Nostoc azollae_ strains representative of the entire _Azolla_ genus. _N. azollae_ genomes were scanned for ORFs and clustered (MCL=7) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. Outside the frequency barplots, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. ANI values in the heatmap range from 90% to 100%. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Nostoc_azollae_pangenome.pdf){#fig:fig4_Nazollae_pangenome}

All genomes of _N. azollae_ taken from various _Azolla_ hosts are highly similar both in ANI and in gene content but have some unique features. 
All genomes count similar amount of gene clusters except the Bordeaux strain, concordant with this assembly being only a portion of the genome (+@fig:fig4_Nazollae_pangenome; Num gene clusters).
The Euazolla section is very similar in ANI; over 97%, but both rhizosperma species are no more than 94% similar to any other _N. azollae_ (+@fig:fig4_Nazollae_pangenome; ANI heatmap).
Strictly speaking, this means that the _N. azollae_ from _A. pinnata_ and _A. nilotica_ are separate species from the _N. azollae_ in the Eukazolla section.
For the manuscript, we chose not do make this disctinction.
Regardless, all genomes show low redundancy and high completion scores, supporting both Illumina and nanopore based assemblies are complete.
A big majority of genes is shared amongst all _N. azollae_. (+@fig:fig4_Nazollae_pangenome; N. azollae core), not regarding any genes missing in the Bordeaux strain.
Within this core genome, a substantial amount of genes has functional annotation (ncbi COG or KEGG KOFAM).
Outside this group, the frequency of functional annotation is less.

Provided this pangenome of _N. azollae_, we next wondered if certain groups of _N. azollae_ genomes contain unique gene clusters.
Calculating functional enrichment on such a small number of genomes is not statistically significant, but by comparing both NCBI COG and KEGG KOFAM annotations, we attempt to gain some insight in the functional diversification that happenend within the _N. azollae_ associated with the _Azolla_ genus.
The Rhizosperma section shares a unique set of genes despite their relatively low ANI (+@fig:fig4_Nazollae_pangenome; _Rhizosperma_).
These unique clusters include genes associated with carbon metabolism and secondary metabolites.
KEGG and NCBI functional annotations indicate beta-lactams and Nocardicin biosynthesis genes are enriched.
Additonally, Cationic AntiMicrobial Peptide (CAMP) resistance are enriched as well.
Finally, some unique carbohydrate genes are present in these _N. azollae_, including propanoyl-CoA and isoprenoid metabolism.
Several DNA maintainance and repair enzymes stand out in NCBI COG enriched functions.
<!---
KEGG_Class
Pathway module; Biosynthesis of other secondary metabolites; Biosynthesis of beta-lactams
Pathway modules; Carbohydrate metabolism; Other carbohydrate metabolism!!!Pathway modules; Energy metabolism; Carbon fixation!!!Pathway modules; Energy metabolism; Carbon fixation!!!Pathway modules; Lipid metabolism; Lipid metabolism!!!Pathway modules; Biosynthesis of terpenoids and polyketides; Terpenoid backbone biosynthesis!!!Pathway modules; Biosynthesis of terpenoids and polyketides; Terpenoid backbone biosynthesis

KEGG_Module
Catechol meta-cleavage, catechol => acetyl-CoA / 4-methylcatechol => propanoyl-CoA
Cationic antimicrobial peptide (CAMP) resistance, dltABCD operon
Ethylmalonyl pathway!!!Hydroxypropionate-hydroxybutylate cycle!!!Dicarboxylate-hydroxybutyrate cycle!!!Ketone body biosynthesis, acetyl-CoA => acetoacetate/3-hydroxybutyrate/acetone!!!C5 isoprenoid biosynthesis, mevalonate pathway!!!C5 isoprenoid biosynthesis, mevalonate pathway, archaea
Nocardicin A biosynthesis, L-pHPG + arginine + serine => nocardicin A

COG20_CATEGORY
Lipid transport and metabolism!!!Secondary metabolites biosynthesis, transport and catabolism!!!Secondary metabolites biosynthesis, transport and catabolism
Secondary metabolites biosynthesis, transport and catabolism!!!Secondary metabolites biosynthesis, transport and catabolism!!!General function prediction only
General function prediction only!!!Secondary metabolites biosynthesis, transport and catabolism
Transcription!!!Function unknown
Transcription!!!Replication, recombination and repair!!!Lipid transport and metabolism

COG20_PATHWAY
Fatty acid biosynthesis!!!Fatty acid biosynthesis

COG20_FUNCTION
Uncharacterized peptidoglycan binding protein, contains LysM and FecR  domains
PAS domain (PAS) (PDB:2MWG)!!!GAF domain (GAF)!!!K+-sensing histidine kinase KdpD (KdpD) (PDB:2KSF)
Predicted nuclease (RNAse H fold)
Urease gamma subunit (UreA) (PDB:1A5K)
Two-component sensor histidine kinase, HisKA and HATPase domains (PDB:4R39)
Acyl carrier protein (AcpP) (PDB:1ACP)!!!EntF, seryl-AMP synthase component  of non-ribosomal peptide synthetase (EntF) (PDB:5ES5)!!!Thioester reductase domain of alpha aminoadipate reductase Lys2 and NRPSs (Lys2b) (PDB:5MSP)
Acyl carrier protein (AcpP) (PDB:1ACP)!!!EntF, seryl-AMP synthase component  of non-ribosomal peptide synthetase (EntF) (PDB:5ES5)!!!Taurine dioxygenase, alpha-ketoglutarate-dependent (TauD) (PDB:1DRT)
Phosphoribosyl-AMP cyclohydrolase (HisI1) (PDB:1ZPS)
Acyl carrier protein (AcpP) (PDB:1ACP)!!!EntF, seryl-AMP synthase component  of non-ribosomal peptide synthetase (EntF) (PDB:5ES5)
Phenylpyruvate tautomerase PptA, 4-oxalocrotonate tautomerase family (PptA) (PDB:1BJP)
Predicted Mg-chelatase, contains ChlI-like and ATPase domains, YifB family (YifB)
EntF, seryl-AMP synthase component  of non-ribosomal peptide synthetase (EntF) (PDB:5ES5)!!!Taurine dioxygenase, alpha-ketoglutarate-dependent (TauD) (PDB:1DRT)!!!Uncharacterized conserved protein, contains a NRPS condensation (elongation) domain
Predicted aspartyl protease
Uncharacterized conserved protein YggU, UPF0235/DUF167 family (YggU) (PDB:1JRM)
Thiosulfate reductase cytochrome b subunit (YdhU)
DNA-binding transcriptional regulator, MarR family (MarR) (PDB:1JGS)
Aspartyl/asparaginyl beta-hydroxylase, cupin superfamily (LpxO2)
Histidinol phosphatase/D-glycero-mannoheptose bisphosphatephosphatase, HAD superfamily (HisB1/GmhB) (PDB:2GMW) (PUBMED:20050615;20050614)
WD40 repeat (WD40) (PDB:3UVN)!!!Uncharacterized conserved protein, contains caspase domain (PDB:3UO8)
WD40 repeat (WD40) (PDB:3UVN)!!!Ca2+-binding protein, RTX toxin-related (PDB:1AF0) (PUBMED:15135544)
Putative component of the toxin-antitoxin plasmid stabilization module
Transposase and inactivated derivatives, IS30 family (Tra8)!!!CRISPR-associated protein Csa3, CARF domain (Csa3) (PDB:2WTE) (PUBMED:21093452)
Superfamily II DNA or RNA helicase (SSL2) (PDB:6JDE)!!!Phosphatidylserine/phosphatidylglycerophosphate/cardiolipin synthase (Cls) (PDB:1BYR)
Predicted P-loop ATPase and inactivated derivatives
Transposase InsO and inactivated derivatives (Tra5)!!!CRISPR-associated protein Csa3, CARF domain (Csa3) (PDB:2WTE) (PUBMED:21093452)
Uncharacterized membrane protein YccC (YccC)
EntF, seryl-AMP synthase component  of non-ribosomal peptide synthetase (EntF) (PDB:5ES5)!!!Taurine dioxygenase, alpha-ketoglutarate-dependent (TauD) (PDB:1DRT)
Sugar isomerase-related protein YecE, UPF0759/DUF72 family (YecE) (PDB:1VPQ)
Photosystem II reaction center protein T, PsbT/Ycf8 (PsbT) (PDB:1S5L) (PUBMED:17935689;17967798;20558739;25043005)
Beta-lactamase class D (YbxI) (PDB:5CTN)
Periplasmic deferrochelatase/peroxidase EfeB (EfeB) (PDB:2D3Q)
Chemotaxis response regulator CheB, contains REC and protein-glutamate methylesterase domains (CheB) (PDB:1A2O)
DNA polymerase III, epsilon subunit or related 3'-5' exonuclease (DnaQ) (PDB:1J53)
PAS domain (PAS) (PDB:2MWG)!!!Cyclic di-GMP metabolism protein, combines GGDEF and EAL domains with a 6TM membrane domain
Acyl carrier protein (AcpP) (PDB:1ACP)!!!NAD(P)-dependent dehydrogenase, short-chain alcohol dehydrogenase family (FabG) (PDB:6L1H)!!!Acyl transferase domain in polyketide synthase (PKS) enzymes (PksD) (PDB:6IYO)
Uncharacterized conserved protein, contains PIN-related Mut7-C RNAse domain (Mut7-C)
MbtH family protein, regulates adenylation domains of NRPSs (MbtH) (PDB:2GPF) (PUBMED:21890635;29921120)
Uncharacterized membrane protein YecN, MAPEG domain (YecN)
Cysteine protease, C1A family (PDB:1AEC)
Septation ring formation regulator EzrA (EzrA) (PDB:4UXV)
Chlorophyll-binding protein PcbABC/IsiA (IsiA) (PUBMED:32393811)
Sulfate permease or related transporter, MFS superfamily (SUL1) (PDB:3NY7)
Cytosine/adenosine deaminase or related metal-dependent hydrolase (SsnA) (PDB:3O7U)
Type I restriction-modification system, DNA methylase subunit (HsdM) (PDB:2AR0) (PUBMED:26872910)!!!Uncharacterized conserved protein, contains restriction enzyme R protein N terminal (HSDR_N) domain
ATP-, maltotriose- and DNA-dependent transcriptional regulator MalT (MalT)!!!Uncharacterized conserved protein, contains CHAT domain (PUBMED:11835511)
--->
The other main section of the genus; the Euazolla section, also shares a specific set of genes (+@fig:fig4_Nazollae_pangenome; _Euazolla_).
NCBI COG annotation categorises these almost exclusivelly as signal transduction and defense mechanisms.
COG functions that reoocur are often associated with DNA replication and repair and membrane chanels.
KEGG annotation annotates these same clusters as enriched in lipid metabolism and ascorbade biosynthesis.
KEGG KOfam indicates that enriched genes code for arsenic resistance and components of VapC and FitA Toxin-Antitoxin systems.
Other clusters visible in the pangenome, like those consisting of _N. azollae_ from _A. filiculoides_ and _A. rubra_ share a unique set of genes as well (+@fig:fig4_Nazollae_pangenome; _filiculoides rubra_).
Similarly, a smaller selection is shared amongst microphylla/mexicana (+@fig:fig4_Nazollae_pangenome _mexicana_/_microphylla_).
These subgroups however, do not seem to contain meaningfull clusters of funtionally annotated genes.
Sumarising, the _N. azollae_ pangenome is highly similar for the vast majority of gene clusters is shared.
The core cluster of genes comprises 3080 such gene clusters, while the biggest accessory set of gene clusters; the _Rhizosperma_, comprises only 308 gene clusters.
The minor differences found within this _N. azollae_ pangenome are associated with carbon or lipid metabolism, and defense or antibiotic functions.

<!---
KEGG_Class
Pathway modules; Lipid metabolism; Lipid metabolism!!!Pathway modules; Lipid metabolism; Lipid metabolism

KEGG_Module
Ceramide biosynthesis!!!Sphingosine biosynthesis
Ascorbate biosynthesis, animals, glucose-1P => ascorbate

KOfam
tRNA(fMet)-specific endonuclease VapC [EC:3.1.-.-]
antitoxin FitA
molybdopterin synthase catalytic subunit [EC:2.8.1.12]
arsenical resistance protein ArsH
arsenate reductase (thioredoxin) [EC:1.20.4.4]
two-component system, sensor histidine kinase PdtaS [EC:2.7.13.3]
5-amino-6-(5-phospho-D-ribitylamino)uracil phosphatase [EC:3.1.3.104]
alpha-ribazole phosphatase [EC:3.1.3.73]
ATP phosphoribosyltransferase [EC:2.4.2.17]
small multidrug resistance pump
CRISPR-associated protein Csc2
periplasmic divalent cation tolerance protein
NAD(P)H-quinone oxidoreductase subunit L [EC:7.1.1.2]
general L-amino acid transport system substrate-binding protein
general L-amino acid transport system permease protein
glycyl-tRNA synthetase alpha chain [EC:6.1.1.14]
two-component system, OmpR family, manganese sensing response regulator
glucosamine-6-phosphate deaminase [EC:3.5.99.6]
glycerophosphoryl diester phosphodiesterase [EC:3.1.4.46]
multiphosphoryl transfer protein [EC:2.7.3.9 2.7.1.202]
photosystem I P700 chlorophyll a apoprotein A1
DNA sulfur modification protein DndE
ArsR family transcriptional regulator, lead/cadmium/zinc/bismuth-responsive transcriptional repressor
transposase
nicotinamide mononucleotide transporter
dTDP-glucose 4,6-dehydratase [EC:4.2.1.46]
glucose-1-phosphate thymidylyltransferase [EC:2.7.7.24]
protein-glutamine gamma-glutamyltransferase [EC:2.3.2.13]
histidine triad (HIT) family protein
polyhydroxyalkanoate synthase subunit PhaC [EC:2.3.1.-]
metallothionein
iron complex outermembrane recepter protein
MerR family transcriptional regulator, redox-sensitive transcriptional activator SoxR


COG20_CATEGORY
Signal transduction mechanisms!!!Signal transduction mechanisms!!!Signal transduction mechanisms!!!General function prediction only!!!Signal transduction mechanisms
Carbohydrate transport and metabolism!!!Signal transduction mechanisms!!!Carbohydrate transport and metabolism!!!Signal transduction mechanisms
Cell cycle control, cell division, chromosome partitioning!!!Cell motility!!!Defense mechanisms
General function prediction only!!!Cell cycle control, cell division, chromosome partitioning
General function prediction only!!!Signal transduction mechanisms
Mobilome: prophages, transposons!!!Defense mechanisms
Nucleotide transport and metabolism!!!Defense mechanisms
Signal transduction mechanisms!!!Signal transduction mechanisms!!!General function prediction only!!!Signal transduction mechanisms
Signal transduction mechanisms!!!Signal transduction mechanisms!!!Signal transduction mechanisms!!!General function prediction only
Signal transduction mechanisms!!!Transcription!!!General function prediction only!!!Signal transduction mechanisms

COG20_FUNCTION
Wyosine [tRNA(Phe)-imidazoG37] synthetase, radical SAM superfamily (Tyw1) (PDB:2YX0)
Signal transduction histidine kinase (BaeS) (PDB:1JOY)!!!CheY-like REC (receiver) domain, includes chemotaxis protein CheY  and sporulation regulator Spo0F (CheY) (PDB:6QRJ)!!!GAF domain (GAF)!!!Sensor histidine kinase WalK (WalK) (PDB:4I5S)
Ribosomal protein S12 methylthiotransferase accessory factor YcaO (YcaO) (PDB:4BS9)
Type III restriction endonuclease (ResIII)
Gamma-glutamyltranspeptidase (Ggt) (PDB:2Z8I) (PUBMED:16618936)
Galactose-1-phosphate uridylyltransferase (GalT) (PDB:1GUP)
WD40 repeat (WD40) (PDB:3UVN)!!!Membrane protein TolA involved in colicin uptake (TolA) (PDB:1S62)
Glycerol uptake facilitator or related aquaporin (Major Intrinsic protein Family) (GlpF) (PDB:1FQY)
Voltage-gated potassium channel Kch (Kch) (PDB:3FWZ)!!!Predicted Kef-type K+ transport protein, K+/H+ antiporter domain (RosB)
Signal transduction histidine kinase (BaeS) (PDB:1JOY)!!!CheY-like REC (receiver) domain, includes chemotaxis protein CheY  and sporulation regulator Spo0F (CheY) (PDB:6QRJ)!!!PAS domain (PAS) (PDB:2MWG)!!!GAF domain (GAF)
Thiol-disulfide isomerase or thioredoxin (TrxA) (PDB:1XFL)!!!DNA-binding beta-propeller fold protein YncE (YncE) (PDB:3VGZ) (PUBMED:22120742;28628661)
Molybdopterin synthase catalytic subunit MoaE (MoaE) (PDB:1FM0) (PUBMED:32239579)
Serine/threonine protein kinase (SPS1) (PDB:6G4J)!!!PAS domain (PAS) (PDB:2MWG)!!!GAF domain (GAF)!!!Predicted ATPase!!!Signal transduction histidine kinase regulating C4-dicarboxylate transport system (PDB:4GCZ)
Signal transduction histidine kinase regulating C4-dicarboxylate transport system (PDB:4GCZ)!!!Bacteriophytochrome (light-regulated signal transduction histidine kinase) (PDB:2VEA)
5-carboxyvanillate decarboxylase LigW (lignin degradation), amidohydro domain (LigW) (PDB:2DVT) (PUBMED:26714575)
Predicted RNA-binding protein, contains EVE domain (EVE) (PDB:1ZCE) (PUBMED:32652237)
Acyl-CoA dehydrogenase related to the alkylation response protein AidB (CaiA) (PDB:1BUC)
Transposase!!!CRISPR-associated protein Csa3, CARF domain (Csa3) (PDB:2WTE) (PUBMED:21093452)
Phosphoenolpyruvate-protein kinase (PTS system EI component in bacteria) (PtsA) (PDB:1EZA)!!!HPr or related phosphotransfer protein (PtsH) (PDB:1CM2)!!!Phosphotransferase subunit DhaM of the dihydroxyacetone kinase DhaKLM complex, contains PTS-EIIA, HPr, and PEP-utilizing domains (DhaM)
Nicotinamide riboside transporter PnuC (PnuC) (PDB:4QTN)
TRAP-type mannitol/chloroaromatic compound transport system, small permease component (FcbT2)
ABC-type amino acid transport system, permease component (HisM) (PDB:4YMS)
ABC-type amino acid transport system, permease component (BatB)
Uncharacterized membrane protein (PUBMED:30962626)
Uncharacterized conserved protein, contains DUF2059 domain (PDB:2X3O) (PUBMED:15741337)
Outer membrane receptor protein, Fe transport (CirA) (PDB:1BY3)
NAD(P)H dehydrogenase cyanobacteria/chloroplast subunit L (NdhL) (PDB:6HUM) (PUBMED:15910282)
Predicted esterase YcpF, UPF0227 family (YcfP) (PDB:4FLE)
Serine/threonine protein kinase (SPS1) (PDB:6G4J)!!!Signal transduction histidine kinase (BaeS) (PDB:1JOY)!!!GAF domain (GAF)!!!Predicted ATPase
Uncharacterized membrane protein, DUF4212 domain
DNA-binding response regulator, NarL/FixJ family, contains REC and HTH domains (CitB) (PDB:1A04)!!!WD40 repeat (WD40) (PDB:3UVN)!!!Predicted NTPase, NACHT family domain (NACHT)
L-amino acid N-acyltransferase MnaT (MnaT) (PDB:3DR6) (PUBMED:27941785)
Molybdopterin biosynthesis enzyme MoaB/MogA (MoaB) (PDB:1DI6) (PUBMED:32239579)
Signal transduction histidine kinase (BaeS) (PDB:1JOY)!!!CheY-like REC (receiver) domain, includes chemotaxis protein CheY  and sporulation regulator Spo0F (CheY) (PDB:6QRJ)
N-hydroxylaminopurine reductase subunit YcbX, contains MOSC domain (YcbX) (PUBMED:18312271;20118259)
5-methylthioribulose/5-deoxyribulose/Fuculose 1-phosphate aldolase (methionine salvage, sugar degradation) (AraD) (PDB:1FUA) (PUBMED:31950558)
Predicted enzyme of the cupin superfamily (PDB:1LKN)
Putative aminopeptidase FrvX (FrvX) (PDB:1VHE)
Ketosteroid isomerase-related protein (YesE) (PDB:1Z1S)
WD40 repeat (WD40) (PDB:3UVN)!!!Septal ring factor EnvC, activator of murein hydrolases AmiA and AmiB (EnvC)
Site-specific recombinase XerC (XerC)
Peroxiredoxin (AHP1) (PDB:1H4O)
Uncharacterized conserved protein, DUF427 family (PDB:3DJM)
Tetratricopeptide (TPR) repeat (TPR) (PDB:3AS4)!!!Serine/threonine protein kinase (SPS1) (PDB:6G4J)
Purine nucleoside phosphoramidase/Ap4A hydrolase, histidine triade (HIT) family (HinT) (PDB:1AV5) (PUBMED:20934431)
dTDP-D-glucose 4,6-dehydratase (RfbB) (PDB:1G1A)
ParA-like ATPase involved in chromosome/plasmid partitioning or cellulose biosynthesis protein BcsQ (ParA) (PDB:6NOO)!!!Predicted type IV restriction endonuclease
Uncharacterized conserved protein, phosphatidylethanolamine-binding protein (PEBP) family (PEBP) (PDB:1A44)
Curved DNA-binding protein CbpA, contains a DnaJ-like domain (CbpA)
Lipoprotein NlpI, contains TPR repeats (NlpI) (PDB:5WQL)
ATP phosphoribosyltransferase (HisG) (PDB:1H3D)
Uncharacterized conserved protein, DUF924 family (PDB:2I6H)
UV DNA damage repair endonuclease (Uve) (PDB:2J6V)
DNA-binding transcriptional regulator, CsgD family (CsgD)
Plastocyanin domain containing protein (PDB:2MRY)
Kynurenine formamidase (PDB:1R61)
Glycyl-tRNA synthetase, alpha subunit (GlyQ) (PDB:1J5W)
DNAse/DNA nickase specific for phosphorothioated or glycosylated phage DNA, GmrSD/DndB/SspE family, contains DUF262 and HNH nuclease domains (GmrSD) (PDB:6JIV) (PUBMED:17188297;32251370)
Alkaline phosphatase (PhoA) (PDB:1AJA)
Predicted ATP-dependent endonucle# Forever together: One nostoc azollae is symbiont to all Azolla speciesase of the OLD family, contains P-loop ATPase and TOPRIM domains (YbjD)
Two-component response regulator, PleD family, consists of two REC domains and a diguanylate cyclase (GGDEF) domain (PleD) (PDB:1W25)!!!Signal transduction histidine kinase regulating C4-dicarboxylate transport system (PDB:4GCZ)
Tetratricopeptide (TPR) repeat (TPR) (PDB:3AS4)!!!WD40 repeat (WD40) (PDB:3UVN)
Protein thiol-disulfide isomerase DsbC (DsbG) (PDB:2HI7)
Uncharacterized cyanobacterial/plant protein Pro1627, DUF3143 (PF11341) family (Pro1627)
Beta-galactosidase/beta-glucuronidase (LacZ) (PDB:5N6U) (PUBMED:19291314)
Predicted type IV restriction endonuclease
Serine/threonine protein kinase (SPS1) (PDB:6G4J)!!!GAF domain (GAF)!!!Predicted ATPase!!!Signal transduction histidine kinase regulating C4-dicarboxylate transport system (PDB:4GCZ)
Photosystem I reaction center subunit A1, PsaA (PsaA) (PDB:4KT0) (PUBMED:11687205;11418848)
Divalent cation tolerance protein CutA (CutA1) (PDB:1NAQ)
DNA-binding transcriptional regulator, XRE family (YozG) (PDB:3TYR)
--->

### Gene selection for comparative phylogenomics
To study coevolution of _N. azollae_ and the host ferns, we chose a phylogenomics approach.
Given the strains of fern and cyanobacterium have speciated recently, we select several genes for phylogeny reconstruction.
These genes must be single copy in all genomes included, and contain nog more than 10% gaps (+@fig:fig4_Nazollae_pangenome; geometric homogeneity).
Additionally, these genes must be no more than 95% identical in amino acid residues (+@fig:fig4_Nazollae_pangenome; functional homogeneity).
The resulting 27 genes (+@fig:fig4_Nazollae_pangenome; phylogenomic core) are extracted as DNA and amino acid sequences and stored for phylogenomic inference.

Next, a chloroplast pangenome is constructed to select genes for pangenomic analysis via similar criteria (+@fig:fig4_chloroplast_pangenome).
Overall, the chloroplast and the _N. azollae_ pangenome appear highly similar.
Both pangenomes have a big majority of genes shared amongst all genomes included, and the ANI heatmaps resemble each other as well (+@fig:ANI heatmap).
_N azollae_ genomes are even more similar (over 90%) to each other than the chloroplast genomes are (over 80%)
The similarity further supports the tight association of _N. azollae_ with the _Azolla_ genus.
Also in the chloroplast pangenome, a selection is made of single copy gene clusters present in all genomes.
These gene clusters must have no more than 10% gaps and no more than 99% identical aminoacid residues.
The resulting 26 genes are indicated as phylogenomic core (+@fig:fig4_chloroplast_pangenome; phylogenomic core).
Finally, a mitochondrium pangenome is constructed (+@fig:fig4_mitochondrium_pangenome).
The mitocondrial pangenome however, contains almost no gene clusters that are present in all _Azolla_ species, thereby making pangenomic analysis impossible.
This gene cluster pattern is a-typical for a plastid pangenome not exeeding the genus level.
The pattern may indicate that the mitochodrium genome assemblies are too fragmented, contaminated, incomplete or a combination of these.
Regardless, a set of 26 chloroplast genes is sufficient for comparative phylogenomics.
This gene cluster is exported from anvio both as DNA and amino acid sequences and stored for phylogenomic inference.

![Pangenome summary of _Azolla_ chloroplasts. Chloroplast genomes were scanned for ORFs and clustered (MCL=6) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. Outside the frequency barplots, SCMG clusters are indicated in Bordeaux red (SCG Clusters) and functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. The final semi circle shows a manual binning of gene clusters in biologically meaningfull groups, including a phylogenomic_core set of genes, used for building a phylogenomic tree. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, Completion and Redundancy (based on SCMG analysis), genes per kb, Singleton gene clusters, total number of gene clusters, and a matrix showing ANI calculations of all genomes against each other. ANI values in the heatmap range from 80% to 100%. Finally, a phylogenomic tree is shown which is also used to order the genomes.](source/figures/fig4_Azolla_chloroplast_pangenome.pdf){#fig:fig4_chloroplast_pangenome}

<!---
80%/90% fafa8e
100% 007872
--->

### co-evolution
Next we study coevolution by phylogenomic inference on two sets of conserved single copy genes of both chloroplasts and _N. azollae_ taken from the _Azolla_ genus (+@fig:fig4_Nazollae_pangenome & +@fig:fig4_chloroplast_pangenome; phylogenomic core).
Amino acid sequences of these gene clusters were extracted as partitioned allignments.
These allignments were submitted to IQtree model selection and ML phylogeny inference.
Trees were rooted manually on the common ancestor of _A. nilotica_ and _A. pinnata_ guided by @Metzgar2007.
The majority of the tree is identical, the _Rhizosperma_ section, the _filiculoides_-_rubra_ section, and the _microphylla_-_mexicana_ section.
Most species (+@fig:fig4_coevolution_trees; green ribons) and samples (+@fig:fig4_coevolution_trees; blue ribons) are placed in similar places in the tree.
The various assembly techniques seem of no influence on the phylogeny; indicated by consistent grouping of all _A. filiculoides_ associated genomes dispite their varying origin.

Besides the overall similarity, two exceptions are reproducibly present in the tree: the placement of _A. caroliniana_ is not consistent, nor is the placement of _A. sp._ 'Bordeaux'.
The cyanobacterium associated with _A. sp._ 'Bordeaux' is placed with _A. caroliniana_, while the chlorolast is placed as a sister group to _A. microphylla_ and _A. mexicana_ (+@fig:fig4_coevolution_trees; Yellow circle).
Perhaps either clade is misplaced due to assembly artefacts caused by low coverage in the assembly of the associated _N. azollae_ genome.
The placement of _A. sp. 'Bordeaux' in the ANI heatmaps however, is consistent with the phylogenomic tree. (+@fig:fig4_Nazollae_pangenome & +@fig:fig4_chloroplast_pangenome; ANI heatmaps).
Similarly, the two _A. caroliniana_ samples are clustered differently in both trees.
The _A. caroliniana_ symbiont is placed as a sister clade of _A. filiculoides_ and _A. rubra_, while the chloroplast is placed with _A. sp._ Bordeaux, _A. mexicana_ and _A. microphylla_ (+@fig:fig4_coevolution_trees; Red circle).
The phylogenomic signal for this placement was relativelly weak (bootstrap 73).
In an attempt to further explore the reliability of this node in the tree, various other trees were build with varying sets of genes; being more or less stringent on the homogeneity statistics.
The placement of the _A. caroliniana_ clade remained the same despite these efforts, often with lower bootstrap values (data not shown).

![Comparative phylogenimcs on _Azolla_ associated _N. azollae and chloroplasts. Phylogenomic trees were infered on a manually selected set of single copy genes with good allignement scores in the pangenomc analyses (+@fig:fig4_Nazollae_pangenome) and +@fig:fig4_chloroplast_pangenome). Partitioned allignments were processed in IQtree, performing model selection and maximum likelihood tree inference. Matching host species are connected by green ribons; matching samples by blue ones. Inconsistencies in the speciation pattern are indicated by coloured circles.](source/figures/fig4_coevolution_trees.pdf){#fig:fig4_coevolution_trees}
**Fork, this is protein data which makes no sense for something so evolutionary recent. Trees running again with nucleotide data**

The branchlengts between the contradiciting nodes of the tree are quite short.
Therefore, the phylogentic inference was repeated on DNA allignments of the same gene clusters.
DNA sequences of these gene clusters were extracted as partitioned allignments.
IQtree merged the various partitions and fitted models to the alligments: TVM+F+I for Nazollae and blosum62+G4 for the chloroplast.

### genomics/synteny
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

beta-lactam antibiotic genes, rhizosperma may have different way of keeping their leafpocket clean and this is aided by N. azollae. Nazollae defends its niche?

DNA repair and maintainance enriched in rhizosperma --> diversified degradation bewteen rhizosperma and Eukazolla?

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

## Supplemental figures

![Assembly and subsetting of _A. filiculoides_ mitochodrium genome. (A) Flye assembly graph of nanopore reads suspected to be mitocondrial. The assembly graph visualisation was made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches colour coded by blast hits and connections between these contigs as grey transparent lines. Blast hits of the _Psilotum nudum_ and _Ophioglossum californicum_ mitocondrial genomes (orange and red), the _Azolla filiculoides_ chloroplast (green) and _Nostoc azollae_ (cyan blue) are indicated in the assembly graph. A mitocondrial subgraph (indicated in red square) was selected for futher processing. B Blast all-vs-all visualisation with circo's of the mitocondrial subgraph. Several contigs are fully represented in contig 11. (C) Mitocondrial draft assembly manually rid of redundancy. Blast all-vs-all visualisation with circos.](source/figures/fig4_mitochondrium_assembly_selection.pdf){#fig:fig4_mitochondrium_assembly_selection}


![Assembly summary of _N. azollae_ flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_Nazollae_nanopore_assemblies.pdf){#fig:fig4_Nazollae_nanopore_assemblies}

![Assembly summary of chloroplast flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_chloroplast_nanopore_assemblies.pdf){#fig:fig4_chloroplast_nanopore_assemblies}

![Assembly summary of mitochondrium flye assemblies. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs (left) depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Statistics (right) were also generated with Bandage.](source/figures/fig4_mitochondrium_nanopore_assemblies.pdf){#fig:fig4_mitochondrium_nanopore_assemblies}

![Assembly graphs of chloroplast SPAdes assemblies with baited Illumina reads. Assembly graph visualisations were made with Bandage `cite bandage`. The graphs depict contiguous DNA streches as randomly coloured strips and connections between these contigs as grey transparent lines. Illumina reads of serveral _Azolla_ species were selected based on homology to the _Azolla_ filiculoides_ draft mitochondrium and assembled with SPAdes. These species are _A. nilotica_, _A. caroliniana_ 1 & 2, _A. microphylla_, _A. mexicana_ and _A. rubra_. Species names are indicated above snapshots of the assembly graph, as well as the total assembly size and amount of contigs.](source/figures/fig4_chloroplast_spades_assemblies.pdf){#fig:fig4_chloroplast_spades_assemblies}

![Pangenome summary of _Azolla_ mitochondria. Mitochondrial genomes were scanned for ORFs and clustered (MCL=3) on co-occurence frequencies of these ORFs in the various genomes (centre dendrogram). The frequency in which gene clusters occur in a genome is shown as barplots drawn as concentric semi-circles around the dendrogram. Outside the frequency barplots, functional annotation is shown in bright green (NCBI COGGs and KEGG KOFAM). Homogenity of clusters is calculated as geometric (few gaps is high homogeneity), functional (matching amino acid residues is high homogeneity) and a combined version of these two. Adjacent to the geneclusters, several plots are shown. These depict total genome length, GC content, genes per kb, Singleton gene clusters and total number of gene clusters.](source/figures/fig4_Azolla_mitochondrium_pangenome.pdf){#fig:fig4_mitochondrium_pangenome}
