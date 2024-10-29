\pagestyle{chapter}
\singlespacing
\setlength{\parindent}{0.0in}
\addthumb{Chapter \thechapter}{\Large{\thechapter}}{white}{gray}

<!-- \chapter{It takes two: Far-Red light induces the \emph{Azolla filiculoides} symbiosis sexual reproduction; triggering symbiont \emph{Nostoc azollae} transporters and \emph{A. filiculoides} GAMYB and MIKCc transcription factors.} -->
\chapter{It takes two: Far-Red light induces the \emph{Azolla}-\emph{Nostoc} symbiosis sexual reproduction.}
\label{it_takes_two}

\footnotesize

Laura W Dijkhuizen^1^
Henriette Schluepmann^1^
Badraldin Ebrahim Sayed Tabatabaei^2^
Paul Brouwer^1^
Niels Rijken^1^
Valerie A. Buijs^1^
Erbil Güngör^1^
Henriette Schluepmann^1^

\scriptsize
1. Laboratory of Molecular Plant Physiology, Department of Biology, Utrecht University, Utrecht, The Netherlands
2. Department of Biotechnology, College of Agriculture, Isfahan University of Technology, Isfahan, 84156-83111, Iran

\newpage
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

<!-- have a mini table of contents -->
\minitoc

\section*{Abstract}

Water ferns of the genus _Azolla_ and the filamentous cyanobacteria _Nostoc azollae_ constitute a model symbiosis that enabled colonization of the water surface with traits highly desirable for development of more sustainable crops: their floating mats capture CO~2~ and fix N~2~ at high rates using light energy.
Their mode of sexual reproduction is heterosporous.
Regulation of the transition from vegetative to spore-forming phases in ferns is largely unknown, yet a pre-requisite for Azolla domestication, and of particular interest since ferns represent the sister lineage of seed plants.

_A. filiculoides_ fern sporocarp formation required far-red light (FR), was increased by fern density, and inhibited by nitrogen in the medium.
Sporocarps induced with FR could be crossed to verify species attribution of strains from the Netherlands but not from the Iranian Anzali lagoon; the latter strain was assigned to a novel species cluster from South America.
Red-dominated light suppresses the formation of dissemination stages in both gametophyte and sporophyte-dominated lineages of plants, the response likely is a convergent ecological strategy to open fields.

FR-responsive transcripts included MIKCC homologues of CMADS1 and miR319-controlled GAMYB transcription factors in the fern, transporters in _N. azollae_, and ycf2 in chloroplasts.
Loci of conserved miRNA in the fern lineage included miR172, yet FR only induced miR529 and miR535, and reduced miR319 and miR159.
Phylogenomic analyses of MIKCC transcription factors suggested that control of flowering and flower organ specification may have originated from the diploid to haploid phase transition in the homosporous common ancestor of ferns and seed plants.

\newpage

# Introduction

Ferns from the genus _Azolla_ thrive floating on freshwater.
They require no nitrogen whilst growing even at the highest rates due to an unusual symbiosis with the cyanobacterium _Nostoc azollae_, which fixes dinitrogen using light energy [@Brouwer2017c].
They are a model plant symbiosis allowing to study important traits: for example, highly efficient N~2~ fixation imparted by a microbial consortium, building of substrate mats capable of massive CO~2~ draw-down [@Speelman2009], and adaptations to the aquatic floating lifestyle in flood-prone regions.
Previously used as biofertilizer, they now are considered a candidate crop for sustainable high-yield production of plant protein in subsiding delta regions but have never been domesticated [@Brouwer2017c; @Brouwer2018].
What controls their sexual reproduction is completely unknown yet central to containment, propagation, breeding schemes or the establishment of biodiversity and germplasm banks.
Insight into the mechanisms controlling sexual reproduction in ferns is of particular interest as it will further uncover how these mechanisms evolved from a common homosporous ancestor because ferns and seed plants are from sister lineages.

_Azolla_ spp. (hereafter Azolla) are heterosporous with diploid sporophytes generating two types of sori, mostly called sporocarps [@Nagalingum2006; @Coulter1910].
Unlike homosporous ferns, the haploid phase of Azolla, the gametophytes, are not free-living but contained inside the sporocarps.
Unlike seed plants, gametophytes do not develop inside the sporocarps when these are still on the sporophytes.
Therefore, fertilization is not guided by structures on the sporophyte such as flowers in angiosperms.
Azolla sporocarps typically detach when mature and sink to the sediment of ditches; they constitute resting stages with nutrient reserves that survive drying or freezing and, thus, are key for dissemination practices [@Brouwer2014].

The developmental transition to sexual reproduction of the Azolla sporophyte begins when shoot apices of the sporophytes will form initials for sporocarps (IS) in addition to branches, leaves and roots.
It marks the beginning of sexual reproduction in Azolla.
In homosporous ferns, IS corresponds to the onset of sori-formation, the control of which is not well studied; sori formation occurs mostly on leaves but fern leaves have indeterminate apical meristems as branches do [@Cruz2020].
In angiosperms, IS may be homologous to the transition of shoot apical meristems (SAM) to flower meristems (IF): the meristem is switching to making branches with leaves and structures containing the sporangia, the “sporocarps”, whereby the making of sporocarps is ancestral to the making of leaves [@Vasco2016].
Gene expression in lycophytes and ferns of Class III HD-Zip transcription factors (C3HDZ) was observed in both leaves and sporangia even though ferns and lycophyte fossil records have shown that the lineages evolved leaves independently.
@Vasco2016, therefore, suggested that the common C3HDZ role in sporangium development was co-opted for leaf development when leaf forms, the micro and megaphylls, evolved in lycophytes and ferns, respectively.

In the SAM transition to IF of the model angiosperm Arabidopsis thaliana (Arabidopsis), the LEAFY transcription factor (TF) complex induces floral homeotic genes [@Sayou2016].
LEAFY is conserved in plant lineages, but LEAFY does not promote formation of reproductive structures in seed-free plants including ferns where, nonetheless, the protein was reported to maintain apical stem cell activity [@Plackett2018].
The pattern emerging, therefore, is that the LEAFY complex is not among those that were already in place to link exogenous cues to the transition of SAM to IS in the common ancestor of seed plants and ferns.

In many angiosperms, MADS-box TF of MIKCC-type form complexes that integrate endogenous and exogenous cues turning SAM into IF [@Theißen2018].
In Arabidopsis, for example, gibberellic acid (GA)-dependent and photoperiod/temperature signaling is integrated by MIKCC from the FLC and SVP clades that, as predicted by @Vasco2016, are floral repressors.
Consistent with separate transitions for inflorescence and flower meristems in Arabidopsis, the MIKCC floral integrators act on another,  SUPPRESSOR OF CONSTANS 1 (AtSOC1), that in turn induces the expression of MIKCC floral homeotic genes.
Homeotic genes of potential relevance for ferns specify ovules, and stamens: these modules could be more ancient than those specifying carpels and sepals.
Specification of ovules/stamens in angiosperms, however, is unlikely homologous to that of mega- and microsporocarps in Azolla because heterospory evolved independently in ferns and angiosperms [@Sessa2016].

