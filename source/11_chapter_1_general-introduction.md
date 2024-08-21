\thispagestyle{plain}
<!-- Start page numbering here, so that part II starts at page one in the table of contents -->
\pagenumbering{arabic}
\setcounter{page}{1}
<!-- Start new part of the book, the scientific chapters (and gen-intro) -->
\part{Chapters}

<!-- line numbers, to be removed in final version -->
\resetlinenumber
\linenumbers

<!-- chapter title and bla bla -->
\chapter{A hitch-hiker's guide to \textit{Azolla} symbiosis genomics}
\label{general_intro}

<!-- thumb index with a I for introduction -->
\addthumb{General Introduction}{\Large{I}}{white}{gray}

\pagestyle{chapter}

<!-- author stuff -->
\footnotesize
Laura W Dijkhuizen^1^
\scriptsize

1. Molecular Plant Physiology Department, Utrecht University, Utrecht 3584CH, The Netherlands

<!-- get ready for the actual text body -->
\newpage
\normalsize
\onehalfspacing
\setlength{\parindent}{0.5in}

<!-- have a mini table of contents -->
\minitoc

\section*{Abstract}

This hitch-hiker's guide serves as a friendly, general introduction to this thesis.
The thesis explores the genomics of the _Azolla_ symbiosis: the relationship between _Azolla_ ferns, their main symbiont _Trichormus_ (or _Nostoc_) _azollae_, and other bacterial partners.
The chapters will discuss the discovery of these additional bacterial partners and the identity and evolution of the main symbiont.
The final chapters focus on the symbiosis' reproductive cycle and some methodological approaches.
This is all new information on the _Azolla_ symbiosis, which I argue is crucial for modern breeding of _Azolla_.
Each chapter already contains in-depth, stand-alone introductions.
Therefore, in this general introduction, I aim to provide broader context and perspective on symbiosis research, the remarkable _Azolla_, and relevant genomics methodologies.
I will argue that a systems biology approach can greatly benefit symbiosis research.
Next, I will offer a broader context on the _Azolla_ symbiosis.
Finally, I will discuss bioinformatics techniques used to address the key questions and hypotheses of this PhD project.
I have endeavoured to make this introduction accessible to all scientific audiences, not just (plant) biologists.
There will be a touch of humour, personal opinion, and informal writing.

\newpage

> _“A system is never the sum of its parts it's the product of their interaction.”_

– Russell Ackoff (professor of systems sciences)

# A Systems Perspective

When imagining an ecosystem, one typically envisions a forest with trees, animals, and insects.
Perhaps some fish swim in a stream, all idyllically thriving as a balanced part of a larger whole.

The ecosystem concept emphasises the abundance and complexity of interactions within the larger system, rather than the individual existence of its separate parts.
However, when one imagines a biological experiment, the image often involves lab coats, petri dishes, and microscopes.
This perception is not incorrect; science has thrived under reductionism.
Scientific experiments often strive to control one variable at a time to isolate its effects.
All other variations are minimised by working with one species or strain at a time, treated identically except for that one experimental variable.
The organism is removed from its natural environment to prevent it from meddling with the experiment.
The ultimate goal is to gain mechanistic insight into the workings of a biological system, one part at a time.
The underlying assumption is that if we understand the function of all its parts, we will understand the system as a whole.

The reductionist dogma yielded considerable advances in biological research; this is undisputed.
However, I argue that it occasionally falls short in capturing the emergent properties of a larger whole.
The complexity of real-world biology does not always allow for the isolation of a single variable from the rest of the system.
Nor does changing one variable in a system always lead to predictable changes.
For examples of the former, this thesis describes such a system.
For the latter, recent attempts at microbiome editing exemplify this limitation.
A microbiome is the collection of all microbial organisms associated with an organ or organism.
Such a collection often contains millions of cells from hundreds of strains, if not more.
It is overly optimistic to take one of these strains, edit it—often genetically—and expect a robust change.
Plenty of examples in the literature support this view [@Bai2023; @Mueller2015a].
Instead, a perspective of the entire (eco)system and lessons from macroecology may be required for sustained microbiome editing [@Albright2022].
This necessitates a systems perspective.

Even within the confines of a cell, the reductionist view of biology is subject to scrutiny.
Mechanistic studies often investigate the workings of single components within the cell, perhaps placing them into metabolic pathways.
These pathways form a vast network of cause and effect.
One can trace how a compound navigates through the network, transforming into another compound.
Or observe how a signal at one point gets amplified and transmitted to another.
We have come to view the cell's metabolism as a chemical machine striving for homeostasis or equilibrium.
This concept is over a century old [@Nicholson2019].

@Nicholson2019 suggests that we should perhaps abandon the view of the cell as a mechanical reductionist entity, studied solely through its molecular components.
He argues that the machine conception of the cell is a misleading representation of biological reality.
An overview of cause-and-effect relationships fails to capture the non-linearity, stochasticity, and plasticity of cellular behaviour [@Nicholson2019].
Groups of cells do not respond to a stimulus gradually and homogeneously.
Instead, their response is stochastic and heterogeneous, switching on or off unpredictably [@Altschuler2010].
Similarly, protein complexes are not static assemblies like engineered machines.
Instead, they self-organise, with multi-functional parts that constantly come together and separate [@Nicholson2019; @Dumont2014].
Apply this state of flux to all parts of a metabolic network, and imagine the consequential chaos.
This chaotic cell is a collection of semi-stable processes that continuously self-organise into alternative steady states.
A system far from equilibrium, seemingly inefficient and costly, yet flexible and robust as a consequence [@Nicholson2019].
@Nicholson2019 is an excellent read, and I would not fault anyone for setting aside this thesis to pick up his article instead.

In this section, I do not argue for the abandonment of mechanistic research, but for its complement with a systems biology perspective.
This is a task well suited for biologists, who are trained from the outset to think across varying scales, from molecule to ecosystem.
In fact, my bachelor studies were organised in this very way.
Yet somehow, something so obvious to a first-year biology student becomes an afterthought in reductionist scientific practice.

# Symbiosis

The study of symbioses may lie at the intersection of system-level understanding and mechanistic research.
The molecular biology methods associated with reductionist approaches remain standard in this field, and my colleagues and I adhere to these methods in our work.
This adherence is necessary because we are studying a young system, which requires foundational groundwork.
However, we should continually question what our findings mean for the system as a whole.
In many cases, we are compelled to study the system in its entirety.
This thesis focuses on an obligate symbiosis.
Any experimental condition affects all organisms involved, and they influence each other.
In this context, studying one symbiont without the other is either not viable or results in significant health issues.
Thus, studying them in isolation without considering the entire symbiotic relationship risks being short-sighted.

By definition, symbiosis is a long-term interaction between two or more organisms.
These interactions can often be categorised as:

- Mutualism: when all partners benefit
- Commensalism: when one partner benefits without harming others
- Amensalism: when one partner is unaffected, but another is harmed
- Parasitism: when one partner benefits at the expense of others
- Competition: when all partners are harmed by the interaction

The general public often associates symbiosis with positive interactions, typically referring to mutualism and commensalism.
However, this is not always practical, as the nature of the interaction is often unknown at the outset.
Therefore, considering the duration of the interaction is a more robust approach.
In this thesis, symbiosis generally refers to mutualism and commensalism, aligning with the common understanding of the term.
The latter three categories are considered general ecological interactions rather than symbioses in this context.

## Symbiosis Breeding

The original premise of this PhD project includes considerations of symbiosis breeding, particularly in mutualistic or commensalistic relationships.
The organisms in this study are part of an obligate symbiosis centred on nitrogen acquisition.
We reasoned that the molecular pathways of the host and symbiont are intricately interconnected.
Therefore, any breeding efforts should involve both the plant and its symbiont.

Traditionally, research on improving symbiotic functions focuses on breeding plants.
Notable examples include root-nodule and mycorrhizal symbioses [@Liu2020; @Thirkell2022].
However, breeding the symbiont may be equally, if not more, important.
This requires a systems biology perspective that integrates ecological, physiological, and genomic data.
While breeding symbioses is challenging, ignoring the symbiont when it plays a central role in the desired traits seems impractical.
This approach may appear naive, given the practical and legislative challenges.

Breeding symbioses demands a holistic perspective that considers all relevant organisms and their interactions.
In the literature, this has been referred to as breeding a "holobiont" [@Zilber-Rosenberg2008].

## The Holobiont Concept

The holobiont concept is a recent proposal in evolutionary biology [@Zilber-Rosenberg2008; @Rosenberg2016].
It suggests that hosts and their symbionts should be viewed as a single unit of evolutionary selection.
This idea is particularly relevant in obligate symbioses, where the microbiome is inherited across generations.
It may even seem odd to argue that systematically inherited DNA should be considered a separate evolutionary unit based solely on the compartment it resides in.
We rarely find this useful for organelles either, although examples exist in the literature [@Keeling2010; @Perez-Escobar2016].
The concept invites thought experiments.
For example, could the rapidly evolving bacterial component of the hologenome provide adaptability to the more static host genome?
This flexibility might explain the swift adaptation of microbiomes to their hosts.

Critics argue that the concept oversimplifies complex interactions and that existing ecological frameworks are sufficient [@Douglas2016].
Holobiont members may interact both beneficially and antagonistically.
The species composition of a holobiont can vary, complicating the evolutionary pressures on the consortium as a whole.
Despite these criticisms, the concept can be useful in certain scenarios, particularly where the host and symbiont are tightly integrated.
I have not yet reached a definitive conclusion on this matter, although I am inclined to agree with the critics in most scenarios.
If we can consider a single gene as an evolutionary unit [@Dawkins2016], perhaps there is also value in considering the holobiont as one.
Both models are undoubtedly imperfect, but they may occasionally offer valuable insights.
However, it is important to use the term carefully, recognising that it is one of many models for understanding symbiosis and co-evolution.
In this thesis, we occasionally use the term holobiont, acknowledging its potential insights while maintaining a cautious perspective.

# The _Azolla_ Symbiosis

This work explores the genomics and metagenomics of a specific symbiosis: that between the floating fern genus _Azolla_ and the cyanobacterium _Nostoc azollae_.
The cyanobacterium supplies the symbiosis with a surplus of nitrogen fixed from the air.
Unlike most plants, _Azolla_ is not terrestrial; instead, it floats on water.
_Azolla_’s aquatic lifestyle makes the fern highly dependent on fresh water.
Even its name reflects this dependency: ἄζος (Azos) is ancient Greek for 'drought' and ὀλλύναι (ollunai) for 'killing'.
The fern spreads horizontally over the water surface, darkening the water column.
This property makes _Azolla_ both infamous among ecologists and renowned in symbiosis research [@Madeira2016a].

Larger plants break into smaller ones, genetically identical but physically separate, forming a large green floating mat.
_Azolla_ mats are known for their high growth rate and high protein content.
A mat can grow so rapidly that _Azolla_ is believed to have overgrown the entire North Pole during a period in geological history [@Brinkhuis2006].
This "_Azolla_ event" contributed to a significant global decline in atmospheric CO₂.
In human history, _Azolla_ has been traditionally used in rice paddy fields [@Wagner1997b;@Shi1988].
Its main function was to prevent toxic cyanobacteria from growing in the water, with any surplus being fed to livestock.
Some of today's agricultural challenges, such as limited arable land, nitrogen fertiliser excesses, and protein shortages, seem a perfect fit for _Azolla_ [@Bijl2014].
_Azolla_ is an incredibly interesting plant.
In this section, I'll briefly elaborate on these points, providing broader context that the individual chapters' introductions may lack.

## _Azolla_ Physiology

_Azolla_ stems spread horizontally over the water surface.
At stem nodes, leaves and roots are attached.
_Azolla_ leaves are highly adapted to the fern's aquatic lifestyle.
They are bi-lobed, with both lobes directed either up- or downward.
The lower lobe is razor-thin, translucent, and concave, lying on the water like a boat, suspending the stem and upper leaf lobe above.
The upper lobe is thick, almost balloon-like, and typically dark green.
Inside the upper lobe, a specialised organ houses the symbiotic bacteria.
The leaves grow in a compact, cabbage-like fashion, giving the whole plant a fish-scale appearance.
The earliest scientific description of the plant I could find is by @Strasburger1873.

<!-- insert macro photo Azolla, macro photo stem tip, microscope photo starting colony -->

All organs originate from the tip of the stem, at the shoot apical meristem (SAM).
The SAM produces primordia, small bulges that develop into leaves, roots, and sporocarps.
Sporocarps are the fern's reproductive structures.
The SAM also harbours a small colony with motile filaments of the cyanobacterium _T. azollae_.
Both leaves and sporocarps encapsulate part of this starting colony during growth, ensuring that all leaves contain a colony of the symbiont [@Campbell1893].

The leaf cavity, or leaf pocket, of _Azolla_ is a specialised structure crucial to its symbiosis with the cyanobacterium _Trichormus azollae_.
These cavities, located within the upper leaf lobes, serve as protective niches for the cyanobiont.
This adaptation ensures a stable population of _T. azollae_ within _Azolla_'s tissues, providing a plentiful supply of fixed nitrogen.
The cyanobacteria are sheltered from environmental fluctuations, such as changes in water and nutrient availability.
The leaf cavity facilitates a regulated exchange of nutrients between the host and symbiont.
_T. azollae_ contributes nitrogen compounds that support _Azolla_'s growth, while the fern likely supplies other essential nutrients like phosphorus.
This mutually beneficial relationship is a key evolutionary adaptation that allows _Azolla_ to thrive in nitrogen-deficient environments.
Understanding the structure and function of these leaf cavities is essential for unravelling the complexities of the _Azolla_ symbiosis.

_Azolla_ roots can be observed hanging loosely in the water like a thin curtain.
Time-lapses show the roots swirling and curling.
<!-- insert link to time-lapse -->
Roots of individual plant fronts grab onto each other like rugby players locking shoulders in a scrum, forming a cohesive mat that keeps the plants together.
I suspect this phenomenon may help in creating favourable conditions for the symbiosis.
It may help in stratifying the water column, keeping nutrients from decaying plants close to the roots for re-absorption.
_Azolla_ can rapidly and massively shed its roots, which may be a mechanism for leaving a certain area [@Cohen2015a].

Interestingly, _Azolla_ roots respond distinctly to typical plant hormones compared to those of flowering plants [@deVries2016].
Roots were likely invented twice in plant history: once in lycophytes and ferns, and later in seed plants (reviewed in @Spencer2021).
The roots invented by ferns were passed down to seed plants, though not all roots developed the same way since their origin.
In seed plants, the hormone cytokinin promotes cell division in shoots and regulates growth differentiation in roots.
In contrast, cytokinin promotes cell division in _Azolla_ roots [@deVries2016].
This finding suggests that _Azolla_ roots have an origin as a shoot structure, making them analogous to plant roots—similar in appearance but separate in origin.

The specifics of _Azolla_ root origin are not of major consequence to this work.
However, they highlight that the evolutionary history of _Azolla_ diverged from that of seed plants a long time ago.
Educated guesses made with a seed-plant background may be incorrect more often than one might think.
I also want to express my dislike for the term "primitive plants," as if ferns have not diversified, adapted, and evolved since their origin.
I hope this thesis, even this introduction, will help in appreciating the intricacies of the _Azolla_ symbiosis life cycle.
We can discuss "primitiveness" further compared to the brute force of non-pollinated flowers or the extravagance of a magnolia.

## Cyanobacterial Symbiosis

Cyanobacterial symbioses are widespread and diverse, spanning various ecosystems, including marine environments, freshwater systems, and terrestrial habitats.
Cyanobacteria form mutualistic associations with a wide range of hosts, including plants, fungi, protists, and even animals.
In marine systems, symbiosis partners can be sponges or diatoms.
In freshwater systems, the _Azolla_ symbiosis is a prime example.
Terrestrial hosts can include cycads (plants), mosses, and lichens (fungi).
Most of these symbioses are facultative, meaning that most cyanobacteria can live independently from their host [@Peters1991].

The _Azolla_-_Nostoc_ symbiosis is perhaps most closely related to moss-cyanobacterium symbioses, particularly in boreal and temperate regions.
Host mosses like _Sphagnum_ and _Pleurozium schreberi_ attract nitrogen-fixing cyanobacteria, primarily from the genera _Nostoc_ and _Anabaena_ [@Bay2013a].
The cyanobacteria provide their host mosses with nitrogen by fixing atmospheric nitrogen [@Rousk2022].
This relationship offers a substantial competitive advantage in nutrient-poor environments [@Alvarenga2022].
The symbiosis significantly contributes to the nitrogen budget, supporting the growth of both mosses and the surrounding plant community [@Calabria2020].
In moss-cyanobacterium associations, the cyanobacteria are often acquired from the environment by each moss generation [@Liu2022].
The cyanobacteria can also live without a host in these environments, with culturing and inoculation protocols well established.
This is unlike the _Azolla_-_Nostoc_ symbiosis, where the cyanobacteria are transferred through fern reproductive structures and cannot live without their host [@Peters1991].
<!-- Moss picture with punctiforme? -->

Cyanobacteria that associate with mosses, and also with _Azolla_, are often part of the Nostocaceae family.
The Nostocaceae family comprises several genera of cyanobacteria known for their filamentous, colony-forming structures and their ability to fix nitrogen.
The family includes genera such as _Nostoc_, _Anabaena_, _Trichormus_, and _Cylindrospermum_.
These genera share common features, such as the presence of specialised heterocyst cells that fix nitrogen under aerobic conditions [@Adams2000].
Phylogenetic studies have shown that the relationships among these genera are complex.
Significant genetic diversity exists within a single genus, and several species have been moved between genera [@komarek2010; @kastovsky2024].
The genus name of _Azolla_'s cyanobacterial symbiont has also changed over the years.

<!-- include phylogeny from a paper or database? -->

## _Anabaena_, _Nostoc_, or _Trichormus_ _azollae_

_Azolla_ species form a unique symbiotic relationship with the cyanobacterium _Trichormus azollae_, which resides in specialised leaf cavities of the fern.
The primary function of _T. azollae_ is to fix nitrogen from the air and provide it to the host plant.
Over the years, the cyanobiont has been classified under various genera, including _Anabaena_, _Nostoc_, and most recently, _Trichormus_.
Traditionally, it was referred to as _Anabaena azollae_, but advances in phylogenetic analysis led to its reclassification [@Pereira2014; @Baker2003].
Most modern literature now uses the name _Nostoc azollae_, though the latest studies favour _Trichormus azollae_ based on comprehensive phylogenetic evidence [@Baker2003].
Strictly speaking, _Trichormus azollae_ is the only verified name [@Pereira2014] and is now the standard in the NCBI taxonomy database ([NCBI: _T. azollae_](https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=551115)).
These taxonomic ambiguities arise from variations in morphological and genetic data considered in the phylogeny of the Nostocaceae family.
In this thesis, both _Nostoc azollae_ and _Trichormus azollae_ are used.
The former is used in chapters published before this thesis was compiled, and the latter in newer work.

<!-- GTDB ANI calculations actually put it with Anabaena rather than Trichormus. WTF. -->

The culturability of _Trichormus azollae_ has been a subject of debate in the scientific community.
While several studies have claimed to culture _T. azollae_ on standard cyanobacterial media like BG11 [@Franche1985; @Zimmerman1987; @abd2013; @Parente2017], these attempts often lack rigorous verification.
Efforts to reproduce these cultures have largely failed, suggesting that the reported cultures may have been misidentified or contaminated with other cyanobacteria [@Pereira2014; @Ladha1982].
At conferences, I learned that many more labs have tried to grow _T. azollae_ and failed, though these negative results are rarely published.
Perhaps other (not necessarily symbiotic) cyanobacteria are systematically associated with _Azolla_ and are, in fact, culturable [@Pratte2021].

One of the key papers for understanding _T. azollae_ is the original genome publication by Ran et al. [@Ran2010].
The study found that the genome of _T. azollae_ has undergone substantial reductive evolution, containing many broken genes that would otherwise be considered essential for a free-living cyanobacterium.
However, the genome retains a complete set of genes required for nitrogen fixation, highlighting the cyanobacterium's crucial role in providing fixed nitrogen to the symbiosis.
These broken genes, or pseudogenes, are often disrupted by insertion sequences (IS elements).
_T. azollae_'s genome contains a high number of IS elements, indicating ongoing and substantial genome reduction and instability.
Lacking many important metabolic genes, _T. azollae_ likely has a high degree of specialisation and dependence on the host plant.
I consider the Ran et al. paper essential reading for _Azolla_ symbiosis research.
It provides the genetic basis for understanding the metabolic potential of _Azolla_'s main symbiont.

The genes in the _T. azollae_ genome sequence reveal both its metabolic potential and its lost capabilities.
This metabolic insight sheds light on the workings and evolution of the symbiosis.
For example, _T. azollae_ retains pathways for phytohormone biosynthesis, which may contribute to _Azolla_'s growth and development [@Ran2010].
This finding indicates a metabolic interdependence between the symbiont and the host.
Nitrogen gas is fixed by the nitrogenase enzyme into ammonium, a process powered by the cyanobacterium's photosynthesis [@Ran2010; @Eily2019; @Ray1979].
_T. azollae_'s photosynthesis uses a slightly different wavelength of light compared to the host, reducing competition and enabling _Azolla_ to thrive in nitrogen-poor environments.

However, _T. azollae_'s genome has undergone significant reductive evolution.
It lost many genes essential for a free-living cyanobacterium, making it highly specialised and dependent on the host.
This genome reduction is characterised by a high number of genes disrupted by insertion sequences (IS elements).
Such pseudogenes are a common feature in obligate symbioses [@Keeling2010; @Wernegreen2002].
Examples from insect symbioses, such as _Buchnera aphidicola_ in aphids and _Wigglesworthia glossinidia_ in tsetse flies, demonstrate similar patterns of genome degradation, where only essential genes for the symbiotic relationship are retained [@Chong2019; @Heller2011].
These parallels illustrate how genome reduction plays a crucial role in the specialisation and dependence of symbionts within their hosts.

## Ecology

_Azolla_ naturally thrives in various nutrient-rich freshwater environments, including ponds, lakes, slow-moving streams, and wetlands.
These habitats provide ideal conditions for _Azolla_'s growth, such as abundant water and nutrient availability.
_Azolla_ species are distributed globally, predominantly in tropical, subtropical, and warm temperate regions.
They are especially prevalent in Asia, Africa, and the Americas, where they have been traditionally used in agriculture [@Madeira2016a; @Lydia2023; @Watanabe1981].
_Azolla_ forms dense mats on the water surface, outcompeting other aquatic plants and algae.
These mats help stabilise ecosystems by reducing water evaporation and providing habitats for microorganisms and small aquatic animals [@Wagner1997b].

Ecologists often associate _Azolla_ with unhealthy ecosystems, labelling it as invasive and dangerous.
However, I argue that _Azolla_ itself is not dangerous but rather a symptom of eutrophic conditions, particularly phosphorus enrichment [@Temmink2018].
Eutrophication disrupts aquatic ecosystems, and _Azolla_ can exploit these conditions, similar to other fast-growing species like algae or _Lemna_ (duckweed) [@VanderLee2018].

_Azolla_ has natural enemies.
For _Azolla_ agriculture, these would be considered pests.
For conservation ecologists, they are considered pest control [@Madeira2016a].
Specifically, the water fern weevil _Stenopelmus rufinasus_ can significantly impact _Azolla_ populations by feeding on the fronds [@Hill1998].
A _S. rufinasus_ swarm can decimate an _Azolla_ mat in days and even completely eradicate it.
We have unwillingly empirically tested this theory several times.

When an _Azolla_ population has covered a water surface, the plants' growth is directed upwards.
An _Azolla_ mat can reach a thickness of a few millimetres to 20 to 30 centimetres in extreme scenarios.
The bottom of the mat is dark and may be submerged by the weight of plants laying on top.
Inside the _Azolla_ mat, the light quality changes, particularly the red vs far-red light ratio.
The plants perceive this light change and adapt their growth as shown in chapter \ref{it_takes_two} \nameref{it_takes_two} or @Dijkhuizen2021.
The internode distance (distance on the stem between leaves) increases, giving the plant an elongated appearance.
This is a common response in plants to being overshadowed by other plants; they stretch out towards the light [@Possart2013].

## Life Cycle

_Azolla_ is a fern genus that produces spores, not flowers, for reproductive purposes.
Sporulation is triggered by a high far-red over red light ratio and the density of the plants in a mat (Chapter \ref{it_takes_two}).
_Azolla_ produces two types of spores: large megaspores, made in megasporocarps, and small microspores, made in microsporocarps [@Schaffner1905].
The cone-shaped megasporocarps are visible to the naked eye.
They contain one megaspore and a resting colony of the symbiotic bacterium _T. azollae_, acquired from the starting colony at the SAM at the beginning of spore development.
The microsporocarps are larger and contain many small massulae housed in microsporangia.
Massulae are non-living structures containing the microscopic microspore.
_Azolla_ massulae are recognisable by their glochidia, arrow-like hair structures on the massulae surface that hook onto the megaspore [@Campbell1893].
When attached to the megaspore, the microspore presumably swims to the megaspore, fertilises it, and a new plant grows.

<!-- pictures! -->

## Agricultural History

The application of _Azolla_ in agriculture does not require high-tech genomic solutions.
_Azolla_ has been used historically as a bio-fertiliser in rice paddies for several millennia [@Watanabe1981; @bocchi2010; @bujak2022].
Rice paddies are often flooded to prevent weeds from growing, but this also creates an opportunity for toxic cyanobacterial blooms, which can poison the rice.
As a countermeasure, a rapidly growing _Azolla_ mat can shield the water from light, preventing algal blooms.
The nitrogen fixed by _Azolla_ can be incorporated into the soil after the rice harvest, fertilising the soil.
Any surplus of the fern can be used as animal feed.
Additionally, it is thought that an _Azolla_ mat prevents mosquitoes from accessing the water to lay their eggs.

## Agricultural Opportunities

_Azolla_ has significant agricultural potential due to its rapid growth, nitrogen independence, and high protein content [@Lumpkin1980a; @Brouwer2014].
It can be used as a bio-fertiliser, enhancing soil fertility by providing a natural source of nitrogen.
This practice reduces the need for synthetic fertilisers, promoting sustainable farming practices [@Watanabe1981].
Incorporating _Azolla_ into rice cultivation has been shown to increase crop yields and improve soil health, particularly in regions where arable land is limited and water is plentiful [@Watanabe1981; @bocchi2010].

Beyond bio-fertilisation, _Azolla_ is being explored as an alternative livestock feed due to its rich amino acid profile [@Brouwer2018].
Its high protein content and rich amino acid profile make it an excellent supplement for animal diets [@becerra1990; @Bujak2022; @Brouwer2014].
_Azolla_ could serve as a local protein source, reducing reliance on imported crops like soy, especially in regions such as the Netherlands, where the demand for protein crops exceeds local production capacity [@BrouwerThesis].
This application may also contribute to the recycling of nutrients within local agricultural systems.
However, challenges remain, such as _Azolla_'s relatively high tannin content, which can inhibit protein digestibility.

_Azolla_ is also considered for phytoremediation, helping to clean contaminated or eutrophic water bodies by absorbing heavy metals and retrieving nutrients like phosphorus and iron from soils [@Sood2012; @Scharer2009; @Temmink2018; @Akhtar2016].
While promising, the use of _Azolla_ in phytoremediation should be approached with caution due to its potential invasiveness and the complexities of pest management in aquatic systems.
Despite these challenges, _Azolla_'s unique properties offer substantial opportunities in addressing modern agricultural challenges.

Despite _Azolla_'s many advantages, its widespread use faces several challenges.
These include the need for large amounts of fresh water and the environmental risks associated with its cultivation.
_Azolla_ populations are also vulnerable to collapse if _S. rufinasus_ weevils infest the plants, complicating pest control in aquatic systems.
Moreover, chemical pest control is not ideal for an aquatic crop, especially one promoted as sustainable.
Lastly, the fern’s high phenolic content can inhibit protein digestion when used as animal feed [@Brouwer2018].
To fully realise _Azolla_'s potential, these challenges may need to be tackled through the domestication of the fern using modern breeding tools and genomic insights.

## _Azolla_ Domestication

The potential for _Azolla_ as a sustainable agricultural resource is clear.
Any drawbacks of _Azolla_ usage, such as digestion inhibition, might be addressed through breeding programs.
However, both historic and modern usage of _Azolla_ in agriculture have relied on local native _Azolla_ strains.
_Azolla_ has never undergone domestication, the process of enhancing crops for human use.
No formal _Azolla_ cultivars exist, and to my knowledge, there has never been any systematic breeding of _Azolla_.

With genomic insights and modern breeding tools, _Azolla_ could still be domesticated.
The first step in any domestication process is the collection of biodiversity.
The International Rice Research Institute (IRRI) collected a notable number of _Azolla_ strains, although some of this germplasm has unfortunately been lost [@Watanabe1992].
Control of sexual reproduction is another critical aspect, as detailed in Chapter \ref{it_takes_two}.
The ability to store and disseminate spores has already been demonstrated [@Brouwer2014].
These are important steps towards domestication.
However, modern breeding also requires genomic information.

The establishment of the first _Azolla_ genome by [@Li2018] marked a significant milestone in _Azolla_ domestication.
With this genomic information, along with emerging gene-editing techniques, wild _Azolla_ strains might be domesticated more efficiently [@Li2018; @Lemmon2018a].
Stable transformation or gene-editing of the symbiosis partners remains a challenge that still needs to be addressed [@Schluepmann2022].

# Methodology

Several _Azolla_ properties make it an interesting plant for addressing 21st-century challenges, such as the demand for plant-based protein and agriculture on non-arable land.
To further realise this potential, we can utilise modern breeding tools and a systems biology perspective on the functioning of the symbiosis.
These modern breeding tools require a foundation of genomic knowledge and expertise.
One must understand the genes involved in a symbiosis before determining which genes to edit.
This genomic understanding of the _Azolla_ symbiosis is the focus of this work.

The first part of this thesis explores the metagenomics of the _Azolla_ symbiosis.
Through metagenomics, I study the collective genomes of microbes associated with _Azolla_, mapping out their (near) complete metabolic potential.
In the last two chapters, my colleagues and I discuss the reproductive cycle of the _Azolla_ symbiosis.
Control of the reproductive cycle is essential for domesticating the symbiosis.
We aim to explore the molecular underpinnings of this cycle by reconstructing the evolution of proteins essential to this process.
The resulting phylogenetic trees allow us to relate knowledge from other plants to _Azolla_ and ferns in general.

## Bioinformatics

This thesis employs a variety of bioinformatics techniques.
Interestingly, the term has not been used until this section of the introduction.
Firstly, because I chose to focus on the plant and symbiosis biology first.
While my work may at times be heavy on the methods, I aim to prioritise the biology.
Secondly, the definition of bioinformatics deserves its own paragraph before we delve deeper.

The typical image of bioinformatics often centres on computer science and tool application, rather than biology.
Bioinformaticians are sometimes perceived as "number crunchers who look at black screens all day."
While there is some truth to this—ask any of my old colleagues how they picture me—it doesn't fully capture the field.
One could similarly claim that ecologists only spend time in the field identifying plant species or that molecular biologists spend all day moving minuscule amounts of water around.
These statements, while ironic and containing a kernel of truth, are not helpful for understanding the broader scope behind these stereotypical actions.
The same holds true for bioinformatics.

The original definition of bioinformatics is far more insightful and useful for understanding bioinformatic work.
**Bioinformatics is the study of information processes in biological systems** [@Hesper1970; @Hogeweg2011].
A bioinformatician may read that information from DNA through genomics or metagenomics.
We study how that information is transmitted within cells via RNA, perhaps with RNAseq, and across millions of years of evolution through phylogenetics.
We investigate how information is used to produce proteins with proteomics and structural bioinformatics.
We examine how information is utilised to make decisions in a cell and how this all integrates into a biological system.

In this work, we use bioinformatics to investigate the information storage and processing of _Azolla_ and its associated microbes.
This does involve a substantial amount of computer work, number crunching, molecule counting, and sequence comparisons.
However, the tedious counting of molecules is a means to an end: understanding the system as a whole.
In our case, this means identifying and understanding the metabolic potential of all _Azolla_-associated microbes or determining how reproduction cycle genes in _Azolla_ compare to homologous genes in seed plants.

I do not claim to address all bioinformatics questions related to the _Azolla_ symbiosis, nor do I claim to fully understand the system.
Instead, I aim to set the context in which I am working.
The _Azolla_ genome was the first fern genome ever published.
We are just beginning to delve into fern genomics with bioinformatics.
It is a long-term goal that my research contributes to a better genomic understanding of _Azolla_ and symbioses in general.
Genomic knowledge and expertise are merely steps toward the ultimate goal of understanding the system.

## Genomics for Breeding Novel Crops

Genomics and bioinformatics have revolutionised plant breeding by enabling unprecedented precision and speed in selecting desirable traits.
Where traditional breeding relied on time-consuming phenotypic selection across generations, modern genomics allows breeders to directly target specific genes associated with key traits.
High-throughput sequencing, coupled with bioinformatics tools, enables the rapid identification of genetic markers linked to disease resistance, yield, and stress tolerance.
This shift has not only accelerated breeding cycles but also opened new possibilities for improving crop resilience and productivity in ways previously unimaginable.

Despite these advances, traditional breeding methods can still be slow and may inadvertently reduce genetic diversity.
Repeated selection for specific traits can narrow a crop's gene pool, making it more vulnerable to diseases, droughts, or other stresses.
<!-- needs reference -->
To counter this, researchers have begun reintroducing desirable traits from wild relatives using modern molecular breeding techniques.
One striking example is the de novo domestication of wild tomato varieties using CRISPR-Cas9 gene-editing technology [@Li2018b].
By disabling key genes involved in domestication, researchers recreated domesticated traits in wild tomatoes, resulting in a crop that retained the stress resilience of its wild ancestors while gaining the desirable traits of commercial varieties.

This approach has also been successfully applied to other crops, such as the ground cherry, an orphan crop related to tomatoes.
Using knowledge gained from tomato genomics, researchers were able to gene-edit ground cherry, enhancing its yield and making it more suitable for agriculture [@Lemmon2018a].
These examples highlight the power of genomic insights and gene-editing technologies to rapidly domesticate new crops while preserving genetic diversity and enhancing resilience.

For novel crops like _Azolla_, these technologies offer a pathway to overcome its current limitations.
However, _Azolla_ researchers currently lack the extensive genomic resources available for crops like tomato.
Moreover, robust gene-editing protocols have yet to be established for _Azolla_ and its symbionts.
Still, with continued research into its genomics and reproduction, the domestication of _Azolla_ could follow a similar trajectory, transforming it into a valuable crop for sustainable agriculture [@Schluepmann2022].

Establishing a gene-editing protocol for _Azolla_ would not only facilitate its domestication but also provide a powerful tool for functional genomics in ferns.
Although growing gene-edited crops remains controversial, these techniques are invaluable for understanding gene function and improving crop traits.
With its genome sequenced and the potential for genetic modification, _Azolla_ is well-positioned to become a model organism among non-seed plants.

In summary, while the road to _Azolla_ domestication is still long, the application of genomics and gene-editing technologies offers a promising future.
As research progresses, these tools could help _Azolla_ realise its full potential as a sustainable crop, tailored to meet the challenges of modern agriculture.

<!-- 
High-throughput sequencing and advanced computational tools allow breeders and researchers to dissect the genetic basis of complex traits, enabling more efficient selection and breeding strategies
[Bioinformatics approaches and applications in plant biotechnology | Journal of Genetic Engineering and Biotechnology | Full Text](https://jgeb.springeropen.com/articles/10.1186/s43141-022-00394-5).
With GMO and gene editing technology, these insights can be tested in a living plant with amazing speed if a reliable transformation protocol is available
[CRISPR-Cas9 based molecular breeding in crop plants: a review | Molecular Biology Reports](https://link.springer.com/article/10.1007/s11033-023-09086-w).

[Bioinformatics approaches and applications in plant biotechnology | Journal of Genetic Engineering and Biotechnology | Full Text](https://jgeb.springeropen.com/articles/10.1186/s43141-022-00394-5)
[Advances in Integrating Genomics and Bioinformatics in the Plant Breeding Pipeline](https://www.mdpi.com/2077-0472/8/6/75).
[Bioinformatics in Plant Breeding and Research on Disease Resistance](https://www.mdpi.com/2223-7747/11/22/3118).

[Impact of Bioinformatics on Plant Science Research and Crop Improvement | SpringerLink](https://link.springer.com/chapter/10.1007/978-3-030-19318-8_2) 
[Application of Bioinformatics in Crop Improvement | SpringerLink](https://link.springer.com/chapter/10.1007/978-981-16-2339-4_30). 

-->

## Genomics for Breeding a Symbiosis

Molecular breeding has its roots in the study of DNA, leading to the field of genomics.
Consequently, symbiosis breeding relies on metagenomics—the study of all DNA associated with an organ or organism.
Unlike traditional microbiome profiling, which often relies on 16S rRNA gene sequencing to identify microbial taxa, metagenomics aims to reconstruct full genomes of all associated organisms.
This approach reveals the complete metabolic potential of the symbionts, providing a more detailed understanding of their roles in the host’s biology.

By sequencing both the host and symbiont genomes, researchers can hypothesise which genes are involved in key symbiotic functions, such as nutrient exchange, stress tolerance, and pathogen resistance.
This genomic data allows for targeted hypothesis generation, enabling the investigation of metabolic interactions and potential gene targets for enhancing symbiosis.
In the _Azolla_ symbiosis, specifically, we hypothesise that some symbiosis partners might actually leach nitrogen fixed by _T. azollae_, as discussed in Chapter \ref{foul_play}.
These "foul players" might be parasites rather than mutualists.
Understanding these dynamics through metagenomics could lead to strategies for optimising symbiotic efficiency, such as removing parasitic partners or enhancing beneficial ones.

Despite its promise, microbiome editing—particularly in complex symbiotic systems—remains a formidable challenge [@Bai2023].
Editing a single microbial species is already difficult, often requiring the ability to grow the microbe in isolation and develop a transformation protocol.
In a symbiotic system, these challenges are magnified by the need to reintroduce the modified microbe into the host and ensure it occupies the same ecological niche as the original strain [@Albright2022].
Alternatively, one can introduce a similar strain with desirable traits into the symbiotic community, which requires a deep ecological understanding to succeed [@Albright2022].

In the _Azolla_ symbiosis, researchers have managed to isolate and culture several bacterial strains; however, reintroducing them into the _Azolla_ leaf pockets has yet to be achieved.
This step is crucial for any future attempts at microbiome editing in _Azolla_.
While these advanced techniques remain on the horizon, the focus now is on identifying and characterising the symbiotic partners.
In Chapter \ref{forever_together}, sequencing data from multiple _Azolla_ species is used to retrieve microbial genomes associated with the genus.
This effort provides a foundation for understanding the symbiosis at a genomic level.

Later, we venture into meta-transcriptomics to investigate what processes are active in these microbes, though we gain little signal about which genes are active in these microbes (Chapter \ref{it_takes_two}).

## Gene Editing Ethics

Throughout this introduction, I have highlighted the potential of _Azolla_ and how modern breeding techniques could further enhance its value.
However, I have naively avoided discussing the ethical implications of deploying gene-edited crops into the environment.

Gene editing offers immense value, even if such crops are not introduced into agriculture.
It can accelerate breeding cycles, test biological hypotheses, and advance fundamental research.
Banning gene-edited crops solely because they involve gene editing leads to inconsistencies.
For instance, two genetically identical plants might be treated differently when gene editing is illegal: the first crop, created through traditional methods, is legal, while the other, created through efficient gene editing, is illegal.
Countries like the U.S., Canada, and Brazil have embraced more permissive laws, while the European Union's strict classification of gene-edited crops as GMOs frustrates many scientists.

Critics often point to off-target effects—unintended DNA changes—as a concern.
However, this argument overlooks that traditional breeding methods also cause significant, unregulated genetic alterations.
Research has shown that off-target edits are very rare.

Societal concerns about gene editing are more compelling.
The promises made during the introduction of GMOs largely benefited biotech companies, often at the expense of farmers in developing countries.
The risk of gene-edited organisms being patented further complicates matters.
If our goal as scientists is to feed the world, we must be cautious about how this technology is used and who controls it.
We have a role in influencing legislation and ensuring our work is used ethically.

The open science movement advocates for transparency and accessibility in research.
Should we apply these principles to gene editing?
Given that our research is publicly funded, should our findings also belong to the public?
Perhaps we should make all DNA constructs publicly available, as we do with raw data, and consider restricting their use for profit.

This is a complex issue.
While preventing commercial exploitation might seem ideal, it could also deter companies from using our discoveries, limiting their public benefit.
We must carefully consider how to implement gene editing responsibly, avoiding the pitfalls encountered with GMOs.

In Europe, gene editing may remain a research tool, or, like in the U.S., exceptions might be made when traditional breeding could achieve the same results.
Alternatively, Canada’s case-by-case approach could offer a balanced path forward.
As a researcher, I believe in the potential of gene editing for crop improvement and enhancing symbioses like _Azolla_, but it must be pursued thoughtfully.

## Introducing Bioinformatics to a Lab

The _Azolla_ lab was part of the molecular plant physiology group at Utrecht University before it was dissolved.
In its early days, the lab focused on optimising the growth and analysing extracts of _Azolla_ biomass.
Introducing bioinformatics to a small lab of three employees with no prior experience was challenging.
This process began during my Masters when I started working on _Azolla_.
Infrastructure issues, such as storage and computing power, were quickly addressed with funding to build a computer and support from the local theoretical biology and bioinformatics group.

The main challenge was building foundational knowledge in programming, handling NGS data, and conducting computational science.
As a computer-savvy student with no bioinformatics training, I was fortunate to attend PhD courses on bioinformatics techniques like metagenomics and RNAseq.
I also received advice from collaborators and bioinformaticians in the department, which helped us publish our first bioinformatics-centered paper (Chapter \ref{foul_play}) within two years of starting the project.
During my PhD, we expanded the lab’s bioinformatics toolkit to include small RNA sequencing, comparative genomics, and nanopore sequencing.

As we faced challenges integrating bioinformatics into a molecular context, so did our students.
The _Azolla_ lab, being a molecular biology lab focused on a novel crop with potential for sustainability research, struggled to attract students with bioinformatics training.
These students needed to analyse bioinformatics-related data but lacked basic computational training.
Given the increasing size of experimental biology datasets, this lack of coding skills seemed undesirable to me.
Teaching students the basics of coding is a strain on a hosting lab.
We eventually developed a flexible co-supervision system among two PhDs and a PI.
This work paid off, as summarised in Chapter \ref{it_takes_two}, which humorously became known as “all student projects of the last years combined into one paper.”

Our experiences taught us that introducing bioinformatics into a molecular biology lab requires more than just acquiring tools and infrastructure.
It involves creating a supportive environment where both students and researchers can develop the necessary computational skills, and where continuous learning is encouraged, and computational work is valued alongside experimental work.

Transitioning from the wet lab to the computer lab posed additional challenges, particularly with documentation and lab journaling.
It surprised me that despite the obvious need for documenting wet lab experiments, students and staff rarely kept notes when doing computer work.
I struggled with this myself during my PhD, trying various methods such as physical journals, Word documents, and long comment lines in scripts.
Bioinformatics education is still relatively young, and perhaps documentation and journaling need to be emphasised more in computer lab projects.
In molecular biology labs at Utrecht University, maintaining a digital lab journal is standardised and obligatory, but no such standard exists in the computer lab.

My personal process evolved from writing loose scripts organised in folders and keeping analytical thoughts in separate notes to committing to writing read-me files and using version control software like Git.
This habit became so ingrained that even this thesis was written in code (Markdown & LaTeX) with all versions tracked in Git.
Biological results, interpretations, and speculations were kept in separate digital notes, which allowed for a more natural combination of results and ideas from various coding projects.
Near the end of my PhD, I started using code notebooks containing R, Python, and BASH code, which integrated code, output, and a research narrative.

Working with code notebooks was so successful that I set up facilities for the entire lab to write code notebooks in a web browser.
The code ran on our local server, using professional hardware with direct access to all our data.
The phylogeny notebook, in particular, became successful, leading to several publications associated with our papers, as described in Chapter \ref{one_two_tree}.

Reflecting on our achievements, I am proud of what we accomplished with _Azolla_ genomics, especially considering the lab started from scratch in 2014.
Despite the challenges and limitations, we made significant progress in my nearly seven years at the lab as a student, PhD candidate, and part-time teacher.
There is still much work to do to understand and manipulate the symbiosis, and I hope that other labs around the world will find our work useful for their experiments.

# Outline of this Thesis

**Chapter \ref{general_intro}** (\nameref{general_intro} on page \pageref{general_intro}) is the current chapter.
I attempted to take a broader vantage point and use less jargon than in the remaining chapters.
A less formal tone was intended to make this chapter more engaging for a broader scientific audience interested in my work.

**Chapter \ref{foul_play}** (\nameref{foul_play} on page \pageref{foul_play}) details the initial discovery of prokaryotic DNA sequences in the _A. filiculoides_ genome assembly.
These bacteria associated with _Azolla_ were the main inspiration for this PhD project.
We identify nearly complete bacterial genomes in whole contigs of this assembly and study them further.
These bacteria are confirmed to be present in _A. filiculoides_ samples from both the wild and the lab.
Non-cyanobacterial prokaryotes are confirmed to be associated with all _Azolla_ species for which WGS data is available.
They may be the same or very closely related microbes.
Finally, we study the metabolic pathways encoded within these genomes and hypothesise that they might denitrify nitrogen-rich compounds within the _A. filiculoides_ leaf pocket.
This hypothesis is falsified, however, as denitrification occurs only in microbes living epiphytically on _A. filiculoides_.

In **Chapter \ref{hidden_treasures}** (\nameref{hidden_treasures} on page \pageref{hidden_treasures}), I build further on the work of Chapter \ref{foul_play}.
This chapter details a workflow to enrich and study the genomes of bacteria associated with all sequenced _Azolla_ species.
The workflow thoroughly removes plant DNA reads and then assembles those of the remaining microbes.
The process of separating distinct microbial genomes (binning) required additional binning signals and manual curation, as these were not part of the original experimental design.
Each _Azolla_ species yielded between 12 and 22 associated bacterial genomes.
The majority of these genomes belong to six taxonomical orders present across the entire _Azolla_ genus: Burkholderiales, Caulobacterales, Nevskiales, Nostocales, Rhizobiales, and Sphingomonadales.
The systematic presence of these taxonomic groups suggests they are selected for in the _Azolla_ symbiosis and may be vertically transferred across host generations, similar to the main symbiont _N. azollae_.

**Appendix \ref{metagenomics_practical}** (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}) illustrates an educational practical based on the first two chapters.
I designed this practical to teach basic metagenomics principles and techniques to Life Sciences students with minimal coding experience.
The practical introduces the Bash language and aims to teach the main concepts behind metagenomics through a hands-on approach.
It starts with a metagenome assembly and guides students through DNA mapping, binning, quality control, gene annotation, and finally, plotting metabolic pathways.
Exercises are implemented in JuPyter notebooks, combining code-writing with text instructions.
The practical is freely available on GitHub here: [github.com/lauralwd/metagenomicspractical](https://github.com/lauralwd/metagenomicspractical).

**Chapter \ref{forever_together}** (\nameref{forever_together} on page \pageref{forever_together}) describes the genomics of the main _Azolla_ symbiont, _N. azollae_, using the genomes assembled in Chapter \ref{hidden_treasures}.
All _N. azollae_ share nearly identical genomes and gene content, indicating they are the same species of _N. azollae_, hosted in various _Azolla_ species.
The _N. azollae_ genome is degraded due to high pseudogene content.
Pseudogenation is caused by high transposon activity early in the symbiosis, but this activity has since slowed down.
A _N. azollae_-specific gene set was identified by comparing many near-complete genomes in the Nostocales family.
A phylogenomics approach confirms that the organisation of genera in this family is paraphyletic, but places _N. azollae_ close to _Anabaena_ species.

**Chapter \ref{it_takes_two}** (\nameref{it_takes_two} on page \pageref{it_takes_two}) provides building blocks for understanding and regulating the sexual reproduction and mode of transmission of the _Azolla_ and _N. azollae_ symbiosis.
Such understanding is a prerequisite for the agricultural application of a novel crop symbiosis.
Several _Azolla_ specimens collected from across the Netherlands were found to be the same species as they produced viable offspring.
We discovered that far-red (FR) light and sporophyte density were the main initiators of sexual reproduction, while nitrogen availability was an inhibitor.
FR-responsive transcripts included MIKCC homologues of CMADS1 and miR319-controlled GAMYB transcription factors in the fern, transporters in _N. azollae_, and ycf2 in chloroplasts.
Phylogenomic analyses of MIKCC transcription factors suggested that the control of flowering and flower organ specification may have originated from the diploid to haploid phase transition in the homosporous common ancestor of ferns and seed plants.

Sexual reproduction of the symbiosis requires that the symbiont is systematically stored in dissemination stages to reinoculate the next generation of hosts.
Contrary to earlier theories, we propose that _N. azollae_ does not colonise developing megasporocarps by travelling from leaf pockets to megasporocarps via small channels.
Instead, we theorise that they colonise early sporocarp initials of both types but are only retained in megasporocarps.
This method of transmission is identical to the colonisation of leaf primordia, requiring no separate machinery and explaining the consistent observation of _N. azollae_ in very young microsporocarps.

**Chapter \ref{phylogeny_workflow}** (\nameref{phylogeny_workflow} on page \pageref{phylogeny_workflow}) describes a workflow for creating large, state-of-the-art phylogenetic trees of gene families, exemplified in land plants.
Studying fern genetics, the _Azolla_ lab often deals with fern genes that are homologous (similar in sequence) to seed plant genes.
With phylogeny, we aim to assess the evolution of a gene family and the orthology/paralogy of _Azolla_ genes to model species genes.
While many user-friendly methods exist to create phylogenetic trees, these are often either closed-source or limited in performance.
Here, I created a workflow for basic phylogeny inference using state-of-the-art open-source tools, unlimited in their performance.
This workflow is aimed at users skilled in reading phylogeny but not necessarily in using the command-line tools required to use the latest software for building them.
It covers data selection, multiple sequence alignment, alignment trimming, and tree inference.
Additionally, it provides tools to create semi-automatic mark-up for phylogenetic trees in the iToL web interface.

## Appendices

Academics are more than just scientists; they are often also teachers at universities and leaders and administrators in academic organisations.
During my PhD, I attempted to incorporate that broader academic experience into my work.
While the doctorate remains intrinsically a scientific degree, and this thesis is first and foremost a scientific document, I have included three appendices that offer a glimpse into my "extracurricular" activities.
My thesis —the culmination of my PhD— would not be complete without them.

Firstly, **Appendix \ref{BKO}** summarises my Basic University Teaching Qualification (bUTQ or BKO) application.
About a quarter of my PhD time was spent on teaching and developing myself as a teacher.
This effort was rewarded with a bUTQ (BKO in Dutch).
The full portfolio is too lengthy to include, so this appendix summarises the original document.
Secondly, an example of teaching material that is entirely of my own design is included in **Appendix \ref{metagenomics_practical}** (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}), as mentioned earlier.
In this practical, students perform all the major steps of Chapter \ref{hidden_treasures} in a day or two.
Finally, I include a short narrative CV on my non-science and non-teaching activities during my PhD and what I gained from them.

**Appendix \ref{metagenomics_practical}** details the development of a computer practical on the basics of metagenomics, with data and research questions taken from Chapter \ref{foul_play}.

**Appendix \ref{portfolio}** contains a personal portfolio of non-research activities during my PhD.
These activities made my time as a PhD student more rounded and representative of the academic experience.

In summary, this thesis aims to explore the intricate symbiosis between _Azolla_ and its cyanobacterial partner _Trichormus azollae_, with a focus on understanding the genomic foundations underpinning this relationship.
Through a combination of genomic, metagenomic, and other bioinformatics approaches, this research seeks to shed light on the evolution and molecular mechanisms driving the symbiosis.
Additionally, we assess the broader microbial community associated with _Azolla_ and evaluate the potential applications of this system in sustainable agriculture.
By addressing these questions, the work presented here not only contributes to our fundamental understanding of symbioses but also explores practical avenues for harnessing _Azolla_'s unique capabilities in addressing some of the pressing agricultural challenges of our time.

\nolinenumbers

<!-- close the last page of this section as required for removing the thumb index on next "part page" -->
\newpage
\null
<!-- don't show page nrs on clear double page -->
\pagestyle{plain}
<!-- stop the thumb marking scheme (part-wise) and start it (chapter-wise) in the next chapter -->
\stopthumb
<!-- clear double page so that the chapters start nicely on a new right page -->
\cleardoublepage
