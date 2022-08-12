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
\linenumbers
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

<!---
rewrite highlights
check all figure legends
--->

## Abstract
Bacteria-host symbioses are present throughout the plant kingdom, and bacteria can contribute all kinds of functions to their hosts.
The plant genus _Azolla_ is known to host multiple endophytic bacteria, which it transfers systematically to successive generations.
Here we set out to acquire bacterial genomes of _Azolla_ associated bacteria by re-using non-metagenomic data already available in public repositories.
Sequencing data of six _Azolla_ species was filtered and assembled with a fully reproducible workflow made in the conda and snakemake frameworks.
Intensive filtering of host DNA data reduced computational requirements but did not increase assembly quality of bacteria.
Binning signals from foreign samples and taxonomy-based signals increased binning quality but required careful manual curation during the binning process.
This method yielded between 11 and 21 bacterial genomes per _Azolla_ species.
The majority belongs to only six taxonomical orders (Burkholderiales, Caulobacteriales, Nevskiales, Nostocales, Rhizobiales and Sphingomonadales). They occur in most species of the _Azolla_ genus.
Rhizobiales and Burkholderiales were transferred over generations in _A. filiculoides_.
Taxonomic consistency of bacterial genomes associated with the _Azolla_ genus suggests these bacteria may be introduced in some common ancestor of _Azolla_ species and that they may be selected for in the evolution of the _Azolla_ holobiont.

## Introduction
Many bacteria associate with multicellular hosts in symbioses and may convey specific metabolic properties or traits to their hosts.
Such associations may be temporary or occasional; these bacteria are often recruited from the environment of a host triggered by certain conditions.
Alternatively, symbionts may be practically ubiquitous among a host species.
They may be housed inside host organs, making them endophytes of their host.
These ubiquitously present symbionts may even be vertically transferred over host generations.
The new host generation thereby inherits the traits associated with these symbionts.
Such systematic presence in a host species will substantially influence selection pressure on the endophyte genome compared to free-living relatives.
In such a case, a conglomeration of evolving organisms sharing both genomes and selection pressure can occasionally be seen as a holobiont: a single evolutionary unit comprising several organisms [@Zilber-Rosenberg2008].
However, the exact scope and applicability of the term remain subject to debate [@Douglas2016].
Nonetheless, studying systematically inherited microbes provides opportunities for studying the adaptation of bacteria to the symbiotic lifestyle and the traits encoded in a plant's second genome.

Symbiotic endophytes are widespread over the plant kingdom, highly polyphyletic and can attribute various functions to their hosts [@Frank2018; @Hassani2018].
The two most studied endophytes of plants are mycorrhiza and nitrogen-fixing Rhizobiaceae.
These two symbioses share a common gene set in the host plants, termed the Common Symbiosis Pathway (CSP), even though components of the pathway vary amongst host-bacteria interactions (@Genre2016).
However, several other plant endophytic symbioses are studied less intensively isolated from various plant organs [@Pinto-Carbo2018; @Frank2018].
One such example, and the subject of this study, is the fern genus _Azolla_.
_Azolla_ ferns harbour symbiotic cyanobacteria, which they systematically transfer to subsequent generations.
@Li2018 showed that the _Azolla filiculoides_ genome does not encode the CSP, indicating the molecular underpinnings of symbioses, in general, may be more diverse.

Work on plant-endophyte symbioses often focuses on one symbiotic partner where there could be multiple.
Researchers may isolate, culture or otherwise enrich symbiotic endophytes, which are often lowly abundant compared to plant tissue [@Ran2010; @DeMeyer2019].
Such enrichments substantially improve the efficiency of sequencing the endophytes' DNA rather than a bulk DNA extraction that includes the host.
Simultaneously, such processes often increase the selectiveness of a methodology, leaving out any additional organisms to a host-endophyte symbiosis.
Full metagenomic sequencing would be a less biased assessment to study all organisms in a symbiosis, at least when one expects more endophytic microbes.

Full metagenomics sequencing is inefficient if symbionts are lowly abundant in plant tissue; hence, the method becomes highly cost-inefficient.
Alternatively, symbiont genomes may be retrieved from sequencing data already available in data repositories, thereby capitalising on opportunities of the FAIR data age and the diversity thereof.
We demonstrated this before in chapter \ref{foul play}, where we serendipitously found bacterial genomes as a by-product of the _A. filiculoides_ genome assembly.
@Delmont2016 extracted three bacterial genomes from the tardigrade genome similarly, using advanced visualisation and multiple sequencing libraries to puzzle apart the scaffolds of multiple organisms in a single assembly.
Additionally, a study may benefit from using public data for the scope of the inquiry can be easily widened to include related species and their metagenomes.
Naturally, the feasibility of such an undertaking depends on data availability in repositories and the complexity of the bacterial community associated with any host.
Given that sufficient data is available, the challenge remains to use metagenomics techniques to retrieve these genomes from data generated in experimental designs not intended for metagenomics.
Such data could be sequencing libraries of bulk DNA extractions, combining host DNA and DNA of associated microbes.
When a host has many microbe associations, this increases demands on the experimental design and variety of input data, especially when these microbes are similar.
One such multi-partite association is the subject studied here: the aquatic ferns of the _Azolla_ genus.

_Azolla_ ferns are particularly interesting to study from a metagenomic perspective.
They host substantial quantities of di-nitrogen fixing symbiotic _Nostoc azollae_ protected inside specialised leaf cavities [@Campbell1893; @Nierzwicki-Bauer1989].
These cavities contain a mucus-like substance [@Forni1998], presumably rich in ammonia [@Newton1976], containing the primary symbiont.
The appropriate genus of the main _Azolla_ symbiont has been prone to debate; it is also known as _Anabaena azollae_ and _Trichormus azollae_.
Here, we name the symbiont _N. azollae_ for consistency with our earlier work.
High sequence identity amongst _N. azollae_ genomes taken from various _Azolla_ species indicates _N. azollae_ was likely introduced once in the symbiosis [Chapter \ref{it takes two}\; @Dijkhuizen2021].
Consequently, all cyanobacterial strains endophytic to _Azolla_ are likely the same cyanobacterial genus, perhaps even species.
At the fern Shoot Apical Meristem (SAM) lies a -somewhat ironically named- 'seed colony of motile _N. azollae_ filaments [Chapter \ref{it takes two}\; @Dijkhuizen2021, @Campbell1893].
Developing leaves encapsulate part of this seed colony as inoculum for every leaf's new cavity [@Campbell1893; @Nierzwicki-Bauer1989].
_Azolla_ ferns systematically transfer their symbiotic cyanobacteria to the next generations via their megaspores (+@fig:fig1_life-cycle).
Recent papers theorised that the symbiont entered the fern megaspores via small channels [@Ran2010; @Zheng2009].
We theorise that early developing spore primordia of either gender encapsulate part of the cyanobacterial seed-colony based on confocal imagery [Chapter \ref{it takes two}\; @Dijkhuizen2021], thereby mirroring the mechanism by which inoculates leaves.
Megasporocarps retain the cyanobacteria, which then develop into resting stages called akinetes.
Microsporocarps lose the symbiont throughout their development.
Electron and confocal microscopy of cyanobacterial resting stages inside microspores support this theory [Chapter \ref{it takes two}\; @Dijkhuizen2021, @Caiola1992].

_Azolla_ leaves and spores harbour by at least one other bacterium, as was shown in multiple species [@Gates1980; @Wallace1986; @Petro1987; @Caiola1988; @Plazinski1990; @Cohen2004; @Banach2019].
These additional bacteria are likely limited in number and relatively understudied compared to the main symbiont _N. azollae_.
While these bacteria were observed inside leaf pockets and spores by electron microscopy by various labs [@Wallace1986; @Nierzwicki-Bauer1990; @Carrapico1991; @Zheng2009], it remains unknown if they are also present in the SAM seed colony.
We theorise this is the case, based on their ostensibly systematic presence in multiple _Azolla_ species and increasing abundance in developing _Azolla_ leaves [@Petro1987].
Culture and electron microscopy-based techniques may also not be so reliable in attributing a species identification to a microbe and have led to uncertainty in comparing results generated in the previous century.
Conversely, the apparent benefit of culture-based techniques is the availability of bioassays and transformation, as in @Banach2019 and @Plazinski1990.
The uncertainty in classifying bacteria to a genus or species complicates estimating the identity and diversity of microbes endophytic to _Azolla_ [@Nierzwicki-Bauer1991; @Leonardi1993].
Nonetheless, _Arthrobacter_ is the most well-known genus associated with _Azolla_ ferns in these studies [@Petro1987].
It remains unclear if all species previously characterised by morphological features are identical or distinct bacteria.
In Chapter \ref{foul play} [@Dijkhuizen2018], we found DNA sequences of Rhizobiales and Burkholderiales associated with _A. filiculoides_.
These may be genome sequences of the bacteria observed earlier in earlier work.
Additionally, we found evidence that these microbes may be present in the _Azolla_ genus as a whole but not in the surrounding water we sampled, based on 16S data and read recruitment to reference genomes.