![Shoot apices of _A. filiculoides_ sporophytes contain the apical _N. azollae_ colony, trichomes and sporocarp initials. (A), Shoot apex with apical _N. azollae_ colony  (ac). Outer leaves were removed for better visualization of developing leaf lobes (l), leaf cavities (lc) and bacteria filaments. (B), the same shoot apex as in (A) with trichomes (t) revealed by transmitting light absorption surrounded by the apical colony and in areas destined to form leaf cavities (lc); Bar: 50 mm. (C), _N. azollae_ hormogonia (h) invading the sporocarp initials (si). Sporophytes were stained with propidium iodide [@Truernit2008], then fluorescence detected using 405 nm activation beam, and emission <560 nm filter for the yellow channel and 505-530 nm for the blue channel with the Confocal Laser Scanning microscope Zeiss LSM5 Pascal.](source/figures/fig6_1.png){#fig:fig6_1 height=80% short-caption="Shoot apices trichomes and sporocarps harbouring Nostoc azollae colonies"}

In addition to MIKCC TF, micro RNA (miR) are known to control phase transitions in angiosperms, including IF.
The miR156/172 age pathway controls flowering: miRNA156 decreases with the age of plants, and thus also its repression of the targets SQUAMOSA PROMOTER BINDING-LIKES (SPL).
In the annual Arabidopsis, SPL promote expression of mir172 that targets another type of floral repressor, the AP2/TOE TF [@Hyun2019].
In the perennial Arabis alpina, the MIKCC FLC homologue and miR156 regulate expression of SPL15 thus integrating temperature and age-dependent IF.
Moreover, AP2/TOE and NIN TF are known to mediate repression of AtSOC1 in Arabidopsis on high nitrate [@Gras2018; @Olas2019].
The MIKCC SOC1 is further known to control levels of miR319 that inhibits TCP protein functions in the FT-FD complex mediating photoperiod control of IF [@Lucero2017 ; @Li2019].
Inextricably, therefore, transition to IF is linked to conserved miRNA modules in angiosperms but we know little of miRNA loci in ferns [@Berruezo2017 ; @You2017].
Systematic research of the symbiosis transition to IS in Azolla is lacking: GA applications did not induce IS, neither did stress treatment [@Kar2002].
Moreover, fern host and symbiont development are tightly coordinated during the induction of sporocarps: mobile filaments of _N. azollae_ generated in the shoot apical colony move into the developing sporocarp initials in the shoot apex (+@fig:fig6_1).
The host SAM developmental transition, therefore, may be influenced by activities of the _N. azollae_ apical colony residing at the SAM (+@fig:fig6_1\-A).
Alternatively, _N. azollae_ development may be controlled by secretions from specialized host trichomes in the SAM, the developing leaf and sporocarp initials [@Cohen2002; @Perkins1993] (+@fig:fig6_1\-B-C ).
We expect elaborate communication given that both genomes co-evolved and that _N. azollae_ is an obligate symbiont with an eroded genome [@Ran2010 ; @Dijkhuizen2018 ; @Li2018 ].
Transition to IS will, therefore, best characterized by profiling expression of the fern host and the symbiont simultaneously; this requires simultaneous profiling of eukaryote and prokaryote RNA (dual RNA sequencing) and has not been established for cyanobacterial symbioses before.
Here we identify external cues that induce or inhibit transition to IS in _A. filiculoides_ under laboratory settings.
We test the viability of reproductive structures induced in different fern accessions by crosses, define species attributions and support the results obtained with phylogenetic analyses of the accessions.
To reveal endogenous mechanisms mediating transition to IS, we profile transcript accumulation by dual RNA-sequencing comparing sporophytes grown with and without far-red light, at a time point when the reproductive structures are not yet visible.
We assign induced MIKCC and MYB TF to known clades using phylogenetic analyses.
In addition, we profile small RNA from the symbiosis, then identify miRNA and their targets in the fern lineage.
Finally, we discover regulatory modules of conserved miRNA/targets involved during induction of IS in ferns.

# Materials and methods

## Plant Materials, growth conditions and crosses

Ferns were collected from differing locations in the Netherlands, grown in liquid medium at a constant temperature of 22oC under long days (16h light) as described earlier [@Brouwer2017c].
Ferns from Spain and Iran were processed to DNA on site.
GPS coordinates from the collection sites of the strains used in phylogenetic analyses are in Supplementary Table S1.
For sporocarp induction, ferns were first raised under 16 h tube light (TL) periods, then transferred for induction under 16 h TL with far-red Light Emitting Diodes - LED (Phillips GrowLED peaking at 735 nm, Supplementary Figure S1A-B).
Photosynthetic Photon Flux Density varied in the range 100-120 μmol m−2 s−1.
Sporophytes were generally kept at densities that covered the surface as this inhibits growth of cyanobacteria and algae.
When testing sporocarp induction sporophytes were kept at set densities (with fresh weight resets once per week, Supplementary Figure 1C-E) and set red to far-red light ratios (Supplementary Table S2).
Phenotypic change in mature sporophytes were photographed using a Nikon D300s with an AF Micro-Nikkor 60mm f/2.8D objective or bellows on a rail to generate image reconstructions with Helicon focus software.
Megasporocarps were collected manually using tweezers, so were microsporocarps.
To initiate crosses microsporocarps were Dounce-homogenized and massulae thus released added to megasporocarps in distilled water (3-6 ml, in 3 cm diameter petri dish), shaking so as to obtain clumps.
The crosses were kept at room temperature (about 18oC) under 16 h light conditions under TL at about 100 μmol m−2 s−1.
As sporelings emerged they were transferred to liquid medium [@Brouwer2014].

## RNA extraction from sporophytes and quantitative RT-PCR

RNA was extracted, DNAse treated then reverse transcribed [@Brouwer2014].
Primers for qRT‐PCR were for the references AfTUBULIN (AfTUBF: CCTCCGAAAACTCTCCTTCC; AfTUBR: GGGGGTGATCTAGCCAAAGT) and AfADENINE PHOSPHORIBOSYLTRANSFERASE (AfAPTF: TAGAGATGCATGTGGGTGCAGT; AfAPTR: AAAAGCGGTTTACCACCCAGTT), and for AfSOC1 (AfSOCF: ATGGGATCGTAAGGCTTCAAAA; AfSOCR: AGCAGAGCACACAGGTCTCAAC).
qRTPCR amplifications were from RNA of three biological replicate growth tubs, significance was assessed by t‐test with P < 0.05.

## Phylogenetic analyses

Chloroplastic marker regions.
DNA was extracted using the extraction kit (EZNA SP Plant DNA), PCR amplifications were using pfu and taq polymerase mixed (1:4 Units) with pfu-bufffer containing MgSO4 (2 mM) and taq-cycling conditions (37 cycles of 30 s 94oC denaturation, 30 s 50-58oC annealing, 1 min 72oC amplification, then 5 min 72 oC) and using primers trnG1F (GCGGGTATGGTTTAGTGGTAA), trnR22R (CTATCCATTAGACGATGGACG), trnLC (CGGAATGGTAGACGCTACG) and trnLF (ACTTGAACTGGTGACACGAG).
Amplicons were purified (EZNA Cycle pure kit) then submitted for sequencing (Macrogen).
Sequences were reconstructed then added to a fasta file containing the cognate sequences from Azolla species sequenced previously [@Madeira2016a; @Dijkhuizen2018].
Sequences were aligned on MEGA 7 [@Kumar2016] using Clustal W [@Thompson1994].
Gap opening and gap extension of 10 and 3, respectively, were used for trnL-trnF and 10 and 4, respectively, were used for trnG-trnR.
Maximum likelihood phylogenetic trees were calculated with alignment lengths of 902 bp and 852 bp for trnL-trnF and trnG-trnR, respectively.
The trnL-trnF tree was constructed using the Tamura 3-parameter plus Gamma (T92 + I) model and the trnG-trnR tree using the Tamura 3-parameter plus Invariant (T92 + I) model.
The gaps/missing data treatment was chosen as “partial deletion”, branch swap filter as “very weak” and ML Heuristic method as “Subtree-Pruning-Regrafting - Extensive (SPR level 5)”.
The reliability of branches was analyzed by using bootstrapping of 1000 replicates; trees obtained were visualized with iTOL [@Letunic2019].

## Sequence logo of ITS1 intergenic regions.

The logo from the _A. filiculoides_ ITS was generated using WebLogo3 [@Crooks2004] after extracting 516 sequences from the Azfi vs 1 genome with in silico PCR [@Slater2005] and the published reference sequence for _A. filiculoides_ [@Li2018].
ITS1 sequences other Azolla species [@Dijkhuizen2018] were extracted by alignment to the _A. filiculoides_ reference sequence, and the Bam file obtained then used to generate the sequence logos of ITS regions from other Azolla including _A. nilotica_ (section Rhizosperma), and _A. caroliniana_1, _A.caroliniana 2_, _A. mexicana_, _A. microphylla_, _A. rubra_ (section Azolla).
MIKCC and R2R3MYB phylogenetic trees.

## MIKCC and R2R3MYB phylogenetic tree.

The automatically generated annotation of Azfi vs1 was first corrected in IGV using reads from the dual RNAsequencing experiment.
Azolla fern sequences were then merged to those extracted from the genome browsers of each species and aligned with MAFFT L-INS-I or E-INS-I [@Katoh2019], then trimmed with trimAL [@Capella-Gutierrez2009].
Phylogenetic inferences were computed with IQTREE [@Nguyen2015] and its internal model fitter [@Trifinopoulos2016].
In case of the MIKCC, the phylogeny obtained with MAFFT E-INS-I was used without trimming as draft phylogeny to guide alignment optimization with PRANK (@Loytynoja2014); the resulting optimized alignment was then trimmed with trimAl and used for inference of the final phylogeny with IQTREE.
The resulting maximum likelihood (ML) trees were visualized in iTOL [@Letunic2019] with minimum bootstrap support of 50% and sequences color‐coded based on their clade assignment (R2R3MYB) or on phylogenetic placement (MIKCC).

## Reference genomes used to determine gene counts from the Dual RNA sequencing reads

Assembly and annotation of the _A. filiculoides_ accession Galgenwaard chloroplast and nuclear genomes were from [@Li2018]; the strain used was devoid of  _N. azollae_ and described previously [@Brouwer2017c].
Since _A. filiculoides_ species attribution was not entirely reliable, we first had to determine how different the genomes of _N. azollae_ are within the Azolla genus and then determine what reference genome could be used for the _N. azollae_ inside the accession Galgenwaard.
Metagenome Assembled Genomes (MAGs) from _N. azollae_ in the Azolla species _A. nilotica_, _A. mexicana_, _A. microphylla_, _A. caroliniana_1, _A. caroliniana_2, A_. rubra_ and _A. filiculoides_ Galgenwaard strains were computed using the shotgun sequencing data of the accessions in [@Dijkhuizen2018].
Reads were trimmed and quality assessed, then filtered (BWA aligner, [@Li2009a]) against the fern and chloroplast genomes then assembled into contiguous sequences (contigs) using SPAdes in metagenome mode [@Nurk2017], and contigs assigned Streptophyta taxonomy with CAT [@VonMeijenfeldt2019] added to the nucleus and chloroplast filter for another round of read filtering.
Reads obtained were then assembled with SPAdes again, then contigs binned according to k-mer, GC and vertical coverage of the reads on the contigs.
Bins were further interactively polished in Anvi’o [@Eren2015]; the MAG sequence data is under the accession PRJEB45214.
Average Nucleotide Identity (ANI) was calculated with the dRep implementation of nucmer using the ANImf preset [@Kurtz2004; @Olm2017].
MAGs were highly complete, and ANI above 99% with _N. azollae_ 708 from the _A. filiculoides_ accession Stockholm (GCF_000196515.1), we therefore aligned reads and then derived read counts for features encoded in this genome.

## Dual-RNA sequencing and data processing

_A. filiculoides_ sporophytes were from the sequenced accession Galgenwaard [@Li2018].
The ferns were maintained on liquid medium without nitrogen in long-day TL, then transferred to TL with and without far-red LED for 7 days, on fresh liquid medium without nitrogen; harvest was 2 h into the light period by snap freezing.
All samples were grown separately and harvested as triplicate biological replicates.
Total RNA was extracted using the Spectrum Plant Total RNA (Sigma-Aldrich) using protocol B, then DNAse treated as described in [@Brouwer2017c], and cleaned using the RNeasy MinElute Cleanup Kit (Qiagen).
rRNA depletions were carried out as per protocol using Ribo-Zero rRNA Removal Kit (Plant Leaf, Illumina), and the RNA was then cleaned again using the RNeasy MinElute Cleanup Kit.
Stranded libraries were then synthesized using the Ovation Complete Prokaryotic RNA-Seq Library Systems kit (Nugen).
The libraries thus obtained were characterized and quantified before sequencing using a single lane Hiseq4000 and 50 cycles PE reading (Illumina).

Reads obtained were de-multiplexed then trimmed and quality filtered with trimmomatic [@Bolger2014], yielding 13-60 million quality PE reads per sample; the data is under the accession number PRJEB45223.
Alignment of the reads to the genome assembly and GFF vs1 of _A. filiculoides_ [Azfi_vs1\; @Li2018] was with STAR-aligner default settings [@Dobin2013] and was combined with the STAR read count feature (PE read counts corresponding to the HTseq “Union” settings, [@Anders2015].
Read count tables were fed into DESeq2 [@Love2014] for analysis of differentially accumulating transcripts.
STAR was also used to align reads to the _N. azollae_ and the chloroplast genomes, and read counts then extracted using STAR default parameters or VERSE [@Zhu2016] with HTSeq setting “Union” comparing single and paired End read counts on the polycistronic RNA.
The three approaches yielded similarly ranked genes but the Padj statistics of differential expression in count tables from the forced single read counts were poor: only 20 _N. azollae_ genes had P- adjusted values smaller than 0.1 compared to up to 67 with the PE- approaches, we therefore present the PE-approach using STAR read counts only.
STAR alignment to concatenated genomes of the _A. filiculoides_ symbiosis using default settings yielded a large proportion of multi-mappers which interfered with PE read counting leading to losses of as much as 30% of the reads.
The strategy would reduce force mapping but is not necessary to extract differentially accumulating transcripts.
In contrast, when mapping the sRNA reads below, we used alignments (allowing no mismatches) to concatenated genomes, and then recovered reads aligning to each genome using Samtools fasta from the indexed .bam files with alignment data of the concatenated genomes.

## Small RNA data sequencing and data processing

Ferns were maintained on liquid medium without nitrogen with 16 h TL, then transferred to TL with and without far-red LED for 7 days as described under Dual-RNA sequencing.
In addition, sporophytes were grown on medium with or without 2 mM NH4NO3; ferns without cyanobacteria [@Brouwer2017c] were grown on medium with 2 mM NH4NO3 in TL with far-red LED.
All sporophytes were harvested 7 d into the treatment, 2 h into the light period and snap frozen.
Samples were harvested from triplicate growth experiments and thus represent triplicate biological replicates.
Small RNA was extracted as per protocol using the mirPremier microRNA Isolation Kit (Sigma-Aldrich), then DNAse treated [@Brouwer2017c], then cleaned using the RNeasy MinElute Cleanup Kit (Qiagen) protocol for small RNA.
Libraries of the sRNA were then generated using the SeqMatic TailorMix miRNA Sample Preparation 12-reaction Kit (Version 2) as per protocol.
Libraries were characterized using an Agilent Technologies 2100 Bioanalyzer and quantified before sequencing using NextSeq500 and 1 x 75 b read chemistry (Illumina).

Reads thus obtained were de-multiplexed, trimmed and quality filtered with trimmomatic (the data is under the accession number PRJEB45223), then aligned with STAR [@Dobin2013] (set at maximal stringency and to output Bam files) to the concatenated fasta files of the genomes Azfi_vs1, its chloroplast, and _N. azollae_ 0708.
The resulting bam files were then split for each genome, and Samtools fasta [@Li2009] used to extract reads aligning to each genome.
fastx collapser (http://hannonlab.cshl.edu/fastx_toolkit) was then used to extract read counts for each identical sequence, with the sequence defining the name in the lists obtained.
A data matrix was generated in bash, then exported to Excel or Rstudio for further analyses.

To determine differential expression, the lists obtained were restricted to sRNA with at least 10 reads per sample joined in bash, and the tables thus obtained, first restricted to containing only reads of 20-22 nt sRNA (to minimize gel excision bias during sequencing library preparation), then exported to R [@Rcoreteam2013].
DESeq2 was then used to display variation and dispersion in the data and identify differentially accumulating sRNA using Padj values [@Love2014].

## miRNA discovery

The miRNA loci in _A. filiculoides_ were analyzed as in Supplementary Figure S2.
Pre-miRNA were predicted with miRDEEP-P2 [@Kuang2019]; multi-mappers min.
100 and max. loop length 500) then extracted and subjected to secondary structure prediction using RandFold default parameters [@Bonnet2004; @Gruber2008].
miRNA candidates containing less than four mismatches within the hairpin structure were viewed in IGV along with RNA expression data aligned to Azfi_vs1.
Predicted miRNAs that were expressed in _A. filiculoides_ were then compared in miRbase [@Kozomara2019].
Prediction of miRNA targets in Azfi_vs1 was using the intersect of both psRNATarget [@Dai2018] and TargetFinder [@Srivastava2014] with a cutoff of 5.0.
Predicted targets were linked to the closest homolog using the Mercator annotation [@Lohse2014] of Azfi_vs1 predicted proteins.

# Results

## Far-red light and canopy density induce, while nitrogen in the medium represses, the transition to sexual reproduction in _A. filiculoides_

A young fern growing at low density typically spreads over the water surface (+@fig:fig6_2\-A).
In contrast, a fern that underwent transition to reproductive development in dense canopies formed a three dimensional web characteristic of Azolla mats (+@fig:fig6_2\-B).
Unlike in the glasshouse, _A. filiculoides_ ferns never sporulated under tube light (TL, Supplementary Figure S1A); TL did not emit any photons in the far-red range (FR, Supplementary Figure S1A).
We, therefore, added FR during the entire 16 h light period (FR, Supplementary Figure S1B).
This initially resulted in the elongation of the stem internodes of the fern (+@fig:fig6_2\-C) and, after 2-3 weeks, in the formation of the sporocarps (+@fig:fig6_2\-D).
Sporocarps were positioned as pairs on the branch side of branch points and were predominantly arranged as a mega- and microsporocarp pair (+@fig:fig6_2\-E).

![Far-red light and nitrogen affect the reproductive phase transition in _A. filiculoides_. (A), vegetatively growing ferns. (B), ferns in the reproductive phase with micro (mi) and megaspores (me). (C), growth habit under TL and TL with far-red LED (FR). (D), a mature sporophyte and (E) its schematic representation: a root is formed at each branch point, and sporocarp pairs are found close-by on the branch side of the branch point but not at all branch points. F, sporulation frequencies at increasing plant density (41.7, 128.8 and 208.3 g m-2 dry weight) and with increasing red to far-red light ratios (FR0-FR4). The red to far-red ratios were 19.13 (FR0), 1.16 (FR1), 0.63 (FR2), 0.50 (FR3) and 0.31 (FR4); to obtain the FR4 ratio, the TL intensity was halved. Each data point represents the average of three independent continuous growth replicates. G, induction of sporulation without nitrogen (-N) or with 2 mM NH4NO3 (+N) in the medium, data are averages from three replicates with standard deviations.](source/figures/fig6_2.png){#fig:fig6_2 short-caption="FR light and nitrogen affect the Azolla reproductive phase transition"}

To test the optimum light quality for sporocarp induction, decreasing ratios of red to FR were applied to sporophytes first raised in TL light.
To test canopy density, light quality was also tested on sporophytes maintained at three differing densities (Supplementary Table S2, Supplementary Figure S1C-E).
FR was required for sporocarp formation regardless of the density of the fern culture (+@fig:fig6_2\-F).
Increasing FR whilst keeping a constant photosynthetic active radiation (PAR) yielded more sporocarps per fern mass.
The sporocarps per fern mass increased with time of exposure to the FR up until five weeks and then decreased, presumably because ripe sporocarps detached.
The sporocarps per fern mass, furthermore, increased with the density of the fern culture.
Reducing the PAR at highest FR intensity (+@fig:fig6_2\-F, FR4) revealed that PAR-intensity limits the production sporocarps at high FR.

Adding 2 mM ammonium nitrate to the medium drastically reduced the spore count when inducing sporocarp formation with FR (+@fig:fig6_2\-G).
Both ammonium and nitrate added individually inhibited sporocarp formation (data not shown); this inhibition explained why sporophytes without _N. azollae_ kept on various nitrogen sources never sporulated.

The ratio of mega- to microsporocarp was approximately equal over nine weeks of induction with FR (Supplementary Figure S1F).
Additionally, the marker SOC1-like from _A. filiculoides_ [@Brouwer2014], was maximally induced when sporocarps became visible four weeks after FR induction started (Supplementary Figure S1G).

| Megaspores: Massulae   | Galgenwaard | Krommerijn | Hoogwoud | Gran Canaria | Den Bosch | Nijmegen | Nieuwebrug | Groningen |
| ---------------------- | ----------- | ---------- | -------- | ------------ | --------- | -------- | ---------- | --------- |
| Galgenwaard            | \>1000      | 17         |          | 1            |           | 13       |            | 2         |
| Krommerijn             | 1           |            |          |              | 16        |          | 2          |           |
| Hoogwoud               |             |            | 20       |              |           |          |            | 2         |
| Gran Canaria[^crosses] | 17          |            |          |              | \>40      | 1        |            |           |
| Den Bosch              |             | 9          |          | 1            |           |          |            |           |
| Nijmegen               |             | 12         |          | 33           |           |          | 2          |           |
| Nieuwebrug             |             | 6          | 3        |              |           | 22       |            |           |
| Groningen              |             |            | 1        |              |           |          | 5          |           |

Table: Sporeling counts obtained from random crosses of _A. filiculoides_ strains collected in the Netherlands and Spain (Gran Canaria). {#tbl:tbl6_crosses}

[^crosses]: crosses involving megaspores from the Gran Canaria strain reproducibly germinated late, generally after 5 weeks instead of 2-3 weeks.

## FR-induced sporocarps are viable which permits crossing for breeding
 We next wondered whether the sporocarps induced with FR were viable.
We grew the following strains of _A. filiculoides_ under far-red-light: _A. filiculoides_ Galgenwaard [@Li2018], six further accessions from the Netherlands, one from Gran Canaria (Spain) and another from the Anzali lagoon (Iran) (Supplementary Table S1).
All accessions could be induced to sporulate under FR, except Anzali.
Crosses of sporocarps obtained from within the Galgenwaard strain yielded viable and fertile offspring, so did crosses of sporocarps from the Hoogwoud accession (Table 1), suggesting that FR-induced sporocarps were generally viable.
All sporulating accessions tested in crosses could be crossed, suggesting that the ferns from the Netherlands and Spain were _A. filiculoides_ (Table 1).
We were unable to induce sporulation in sporophytes from the Anzali lagoon, which had been reported as _A. filiculoides_, and therefore considered whether behavior under far-red light and crosses predict phylogenetic attributions.

## Phylogeny-derived species attributions are consistent with those obtained from crosses and reveal that Anzali ferns were not _A. filiculoides_

To research the taxonomy of the accessions, intergenic regions of the chloroplast rRNA, used for phylogenetic studies previously [@Madeira2016a], were amplified and sequenced to compute phylogenetic relations.
The regions trnL-trnF (+@fig:fig6_3\-A), and trnG-trnR  (+@fig:fig6_3\-B) yielded similar trees confirming the close relationship of the _A. filiculoides_ accessions from the Netherlands and Spain.
The trees further revealed that the Anzali accession clustered along with two accessions from South America that do not cluster within the _A. caroliniana_ group (Southern Brazil and Uruguay, Supplementary Table S1).
Use of the nuclear ITS region for phylogeny reconstruction proved futile when amplifying the region on the _A. filiculoides_ genome in silico: the _A. filiculoides_ genome assembly contained over 500 copies of the ITS sequence, and the copies of ITS were variable within the same genome (+@fig:fig6_3\-C).
Variations within any one genome were furthermore large when comparing variations between genomes of Azolla species (Supplementary Figure S3A).

The dorsal side of the upper leaf lobes of the Anzali accession has two-celled, distinctly pointed, papillae unlike _A. filiculoides_ that mostly, but not exclusively, have single-celled and rounded papillae (Supplementary Figure S3B).
Consistent with its differing response to FR, and its phylogenetic position based on the chloroplast sequences, the Anzali accession, we conclude, is not _A. filiculoides_.

![Chloroplast marker regions in strains from the Netherlands, Spain and Iran, and the rRNA intergenic regions of the _A. filiculoides_ genome. (A), Phylogenetic tree of chloroplast regions trnL-trnF. The maximum likelihood trees were bootstrapped 1000x. All bootstrap values >0.70 are displayed. In bold: sequences from accessions in this study labelled after their collection site and sequences from the differing species extracted from genome shot-gun sequencing [@Li2018]. In regular type: sequences from the @Madeira2016a study. (B), Phylogenetic tree of chloroplast regions trnG-trnR. (C), Sequence logo of all ITS1 gene regions in the _A. filiculoides_ genome [@Li2018]. The gene regions were extracted and aligned (MEGA 7) then used for in-silico PCR. Results were visualized using WebLogo [vs 2.8.2\; @Crooks2004]: at each position of the ITS, the height of the stack indicates the sequence conservation, while the height of symbols within the stack indicates the relative frequency of each base.](source/figures/fig6_3.png){#fig:fig6_3 short-caption="Diversity of Azolla strains in the Netherlands compared to strains from Iran and Spain"}

## Dual RNA sequencing by rRNA depletion profiles RNA from organelle, prokaryotic symbiont and fern nucleus
 We next wondered which molecular processes are altered during the symbiosis transition to IS.
Ferns maintained on TL were transferred to TL with and without FR for a week in triplicate cultures, then collected 2 h into the 16 h light period and snap frozen.
Total RNA was then extracted, its plant rRNA depleted, and stranded sequencing libraries generated which were depleted for rRNA from gram-negative bacteria.
Libraries were sequenced to obtain 12 to 60 million paired-end (PE) 50 b long reads, quality filtered and trimmed.
To align the reads obtained, nuclear and chloroplast genomes with annotations for the _A. filiculoides_ Galgenwaard accession were available [@Li2018].
In contrast, the genome of its _N. azollae_ symbiont was not available since the long-read sequencing of the _A. filiculoides_ Galgenwaard reference was done with the strain devoid of cyanobacteria [@Li2018].
In addition, we learnt from above that species attributions can be misleading.
We, therefore, decided to first determine how variable the genomes of the _N. azollae_ are within the _A. filiculoides_ species and the Azolla genus.
The _N. azollae_ Galgenwaard genomes were assembled both from _A. filiculoides_ kept in the laboratory [_A. filiculoides_ lab\; @Li2018], taken from the original sampling location [_A. filiculoides_ wild\; @Dijkhuizen2018] and other Azolla species [@Dijkhuizen2018].
Assemblies were from short-reads of the entire symbiosis metagenome (MAGs); they were fragmented but highly complete: over 95% complete based on single copy marker genes.
Moreover, all contigs of _N. azollae_ from the Utrecht _A. filiculoides_ aligned to the _N. azollae_ 0708 reference from _A. filiculoides_ Stockholm [@Ran2010] and were well over 99.5% identical to each other (+@fig:fig6_4\-A).
This degree of nucleotide identity was well above the maximum mismatch of the STAR-aligner’s default setting which meant that reads could be aligned to the reference taking the NCBI-defined features to derive read-counts for each feature: there we argue are superior to the automated annotation by Prokka [@Seemann2014].
The PE reads obtained from sequencing libraries made from rRNA-depleted RNA were thus aligned to the Galgenwaard accession nuclear and chloroplast genomes, and the _N. azollae_ 0708 genome, and read counts derived from their GFF annotation files.
Alignments revealed a high proportion of uniquely mapped reads to the fern nuclear and _N. azollae_ genomes suggesting efficient removal of rRNA (+@fig:fig6_4\-B).
For the chloroplast, the larger proportion of PE reads mapping to multiple loci in the chloroplast was mostly due to the genes in the repeat with a minor contribution of reads from chloroplast 23S rRNA sequence making up no more than 0.35 % of the reads in the six samples.
Read counts for the few chloroplast genes were generally high (84 without rRNA and tRNA genes).
Read counts in genome features further revealed that sense alignments dominated and thus that the libraries were stranded (+@fig:fig6_4\-C).

Dispersion of sense read count per gene was low which permitted identification of differentially accumulating transcripts [defined as DEseq2 P-adjusted (Padj) <0.1\; @Love2014] comparing ferns on TL and TL with FR: 318 from the fern nucleus, 67 from _N. azollae_ and five from the fern chloroplast (Supplementary Table S4).
We next wondered whether the changes in transcript abundance reflect adaptations to light quality and the transition to reproductive development.

![Profiling eukaryotic and prokaryotic RNA simultaneously in _A. filiculoides_ (dual RNAseq). (A), Similarity of  the _N. azollae_ 0708 genome and Metagenome Assembled Genomes (MAGs) from _N. azollae_ strains in Azolla species. Average Nucleotide Identity (ANI) was calculated with the dRep implementation of nucmer using the ANImf preset [@Kurtz2004; @Olm2017]. Pairwise average ANI is shown in an UPGMA dendrogram [@vries2020; @Wickham2011a]. Aligned MAGS covered over 90% of the reference _N. azollae_ 0708. (B), Proportion (percent) of uniquely aligned PE reads (dark color) and PE reads aligning at multiple loci (light color) on the genomes of fern (green), fern chloroplast (purple) and _N. azollae_ 0708 (red). PE reads were from samples of sporophytes grown for a week on TL-light (replicates T1, T2, T3) or TL light with FR (replicates F1, F2, F3). STAR-aligner was used in PE mode. (C), Yields of PE uniquely mapped compared with PE read counts on features and PE reads that STAR aligned ambiguously to several features. Features were specified by current general features files of each of the fern (green), chloroplast (purple) and _N. azollae_ 0708 (red) genomes.](source/figures/fig6_4.png){#fig:fig6_4 short-caption="Dual RNAseq yields of the Azolla symbiosis"}

## FR causes small transcriptional changes that may reflect small light-harvesting adaptations in chloroplasts and _N. azollae_, but large changes in transporters of _N. azollae_

After a week exposure to FR, decreased chloroplast transcripts included psbD (18651 BM, -0.72 log2FC, 0.074 Padj), previously reported as responsive to light quality in plant lineages [@Shimmura2017] and suggesting that read counts obtained made some sense.
In contrast, increased chloroplast transcripts encoded ycf2 (141 Base Mean (BM) related to reads per million (this is low because ycf2 is in the repeat region), 2.9 log 2 fold change (log2FC), 0.001 Padj), energizing transport of proteins into the chloroplast, and RNA polymerase subunit rpoA (1284 BM, 1.3 log2FC, 0.000 Padj) (Supplementary Table S4, _A. filiculoides_ Chloroplast).

Consistent with the high levels of N~2~ fixation measured in Azolla [@Brouwer2017c], the highest _N. azollae_ read counts were in transcripts of the nif operon (the highest: AAZO_RS06505 nifH  averaging 45,084 reads per million reads aligning to the _N. azollae_ genome (rpm)), genes encoding photosystem I (AAZO_RS02645 psbA averaging 47,415 rpm) and II proteins (AAZO_RS06500 psbB averaging 29,767 rpm) and ATP synthase subunits (the highest: AAZO_RS15835 AtpA averaging 13,024 rpm).
In addition, read counts for the global nitrogen regulator ntcA (AAZO_RS05170 averaging 1,329 rpm) and metabolic enzymes supporting high N~2~ fixation were high (Supplementary Table S5).
Read counts from the _N. azollae_ transcripts reflected the known very high N~2~-fixation capacity of the symbiont; we thus analyzed the data for differential expression with a measure of confidence.

In _N. azollae_, FR led to barely significant accumulation of a PsbA transcript of low abundance (817 BM; 1.36 log2FC with 0.099 Padj; Supplementary Table S4, _N. azollae_).
In contrast, FR led to significant reduction of transcripts from photosystem I reaction center subunit XII (149 BM; -1.22 log2FC, 0,047 Padj), geranylgeranyl hydrogenase ChlP (909 BM; -1.10 log2FC; 0.037 Padj), and phycobilisome rod-core linker polypeptide CpcG2 (1588 BM; -1.19 log2FC; 0.002 Padj; Supplementary Table S4, _N. azollae_).
These changes in light harvesting-related transcripts were small, however, compared to changes in transcripts encoding hypothetical proteins of unknown function, transposases and highly expressed transporters (TrKA: 2355 BM, 3.41 log2FC, 0.000 Padj; MFS:2361 BM, 2.66 log2FC, 0.003 Padj; and ABC transporter permease: 3996 BM, 2.53 log2FC, 0.000 Padj).
We conclude that a one-week induction of reproductive structures with FR may have caused few and small transcriptional changes reflecting light-harvesting adaptations in _N. azollae_.
The larger differential accumulation of transporter transcripts may reflect more important changes in metabolite trafficking and communication with the host fern.

| _A. filiculoides_ locus | baseMean | Log2Fold Change | DESeq2 padj | Mercator 4.0 annotation              | Closest _Arabidopsis_ Homolog               |
| ----------------------- | -------- | --------------- | ----------- | ------------------------------------ | ------------------------------------------- |
| Azfi\_s0028.g024032     | 9        | 7.22            | 0.001       | 15.5.14 MADS/AGL                     | AGL20/SOC1, MIKCC                           |
| Azfi\_s0113.g045874     | 155      | 6.41            | 0.002       | 15.5.2 R2R3MYB                       | AtMYB 32 (AT4G34990.1), R2R3MYB VIII-E\*    |
| Azfi\_s0083.g038807     | 59       | 5.75            | 0           | 15.5.32 Basic Helix-Loop-Helix       | EDA33, IND1, INDEHISCENT (AT4G00120.1)      |
| Azfi\_s0003.g007560     | 8        | 5.27            | 0.011       | 15.5.32 Basic Helix-Loop-Helix       | FIT1 (regulates iron transport)             |
| Azfi\_s0003.g007559     | 34       | 3.49            | 0           | 15.5.32 Basic Helix-Loop-Helix       | FIT1 (regulates iron transport)             |
| Azfi\_s0096.g043715     | 31       | 3.13            | 0.001       | 15.5.7 DREB subfamily A-2 of ERF/AP2 | AT5G18450.1                                 |
| Azfi\_s0003.g007710     | 1778     | 2.82            | 0           | 15.5.14 MADS/AGL                     | AGL6, MIKCC                                 |
| Azfi\_s0015.g013719     | 111      | 2.57            | 0           | 15.5.2 G2-like, GARP                 | HHO2, NIGT1.2                               |
| Azfi\_s0112.g045798     | 66       | 2.2             | 0           | 15.5.51.1 NF-Y component NF-YA       | AT5G12840.4                                 |
| Azfi\_s0014.g013539     | 105      | 2.07            | 0.005       | 15.5.2 R2R3MYB                       | LOF2, R2R3MYB V [^R2R3]                     |
| Azfi\_s0015.g014012     | 165      | 1.99            | 0.026       | 15.5.17 NAC domain                   | NAC025                                      |
| Azfi\_s0004.g008455     | 103      | 1.93            | 0.003       | 15.5.2 R2R3MYB                       | miRNA319 controlled GAMYB 33, R2R3MYB VII [^R2R3] |
| Azfi\_s0132.g049213     | 63       | \-2.35          | 0.004       | 15.5.32 Basic Helix-Loop-Helix       | No hits                                     |
| Azfi\_s0182.g056462     | 10       | \-4.46          | 0.049       | 15.5.3 HD-ZIP I/II                   | HB16                                        |

Table: Transcription factors with largest changes in transcript abundance in sporophytes in TL with versus without FR. TF with homology to TF related to flowering are bold type. {#tbl:tbl6_TFs}

[^R2R3]: R2R3 MYB classification according to @Jiang2020a.

## FR alters transcripts from MIKCC and R2R3MYB TF related to those of the IF of seed plants

As in the case of _N. azollae_ symbiont, the ferns largest changes in transcript accumulation under FR were in genes with unknown function, then in secondary- and lipid-metabolism (Supplementary Table S4, _A. filiculoides_ nucleus).
We noted the large induction of the SWEET-like transporter (Azfi_s0221.g058704: 22 BM, 7.5 log2FC, 0.000 Padj), of transcripts related to cysteine-rich peptide signaling (Azfi_s0046.g030195: 42 BM, 7.1 log2FC, 0.074 Padj; Azfi_s0745.g084813: 99 BM,  4.0 log2FC, 0.000 Padj) and of transcripts from jasmonate metabolism.
To examine the link between IF in seed plants and IS ferns, however, TF were analyzed in more depth.
Transcripts of MIKCC and of R2R3MYB TF were strikingly induced in sporophytes under FR (Table 2).

The most induced TF transcript was annotated as SOC1-like MIKCC (Azfi_s0028.g024032: 9 BM, 7.2 log2FC, 0.001 Padj); its predicted gene model, however, lacked the K-domain.
This problem was due to the fact that the TF encoded by Azfi_s0028.g024032 was not expressed in vegetative sporophytes used for the original annotation of the _A. filiculoides_ genome [@Brouwer2017c; @Li2018].
Manual re-annotation of this TF using the reads obtained in this study allowed to place it precisely in phylogenetic trees of MIKCC transcription factors sampled over taxa representing different lineages of land plant evolution (Supplementary Figure S4).
In fact, both induced Azolla MIKCC from Table 2 were placed in the reproducibly well-supported clade (95.5% bootstrap confidence) of fern sequences radiating separately from the angiosperm and gymnosperm MIKCC clade that gave rise to AtSOC1, FLC, and the A,C,D and E-function floral homeotic genes (Supplementary Figure S4).
Induction of the _A. filiculoides_ SOC1-paralogue had been confirmed by qRT-PCR (Supplementary Figure S2G).
In Arabidopsis, AtSOC1 is known to control the steady state of miR319 that inhibits TCP TF functions necessary for the transition to an inflorescence meristem at the shoot apex [@Lucero2017]; the link may also operate in Azolla since a TCP TF (Azfi_s0168.g054602: 661 BM, 1.11 log2FC; 0.086 Padj) was induced in ferns on TL with FR (Supplementary Table S4, _A. filiculoides_ nucleus).

Transcripts of R2R3MYB TF could be assigned to families using data from @Jiang2020a (Table 2).
The highly induced class VIII-E TF Azfi_0113.g045874: 155 BM, 6.4 log2FC, 0.002 Padj) likely controls changes in secondary metabolism together with the similarly changed bHLH TF [@Gungor2021], and therefore may not be linked to IS directly.
In contrast, induced R2R3MYB from the classes V (Azfi_s0014.g013539: 105 BM, 2.1 log2FC, 0.005 Padj) and VII (Azfi_s0004.g008455: 104 BM, 1.9 log2FC, 0.003 Padj) are known to affect seed plant IF, with the GA pathway associated class VII GAMYB in seed plants known to be regulated by miR319.

Prominence of transcription factors in Table 2 known for their role in IF-development in seed plants begged the question as to whether any IF pathways with conserved miRNA were conserved in the common ancestor of seed plants and ferns.
This required to first characterize miRNA loci in the _A. filiculoides_ symbiosis.

![sRNA size distribution and sequence diversity for each size from the genomes in the _A. filiculoides_ symbiosis. sRNA reads were mapped with 0 mismatches, no overhang, to the concatenated genomes; bam2fasta was then used to extract sRNA sequences aligning per genome, the fasta files obtained were then collapsed to compute read counts for each sRNA, the lists obtained were then joined to a read count matrix imposing at least 1 read per sRNA in each of the three replicate sample types: f (FR), t (TL) and fn (FR and nitrogen in the medium). sRNA counts were then normalized to the total read counts per sample for that genome. sRNA read counts were further averaged over all samples considered, then the averages of sRNA with the same size summed up of sRNA which yielded the sum of normalized read count averages and reflects how many sRNA are found for each size (read counts). For each sRNA size we also calculated the mean number of different sRNA sequences found (diversity). (A), Fern nucleus. (B), Chloroplast, included samples from sporophytes without cyanobacteria in the analysis. (C), _N. azollae_, read count files joined imposing at least 10 reads per sRNA in every sample.](source/figures/fig6_5.png){#fig:fig6_5 height=80% short-caption="sRNA distribution in the Azolla symbiosis' genomes"}

## Small RNA profiles are characteristic for fern nucleus, chloroplast or _N. azollae_

Short RNA reads were obtained from sporophytes after a week growth under TL without and with FR from the same cultures as those used for dual RNA sequencing.
In addition, reads were obtained from sporophytes grown under TL with FR on medium with 2 mM NH4NO3, and from sporophytes without _N. azollae_ on medium with 2 mM NH4NO3.
All samples were collected two hours into the 16 h light period.
The sRNA sequencing library preparation chemistry did not distinguish pro- from eukaryote sRNA and therefore was inherently a dual profiling method.
Reads obtained were aligned to concatenated genomes which yielded small RNA profiles characteristic for the fern nucleus, chloroplast and _N. azollae_ (+@fig:fig6_5; Supplementary Figure S5).

The most abundant sRNA encoded in the fern nucleus were 21, 20 and 24 nt long, but the most sequence-diverse were 24 nt long (+@fig:fig6_5\-A).
This was consistent with an abundance of 21 nt miRNA discretely cut into one or a very few 21 nt miRNA from a single hair-pin precursor [@Singh2018].
The higher sequence diversity of the somewhat less abundant 24 nt siRNA was consistent with the multiple cleavage sites on the longer double stranded RNA generated by RNA-dependent polymerase of the siRNA precursors that lead to several different 24 nt siRNA per locus transcribed [@Singh2018].
The chloroplast most abundant sRNA of 28 nt was also the most sequence diverse, but the chloroplast sRNA have a conspicuous number of sRNA of 34 nt which represent only few different sequences (+@fig:fig6_5\-B).
The sRNA encoded in _N. azollae_ are generally shorter than those of the chloroplast, yet, they have a conspicuous abundance of 42 nt sRNA, consistent in length with CRISPR RNA; these sRNA have not a very varied sequence (+@fig:fig6_5\-C).

![The miRNA 172a locus in _A. filiculoides_.  Alignments at the Azfi_miRNA172α locus are visualized using the Integrative Genomics Viewer [@Thorvaldsdottir2013]; S, read summary; i, individual reads. (A), Reads from pre-miRNA at the miR172a locus. RNAseq all conditions, all reads pooled from  the diel RNAseq experiment in [@Brouwer2017c]. (B), Reads of the miR172 in sRNA libraries including those of ferns without _N. azollae_ (sRNAseq-_N. azollae_), ferns grown with and without far-red LED (sRNAseq+FR, sRNAseq TL-FR). (C), Reads of the miR172\*. (D), Azfi_miRNA172α hairpin folded using Vienna RNAfold [@Gruber2008]. RNAfold predicts -104,07 kcal mol-1 at 22 oC upon folding. miRNA (purple) and miRNA\* (pink) stem arms are shown with 3’overhangs.](source/figures/fig6_6.png){#fig:fig6_6 short-caption="the miRNA 172a locus in Azolla filiculoides"}

## Conserved miRNA in _A. filiculoides_ include miR172 and 396, but only miR319 and miR159 were decreased  in response to FR, whilst miR529 and miR535 were increased

Fern genome-encoded sRNA reads of 20-25 nt length were used for miRNA predictions allowing a hairpin of maximally 500 bp.
Loci predicted were then verified against miRNA criteria [@Axtell2018] as, for example, in the case of the miR172 locus Azfi_s0021g15800 (+@fig:fig6_6): the locus was expressed as a pre-miRNA (+@fig:fig6_6\-A, RNAseq all conditions) and both the miRNA and miRNA\* are found in replicate samples and cut precisely with two base overhangs (+@fig:fig6_6\-B-C, sRNAseq).
The miR172 reads were derived from the fern since they were also found in sporophytes without _N. azollae_ (+@fig:fig6_6, RNAseq -_N. azollae_).
The locus encoded a stable long hairpin which when folded released -65.76 kcal mol-1 at 37oC.
miR172 targets in seed plants include the AP2/TOE transcription factors, and alignment of the target sites to all annotated AP2/TOE transcripts from _A. filiculoides_ revealed target sites for the AzfimiR172 (Supplementary Figure S6).
The miR156a locus was similarly verified (Supplementary Figure S7).

Mature miRNA were compared in miRbase [@Kozomara2019] which identified 11 of the conserved miRNA families of 21 nt in the _A. filiculoides_ genome and thus in the fern lineage (+@fig:fig6_7).
The list included miR396, as well as miR172, not yet confirmed in other seed-free plant lineages.
miRNA predictions further uncovered a number of novel miRNA (miRNF).

![Conserved and FR-responsive miRNA in the fern _A. filiculoides_. (A), Conserved miRNA in the _A. filiculoides_ fern compared to other land plant lineages. miRNA from the fern were predicted computationally by miRDEEP-P2 [@Kuang2019] using sRNA seq reads then curated manually, the remainder of the table was from @Axtell2018. Green, high confidence miRNA; yellow low confidence miRNA. (B), miRNA with altered steady state in response to far-red light. Shown are average read counts per million 20-22 nt reads in samples of sporophytes after one week on TL with FR (f) or without (t); raw read counts were submitted to DESeq2 for statistical analyses yielding P-adjusted values: * indicates Padj <0.1; ^ indicates Padj <0.16.](source/figures/fig6_7.png){#fig:fig6_7 short-caption="FR light induces a conserved miRNA response in A. filiculoides"}

Differential expression analysis of 20-22 nt reads exhibited more dispersion than the dualRNAseq of long RNA, yet, it reliably identified sRNA with low Padj values when comparing ferns under TL with and without FR (Supplementary Figure 5D-E).
Reads from miR529c&d and miR535 increased (Padj < 0.1) whilst those of miR159, miR319 and miRNF4 decreased (Padj <0.16) in sporophytes on TL with FR compared to TL light only (+@fig:fig6_7\-B).
We conclude that the miR156/miR172 known to reciprocally control flowering are not altered when whole ferns undergoing transition to IS under FR are analyzed.

## miR319/GAMYB is responsive in sporophytes induced by FR

miRNA targets were predicted combining psRNATarget [@Dai2018] and TargetFinder [@Srivastava2014] then annotated with Mercator [@Lohse2014; @Schwacke2019].
Predictions were consistent with analyses in other land plant lineages (Supplementary Table S6): miR172 targeted AP2/TOE-like transcription factors and miR156, 529 and miR319 SPL-like proteins.

Transcripts of neither SPL nor AP2/TOE-like targets, however, were significantly (Padj < 0.1) altered in sporophytes comparing TL with and without FR (Supplementary Table S6, F vs T Padj).
The Azfivs1 assembly is far from chromosome scale, and it annotation is based on very few experimental data sets, we may therefore be missing SPL or AP2 targets.
Nevertheless, consistent with an increased miR529c&d, the SPL from the Azfi_s0173.g055767 transcript appeared reduced but with no significance (Padj of 0.356).
In contrast, transcripts of two GAMYB (Azfi_s0004.g008455 and Azfi_s0021.g015882) increased up to 4 fold in sporophytes with decreased miR319 on TL with FR.
The location of miR319 binding is shown for the GAMYB encoded in Azfi_s0004.g008455 (Supplementary Figure S8).

Phylogenetic analyses revealed that the GAMYB targeted by miR319 were on the same leaf as the GAMYB33 from Arabidopsis and were placed next to each other, probably because they arose from gene duplication (+@fig:fig6_8).
This is consistent with the whole genome duplication observed at the base of Azolla fern evolution [@Li2018].
We conclude, therefore, that miR319/GAMYB is responsive in sporophytes undergoing FR-induced transition to IS.

![R2R3MYB phylogenetic analyses and expression fold-change in sporophytes with versus without FR. Sequences were extracted from the genome browsers of each species, aligned with MAFFT E-INS-I [@Katoh2019], then trimmed with trimAL [gap threshold 40\%\; @Capella-Gutierrez2009]. Phylogenetic inferences were computed with IQtree with the LG+F+R10 model as determined by the Iqtree internal model fitter [@Nguyen2015]; non-parametric bootstrap values are shown. _Chara autralis_ (Ca), _Chara braunii_ (Cb), _Chara leptospora_ (Cl), _Marchantia polymorpha_ (Mp), _Selaginella moellendorfii_ (Sm), _A. filiculoides_ (Azfi), ), _Salvinia cuculata_ (Sc), _Picea abies_ (Pa), _Amborella trichopoda_ (Atri), _Arabidopsis thaliana_ (At). Sequence names are color coded after the R2R3 MYB subfamilies defined in @Jiang2020a. Log two fold change (Fold change) in response to FR was calculated by DESeq2, green stars mark significant changes with Padj <0.1.](source/figures/fig6_8.pdf){#fig:fig6_8 height=85% short-caption="R2R3MYB phylogenitec tree with transcriptomics data"}

# Discussion

Results obtained indicated that FR and canopy density are required for the elongation and then induction of sporocarps in _A. filiculoides_; the sporocarps thus obtained could be used for crosses.
Results were valid for _A. filiculoides_ but for a different species collected in the Anzali lagoon, phylogenetically close to species from Southern Brazil and Urugay.
Fern and seed plants share a common ancestor which may predict similar mechanisms in the responses to FR, including elongation and transition to sexual reproduction.
Dual RNA profiling revealed differential transcript accumulation in the symbiosis upon exposure to FR, most notably of transporters in the _N. azollae_, and of TF known from the flowering transition in seed plants.
sRNA profiling provided a first insight in the diversity of sRNA of the symbiosis including conserved miRNA in the fern and other land plant lineages.
We thus firstly discuss possible mechanisms involved in the sensing and signal transduction of FR in ferns compared to other plant lineages.
Secondly, we discuss regulons that appeared conserved in ferns and seed plants undergoing transition to sexual reproduction.
Finally, we discuss the method of dual-RNA sequencing as a more generally required tool, but insufficient.

## Red-dominated light suppresses formation of dissemination stages in both gametophyte and sporophyte-dominated lineages of plants and  represents a convergent ecological strategy.

FR responses in Azolla look like a shade-avoidance syndrome but signal transduction pathways that mediate them in ferns remain largely uncharacterized [@Inoue2019].
Pathways causing shade response components are known to use alternative phytochromes and interacting factors [@Possart2013b; @Xie2020].

Phytochromes in ferns radiated separately from those of seed plants [@Li2015a], hence, their function cannot be predicted using orthology with seed plants.
Nevertheless, fern phytochromes have a similar structure and, as in the case of PHYB in Arabidopsis, may sense temperature as well as red/FR light by thermal reversion from the Pfr into Pr state [@Legris2017; @Klose2020]: initiation of fern, liverwort and bryophyte sporangia is reported as dependent on temperature and photoperiod [@Labouriau1958; @Benson-Evans1961; @Nishihama2015].
Moreover, thermal reversion of phytochromes from some cyanobacteria was described in vitro as early as 1997 [@Yeh1997].
Therefore, if FR induces IS in _A. filiculoides_, then differing temperature regimes combined with light quality changes may yet induce IS in the Anzali ferns.
Anzali ferns were not _A. filiculoides_ but related to species from Uruguay and Southern Brazil which did not cluster with the bulk of the _A. caroliniana_ species (+@fig:fig6_2), and did not have the single-celled papillae described for _A. caroliniana_ [@Pereira2006](Supplementary Figure S3).
More work is needed to verify whether these south American strains represent a new species of Azolla.
The phylogenetic position of the Anzali accession analyzed here was consistent with observations of several distinct-looking Azolla in the Anzali lagoon [@Farahpour-Haghani2017], and suggests that not only _A. filiculoides_ may have been released as nitrogen biofertilizer.

Unlike _A. filiculoides_, Arabidopsis will transition to IF in the TL generally used for indoors cultivation.
Most studies on the transition to IF, therefore, were done with red-light gated Arabidopsis plants, in conditions leading to artefactual peaking of CONSTANS protein accumulation and florigen (FT) expression [@Song2018].
 Nevertheless, Arabidopsis as well as many other seed plants flower early when in ratios of red to FR approaching one, the ratio encountered in day light, compared to TL.
FR-dependent flowering is mediated by PHYB and D, eventually leading to SOC1 expression in the meristem [@Halliday1994; @Aukerman1997; @Lazaro2015].
FT mutant Arabidopsis flowered earlier under incandescent light [@Martinez-Zapater1990] or in FR compared to in TL (Schluepmann et al., unpublished) suggesting that FT is not involved.
Signaling was also reported via PHYB-regulated PIF4 protein complexes that bind the promoters of miR156/172 directly with interference from PHYA-regulated TF [@Sanchez-Retuerta2018; @Sun2018; @Xie2020].
In the present study, the highly induced MIKCC turned out to be a paralogue of AtSOC1, and miR156/172 steady states were unaltered by the FR-induced transition to IS in _A. filiculoides_ (+@fig:fig6_7\-B; Supplementary Table S6) suggesting that signal transduction leading to IS/IF control in fern and seed plant sporophytes are not conserved.

FR-induced sexual reproduction in the liverwort gametophytes of _Marchantia polymorpha_ [@Chiyoda2008; @Kubota2014; @Yamaoka2018; @Tsuzuki2019].
The mechanism in these liverworts involved the MpmiR529c/MpSPL module, which was necessary for the development of reproductive branches.
MpPHY and MpPIF were required to mediate the response [@Inoue2019].
Our analyses with _A. filiculoides_ reveal induction of AzfimiR529 under FR but no significant change in SPL targets.
Additionally, the specific MpmiR529c sequence involved in _M. polymorpha_ was not detected in our ferns.
The pathways thus differ in the two seed-free plants.

Given that gametophyte and sporophyte dominated lineages require FR to initiate formation of dissemination stages, we conclude that repression of IS under dominating red light in Azolla likely reflects a convergent ecological strategy: in open surfaces, where red-light is abundant, there is sufficient space to prolong vegetative development and no need for dispersal.
Consistently, in addition to FR, density of the _A. filiculoides_ canopy had an additional impact on the number of sporocarps observed per gram plant (+@fig:fig6_2\-F); this may stem from alternative cues such as volatile organic compounds released by neighbors [@Vicherova2020].
Taken together, results presented in this work signify that, for the first time, IS of the Azolla fern symbiosis is amenable to experimental enquiry.

## Phylogenetic position of MIKCC TF responsive to IS suggests that control of flowering in seed plants originates from the diploid to haploid transition in the common ancestor of seed plants and ferns

The GAMYB TF clade arose before land plants evolved, and before GA signaling [@Aya2011; @Bowman2017a; @Jiang2020a] (+@fig:fig6_8).
Azolla GAMYB induced under FR, therefore, likely function in IS by mediating cues perceived by the sporophyte but originating from an ancestral gametophyte regulon.
Consistently, GAMYB from the moss Physcomytrella patens were required for the formation of antheridiophores by the gametophyte [@Aya2011].
The lycophyte GAMYB regulon did not play a role in the induction of sporogenic structures.

AtGAMYB are known to be regulated by miR159 in Arabidopsis and by the related and more ancestral miR319 in seed-free plant lineages [@Achard2004; @Palatnik2007].
The AtGAMYB/miR159 is part of the GA pathway promoting flowering in Arabidopsis under short days [@Millar2019].
Specifically, AtMYB33 was shown to directly act on the promotors of both miR156 and AtSPL9 [@Guo2017].
In Azolla, FR repressed miR159 and miR319, and increased AzfiGAMYB but this is difficult to interpret given that the compressed life cycle of the gametophyte inside the sporocarps.
Extending the analysis of the GAMYB regulon to homosporous ferns with free gametophytic stages will reveal whether this regulon is important for the diploid to haploid transition, or rather with gametophyte development as predicted from lycophyte studies.

Control over sexual reproduction switched from the gametophyte, in gametophyte dominated seed-free plants, to the diploid sporophyte in seed plants.
The switch led to the evolution of regulons with MIKCC TF commanding floral meristems and flower architecture.
The MIKCC clade of TF that specify both IF and floral organs in seed plant sporophytes, (such as AtSOC1 and AtFLC, and the A,C, D and E homeotic functions) are peculiar in that the TF radiated in each megaphyll plant lineage separately [Supplementary Figure S4\; @Leebens-Mack2019].
The TF work as hetero-tetramers and may have evolved from an ancient tandem gene duplication through subsequent polyploidy events [@Zhao2017].
Sepals are organs formed only in angiosperms.
Consistently, the TF clade with A functions specifying sepals contains solely angiosperm sequences.
MIKCC specifying organs that contain the reproductive structures in angiosperms (C, D and E homeotic genes), had direct homologues in gymnosperms, but not in ferns.
Instead, ferns radiated a sister clade to the clade containing AtSOC1, and A, C, D and E MIKCC.
This clade contained the Azolla MIKCC responsive to FR (SOC1 paralogues) and the closely related CMADS1 from Ceratopteris richardii.
In situ hybridizations and northern blot analyses reveal that CMADS1 transcripts accumulate at high levels in the sporangia initials [@Hasebe1998].
At the base of the radiating clade of modern MIKCC that specify flower organs of the sporophytes controlling the gametophyte development within, is the LAMB1 protein expressed specifically in sporogenic structures of lycophytes [Supplementary Figure S4\; @Leebens-Mack2019; @Svensson2000].
Combined phylogenetic and RNAseq analyses, therefore, suggest that the MIKCC regulons controlling flowering and flower architecture likely originate from the diploid to haploid phase transition of the common ancestor to ferns and seed plants, not from regulons controlling sexual reproduction per se.

## Dual RNA sequencing to study coordinate development in assemblages of pro- and eukaryotic organisms

The dual RNAseq method employed here could be applied more generally to study bacteria/plant assemblages particularly common in the seed-free plant lineages, and representing an important base of the “tangled tree” of plant lineage evolution [@Quammen].
For Azolla where co-evolution of _N. azollae_ and fern host genomes demonstrated that fitness selection occurs at the level of the metagenome [@Li2018], it delivered foundational data and opens the way to studying the coordinate development of host and obligate symbiont.
Efficient removal of the rRNA was key to the success of sequencing RNA.
Transcripts from the fern’s mitochondrial genome are likely in the data but we have yet to assemble the _A. filiculoides_ mitochondrial genome to confirm this.

The RNA profiling did not reveal whether the _N. azollae_ trigger fern IS since roles of the FR responsive transcripts in _N. azollae_, particularly those encoding the transporters, have yet to be studied.
An approach could be to study these in free living filamentous cyanobacteria amenable to genetic manipulation.
Manipulation of the symbiont would, however, be preferred.
Tri-parental mating protocols may be effective on _N. azollae_ in situ if combined with high-frequency RNA-guided integration with Cas12k enzyme complexes [@Strecker2019].
_N. azollae_ Cas genes were found to be mostly pseudogenes and CRISPR arrays appeared missing [@Cai2013], suggesting that incoming cargo plasmid may not be destroyed by Cas complexes.
Nevertheless, sRNA profiles from +@fig:fig6_6 show discrete accumulation of 31 and 42 b sRNA of very low complexity and a functional Cas6 splicing CRISPR precursor RNA was induced on FR (Supplementary Table S4, _N. azollae_).
CRISPR arrays may not have been recognized if they contained few repeats due to the sheltered life-style inside the fern.
Rendering _A. filiculoides_ and _N. azollae_ amenable to genetic manipulation will be crucial to provide evidence for hypotheses generated by transcript profiling in the future.

# Acknowledgments

We are grateful to Bruno Huettel for advice on dual RNA sequencing library preparation methods.
We thank Bas Dutilh and Berend Snel for access to the Utrecht University bioinformatic computing resources.
Data Availability Statement
Data will be uploaded upon acceptance of the manuscript and will include 1) read files for the dual RNA seq as well as small RNA seq on ENA, 2) phylogeny files on Github.

<!-- close the last page of this section as required for removing the thumb index on next "part page" -->
\newpage
\null
<!-- don't show page nrs on cleardouble page -->
\pagestyle{plain}
<!-- stop the thumbmarking scheme (partwise) and start it (chapterwise) in the next chapter -->
\stopthumb
<!-- clear double page so that the chapters start nicely on a new right page -->
\cleardoublepage
