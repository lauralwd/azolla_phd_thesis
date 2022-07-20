\onehalfspacing
\setlength{\parindent}{0.0in}
# Is there foul play in the leaf pocket? The metagenome of floating fern _Azolla_ reveals endophytes that do not fix N~2~ but may denitrify

Laura W Dijkhuizen^1^,
Paul Brouwer^1^,
Henk Bolhuis^2^,
Gert-Jan Reichart^3^,
Nils Koppers^4^,
Bruno Huettel^5^,
Anthony M Bolger^6^,
Fay-Wei Li^7,8^,
Shifeng Cheng^9^,
Xin Liu^9^,
Gane Ka-Shu Wong^9,10^,
Kathleen Pryer^6^,
Andreas Weber^4^,
Andrea Bräutigam^4^,
Henriette Schluepmann^1^.

1. ,Molecular Plant Physiology Department, Utrecht University, Utrecht 3584CH, The Netherlands <br>
2. Department of Marine Microbiology and Biogeochemistry, Netherlands Institute for Sea Research (NIOZ), Utrecht University, Den Hoorn 1797SZ, The Netherlands<br>
3. Department of Earth Sciences, Utrecht University, Utrecht 3508TA, The Netherlands<br>
4. Cluster of Excellence on Plant Sciences (CEPLAS), Department of Plant Biochemistry, Heinrich Heine University, Düsseldorf 40225, Germany<br>
5. Max Planck Institute for Plant Breeding ADIS/DNA Core Facility, Cologne 50829, Germany<br>
6. Institute for Biology I, Institute for Botany and Molecular Genetics (IBMG), RWTH Aachen University, Aachen, Germany<br>
7. Department of Biology, Duke University, Durham, NC 27708, U.S.A<br>
8. Boyce Thompson Institute For Plant Research, Cornell University, Ithaca, NY 14853, U.S.A<br>
9. Beijing Genomics Institute-Shenzhen, Shenzhen 518083, China<br>
10. Department of Biological Sciences, University of Alberta, Edmonton, AB T6G 2E9, Canada.<br>

manuscript published in new phytologist
\newpage
\setlength{\parindent}{0.5in}

## Abstract
Dinitrogen fixation by _Nostoc azollae_ residing in specialized leaf pockets supports prolific growth of the floating fern _Azolla filiculoides_.
To evaluate contributions by further microorganisms, the _A. filiculoides_ microbiome and nitrogen metabolism in bacteria persistently associated with Azolla ferns were characterized.
A metagenomic approach was taken complemented by detection of N~2~O released and nitrogen isotope determinations of fern biomass.
Ribosomal RNA genes in sequenced DNA of natural ferns, their enriched leaf pockets and water filtrate from the surrounding ditch established that bacteria of _A. filiculoides_ differed entirely from surrounding water and revealed species of the order Rhizobiales.
Analyses of seven cultivated Azolla species confirmed persistent association with Rhizobiales.
Two distinct near full-length Rhizobiales genomes were identified from leaf-pocket enriched samples from ditch grown _A. filiculoides_.
Their annotation revealed genes for denitrification but not N~2~-fixation. ^15^N~2~ incorporation was active in ferns with _N. azollae_ but not in ferns without.
N~2~O was not detectably released from surface sterilized ferns with the Rhizobiales.
N~2~-fixing _N. azollae_, we conclude, dominated the microbiome of Azolla ferns.
The persistent but less abundant heterotrophic Rhizobiales bacteria possibly contributed to lowering O~2~ levels in leaf pockets but did not release detectable amounts of the strong greenhouse gas N~2~O.

## Introduction
Our growing global population is rapidly escalating the demand for nutritious food, requiring highly prolific and sustainable primary production.
In tandem, the need for renewable feedstocks for the industry derived from primary production is also growing.
To sustain future food and feedstock production, we need to explore novel crops that comply with limitations imposed by climate change, agrosystem inputs (e.g., water, fertilizers), and available arable land.
Of particular concern, is the ubiquitous requirement for nitrogen fertilizer in current agriculture that is tied to high input costs and negative climate consequences [@Jensen2012a].
No crop plant is capable of fixing atmospheric dinitrogen (N~2~) autonomously.
In leguminous crops such as soybean, for example, plants recruit free-living, nitrogen-fixing bacteria ranked in the order Rhizobiales from their environment anew each host generation [@Vance2002], and it is within the legume’s specialized root nodules that these symbiotic heterotrophic bacteria fix dinitrogen sufficient for host and bacteria.
N~2~-fixation requires large amounts of energy derived from the oxidation of plant sugars, which are a limiting factor.
Under intensive agriculture, therefore, most leguminous crops are supplied with surplus nitrogen fertilizer to improve bean yields beyond 5 t ha-1 a-1.

