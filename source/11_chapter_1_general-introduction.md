
<!-- Start new part of the book, the scientific chapters (and gen-intro) -->
<!-- Start page numbering here, so that part II starts at page one in the table of contents -->
\pagenumbering{arabic}
\setcounter{page}{1}
\part{Chapters}

<!-- line numbers, to be removed in final version -->
\resetlinenumber
\linenumbers

<!-- chapter title and bla bla -->
\chapter{A hitchhikers guide to symbioses, \textit{Azolla}, its symbionts, and why people care}
\label{general_intro}

\addthumb{General Introduction}{\Large{I}}{white}{gray}

\pagestyle{chapter}

\footnotesize
Laura W Dijkhuizen^1^
\scriptsize

1. Molecular Plant Physiology Department, Utrecht University, Utrecht 3584CH, The Netherlands

\newpage
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

# Symbioses

> _“A system is never the sum of its parts it's the product of their interaction.”_
– Russell Ackoff (professor of systems sciences)

## A system perspective

When imagining an ecosystem, one typically thinks of a forest with trees, animals, and insects.
Perhaps also a stream and some fish; all thriving as a balanced part of a larger whole.
The concept emphasises the abundance and complexity of interaction within the larger system, rather than the individualistic existence of the loose parts.
Yet, when an average person imagines a biological experiment, they think of lab coats, petri dishes, and perhaps microscopes.
They are not wrong; science has thrived under reductionism.
Scientific experiments often strive to control one variable at a time to isolate its effects.
All other variations are reduced by working with one species or one strain at a time, dislodged from its natural environment to prevent it from meddling with the experiment.
We, scientists, call this: 'controlled conditions.'
The ultimate goal is to gain mechanistic insight into the workings of a biological system, reasoning that if we know the function of all its parts, we then know the system.

The reductionist dogma yielded considerable advances in biological research; I wouldn't dream of debating this.
But I will argue that it occasionally falls short in encompassing emergent properties of a larger whole.
The complexity of real-world biology does not always allow for isolating one variable from the rest of the system.
Nor does changing one variable in a system always lead to robust change.
For examples of the former, this thesis describes such a system.
The latter, I find exemplified in recent attempts at microbiome editing.
A microbiome is the collection of all microbial organisms associated with any organ or organism.
Such a collection often contains millions of cells of hundreds of strains if not more.
I think it is very optimistic to take one of these strains, edit it in some often genetic way, and expect robust change and plenty of examples in literature support this opinion.
<https://www.nature.com/articles/s44222-023-00072-2>

Even within the confines of a single cell, the reductionist view on biology is subject to scrutiny.
Nicholson (2019) argues that perhaps we should abandon our view of the cell as a mechanical reductionist entity to be studied through its molecular components.
Instead, we should consider the cell as a complex, adaptive system where interactions and emergent properties are crucial for its function.
I argue not for the complete abandonment of mechanistic research, but for complementing it with a systems biology perspective.
A task well suited for biologists, who are trained from the onset to think at varying scales; from molecule to ecosystem.
In fact my bachelor studies were organised this very way.
Yet, somehow, something so obvious to a first-year biology student becomes an afterthought in reductionist scientific practice; an interesting speculation for the discussion.

Perhaps the study of symbioses takes place in between the ambition of full system understanding, and the practice of mechanistic researching pathways.
The methodology of the reductionist dogma remains the gold standard that we want to adhere to, also in this work.
But always asking what it means for a system as a whole.
Or, more often than not, forced to work with the system as a whole.
Whether that system is an ecosystem, a cell, or, as is in this thesis: a symbiosis.
By definition, a symbiosis is a long-term interaction of two or more organisms.
They often can be categorised in:

* mutualism: when all partners benefit
* commensalism: when one partner benefits, but does not harm others
* amensalism: when one partner is unaffected, but still at the cost of another
* parasitism: when one partner benefits at the cost of the others
* competition: when all partners are harmed by the interaction.

The general public often assigns a positive connotation to the concept of symbiosis, referring to the first two categories.
This is not always practical, for the type of interaction is often unknown at first.
Hence, the time span of an interaction is a more robust approach.
In this thesis, symbiosis typically refers to the first two categories; congruent with the general sentiment of the word.
The latter three categories are thought of as general ecological interactions rather than symbioses, in the context of this document.