Regarding the function of _Azolla_ associated bacteria, many theories coexist in the literature that are not mutually exclusive.
In our previous work [Chapter \ref{foul play}\; @Dijkhuizen2018], we wondered whether these bacteria are foul players parasitising on the nitrogen fixed in the _Azolla_ symbiosis or if they are a third symbiotic party of benefit to the symbiosis, as did @Carrapico1991.
The seminal paper on the additional microbes of _Azolla_, @Wallace1986, already found that isolates from _Azolla_ leaves can denitrify NO~3~ to N~2~, indicating these microbes may gain energy from the ammonia fixed by _N. azollae_.
However, in Chapter \ref{foul play} [@Dijkhuizen2018], we found that the microbes whose genomes encode this pathway are outside the plant rather than inside the leaf cavities.
Additionally, we found no pathway to convert NH~4~ to NO~3~ in bacteria associated with _A. filiculoides_.
A second theory is that the other bacteria are mucilage producers, possibly facilitating a polysaccharide matrix for the _Azolla_-_Nostoc_ symbiosis [@Forni1992; @Zheng2009].
This hypothetical function is mainly attributed to a bacterium identified as _Arthrobacter_ [@Forni1992; @Forni1998].
A third theory is that the additional bacteria inside _Azolla_ leaves may also fix N~2~, mirroring the niche of the cyanobacterial symbiont.
@Lindblad1991 found these enzymes expressed inside _Azolla_ leaf bacteria by immunogold labelling and TEM.
In Chapter \ref{foul play} [@Dijkhuizen2018], we did not find evidence for this process, both in  N~2~^15^ labelling experiments and in the analyses of the genomes we sequenced.
A fourth theory is that these bacteria produce plant growth-promoting factors such as IAA when provided with tryptophan, theoretically reducing tryptophan-inhibition on nitrogen fixation and promoting plant growth by exporting auxin [@Forni1992b; @Forni1996; @Banach2019 ].

Here, we set out to reconstruct all _Azolla_ associated microbial genomes from public sequencing data; some data is part of a metagenomic study design, but most is not.
We take a similar approach as @Delmont2016, with two major adaptations: firstly, we remove as much as possible host DNA, and secondly, we broaden the perspective from a single species to a whole genus of species.
One species has been abundantly sequenced in various experimental designs: _Azolla filiculoides_.
Most species, however, have been sequenced once based on a single DNA extraction, as is the case for the _Azolla_ genome project.
The _Azolla_ genome project [@Li2018] provided the research community with the _A. filiculoides_ genome and WGS sequencing data for six of the seven known _Azolla species_.
This recent wealth in _Azolla_ sequencing data provides an opportunity to acquire more genomes of microbes associated with the _Azolla_ genus as a whole.
The experimental design of the _Azolla_ genome project does not facilitate metagenomics of a single _Azolla_ species.
Still, we may be able to use metagenomics techniques, thorough data filtering, and specific metagenomic data from other research projects on _Azolla_ species to acquire the genomes of _Azolla_ associated bacteria from this data.

This manuscript presents the methods by which we systematically acquire genomes of bacteria associated with the genus _Azolla_.
We assemble multiple high-quality Metagenome Assembled Genomes (MAGs) for each _Azolla_ species from publicly available data.
In doing so, we make our methods reproducible via the Snakemake and conda frameworks and document any progress in the workflow on Github.
Finally, we are glad to share the genomes of all these _Azolla_ associated bacteria with the _Azolla_ community for further studies: The _Azolla_ genus-wide metagenome.

## Methods

