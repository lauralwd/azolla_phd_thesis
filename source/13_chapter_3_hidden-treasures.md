\singlespacing
\setlength{\parindent}{0.0in}
# Hidden treasures: public sequencing data of symbiotic _Azolla_ ferns harbours a genus-wide metagenome
\label{hidden treasures}

\footnotesize

Laura W Dijkhuizen^1^,
Henriette Schluepmann^1^.

\scriptsize

1. Molecular Plant Physiology Department, Utrecht University, Utrecht 3584CH, The Netherlands

\newpage
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

<!---
General notes:
16-18   rewrite highlights
check all figure legends
Final figure binning comparison
--->

## Abstract
Bacteria-host symbioses are present throughout the plant kingdom, and bacteria can contribute all kinds of functions to their host.
The plant genus _Azolla_ is known to host multiple endophytic bacteria, which it transfers systematically to successive generations.
Here we set out to acquire bacterial genomes of _Azolla_ associated bacteria by re-using non-metagenomic data already available in public repositories.
_Azolla_ sequencing data of six species was filtered and assembled with a fully reproducible workflow made in the conda and snakemake frameworks.
Intensive filtering of host DNA data reduced computational requirements but did not increase assembly quality.
The use of binning signals from foreign samples and taxonomy-based signals was helpful but required careful manual curation during the binning process.
High-quality bacterial genomes can be assembled from repository sequencing data, but this requires manual curation.
Re-using public data can be a cost-effective method to acquire such genomes.
We successfully assembled between 12 and 22 bacterial genomes per _Azolla_ species.
The majority belongs to only six taxonomical orders and occurs in most species of the _Azolla_ genus.
Taxonomic consistency of bacterial genomes associated with the _Azolla_ genus suggests these bacteria may be introduced in some common ancestor of _Azolla_ species and may be selected for in the evolution of the _Azolla_ holobiont.

## Introduction
Many bacteria associate with multicellular hosts in symbioses and may convey specific metabolic properties or traits to their hosts.
Such associations may be temporary or occosional; these bacteria are often recruited from the environment of a host triggered by certain conditions.
Alternatively, symbionts may be practically ubiquitous among a hosts species.
They may be housed inside host organs, making them endophytes of their host.
These ubiquitously present symbionts may even be vertically transfered over host generations.
The new host generation thereby inherrits the traits associated with these symbionts.
Such systematic presence in a host species will substantially influence selection pressure on the endophyte genome compared to free-living relatives.
In such a case, a conglomeration of evolving organisms sharing both genomes and selection pressure can occasionally be seen as a holobiont: a single evolutionary unit comprising several organisms [@Zilber-Rosenberg2008].
However, the exact scope and applicability of the term remain subject to debate [@Douglas2016].
Nonetheless, the study of systematically inherited microbes provides opportunities for studying adaptation of bacteria to the symbiotic lifestyle and the traits encoded in a plant's second genome.

Symbiotic endophytes are widespread over the plant kingdom, highly polyphyletic and can attribute various functions to their hosts [@Frank2018; @Hassani2018].
The two most studied endophytes of plants are mycorrhiza and nitrogen-fixing Rhizobiaceae.
These two symbiosis share a common gene set in the host plants, termed the Common Symbiosis Pathway (CSP), even though components of the pathway vary amongst host-bacteria interactions (@Genre2016).
There are, however, several other plant endophytic symbioses that are studied less intensively isolated from various plant organs [@Pinto-Carbo2018; @Frank2018].
One such example, and the subject of this study, is the fern genus _Azolla_.
_Azolla_ ferns harbour symbiotic cyanobacteria, which they systematically transfer to subsequent generations.
@Li2018 showed that the _Azolla filiculoides_ does not encode the CSP, indicating the molecular underpinnings of symbioses in general may be more diverse.

Work on plant-endophyte symbioses often focuses on one symbiotic partner where there could be multiple.
Researchers may isolate, culture or otherwise enrich symbiotic endophytes, which are often lowly abundant compared to plant tissue [@Ran2010; @DeMeyer2019].
Such enrichments substantially improve the efficiency of sequencing the endophytes DNA rather than a bulk DNA extraction that includes the host.
Simultaneously, such processes often increase the selectiveness of a methodology, leaving out any additional organisms to a host-endophyte symbiosis.
Full metagenomic sequencing would be a less biased assessment to study all organisms in a symbiosis, at least when one expects more endophytic microbes.

Full metagenomics sequencing is inefficient if symbionts are lowly abundant in plant tissue, and hence the method becomes highly cost-inefficient.
Alternatively, symbiont genomes may be retrieved from sequencing data already available in data repositories, thereby capitalising on opportunities of the FAIR data age and the diversity thereoff.
We demonstrated this before in chapter \ref{foul play}, where we serendipitously found bacterial genomes as a by-product of the _A. filiculoides_ genome assembly.
@Delmont2016 extracted three bacterial genomes from the tardigrade genome in a similar fashion, using advanced visualisation and multiple sequencing libraries to puzzle apart the scaffolds of multiple organisms in a single assembly.
Additionally, a study may benefit from using public data for the scope of the inquiry can be easily widened to include related species and their metagenomes.
Naturally, the feasibility of such an undertaking depends on data availability in repositories and the complexity of the bacterial community associated with any host.
Given that sufficient data is available, the challenge remains to use metagenomics techniques to retrieve these genomes from data generated in experimental designs not intended for metagenomics.
Such data could be sequencing libraries of bulk DNA extractions, combining host DNA and DNA of associated microbes.
When a host has many microbe associations, this increases demands on the experimental design and variety of input data, especially when these microbes are similar.
One such multi-partite association is the subject studied here: the aquatic ferns of the _Azolla_ genus.

_Azolla_ ferns are particularly interesting to study from a metagenomic perspective.
They host substantial quantities of di-nitrogen fixing symbiotic _Nostoc azollae_ protected inside specialised leaf cavities [@Campbell1893; @Nierzwicki-Bauer1989].
These cavities contain a mucus-like substance [@Forni1998] presumably rich in ammonia [@Newton1976] containing the primary symbiont.
The appropriate genus of the main _Azolla_ symbiont has been prone to debate; it is also known as _Anabaena azollae_ and _Trichormus azollae_.
Here, we name the symbiont _N. azollae_ for consistency with our earlier work.
High sequence identity amongst _N. azollae_ strains taken from various _Azolla_ strains indicates it was likely introduced once in the symbiosis [Chapter \ref{it takes two}\; @Dijkhuizen2021].
Consequently, all cyanobacterial strains endophytic to _Azolla_ are likely are the same cyanobacterial genus, perhaps even species.
At the fern Shoot Apical Meristem (SAM) lies a -somewhat ironically named- 'seed colony of motile _N. azollae_ filaments [Chapter \ref{it takes two}\; @Dijkhuizen2021, @Campbell1893].
Developing leaves encapsulate part of this seed colony as inoculum for every leaf new cavity [@Campbell1893; @Nierzwicki-Bauer1989].
_Azolla_ ferns systematically transfer their symbiotic cyanobacteria to next generations via their megaspores (+@fig:fig1_life-cycle).
Recent papers theorised that the symbiont entered the fern megaspores via small channels [@Ran2010; @Zheng2009].
Contrastingly, we theorise that early developing spore primordia of either gender encapsulate part of the cyanobacterial seed-colony based on confocal imagery [Chapter \ref{it takes two}\; @Dijkhuizen2021], thereby mirroring the mechanism by which inoculates leaves.
Megasporocarps retain the cyanobacteria, which then develop into resting stages called akinetes.
Microsporocarps lose the symbiont throughout their development.
Electron and confocal microscopy of cyanobacterial resting stages inside microspores support this theory [Chapter \ref{it takes two}\; @Dijkhuizen2021, @Caiola1992].

_Azolla_ leaves and spores harbour by at least one other bacterium, as was shown in multiple species [@Gates1980; @Wallace1986; @Petro1987; @Caiola1988; @Plazinski1990; @Cohen2004; @Banach2019].
These additional bacteria are likely limited in number and relatively understudied compared to the main symbiont _N. azollae_.
While these bacteria were observed inside leaf pockets and spores by electron microscopy by various labs [@Wallace1986; @Nierzwicki-Bauer1990; @Carrapico1991; @Zheng2009], it remains unknown if they are also present at the SAM seed colony.
We theorise this is the case, based on their ostensibly systematic presence in multiple _Azolla_ species and increasing abundance in developing _Azolla_ leaves [@Petro1987].
Culture and electron microscopy-based techniques may also not be so reliable to attribute a species identification to a microbe and have led to uncertainty in comparing results generated the previous century.
Conversely, the apparent benefit of culture-based techniques is the availability of bioassays and transformation as in @Banach2019 and @Plazinski1990 respectively.
The uncertainty in classifying bacteria to a genus or species complicates estimating both the identity and diversity of microbes endophytic to _Azolla_ [@Nierzwicki-Bauer1991; @Leonardi1993].
Nonetheless, _Arthrobacter_ is the most well-known genus associated with _Azolla_ ferns in these studies [@Petro1987].
It remains unclear if all species previously characterised by morphological features are the same or distinct bacteria.
In Chapter \ref{foul play} [@Dijkhuizen2018], we found DNA sequences of Rhizobiales and Burkholderiales associated with _A. filiculoides_.
These may be genome sequences of the bacteria observed earlier in earlier work.
Additionally, we found evidence these microbes may be present in the _Azolla_ genus as a whole but not in the surrounding water we sampled, based on 16S data and read recruitment to reference genomes.

Towards the function of _Azolla_ associated bacteria, many theories coexist in the literature that are not mutually exclusive.
In our previous work [Chapter \ref{foul play}\; @Dijkhuizen2018], we wondered whether these bacteria are foul players parasitising on the nitrogen fixed in the _Azolla_ symbiosis or if they are a third symbiotic party of benefit to the symbiosis, as did @Carrapico1991.
The seminal paper on the additional microbes of _Azolla_, @Wallace1986, already found that isolates from _Azolla_ leaves can denitrify NO~3~ to N~2~, indicating these microbes may gain energy from the ammonia fixed by _N. azollae_.
However, in Chapter \ref{foul play} [@Dijkhuizen2018], we found that the microbes whose genomes encode this pathway are outside the plant rather than inside the leaf cavities.
Additionally, we found no pathway to convert NH~4~ to NO~3~ in bacteria associated with _A. filiculoides_.
A second theory is that the additional bacteria are mucilage producers, possibly facilitating a polysaccharide matrix for the _Azolla_-_Nostoc_ symbiosis [@Forni1992; @Zheng2009].
This hypothetical function is mainly attributed to a bacterium identified as _Arthrobacter_ [@Forni1992; @Forni1998].
A third theory is that the additional bacteria inside _Azolla_ leaves may also fix N~2~, mirroring the niche of the cyanobacterial symbiont.
@Lindblad1991 found these enzymes expressed inside _Azolla_ leaf bacteria by immunogold labelling and TEM.
In Chapter \ref{foul play} [@Dijkhuizen2018], we did not find evidence for this process, both in  N~2~^15^ labelling experiments and in the analyses of the genomes we sequenced.
A fourth theory is that these bacteria produce plant growth-promoting factors such as IAA when provided with tryptophan, theoretically reducing tryptophan-inhibition on nitrogen fixation and promoting plant growth by exporting auxin [@Forni1992b; @Forni1996; @Banach2019 ].