## Symbiosis breeding

The original premise of this PhD project includes thoughts on symbiosis breeding.
The organisms of choice here, are part of an obligate symbiosis focused on nutrient acquisition; specifically nitrogen.
We reasoned that molecular pathways of host and symbiont would be intricately interconnected.
Hence, any breeding efforts of the host plant should not be limited to the plant physiology and genomics, but include those of its symbiont.
For symbiosis traits, breeding a symbiont should perhaps take precedence over breeding the host.
We advocated then, that breeding a functionally intertwined unit of organisms requires that systems biology perspective.
A perspective that integrates ecological, physiological and (meta)genomic data to understand and eventually manipulate a plant-microbe symbiosis.

## The holobiont concept

The holobiont concept is a recent proposition in evolutionary jargon.
It proposes to think of a host and a symbiont as one unit of evolutionary selection.
This is not a far fetch in the case of an obligate symbiosis where a microbiome is actively transferred to subsequent host generations.
It might be odd even, to argue that certain genetic material should be regarded as a separate evolutionary unit based solely on the compartment it is housed in.
We rarely find this useful for organelles either, although examples do exist in literature.
The holobiont concept paves the way for some interesting thought experiments.
Could a fast-evolving bacterial section of the hologenome (all genetic material of a holobiont) provide flexibility to the rigid host genome.
This may explain the fast adaptations of microbiomes to their hosts.

After advocating a systems biology perspective on symbiosis research, the holobiont concept seems fitting in this work.
Yet, the concept is also critisised.
The holobiont is also argued to be a romantic over-simplification of a set of complex interactions.
Holobiont members may interact beneficially as well as antagonistically.
Additionally, a lack of consistency in a species consortium may challenge the evolutionary pressure exerted on them as a whole.
Critics of the concept suggest that traditional ecological and evolutionary frameworks suffice for what could be called a holobiont.
Additionally, they argue that existing frameworks are better equipped to handle nuances and conflicts between symbiosis partners.

I have not decided on the matter yet, although I am inclined to agree with the critics for most scenarios.
Yet, if we can occasionally find use in thinking of a single gene as an evolutionary unit, then perhaps the holobiont perspective has use as well.
Even if that is only in specific cases.
It seems unproductive to me, to use holobiont as a buzz-word, to elevate a consortium of organisms above others.
In this thesis my colleagues and I do use the word occasionally.
Take it with a pinch of salt.

# The _Azolla_ symbiosis

This work discusses the genomics and metagenomics of a specific symbiosis: that between the floating fern genus _Azolla_, and a cyanobacterium _Nostoc azollae_.
The Cyanobacterium supplies the symbioses with a surplus of nitrogen fixed from the air.
The symbiosis floats on water.
_Azolla_ its aquatic lifestyle makes the fern highly dependent on fresh water.
Even its name is derived from this property, 'Azo' is greek for 'dry' and 'allyo' for 'kill'.
The fern spreads horizontally over the water surface, darkening the water column.
This property makes _Azolla_ as infamous under ecologists, as it is famous in symbiosis research.
Bigger plants break irregularly into smaller ones, genetically identical, but physically separate; forming a big green floating mat.
_Azolla_ mats are known for their high growth rate and high protein content.
A mat can grow so spectacularly fast, that _Azolla_ is thought to have overgrown the entire north pole for some time in geological history.
This "_Azolla_ event" is associated with a steep decline in global CO2 concentration in the air.
Within human history, _Azolla_ has traditionally been used in rice pady fields.
Its main function was to prevent toxic cyanobacteria from growing in the water, any surplus was feed for animals.
Some of today's agricultural challenges seem to be a perfect fit for _Azolla_: limit arable land, nitrogen fertilizer excesses, and protein shortage.
_Azolla_ is an amazingly interesting plant, in this section I'll elaborate shortly on all these statements.

## _Azolla_ physiology

_Azolla_ stems spread horizontaly over the water surface.
At stem nodes, leaves and roots are attached.
_Azolla_ leaves are highly adapted to their function.
They are bi-lobed, directed either up- or down-ward.
The lower lobe is razor-thin, translucent-looking and concave.
It lies on the water like a boat, suspending the stem and upper leaf lobe above.
The upper lobe is thick; almost balloon-like, and typically dark green.
Inside this the upper lobe, a special organ houses the symbiotic bacteria.
The leaves typically grow in a compact cabbage-like fashion; giving the whole plant a fish-scale appearance.