### Tools and data availability
In this study, we use various metagenomics tools to acquire genomes of bacterial endophytes associated with an entire genus of hosts
from publicly available bulk DNA extractions.
Sequenced DNA of various sources was iteratively filtered and assembled into contigs with SPAdes [@Nurk2017].
Data was filtered in the first filter stage by mapping [@Li2009a] against a curated reference consisting of host nuclear DNA and chloroplast DNA by @Li2018 (Azfiv1.1 fernbase) (host filtered).
For the _Azolla_ genus, only the genome of _Azolla filiculoides_ is available; hence this was used for filtering all _Azolla_ species studied here.
Before using as a filter, the _Azolla filiculoides_ reference genome's taxonomy was rid of any bacterial contigs with CAT [@VonMeijenfeldt2019].
CAT assigned an approximate taxonomy to contigs by first finding all open reading frames (ORFs), then blasting these to a custom database consisting of the NCBI blast NR protein database and all high confidence proteins of the _A. filiculoides_ v1.1 genome assembly.
Only contigs classified as eukaryotic were kept in the filter.
The reads passing the filter were assembled with SPAdes in metagenomics mode [@Nurk2017].
This first filtering step was not expected to perform equally well for all _Azolla_ species, especially those more phylogenetically distant to the reference genome.
Hence in a second filter, eukaryotic contigs were identified in each of the host filtered assemblies and used as a second filter tailored to a specific sequencing library.
These double-filtered reads were then assembled again with SPAdes metagenomics mode.
Only after this second filtering, step hybrid assemblies were generated when multiple sequencing libraries were available per biological sample.
After assembly, scaffolds were binned into Metagenome Assembled Genomes (MAGs) with several tools, then curated manually in Anvi'o [@Eren2015].
To reproducible execute and document these analyses, a bioinformatic workflow was created with snakemake [@Molder2021] and documented in [Github](https://github.com/lauralwd/azolla_genus_metagenome).
All tools used in this snakemake workflow are selected and installed from the Bioconda repository of bioinformatics software.
Conda environments used in this study can be found in [github env link](https://github.com/lauralwd/Azolla_genus_metagenome/tree/master/envs).

### Data
Sequencing data used here represented six of seven species in the _Azolla_ genus and was generated as part of three studies (+@fig:fig3_data_overview).
These species are part of two subgenera, the _Rhizosperma_ section of the genus comprising _Azolla pinata_ and _Azolla nilotica_, and the _Euazolla_ section comprising the other four species (+@fig:fig3_data_overview\-A)
Within the _Euazolla_ section, two subclusters of closely related species can be distinguished; firstly _A. rubra_ and _A. filiculoides_ and secondly _A. mexicana_, _A. microphylla_ and _A. carolinana_.
These subclusters diverged between 10 and 20M years ago.
The _Rhizosperma_ section is represented only by _A. nilotica_ here and is estimated to have diverged from the _Euazolla_  section approximately 50M years ago (+@fig:fig3_data_overview\-A [@Metzgar2007].
The first published data of _Azolla_ Whole Genome Sequencing (WGS) data was Chapter \ref{foul play} [@Dijkhuizen2018].
In that study, we sampled _A. filiculoides_ from triplicate whole plant fractions and triplicate leaf-pocket enriched fractions (P1,2,3 and L1,2,3 respectively; +@fig:fig3_data_overview\-B).
Secondly, the _Azolla_ genome project [@Li2018] published short-read sequencing data of six _Azolla_ species, including _A. filiculoides_ and long-read sequencing of _A. filiculoides_ (+@fig:fig3_data_overview\-B).
Sequencing data is mainly generated on Illumina platforms with typical insert sizes of 400 to 800bp and typically yielding approximately 30Gbase of DNA, except for the P and L samples which yield 2 to 3Gbase per sample (+@fig:fig3_data_overview\-B).
Both studies' their _A. filiculoides_ samples originate from the same Ditch in Utrecht, the Netherlands.
One sample was treated to remove the most abundant symbiont: _N. azollae_; it is indicated as the no-cyano sample (+@fig:fig3_data_overview\-B).
All samples acquired from the International Rice Research Institute (IRRI) were maintained for approximately two decades by the IRRI by vegetative propagation [@Watanabe1992] (+@fig:fig3_data_overview\-B).
These plant strains were sampled at various locations around the globe (+@fig:fig3_data_overview\-C): _Azolla nilotica_, _Azolla rubra_, _Azolla mexicana_, _Azolla microphylla_, and two _Azolla_ samples, which were initially classified as _Azolla carolinana_ but are likely a new _Azolla_ species, here termed, _Azolla sp.nov._ [Chapter \ref{it takes two}\; @Dijkhuizen2021]
The third data source is the seminal paper introducing the _N. azollae_ genome sequence [@Ran2010].
This paper includes ion-torrent sequencing of a gradient purified extraction of the primary symbiont of _A. filiculoides_.
Data of the latter study was acquired from SRA: for the first and last studies via the accession numbers listed in +@fig:fig3_data_overview\-B.
Data from the _Azolla_ genome project was made available to our lab before it was uploaded to a repository.
Unfortunately, we cannot link the sample identities of the data made available to us with those uploaded to NCBI SRA.
Hence,  we refer to the study as a whole.
In total, this study examines eighteen sequencing libraries, taken from nine biological samples accounting for six _Azolla_ species, treating L1,2,3, P1,2,3 combined as one biological sample.

\begin{sidewaysfigure}
\begin{figure}
\hypertarget{fig:fig3_data_overview}{%
\centering
\includegraphics{source/figures/fig3_data-in-overview.pdf}
\caption{
  DNA sequencing of the \emph{Azolla} genus. The \emph{Azolla} genus phylogeny is adapted from Metzgar et al. (2007) (A). Sequencing data considered here for species in the \emph{Azolla} genus (B).
  Sequencing data was retrieved from two main studies:
  the \emph{Azolla} genome project from Li et al. (2018) with accession nr. PRJNA430527 and from
  Chapter \ref{foul play} (Dijkhuizen et al. 2018) with accession nr. PRJEB19522 abbreviated as α and β
  respectively in the final column of panel 1B.
  Sampling details are available in the latter paper.
  The original sampling location for \emph{Azolla} specimens sequenced and considered here (C).}
\label{fig:fig3_data_overview}
}
\end{figure}
\end{sidewaysfigure}

## Results

### Filtering of _Azolla_ sequencing data against host DNA reduces assembly size and the computational requirements thereof
First, we set out to rid raw WGS data from plant DNA to ease the assembly of the bacteria whose genomes are also present in this data.
Filtering reduces input complexity and hence reduces complexity in the assembly graph, possibly improving metagenome assembly quality.
The bioinformatic workflow developed here takes short-read DNA sequencing data as the main input, then iteratively removes host reads and finally assembles the remainder into contigs (+@fig:fig3_filtering_and_assembly\-A).
The first stage of host DNA removal is achieved by mapping DNA reads that passed trimmomatic Quality Control (QC) to a reference genome [@Bolger2014], then assembling the remaining reads into contigs with SPAdes in metagenomics mode [@Nurk2017] (host filtered).
QC removed, on average, 4.4% and no more than 7% of reads of any sequencing libraries (+@fig:fig3_filtering_and_assembly\-B; bottom).
Filtering with the reference genome reduced read input substantially for _A. filiculoides_ (51% of reads for lab samples and 79% for no-cyano samples; +@fig:fig3_filtering_and_assembly\-B; bottom; _Azolla filiculoides_).
Filtering efficiency diminished substantially even for species phylogenetically close (+@fig:fig3_data_overview\-A) to the reference genome such as _A. rubra_ 24% (+@fig:fig3_filtering_and_assembly\-B; bottom; _Azolla rubra_), and other species in the _Azolla_ section of the genus (between 18% and 20%) (+@fig:fig3_filtering_and_assembly\-B; bottom).
This first filtering step removed only 8% of reads for the phylogenetically distant _A. nilotica_ (+@fig:fig3_filtering_and_assembly\-B; bottom; _Azolla nilotica_).
After this first filtering step (host filtered), assemblies were typically around 600 Mbase and likely contained substantial amounts of host DNA (+@fig:fig3_filtering_and_assembly\-B; top).

To further improve filtering efficiency, a second filtering strategy was applied.
Assembled contigs of all host filtered assemblies were classified with CAT [@VonMeijenfeldt2019], and contigs classified as eukaryotic were used as a second filter specific for that particular sequencing library.
Contigs classified as eukaryotic did not contain substantial amounts (1Mbase or higher in all assemblies combined; [lauradijkhuizen.com/blog/AGMB](lauradijkhuizen.com/blog/AGMB)) of DNA classified as anything other than streptophyta hence the assemblies contain only one eukaryote: _Azolla_ ferns.
The efficacy of this second stage of host DNA removal was typically opposite to the former stage: being least effective for _A. filiculoides_ (no more than 11%) and _A. rubra_ (25%), whilst most effective for those farther removed in the phylogeny; i.e. 42% for _A. microphylla_ and 56% of _A. nilotica_ (+@fig:fig3_filtering_and_assembly\-B bottom filtered vs double filtered).
Combined, both filtering approaches removed between 50% and 64% of reads from plant samples maintained in the lab and not experimentally treated (+@fig:fig3_filtering_and_assembly\-B trimmed vs double filtered).
The double filtered reads were assembled again with SPAdes in metagenomics mode, both as single libraries or hybrid assemblies when multiple sequencing libraries or read types were available per biological sample (+@fig:fig3_filtering_and_assembly\-B top; H).
Assembly sizes were reduced substantially after the second filtering step for all species except for _A. filiculoides_ samples with lower insert sizes (+@fig:fig3_filtering_and_assembly\-B top).
Metagenome Assembly sizes typically varied from 160 to  250 Mbase, except for the _A. filiculoides_ wild sample (738 Mbase), the sterilised _A. filiculoides_ no-cyano sample (60 Mbase), and the _A. caroliniana_ 2 sample (456 Mbase) (+@fig:fig3_filtering_and_assembly\-B top).
The double filter reduced assembly size by 60% to 70% (+@fig:fig3_filtering_and_assembly\-B top).
Reduced assembly size and host DNA contamination make manual binning feasible, and metagenome assembly sizes (+@fig:fig3_filtering_and_assembly\-B top) indicate that all assemblies likely contain multiple bacterial genomes.
Secondly, removing host DNA from the assembly input reduces input complexity and thereby substantially reduces computational requirements for assembly in terms of peak RAM usage (+@fig:fig3_filtering_and_assembly\-B RAM usage).

![Filtering and assembly of DNA sequencing of the _Azolla_ genus. Sequencing filtering workflow and guide to the graph (A). Quantities of sequencing input in Gbase (B; bottom), corresponding assembly output during the process (B; top), and the peak RAM usage during the assembly process (B; RAM usage). The bottom panel shows consecutive sequencing quantities at raw, trimmed, host filtered, and double filtered stages. At the latter two stages, sequencing data was assembled with SPAdes. The upper half of panel B shows assembly RAM usage in Gbyte and assembly sizes in MBase for both filtering stages of single sequencing library assemblies and hybrid assemblies if applicable.](source/figures/fig3_sequencing-filtering-and-assembly.pdf){#fig:fig3_filtering_and_assembly}

### Filtering reduced eukaryotic DNA content but did not increase the assembly quality of bacterial DNA
Filtering input sequencing data reduced assembly size.
Next, we investigate the efficacy of this filtering approach in terms of taxonomic complexity and quality of the assembly.
The main rationale for this intensive filtering approach was to decrease complexity in the metagenome assembly graph, thereby improving the length and quality of assembled bacterial contigs.
The double filtering step substantially reduced total assembly size (+@fig:fig3_filtering_and_assembly\-B top) and length distributions of eukaryotic contigs (+@fig:fig3_filter_length_distributions Eukaryota, +@tbl:tbl3_1), as well as contigs which were not assigned a taxonomy or did not yield any open reading frames (+@tbl:tbl3_1).
These latter two taxonomical categories often had similar depth/length distributions as scaffolds assigned Eukaryota ([lauradijkhuizen.com/blog/AGMB](lauradijkhuizen.com/blog/AGMB)).
In contrast, bacterial assembly size and length distributions were practically identical between the two different filtering stages (+@fig:fig3_filter_length_distributions Bacteria), although the average and median scaffold size did increase slightly (+@tbl:tbl3_1 Bacteria).
Contigs assigned as Archeal in the host filtered assembly were not classified as such in the double filtered assembly (+@fig:fig3_filter_length_distributions Archaea).
Similarly, viral contigs often were only assembled in the host filtered assembly (+@fig:fig3_filter_length_distributions Viruses).
The bacterial fraction of the metagenome assembly is of substantial size and was not negatively affected by the filtering approach, thereby paving the way to investigate the diversity of bacterial genomes in this fraction.

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
\hypertarget{fig:fig3_filter_length_distributions}{%
\centering
\includegraphics{source/figures/fig3_figure-filter-length-distributions.pdf}
\caption{Length distributions of \emph{Azolla} sp. metagenome assembles per kingdom before and after two stages of filtering.
  Metagenome assemblies of individual sequencing libraries (\cref{fig:fig3_data_overview}) were filtered with the Host genome (Host filtered; red) and with a library specific subset of eukaryotic contigs (Double filtered; blue; \cref{fig:fig3_filtering_and_assembly}).
  Scaffolds of metagenome assemblies were assigned taxonomy with CAT (Von Meijenfeldt \emph{et al}. 2019), and their length distributions were plotted as boxplot per taxonomic kingdom (vertical panels: Viruses, Eukaryota, Bacteria and Archae) per sequencing library (horizontal panels).
  The width of the boxplot is proportional to the number of scaffolds represented (\cref{tbl:tbl3_1}).}
\label{fig:fig3_filter_length_distributions}
}
\end{figure}
\end{sidewaysfigure}

### Filtered metagenome assemblies contain distinct microbial genomes systematically reoccurring in the _Azolla_ genus
The double filtered assemblies contain numerous bacterial contigs of each _Azolla_ species sampled here (+@fig:fig3_filter_length_distributions Bacteria).
Next, we take a genus perspective and compare these assemblies by taxonomy and abundance, now counting scaffolds rather than contigs.
Bacterial scaffolds in all double filtered assemblies had a median length of 5671 bp; hence, bacterial genomes in the assembly are highly fragmented.
Despite this fragmentation, scaffolds group into approximate bacterial genomes quite distinctly when examining them by their abundance, length, and taxonomy as determined by CAT (+@fig:fig3_Azolla_genus_metagenome_order).
The genomes can be recognised as clusters of scaffolds with equal abundance and taxonomy but varying scaffold lengths (+@fig:fig3_Azolla_genus_metagenome_order).
All samples but the no-cyano sample (+@fig:fig3_Azolla_genus_metagenome_order Azfil_minuscyano) show the most abundant species in the metagenome is a Nostocales cyanobacterium (+@fig:fig3_Azolla_genus_metagenome_order cyan blue).
Rhizobiales genomes were found in all _Azolla_ species sampled here, visible as horizontal clusters of dots with identical colour (+@fig:fig3_Azolla_genus_metagenome_order purple).
Plotting the scaffolds of all assemblies by these two characteristics allows one to distinguish individual bacterial genomes in each of the _Azolla_ species sampled here (+@fig:fig3_Azolla_genus_metagenome_order).

\begin{sidewaysfigure}
\begin{figure}
\hypertarget{fig:fig3_Azolla_genus_metagenome_order}{%
  \centering
  \includegraphics{source/figures/fig3_Azolla_genus_metagenome_order.png}
  \caption{Metagenome assemblies of 6 species of the fern genus Azolla (horizontal panels).
    Sequencing data was derived from three public projects \cref{fig:fig3_data_overview}.
    Sequencing reads were rid of host plant DNA reads and assembled with SPAdes in metagenome mode \cref{fig:fig3_filtering_and_assembly}-A.
    The resulting scaffolds were then assigned an approximate taxonomy with CAT (VonMeijenfeldt \emph{et al}. (2019)).
    Metagenome assembly scaffolds are displayed as dot plots with length on the x-axis and depth in the assembly graph on the y-axis; both log10 transformed.
    Dot colour represents the taxonomical order, and dot size represents ORF count.
    Scaffolds without ORFs and scaffolds without taxonomy are filtered out for clarity.
    Additionally, scaffolds are filtered if they have less than 5 ORFs classified or when a taxonomic group amounts to less than 2Mbase in the entire figure.
    An \href{https://utrecht-university.shinyapps.io/Azolla_genus-wide_metagenome_taxonomy/}{online interactive version of this figure} can be manipulated to modify these filters and assumptions and to include more assemblies done in the \emph{Azolla} metagenome project.
    }
    \label{fig:fig3_Azolla_genus_metagenome_order}
}
\end{figure}
\end{sidewaysfigure}

Even before binning scaffolds into MAGs, metagenomes of the _Azolla_ genus show clear similarities; several taxonomical orders reoccur systematically (+@fig:fig3_Azolla_genus_metagenome_order).
Most prominently, the Nostocales are the most abundant order in all _Azolla_ species except one, which was artificially devoid of the cyanobacteria.
Contigs assigned Nostocales have a high variance in abundance; standard deviations vary in the various samples from 300 to 600 (arbitrary unit representing depth in the assembly graph; +@fig:fig3_Azolla_genus_metagenome_order; [lauradijkhuizen.com/blog/AGMB](https://www.lauradijkhuizen.com/blog/AGMB)).
In contrast, other distinguishable microbial genomes show a typical depth standard deviation often lower than 1, but in almost all cases lower than 10 (depth variance visible in the interactive figure).
This abundance pattern of _Nostoc azollae_ is typical of a degraded genome with many transposons and repetitive regions and may explain why the assembled length of this MAG is shorter than the reference; 4Mbase rather than 6Mbase (+@tbl:tbl3_2).
Nevertheless, it might also indicate an upper limit of assembly depth.
The second most abundant order across the genus is the Rhizobiales, ranging between 16 and 44 Mbase of assembled DNA in the different samples (+@fig:fig3_Azolla_genus_metagenome_order blue; [lauradijkhuizen.com/blog/AGMB](https://www.lauradijkhuizen.com/blog/AGMB)).
In all host species, multiple Rhizobiales genomes can be distinguished.
The third most abundant order is the Burkholderiales (+@fig:fig3_Azolla_genus_metagenome_order yellow), which is present in all host species except for _A. rubra_ and amounts to between 5 and 17 Mbase per assembly ([lauradijkhuizen.com/blog/AGMB](https://www.lauradijkhuizen.com/blog/AGMB)).
Other notable orders reoccurring in several metagenome assemblies are the Caulobacterales, Nevsiales and Sphingomonadales.
Each of these last three orders occurs in at least five of the six host species and is found in data from different studies.

Metagenome assemblies likely do not fully represent all bacteria in the original plant samples.
When approaching the least abundant scaffolds, scaffold length diminishes to less than 1Kb, indicating the lower abundance limit of assembly.
This lower limit region contains a substantial amount of scaffolds from different orders of taxonomy.
This diversity indicates that several low abundant microbes were too lowly abundant to assemble properly; hence, the current assemblies are likely incomplete representations of the microbial diversity associated with these plants.
An exception to this observation is the _A. filiculoides_ minus_cyano sample.
Here, all scaffolds assembled are highly abundant and are rather long compared to non-sterilised plant samples.
Hybrid assemblies are a second exception to this observation.
In these assemblies, final graph resolution was aided by PacBio long reads from the _A filiculoides_ minus_cyano sample.
In this process, low abundant scaffolds were combined into longer scaffolds aided by long read data.
However, the scaffold abundance remains a reflection of the original Illumina contribution to that scaffold only, but it is corrected for the new scaffold length, explaining why such long scaffolds can have such a low abundance.

### _Azolla filiculoides_ contains multiple endophytic bacteria
Contigs of metagenome assemblies were manually binned into MAGs.
First, metagenome assemblies were binned automatically by both metabat2 and concoct based on their 4mer profiles and differential abundance in various sequencing libraries.
Then, these automatically generated MAGs were imported into Anvi'o and curated manually while being guided by the automated binning and scaffold taxonomy determined by CAT.

The _A. filiculoides_ wild sample metagenome contains multiple high-quality MAGs, several likely from species living inside the plant leaf cavities.
Only sequencing data of the _A. filiculoides_ wild sample was derived from a metagenomic study design, including samples of whole plants and leaf-pocket enriched 'juice'.
Separating the different MAGs in this metagenome assembly benefits from differential sampling and the consequent differential abundance of genomes per sample (+@fig:fig3_Azfil_wild_binning).
Additionally, the PacBio RSII long-read sequencing of the _A. filiculoides_ minus-cyano sample was used as an additional binning signal to distinguish MAGs; this data was used for scaffolding the assembly of the _A. filiculoides_ wild sample.
Several MAGs of similar taxonomy, i.e. Rhizobium and Rhizobiales, could be resolved into well distinguished high-quality MAGs.
Binning yielded seven high-quality bins in total (completeness > 90% redundancy < 10%) with appropriate genome sizes, three medium-quality MAGs also with appropriate sizes(completeness > 60%), and several low-quality bins likely representing partial genomes of low abundant bacteria. (+@tbl:tbl3_2).
Despite the metagenomic study design, not all bins could be resolved to high quality.
This may be related to the relatively low input of DNA sequencing in the assembly, hence not allowing to sufficiently resolve lowly abundant microbial genomes.
Differential sampling, comparing the whole plant to leaf cavity enrichments, allows estimating whether a MAG is more abundant in the leaf cavities.
The bacteria represented by these MAGs are likely endophytes of _A. filiculoides_ (+@fig:fig3_Azfil_wild_binning blue rings).
This is the case for MAGs 'Rhizobium','Rhizobiales','Curvibacter', and 'Ferrovibrio' (+@fig:fig3_Azfil_wild_binning).
The former two are abundant in PacBio long-read sequencing of the _A. filiculoides_ minus_cyano sample, indicating they survived stringent sterilisation and antibiotic regime removing the main symbiont _N. azollae_.
Conversely, MAGs of similar taxonomy are detected in the _A. filiculoides_ 'lab' (+@fig:fig3_Azfil_lab_binning) and 'minus-cyano' assemblies (+@fig:fig3_Azfil_minus_cyano_binning)
These bins, specifically the Rhizobiales and Burkholderiales orders, recruit reads from the _A. filiculoides_  'wild' binning signals (blue and green rings in +@fig:fig3_Azfil_lab_binning \& +@fig:fig3_Azfil_minus_cyano_binning).
In contrast, a second cyanobacterium in the _A. filiculoides_ 'wild' assembly is present only outside the ferns and not in the leaf cavity enriched fraction nor in the lab-derived assemblies.
This difference indicates that this particular cyanobacterium is epiphytic, consistent with earlier findings that _Azolla_ has only one cyanobacterial symbiont.

![Anvi'o overview of the _A. filiculoides_ 'wild' metagenome assembly and binning into MAGs. The centre dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (light green), scaffold abundance in PacBio reads from the _A. filiculoides_ 'lab' sample (yellow). Then follow several coloured rings representing taxonomy determined by CAT, starting at the kingdom level down to the species level. The before-last red ring indicates the presence of any ribosomal RNA genes in a scaffold (drastically influencing the depth of the scaffold and, therefore, the binning process). The final ring indicates in which bin a scaffold was categorised. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_2.](source/figures/fig3_Azfil_wild_binning.pdf){#fig:fig3_Azfil_wild_binning}

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

\caption{Quality, taxonomy and abundance of MAGs assembled from sequencing data
         derived from the \emph{A. filiculoides} 'wild' sample.
         Quality is assessed as approximate genome completion and redundancy by two
         distinct tools: Anvio (Eren et al. 2015) and CheckM (Horton et al. 2014).
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

### Binning assemblies from non-metagenomic data is feasible with extraneous binning signals
Provided with thoroughly filtered metagenome assemblies, the binning process becomes feasible even if the assembly lacks a metagenomic study design.
Typically, binning would depend highly on the differential abundance of scaffolds over various sequencing libraries and, to a lesser extent, on k-mer profiles of scaffolds.
However, several _Azolla_ species sequenced have only one sample, hence one sequencing library available.
Therefore, binning cannot use differential abundance over various samples.
Within the _Azolla_ genus, we assume several microbes or close relatives may be shared among several _Azolla_ species.
Under this assumption, we employed a manual method adding extraneous binning signals from the one metagenomic study done on this genus, the seminal paper on the _N. azollae_ genome, and scaffold taxonomy determined by CAT.
No automated binning algorithm can implement these binding signals while accounting for the nuances required in interpreting them; hence automated binning algorithms will likely produce false MAGs.
Using Anvi'o [@Eren2015], it is possible to visualise the aforementioned extraneous binning signals and bin scaffolds manually whilst accounting for the nature of different binning signals appropriately.
Within Anvi'o, all metadata was plotted per metagenome assembly.
Next, scaffolds were binned manually, guided at first by automated binning methods but primarily by scaffold depth in the native sequencing libraries for that particular biological sample.
Contig depth was often the clearest binning signal in these samples (+@fig:fig3_Azmic_binning).
Abundance in _A. filiculoides_ 'wild' sequencing was used carefully when applicable and checked with anvi'o clustering based only on k-mer profiles.
Manual binning of _A. microphylla_ yielded nineteen MAGs, of which eleven can be considered high quality and four medium quality, all with appropriate genome sizes. (+@tbl:tbl3_MAGs_azmic),

In some metagenomes, the extraneous binning signals provided helpful information for some bins, for example, in _A. rubra_ and _A. mexicana_ (+@fig:fig3_Azrub_binning; +@fig:fig3_Azmex_binning).
In other metagenomes, like _A. microphylla_, the extraneous binning signals provided little to no additional information for clustering (+@fig:fig3_Azmic_binning).
In such cases, abundance in the native sequencing library and k-mer clustering were used to disentangle bins from one another.
Exceptionally, clustering dendrograms showed better clusters when clustering only on k-mer content and not on abundance data (+@fig:fig3_Aznil_binning; +@fig:fig3_Azcar_1_binning).
Finally, scaffold taxonomy was considered as an indication to support specific groupings of scaffolds.
Scaffold taxonomy often showed discrete patterns matching the input dendrogram and binning when other binning signals were already distinctive, further solidifying CAT taxonomy as a valuable binning signal.
CAT taxonomy helped considerably when other binning signals were lacking, for example, in the case of the _A. caroliniana_ '2' metagenome (+@fig:fig3_Azcar_2_binning).
In no case of manual metagenome binning was CAT taxonomy used as input for the clustering dendrograms in any of the Anvi'o figures.

![Anvi'o overview of the _A. microphylla_ metagenome assembly and binning into MAGs. The centre dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles but not differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. microphylla_ sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (green). Then follow several coloured rings representing taxonomy determined by CAT, starting at the kingdom level down to the species level. The before-last red ring indicates the presence of any ribosomal RNA genes in a scaffold (drastically influencing the depth of the scaffold and, therefore, the binning process). The final ring indicates in which bin a scaffold was categorised. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_MAGs_azmic.](source/figures/fig3_Azmic_binning.pdf ){#fig:fig3_Azmic_binning}

\begin{threeparttable}

\begin{longtable}[]{@{}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.30}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.35}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.1}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 16\tabcolsep) * \real{0.05}}@{}}

\caption{Quality and taxonomy bins/MAGs assembled from sequencing data derived
         from \emph{A. microphylla}.
         Quality is assessed as approximate genome completion and redundancy by
         two distinct tools: (Eren et al. 2015) and CheckM (Parks et al. 2015).
    \label{tbl:tbl3_MAGs_azmic}}
\tabularnewline

\toprule
taxonomical order\tnote{a}    &
MAG name\tnote{b}             &
\rotatebox{45}{MAG length (Mbase)}            &
\rotatebox{45}{Anvi'o completeness\tnote{c}}  &
\rotatebox{45}{Anvi'o redundancy\tnote{c}}    &
\rotatebox{45}{CheckM completeness\tnote{c}}  &
\rotatebox{45}{CheckM redundancy\tnote{c}} \\
\midrule
\endhead
Acidobacteriaceae   & Acidobacteria             & 4.29 &  82 &  4 &  76 & 0 \\
Micrococcales       & Actinobacteria            & 3.34 &  92 & 27 &  77 & 4 \\
Caulobacterales     & Alphaproteobacteria       & 4.80 &  99 &  4 &  80 & 4 \\
NA                  & Alphaproteobacteria2      & 5.13 &  93 &  4 &  91 & 1 \\
Caulobacterales     & Asticcacaulis             & 3.48 &  70 &  1 &  82 & 3 \\
Caulobacterales     & Asticcacaulis\_taihuensis & 4.14 &  99 &  0 &  98 & 0 \\
Cytophagales        & Bacteriodetes             & 6.37 &  99 &  0 &  97 & 0 \\
Burkholderiales     & Herbaspirillum            & 4.81 &  96 &  6 &  86 & 2 \\
Rhizobiales         & Bradyrhizobiaceae         & 7.29 & 100 &  0 & 100 & 0 \\
Rhizobiales         & Hyphomicrobium            & 3.67 &  76 & 10 &  72 & 2 \\
Nevskiales          & Nevskia                   & 6.01 & 100 &  4 &  98 & 5 \\
Sphingomonadales    & Novosphingobium           & 4.51 & 100 &  4 &  99 & 1 \\
Rhizobiales         & Rhizobiales2              & 5.01 &  94 &  4 &  97 & 1 \\
Rhizobiales         & Rhizobiales3              & 2.34 &  28 &  3 &  16 & 1 \\
Rhizobiales         & Rhizobiales1              & 7.15 &  93 &  4 &  95 & 1 \\
Nostocales          & Trichormus                & 4.85 &  97 &  4 &  99 & 0 \\
Cytophagales        & rest                      & 0.53 &  15 &  4 &  11 & 0 \\
NA                  & rest2                     & 0.21 &   0 &  0 &   6 & 0 \\
Burkholderiales     & rest3                     & 1.62 &   0 &  0 &  20 & 0 \\
\bottomrule
\end{longtable}

\begin{tablenotes}
  \footnotesize
  \item[a] Taxonomic order determined by BAT taxonomy (VonMeijenfeldt \emph{et al.} (2019)
  \item[b] manually assigned name
  \item[c] MAG completeness and redundancy assessed via Single Copy Marker Gene scoring
\end{tablenotes}

\end{threeparttable}

### Manual binning yields up to 21 bins per sample, outperforming automated binning with extraneous binning signals
Manual binning with extraneous binning signals and scaffold taxonomy provided high-quality bins for all metagenome assemblies (+@tbl:tbl3_4).
The method yields between 12 and 21 bins for each non-sterilised _Azolla_ sample, of which the majority are considered high-quality bins.
Manual binning explains between 95 and 100% of each metagenome assembly (+@tbl:tbl3_4).
Automated binning approaches like Concoct within Anvi'o [@Eren2015] and Metabat2 were often near-equally good in distinguishing bins of high quality (+@fig:fig3_binning_QC_anvio & +@fig:fig3_binning_QC_checkm) as the manual approach.
The manual approach, however, succeeds in improving bin quality of those bins of medium quality (i.e. +@fig:fig3_binning_QC_anvio; _A. filiculoides_ 'minus-cyano') and low quality (i.e. +@fig:fig3_binning_QC_anvio; _A. mexicana_).
Additionally, the manual method creates fewer bins compared to the automated methods (+@fig:fig3_binning_QC_anvio; black numbers: Concoct & Metabat2 vs Manual), while the amount of bins of high-quality increases or remains stable (+@fig:fig3_binning_QC_anvio; green numbers).
This effectively means the diversity in a metagenome is explained with fewer genomes and of higher quality.
Hence, the manual method allows to more reliably study the genomes of more bacteria associated with a sample.

![Binning quality control in Anvi'o [@Eren2015] of various binning methods. The quality of bins was assessed as completeness (dark green) and redundancy (red) by scoring SCMGs. Bin quality was assessed for all bins of all metagenome assemblies, comparing two automated binning methods (Metabat2 and Concoct) and the manual method described here (Manual). Numbers in the panels show the total number of bins created by a particular method for a particular assembly (black) and those bins passing QC criteria of completeness above 90% and redundancy below 10% (Dark green). Grey lines in the figure also indicate these thresholds. Similar statistics were generated with CheckM [@Parks2015], utilising a different set of SCMGs. See +@fig:fig3_binning_QC_checkm](source/figures/fig3_binning_QC_anvio.pdf ){#fig:fig3_binning_QC_anvio}

\begin{threeparttable}
\begin{longtable}[]{@{}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.3}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}
  >{\raggedright\arraybackslash}p{(\columnwidth - 8\tabcolsep) * \real{0.05}}@{}}

\caption{MAG yield per biological sample and their quality as assessed
  by the presence of single copy marker genes via both Anvi'o and CheckM.
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
\emph{Azolla mexicana}                    & 21 &100 & 10 & 13 \\
\emph{Azolla nilotica}                    & 20 & 96 &  7 &  7 \\
\emph{Azolla microphylla}                 & 19 & 95 & 11 &  9 \\
\emph{Azolla filiculoides} 'wild'         & 17 & 97 &  6 &  6 \\
\emph{Azolla filiculoides} 'lab'          & 17 & 95 &  7 &  7 \\
\emph{Azolla carolinana} 1                & 15 & 99 &  7 &  9 \\
\emph{Azolla carolinana} 2                & 13 & 99 &  9 & 12 \\
\emph{Azolla rubra}                       & 11 &100 &  8 &  9 \\
\emph{Azolla filiculoides} 'minus-cyano'  &  5 &100 &  5 &  5 \\
\bottomrule
\end{longtable}

\begin{tablenotes}
  \footnotesize
  \item[a] Passing QC means over 90% completeness and less than 10% redundancy.
  \item[b] Calculated as the percentage of bases from scaffolds over 2.5kbp that are part of any bin.
\end{tablenotes}

\end{threeparttable}

Next, we assessed bin taxonomy and used successful taxonomic classification as a quality metric.
Bins were processed with CAT [@VonMeijenfeldt2019] mode for bins: BAT.
Since taxonomy is now determined for long bins rather than short scaffolds, classification is likely more accurate.
First, we compare the number of bins without classification for all host species and the three different binning methods.
Again, the manual method outperforms the two automated methods, creating fewer bins without taxonomy on practically all levels of taxonomy in all metagenome assemblies (+@fig:fig3_binning_QC_no_taxonomy).
Nearly all bins are assigned a taxonomy in all samples at the order level.
Given the high generally QC scores and assigned taxonomy, these binned metagenomes are ready to be studied in more detail.

![Counts of bins without taxonomic classification. Bin taxonomy was determined with BAT [@VonMeijenfeldt2019], and then counts of bins without taxonomy are shown as line plots for various levels of taxonomy (x-axis) and individual metagenome assemblies (vertical panels). Different binning methods (Concoct, Metabat2, Manual) are depicted in red, green and blue, respectively.](source/figures/fig3_binning_QC_no_taxonomy.pdf){#fig:fig3_binning_QC_no_taxonomy}

### Systematic occurrence of taxonomical orders in the entire _Azolla_ genus
Next, we assessed whether bins of certain taxonomical orders reoccur systematically in the _Azolla_ genus as scaffolds did in +@fig:fig3_Azolla_genus_metagenome_order.
Since the binning process has concluded satisfactory, bins are now termed MAGs.
A similar pattern can be seen when counting MAGs classified to the aforementioned orders across all biological samples.
At the level of Phylum, the common denominator consists of cyanobacteria and proteobacteria (+@fig:fig:fig3_binning_QC_all_taxonomy; Phylum), the latter being dominated by Alphaproteobacteria at the class level (+@fig:fig:fig3_binning_QC_all_taxonomy; class).
However, betaproteobactera are also present in all _Azolla_ samples, and gammaproteobacteria in all non-sterilised samples in the _Euazolla_ section of the _Azolla_ genus (+@fig:fig3_data-in-overview).
Specifically, at the order level (+@tbl:tbl3_5; +@fig:fig3_binning_QC_all_taxonomy; order), Rhizobiales bacteria can be found in multiple bins associated with any of the _Azolla_ species examined, ranging from 4 to 8 bins.
Burkholderiales bacteria can be found in all but one biological sample and in all of the examined species.
These two orders of bacteria are also the two orders present in the _A. filiculoides_ minus_cyano sample, and hence survived intensive sterilisation and antibiotic treatment.
Bins of these orders were also found to be endophytic in _A. filiculoides_ 'wild'.
Both types of evidence support their endophytic status in both _A. filiculoides_ and the _Azolla_ genus as a whole.
Caulobacterales and Nevskiales were found in all _Azolla_ species in the _Euazolla_ section; all species except for _A. nilotica_.
Finally, the Sphingomonadales order was found in all species except for _A. rubra_.
The latter three those orders were not systematically found in all _Azolla_ species but were found in plants sampled at different locations and sequenced in different labs.
At the level of family and genus, few common denominators remain.
The primary symbiont is distinguishable as Nostocaceae or Trichormus, respectively.
Bacterial families that stand out are Sinobacteraceae, Bradyrhizobiaceae and Calubacetaceae.

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
Nevskiales        & 1 & 0 & 1 & 1 & 1 & 0 & 1 & 2 & 1 \\
Nostocales        & 1 & 0 & 1 & 1 & 1 & 1 & 1 & 1 & 1 \\
Rhizobiales       & 8 & 3 & 5 & 8 & 5 & 6 & 5 & 4 & 5 \\
Sphingomonadales  & 1 & 0 & 0 & 2 & 1 & 1 & 0 & 1 & 1 \\
\bottomrule
\end{longtable}

\begin{sidewaysfigure}
\begin{figure}
\hypertarget{fig:fig3_binning_QC_all_taxonomy}{%
\centering
\includegraphics{source/figures/fig3_binning_QC_all_taxonomy.pdf}
\caption{heatmap of MAG taxonomy (horizontal axis) for all metagenome assemblies (vertical axis) for various levels of taxonomy (horizontal panels).
  Quantity is indicated as a shade ranging from dark blue to bright yellow.
  }
\label{fig:fig3_binning_QC_all_taxonomy}
}
\end{figure}
\end{sidewaysfigure}

## Discussion
In this study, we acquired high-quality MAGs from non-metagenomic sequencing data of 6 species of the _Azolla_ genus (+@fig:fig3_data_overview) through a process of thorough filtering (+@fig:fig3_filtering_and_assembly), thereby substantially reducing the fraction of eukaryotic DNA whilst not impacting Bacterial assembly quality (+@fig:fig3_filter_length_distributions).
Each species' metagenome assembly contained several distinct bacterial genomes, and these metagenomes resembled each other in terms of taxonomy (+@fig:fig3_Azolla_genus_metagenome_order).
Manual binning (+@fig:fig3_Azfil_wild_binning +@fig:fig3_Azmic_binning) allowed to retrieve these MAGs better than automated binning approaches (+@fig:fig3_binning_QC_anvio; +@fig:fig3_binning_QC_no_taxonomy) and provide them to the _Azolla_ and plant-microbe research community.
Several orders of bacteria are systematically associated with the _Azolla_ genus as a whole (+@fig:fig:fig3_binning_QC_all_taxonomy; order).

### Metagenome assemblies can be retrieved from publicly available non-metagenomic data
Acquiring metagenomes from public sequencing data not originally meant for metagenome assembly is feasible and may be further applied to shed light on the mechanisms of host-microbe symbioses.
Researchers interested in metagenomes may use a similar method as demonstrated here to mine existing data for microbial genomes.
The approach is especially interesting if a host species is already known or suspected to host bacteria or if bacterial DNA was previously identified in reads or assemblies of a sequencing run, as was the case for _Azolla_.
However, not all eukaryotic species or DNA extractions will encompass substantial fractions of DNA from associated bacteria.
Before thorough and costly filtering and assembly, sequencing data may be searched for signs of bacterial genomes as we have done in Chapter \ref{foul play} [@Dijkhuizen2018].
Such signals could be extracted from raw sequencing data, for example, by searching for rRNA reads [@Miller2011; @Xie2016], for bacterial genes similarly to @VonMeijenfeldt2019 or by kmer-based approaches such as kraken2 [@Wood2019].
This approach allowed us to find bacteria associated with hosts studied in the past and paves the way to further mine host-bacteria interactions in a great variety of data from past experiments and multiple labs, as demonstrated here.

High-quality MAGs can be assembled from bulk DNA extractions with minimal filtering, but this process requires manual curation and interpretation.
The double filtering of bulk DNA sequencing proved effective in removing host DNA even if only a related host genome was available (+@fig:fig3_filtering_and_assembly).
Metagenome assemblies of double filtered data showed clean and distinct clusters of scaffolds resembling single bacterial genomes (+@fig:fig3_Azolla_genus_metagenome_order).
The approach was, however, unnecessarily costly, for assembly quality did not increase (+@fig:fig3_filter_length_distributions; +@tbl:tbl3_1).
The k-mer spaces in which these genomes are assembled are presumably so distinct that they do not overlap in a De Bruijn graph even before filtering.
Therefore, the co-assembly of these genomes would not create ambiguities which the assembler could not solve.
By this argument, filtering of the bulk DNA extraction may even be obsolete; @Delmont2016 showed that bacterial genomes could be extracted from a bulk assembly of host and symbionts.
Particularly for very big host genomes, as is the case for the _Azolla_ genus, removing host DNA with a single host filtering step may be the preferable and faster approach than (re)assembling the host's genome in the process.
At the very least, host filtering allows to assemble a metagenome with fewer RAM resources (+@fig:fig3_filtering_and_assembly\-B; RAM usage) and hence allows for bigger hybrid assemblies.
Alternatively, host scaffolds can be removed after assembly using CAT taxonomy, thereby relaxing resource requirements for the manual binning process.
The Anvi'o interactive interface was essential in manual binning, but the feasibility of this process was reduced substantially with very large metagenome assemblies such as that of _A. rubra_ at 200 MBase.
We estimate that the beneficial effect of filtering after assembly on manual binning feasibility would equal the double filtering step.

In the methods presented here, we deliberately do not provide a single tool to the community.
We aim to make the method as open and reproducible as possible by documenting the workflow on Github and discussing the benefits and costs of several aspects of our approach in this manuscript.

### Manual curation allowed for high-quality bins
Binning of non-metagenomic assemblies is possible and may be aided by extraneous binning signals and scaffold taxonomy.
Here, we assemble DNA extracted from bulk plant samples and retrieve MAGs of bacteria associated with those plants.
Ideally, differential sampling of various fractions or biological replicates allows distinguishing scaffolds of the various genomes from each other.
In the data used here, this differential sampling is often not present.
Instead, we build on the assumption that some microbes may be shared amongst different _Azolla_ species and use sequencing data of related species to differentiate different microbial genomes from each other.
Such extraneous binning signals may provide false motivation to exclude a certain part of a microbe's genome that is present in the assembly but not in the data used as a binning signal.
Therefore, we consider manual curation a requirement when using such binning signals while appropriately valuing and cross-referencing the different binding signals available.
In binning the _Azolla_ species studied here, binning signals of related samples were occasionally informative in the manual binning process (+@fig:fig3_Azmex_binning), but some samples not (+@fig:fig3_Azmic_binning).
This method can be informative only when genomes in a metagenome are expected to be shared between two different host DNA extractions.
The feasibility of this approach depends on the community complexity, relatedness of the samples available, and similarity of microbes in those samples.

Scaffold taxonomy determined by CAT proved to be a valuable additional binning signal when differential abundance was lacking.
CAT classifications often overlapped well with bins demarcated clearly by other binning signals (+@fig:fig3_Azfil_wild_binning; +@fig:fig3_Azmic_binning; +@fig:fig3_Azfil_lab_binning; +@fig:fig3_Azfil_minus_cyano_binning; +@fig:fig3_Azmex_binning; +@fig:fig3_Aznil_binning; +@fig:fig3_Azrub_binning; +@fig:fig3_Azcar_1_binning; +@fig:fig3_Azcar_2_binning).
This result further confirms the robustness of CAT scaffold classifications and its use case for manual binning when depth and k-mer profiles are lacking.
The specificity of CAT taxonomy differed substantially: some bins were reliably and reproducibly classified at the genus level (+@fig:fig3_Azmic_binning; Nevskia) while others only were classified at the phylum level (+@fig:fig3_Azmic_binning; Bacteriodetes).
Database bias surely plays a role in this specificity issue, but our results show that per bin, both the taxonomy and specificity thereof are consistent.
Single copy marker gene validation with both CheckM and Anvi'o supported the quality of bins for which CAT classification was instrumental in their reconstruction.

Our view on these methods is that a researcher should bin primarily on the differential abundance in sample-native sequencing libraries and scaffold k-mer profiles.
When those primary binning signals are unclear, extraneous binning signals and scaffold taxonomy may be used in an advising manner.
Additionally, when using extraneous binning signals, these potential MAGs should be cross-referenced with the k-mer profile only clustering of scaffolds to resolve conflicts.
This manual approach yielded fewer bins per metagenome, which were of higher quality as determined by SCMG analyses (+@fig:fig3_binning_QC_anvio; +@fig:fig3_binning_QC_checkm; manual vs Metabat2 and Concoct).
Additionally, the specificity of the taxonomy of these bins as determined by BAT increased (+@fig:fig3_binning_QC_no_taxonomy; Manual vs Metabat2 and Concoct), indicating that the complete gene content of these bins was more like known genomes of similar taxonomy.
Manual binning and manual curation of extraneous binning signals allowed for a more parsimonious solution of the _Azolla_ genus metagenome, providing MAGs of higher quality.

Despite intensive sequencing efforts, this study does not exhaust the diversity of _Azolla_ associated microbes.
All assemblies except for _A. filiculoides_ minus_cyano contained many scaffolds near the lower abundance limit of assembly (+@fig:fig3_Azolla_genus_metagenome_order) and in concordance binning yielded many bins with only fractions of genomes (+@fig:fig3_Azfil_wild_binning +@tbl:tbl3_2).
Still, between 11 and 21 bacterial genomes were found with any _Azolla_ species analysed here (+@tbl:tbl3_4).

### microbiome vertical transmission in _Azolla_
To our knowledge, this is the first scholarly publication about the metagenome of a whole genus with a clear mechanism vertical transfer mechanism of the microbiome.
This mechanism is demonstrated for _N. azollae_, but more microbes have been seen in _Azolla_ ferns their leaf pockets and megasporocarps via electron microscopy [@Wallace1986; @Nierzwicki-Bauer1990; @Carrapico1991; @Zheng2009].
To demonstrate vertical transmission of microbes besides _N. azollae_, it may be more fitting to sequence multiple generations of plants and the reproductive organs of those generations.
However, we argue that rather indirectly, we have sequenced multiple generations of the same population of plants.
_A. filiculoides_ sequenced by @Li2018 was taken from a Ditch near the Galgenwaard football station in Utrecht, the Netherlands in 2012 (@Brouwer2014).
Several years later, in 2015, we went to the same ditch to sequence _A. filiculoides_ for Chapter \ref{foul play} [@Dijkhuizen2018].
The _Azolla_ population in this ditch does not survive the winter, and hence we reason the microbes sequenced in Chapter \ref{foul play} [@Dijkhuizen2018] have survived three generations, either through direct vertical transfer via the ferns megaspores or via re-inoculation from the surrounding environment.
Secondly, the presence of the same microbes in the thoroughly sterilised _A. filiculoides_ minus-cyano provides further indication that these microbes are endophytic and, in that way, survived the sterilisation process.
The genomes present in both 2012 and 2015 _A. filiculoides_ are most easily extracted from the binning overview of the _A. filiculoides_ 'lab' strain (+@fig:fig3_Azfil_lab_binning).
Several MAGs are clearly present in the native 'lab' strain sequencing (black), the 'wild' strain sequencing leaf pocket (blue) and whole plant (green), and finally in the 'minus-cyano' strain (yellow).
These MAGs are the 'Rhizobiaceae endophytic', 'Ralstonia 1', and 'Burkholderiales'.
Other MAGs might also be endophytic and vertically transmitted, but their abundance is lower than the detection limit in the sequencing of \ref{foul play} [@Dijkhuizen2018].

Two theories currently coexist in the literature about how _N. azollae_ enters _Azolla_ megasporocarps.
Recently, motile _N. azollae_ filaments were observed with confocal microscopy in small channels of the _Azolla_ megasporocarp indusium cap [@Zheng2009; @Ran2010].
We theorise, however, that both _N. azollae_ and other microbes may be retained in seed colonies near the shoot apical meristem (SAM) of _Azolla_ ferns, as we showed Chapter \ref{it takes two} [@Dijkhuizen2021].
Leaf and sporocarp primordia use trichomes to encapsulate _N. azollae_ from this seed colony during early development, which functions as inoculum for the forming organ. [@Campbell1893; @Nierzwicki-Bauer1989; @Perkins1993].
We prefer this mechanism supported by many electron microscopy studies for its parsimonious solution to _N. azollae_ desimination over _Azolla_ organs.
This hypothesised mechanism of microbiome transfer does not explain motile cyanobacterial filaments often observed in a channel of the megaspores' indusium caps in [@Ran2010; @Zheng2009].

Despite both sporocarps gaining _N. azollae_ colonies, microsporocarps lose the cyanobacterial symbionts while megasporocarps retain them in the form of akinete resting stages `Anna's confocal pictures in the \ref{forever together} chapter?`.
In our data, we cannot definitively prove that the three endophytic MAGs, nor any other systematically associated order of bacteria, are endophytic, vertically transferred or present at the SAM seed colony.
However, we consider it extremely likely to be so, especially supported by the metagenome data on all _A. filiculoides_ strains and the reproducible presence of bacteria in fern megasporocarps.
Sequencing the SAM and reproductive stages could provide further information on the mechanism of microbiome vertical transfer in _Azolla_.
Alternatively, FISH may pinpoint the exact location of the bacteria whose genomes were assembled here, either in the SAM, the leaves or the sporocarps.

### Azolla genus-wide metagenome
Inspired by the holobiont concept [@Zilber-Rosenberg2008] and the mechanism for vertical transfer in _Azolla_ ferns, it makes sense to study a symbiosis like _Azolla_ from the genus perspective rather than a single species.
Systematically _Azolla_ associated bacteria besides the primary symbiont are predominantly proteobacteria, mostly Alphaproteobacteria and Betaproteobacteria (fig:fig3_binning_QC_all_taxonomy; Phylum & class).
These classes have often been seen as endophytes to plants before @Frank2018.
More specifically, _Azolla_ ferns systematically harbour microbes of six taxonomical orders (+@tbl:tbl3_5; fig:fig3_binning_QC_all_taxonomy; order).
Beyond the level of order, no clear taxonomical pattern is distinguishable other than the main symbiont _N. azollae_ (fig:fig3_binning_QC_all_taxonomy; family & genus).
The Nostocales order encompasses only the main symbiont _N. azollae_ and was highly abundant in all species, contradicting theories that other cyanobacterial strains may inhibit _Azolla_ ferns at lower abundances [@Papaefthimiou2008].
The two most prominent orders, Burkholderiales and Rhizobiales, were already identified in Chapter \ref{foul play} [@Dijkhuizen2018].
However, their genomes across the entire _Azolla_ genus were not published before, nor was it clear that multiple Rhizobiales and Burkholderiales genomes are systematically associated with single species of the _Azolla_ genus.
The remaining three orders, Caulobacterales, Nevskiales and Sphingomonadales, were seen before in \ref{foul play} [@Dijkhuizen2018] (+@fig:fig2_2; +@fig:fig2_3), but not as whole genomes across the entire genus.

The new availability of all MAG sequences allows for studying the bacteria of the _Azolla_ genus through the perspective of comparative genomics.
We may now inquire, for example, if _Azolla_ associated bacteria share a common ancestor and a common introduction in the _Azolla_ genus, if their metabolism is similar, and if their genomes have adapted to the symbiotic lifestyle.
The nature of the data presented here does warrant caution on two important fronts.
First, except for the _A. filiculoides_ 'wild' sample, no judgement can be made whether the MAGs presented here belong to endophytic or epiphytic bacteria.
Second, ferns acquired from the IRRI collection were maintained for long periods in close vicinity to each other and cross contamination is a real risk.
The latter consideration is somewhat mitigated by the presence of these orders in samples acquired both from Utrecht, the Netherlands, and the IRRI collection.

The systematic presence of specific groups of bacteria suggests that ferns of the genus _Azolla_ may acquire some fitness benefit from their microbiome.
@Forni1992 theorised that _Azolla_ associated bacteria may be responsible for the mucus in which both _N. azollae_ and other microbes are harboured.
A similar mucus is found at the apical meristem colony in Chapter \ref{it takes two} [@Dijkhuizen2021].
Mining the genomes published here may indicate if the genes required for producing this mucus are present.
Systematic presence, and possible systematic vertical transmission, are no requirements to consider a microbe as a symbiont.
Alternatively, microbes may associate with _Azolla_ but live in the environment, as is the case with Rhizobiales-legume symbioses.
This would allow for a less direct inheritance of microbial symbionts, as is often the case in marine eukaryote-bacterial symbioses [@Russell2020].

...

In this manuscript, we characterise the _Azolla_ holobiont from the perspective of the entire genus rather than a single species.
This broader perspective ideally will allow us to identify parts that are persistently present in the genus or parts thereof.
With parts, we deliberately do not mean genomes or even single genomes.
Rather, we like to think of pathways which may be encoded in any set of genomes that may be relevant to the fitness of the holobiont.
The MAGs assembled and published here hopefully allow the _Azolla_ research community to study the bacteria of the genus from that broader perspective and add to it as more _Azolla_ ferns are published.
Study approaches that benefit from the whole genus perspective are, for example, phylogenetics and phylogenomics.
If any bacterial species were introduced once and retained by the host, the genomes of this one species would have persisted through host speciations.
Consequently, a phylogenetic tree of the symbiont will likely resemble that of the host species.
By the same reasoning, these bacterial genomes associated with _Azolla_ hosts will cluster together in a phylogenetic tree of a broader selection of related bacteria.
Persistent symbionts may also show signs of genome degradation as the main symbiont _N. azollae_ does.
Acknowledging that bacterial genomes are more flexible in their content and structure, we may employ the near-complete MAGs published here to study their genetic content rather than the presence or absence of a genome as a whole.
For example, we may find clusters of genes involved in symbiosis or of particular interest to _Azolla_-Rhizobiales symbiosis by pangenomics of a selection of Rhizobiales, including those associated with _Azolla_, those in symbioses with legumes, and non-symbiotic species.
Although our sample size is small, we may attempt to mine the pathways found in _Azolla_ associated bacterial genomes for genes under positive selection.
We might wonder how microbes evade the plant immune system, perhaps studying type 3 and 4 secretion systems encoded in their genomes [@DeMeyer2019; @Frank2018].

Possible study directions of the _Azolla_ genus metagenome are numerous, and the previous list of examples is not exhaustive.
We gladly share all genomes of bacteria associated with the _Azolla_ genus with the research community to study this remarkable symbiosis.

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

![Anvi'o overview of the _A. filiculoides_ 'lab' metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. filiculoides_ 'lab' sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (light green), scaffold abundance in PacBio reads from the _A. filiculoides_ 'lab' sample (yellow). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_2.](source/figures/fig3_Azfil_lab_binning.pdf){#fig:fig3_Azfil_lab_binning}

![Anvi'o overview of the _A. filiculoides_ 'minus-cyano' metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. filiculoides_ 'minus-cyano' sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (light green), scaffold abundance in PacBio reads from the _A. filiculoides_ 'lab' sample (yellow). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_all_MAGs.](source/figures/fig3_Azfil_minus_cyano_binning.pdf){#fig:fig3_Azfil_minus_cyano_binning}

![Anvi'o overview of the _A. rubra_ metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles but not differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. rubra_ sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (green). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_all_MAGs.](source/figures/fig3_Azrub_binning.pdf ){#fig:fig3_Azrub_binning}

![Anvi'o overview of the _A. mexicana_ metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. mexicana_ sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (green). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_all_MAGs.](source/figures/fig3_Azmex_binning.pdf ){#fig:fig3_Azmex_binning}

![Anvi'o overview of the _A. nilotica_ metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles but not differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. nilotica_ sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (green). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_all_MAGs.](source/figures/fig3_Aznil_binning.pdf ){#fig:fig3_Aznil_binning}

![Anvi'o overview of the _A. carolinana_ '1' metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles but not differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. carolinana_ '1' sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (green). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_all_MAGs.](source/figures/fig3_Azcar_1_binning.pdf ){#fig:fig3_Azcar_1_binning}

![Anvi'o overview of the _A. carolinana_ '2' metagenome assembly and binning into MAGs. The center dendrogram reflects a hierarchical clustering of scaffolds based on 4-mer profiles and differential abundance in biological samples. In the dendrogram, each leaf is one scaffold (or split in Anvi'o). In circles around the dendrogram, metadata about the scaffolds is displayed. This metadata is, in order of inside to outside: split-parent, scaffold length, scaffold GC content (dark green), scaffold abundance in _A. carolinana_ '2' sequencing (black), scaffold abundance in leaf cavity enriched samples (blue), scaffold abundance in whole plant samples (green). Then follow several coloured rings representing taxonomy as determined by CAT, starting at the kingdom level down to species level. The before last red ring indicates presence of any ribosomal RNA genes in a scaffold (drastically influencing depth of the scaffold and therefore the binning process). The final ring indicates in which bin a scaffold was categorises. The corresponding bins, their size and estimated completeness are shown in +@tbl:tbl3_all_MAGs.](source/figures/fig3_Azcar_2_binning.pdf ){#fig:fig3_Azcar_2_binning}


![Binning quality control in CheckM [@Parks2015] of various binning methods. Quality of bins was assessed as completeness (dark green) and redundancy (red) by ways of scoring SCMGs. Bin quality was assessed for all bins of all metagenome assemblies, comparing two automated binning methods (Metabat2 and Concoct) and the manual method described here (Manual). Numbers in the panels show the total amount of bins created by a particular method for a particular assembly (black) and the amount of those bins passing QC criteria of completeness above 90% and redudancy below 10% (Dark green). These thresholds are also indicated by grey lines in the figure.](source/figures/fig3_binning_QC_anvio.pdf ){#fig:fig3_binning_QC_checkm}

\nolinenumbers