Here, we set out to reconstruct all _Azolla_ associated microbial genomes from public sequencing data; some data is part of a metagenomic study design, most is not.
We take a similar approach as @Delmont2016, with two major adaptations: firstly, we remove as much as possible host DNA, and secondly, we broaden the perspective from a single species to a whole genus of species.
One species has been abundantly sequenced in various experimental designs: _Azolla filiculoides_.
Most species, however, have been sequenced once based on a single DNA extraction, as is the case for the _Azolla_ genome project.
The _Azolla_ genome project [@Li2018] provided the research community with the _A. filiculoides_ genome and WGS sequencing data for six of the seven known _Azolla species_.
This recent wealth in _Azolla_ sequencing data provides an opportunity to acquire more genomes of microbes associated with the _Azolla_ genus as a whole.
The experimental design of the _Azolla_ genome project does not facilitate metagenomics of single _Azolla_ species.
Still, we may be able to use metagenomics techniques, thorough data filtering, and specific metagenomic data from other research projects on _Azolla_ species to acquire the genomes of _Azolla_ associated bacteria from this data.

This manuscript presents the methods by which we systematically acquire genomes of bacteria associated with the genus _Azolla_.
We assemble multiple high-quality Metagenome Assembled Genomes (MAGs) for each _Azolla_ species from publicly available data.
In doing so, we make our methods fully reproducible via the Snakemake and conda frameworks and document any progress in the workflow on Github.
Finally, we are glad to share the genomes of all these _Azolla_ associated bacteria with the _Azolla_ community for further studies: The _Azolla_ genus-wide metagenome.

## Methods