All organs find their origin at the tip of the stem, at the shoot apical meristem (SAM).
At the SAM, leaves, roots and sporocarps (the ferns reproductive structures) find their origin.
The SAM also harbours a small colony with motile filaments of the cyanobacterium _T. azollae_.
Both leaves and sporocarps encapsulate part of the starting colony during growth.
This process ensures that all leaves have a colony of the symbiont.

Azolla roots can be observed hanging loosely in the water like a thin curtain.
On timelapses, the roots were seen swirling and curling.
Roots of individual plant fronts grabbed onto each other like rugby players locking shoulders in a scrum
This way, individual plants formed a cohesive mat, keeping together.
I suspect this phenomenon may help in creating favourable conditions for the symbiosis.
It may help in stratifying the water column, keeping nutrients from dying plants close to the plant roots for re-absorption.

Interestingly, Azolla roots respond distinctly to typical plant hormones compared to flowering plants.
Roots were likely invented twice in plant-history: in lycophytes and in ferns.
The fern-invented-roots were passed down to seed-plants.
However, not all roots will have developed the same since their original invention.
In seed-plants, the hormone cytokinin promotes cell division in shoots, and regulates differentiation growth in roots.
In contrast to the typical response, _Azolla_ roots' cell division is promoted by cytokinin [@DeVries].
This finding suggest that Azolla roots have an origin as a shoot structure.
They are analogous to plant roots; similar in appearance but separate in origin.

The specifics of the shoot-origin of _Azolla_ roots are not of major consequence to this work.
It does highlight and illustrate that the evolutionary history of _Azolla_ deviated from that of seed plants a very long time ago.
Educated guesses made with a seed-plant background, may be false more often than one thinks.
Now let me also express my dislike for the term "primitive plants".
As if ferns have not diversified, adapted and evolved since their origin.
I hope this thesis will help in appreciating the intricacies of the _Azolla_ symbiosis life cycle.
We can discuss "primitiveness" further compared to the brute force of non-polinated flowers or the extravaganza of a magnolia.

## Cyanobacterial symbiosis

Cyanobacterial symbioses are widespread and diverse.
They span various ecosystems: like marine environments, freshwater systems, and terrestrial habitats.
Cyanobacteria form mutualistic associations with a wide range of hosts, including plants, fungi, protists, and even animals.
In marine systems, symbiosis partners can be sponges or diatoms.
In fresh water systems, the _Azolla_ symbiosis is a prime example.
Terrestrial hosts can by cycads (plants), mosses, but also lichens (fungi).
Even some animals can be hosts: flatworm  _Convoluta roscoffensis_ can host a cyanobacterial symbiont.
These symbioses are mostly not obligate; most cyanobacteria can live independently from their host.