N~2~-fixing cyanobacteria are known to form symbioses with other plants such as cycads, ferns and bryophytes [@Adams2013].
These symbiotic cyanobacteria can use light, as well as plant-derived sugars, as an energy source to drive N~2~-fixation.
A single fern genus, Azolla, benefits from such a cyanobacterial symbiosis, and stands out for its prolific growth resulting in high protein biomass without nitrogen fertilizer.
For example, _A. filiculoides_ produced 39 t ha-1 a-1 dry weight (DW) biomass containing up to 25% protein [@becerra1990; @Brouwer2017c], whereas clover, Trifolium pratense, a high–yielding forage legume that is commonly grown with low fertilizer applications (150 kg ha-1 a-1), produced up to 15 t ha-1 a-1 DW biomass containing similar protein amounts [@anglade2015].
The cyanobacterial symbiont _Nostoc azollae_ is key to the fern’s remarkable productivity.
With its genome highly degraded (containing 31.2% pseudogenes and over 600 transposable elements), _N. azollae_ is unable to survive without its host [@Ran2010], and its spores are vertically transmitted to the next fern generation via the fern megaspores [sensu @Nagalingum2006] during sexual reproduction.
The cyanobacteria reside within specialized leaf pockets of Azolla, where they form heterocysts with high frequency and utilize photosystem I to drive N~2~-fixation.
A colony of motile cyanobacteria typically resides at the meristematic tip of the branch where the leaf pockets of the young developing leaves are still open, allowing cyanobacteria to migrate inside [@Perkins1993b].
Such a specialized environment that is attractive to cyanobacteria may also attract other bacteria.
Electron micrographs of leaf and megasporangiate sori cross sections have revealed the presence of other bacteria in addition to the cyanobacteria [@Carrapico1991; @Zheng2009].
Immuno-histochemical detection of nitrogenase using poly-clonal antisera did not, however, unequivocally reveal nitrogenase in these bacteria [@Braun-Howland1988; @Lindblad1991].
Moreover, the number of species and taxonomy of the cyanobacteria associated with Azolla has been controversial [@Pereira2014].
The focus of our present study is to characterize the microbiome associated with _A. filiculoides_.    
Plant-microbe interactions research has rapidly evolved over the last decades [@Turner2013].
Most studies focus on microbial interactions between plant roots and the rhizosphere, whereas microbes in the phyllosphere, the above-ground plant organs, have been less thoroughly examined [@Penuelas2014.
Symbiotic bacterial endophytes, non-pathogenic organisms that colonize intercellular spaces in plants, have been rediscovered with next-generation sequencing approaches that permit in situ studies.
Endophytes are ubiquitous and frequently found in plant species [@Stone2000c].
Although microbial species associated with a particular plant species can be numerous and diverse, a core microbiome can be identified, as illustrated for _Arabidopsis_ thaliana [@Lundberg2012a].
Microbiomes in the rhizosphere and phyllosphere are not the same, however, reflecting disparate niches in the different plant organs, each subject to its own developmental and environmental influences [@Turner2013].
hese microbiome differences are not just opportunistic, but often convey beneficial properties to the host plant.
Persistent mutualistic microbes have been shown in specific cases to increase fitness of plants, for example, in legumes non-nitrogen fixing rhizobia decrease grazing thus eliminating the fitness costs of the mutualistic interaction [@Simonsen2014].
Arthrobacter species were isolated repeatedly from Azolla and one strain was shown to produce the auxin indole acetic acid, possibly affecting fern development and growth [@Forni1992];
an _Agrobacterium_ strain isolated from surface sterilized _A. filiculoides_ assimilated ammonium possibly sequestering the growth inhibitory nutrient when it accumulates in the leaf pockets in excess [@Plazinski1990].
Capabilities of the host and microbiome, therefore, should be viewed as one unit, the metagenome, evolving through myriad environmental constraints.
Recently, shotgun sequencing of DNA extracted from microbial communities without PCR and subsequent metagenome assembly have become feasible, allowing for functional analyses of multiple genomes in addition to taxonomic assignments [@Castelle2013a; @Wrighton2014].
Assembly of short sequencing reads obtained from metagenome shotgun sequencing into long scaffolds, ideally representing near complete microbial genomes, however, is still elusive [@Tyson2004; @Charuvaka2011a; @Mendoza2014].
Metagenome assembly quality is primarily influenced by number and diversity of organisms present, as well as the length of reads.
Improved assemblies with long scaffolds could be obtained by sub-cloning DNA into fosmids before sequencing or by using long-read technologies such as those that were validated in studies of gut microbes [@Mizuno2013; @Leonard2014].
The presence of an organism in an environmental sample may then be computed by recruiting short reads from the environmental sample onto the assembled genome of that particular organism, such as what was successfully demonstrated with phage genomes from the ocean or bacterial genomes from salt brines [@Mizuno2013; @Pasic2009].
The focus of the present study is to characterize the identity and function of microbes persistently associated with _Azolla filiculoides_ using metagenomics shotgun sequencing of total DNA from samples collected in their natural environment, and also from cultured species of Azolla.

## Materials and methods

### Plant materials
_Azolla filiculoides_ Lam was obtained from the Galgenwaard ditch in Utrecht, The Netherlands.
In addition, six Azolla species were obtained from the bio-fertilizer germplasm collection at the International Rice Research Institute in the Philippines [Table 1 in @Watanabe1992].

### Collection and processing of samples from the natural environment
Whole plants of _A. filiculoides_, its enriched leaf pocket contents, and water filtrates from the surrounding water (13°C, pH 7.2) were collected as triplicate replicates from the Galgenwaard ditch in Utrecht (Table 1) on October 28th 2015.
Plant and water replicates were carried from the collection site in separate containers and treated separately.
Ferns were filtered using sieves of 4 mm mesh size to remove contaminating aquatic plants and animals, then washed by vortexing at full speed for 60s in 0.5% Tween-20, in batches of 5 g fresh weight (FW).
For whole plant samples, one plant of 200 mg FW and two ø3 mm glass beads were placed into tubes, snap frozen, and then homogenized by a TissueLyser II (QIAGEN, Duesseldorf, Germany).
Leaf pocket enriched fractions were prepared from washed ferns as described in @Orr1982.
Ditch water (1 L) from every replicate was passed through a 0.45 μm filter, then the biomass on the filter was resuspended in 500 µL water and frozen (-80°C) until DNA extraction.
DNA was extracted using the Mobio PowerLyzer® PowerSoil® kit (QIAGEN), according to the manufacturer’s protocol.

### Fern cultures and processing
Cultures of different Azolla species were obtained from the International Rice Research Institute (Philippines) except for _A. filiculoides_ [Table 1 in @Watanabe1992].
All Azolla species were grown on liquid medium without nitrogen and under long-day light with a far-red component as described in @Brouwer2017c, except when stated otherwise.
To obtain sterilized cultures of _A. filiculoides_, explants (<1 mm3) of leaves from the ditch plants were surface-sterilized using bleach at 1% available chlorine for 40 s, with four consecutive rinses in sterile water prior to cultivation on agar medium (0.6% w/v agarose, Duchefa, Netherlands).
Azolla without _N. azollae_ (referred to here as _A. filiculoides_-Sterilized) was first cultured on solid agar medium with 60 µg ml-1 erythromycin and 2 mM NH~4~NO~3~; the absence of _N. azollae_ was verified using confocal microscopy and by q-PCR, [Fig. 4\; @Forni1991; @Brouwer2017c].
Sterilized cultures were grown in enclosed glass containers with a stream of air (78 L h-1) pumped through 0.45 µm filters using aquarium pumps (SuperFish Air flow mini); _A. filiculoides_-Sterilized were used for DNA sequencing, the ^15^N~2~-fixation experiments and ^15^N determinations of Azolla biomass.
DNA extractions from cultured plants was after enrichment for nuclei [@Lutz2011] combined with Genomic-tip 100/G protocol (QIAGEN), for the long read sequencing, or directly using the Genomic-tip 100/G protocol for the short-read Illumina sequencing.
Sequencing library preparations and sequencing of DNA Libraries for short-read sequencing (in paired-end mode) were made after shearing the DNA as per the recommended protocol (TruSeq Nano DNA Library Prep Kit, illumina, Madison, WI, USA).
For Azolla samples from the ditch, care was taken to shear the DNA to approximately 800 bp (Covaris, Woburn, MA, USA) to improve EMIRGE assemblies.
Sequencing was performed using the illumina NextSeq500 desktop sequencer, yielding approximately 3 Gb sequence information per replicate (Supporting Information Table S1).  For cultured Azolla samples, libraries were generated sized at 250, 500 and 800 bp and sequenced at high coverage such that the data needed to be sub-sampled to 10 and 30 M reads, for comparison with data obtained from ditch Azolla.
Libraries for PacBioRS II (Pacific Biosciences, Palo Alto, CA, USA) sequencing of the nuclear DNA from a single plant of _A. filiculoides_-Sterilized (described under “Fern cultures and processing”) were generated after size separation with a cut-off at 14 kb (Blue Pippin, Sage Science, Beverly, MA, USA) according to the PacBio RS II protocol and sequenced using the P5-C3 chemistry, reaching 57 times coverage of the 750 Mb genome.

### Taxonomic assignments based on small ribosomal RNA (sRNA) sequences
Short-read sequences were sorted according to biological replicates and paired-end reads were trimmed using Trimmomatic [parameters `LEADING:5 TRAILING:5 SLIDINGWINDOW:4:15 MINLEN:36`\; @Bolger2014].
All reads passing quality control (QC) were processed in parallel by RiboTagger which directly assigns taxonomy from variable regions of rRNA genes found in single reads using a subset of the Silva database containing the V4 to V7 variable regions as reference [@Tange2011; @Xie2016].
Near whole-length rRNA genes were assembled with EMIRGE using standard parameters over 120 iterations [@Miller2011].
Classification of assembled rRNA genes was performed by Mothur, using the Silva non-redundant v119 reference database [@Schloss2009a; @Quast2013] .
In addition to processing samples as individual replicates (P1 to 3, L1 to 3, W1 to 3), reads from the three biological replicates of whole-plant, leaf-juice or water were pooled (P, L, W respectively) before analyses with either RiboTagger or EMIRGE.
This was done to evaluate the sensitivity of the taxon detection using either Emirge or RiboTagger with three times more reads.
### Genome assemblies with long reads
Long reads (PacBioRS II) from DNA of _A. filiculoides_-Sterilized were read-corrected then assembled into scaffolds by both Celera and Falcon assembler pipelines, yielding two preliminary genome assemblies [[https://github.com/PacificBiosciences/FALCON](https://github.com/PacificBiosciences/FALCON)\; @Myers2000; @Koren2012].
Bacterial scaffolds in the genome assemblies were identified by RNAmmer [@Lagesen2007].
Bacterial scaffolds with a minimum length of 0.1 Mb were extracted and assigned taxonomy based on the 16S rRNA genes in Mothur using the Silva database (Table 2).
Once identified, the scaffolds were submitted to RAST [@Overbeek2014] for annotation, which scored the nearest neighbour.
### Recruitment analyses
Short-read sequences were mapped to reference scaffolds and genomes with bowtie2 [v2.2.6; options: `--very-sensitive (-D20-R3-N0-L20-iS1,0.50)`\; @Langmead2012].
If applicable, fragmented genomes were converted to one sequential sequence for the purpose of visualisation.
Bowtie output was parsed with a custom script to extract position and the common bases in the alignment (identity score).
In a custom R script, aligned reads were binned (normalized for 0.05 Mb and 1 % ID) and read count per bin was log10 transformed [@Wickham2011; @Rcoreteam2013; @Dowle2014; @Carr2015].
### Data deposition
The sequences reported in this paper have been deposited in the ENA database with the study accession number PRJEB19522; the data is separated in three categories: Illumina paired end NextSeq500 sequences (2x 150b) from the environmental samples, Illumina paired end NextSeq500 sequences (2x 150b) short-read sequences sampled at 30 M reads from each of the different species and bacterial scaffolds.
### ^15^N~2~ fixation, 5N determinations and N~2~O release
Surface-sterilized ferns (100 mg FW) were placed in enclosed bottles with 43 ml of sterile medium and a residual air space of 262 ml.
To determine N~2~ fixation after 2 h, ^15^N~2~ (15 ml) was added at 14 h using air-tight syringes whilst overpressure was removed using a release needle; the bottles were then incubated for 2 h under growth conditions as in @Brouwer2017c.
To determine N~2~ fixation after 24 h, ^15^N~2~ (5 ml) was added as well as CO~2~ (5 ml).
After the incubation with ^15^N~2~, samples were snap frozen in liquid nitrogen, freeze-dried and homogenized before analysis of the dry weights, N content and isotope abundance determinations.
In both the 2 and 24 h incubation experiments ^15^N~2~ provided from Sigma was washed with acid to remove ammonia.
In the 24 h incubation experiment the gas was washed in addition with a base to remove NOx.
Total N content and stable nitrogen isotopes (δ^15^N) were analyzed on a ThermoScience Delta Plus isotope ratio mass spectrometer connected on-line to a Carlo Erba Instruments Flash 1112 elemental analyzer.
We assumed no isotope discrimination during the fixation process and therefore rates of fixation calculated may be underestimated.
Ferns used for N~2~O measurements included _A. filiculoides_ cultured in the laboratory (non-sterile), surface sterilized ferns with and without _N. azollae_ (_A. filiculoides_-Sterilized) grown under sterile conditions.
For experiments with non-sterile material 10 g FW fern were used with 200 ml air headspace.
For experiments including sterile materials 100 mg FW fern were used with 15 ml micro-aerobic (10% v/v O~2~) head space.  Gas samples of 6 ml were separated on a Hayesep Q column by gas chromatography (GC Hewlett Packard Agilent technologies, Palo Alto, CA, USA) and gases detected with an electron capture detector (ECD 63 Ni).

## Results

### _A. filiculoides_ sustains a unique microbiome
The Dutch ditch plants of _Azolla filiculoides_, together with samples of their in-situ ditch water, were sampled and processed for sequencing independently in three biological replicates (i=1-3) of the following types: whole plant (Pi), enriched leaf pocket contents (Li) and surrounding water (Wi), conatining 8.42-11.99 M reads averaging 147 b (Table S1).
Taxonomic groups present in samples were computed either by rRNA assembly with EMIRGE or by analysis of reads containing 16S rRNA variable regions with RiboTagger; using the Silva rRNA reference database [@Miller2011; @Quast2013; @Xie2016].
The distribution of taxonomic classes or orders over replicate samples was similar for both methods and very similar among biological replicates (Fig @fig:fig2_1\-a).
RiboTagger taxonomic assignments were not influenced by the number of reads sampled (10 or 30 M) since it computed an identical set of classes or orders in replicates with 10 M reads compared to when the three replicates were pooled to submit 30 M reads for analysis.
When assembling rRNA genes with EMIRGE, however, pooling replicates before EMIRGE assembly occasionally yielded more taxonomic assignments, likely because assemblies were dependent on read coverage (Supporting Information Figs. S1, S2).
Ditch water surrounding _A. filiculoides_ was more diverse in its microbial community composition than were the plant-related samples: the mean Shannon diversity of RiboTagger-assigned microbial taxonomy was 3.11±0.16 (standard deviation) for water samples, compared to 1.47±0.07 and 1.11±0.08 for whole plant and leaf samples, respectively.
The community richness was also higher in the ditch water samples than in plant-related samples.
Rarefaction analysis showed saturation of the plant-associated microbiome with sampling size, but not for the ditch water (Fig. 1b).
Over half of the taxa found in water samples were identified as class Betaproteobacteria, with the orders Burkholderiales, Rhodocyclales and Methylococcales being the most abundant (Fig. 1a).
Overlap between Azolla-associated samples and water samples was zero at order level and minimal at class level.

![Taxonomic diversity revealed in DNA isolated from ditch samples of _A. filiculoides_. Sequence data originating from leaf pocket-enriched samples (L), whole plants (P), and surrounding ditch water (W) were processed as individual biological triplicates, and as a pool thereof. (a) Relative abundance of bacterial classes derived from rRNA assemblies with EMIRGE combined with taxonomic assignments with Mothur (EMIRGE) or from RiboTagger analyses of reads with rRNA variable regions (RiboTagger). (b) RiboTagger OTU count with increased reads from pooled samples of leaf pocket-enriched samples (L), whole plants (P) and surrounding ditch water (W).](source/figures/fig2_1.pdf "Taxonomic diversity in A. filiculoides Wild samples"){#fig:fig2_1}

### _Nostoc azollae_ is the most abundant endophyte of _A. filiculoides_
Taxonomic identification revealed a conserved and plant-specific microbial community associated with _A. filiculoides_ (Fig. 1a L, P).
Most rRNA hits were assigned to either fern chloroplasts, Viridiplantae nuclei, or cyanobacteria.
Cyanobacteria-derived rRNA sequences were more abundant in the enriched leaf pocket contents than in the whole plant samples.
Fern mitochondrial rRNA was absent from the database and instead assigned to the order Ricketsiales (class Alphaproteobacteria) that was systematically present in all whole plant Azolla samples, yet less abundant in leaf pocket enriched samples.
Cyanobacteria-related sequences were the most abundant in all fern samples making up approximately 60-75% and 45% of the rRNA hits in (L) and (P) samples, respectively (Fig. 1a L, P).
Accuracy of assembled 16S rRNA genes was confirmed by aligning the rRNA assemblies assigned to cyanobacteria to the _N. azollae_ 16S rRNA gene (NCBI reference sequence: NR_074259.1): multiple sequence alignment with ClustalW showed over 99.5% identity over the full length of the alignment.
Results therefore confirmed that _N. azollae_ is the primary symbiont of _A. filiculoides_.

![Relative abundance of orders within cultured species of Azolla (Table 1) and ditch samples of _A. filiculoides_ (natural and sterilized). Taxonomy was assigned to rRNA fragments found in single reads by RiboTagger (RiboTagger) and to rRNA genes assembled with EMIRGE by Mothur (EMIRGE). Unclassified orders or those originating from Viridiplantae nuclei, fern plastids and cyanobacteria are not shown. Environmental sequencing data originated from _A. filiculoides_ leaf pocket-enriched samples (L) and whole plants (P) in biological triplicates. Sequence reads from cultured ferns were processed as subsets of 10 M and 30 M reads.](source/figures/fig2_2.pdf "Azolla genus wide microbial taxonomy"){#fig:fig2_2 width=100%}

### Rhizobiales are constitutive members of the microbiome in natural and cultivated Azolla species
To help reveal microorganisms associated at low abundance with _A. filiculoides_ from the ditch, we removed rRNA hits derived from chloroplasts, Viridiplantae nuclei, mitochondria, cyanobacteria and unclassified sequences (Fig. 2, Environmental).
RiboTagger found more OTUs in nearly all samples than did EMIRGE.
Only EMIRGE, however, found Metazoa 18S rRNA in all Azolla plant (P) and one leaf pocket-enriched (L) samples.
These rRNA genes all mapped to Stenopelmus rufinasus, a weevil specialized in feeding on Azolla [@Hill1998].
All five assembled Metazoa rRNA genes and Genbank reference FJ867794.1 were trimmed to corresponding lengths and aligned: 98.2% of the 1200 bp multiple sequence alignment was identical.
Detection of the weevil and the perfect assembly of the _N. azollae_ rRNA confirmed the accuracy of EMIRGE assemblies and subsequent taxonomic assignments by Mothur.
The bacterial orders Rhizobiales and Burkholderdiales were found enriched in (L) samples by both methods at 2% and 1% abundance, respectively, and in all but one (L) sample by RiboTagger (Fig. 2, Environmental).
For the cultured Azolla species, short-read sequencing data obtained from seven different species were also analyzed using EMIRGE and RiboTagger (Table 1).
Cultured ferns included _A. filiculoides_ originating from the same ditch as the environmental sample but cultured for two years so as to be devoid of _N. azollae_ (=_A. filiculoides_-Sterilized).
The most abundant taxonomic assignments from DNA of cultured Azolla species were Viridiplantae nuclei, chloroplast and cyanobacteria (Fig. S1); these were removed so as to reveal taxa present at a lower abundance (Fig. 2, Cultured).
Members of Burkholderiales, present in ditch samples of _A. filiculoides_, were infrequently observed in cultured Azolla species.
However, they were particularly prominent in _A. filiculoides_-Sterilized.
Similarly, Caulobacteriales were infrequently observed in cultured Azolla.
In contrast, Rhizobiales were observed in all cultured and environmental Azolla samples, including those devoid of _N. azollae_ (Fig. S2, _A. filiculoides_-Sterilized).
Azolla accessions from IRRI had been cultured for many years (Table 1), raising the likelihood that their microbiomes were considerably altered from when first collected in their natural environment.
The persistent occurrence of Rhizobiales in environmental, cultured and sterilized ferns, however, suggested that these bacteria are closely associated with the fern and possibly have an added ecological function in the Azolla-Nostoc symbiosis.
Detection of the rRNA genes from Rhizobiales in DNA from _A. filiculoides_-Sterilized further predicted that the long-read nuclear genome assemblies from this plant likely contained scaffolds of persistent bacterial endophytes.

![Recruitment summary on bacterial scaffolds obtained by Celera or Falcon assemblies of the _A. filiculoides_ genome. Short reads from cultured Azolla species and environmental samples, A.filiculoides leaf pocket enriched and whole plant (L,P) and water control (W), were recruited onto assembly scaffolds including the _A. filiculoides_ chloroplast as well as on to _E.coli_ (GCA\\_000005845.2\\_ASM584v2) and _N. azollae_ (NC\\_014248.1) reference genomes. Bacterial scaffolds were from _A. filiculoides_ genome assemblies computed with either Celera (C) or Falcon (F) pipelines, length of the scaffolds is in megabases (Mb). Read counts were normalized per kb with colour coding in linear scale (top panel) illustrating the dominance of DNA from chloroplast and _N. azollae_. Normalized read counts were further scaled logarithmically (bottom panel) to reveal differences between the negative control _E. coli_ and presence calls for scaffolds belonging to the bacterial genera _Hydrocarboniphaga_, _Rhizobium_ and _Shinella_.](source/figures/fig2_3.png "Read recruitment heatmap"){#fig:fig2_3 width=100%}

### Near full-length genomes of two novel Rhizobiales species in assemblies of the _A. filiculoides_ genome are present in all Azolla species
The Falcon and Celera assemblies from the _A. filiculoides_-Sterilized were scanned for bacterial scaffolds (presence of 16S rRNA) with RNAmmer; scaffold taxonomy was then assigned using Mothur if they were longer than 0.1 Mb (Table 2).
Both assemblies reproducibly yielded scaffolds from the genera _Shinella_ and _Rhizobium_ (Rhizobiales).
To differentiate true endophytic partners from bacterial infections due to culture treatments or DNA extractions, recruitment analyses were carried out: short reads of all cultured species and environmental samples were mapped to the bacterial scaffolds extracted from the nuclear genome assemblies, then only hits with an identity over 97% were counted and hit frequency normalized for scaffold length, thus generating a heat map (Fig. 3).
Assuming that the scaffolds were not chimera from faulty assembly, restricting the recruitment to reads mapping at over 97% identity allowed inferring from recruitment frequencies whether organisms with a specific scaffold were present in a given sample and in significant abundance.
Scaffolds assigned to Ralstonia (Burkholderiales) were most abundant in samples of _A. filiculoides_-Sterilized, whilst absent in other species (Fig. 3).
Three other bacterial genera present in multiple Azolla species stood out with substantial counts: _Hydrocarboniphaga_ (Nevsikiales), and _Shinella_ and _Rhizobium_ (Rhizobiales).
Then, considering the averaged and normalized frequency at which reads mapped with such high identity along the scaffolds we predicted that scaffolds with reproducibly the same mapping frequency in samples likely originated from the genome of the same bacteria.
The three _Rhizobium_ and two _Shinella_ scaffolds had the same relative frequencies of recruitment in each sample, indicating that they each originated from one species of _Rhizobium_ and _Shinella_, respectively.
Scaffolds from the Rhizobiales were on average more frequently mapped by reads from the leaf pocket-enriched (L) samples than from whole plants (P); the recruitment frequency, therefore, located the bacteria from the _Rhizobium_ genome in the leaf pockets (Fig. S3).
To evaluate their representation in the data over the full length of their genomes, short reads of all cultured and environmental samples were mapped to the longest scaffolds of these bacterial genera (Fig. 4).
High identity reads (100%) mapped with high frequency to the _N. azollae_ genome, revealing that the published _N. azollae_ genome is the same species as that found in _A. filiculoides_ from the Dutch ditch.
Absence of reads from the _A. filiculoides_-Sterilized samples mapping to _N. azollae_ confirmed tha
t these plants were devoid of cyanobacteria.
In the genomes that were absent from these samples, sporadic loci still mapping reads with high identity were localized at highly conserved genes such as rRNA.
In contrast, the 3.2 Mb _Rhizobium_ and 4.9 Mb _Shinella_ scaffolds, were represented over the full length of the scaffolds in all fern samples.
High identity reads were most abundant in _A. filiculoides_ environmental and cultured samples compared to other Azolla species; nevertheless, these scaffolds were mapped with over 90% identity over their full length in all Azolla species.
The _Hydrocarboniphaga_ scaffold was only highly represented in fern samples in an area confined to the end of the scaffold; this scaffold therefore was likely an artefact of assembly fused at its end to _A. filiculoides_ genomic DNA (Fig. S4).

![Recruitment analysis using short reads from cultured and environmental Azolla and water samples onto reference genomes of _N. azollae_ (GenBank CP002059.1), _E. coli_ (GCA\\_000005845.2\\_ASM584v2), the _Shinella_ scaffold and two _S. meliloti_  genomes (AL591688.1 and AKZZ01000000 respectively). Reads were from DNA of cultured ferns or from the ditch samples as in Figs. 1-3 (see also Table 1). All reads were mapped with bowtie (options `–very-sensitive`) and identity scores were calculated with a custom script (Materials and Methods). Reads were binned according to identity score and position on the respective genome, then counted per 50 kb for normalization, counts were log10 transformed.](source/figures/fig2_4.pdf "Read recruitment to genomes of interest"){#fig:fig2_4 width=100%}

### The Rhizobiales endophytes of _A. filiculoides_ contain denitrification enzymes
To explore possible functions of bacteria from the Azolla microbiomes identified during our recruitment analysis, the combined _Rhizobium_ and combined _Shinella_ scaffolds were submitted for annotation to RAST [@Aziz2008; @Overbeek2014], which computed that the most similar organisms were, respectively, _Agrobacterium tumefaciens_ and _Sinorhizobium meliloti_ (Rhizobiales).
To evaluate the relatedness of our _Sinorhizobium_-like genome with the two known _S. meliloti_ genomes (GenBank AL591688.1 and AKZZ01000000), we mapped reads from environmental samples and _A. filiculoides_-Sterilized to these genomes (Fig. S4).
Whilst the _Sinorhizobium_-like genome was well represented in all Azolla samples, reads of all ditch and cultured fern samples mapped less efficiently to both known _S. meliloti_ genomes.
The _Sinorhizobium_-like endophyte was thus determined to be a distinct species from _S. meliloti_.
Similarly, the _Agrobacterium_-like endophyte persistently detected in all Azolla ferns (Fig. 4) proved distinct from known _Agrobacterium_ tumefaciens strains.
Analyses of N-cycle coding genes revealed that both Rhizobiales genomes were lacking the N~2~-fixing nitrogenase but instead encoded proteins from the denitrifying pathway (Fig. 5; Table S2).
The _Sinorhizobium_-like genome contained intact nitrite reductase, nitric oxide reductase and their accessory proteins (Figs. S4, S5).
The _Agrobacterium_-like genome did not contain nitrite reductase but contained nitric oxide reductase and nitrous oxide reductase features.
Closer inspection of the locus and protein alignment, however, revealed insertions of mobile elements in key genes of the nor and nos operons (Figs. S6, S7).
hizobiales endophytes hosted by Azolla ferns, therefore, did not contribute to N~2~-fixation but may have released N~2~O and possibly also N~2~.

![Nitrogen metabolism pathway comparing merged Agrobactrium-like, _Sinorhizobium_-like genomes and _N. azollae_. The KEGG database was used to retrieve proteins from the closest relative that was manually annotated [@Kanehisa2010], then the proteins were BLAST-aligned to the merged scaffolds using the RAST/SEED viewer tool [@Overbeek2014]. The KEGG-map of the nitrogen metabolism pathway was used to colour-in proteins detected in the merged scaffolds named after the closest relative computed by RAST, or in the _N.azollae_ genome using the KEGG/NCBI annotation: _Agrobacterium_-like (yellow), _Sinorhizobium_-like (red) and _N. azollae_ (green).](source/figures/fig2_5.png "Nitrogen metabolism pathway of Azolla filliculoides associated microbes"){#fig:fig2_5 width=100%}

### _A. filiculoides_ lacking cyanobacteria, but with the Rhizobiales present, neither fix nitrogen nor release detectable amounts of N~2~O
Nitrogen-fixation in surface-sterilized _A. filiculoides_ was examined by supplying ^15^N~2~ at mid-day for 2 h (Fig. 6a), when both CO~2~ and N~2~ fixation peak [@Brouwer2017c].
^15^N~2~-fixation was not significant in _A. filiculoides_-Sterilized (Fig. 6a –Cynao+N).
N~2~-fixation was inhibited by N-fertilizer in the medium required to sustain growth of _A. filiculoides_-Sterilized (Fig. 6a, compare +Cyano-N with +Cyano+N), but _A. filiculoides_ with _N. azollae_ fixed significant amounts of nitrogen already after 2 h (Fig. 6a, +Cyano+N).
When examining ^15^N~2~ fixation after one diel cycle of 24 h, ^15^N of the biomass was still not significantly increased in _A. filiculoides_-Sterilized compared to the boiled control whilst it reached on average 362 in ferns with cyanobacteria (Fig. S8).
Endophytic Rhizobiales in _A. filiculoides_-Sterilized, therefore, did not fix N~2~.
This result was consistent with the absence of the N~2~-fixing pathway in our Rhizobiales genomes (Fig. 5).
In air without ^15^N~2~ added, biomass15N of the ferns with _N. azollae_ in the absence of N-fertilizer was much higher than with fertilizer (Fig. 6b, +cyano-N versus +cyano+N), consistent with inhibition of N~2~-fixation on media with 2 mM NH~4~NO~3~ in Fig. 6a.
The most negative 15N in _A. filiculoides_-Sterilized confirms absence of N~2~-fixation in these ferns (Fig. 6a).

![Is N-cycling inside _A. filiculoides_? _A. filiculoides_-Sterilized symbionts were cultured in sterile medium with 2 mM NH~4~NO~3~ (-cyano+N) and compared to surface-sterilized _A. filiculoides_ (with _N. azollae_) growing in sterile medium without NH~4~NO~3~ fertilizer (+cyano-N) and with 2 mM NH~4~NO~3~ (+cyano+N). (a) Midday uptake of ^15^N~2~ after 2 h exposure to ^15^N~2~ enriched air. (b) ^15^N in the biomass of the clonal _A. filiculoides_ as in (a) but without ^15^N~2~ enriched air and NH~4~NO~3~. (c) Non-sterile Azolla containing cyanobacteria (+cyano) were used to detect N~2~O released after 6 h comparing light and dark, and +/-N medium. (d) N~2~O concentration after 6 h incubation in the dark at the end of the night in micro-aerobic (about 10\\% v/v O~2~) air-space from _A. filiculoides_ as in (a), non-sterile Azolla containing cyanobacteria growing on +N medium and from +N medium. Means with standard deviations for n=3 are shown. *, indicates significant difference with –cyano ferns (a), with –N medium (c) and with Medium control (d) with P<0.05, Student’s t-test.](source/figures/fig2_6.png "Nitrogen cycling in and on Azolla filiculoides"){#fig:fig2_6 width=100%}

N~2~O release was robustly detected when assayed after 6 h in darkness using non-sterile Azolla on medium with 2 mM NH~4~NO~3~, but not on medium without nitrogen fertilizer (Fig. 6c), even after much longer than 6 h incubation (data not shown).
Dependence of N~2~O release on medium with N suggested that if any N~2~O was synthesized in the leaf pockets it would be efficiently converted into N~2~.
In contrast to non-sterile _A. filiculoides_, N~2~O release was not detected when _A. filiculoides_-Sterilized were grown used on medium with N-fertilizer after 6 h darkness at the end of the night and in a micro-oxic air space (Fig. 6d).
N~2~O release from non-sterile _A. filiculoides_ therefore likely originated from bacteria loosely associated with the fern surface, not from the endophytes.
Results were consistent with the low abundance of the denitrifying Rhizobiales endophytes (Fig. 2).

## Discussion

### _Nostoc azollae_ is abundant and the only cyanobacterium that fixes N~2~ in _A. filiculoides_
N. azollae in _A. filiculoides_ from the present study and the published strain from Stockholm [@Ran2010] were the same species based on the above 97% identity of their rRNA.
did not detect any rRNA from another cyanobacterial species suggesting that in the Utrecht ferns, _N. azollae_ was the only abundant cyanobacterium in the leaf pockets; Fig. 6 and Fig. S8 further demonstrated that _N. azollae_ was responsible for N~2~ fixation in the ferns.
The large number of reads that mapped to the _N. azollae_ genome with less than 100% identity in the recruitment analyses (Fig. 4) were likely explained by natural variation in bacterial populations and activity of insertion elements in _N. azollae_ [@Vigil-Stenman2015].
Previous reports suggesting that several species of cyanobacteria may inhabit the leaf pockets [@Gebhardt1991] may have described very low abundance cyanobacteria not detected by our analyses which revealed bacteria with a relative rRNA abundance at relative detection limit of 0.2 %.
Our analyses confirmed presence of less abundant gram-negative eubacteria in leaf pockets of _A. filiculoides_, in particular, that of an _Agrobacterium_ strain [@Plazinski1990].

### Two novel candidate bacterial species from the Rhizobiales are persistent endophytes of all Azolla species
Our data supports that Azolla has control over the bacterial community assembly within its closed leaf pockets.
Firstly, the bacterial community of the surrounding ditch water was dominated by Proteobacteria, which is typically found in Dutch ditches [@El-Chakhtoura2015], and had no overlap with Taxa within the Azolla leaf pocket.
Secondly, different Azolla species cultured under the same conditions housed reproducibly different assemblages of microbial endophytes (Fig. 2, cultured).
Thirdly, Rhizobiales endophyte genome scaffolds were recovered from sequencing nuclear preparations of _A. filiculoides_-Sterilized; this Azolla strain had been grown on erythromycin then cultured in sterile conditions for over two years (Fig. 4).
In accordance, _Arabidopsis_ leaf endophytes were shown to depend on the plant genotype, thus, demonstrating that the plant host controls the assembly of endophytic bacterial communities [@Horton2014]; gene loci that influenced the bacterial communities, for example, encoded regulators of viral reproduction, pectin metabolism and trichome development.
The Azolla control over the leaf pocket bacterial community may also depend on the presence of cyanobacteria, since Burkholderiales bacteria were more abundant in _A. filiculoides_-Sterilized (Fig. 2 A).
The more general lesson learnt was that bacterial scaffolds in genome assemblies may represent persistent endophytic bacteria and therefore deserve attention.
Rhizobiales bacteria were found in all species of Azolla examined, despite the low proportion of reads with 16S rRNA sequences when sequencing all DNA extracted from the ferns or leaf juice compared to when sequencing PCR amplified rRNA genes.
The difference in the 10 and 30 M read-based taxonomy assignments using EMIRGE/Mothur in Fig. 2 and no saturation in Fig. 1b attest to this limitation.
Rhizobiales were also reproducibly detected in the leaves of several species from the carnivorous angiosperm _Genlisea_ using the meta-transcriptomics approach, which will yield proportionally more rRNA sequences because of the high accumulation of rRNA in RNA extracts [@Cao2015].
The long-read assembly of bacterial scaffolds combined with recruitment analyses, however, allowed a very high resolution of the taxonomic assignments in the present study.
With RAST, closest relatives were computed scoring homologies of gene candidates predicted by GLIMMER3 with a set of universal proteins and 200 unduplicated proteins [@Overbeek2014].
Recruitment analyses further refined this and showed that the _Sinorhizobium_-like endophytes in _A. filiculoides_ were not the _S. meliloti_ species known (Fig. S4), yet were above 90% identical over the genome length when comparing the differing Azolla species (Fig. 4).
Furthermore, calculating read counts per kb in Fig. S3 quantified enrichment of Rhizobiales in leaf-pocket content compared to plant samples, thus locating _Agrobacterium_-like bacteria preferentially in the leaf pockets.
Unlike the cyanobacteria in the leaf pockets, the Rhizobiales endophytes did not fix N~2~ and were present in much lower abundance as judged from the recruitment analyses.

### A possible role for denitrifying Rhizobiales of the Azolla metagenome
Persistent Rhizobiales endophytes with denitrifying pathways suggested there may be some wasted cycling of the fixed nitrogen that is not likely to be of direct benefit to Azolla (Fig. 5).
In the absence of N fertilizer Azolla will thrive entirely on N~2~ fixed by _N. azollae_; this explained the low δ^15^N of the fern biomass grown without N fertilizer compared to legume biomass reported earlier [Fig. 6\; @Hipkin2004] and suggested that growth of Azolla was not limited by nitrogen.
Rhizobia are known epiphytes of cyanobacteria heterocysts [@Stevenson2006].
Possibly, the heterotrophic Rhizobiales help to lower the massive amounts of O~2~ released from leaf cell PSII activity at daytime in the leaf pockets, thereby preserving nitrogenase efficiency inside the heterocysts.
Rhizobia may have adapted to survive the micro-oxic environment they create, particularly at night, by respiring nitrate or nitrite.
_Bradirhizobium japonicum_ in soybean nodules is responsible for the bulk of N~2~O emissions when flooding soybeans: plants nodulated with _B. japonicum_ mutants with a defect in NapA nitrate reductase producing nitrite emitted less N~2~O whilst plants with a defect in N~2~O reductase emitted more N~2~O [@Tortosa2015].
In Azolla, as in legumes, therefore, the denitrification pathway may present an adaptive advantage even though it may constitute futile cycling: survival of the bacteria when O~2~ levels are low.
Direct N~2~O release from surface-sterilized Azolla containing the Rhizobiales genomes could not be detected in this study, however, even in micro-oxic conditions and after a prolonged night.
Possibly, endophyte communities co-evolve with Azolla, and the metagenome is the unit that undergoes selection by the environment.
This would be demonstrated if phylogenetic relationships of Azolla and its endophytes were to mirror one another, and if the endophytes were shown to be transmitted vertically upon sexual reproduction of Azolla by way of spores.
Vertical transmission has been demonstrated for _N. azollae_ in _A. filiculoides_ [@Ran2010], and it is entirely possible that the rhizobia reported here are similarly transmitted together with _N. azollae_ the megasporangiate sori of _A. filiculoides_ [@Carrapico1991; @Zheng2009].
Phylogenetic studies are underway to verify this because, if true, it would imply that crop breeding approaches would have to consider endophytic communities.

### Nitrification: how could nitrate and nitrite be formed from the NH~4~+ released by _N. azollae_?
Because bacterial endophytes from rice roots contained the AmoA (pfam 05145) ammonia monooxygenase [@Sessitsch2012], which converts ammonium into nitrate, it is plausible that Azolla endophytes still awaiting characterization may be capable of converting the ammonium released by _N. azollae_ into nitrate.
Alternatively, many N~2~-fixing plants are capable of phototrophic nitrification [@Hipkin2004].
In several leguminous plants, malonate is transformed via monoamide to 3-nitropropionic acid (3-NPA) and then to nitrate and nitrite [@Francis2013].
3-NPA is an inhibitor of mitochondrial succinate dehydrogenase (E.C. 1.3.5.1) and is therefore a strong antigrazing compound.
It has been shown to accumulate at high levels in aquatic plants that fix N~2~ (e.g., Lotus), and is inactivated by the by 3-NPA oxidases detected in a leguminous herb and characterized in _Pseudomonas aeruginosa_, _Burkholderia phytofirmans_, and fungi [@Nishino2010; @Francis2013; @Salvi2014].
It will be important to decipher whether nitrification reactions occur within the leaf pocket or inside the fern cells.
The combination of nitrifying and denitrifying endophytes could permit _Azolla_ to cope with surplus levels of NH~4~+ from _N. azollae_ or micro-oxic ditch waters when phosphate availability is limiting and, therefore, contribute to defining the aquatic fern’s ecological niche.