### Tools and data availability
In this study, we use various metagenomics tools to acquire genomes of bacterial endophytes associated with an entire genus of hosts
from publicly available bulk DNA extractions.
Sequenced DNA of various sources was iteratively filtered and assembled into contigs with SPAdes [@Nurk2017].
Data was filtered in the first filter stage by mapping [@Li2009a] against a curated reference consisting of host nuclear DNA and chloroplast DNA by @Li2018 (Azfiv1.1 fernbase) (hostfiltered).
For the _Azolla_ genus, only the genome of _Azolla filiculoides_ is available; hence this was used for filtering all _Azolla_ species studied here.
Before use as a filter, the _Azolla filiculoides_ reference genome's taxonomy was rid of any bacterial contigs with CAT [@VonMeijenfeldt2019].
CAT assigned an approximate taxonomy to contigs by first finding all open reading frames (ORFs), then blasting these to a custom database consisting of the NCBI blast NR protein database and all high confidence proteins of the _A. filiculoides_ v1.1 genome assembly.
Only contigs classified as eukaryotic were kept in the filter.
The reads passing the filter were assembled with SPAdes in metagenomics mode [@Nurk2017].
This first filtering step was not expected to perform equally well for all _Azolla_ species, especially those more phylogenetically distant to the reference genome.
Hence in a second filter, eukaryotic contigs were identified in each of the hostfiltered assemblies and used as a second filter tailored to a specific sequencing library.
These double-filtered reads were then assembled again with SPAdes metagenomics mode, and only after this second filtering step hybrid assemblies were generated when multiple sequencing libraries were available per biological sample.
After assembly, scaffolds were binned into Metagenome Assembled Genomes (MAGs) with several tools, then curated manually in Anvi'o [@Eren2015].
To reproducible execute and document these analyses, a bioinformatic workflow was created with snakemake [@Molder2021] and documented in [Github](https://github.com/lauralwd/azolla_genus_metagenome).
All tools used in this snakemake workflow are selected and installed from the Bioconda repository of bioinformatics software.
Conda environments used in this study can be found in [github env link](https://github.com/lauralwd/Azolla_genus_metagenome/tree/master/envs).

### Data
Sequencing data used here represented six of seven species in the _Azolla_ genus and was generated as part of three studies (+@fig:fig3_data-overview).
These species are part of two subgenera, the _Rhizosperma_ section of the genus comprising _Azolla pinata_ and _Azolla nilotica_, and the _Euazolla_ section comprising the other four species (+@fig:fig3_data-overview\-A)
Within the _Euazolla_ section, two subclusters of closely related species can be distinguished; firstly _A. rubra_ and _A. filiculoides_ and secondly _A. mexicana_, _A. microphylla_ and _A. carolinana_.
These subclusters diverged between 10 and 20M years ago.
The _Rhizosperma_ section is represented only by _A. nilotica_ here and is estimated to have diverged from the _Euazolla_  section approximately 50M years ago (+@fig:fig3_data-overview\-A [@Metzgar2007].
The first published data of _Azolla_ Whole Genome Sequencing (WGS) data was Chapter \ref{foul play} [@Dijkhuizen2018].
In that study, we sampled _A. filiculoides_ from triplicate whole plant fractions and triplicate leaf-pocket enriched fractions (P1,2,3 and L1,2,3 respectively; +@fig:fig3_data-overview\-B).
Secondly, the _Azolla_ genome project [@Li2018] published short-read sequencing data of six _Azolla_ species, including _A. filiculoides_ and long-read sequencing of _A. filiculoides_ (+@fig:fig3_data-overview\-B).
Sequencing data is mainly generated on Illumina platforms with typical insert sizes of 400 to 800bp and typically yielding approximately 30Gbase of DNA, except for the P and L samples which yield 2 to 3Gbase per sample (+@fig:fig3_data-overview\-B).
Both studies' their _A. filiculoides_ samples originate from the same Ditch in Utrecht, the Netherlands.
One sample was treated to remove the most abundant symbiont: _N. azollae_ and is indicated as the no-cyano sample (+@fig:fig3_data-overview\-B).
All samples acquired from the International Rice Research Institute (IRRI) were maintained for approximately two decades by the IRRI by vegetative propagation [@Watanabe1992] (+@fig:fig3_data-overview\-B).
These plant strains were sampled at various locations around the globe (+@fig:fig3_data-overview\-C): _Azolla nilotica_, _Azolla rubra_, _Azolla mexicana_, _Azolla microphylla_, and two _Azolla_ samples, which were initially classified as _Azolla carolinana_ but are likely a new _Azolla_ species, here termed, _Azolla sp.nov._ [Chapter \ref{it takes two}\; @Dijkhuizen2021]
The third data source is the seminal paper introducing the _N. azollae_ genome sequence [@Ran2010].
This paper includes ion-torrent sequencing of a gradient purified extraction of the primary symbiont of _A. filiculoides_.
Data of the latter study was acquired from SRA: for the first and last studies via the accession numbers listed in +@fig:fig3_data-overview\-B.
Data of the _Azolla_ genome project was made available to our lab before it was uploaded to a repository.
Unfortunately, we cannot link the sample identities of the data made available to us, with those uploaded to NCBI SRA, hence,  we refer to the study as a whole.
In total, this study examines eighteen sequencing libraries, taken from nine biological samples accounting for six _Azolla_ species, treating L1,2,3, P1,2,3 combined as one biological sample.

\begin{sidewaysfigure}
\begin{figure}
\hypertarget{fig:fig3_data-overview}{%
\centering
\includegraphics{source/figures/fig3_data-in-overview.pdf}
\caption{
  DNA sequencing of the \emph{Azolla} genus. The \emph{Azolla} genus phylogeny adapted from Metzgar et al. (2007) (A). Sequencing data considered here for species in the \emph{Azolla} genus (B).
  Sequencing data was retrieved from two main studies:
  the \emph{Azolla} genome project from Li et al. (2018) with accession nr. PRJNA430527 and from
  Chapter \ref{foul play} (Dijkhuizen et al. 2018) with accession nr. PRJEB19522 abbreviated as α and β
  respectively in the final column of panel 1B.
  Sampling details are available in the latter paper.
  The original sampling location for \emph{Azolla} specimens sequenced and considered here (C).}
\label{fig:fig3_data-overview}
}
\end{figure}
\end{sidewaysfigure}

## Results

### Filtering of _Azolla_ sequencing data against host DNA reduces assembly size and the computational requirements thereof
First, we set out to rid raw WGS data from plant DNA to ease assembly of the bacteria whose genomes are also present in this data.
Filtering reduces input complexity and hence reduces complexity in the assembly graph, possibly improving metagenome assembly quality.
The bioinformatic workflow developed here, takes short read DNA sequencing data as a main input, then itteratively removes host reads and finally assembles the remainder into contigs (+@fig:fig3_filtering-and-assembly\-A).
The first stage of host DNA removal is achieved by mapping DNA reads that passed trimmomatic Quality Control (QC) to a reference genome [@Bolger2014], then assembling the remaining reads into contigs with SPAdes in metagenomics mode [@Nurk2017] (host filtered).
QC removed on average 4.4% and no more than 7% of reads of any of the sequencing libraries (+@fig:fig3_filtering-and-assembly\-B; bottom).
Filtering with the reference genome reduced read input substantially for _A. filiculoides_ (51% of reads for lab samples and 79% for no-cyano samples; +@fig:fig3_filtering-and-assembly\-B; bottom; _Azolla filiculoides_).
Filtering efficiency deminished substantially even for species phylogenetically close (+@fig:fig3_data-overview\-A) to the reference genome such as _A. rubra_ 24% (+@fig:fig3_filtering-and-assembly\-B; bottom; _Azolla rubra_), and other species in the _Azolla_ section of the genus (between 18% and 20%) (+@fig:fig3_filtering-and-assembly\-B; bottom).
This first filtering step removed only 8% of reads for the phylogenetically distant _A. nilotica_ (+@fig:fig3_filtering-and-assembly\-B; bottom; _Azolla nilotica_).
Assemblies after this first filtering step (host filtered) were typically around 600 Mbase and hence likely contain substantial amounts of host DNA still (+@fig:fig3_filtering-and-assembly\-B; top).

To further improve filtering efficiency, a second filtering strategy was applied.
Assembled contigs of all hostfiltered assemblies were classified with CAT [@VonMeijenfeldt2019], and contigs classified as eukaryotic were used as a second filter specific for that particular sequencing library.
Contigs classified as eukaryotic did not contain substantial amounts (1Mbase or higher in all assemblies combined; [lauradijkhuizen.com/blog/AGMB](lauradijkhuizen.com/blog/AGMB)) of DNA classified as anything other than streptophyta hence the assemblies contain only one eukaryote: _Azolla_ ferns.
The efficacy of this second stage of host DNA removal was typically opposite to the former stage: being least effective for _A. filiculoides_ (no more than 11%) and _A. rubra_ (25%), whilst most effective for those farther removed in the phylogeny; i.e. 42% for _A. microphylla_ and 56% of _A. nilotica_ (+@fig:fig3_filtering-and-assembly\-B bottom filtered vs. double filtered).
Combined, both filtering approaches removed between 50% and 64% of reads from plant samples that were maintained in the lab and not experimentally treated (+@fig:fig3_filtering-and-assembly\-B trimmed vs double filtered).
The double filtered reads were assembled again with SPAdes in metagenomics mode, both as single libraries or as hybrid assemblies when multiple sequencing libraries or read types were available per biological sample (+@fig:fig3_filtering-and-assembly\-B top; H).
Assembly sizes were reduced substantially after the second filtering step for all species except for _A. filiculoides_ samples with lower insert sizes (+@fig:fig3_filtering-and-assembly\-B top).
Metagenome Assembly sizes typically varied from 160 to  250 Mbase, with exceptions for the _A. filiculoides_ wild sample (738 Mbase), the sterilised _A. filiculoides_ no-cyano sample (60 Mbase), and the _A. spnov._ 2 sample (456 Mbase) (+@fig:fig3_filtering-and-assembly\-B top).
The double filter typically reduced assembly size by 60% to 70% (+@fig:fig3_filtering-and-assembly\-B top).
Reduced assembly size and host DNA contamination make manual binning feasible and metagenome assembly sizes (+@fig:fig3_filtering-and-assembly\-B top) indicate that all assemblies likely contain multiple bacterial genomes.
Secondly, removing host DNA from the assembly input reduces input complexity and thereby substantially reduced computational requirements for assembly in terms of peak RAM usage (+@fig:fig3_filtering-and-assembly\-B RAM usage).

![Filtering and assembly of DNA sequencing of the _Azolla_ genus. Sequencing filtering workflow and guide to the graph (A). Quantities of sequencing input in Gbase (B; bottom), corresponding assembly output during the process (B; top), and the peak RAM usage during the assembly process (B; RAM usage). The bottom panel shows consequtive sequencing quantities at raw, trimmed, hostfiltered, and double filtered stages. At the latter two stages, sequencing data was assembled with SPAdes. The upper half of panel B shows assembly RAM usage in Gbyte and assembly sizes in MBase for both filtering stages of single sequencing library assemblies, and for hybrid assemblies if applicable.](source/figures/fig3_sequencing-filtering-and-assembly.pdf){#fig:fig3_filtering-and-assembly}

### Filtering reduced eukaryotic DNA content but did not increase assembly quality of bacterial DNA
Filtering input sequencing data reduced assembly size, next we investigate the efficacy of this filtering approach in terms of taxonomic complexity and quality of the assembly.
The main rationale for this intensive filtering approach was to decrease complexity in the metagenome assembly graph; thereby improving the length and quality of assembled bacterial contigs.
The double filtering step substantially reduced total assembly size (+@fig:fig3_filtering-and-assembly\-B top) and length distributions of eukaryotic contigs (+@fig:fig3_filter-length-distributions Eukaryota, +@tbl:tbl3_1), as well as contigs which were not assigned a taxonomy or did not yield any open reading frames (+@tbl:tbl3_1).
These latter two taxonomical categories often had similar depth/length distributions as scaffolds assigned Eukaryota ([lauradijkhuizen.com/blog/AGMB](lauradijkhuizen.com/blog/AGMB)).
In contrast, bacterial assembly size and length distributions were practically identical between the two different filtering stages (+@fig:fig3_filter-length-distributions Bacteria), although the average and median scaffold size did increase slightly (+@tbl:tbl3_1 Bacteria).
Contigs assigned as Archeal in the hostfiltered assembly, were not classified as such in the doublefiltered assembly (+@fig:fig3_filter-length-distributions Archaea).
Similarly, viral contigs often were only assembled in the hostfiltered assembly (+@fig:fig3_filter-length-distributions Viruses).
The bacterial fraction of the metagenome assembly is of substantial size and was not negativelly affected by the filtering approach, thereby paving the way to investigate the diversity of bacterial genomes in this fraction.

filter stage    | superkingdom  | contig count |scaffold count | total scaffold length (Mb) | median scaffold length (kb) | average scaffold length (kb)
-----           |    -----      | ---   |  ---  | --- |  ---  |  ---
host filtered   | Bacteria	    |	44861 | 48500	| 814	| 5666	| 16775
double filtered | Bacteria      |	44742 | 48304	| 812	| 5671	| 16816
host filtered   | Eukaryota	    |	70168 | 70273	| 636	| 5588	|  9045
double filtered | Eukaryota     |	  612 |   960	|   4	| 3382	|  4068
host filtered   | not classified|  2872 |  2302	|  21 |	5470  |	 8914
double filtered | not classified|   507 |   536	|   3 |	3626	|  4971
host filtered   | no ORFs found |120555 |112519 |	762	| 4748	|  6768
double filtered | no ORFs found | 19523 | 25323	| 101	| 3282	|  3989

Table: Assembly statistics per superkingdom before and after the second filtering stage. Only contigs and scaffolds longer than 2.5kbp are included. {#tbl:tbl3_1}

\begin{sidewaysfigure}
\begin{figure}
\hypertarget{fig:fig3_filter-length-distributions}{%
\centering
\includegraphics{source/figures/fig3_figure-filter-length-distributions.pdf}
\caption{Length distrubtions of \emph{Azolla} sp. metagenome assembles per kingdom before and after two stages of filtering.
  Metagenome assemblies of individual sequencing libraries (\cref{fig:fig3_data-overview}) were filtered with the Host genome (Host filtered; red) and with a library specific subset of eukaryotic contigs (Double filtered; blue; \cref{fig:fig3_filtering-and-assembly}).
  Scaffolds of metagenome assemblies were assigned taxonomy with CAT (Von Meijenfeldt \emph{et al}. 2019) and their length distributions were plotted as boxplot per taxonomic kingdom (vertical pannels: Virusses, Eukaryota, Bacteria and Archae) per sequencing library (horizontal pannels).
  Width of the boxplot is propportional to the amount of scaffolds represented (\cref{tbl:tbl3_1}).}
\label{fig:fig3_filter-length-distributions}
}
\end{figure}
\end{sidewaysfigure}

### Filtered metagenome assemblies contain distinct microbial genomes systematically reoccuring in the _Azolla_ genus
The double filtered assemblies contain numerous bacterial contigs of each _Azolla_ species sampled here (+@fig:fig3_filter-length-distributions Bacteria).
Next, we take a genus perspective and compare these assemblies by the taxonomy and abundance, now counting scaffolds rather than contigs.
Bacterial scaffolds in all doublefiltered assemblies had a median length of 5671 bp; hence, bacterial genomes in the assembly are highly fragmented.
Despite this fragmentation, scaffolds group into approximate bacterial genomes quite distinctly when examining them by their abundance, length, and taxonomy as determined by CAT (+@fig:fig3_Azolla-genus-metagenome-order).
The genomes can be recognised as clusters of scaffolds with equal abundance and taxonomy but varying scaffold length (+@fig:fig3_Azolla-genus-metagenome-order).
All samples but the no-cyano sample (+@fig:fig3_Azolla-genus-metagenome-order Azfil_minuscyano) show the most abundant species in the metagenome is a Nostocales cyanobacterium (+@fig:fig3_Azolla-genus-metagenome-order cyan blue).
Rhizobiales genomes were found in all _Azolla_ species sampled here, visible as horizontal clusters of dots with identical colour (+@fig:fig3_Azolla-genus-metagenome-order purple).
Plotting the scaffolds of all assemblies by these two characteristics allows to distinguish individual bacterial genomes in each of the _Azolla_ species sampled here (+@fig:fig3_Azolla-genus-metagenome-order).

\begin{sidewaysfigure}
\begin{figure}
\hypertarget{fig:fig3_Azolla-genus-metagenome-order}{%
  \centering
  \includegraphics{source/figures/fig3_Azolla-genus-metagenome-order.png}
  \caption{Metagenome assemblies of 6 species of the fern genus Azolla (horizontal panels).
    Sequencing data was derived from three public projects \cref{fig:fig3_data-overview}.
    Sequencing reads were rid of host plant DNA reads and assembled with SPAdes in metagenome mode \cref{fig:fig3_filtering-and-assembly}-A.
    Resulting scaffolds were then assigned an approximate taxonomy with CAT (VonMeijenfeldt \emph{et al}. (2019)).
    Metagenome assembly scaffolds are displayed as dot plots with length on the x-axis and depth in the assembly graph on the y-axis; both log10 transformed.
    Dot colour represents the taxonomical order and dot size represents ORF count.
    Scaffolds without ORFs and scaffolds without taxonomy are filtered out for clarity.
    Additionally, scaffolds are filtered if they have less than 5 ORFs classified or when a taxonomic group amounts to less than 2Mbase in the entire figure.
    An \href{https://utrecht-university.shinyapps.io/Azolla_genus-wide_metagenome_taxonomy/}{online interactive version of this figure} can be manipulated to modify these filters and assumptions, and to include more assemblies done in the \emph{Azolla} metagenome project.
    }
    \label{fig:fig3_Azolla-genus-metagenome-order}
}
\end{figure}
\end{sidewaysfigure}

Even before binning scaffolds into MAGs, metagenomes of the _Azolla_ genus show clear similarities amongst each other; several taxonomical orders reoccur systematically (+@fig:fig3_Azolla-genus-metagenome-order).
Most prominently, the Nostocales, which are the most abundant order in all _Azolla_ species except one which was artificially devoid of the cyanobacteria.
Contigs assigned Nostocales have a high variance in abundance, standard deviations vary in the various samples from 300 to 600 (arbitrary unit representing depth in the assembly graph; +@fig:fig3_Azolla-genus-metagenome-order; [lauradijkhuizen.com/blog/AGMB](https://www.lauradijkhuizen.com/blog/AGMB)).
In contrast, other clearly distinghuishable microbial genomes show a typical depth standard deviation often lower than 1, but in almost all cases lower than 10 (depth variance visible in interactive figure).
This abundance pattern of _Nostoc azollae_ is typical of a degraded genome with many transpons and reptitive regions and may explain why the assembled length of this MAG is shorter than the reference; 4Mbase rather than 6Mbase (+@tbl:tbl3_2).
Yet, it might also indicate an upper limit of assembly depth.
The second most abundant order accross the genus, is the Rhizobiales, ranging between 16 and 44 Mbase of assembled DNA in the different samples (+@fig:fig3_Azolla-genus-metagenome-order blue; [lauradijkhuizen.com/blog/AGMB](https://www.lauradijkhuizen.com/blog/AGMB)).
In all host species, multiple Rhizobiales genomes can be distinghuised.
The third most abundant order is the Burkholderiales (+@fig:fig3_Azolla-genus-metagenome-order yellow), which is present in all host species except for _A. rubra_ and amounts to between 5 and 17 Mbase per assembly ([lauradijkhuizen.com/blog/AGMB](https://www.lauradijkhuizen.com/blog/AGMB)).
Other notable orders that reoocur in several metagenome assemblies are the Caulobacterales, Nevsiales and Sphingomonadales.
Each of these last three orders occurs in at least five of the six samples host species, and are found in data from different studies.

Metagenome assemblies likely do not fully represent all bacteria present in the original plant samples.
When approaching the least abundant scaffolds, scaffold length deminishes to less than 1Kb, indicating the lower abundance limit of assembly.
This lower limit region does contain a substantial amount of scaffolds from different orders of taxonomy.
This indicates that several low abundant microbes were too lowly abundant to assemble propperly, and hence the current assemblies are likely incomplete representations of the micribial diversity associated with these plants.
An exception to this observation are the _A. filiculoides_ minus_cyano samples, here all scaffolds assembled are highly abundant and scaffolds are rather long compared to non-sterilised plant samples.
Hybrid assemblies are a second exception to this observation.
In these assemblies, final graph resolution was aided by PacBio long reads from the _A filiculoides_ minus_cyano sample.
In this process, low abundant scaffolds were combined into longer scaffolds aided by long read data.
However, the scaffold abundance remains a reflection of the original Illumina contribution to that scaffold only but it is corrected for the new scaffold length; explaining why such long scaffolds can have such a low abundance.

### _Azolla filiculoides_ contains multiple endophytic bacteria
Contigs of metagenome assemblies were manually binned into MAGs.
First, metagenome assemblies were binned automatically by both metabat2 and concoct based on their 4mer profiles and differential abundance in various sequencing libraries.
Then, these automatically generated MAGs were imported into Anvi'o and curated manually while being guided by the automated binning and scaffold taxonomy determined by CAT.

The _A. filiculoides_ wild sample metagenome contains multiple high quality MAGs of which several are likely from species living inside the plant leaf cavities.
Only sequencing data of the _A. filiculoides_ wild sample was derived from a metagenomic study design, including samples of whole plants and leaf-pocket enriched 'juice'.
Separating the different MAGs in this metagenome assembly benefits from differential sampling and the consequent differental abundance of genomes per sample (+@fig:fig3_Azfil-wild-binningsignals).
Additionally, the PacBio RSIIlong read sequencing of the _A. filiculoides_ minus-cyano sample which was used as an additional binning signal to distinghuish MAGs from each other, as this data was also used during the final stages of assembly of the _A. filiculoides_ wild sample.
Several MAGs of similar taxonomy, i.e. Rhizobium, Rhizobiales, etc., could be resolved into well distinghuised high quality MAGs.
Binning yielded 7 high quality bins in total (completeness > 90% redundancy < 10%) with appropriate genome sizes, 3 medium quality MAGs also with appropriate sizes(completeness > 60%), and several low quality bins likely representing partial genomes of low abundant bacteria. (+@tbl:tbl3_2).
Despite the metagenomic study design, not all bins could be resolved to high quality.
This may be related to the relatively low input of DNA sequencing in the assembly, hence not allowing to resolve lowly abundant microbial genomes sufficiently.
Differential sampling, comparing whole plant to leaf cavity enrichments, allows to estimate whether a MAG is more abundant in the leaf cavities.
The bacteria represented by these MAGs are likely endophytes of _A. filiculoides_ (+@fig:fig3_Azfil-wild-binningsignals; blue rings).
This is the case for MAGs 'Rhizobium','Rhizobiales','Curvibacter', and 'Ferrovibrio' (+@fig:fig3_Azfil-wild-binningsignals).
The former two are substantialy abundant in PacBio long read sequencing of the _A. filiculoides_ minus_cyano sample, indicating they survived a stringent sterilisation and antibiotic regime removing the main symbiont _N. azollae_.
In constrast, a second cyanobacterium found in the bins, is present only on the outside of the ferns, and not in the leaf cavity enriched fraction, indicating that this is an epithitic cyanobacterium and consistent with earlier findings that _Azolla_ has only one cyanobacterial symbiont.

![Anvi'o overview of the _A. filiculoides_ 'wild' metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (light green), scaffold abundance in PacBio reads from the _A. filiculoides_ 'lab' sample (yellow). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_2.](source/figures/fig3_Azfil_wild_binning.pdf){#fig:fig3_Azfil-wild-binningsignals}

### Binning assemblies from non-metagenomic data is feasible with extragenous binning signals
Provided with thoroughly filtered metagenome assemblies, the binning process becomes feasible even if the assembly lacks a metagenomic study design.
Typically, binning would depend highly on the depth of scaffolds in one sequencing library and on k-mer profiles of  scaffolds.
Here, we employed a manual method adding extragenous binning signals from the one metagenomic study done on this genus, the seminal paper on the _N. azollae_ genome, and scaffold taxonomy determined by CAT.
No automated binning algorith can implement these binningsignals while also accounting for the nuances required in interpreting them, hence automated binning algorithms will likely produce false MAGs.
Using Anvi'o, it is possible to visualise aforementioned extragenous binning signals and bin scaffolds manually whilst accounting for the nature of different binning signals appropriately.
Within Anvi'o, all metadata was plotted for every biological sample as in +@fig:fig3_Azmic-binningsignals.
Next, scaffolds were binned manually, guided at first by autmated binning methods, but primarily by scaffold depth in the native sequencing libraries for that particular biological sample.
Contig depth was often the most clear binning signal in these samples (+@fig:fig3_Azmic-binningsignals).
Abundance in _A. filiculoides_ 'wild' sequencing was used carefully when applicable, and checked with anvi'o clustering based only on k-mer profiles.
Using metagenomic sequencing data from another species in the genus relies on the assumption that a bacterium might be shared among these species and risks not binning genome rearangements that have occured.
This extragenous binning signal was not informative for most MAGs from non-_A. filiculoides_ species but it was for some for some MAGs, for example in _A. mexicana_ (Supp fig. X) and _A. spnov. (Supp fig. X).
Finally, scaffold taxonomy was considered as an indication to support specific groupings of scaffolds.
Contig taxonomy often showed discrete patterns matching the input dendrogram and binning when other binning signals were already distinctive, thereby further solidifying CAT taxonomy as a valuable binning signal.

Manual binning with extragenous binning signals and scaffold taxonomy provided high quality bins for alle metagenome assemblies. `Can I visualise this somehow...``
For exmple in _A. microphylla_ where are MAGS are poorly distributed on the main dendrogram and hard to distinghuish (+@fig:fig3_Azmic-binningsignals).
Still, manual binning of _A. microphylla_ yielded ninteen MAGs of which eleven can be considered high quality and four medium quality, all with appropriate genome sizes. (+@tbl:tbl3_3),
Note that the clustering dendrogram was based on sequencing depth in all samples and scaffold kmer profile, but not scaffold taxonomy.
Similar results were obtained for all other plant samples and using the same methodology (supplemental figures X-X).

![Anvi'o overview of the _A. microphylla_ 'wild' metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (light green), scaffold abundance in PacBio reads from the _A. filiculoides_ 'lab' sample. Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_3.](source/figures/fig3_azmic-metagenome-binning.png){#fig:fig3_Azmic-binningsignals}

\newpage
\begin{threeparttable}
\begin{longtable}[]{@{}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.25}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.30}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.08}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.08}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.1}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}@{}}

\caption{MAG quality of MAGs assembled from sequencing data derived from the \emph{A. filiculoides} 'wild' sample.
         Quality is assessed as approximate genome completion and redundancy by two distint tools: Anvio (Eren et al. 2015) and CheckM (Horton et al. 2014).
\label{tbl:tbl3_2}}\tabularnewline

\toprule
taxonomical order\tnote{a}    &
MAG name\tnote{b}             &
\rotatebox{45}{MAG length (Mbase)}            &
\rotatebox{45}{abundance ratio\tnote{c}}      &
\rotatebox{45}{PacBio mean coverage\tnote{d}} &
\rotatebox{45}{Anvi'o completeness\tnote{e}}  &
\rotatebox{45}{Anvi'o redundancy\tnote{e}}    &
\rotatebox{45}{CheckM completeness\tnote{e}}  &
\rotatebox{45}{CheckM redundancy\tnote{e}} \\
\midrule
\endhead

Caulobacterales   & Caulobacter       &  3.97 &  0.09 &   0.79 &  82 &  3 & 84 &  2 \\
Burkholderiales   & Comamonadaceae    &  4.16 &  0.55 &   9.37 &  93 &  4 & 94 &  2 \\
Burkholderiales   & Curvibacter       &  3.57 &  2.91 &   4.04 &  96 &  4 & 97 &  1 \\
Nostocales        & Cyanobacteria     &  5.75 &  0.02 &   0.90 &  96 &  6 & 98 &  0 \\
Rhodopspirillales & Ferrovibrio       &  4.05 &  5.27 &   0.78 &  66 &  7 & 86 &  2 \\
Burkholderiales   & Polaromonas       &  5.15 &  1.03 &   2.97 &  75 & 24 & 64 & 11 \\
Rhizobiales       & Rhizobiales       &  5.34 &  1.17 &  24.66 &  92 &  6 & 87 &  3 \\
Rhizobiales       & Rhizobium         &  5.25 &  2.18 &  59.73 &  99 & 11 & 99 &  2 \\
Rhodopspirillales & Rhodospirillaceae &  5.42 &  0.45 &   1.25 & 100 &  1 & 99 &  1 \\
Nostocales        & Nostoc            &  4.79 &  1.68 &   0.45 &  96 &  3 & 98 &  0 \\
Burkholderiales   & rest\_1           &  2.49 &  0.54 &   0.36 &  37 &  7 & 23 &  2 \\
Nevskiales        & rest\_2           &  4.19 &  0.47 & 105.93 &   0 &  0 & 73 & 13 \\
NA                & rest\_3           &  1.09 &  0.37 &  79.47 &   0 &  0 &  5 &  0 \\
Rhizobiales       & rest\_4           &  0.86 &  0.20 &  10.88 &  28 &  6 & 19 &  1 \\
Burkholderiales   & rest\_5           &  3.38 &  0.06 &   0.07 &  39 & 10 & 26 &  2 \\
Rhizobiales       & rest\_6           &  3.40 &  1.63 &   0.37 &  30 &  0 & 42 &  0 \\
Rhizobiales       & rest\_7           &  1.36 &  0.69 &   0.11 &   0 &  0 & 14 &  0 \\
\bottomrule
\end{longtable}

\begin{tablenotes}
  \footnotesize
  \item[a] Taxonomic order determined by BAT taxonomy (VonMeijenfeldt \emph{et al.} (2019)
  \item[b] manually assigned name
  \item[c] Mean coverage in leaf pocket samples over mean coverage of whole plant samples from the Dijkhuizen. \emph{et al.} (2018) study.
  \item[d] Mean coverage of PacBio RS II reads from Li \emph{et al.} (2018)
  \item[e] MAG completeness and redundancy assessed via Single Copy Marker Gene scoring
  \end{tablenotes}

\end{threeparttable}

### Decontaminated metagenome assemblies provide up to 22 bins per biological sample
Manual binning with extragenous binning signals yields between 12 and 22 bins for each non-sterilised _Azolla_ sample of which the majority is considered to be a high quality bin (+@tbl:tbl3_4).
Automated binning of the same data with metabat2 and concoct performed `make table`


Fig 7: visual summary of completeness, redundance per metagenome (per binning method?)

```
The point I'd like to examine here, is if I can show in numbers, that the manual binning does better quality wise then:
 1. automated binning.
 2. single-(host) filtered binning
 I'm quite sure that is the case, but need to show that in numbers here first.
 The double filtering workflow did not improve assembly quality of the bacterial fraction, but it does enable manual binning and hence improves quality of the final bins.
 This would be the techinal take-away of the methods part of this manuscript
 The biological take-away, the genus wide systematic occurance, is for the next section:
```
\begin{threeparttable}
\begin{longtable}[]{@{}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.3}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}@{}}

\caption{MAG yield per biological sample and their quality as assessed
  by presence of single copy marker genes via both Anvi'o and CheckM.
  \label{tbl:tbl3_4}}
\tabularnewline

\toprule
Species \& Sample                                         &
\rotatebox{45}{total nr. of bins}                         &
\rotatebox{45}{metagenome fraction in bins (\%)\tnote{b}} &
\rotatebox{45}{bins passing Anvi'o QC\tnote{a}}           &
\rotatebox{45}{bins passing CheckM QC\tnote{a}}           \\
\midrule
\endhead
\emph{Azolla mexicana}                    & 22 & 89 & 12 & 13 \\
\emph{Azolla nilotica}                    & 20 & 84 &  9 & 10 \\
\emph{Azolla microphylla}                 & 19 & 79 & 14 & 15 \\
\emph{Azolla filiculoides} 'wild'         & 18 & 36 &  8 &  9 \\
\emph{Azolla filiculoides} 'lab'          & 17 & 73 & 10 & 13 \\
\emph{Azolla carolinana} 1                & 15 & 79 &  9 &  9 \\
\emph{Azolla carolinana} 2                & 13 & 71 & 12 & 12 \\
\emph{Azolla rubra}                       & 12 & 85 &  9 &  9 \\
\emph{Azolla filiculoides} 'minus-cyano'  &  5 & 84 &  5 &  5 \\
\bottomrule
\end{longtable}

\begin{tablenotes}
  \footnotesize
  \item[a] Passing QC means over 70 completeness and less than 20 redundancy.
  \item[b] Calculated as the percentage of bases from scaffolds over 2.5kbp that are part of any bin.
\end{tablenotes}

\end{threeparttable}

### Systematic occurence of taxonomical orders in the entire _Azolla_ genus
Next, we assessed whether MAGs of certain taxonomical orders reoccur systematically in the _Azolla_ genus as scaffolds did in +@fig:fig3_Azolla-genus-metagenome-order.
When counting bins classified to the aforementioned orders across all biological samples, a similar pattern can be seen.
Rhizobiales bacteria can be found in multiple bins associated with any of the _Azolla_ species examined, ranging from 4 to 8 bins.
Burkholderiales bacteria can be found in all but one biological sample, and in all of the examined species.
These two orders of bacteria are also the two orders present in the _A. filiculoides_ minus_cyano sample, and hence survived intensive sterilisation and antibiotic treatment.
Bins of these orders were also found to be endophytic in _A. filiculoides_ 'wild'.
Both types of evidence support their endophytic status in both _A. filiculoides_ and the _Azolla_ genus as a whole.
Caulobacterales were found in all _Azolla_ species except for _A. nilotica_, Nevskiales were found in all species except for _A. nilotica_ and _A. microphylla_, and Sphingomonadales were found in all species except for _A. rubra_.
These three those orders were not systematically found in all _Azolla_ species, but were found in plants sampled at different locations and sequenced in different labs.

\begin{longtable}[]{@{}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.3}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 18\tabcolsep) * \real{0.05}}@{}}

\caption{MAGs present per biological sample per taxonomical order.
\label{tbl:tbl3_5}}
\tabularnewline

\toprule
order &
\rotatebox{45}{\emph{Azolla filiculoides} 'lab' }       &
\rotatebox{45}{\emph{Azolla filiculoides} 'minus-cyano'}&
\rotatebox{45}{\emph{Azolla filiculoides} 'wild'}       &
\rotatebox{45}{\emph{Azolla mexicana}}                  &
\rotatebox{45}{\emph{Azolla microphylla}}               &
\rotatebox{45}{\emph{Azolla nilotica}}                  &
\rotatebox{45}{\emph{Azolla rubra}}                     &
\rotatebox{45}{\emph{Azolla carolinana} 1}              &
\rotatebox{45}{\emph{Azolla carolinana} 2}              \\
\midrule
\endhead
Burkholderiales   & 2 & 1 & 6 & 4 & 2 & 5 & 1 & 1 & 0 \\
Caulobacterales   & 0 & 0 & 1 & 1 & 3 & 0 & 1 & 2 & 4 \\
Nevskiales        & 1 & 0 & 1 & 1 & 0 & 0 & 1 & 2 & 1 \\
Nostocales        & 1 & 0 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
Rhizobiales       & 8 & 3 & 5 & 8 & 5 & 6 & 5 & 4 & 5 \\
Sphingomonadales  & 1 & 0 & 0 & 2 & 1 & 1 & 0 & 1 & 1 \\
\bottomrule
\end{longtable}

## Discussion
In this study, we acquired high quality MAGs from non-metagenomic sequencing data of 6 species of the _Azolla_ genus (+@fig:fig3_data-overview) through a process of thorough filtering (+@fig:fig3_filtering-and-assembly) thereby substantially reducing the fraction of eukaryotic DNA whilst not impacting Bacterial assembly quality (+@fig:fig3_filter-length-distributions).
Each species' metagenome assemblie contained several distinct bacterial genomes and these assemblies resembled each other in terms of taxonomy (+@fig:fig3_Azolla-genus-metagenome-order).
Manual binning allowed to retrieve these MAGs `better than automated binning approaches` and provide them to the _Azolla_ and plant-microbe research community (+@fig:fig3_Azfil-wild-binningsignals; +@fig:fig3_Azmic-binningsignals).


### Metagenome assemblies can be retrieved from publicly available non-metagenomic data
Acquiring metagenomes from public sequencing data not originally meant for metagenome assembly is feasible and may be further applied to shed light on the mechanisms of host-microbe symbioses.
Researchers interested in metagenomes may use a similar method as demonstrated here to mine existing data for microbial genomes.
This is especially interesting if a host species is already known or suspected to host bacteria, or if bacterial DNA was previously identified in reads or assemblies of a sequencing run as was the case for _Azolla_.
However, not all eukaryotic species or DNA extractions will encompass substantial fractions of DNA from associated bacteria.
Before thorough and costly filtering and assembly, sequencing data may be searched for signs of bacterial genomes as we have done in Chapter \ref{foul play} [@Dijkhuizen2018].
Such signals could be extracted from raw sequencing data for example by searching for rRNA reads (emirge, ribotagger, many more), for bacterial genes (RAT Tina) or by kmer based approaches such as kraken2.
This approach allows us to find bacteria associated with host species we have already studied in the past and hence mine host-bacteria interactions in a great variety of data of past experiments and from a variety of labs as demonstrated here.

Many plant species are known to interact with bacteria systematically and even transmit these systematically [@Frank2018; @Pinto-Carbo2018], but the mechanisms underpinning symbiosis are often unclear.
The best known mechanism is termed the common symbiosis pathway, variations of this common pathway facilitate both Rhizobiales-legume and mycohorriza symbiosis [@Genre2016].
But other symbioses, like Cuanobacteria-plant symbises and ... , are not facilitated by this pathway [@Li2018] `more examples would be nice`.
Mining the genomes of symbiotic bacteria already hidden away in host sequencing data may allow comparative genomics of symbionts on a large scale and further elucidation of the mechanisms of plant-microbe symbioses.

High quality MAGs can be assembled from bulk DNA extractions with minimal filtering, but this process requires manual curation and interpretation.
The doublefiltering of bulk DNA sequencing proved effective in removing host DNA even if no host genome was available (+@fig:fig3_filtering-and-assembly) and provided clean metagenome assemblies with distinct clusters of scaffolds resemling single bacterial genomes (+@fig:fig3_Azolla-genus-metagenome-order).
The approach was however unnessicarily costly, for assembly quality did not increase due to reduced complexity of the assembly graph (+@fig:fig3_filter-length-distributions; +@tbl:tbl3_1).
The k-mer spaces in which these genomes are assembled are presumably so distinct that they do not overlap in a De-Bruijn-graph even before filtering and hence would never create ambiguities which could not be solved by the assembler.
By this argument, filtering of the bulk DNA extraction may even be obsolete; @Delmont2016 showed that bacterial genomes could be extracted from a bulk assembly of host and symbionts.
However, especially for larger scale mining of bacterial symbionts, removing host DNA with a single hostfiltering step may be the preferable and faster approach than (re)assembling the genome of the host in the process, especially for bigger host genomes.
At the very least, hostfiltering allows to assemble a metagenome with less resources `RAM reduction`.
The doublefiltered approach is especially intensive, and may easily be ommitted in future workflows.
This step is only required when sequencing libraries including host DNA are too big for hybrid assembly.
Alternatively, scaffold taxonomy of the hostfiltered assembly could be classified with CAT, and then scaffolds that are not of interest may be removed before the binning process.
This would greatly reduce binning input, hence simplifying the process of either manual or automated binning.
The beneficial effect would be equal as the double filtering step.

In the methods presented here, we diliberately don't provide a single tool to the community.
We do aim to make the method as open and reproducible as possible by documenting the workflow on Github and discussing the benefits and costs of several aspects of our approach in this manuscript.

### Manual curation allowed for high quality bins
Binning of non-metagenomic assemblies is possible and may be supplemented with extragenous binning signals and scaffold taxonomy.
Here, we assemble DNA extracted from bulk plant samples and retrieve MAGs of bacteria associated with those plants.
Ideally, differential sampling of various fractions or biological replicates allows to distinguish scaffolds of the various genomes from each other.
In the data used here, this differential sampling is often not present.
Instead, we build on the assumption that some microbes may be shared amongst different _Azolla_ species and use sequencing data of related species to differentiate different microbial genomes from each other.
Such extragenous binning signals may provide false motivation to exclude a certain part of a microbe's genome that is present in the assembly, but not in the data used as binning signal.
Therefore, we consider manual curation a requirement when using such binning signals, while appropriately valueing and crossreferencing the different binningsignals available.
In binning the _Azolla_ species studied here, binning signals of related samples were occasionally informative in the manual binning process (Supp. mexicana) but in some samples not (Supp fig _A. microphylla_).
Only when genomes in a metagenome as expected to be shared between two different host DNA extractions, then this method can be informative.
Feasibility of this approach depends on the community complexity, relatedness of the samples available, and similarity of microbes in those samples.

An additional binning signal was scaffold taxonomy determined by CAT.
CAT classifications often overlapped well with bins demarcated clearly by other binning signals (+@fig:fig3_Azfil-wild-binningsignals; +@fig:fig3_Azmic-binningsignals).
This result further confirms the robustness of CAT scaffold classifications and it's use-case for manual binning when depth and k-mer profiles are lacking.
Single copy marker gene validation with both CheckM and Anvi'o supported the quality of bins for which CAT classification was instrumental in their reconstruction.
Our view on t hese methods is that a researcher should bin primarily on the sample-native sequencing libraries and k-mer profiles and then use extragenous binning signals and scaffold taxonomoy only in an advising manner.
Additionally, when using extragenous binning signals, these potential MAGs should be cross-referenced with k-mer profile only clustering of scaffolds.
`possibly more info based on different binning performances benchmarking`

While the filtering did not improve assembly quality, it does ease the process of manual binning in Anvi'o.
The Anvi'o interactive interface was essential in manual binning but feasibility of this process reduced substantially with very big assemblies (numbers).
In @Delmont2016 the total assembly including host and symbionts was approximately 252 Mbase; `compare to assembly sizes here`.
`Open question still: cleanness of the Assembly allows for better binning`

### Azolla genus-wide metagenome and vertical transmission of the whole metagenome
`root nodule bacteria diversity; disporiensis diversity`

To our knowledge, this is the first scholarly publication about the metagenome of a whole genus.
Inspired by the holobiont concept [@Zilber-Rosenberg2008] and the mechanism for vertical transfer in _Azolla_ ferns, it makes sense to study a symbiosis like _Azolla_ from the genus perspective, rather than a single species.
To demonstrate vertical transmission of microbes besides _N. azollae_, it would be more fitting to sequence multiple generations of plants and the reproductive organs of those generations.
However, we argue that rather indirectly, we have sequenced multiple generations of the same population of plants.
_A. filiculoides_ sequenced by @Li2018 was taken from a Ditch near the Galgenwaard footbal station in Utrecht, the Netherlands in 2012 (@Brouwer2014).
Several years later, in 2015 we went to the same ditch to sequence _A. filiculoides_ for Chapter \ref{foul play} [@Dijkhuizen2018].
The _Azolla_ population in this ditch doesn't survive the winter, and hence we reason the microbes found in the data sequenced by Chapter \ref{foul play} [@Dijkhuizen2018] has survived 3 generations, either through direct vertical transfer via the ferns megaspores, or via reinnoculation from the surrounding environment.
Secondly, the presence of the same species of microbes in the thoroughly sterilised _A. filiculoides_ minus-cyano provides further indication that these microbes are endophytic and in that way survived the sterilisation process.

_Azolla_ ferns systematically harbour microbes of 6 taxonomical orders.
The Nostocales order encompasses only the main symbiont _N. azollae_ and was highly abundant in all species, contradicting theories that other cyanobacterial strains may inhibit _Azolla_ ferns at lower abundances [@Papaefthimiou2008].
The two most prominent orders Burkholderiales and Rhizobiales were already identified in Chapter \ref{foul play} [@Dijkhuizen2018] but their genomes acros the entire _Azolla_ genus were not published before, nor was it clear that multiple Rhizobiales and Burkholderiales genomes are systematically associated with single species of the _Azolla_ genus.
The remaining three orders, Caulobacterales, Nevskiales and Sphingomonadales, were hinted at before, but not substantiated by systematic evidence before, nor where genome sequences available.
`do any of the published microbes fit in these orders?`
The new availibility of all MAG sequences allows to study the bacteria of the _Azolla_ genus through the perspective of comparative genomics.
Classes alfa/beta/gamma proteobacteria, Actinobacteria, Bacillales, have all been seen as endophytes to plants before @Frank2018.
The diversity of _Azolla_ associated microbes is not exhausted in this study.
All assemblies except for _A. filiculoides_ minus_cyano contained many scaffolds near the lower abundance limit of assembly (+@fig:fig3_Azolla-genus-metagenome-order) and in concordance binning yielded many bins with only fractions of genomes (+@fig:fig3_Azfil-wild-binningsignals; +@tbl:tbl3_2).
Despite that, it is perhaps more interesting to wonder which microbes are endophytes of the _Azolla_ genus and which microbes share a common ancestor and common introduction in the _Azolla_ genus.
The nature of the data presented here does warrant caution on two important fronts.
First, except for the _A. filiculoides_ 'wild' sample, no judgement can be made wether the MAGs presented here belong to endophytic or epithitic bacteria.
Second, ferns acquired from the IRRI collection were maintained for long periods in close vacinity to each other and cross contamination is a realistic risk
The latter consideration is somewhat mitigated by the presence of these order in samples acquired both from Utrecht, the Netherlands, and the IRRI collection.

Systematic presence of specific groups of bacteria suggests ferns of the genus _Azolla_ may acquire some fitness benefit from their microbiome and begs the question how these bacteria are systematically transfered.
The plants may actively retain these bacteria in their ecosystem, and transfer them to subsequent generations via their megaspores as is the case for _N. azollae_.
Bacteria were seen in mulitple _Azolla_ species their reproductive structures adjacent to _N. azollae_ resting stages [@Carrapico1991] `and also Sandra and Zheng?`.
@Forni1992 theorised that _Azolla_ associated bacteria may be responsible for the mucus in which both _N. azollae_ and additional microbes are harboured.
A similar mucus is found at the apical meristem colony in Chapter \ref{it takes two} [@Dijkhuizen2021].
Mining the genomes published here may indicate if the genes required for producing this mucus are present.

It is commonly believed that _N. azollae_ bacteria enter the _Azolla_ megasporocarps via small channels `bunch of refs`.
We theorise however, that _N. azollae_ and additional microbes may be retained in seed colonies near the shoot apical meristem (SAM) of _Azolla_ ferns as we showed Chapter \ref{it takes two} [@Dijkhuizen2021].
Leaf and sporocarp primordia encapsulate part of this seed colony during early development which functions as innoculum for the forming organ. [@Campbell1893; @Nierzwicki-Bauer1989].
Microspores loose the cyanobacterial symbionts, and megaspores retain them in the form of akinete resting stages`Anna's results, or published in 19-longago? `.
Whilst highly likely in some cases, we do not provide definitive proof of endophytism of any bacterium whose genome we have assembled, nor of its presence in the SAM seed colony, nor of vertical transfer via megasporocarps.
Also, this hypothesis on the mechanism of microbiome transfer over the plant organs and over plant generations does not explain motile cyanobacterial filaments often observed in a channel of the megaspores' indusium caps in [@Ran2010;] `any more papers?`
Sequencing the SAM and reproductive stages could provide furhter information on the mechanism of microbiome vertical transfer in _Azolla_.
Alternatively, FISH may be used to pinpoint the exact location of the bacteria of which the genomes were assembled here, either in the SAM, the leaves or the sporocarps.

Systematic presence, and possible systematic vertial transmission, are no requirement to consider a microbe as a symbiont.
Alternatively, microbes may associate with _Azolla_ but live in environment as well as is the case with Rhizobiales-legume symbioses.
This would allow for a less direct inheritance of microbial symbionts as is the case in clams `find that paper`.


```
I have said nothing of membrane vesicles from both cyano's and bact observed by at least @Zheng2009

Is this a small group of bacteria maintained by the plant, or conversely,
How do these bacteria co-exist in this special niche with generational bottleneck.
Hypothesis: all persistent partners have some specialised function in a bigger cooperation, a function which they are selected upon.
   question: are persistent microbes prone to pseudogenation
   question: are persistent microbes evolving slower than a representative subset of their genus/family.
   question: cyano's are mobile, are these bacteria mobile in order to board "noahs ark" to the next genration.
Alternate hypothesis: Bacteria are present in low abundances until their specific "usecase" comes into effect.
In other words: we see a snapshot of a community, but that does not imply equilibrium.
Alternative hypothesis: these bacteria "battle out" other bacteria and hence function as a leaf pocket immune system
Another idea: the generational bottleneck undermines a major requirement for high diversity ecosystems: spatial diversification and hetrogeneïty.
More important: the generational bottleneck should imply muller's ratchet unless some genetic exchange is happening.
Perhaps a semi open system which allows for more microbes to enter and replace damaged ones.
That's why these microbes don't show signs of degradation...
How then does _N. azollae_ escape this... Is multiple genome coppies sufficient?

The leaf pocket ecosystem:
_N. azollae_ is an autotroph in a highly closed leaf pocket.
Presumably, all elements that can't be fixed photosynthetically or with energy from photosynthesis, are delivered by the plant.
What about the excretory and dead _N. azollae_ material however
It's unreasonable to expect _N. azollae_ has the genetic capacity to completely recycle it's own decaying material.
Perhaps the plant can remove this organic waste itself, just as it can remove fixed N and supply all nutrients for _N. azollae_
Alternatively, the bacteria inside the leaf pocket may form some closed nutrient cycle.
The "additional" microbiome feeds of _N. azollae_ waste, decomposing it to inorganic form to be recycled again by _N. azollae_ (or the plant).
One wonders if the low abundance of "additional microbes" is sufficient to fulfil that role in the cycle however...
Again, it may be "waiting" there for a later life stage of the leaf pocket, we sampled material that's "too fresh".
Also, there is presumablyy no requirement to close the nutrient cycle since the plant has to be able to support _N. azollae_ with nutrients.
Perhaps
With ideas from [@rillig2019]

Again a completely different hypothesis: The "additional microbiome" adds some function that was lost/damaged in _N. azollae_, perhaps connecting to the reason _N. azollae_ can't be cultered.

ITSNTS versus "simple altruism"

```

```
Microbiology and ecology need, in the end, a reductionist approach to piece appart the nuts and bolts co-existance.
We need at least a way to manipulate the microbial community of a plant organ, or simulate this in microcosms to come to the level of hypothesis testing.
[@rillig2019]

Given systematic occurence, are we looking at a ITSNTS picture or a holobiont picture.
Here, I'm not particularly looking at functions so I can't really see ITSNTS, but does the holobiont break down if I go to deeper taxonomy, and is that even meaningful.
[@FordDoolittle2018]
The main ITSNTS argument against the holobiont is the too-many-parents-means-no-parents-at-all-argument, with which I agree.
However, this argument assumes complete lossy/random inheritance.
The holobiont argument stands if inheritance is systematic, if the genetic material and phenotype of the child generation represents that of their parent population.
Counting parents and assuming randomness ignores that the persistance of genetic material can move in a range of strictness.
On the one hand (near) 100% strict, such as _N. azollae_


If we conclude there is strict holobiont like inheritance of a slection of microbes,
with that bottleneck maternal mechanism,
then why is this beneficial to recruiting symbionts from the environment as so many hosts do.
Is this a matter of not having the tools to do so (as a fern) Seems not, for facultative cyanobacterial and moss symbioses exist as well. Hence at leaset the potential for facultative symbiosis was present in the common ancestor of ferns and mosses.


1. assuming variation in a population of microbes across members of a host species
2. assume systematic inheritance of organisms and genes via megaspores (1 parent maternal transmission)
3. if these have differential bennefit, there's classic darwinian evolution

This scenario is very different from rhizosphere microbiota, the many-partent-argument.

ITSNTS and redundancy in the mags we find. Redundancy in singers implies redunancy in the parts of the song they sing.


microbes recycling dead azolla and making nutrients available again.

Pose that the Azolla-microbe system is just a (collection) of niches (songs) to be fulfilled (sung) by microbes/genes.
Now asume that these functions are reasonably generic and could be reqruited from the environment (as Moss-cyano, legume-rhizobia).
Corollary then, these functions were reqruited from the environment in some Ancestral Azolla-microbe state before they were transfered vertically by the host.
What makes it beneficial to fix these processes/genes/genomes in maternal transmission?
How does the drastic reduction in gene pool and risk of genetic drift pay back?
Especially given the current default is still reqruitment of microbes from the environment, again mosses, legumes, all rhizome associated bacteria.
To clarify our thinking, let's consider other systems where this is the case: lichen, some insects, more?.
Lichen are specialised to grow in harsh conditions, nutrient poor, the odds of encountering the required functions in the genomes of bacteria already present may be so low that the lichens benefit from the safety of carying them in spores.
This assumtion is not the case for Azolla, Azolla is part of a family (or even order) of (semi) aquatic ferns.
Nitrogen fixing cyanobacteria should be available in the potential living environment even of what I envision as the most recent common ancestor of Azolla.


If the host plant provides niches to microbes, thereby defining the processes/songs, and even just a part of microbes is systematic part of that song (permanent singers).
Then does it even matter if part of the singers is swapped in and out?
Yes if we're talking about evolution, for selection can only occur if the traits and associated fittness of one generation are transfered to the next generation.
This may be partially untrue if the song is defined already in advance by the permanent particants/singers (Host and Nostoc).
Evolution of these heritable parts of the hologenome may define in advance the niche to be filled, even if the gene to fill that niche is one another genome.
How then, does this differ from traditional co-evolution...?


Selection for reduced genome size lower in extracellular symbionts than intracellular ones?


```
### Bacteria known to associate with plants (a fast evolving, modular subset of a hologenome?)
Microbial genomes may encode and convey traits to a host when in symbiosis.
The most obvious example is _Azolla_ its independence of nitrogen in the surrounding water or sediment, a trait conveyed by _N. azollae_.
Bacterial genomes are substantially more fluid in their structure and content than their eukaryotic hosts and bacterial species may leave or enter the symbiosis.
Consequently, the functions these genomes convey are more easily lost or acquired.
This modular and variant subset of the hologenome can provide a bigger pool of genes and functions for the holobiont to be selected on.
Arguably, current ecological and evolutionary terminology may be sufficient to describe and understand a host and symbionts as individual units [@Douglas2016].
We argue, a holobiont must not be a new concept for a singular species with extra elements per say.
`re-read the whole holobiont polemiek thing to make sure I cite stuff appropriately`
Rather we subscribe to the view of a holobiont as a modular agglomeration of individuals who may move in and out of symbiosis with each other.
The assocation of those indivuduals may be of differing consistency.
For example, reliable vertical transfer has been proven as the exclusive method of transfer, as is the case for _N. azollae_, we deem using holobiont as a concept to describe a single unit is justified.
Just as it is justified to include plastig genomes in the concept of a species' genome.
In some species, vertical transfer may be established but not as fixed as is the case for _Azolla_ `clam paper`.
Alternatively, symbionts may need to reinnoculate their host annew every generation as is the case for Rhizobiales-legume symbioses.
No particular mode of transmission of genetic material is more or less relevant to be included in a hologenome, instead the holobiont term must be a usefull concept in research applied appropriately.

In this manuscript, we chose to characterise the components of the _Azolla_ holobiont from the perspective of the entire genus rather than a single species.
This broader perspective ideally will allow us to identify parts that are persistently present in the genus or parts thereoff.
With parts, we deliberately don't mean genomes, or even single genomes.
Rather, we like to think of pathways which may be encoded in any set of genomes that may be relevant to the fitness of the holobiont.
The MAGs assembled and published here, hopefully allow the _Azolla_ research community to study the bacteria of the genus from that broader perspective and add to it as more _Azolla_ ferns are published.
Study approaches that benefit from the whole genus persepective are for example phylogenetics and phylogenomics.
If any bacterial species was introduced once and retained by the host, the genomes of this one species would have persisted through host speciations, and hence a phylogenetic tree of the symbiont will likely resemble that of the host species.
By the same reasoning, these bacterial genomes associated with _Azolla_ hosts, will cluster together in a phylogentic tree of a broader selection of related bacteria.
Persistent symbionts may also show signs of genome degradation as the main symbiont _N. azollae_ does.
Awknoledging again that bacterial genomes are more flexible in their content and structure, we may employ the near complete MAGs published here to study their genetic content rather than the presence or absence of a genome as a whole.
For example, we may find clusters of genes involved in symbiosis or of particular interest to _Azolla_-Rhizobiales symbiosis by pangenomics of a selection of Rhizobiales species, including those associated with _Azolla_, those in symbioses with legumes, and non-symbiotic species.
Although our sample size is small, we may attempt to mine the pathways found in _Azolla_ associated bacterial genomes for genes under positive selection.
We might wonder how microbes evade the plant immune system, perhaps studying type 3 and 4 secretion systems encoded in their genomes [ @DeMeyer2019; @Frank2018].

Possible study directions of the _Azolla_ genus metagenome are numerous and the previous list of examples is not exhaustive.
We gladly share all genomes of bacteria associated with the _Azolla_ genus with the research community to study this remarkable symbiosis.

```
In microbial ecology, natural low diversity, low complexity populations are rare.
This is such an example, perhaps many plant-microbe associations are.
The plant genome does add complexity, but other than that ...
[@Rillig2019]
```
\newpage
## Supplemental data
\tiny
| taxonomical order | MAG name | MAG length (Mbase) | Anvi\'o completeness | Anvi\'o redundancy | CheckM completeness | CheckM redundancy |
| --------- | --------- | --   | --  | --   | --  | --   |
| _Azolla rubra_                     | Asticcacaulis             | 4.29       | 100          | 0            | 100           | 1             |
| _Azolla rubra_                     | Betaproteobacteria        | 3.27       | 99           | 0            | 100           | 1             |
| _Azolla rubra_                     | Methylovorus              | 3          | 100          | 3            | 100           | 0             |
| _Azolla rubra_                     | Rhizobiales               | 5.28       | 96           | 0            | 99            | 0             |
| _Azolla rubra_                     | Rhizobiales2              | 5.09       | 80           | 1            | 100           | 1             |
| _Azolla rubra_                     | Rhizobiales3              | 4.56       | 100          | 1            | 99            | 0             |
| _Azolla rubra_                     | Rhizobiales4              | 4.67       | 94           | 0            | 97            | 1             |
| _Azolla rubra_                     | Rhizobiales5              | 2.45       | 45           | 1            | 29            | 0             |
| _Azolla rubra_                     | Trichormus                | 4.7        | 97           | 3            | 98            | 0             |
| _Azolla rubra_                     | alphaproteobacteria       | 6.3        | 100          | 6            | 100           | 0             |
| _Azolla rubra_                     | proteobacteria            | 4.75       | 70           | 8            | 74            | 3             |
| _Azolla filiculoides_ 'lab'        | Bacteria                  | 5.05       | 51           | 4            | 44            | 13            |
| _Azolla filiculoides_ 'lab'        | Bacteriodetes1            | 3.41       | 63           | 4            | 83            | 3             |
| _Azolla filiculoides_ 'lab'        | Bacteriodetes2            | 0.95       | 85           | 3            | 82            | 0             |
| _Azolla filiculoides_ 'lab'        | Bacteriodetes3            | 2.29       | 54           | 3            | 42            | 1             |
| _Azolla filiculoides_ 'lab'        | Bradyrhizobiaceae         | 8.01       | 65           | 11           | 73            | 19            |
| _Azolla filiculoides_ 'lab'        | Bradyrhizobiaceae2        | 4.95       | 55           | 1            | 63            | 4             |
| _Azolla filiculoides_ 'lab'        | Bradyrhizobiaceae3        | 5.75       | 73           | 1            | 64            | 5             |
| _Azolla filiculoides_ 'lab'        | Bradyrhizobium            | 8.8        | 96           | 10           | 94            | 14            |
| _Azolla filiculoides_ 'lab'        | Burkholderiales           | 5.6        | 87           | 31           | 87            | 13            |
| _Azolla filiculoides_ 'lab'        | Hyphomicrobium            | 3.84       | 100          | 0            | 97            | 0             |
| _Azolla filiculoides_ 'lab'        | Ralstonia\_1              | 5.18       | 66           | 6            | 80            | 4             |
| _Azolla filiculoides_ 'lab'        | Rhizobiaceae\_endophytic  | 5.18       | 100          | 0            | 99            | 0             |
| _Azolla filiculoides_ 'lab'        | Rhizobiales               | 4.39       | 86           | 0            | 97            | 1             |
| _Azolla filiculoides_ 'lab'        | Sinobacteraceae           | 3.87       | 97           | 3            | 97            | 1             |
| _Azolla filiculoides_ 'lab'        | Sphingobacteriales        | 7.75       | 94           | 0            | 99            | 2             |
| _Azolla filiculoides_ 'lab'        | Sphingomonas              | 4.3        | 94           | 0            | 95            | 1             |
| _Azolla filiculoides_ 'lab'        | Trichormus\_azollae       | 4.72       | 96           | 3            | 98            | 0             |
| _Azolla filiculoides_ 'minus-cyano'| Paenibacillus\_lab        | 8.07       | 100          | 6            | 99            | 1             |
| _Azolla filiculoides_ 'minus-cyano'| Ralstonia\_maybewild      | 5.54       | 100          | 3            | 100           | 1             |
| _Azolla filiculoides_ 'minus-cyano'| Rhizobiales\_endophytic   | 5.21       | 100          | 0            | 100           | 0             |
| _Azolla filiculoides_ 'minus-cyano'| Rhizobiales\_lab          | 6.3        | 100          | 0            | 98            | 1             |
| _Azolla filiculoides_ 'minus-cyano'| Rhizobiales\_wild         | 5.59       | 100          | 0            | 100           | 0             |
| _Azolla mexicana_                  | Asticcacaulis             | 5.19       | 100          | 0            | 99            | 1             |
| _Azolla mexicana_                  | Bradyrhizobiaceae         | 6.65       | 54           | 4            | 70            | 2             |
| _Azolla mexicana_                  | Burkholderiales1          | 3.21       | 66           | 14           | 70            | 11            |
| _Azolla mexicana_                  | Burkholderiales2          | 7.9        | 161          | 39           | 108           | 18            |
| _Azolla mexicana_                  | Herbaspirillum            | 5.17       | 100          | 1            | 100           | 0             |
| _Azolla mexicana_                  | Methylophilaceae          | 2.62       | 56           | 3            | 94            | 1             |
| _Azolla mexicana_                  | Methylophilaceae2         | 3.03       | 94           | 1            | 97            | 0             |
| _Azolla mexicana_                  | Nevskia\_soli             | 5.44       | 97           | 6            | 93            | 5             |
| _Azolla mexicana_                  | Novosphingobium           | 4.07       | 97           | 0            | 97            | 0             |
| _Azolla mexicana_                  | Rhizobiales               | 4.59       | 61           | 6            | 95            | 1             |
| _Azolla mexicana_                  | Rhizobiales2\_1           | 4.29       | 94           | 0            | 95            | 1             |
| _Azolla mexicana_                  | Rhizobiales3              | 5.45       | 61           | 0            | 98            | 0             |
| _Azolla mexicana_                  | Rhizobiales4              | 4.38       | 100          | 4            | 100           | 2             |
| _Azolla mexicana_                  | Sphingomonadaceae         | 4.3        | 100          | 0            | 99            | 0             |
| _Azolla mexicana_                  | Sphingomonadaceae2        | 4.59       | 94           | 0            | 90            | 1             |
| _Azolla mexicana_                  | Trichormus                | 4.87       | 97           | 4            | 99            | 0             |
| _Azolla mexicana_                  | rest\_1                   | 0.98       | 73           | 24           | 59            | 17            |
| _Azolla mexicana_                  | rest\_2                   | 2.05       | 45           | 0            | 9             | 0             |
| _Azolla mexicana_                  | rest\_3                   | 4.37       | 61           | 1            | 28            | 2             |
| _Azolla mexicana_                  | rest\_4                   | 3.65       | 42           | 17           | 30            | 8             |
| _Azolla mexicana_                  | rest\_5                   | 6.68       | 0            | 0            | 39            | 9             |
| _Azolla microphylla_               | Acidobacteria             | 4.29       | 82           | 4            | 76            | 0             |
| _Azolla microphylla_               | Actinobacteria            | 3.34       | 92           | 27           | 77            | 4             |
| _Azolla microphylla_               | Alphaproteobacteria       | 4.8        | 99           | 4            | 80            | 4             |
| _Azolla microphylla_               | Alphaproteobacteria2      | 5.13       | 93           | 4            | 91            | 1             |
| _Azolla microphylla_               | Asticcacaulis             | 3.48       | 70           | 1            | 82            | 3             |
| _Azolla microphylla_               | Asticcacaulis\_taihuensis | 4.14       | 99           | 0            | 98            | 0             |
| _Azolla microphylla_               | Bacteriodetes             | 6.37       | 99           | 0            | 97            | 0             |
| _Azolla microphylla_               | Bradyrhizobiaceae         | 7.29       | 100          | 0            | 100           | 0             |
| _Azolla microphylla_               | Herbaspirillum            | 4.81       | 96           | 6            | 86            | 2             |
| _Azolla microphylla_               | Hyphomicrobium            | 3.67       | 76           | 10           | 72            | 2             |
| _Azolla microphylla_               | Nevskia                   | 6.01       | 100          | 4            | 98            | 5             |
| _Azolla microphylla_               | Novosphingobium           | 4.51       | 100          | 4            | 99            | 1             |
| _Azolla microphylla_               | Rhizobiales2              | 5.01       | 94           | 4            | 97            | 1             |
| _Azolla microphylla_               | Rhizobiales3              | 2.34       | 28           | 3            | 16            | 1             |
| _Azolla microphylla_               | Rhizobiales\_1            | 7.15       | 93           | 4            | 95            | 1             |
| _Azolla microphylla_               | Trichormus                | 4.85       | 97           | 4            | 99            | 0             |
| _Azolla microphylla_               | rest                      | 0.53       | 15           | 4            | 11            | 0             |
| _Azolla microphylla_               | rest2                     | 0.21       | 0            | 0            | 6             | 0             |
| _Azolla microphylla_               | rest3                     | 1.62       | 0            | 0            | 20            | 0             |
| _Azolla nilotica_                  | Bacteria                  | 4.32       | 97           | 0            | 100           | 1             |
| _Azolla nilotica_                  | Bacteria2                 | 4.33       | 86           | 10           | 68            | 1             |
| _Azolla nilotica_                  | Bacteriodetes             | 3.51       | 99           | 4            | 97            | 1             |
| _Azolla nilotica_                  | Bacteroidetes2            | 3.64       | 96           | 1            | 99            | 0             |
| _Azolla nilotica_                  | Bradyrhizobiaceae         | 6.66       | 63           | 6            | 84            | 9             |
| _Azolla nilotica_                  | Bradyrhizobiaceae2        | 4.63       | 61           | 11           | 67            | 12            |
| _Azolla nilotica_                  | Burkholderiaceae          | 3.35       | 39           | 3            | 43            | 3             |
| _Azolla nilotica_                  | Comamonadaceae            | 3.62       | 100          | 1            | 98            | 0             |
| _Azolla nilotica_                  | Mesorhizobium             | 6.39       | 94           | 1            | 98            | 1             |
| _Azolla nilotica_                  | Rhizobiales               | 4.43       | 62           | 1            | 83            | 0             |
| _Azolla nilotica_                  | Rhizobiales2              | 4.77       | 56           | 3            | 25            | 1             |
| _Azolla nilotica_                  | Sphingomonas              | 4.53       | 97           | 0            | 99            | 3             |
| _Azolla nilotica_                  | Trichormus                | 4.76       | 97           | 4            | 98            | 0             |
| _Azolla nilotica_                  | bacteriodetes3            | 3.61       | 89           | 7            | 78            | 0             |
| _Azolla nilotica_                  | betaproteobactera         | 9.82       | 58           | 31           | 74            | 48            |
| _Azolla nilotica_                  | rest1                     | 0.52       | 46           | 18           | 18            | 7             |
| _Azolla nilotica_                  | rest2                     | 3.95       | 34           | 6            | 32            | 0             |
| _Azolla nilotica_                  | rest\_3                   | 0.88       | 32           | 17           | 4             | 0             |
| _Azolla nilotica_                  | rest\_4                   | 2.02       | 0            | 0            | 14            | 0             |
| _Azolla nilotica_                  | rest\_5                   | 0.24       | 0            | 0            | 3             | 0             |
| _Azolla caroliniana_ 1             | Alphaproteobacteria       | 2.48       | 34           | 3            | 33            | 0             |
| _Azolla caroliniana_ 1             | Asticacaulis              | 4.48       | 69           | 0            | 68            | 0             |
| _Azolla caroliniana_ 1             | Bacteria                  | 2.49       | 59           | 4            | 49            | 1             |
| _Azolla caroliniana_ 1             | Bacteria2                 | 4.97       | 100          | 0            | 95            | 1             |
| _Azolla caroliniana_ 1             | Bradyrhizobiaceae         | 3.43       | 70           | 1            | 97            | 0             |
| _Azolla caroliniana_ 1             | Bradyrhizobium            | 8.31       | 100          | 1            | 100           | 1             |
| _Azolla caroliniana_ 1             | Burkholderiales           | 6.09       | 65           | 0            | 98            | 1             |
| _Azolla caroliniana_ 1             | Caulobacter               | 4.15       | 100          | 0            | 100           | 0             |
| _Azolla caroliniana_ 1             | Chitinophaga              | 8.03       | 100          | 0            | 100           | 1             |
| _Azolla caroliniana_ 1             | Nevskia\_ramosa           | 3.14       | 0            | 0            | 34            | 0             |
| _Azolla caroliniana_ 1             | Nevskia\_soli             | 6.12       | 94           | 4            | 97            | 5             |
| _Azolla caroliniana_ 1             | Rhizobiales               | 4.9        | 73           | 7            | 59            | 3             |
| _Azolla caroliniana_ 1             | Rhizobiales2              | 5.07       | 100          | 3            | 100           | 1             |
| _Azolla caroliniana_ 1             | Sphingomonadaceae         | 3.01       | 46           | 3            | 44            | 2             |
| _Azolla caroliniana_ 1             | Trichormus                | 4.7        | 97           | 4            | 98            | 0             |
| _Azolla caroliniana_ 2             | Alphaproteobacteria       | 6.74       | 56           | 7            | 38            | 3             |
| _Azolla caroliniana_ 2             | Asticcacaulis             | 3.7        | 99           | 0            | 98            | 0             |
| _Azolla caroliniana_ 2             | Asticcacaulis2            | 4.9        | 89           | 4            | 95            | 3             |
| _Azolla caroliniana_ 2             | Asticcacaulis\_taihuensis | 3.84       | 89           | 0            | 100           | 0             |
| _Azolla caroliniana_ 2             | Bradyrhizobium            | 7.53       | 100          | 0            | 100           | 0             |
| _Azolla caroliniana_ 2             | Caulobacterales           | 4.66       | 89           | 0            | 100           | 2             |
| _Azolla caroliniana_ 2             | Methylovorus              | 2.85       | 99           | 1            | 100           | 0             |
| _Azolla caroliniana_ 2             | Nevskia\_soli             | 5.79       | 92           | 6            | 94            | 5             |
| _Azolla caroliniana_ 2             | Novosphingobium           | 4.51       | 97           | 0            | 98            | 2             |
| _Azolla caroliniana_ 2             | Rhizobiales               | 5.42       | 100          | 7            | 100           | 9             |
| _Azolla caroliniana_ 2             | Rhizobiales2              | 5.57       | 94           | 8            | 92            | 2             |
| _Azolla caroliniana_ 2             | Rhizobiales3              | 4.03       | 100          | 6            | 98            | 1             |
| _Azolla caroliniana_ 2             | Trichormus                | 4.72       | 97           | 4            | 98            | 0             |

Table: MAG statistics for all samples except those _A. filiculoides_ 'wild' which are shown in +@tbl:tbl3_2 {#tbl:tbl3_all_MAGs}

\normalsize
Anvio figs...