The _Azolla_-_Nostoc_ symbiosis is perhaps most related to moss-cyanobacterium symbioses.
Moss-cyanobacterium symbioses are particularly present in boreal and temperate regions.
Host mosses like _Sphagnum_ and _Pleurozium schreberi_ harbour nitrogen-fixing cyanobacteria, primarily from the genus _Nostoc_ and _Anabaena_.
The cyanobacteria provide their host mosses with nitrogen by fixing atmospheric nitrogen into ammonia through the enzyme nitrogenase.
This relationship is a big competitive advantage in nutrient-poor environments.
The symbiosis significantly contributes to the nitrogen budget and supports the growth of both mosses and the surrounding plant community.
[Moss-cyanobacteria associations as a novel source of biological N2-fixation in temperate grasslands](https://link.springer.com/article/10.1007/s11104-020-04695-x)
In moss-cyanobacteria associations, the cyanobacteria are often acquired horizontally from the environment each generation.
The cyanobacteria can also live without a host in these environments, and culturing and innoculation protocols are established.
This is unlike the _Azolla_-_Nostoc_ symbiosis, where cyanobacteria are transferred vertically through reproductive structures.
[Rousk: Unraveling host–microbe interactions and ecosystem functions in moss–bacteria symbioses](https://academic.oup.com/jxb/article/73/13/4473/6612780).

In addition to nitrogen fixation, these symbioses also influence the broader ecosystem processes.
The fixed nitrogen not only supports the mosses but also enriches the soil after part of the moss dies, benefiting other plants and microorganisms in the ecosystem.
[Moss-cyanobacteria associations as a novel source of biological N2-fixation in temperate grasslands](https://link.springer.com/article/10.1007/s11104-020-04695-x)
The presence of cyanobacteria enhances the mosses' ability to retain water and nutrients, thereby stabilizing soil and preventing erosion.
This mutually beneficial relationship exemplifies the intricate connections between plants and microbes.
It examplifies the ecological importance of cyanobacterial symbioses.
Initiation of these interactions take a complex web of molecular signaling and metabolic exchange.
[The moss traits that rule cyanobacterial colonization](https://academic.oup.com/aob/article/129/2/147/6386096)

Cyanobacteria associated with mosses, and also with Azolla, are often part of the Nostocaceae family.
The Nostocaceae family comprises several genera of cyanobacteria known for their filamentous, colony-forming structures and their ability to fix nitrogen.
The family includes genera such as _Nostoc_, _Anabaena_, _Trichormus_, and _Cylindrospermum_.
These genera share common features like the presence of specialised heterocysts cells that fix nitrogen under aerobic conditions.

Phylogenetic studies have shown that the relationships among these genera are complex.
Within a single genus, significant genetic diversity can be observed.
[Modern taxonomic revision of planktic nostocacean cyanobacteria: a short review of genera](https://link.springer.com/article/10.1007/s10750-009-0030-4)
Specifically, _Anabaena_ and _Nostoc_ are closely related but exhibit distinct ecological and morphological adaptations.
[Morphological, biochemical and molecular characterization of Anabaena, Aphanizomenon and Nostoc strains (Cyanobacteria, Nostocales) isolated from Portuguese freshwater habitats](https://link.springer.com/article/10.1007/s10750-010-0572-5)
_Anabaena_ is often found in both freshwater and saltwater environments and can form toxic blooms.
_Nostoc_ is more commonly associated with symbiotic relationships in terrestrial and freshwater habitats

Recent molecular analyses have provided deeper insights into the evolutionary relationships within the Nostocaceae family.
These studies have utilized multiple genetic markers to elucidate the phylogeny of these cyanobacteria.
The findings highlight the importance of horizontal gene transfer and genetic recombination in shaping the genetic diversity of Nostocaceae, contributing to their adaptability and ecological success across various environments
[Morphological, biochemical and molecular characterization of Anabaena, Aphanizomenon and Nostoc strains (Cyanobacteria, Nostocales) isolated from Portuguese freshwater habitats](https://link.springer.com/article/10.1007/s10750-010-0572-5)
[Modern taxonomic revision of planktic nostocacean cyanobacteria: a short review of genera](https://link.springer.com/article/10.1007/s10750-009-0030-4)

## _Nostoc azollae_ or _Trichormus azollae_

_Azolla_ species form a unique symbiotic relationship with _Trichormus_ azollae_; the cyanobacterium resides in specialized leaf cavities of the fern.
The symbiosis main function, from the host-plant perspective, is that T. azollae_ sequesters di-nitrogen gas from the air and shares this with the host.
Several papers claim to have cultured _T. azollae_ on standard cyanobacterial media like BG11.
We have tried to do reproduce this ourselves, and have talked to scientist better equipped to do so than us.
Yet all efforts failed.
Additionally, I personally find that papers claiming a culturing protocol for _T. azollae_ lack proper checks.
More often than not, these checks are a PCR for the very common nitrogenase gene, or a visual check for heterocysts common to many genera of cyanobacteria.
I suspect these works describe cultures of other cyanobacteria.

Like the organisation of the Nostocaceae family, the genus name of _T azollae_ is also up for debate.
_N. azollae_ has undergone multiple reclassifications due to advances in molecular phylogenetics such as phylogenomics techniques.
Traditionally, it has been referred to as _Anabaena azollae_.
Most modern literature refers now to _Nostoc azollae_.
More recently _Trichormus azollae_ was proposed to be the propper genus for the symbiont, this is now also the standard in the NCBI taxonomy database.
These taxonomic ambiguities arise from variations in morphological and genetic data that were considered for the phylogeny of the Nostocaceae family.
[Modern taxonomic revision of planktic nostocacean cyanobacteria: a short review of genera](https://link.springer.com/article/10.1007/s10750-009-0030-4)
Recent studies favor the classification of this cyanobiont as _Trichormus azollae_ based on comprehensive phylogenetic analyses.
[trichormus paper link]
In this thesis both _Nostoc azollae_ and _Trichormus azollae_ are used.
The former in chapters that were published before this thesis was compiled, the latter for newer work.

One of the key papers to understand _N. azollae_ is the original genome publication by Ran et al. [cite].
The study found the genome of _Nostoc azollae_ has undergone substantial reductive evolution.
It contains many broken genes that would otherwise be considered essential for a free-living cyanobacterium.
The genome does contain a complete set of genes required for nitrogen fixation, highlighting the cyanobacterium's crucial role in providing fixed nitrogen to the symbiosis.
These broken genes, or pseudo genes, are often damaged by insertion sequences (IS elements).
_T. azollae_s genome contains a high amount of IS elements, indicating ongoing and substantial genome reduction and instability.
Lacking many important metabolic genes, _T. azollae_ likely has a high degree of specialization and dependence on the host plant.
I find the Ran et al. paper essential reading for _Azolla_ symbiosis research.
It provides the genetic basis for understanding the metabolic potential of the main symbiont of _Azolla_ ferns.
By elucidating the genetic adaptations of _T azollae_, the study paves the way for further research into optimizing _Azolla_ for agricultural and environmental applications.

Genome degradation sounds worrisome, but is actually a well documented process for obligate symbioses.
Organelles are extreme examples of this process.
Symbiotic bacteria often lose genes that are unnecessary for their specialised lifestyles.
For example, _Buchnera aphidicola_, an endosymbiont of aphids, has reduced its genome to about 600-800 kilobases, retaining only essential genes for amino acid synthesis, while losing genes involved in DNA repair and regulatory functions
[buchnera](https://academic.oup.com/mbe/article/36/7/1481/5466460#:~:text=URL%3A%20https%3A%2F%2Facademic.oup.com%2Fmbe%2Farticle%2F36%2F7%2F1481%2F5466460%0ALoading...%0AVisible%3A%200%25%20)
[Genome interdependence in insect-bacterium symbioses](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2001-2-12-reviews1032).
Similarly, _Wigglesworthia glossinidia_, a symbiont of tsetse flies, has a genome of approximately 700 kilobases, which includes genes vital for the biosynthesis of vitamins needed by the fly, but lacks many metabolic pathways, relying heavily on the host for these functions
[Genome evolution in bacterial endosymbionts of insects](https://www.nature.com/articles/nrg931.pdf)
[Tsetse Flies Rely on Symbiotic Wigglesworthia for Immune System Development](https://journals.plos.org/plosbiology/article?id=10.1371/journal.pbio.1001070).
In an even more extreme case, _Carsonella ruddii_, the endosymbiont of psyllids, has the smallest known bacterial genome at about 160 kilobases, maintaining only a minimal set of genes required for protein synthesis and essential nutrient production, illustrating its high level of dependence on the host [Carsonella](https://academic.oup.com/mbe/article/24/2/449/1149358#:~:text=URL%3A%20https%3A%2F%2Facademic.oup.com%2Fmbe%2Farticle%2F24%2F2%2F449%2F1149358%0ALoading...%0AVisible%3A%200%25%20)
[Genome interdependence in insect-bacterium symbioses](https://genomebiology.biomedcentral.com/articles/10.1186/gb-2001-2-12-reviews1032).
These examples highlight how genome reduction enables symbiotic bacteria to become highly specialized and efficient in their roles, focusing on essential symbiotic functions and relying on their hosts for other needs.

The genes in the _T. azollae_ genome sequence reveal the symbionts metabolic potential, as well as its lost metabolic potential.
These features tell us about the workings and evolution of the symbiosis.
For example, Ran et al. found pathways for the biosynthesis of phytohormones.
These pathways may contribute to the growth and development of _Azolla_, indicating a two-way metabolic intertwined-ness between the two.
Nitrogen gas is fixed with the nitrogenase enzyme into amonium.
This costly process is powered by energy and redux from the cyanobacterium's own photosynthesis which remains intact.
[Eily et al.; Ray 1979]
_Nostocs_ photosynthesis uses a slightly different colour green than the plant does, so they compete less for the same light.
This association allows _Azolla_ to thrive on nitrogen-poor or even nitrogen-free water.
In return _T. azollae_ is thought to get carbon compounds from the host plant.

## Ecology

When an _Azolla_ population has covered a water surface, the plants' growth is directed upwards.
An _Azolla_ mat is formed between few millimeters and 20 to 30 centimeters in extreme scenario's.
The bottom of the mat is dark, and may be submerged by the weight of plants laying on top.
Inside the _Azolla_ mat, the light quality changes.
Specifically the red vs far-red light ratio.
The plants perceive this light change, and adapt their growth.
The internode distance (distance on the stem between leaves) increases, giving the plant an elongated appearance.

phosphorus heavy environments --> B-Ware paper

## Life cycle

_Azolla_ is a fern genus, it makes no flowers but spores for reproductive purposes.
Sporulation is triggered by a high far-red over red light ratio, and density of the plants in a mat.
_Azolla_ makes two types of spores: Big megaspores, made in megasporocarps and small microspores made in microsporocarps.
The cone-shaped megasporocarps can just be observed by the naked eye and contain one megaspore as well as a dormant colony of the symbiotic bacterium _T. azollae_.
The microsporocarps are bigger, and contain many small massulae.
Massulae are presumably non-living structures containing the microscopic microspore.
_Azolla_ massulae are very recognisable by their clochidia.
These are arrow like structures on the surface that serve to hook onto the megaspore.
When attached to the megaspore, the microspore presumably swims to the megaspore, fertilises it and a plant grows out of it.

pictures!



## agricultural history

The _Azolla_-_Nostoc_ symbiosis is not only ecologically significant but also offers considerable potential for sustainable agriculture.
_Azolla_ has been used historically as a biofertilizer in rice paddies, where its rapid growth and nitrogen-fixing ability enhance soil fertility and crop yields.
The genomic and metagenomic analyses presented in this thesis aim to unravel the complexities of this symbiotic relationship, providing insights into the genetic and functional dynamics that underpin this association.

> The utility of Azolla extends beyond its ecological benefits to practical applications in agriculture and environmental management.
Historically, it has been used as a green manure in rice paddies, particularly in Asia, where its ability to fix nitrogen enhances
soil fertility and boosts crop yields. The fern’s high protein content makes it an excellent feed for livestock, providing a
 nutritious and sustainable alternative to conventional animal feeds. Additionally, Azolla is being explored for its potential
 in biofuel production and as a means of controlling mosquito populations by covering stagnant water where mosquitoes breed.
 These diverse applications highlight Azolla’s versatility and its potential to contribute to sustainable agricultural practices
 and environmental conservation efforts ￼ ￼.

## agricultural opportunities

heavy metals, pollutants?

protein!

## the Azolla event

## my motivation for studying Azolla

# Methodology

Through advanced sequencing technologies, this research characterizes the genomes of both _Azolla_ and _Nostoc azollae_, revealing the genetic basis of their symbiotic interaction.
Metagenomic approaches further elucidate the broader microbial community associated with _Azolla_, identifying other potential endophytes that contribute to the fern's growth and resilience.
By integrating genomic and metagenomic data, this work seeks to deepen our understanding of the molecular mechanisms driving the _Azolla_-_Nostoc_ symbiosis and to explore its applications in enhancing agricultural sustainability.

## introducing bioinformatics to a lab

* challenges
* documentation

## roadmap to breeding a novel-symbiosis-crop

## Bioinformatics of novel-crops

## Documentationi and reproducibility in bioinformatics

## Innovative aspects

<!---
# old

## Symbioses

Trend in biology to see organisms as assemblages rather than individuals.

- gut microbiome
- hygene and allergies
- root microbiome
- plant micorhiza networks

Why symbioses motivate me

- "romanticised" image of organisms working together
- interesting biology
- inter-species complexity and evolution

![Illustration of the _Azolla_ symbiosis life cycle by Erbil Güngör](source/figures/fig1_life-cycle.png){#fig:fig1_life-cycle width=100% short-caption="Azolla life cycle"}
--->

<!---
# Plant biology for the twentyfirst century
These days, scientists, -humanity itself- is challenged with the advent of climate change, dramatic global population growth, and major loss of rurable land.
The field of plant biology plays a particularly important role securing a sustainable and healty future for humanity on plant earth.
IPCC
IPCC
FAO

Challenges that plant biologist may tackle

Efforts include improving existing crops

Novel crops

## Azolla
Ferns of the genus _Azolla_ have several key advantages

_Nostoc azollae_ Nitrogen independence

# Establishing the genetics of a novel crop symbiosis

## Domestication

## Breeding arrearage

## Breeding a symbiosis

## Challenges of Azolla

### framework
1. ~~Plant biology: Food, Novel crops, Azolla symbiosis
  - X challenges, solutions in novel crops
  - opportunities Azolla~~
2. ~~Genetics of a novel crop, breeding a Symbiosis
  - What questions need to be answered for novel crop
  - and for a symbiosis specifically
  - Challenges Azolla, fern life cycle, heterospory, nostocs~~
3. Bioinformatics and plant biology
  - The study of information in biological systems
  - Comparative genomics to speed-up breeding arrearage
  - Elucidating the plant's second genome:
4. Open science, share and re-use resources, how to bring a small field forward
  - share methods, data, workflows
  - Collaboration and outreach
  - Societial solutions vs. technology solutions
  - Teaching?
5. Key advances...
--->

<!---
label sections with LaTeX:
`\label{hidden_treasures}`
or with markdown:
`{#sec:foul-play-in-the-pocket}`

Then referece to the full chapter name:
\nameref{hidden_treasures}

the specific page:
\pageref{hidden_treasures}

the chapter number:
\ref{hidden_treasures}

with markdown if the ref contains no spaces:
+@sec:hidden-treasures

and for a markdown label only markdown refs work:
+@sec:foul-play-in-the-pocket
--->

# Outline of this thesis

**Chapter \ref{general_intro}__ (\nameref{general_intro} on page \pageref{general_intro}) is the current chapter.
I attempted to take a broader vantage point and less jargon than the remaining chapters.
A lesser-than-formal tone hopefully made this chapter more fun to read to the broader scientific audience interested in my work.

**Chapter \ref{foul_play}** (\nameref{foul_play} on page \pageref{foul_play}) details the initial discovery of prokaryotic DNA sequences in the _A. filiculoides_ genome assembly and includes the work that inspired this PhD project.
We identify near complete bacterial genomes in whole contigs of this assembly and study these further.
These bacteria are confirmed to be present in _A. filiculoides_ taken from the wild as well as from the lab.
The Non-cyanobacterial prokaryotes are confirmed to be associated with all _Azolla_ species for which WGS data is available.
They may be the same or very related microbes.
Finally, we study the metabolic pathways encoded within these genomes and hypothesise they might denitrify Nitrogen rich compounds within the _A. filiculoides_ leaf pocket.
This hypothesis is falsified however, denitrification occors only in microbes living epiphytically on _A. filiculoides_.

In **chapter \ref{hidden_treasures}** (\nameref{hidden_treasures} on page \pageref{hidden_treasures}), I build further on the work of chapter \ref{foul_play}.
This chapter details a workflow to enrich and study the genomes of bacteria associated with all sequenced _Azolla_ species.
The workflow thoroughly removes plant DNA reads, and then assembles those of the remaining microbes.
The process of separating disctint microbial genomes (binning) required extra binningsignals and manual curation for these were not part of the original experimental design.
Each respresented species of the _Azolla_ genus yielded between 12 and 22 associated bacterial genomes.
The majority of these genomes belong only to six taxonomical orders present in the majority of the entire _Azolla_ genus: Burkholderiales, Caulobacterales, Nevskiales, Nostocales, Rhizobiales and Sphingomonadales.
The systematic presence of these taxonomic groups suggests they be selected for in the _Azolla_ symbiosis and they may be vertically transfered over host generations as is the main symbiont _N. azollae_.

**Appendix \ref{metagenomics_practical}** (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}) illustrates an educational practical based on these first two chapters.
I designed this practical to teach the basic metagenomics principles and techniques to Life Sciences students with minimal coding experience.
The practical introduces the Bash language and tries to learn the main concepts behind metagenomics through a hands-on approach.
It starts with a metagenome assembly, and guides the students through DNA mapping, binning, quality control, gene annotation and finally plotting of metabolic pathways.
Exercises are implemented in JuPyter notebooks, combining code-writing with text instructions.
The practical is freely available on GitHub here [github.com/lauralwd/metagenomicspractical](https://github.com/lauralwd/metagenomicspractical)

**Chapter \ref{forever_together}** (\nameref{forever_together} on page \pageref{forever_together}) describes the genomics of the main _Azolla_ symbiont: _N. azollae_, using the genomes assembled in chapter \ref{hidden_treasures}.
All _N. azollae_ share near identical genomes and gene content, indicating they are the same species of _N. azollae_, hosted in various _Azolla_ species.
The _N. azollae_ genome is degraded due to high pseudogene content.
Pseudogenation is caused by high transposon activity early in the symbiosis, but has since then slowed down.
A _N. azollae_ specific gene set was identified comparing many near complete genomes in the Nostocales family.
A phylogenomics approach confirms that te organisation of genera in this family is paraphyletic, but places _N. azollae_ close to _Anabeana_ species.

**Chapter \ref{partners_and_passengers}** (\nameref{partners_and_passengers} on page \pageref{partners_and_passengers}) is likely not going to happen...

**Chapter \ref{it_takes_two}** (\nameref{it_takes_two} on page \pageref{it_takes_two}) provides building blocks for understanding and regulating the sexual reproduction and mode of transmission of the _Azolla_ & _N. azollae_ symbiosis.
Such understanding is a pre-requisite for agricultural application of a novel crop symbiosis.
Several _Azolla_ specimens collected all over the Netherlands were all the same species for they produced viable offspring.
We found that FR light and sporophyte density were main initiators of sexual reproduction while nitrogen availiblity was an inhibitor.
FR-responsive transcripts included MIKCC homologues of CMADS1 and miR319-controlled GAMYB transcription factors in the fern, transporters in _N. azollae_, and ycf2 in chloroplasts.
Phylogenomic analyses of MIKCC transcription factors suggested that control of flowering and flower organ specification may have originated from the diploid to haploid phase transition in the homosporous common ancestor of ferns and seed plants.

Sexual reproduction of the symbiosis requires that the symbiont is systematically stored in dissemination stages to reinnoculate the next generation of hosts.
Contrasting earlier theories, we propose that _N. azollae_ does not colonise developing megasporocarps travelling from leaf pockets to megasporocarps via small channels.
Instead, we theorise that they colonise early sporocarp initials of both typles, but are only retained in megasporocarps.
This method of transmission is identical to colonisation of leaf primordia, hence requires no separate machinery and explains consistent observation of _N. azollae_ in very young microsporocarps.

**Chapter \ref{phylogeny_workflow}** (\nameref{phylogeny_workflow} on page \pageref{phylogeny_workflow}) describes a workflow for creating large and state-of-the-art phylogentic trees of gene families; examplified in landplants.
Studying fern genetics, the _Azolla_ lab often deals with fern genes that are homologous (similar in sequence) to a seedplant gene.
With phylogeny, we aim to assess the evolution of a gene family and orthology/paralogy of _Azolla_ genes to model species their genes.
While many user friendly methods exist to create phylogenetic trees, these are often either closed-source, or their performance is limited.
Here I created a workflow for basic phylogeny inference with state-of-the-art open source tools, unlimitted in their performance.
This workflow is aimed at user skilled in reading a phylogeny, but not in using the CML tools to use the latest software to build them.
It covers data-selection, multiple sequences alignment, alignment trimming, and tree inference.
Additionally, it provides tools to create semi-automatic mark-up for phylogenetic trees in the iToL webinterface.

## Appendeces

Academics are more than just scientitsts.
They are often also teachers on universities and leaders and administrators in academic organs.
During my PhD, I attempted to incorparate that broader academic experience in my work.
The doctorate remains intrinsically a scientific degree and this thesis is first and foremost a scientific document.
Still, I add three appendeces that give a glimpse in my "extracurricular" activities.
My thesis; the culmination of my PhD, simply would not be complete without them.

Firstly, **Appendix \ref{BKO}** summarises my basic University Teaching Qualification (bUTQ or BKO) application.
About a quarter of My PhD I spend on teaching and developping myself as a Teacher.
This effort was rewarded with a bUTQ or BKO in Dutch.
The full portfolio is too lengthy to include, so this chapter sumarises the original document.
Secondly, an example of teaching material that is completely of my own design is included in **Appendix \ref{metagenomics_practical}** (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}) as mentioned before.
Finally, I include a short narrative CV on my non-science and non-teaching activities during my PhD and what I gained from them.

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
