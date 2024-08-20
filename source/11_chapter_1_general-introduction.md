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

This hitch-hiker's guide is meant to be a friendly general introduction to this thesis.
The thesis describes the genomics of the _Azolla_ symbiosis: that of _Azolla_ ferns, its main symbiont _Trichormus_ (or _Nostoc_) _azollae_, and other bacterial partners.
Its chapters will discuss the discovery of those other bacterial partners and the identity and evolution of the main symbiont.
The final chapters center around the symbiosis' reproductive cycle and some methodology.
This is all new information on the _Azolla_ symbiosis, and I will argue important information for modern breeding of _Azolla_.
There will be a lot of bioinformatics, some molecular biology and some ecology now and then.
All individual chapters already have in-depth stand-alone introductions.
So in this general introduction, I mean to give a broader context and perspective on symbiosis research, the amazing _Azolla_, and relevant genomics methodologies.
I will argue how a systems biology mindset can benefit symbiosis research.
Then I will provide a broader context on the _Azolla_ symbiosis.
And finally I will discuss bioinformatics techniques to address the relevant questions and hypotheses of this PhD project.
I attempted to make this introduction palpable for all scientific audiences, not just (plant)biologists.
There will be a bit of humour, opinion, and informal writing.

\newpage

> _“A system is never the sum of its parts it's the product of their interaction.”_

– Russell Ackoff (professor of systems sciences)

or...

> _"Biologists tend not to talk about the big ideas; we leave those to physicists. We biologists tend to be more comfortable with details, we like to count and list things."_

– Sir Paul Nurse (Chief Executive Director Francis Crick Institute)

# A system perspective

When imagining an ecosystem, one typically thinks of a forest with trees, animals, and insects.
Perhaps some fish swim in a stream.
All are idyllically thriving as a balanced part of a larger whole.
The concept emphasises the abundance and complexity of interactions within the larger system, rather than the individualistic existence of the loose parts.
Yet, when one imagines a biological experiment, they think of lab coats, petri dishes, and perhaps microscopes.
They are not wrong; science has thrived under reductionism.
Scientific experiments often strive to control one variable at a time to isolate its effects.
All other variations are reduced by working with one species or strain at a time, treated exactly the same except for that one experimental variable.
The organism is dislodged from its natural environment to prevent it from meddling with the experiment.
We, scientists, call this: 'controlled conditions'.
The ultimate goal is to gain mechanistic insight into the workings of a biological system; one part at a time.
The underlying reasoning is that if we know the function of all its parts, we then know the system.

The reductionist dogma yielded considerable advances in biological research; I wouldn't dream of debating this.
But I will argue that it occasionally falls short in encompassing emergent properties of a larger whole.
The complexity of real-world biology does not always allow for isolating one variable from the rest of the system.
Nor does changing one variable in a system always lead to robust change.
For examples of the former, this thesis describes such a system.
The latter, I find exemplified in recent attempts at microbiome editing.
A microbiome is the collection of all microbial organisms associated with any organ or organism.
Such a collection often contains millions of cells of hundreds of strains if not more.
I think it is very optimistic to take one of these strains, edit it in some often genetic way, and expect robust change.
Plenty of examples in literature support this opinion [@Bai2023; @Mueller2015a].
Instead, a perspective of the entire (eco)system and ecological lessons from macroecology may be required for sustained microbiome editing [@Albright2022].
It requires a system perspective.

Even within the confines of a cell, the reductionist view on biology is subject to scrutiny.
Mechanistic studies often research the workings of single components in the cell, and then perhaps place these into metabolic pathways.
These pathways turn into a vast network of cause and effect.
One can follow how one compound finds its way through the network, being turned into another compound.
Or see how a signal at one point gets amplified and transmitted to some other point.
We have learned to view the cell's metabolism as a chemical machine pursuing homeostasis or equilibrium.
This idea is over a century old [@Nicholson2019].

@Nicholson2019 poses that perhaps we should abandon our view of the cell as a mechanical reductionist entity to be studied solely through its molecular components.
The machine conception of the cell is a misleading representation of biological reality, he argues.
An overview of cause-and-effect relations falls short of capturing the non-linearity, stochasticity, and plasticity of cellular behaviour [@Nicholson2019].
Groups of cells' response to a stimulus is not gradual and homogenous.
Instead their response switches on or off stochastically and heterogeneously [@Altschuler2010].
<!-- like how radioactive matter decays. inherrent quantum randomness seems like a gradual predictable progress when one takes millions of molecules.
Except radioactive decay, doesn't influence other molecules in complicated pathways. -->
Similarly, protein complexes are not static assemblies as engineered machines are.
Instead, they self-organise with often multi-functional parts that come on and off constantly. [@Nicholson2019; @Dumont2014]
Apply this state of flux to all parts of a network of metabolic reactions, and imagine the consequential chaos.
This chaotic cell is a collection of semi-stable processes that constantly self-organise in alternate steady states.
A system far from equilibrium, seemingly inefficient and costly, but flexible and robust as a consequence [@Nicholson2019].
@Nicholson2019 is a great read, and I will not blame anyone who puts away this thesis and picks up his article instead.

In this section, I argue not for the abandonment of mechanistic research, but for complementing it with a systems biology perspective.
A task well suited for biologists, who are trained from the onset to think at varying scales; from molecule to ecosystem.
In fact, my bachelor studies were organised this very way.
Yet, somehow, something so obvious to a first-year biology student becomes an afterthought in reductionist scientific practice.

# Symbiosis

Perhaps the study of symbioses takes place in between the ambition of system understanding and the practice of mechanistic research.
The molecular biology methods common to the reductionist dogma remain the field's standard that my colleagues and I want to adhere to, also in this work.
We need to, for we study a young system.
This requires to first do some groundwork.
But we should always ask ourselves what our findings mean for the system as a whole.
Or, more often than not, we are forced to work with the system as a whole.
This work focuses on an obligate symbiosis.
In the context of this thesis, one symbiont without the other is either not viable or deeply unhealthy.
Studying them in isolation without the perspective of the entire symbiosis risks being short-sighted.

By definition, symbiosis is a long-term interaction of two or more organisms.
They often can be categorised as:

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

The original premise of this PhD project includes thoughts on symbiosis breeding, specifically mutualist or commensalist associations.
The organisms of choice here, are part of an obligate symbiosis focused on nutrient acquisition; specifically nitrogen.
At the time, we reasoned that molecular pathways of host and symbiont would be intricately interconnected.
Hence, any breeding efforts of the host plant should not be limited to the plant physiology and genomics, but include those of its symbiont.

Typically, research into breeding symbioses focuses on breeding plant properties for increased symbiosis functioning [@Liu2020; @Thirkell2022].
These functions revolve around nutrient acquisition in root-nodule type- and mycorrhizzal -symbioses.
For symbiosis traits, breeding a symbiont should perhaps take precedence over breeding the host.
We advocated then, that breeding a functionally intertwined unit of organisms requires that systems biology perspective.
Understanding and eventually manipulation of a plant-microbe symbiosis needs a perspective that integrates ecological, physiological, and (meta)genomic data.
Indeed, breeding or even gene-editing assemblages of obligate symbionts is a paperwork nightmare and comes with a plethora of practical obstacles.
But, for example, breeding symbiotic nitrogen acquisition in a root-nodule type symbiosis only via plant properties seems odd to me.
After all, it is the microbes that do the actual nitrogen acquisition.

With symbiosis breeding, I naively advocate breeding both the host and the symbionts who contribute a function to the symbiosis.
Naively, because I omit discussion of all the practical and legislational barriers.
Breeding a symbiosis requires a perspective including all relevant organisms, their genomes and their relations to each other.
I would say a systems perspective, but equally valid, others would say a holistic perspective including every symbiont.
In symbiosis literature, a new term was proposed for such an assemblage: a holobiont [@Zilber-Rosenberg2008].

## The holobiont concept

The holobiont concept is a recent proposition in evolutionary jargon [@Zilber-Rosenberg2008; @Rosenberg2016].
It proposes to think of a host and a symbiont as one unit of evolutionary selection.
This is not a far fetch in the case of an obligate symbiosis where a microbiome is actively transferred to subsequent host generations.
It might be odd even, to argue that systematically inherited DNA should be regarded as a separate evolutionary unit based solely on the compartment it is housed in.
We rarely find this useful for organelles either, although examples do exist in literature [@Keeling2010; @Perez-Escobar2016].
The holobiont concept paves the way for some interesting thought experiments.
Could a fast-evolving bacterial section of the hologenome (all genetic material of a holobiont) provide flexibility to the stationary host genome.
This may explain the fast adaptations of microbiomes to their hosts.

After advocating a systems biology perspective on symbiosis research, the holobiont concept seems fitting in this work.
Yet, the concept is also criticised [@Douglas2016].
The holobiont is also argued to be a romantic over-simplification of a set of complex interactions.
Holobiont members may interact beneficially as well as antagonistically.
Additionally, a lack of consistency in a species consortium may challenge the evolutionary pressure exerted on them as a whole.
Critics of the concept suggest that traditional ecological and evolutionary frameworks suffice for what could be called a holobiont.
Where does one draw a line: a plant interacts with plastids, perhaps endosymbionts, external symbionts like mycorrhiza, pollinators and maybe animals for seed distribution.
@Douglas2016 argues that existing frameworks are better equipped to handle nuances and conflicts between symbiosis partners.

I have not decided on the matter yet, although I am inclined to agree with the critics for most scenarios.
Yet, if we can find use in thinking of a single gene as an evolutionary unit [@Dawkins2016], then perhaps the holobiont perspective has use as well.
Either models will undoubtedly be wrong, but perhaps occasionally insightful.
It seems unproductive to me, to use holobiont as a buzz-word; as a means to elevate a consortium of organisms above others.
In this thesis, my colleagues and I do use the word occasionally.
Take it with a pinch of salt.

At the bottom line, biological entities exist at a huge scale range from the smallest molecules to entire ecosystems, or even the entire planet.
Take any entity at any scale, and one can defend it as either being selfish or cooperative.
The lesson I take from the holobiont polemic, is again to take a systems perspective; to emphasise relations and processes over the individual parts.

# The _Azolla_ symbiosis
<!-- Perhaps this section needs re-organising.
Claude says:
Azolla physiology and life cycle
- General Azolla physiology
- Life cycle
- Cyanobacterial symbiosis (general overview)
- Trichormus azollae (specific symbiont details)

Ecology and natural history
- Natural habitats and distribution
- Ecological role and interactions

Agricultural history and opportunities
- Traditional uses in agriculture
- Modern agricultural potential

Challenges and the need for domestication
- Current limitations in Azolla use
- Goals for domestication
  
 -->

This work discusses the genomics and metagenomics of a specific symbiosis: that between the floating fern genus _Azolla_, and a cyanobacterium _Nostoc azollae_.
The Cyanobacterium supplies the symbioses with a surplus of nitrogen fixed from the air.
Unlike most plants, _Azolla_ is not terrestrial.
Instead, the symbiosis floats on water.
_Azolla_ its aquatic lifestyle makes the fern highly dependent on fresh water.
Even its name is derived from this property, ἄζος (Azos) is ancient greek for 'drought' and ὀλλύναι (ollunai) for 'killing'.
The fern spreads horizontally over the water surface, darkening the water column.
This property makes _Azolla_ as infamous under ecologists, as it is famous in symbiosis research [@Madeira2016a].
Bigger plants break irregularly into smaller ones, genetically identical, but physically separate; forming a big green floating mat.
_Azolla_ mats are known for their high growth rate and high protein content.
A mat can grow so spectacularly fast, that _Azolla_ is thought to have overgrown the entire north pole for some time in geological history [@Brinkhuis2006].
This "_Azolla_ event" is associated with a steep decline in global CO2 concentration in the air.
Within human history, _Azolla_ has traditionally been used in rice paddy fields [@Wagner1997b;@Shi1988].
Its main function was to prevent toxic cyanobacteria from growing in the water.
Any surplus was fed to livestock.
Some of today's agricultural challenges seem to be a perfect fit for _Azolla_: limited arable land, nitrogen fertilizer excesses, and protein shortage [@Bijl2014].
_Azolla_ is an amazingly interesting plant, in this section I'll elaborate shortly on all these statements.
I mean to give some broader context that lacks from individual chapters' introductions.

## _Azolla_ physiology

_Azolla_ stems spread horizontally over the water surface.
At stem nodes, leaves and roots are attached.
_Azolla_ leaves are highly adapted to the fern's living style.
They are bi-lobed; both lobes being directed either up- or down-ward.
The lower lobe is razor-thin, translucent-looking and concave.
It lies on the water like a boat, suspending the stem and upper leaf lobe above.
The upper lobe is thick; almost balloon-like, and typically dark green.
Inside this the upper lobe, a special organ houses the symbiotic bacteria.
The leaves typically grow in a compact cabbage-like fashion; giving the whole plant a fish-scale appearance.
The earliest scientific description of the plant I could find is @Strasburger1873.

<!-- insert macro photo Azolla, macro photo stem tip, microscope photo starting colony -->

All organs find their origin at the tip of the stem, at the shoot apical meristem (SAM).
The SAM produces primordia, little bulges, which develop into leaves, roots, and sporocarps.
Sporocarps are the ferns reproductive structures.
The SAM also harbours a small colony with motile filaments of the cyanobacterium _T. azollae_.
Both leaves and sporocarps encapsulate part of the starting colony during growth.
This process ensures that all leaves have a colony of the symbiont. [@Campbell1893]

## The Azolla Leaf Cavity

The leaf cavity, or leaf pocket, of _Azolla_ is a specialized structure that plays a crucial role in its symbiosis with the cyanobacterium _Trichormus azollae_.
These cavities are located within the upper lobes of _Azolla_ leaves and serve as protective niches where the cyanobiont resides.
This unique adaptation allows _Azolla_ to house a stable population of _T. azollae_ within its tissues, ensuring a constant supply of fixed nitrogen directly to the plant.
The cyanobacteria within these cavities are effectively sheltered from environmental fluctuations, such as changes in light intensity and water availability, which might otherwise impede their nitrogen-fixing capabilities.
The leaf cavity not only provides a habitat for _T. azollae_ but also facilitates a tightly regulated exchange of nutrients between the host and symbiont.
The cyanobacteria contribute nitrogen compounds that are essential for the growth of _Azolla_, while the fern supplies organic carbon derived from photosynthesis, creating a mutually beneficial relationship.
This symbiotic arrangement within the leaf cavity is a prime example of the intricate evolutionary adaptations that have enabled _Azolla_ to thrive in nutrient-poor aquatic environments.
Understanding the structure and function of these leaf cavities is essential for unraveling the complexities of the _Azolla_ symbiosis and holds potential implications for biotechnological applications in sustainable agriculture.

Azolla roots can be observed hanging loosely in the water like a thin curtain.
On time-lapses, the roots were seen swirling and curling.
<!-- insert link to time-lapse -->
Roots of individual plant fronts grabbed onto each other like rugby players locking shoulders in a scrum
This way, individual plants formed a cohesive mat, keeping together.
I suspect this phenomenon may help in creating favourable conditions for the symbiosis.
It may help in stratifying the water column, keeping nutrients from dying plants close to the plant roots for re-absorption.
Azolla can rapidly and massively shed its roots, which may be a mechanism to leave a certain area [@Cohen2015a].

Interestingly, Azolla roots respond distinctly to typical plant hormones compared to flowering plant's roots [@deVries2016].
Roots were likely invented twice in plant history: in lycophytes and ferns (reviewed in @Spencer2021).
The fern-invented roots were passed down to seed plants.
However, not all roots will have developed the same since their original invention.
In seed plants, the hormone cytokinin promotes cell division in shoots and regulates differentiation growth in roots.
In contrast to the typical response, _Azolla_ roots' cell division is promoted by cytokinin [@deVries2016].
This finding suggests that Azolla roots have an origin as a shoot structure.
They are analogous to plant roots; similar in appearance but separate in origin.

The specifics of _Azolla_ root's origin are not of major consequence to this work.
It does highlight and illustrate that the evolutionary history of _Azolla_ deviated from that of seed plants a very long time ago.
Educated guesses made with a seed-plant background, may be false more often than one thinks.
Now let me also express my dislike for the term "primitive plants".
As if ferns have not diversified, adapted, and evolved since their origin.
I hope this thesis, even this introduction, will help in appreciating the intricacies of the _Azolla_ symbiosis life cycle.
We can discuss "primitiveness" further compared to the brute force of non-pollinated flowers or the extravaganza of a magnolia.

## Cyanobacterial symbiosis

Cyanobacterial symbioses are widespread and diverse.
They span various ecosystems: like marine environments, freshwater systems, and terrestrial habitats.
Cyanobacteria form mutualistic associations with a wide range of hosts, including plants, fungi, protists, and even animals.
In marine systems, symbiosis partners can be sponges or diatoms.
In freshwater systems, the _Azolla_ symbiosis is a prime example.
Terrestrial hosts can be cycads (plants), mosses, but also lichens (fungi).
These symbioses are mostly not obligate; most cyanobacteria can live independently from their host. [@Peters1991]

The _Azolla_-_Nostoc_ symbiosis is perhaps most related to moss-cyanobacterium symbioses.
Moss-cyanobacterium symbioses are particularly present in boreal and temperate regions.
Host mosses like _Sphagnum_ and _Pleurozium schreberi_ attract nitrogen-fixing cyanobacteria, primarily from the genus _Nostoc_ and _Anabaena_ [@Bay2013a].
The cyanobacteria provide their host mosses with nitrogen by fixing atmospheric nitrogen [@Rousk2022].
This relationship is a big competitive advantage in nutrient-poor environments [@Alvarenga2022].
The symbiosis significantly contributes to the nitrogen budget and supports the growth of both mosses and the surrounding plant community [@Calabria2020].
In moss-cyanobacteria associations, the cyanobacteria are often acquired from the environment by each moss generation [@Liu2022].
The cyanobacteria can also live without a host in these environments, and culturing and inoculation protocols are established.
This is unlike the _Azolla_-_Nostoc_ symbiosis, where cyanobacteria are transferred through fern reproductive structures and the cyanobacteria cannot live without their host [@Peters1991].
<!-- Moss picture with punctiforme? -->

Cyanobacteria that associate with mosses, and also with Azolla, are often part of the Nostocaceae family.
The Nostocaceae family comprises several genera of cyanobacteria known for their filamentous, colony-forming structures and their ability to fix nitrogen.
The family includes genera such as _Nostoc_, _Anabaena_, _Trichormus_, and _Cylindrospermum_.
These genera share common features like the presence of specialised heterocyst cells that fix nitrogen under aerobic conditions [@Adams2000].
Phylogenetic studies have shown that the relationships among these genera are complex.
Within a single genus, significant genetic diversity can be observed and several species were moved between genera [@komarek2010; @kastovsky2024].
The genus name of _Azolla_'s cyanobacterial symbiont has also changed throughout the years.

<!-- include phylogeny from a paper or database? -->

## _Anabaena_, _Nostoc_ or _Trichormus_ _azollae_

_Azolla_ species form a unique symbiotic relationship with _Trichormus azollae_; the cyanobacterium resides in specialized leaf cavities of the fern.
The symbiosis main function, from the host-plant perspective, is that _T. azollae_ sequesters di-nitrogen gas from the air and shares this with the host.
Several papers claim to have cultured _T. azollae_ on standard cyanobacterial media like BG11 [@Franche1985; @Zimmerman1987; @abd2013; @Parente2017].
We have tried to do reproduce this ourselves, and have talked to scientists better equipped to do so than us.
Yet all efforts failed.
Additionally, I find that papers claiming a culturing protocol for _T. azollae_ lack proper checks.
More often than not, these checks are a PCR for the very common nitrogenase gene, or a visual check for heterocysts common to many genera of cyanobacteria.
I suspect these works describe cultures of other cyanobacteria, as do others [@Pereira2014; @Ladha1982].
Some independently sequenced genomes of these cultures showed remarkable genomic resemblance.
Perhaps other (not per say symbiotic) cyanobacteria are systematically associated to Azolla, and are in fact culturable [@Pratte2021].

Like the organisation of the Nostocaceae family, the genus name of _T azollae_ is also up for debate [@Pereira2014; @Baker2003].
In most work of our lab, we write _Nostoc azollae_ when we refer to the symbiont.
_N. azollae_ has undergone multiple reclassifications due to advances in phylogenetics.
Traditionally, it has been referred to as _Anabaena azollae_.
Most modern literature refers now to _Nostoc azollae_.
Recent studies favour the classification of this cyanobiont as _Trichormus azollae_ based on comprehensive phylogenetic analyses.
[@Baker2003]
Strictly speaking, _T. azollae_ is the only verified name of the symbiont [@Pereira2014].
It is now also the standard in the NCBI taxonomy database: [NCBI: _T. azollae_](https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=551115) (<https://www.ncbi.nlm.nih.gov/Taxonomy/Browser/wwwtax.cgi?id=551115>).
These taxonomic ambiguities arise from variations in morphological and genetic data that were considered for the phylogeny of the Nostocaceae family.
Re-organisation of taxonomy will always be somewhat chaotic and possibly met by resistance.
In this thesis both _Nostoc azollae_ and _Trichormus azollae_ are used.
The former is used in chapters that were published before this thesis was compiled, the latter in newer work.

<!-- GTDB ANI calculations actually put it with anabaena rather than trichormus. WTF. -->

One of the key papers to understand _T. azollae_ is the original genome publication by Ran et al. [@Ran2010].
The study found the genome of _T azollae_ has undergone substantial reductive evolution.
It contains many broken genes that would otherwise be considered essential for a free-living cyanobacterium.
The genome does contain a complete set of genes required for nitrogen fixation, highlighting the cyanobacterium's crucial role in providing fixed nitrogen to the symbiosis.
These broken genes, or pseudogenes, are often damaged by insertion sequences (IS elements).
_T. azollae_'s genome contains a high amount of IS elements, indicating ongoing and substantial genome reduction and instability.
Lacking many important metabolic genes, _T. azollae_ likely has a high degree of specialization and dependence on the host plant.
I find the Ran et al. paper essential reading for _Azolla_ symbiosis research.
It provides the genetic basis for understanding the metabolic potential of the main symbiont of _Azolla_ ferns.

The genes in the _T. azollae_ genome sequence reveal the symbiont's metabolic potential, as well as its lost metabolic potential.
These features tell us about the workings and evolution of the symbiosis.
For example, @Ran2010 found pathways for the biosynthesis of phytohormones.
These pathways may contribute to the growth and development of _Azolla_, indicating a two-way metabolic intertwined-ness between the two.
Nitrogen gas is fixed with the nitrogenase enzyme into ammonium.
This costly process is powered by energy and redux from the cyanobacterium's own photosynthesis which remains intact.
[@Ran2010; @Eily2019; @Ray1979]
_T. azollae_'s photosynthesis uses a slightly different colour green than the plant does, so they compete less for the same light.
This association allows _Azolla_ to thrive on nitrogen-poor or even nitrogen-free water.
In return, _T. azollae_ is thought to get carbon compounds from the host plant.

### Symbiont genome degradation

Genome degradation seems worrisome but it is a normal and well-documented process for obligate symbioses.
Organelles are extreme examples of this process [@Keeling2010].
Symbiotic bacteria often lose genes that are unnecessary for their specialised lifestyles.
In insects, this process is more elaborately studied than in plants, in part due to the strict obligate nature common to these symbioses [@Wernegreen2002].
For example, the genome of _Buchnera aphidicola_, an endosymbiont of aphids, encodes only essential genes for amino acid synthesis and lost genes involved in DNA repair and regulatory functions [@Chong2019].
Similarly, _Wigglesworthia glossinidia_, a symbiont of tsetse flies, has a genome of approximately 700 kilobases.
These 700kb contain genes vital for the biosynthesis of vitamins needed by the fly, but lack many metabolic pathways considered essential for free-living bacteria [@Heller2011].
In an even more extreme case, _Carsonella ruddii_, the endosymbiont of psyllids, has the smallest known bacterial genome at about 160 kilobases.
The symbiont has a minimal set of genes required for protein synthesis and essential nutrient production [@Khachane2007].
These studies exemplify how genome reduction plays a part in symbiont's specialisation and their dependence on their hosts for other needs.

<!-- Should I lose this last paragraph/section? -->

## Ecology

_Azolla_ naturally thrives in a variety of nutrient-rich freshwater environments including ponds, lakes, slow-moving streams, and wetlands.
These habitats provide the ideal conditions for _Azolla_'s growth, such as abundant water and nutrient availability.
_Azolla_ species are distributed globally, predominantly found in tropical, subtropical, and warm temperate regions.
They are especially prevalent in Asia, Africa, and the Americas, where they are used in traditional agriculture [@Madeira2016a; @Lydia2023; @Watanabe1981].
The fern forms dense mats on the water surface, which helps it outcompete other aquatic plants and algae.
These floating mats are crucial for stabilizing the ecosystem by reducing water evaporation and providing a habitat for various microorganisms and small aquatic animals. [@Wagner1997b]

Ecologists associate _Azolla_ often with unhealthy ecosystems, terming it invasive and dangerous.
I argue that _Azolla_ is not a dangerous plant, nor invasive.
Harmful levels of _Azolla_ growth are, in my opinion, a symptom of eutrophic ecosystems.
Specifically phosphorus is linked to _Azolla_ growth, as the fern grows independent of nitrogen [@Temmink2018].
Eutrophication will lead to unhealthy ecological dynamics in aquatic systems in one way or another [@VanderLee2018].
Some fast grower will take advantage of this situation.
Whether this is an alga, _Lemna__ (duckweed) or _Azolla_ is irrelevant.  [@Sabetraftar2013]

_Azolla_ is a fast grower, and can further damage eutrophic ecosystems by darkening the water column.
It does, however, also have natural enemies.
For _Azolla_ agriculture, these would be considered pests.
For conservation ecologists, these are considered pest control [@Madeira2016a].
Specifically, the water fern weevil _Stenopelmus rufinasus_ can significantly impact _Azolla_ populations by feeding on the fronds [@Hill1998].
A _S. rufinasus_ swarm can decimate an _Azolla_ mat in days and even completely eradicate it.
We have unwillingly empirically tested this theory several times.

When an _Azolla_ population has covered a water surface, the plants' growth is directed upwards.
An _Azolla_ mat is formed between a few millimetres and 20 to 30 centimetres thick in extreme scenarios.
The bottom of the mat is dark and may be submerged by the weight of plants laying on top.
Inside the _Azolla_ mat, the light quality changes.
Specifically the red vs far-red light ratio.
The plants perceive this light change and adapt their growth as shown in chapter \ref{it_takes_two} \nameref{it_takes_two} or @Dijkhuizen2021.
The internode distance (distance on the stem between leaves) increases, giving the plant an elongated appearance.
This is a common response in plants to being overshadowed by other plants; they stretch out towards the light [@Possart2013].

## Life cycle

_Azolla_ is a fern genus, it makes no flowers but spores for reproductive purposes.
Sporulation is triggered by a high far-red over red light ratio, and density of the plants in a mat (Chapter \ref{it_takes_two}).
_Azolla_ makes two types of spores: Big megaspores, made in megasporocarps, and small microspores made in microsporocarps [@Schaffner1905].
The cone-shaped megasporocarps can just be observed by the naked eye.
They contain one megaspore as well as a resting colony of the symbiotic bacterium _T. azollae_.
This colony was acquired from the starting colony at the SAM at the very beginning of spore develoment.
The microsporocarps are bigger, and contain many small massulae housed in microsporangia.
Massulae are presumably non-living structures containing the microscopic microspore.
_Azolla_ massulae are recognisable by their glochidia.
Glochidia are arrow-like hair structures on the massulae surface that serve to hook onto the megaspore. [@Campbell1893]
When attached to the megaspore, the microspore presumably swims to the megaspore, fertilises it and a plant grows out of it.

<!-- pictures! -->

## Agricultural history
The application of _Azolla__ in agriculture does not require high-tech genomics solutions.
_Azolla_ has been used historically as a bio-fertiliser in rice paddies for several millennia [@Watanabe1981; @bocchi2010; @bujak2022].
Rice paddies are often flooded to prevent weeds from growing there, but this provides an opportunity for toxic cyanobacterial blooms, poisoning the rice.
As a countermeasure, a rapidly growing _Azolla_ mat can shield the water from light, preventing algal blooms.
The nitrogen fixed can be incorporated into the soil after rice harvest; fertilising the soil.
Any surplus of the fern can be used as animal feed.
Additionally, it is thought that an Azolla mat prevents mosquitoes from accessing the water to lay their eggs.

## Agricultural opportunities

_Azolla_'s properties give it substantial agricultural potential [@Lumpkin1980a; @Brouwer2014].
These are properties like rapid growth, nitrogen fertiliser independence, and high protein content [@Brouwer2014].
Firstly, as in rice paddies, _Azolla_ can be used as a bio-fertiliser, enhancing soil fertility by providing a natural source of nitrogen [@Watanabe1981].
This reduces the need for synthetic fertiliser; promoting sustainable farming practices and reducing environmental impact.
Studies have shown that incorporating _Azolla_ in rice cultivation can increase crop yields and improve soil health [@Watanabe1981;@bocchi2010].
Especially when arable land is limited but fresh water is not, _Azolla_ may prove useful to farmers [@Lumpkin1980a].
There are caveats naturally.
_Azolla_ growth requires a big amount of fresh water, and the incorporation of _Azolla__ as bio-fertiliser will underperform compared to synthetic fertiliser use.
This practice is only feasible in areas where fresh water is plentiful and the use of cheap but environmentally damaging synthetic fertiliser is discouraged.

Beyond its use as a bio-fertiliser, _Azolla_ is also explored as an alternative feed for livestock [@Brouwer2018].
Its high protein content and rich amino-acid profile make it an excellent supplement for animal diets [@becerra1990;@Bujak2022;@Brouwer2014].
The current major protein crop is soy.
It is massively imported for feed purposes.
Currently, the Netherlands imports more soy than we could grow soy plants in the total area of the country [@BrouwerThesis].
_Azolla_ could be an alternative plant that grows well in the Dutch temperate climate.
This application may also contribute to the recycling of nutrients within agricultural systems.
Again, there are challenges for including _Azolla_ in feed diets.
A relatively high content of tannins and other polyphenols may inhibit _Azolla_'s digestibility.

_Azolla_ is also thought capable of cleaning up contaminated or eutrophic water bodies through phytoremediation [@Sood2012].
This process involves using plants to remove, degrade, or stabilize environmental contaminants.
It could be leveraged to retrieve phosphorus and iron that are locked and unavailable in agricultural soils under aerobic conditions [@Scharer2009; @Temmink2018].
When a meadow is flooded and covered with _Azolla_ ferns, the anoxic conditions may release Iron and Phosphorus from the soil [@Scharer2009].

_Azolla_ is shown to absorb heavy metals such as lead, cadmium, and arsenic from polluted waters [@Sood2012].
The plants may not be suitable for consumption or use as feed or fertiliser, but the contaminated ecosystem may be cleaner after the process.
Some studies suggest incorporating _Azolla_ in water management strategies.
They argue it may help restoring ecological balance to eutrophic and contaminated water bodies [@Akhtar2016].
Given Azolla’s rapid and invasive growth tendencies, I argue to practice extreme caution before implementing such measures.

Given all these special properties and agricultural opportunities, one may wonder why _Azolla_ is not used all around.
There are naturally several caveats to using _Azolla_ in practice.
Fresh water usage and environmental risks of growing _Azolla_ are among those.
Besides, _Azolla_ populations can collapse once _S. rufinasus_ populations settle on the plants.
Pest control in an aquatic system is more complex than on land.
Besides, since I'm advocating _Azolla_ as a sustainable alternative, chemical pest control is not desirable although perhaps not avoidable.
Finally, when using _Azolla_ as feed for animals, the fern's high phenolic content can inhibit digestion of the protein content [@Brouwer2018].
<!-- This transition could be better. -->

## Azolla domestication
Both historic and recent agricultural _Azolla_ applications used local native strains.
No _Azolla_ cultivars exist, or has there ever been any _Azolla_ breeding to my knowledge.
The caveats of _Azolla_ usage, like digestion inhibition, could be tackled with modern breeding tools.
With genomic insights and gene editing techniques, wild crops can be domesticated with incredible efficiency [@Li2018b; @Lemmon2018a].
However, domestication of the _Azolla_ symbiosis has only yet begun [@Schluepmann2022].
Collecting biodiversity is one of the first steps in domestication.
The International Rice Research Institute (IRRI) did collect a notable amount of _Azolla_ strains [@Watanabe1992].
Unfortunately, a decent portion of the _Azolla_ germplasm at IRRI was lost.
Additionally, control of the sexual reproduction of the fern is essential, as detailed in \ref{it_takes_two}.
Storage and dissemination of those spores was demonstrated in @Brouwer2014.
Modern breeding however, requires genomic information to be established as well.
Establishing the first _Azolla_ genome in @Li2018 was an essential step in the domestication process.
Stable transformation or gene-editing of the symbiosis partners has yet to be unlocked and is the next major step in unlocking _Azolla_'s potential.

# Methodology

Several _Azolla_ properties make it an interesting plant for 21st century specific challenges like the demand for plant based protein and agriculture on non-arable land.
To further realise that potential, we can make use of modern breeding tools and a system biology perspective on the functioning of the symbiosis.
These modern breeding tools require a fundament of genomic knowledge and know-how.
One most know the genes of a symbiosis before one knows what gene to edit.
That genomic understanding of the _Azolla_ symbiosis, is what I work on here.
The first part of this thesis focuses on the metagenomics of the _Azolla_ symbiosis.
With metagenomics, I study the collective genomes of microbes associated to _Azolla_, mapping out their (near) complete metabolic potential.
In the last two chapters, my colleagues and I discuss the reproductive cycle of the _Azolla_ symbiosis.
Control of the reproductive cycle is essential for domesticating the symbiosis after all.
We try to explore the molecular underpinning of this cycle.
To this end, we reconstruct the evolution of proteins essential to this process.
The resulting phylogenetic trees allow us to relate knowledge from other plants to _Azolla_ and ferns in general.

## Bioinformatics

This thesis employs ample bioinformatics techniques.
Notably, the term has not been used once before this section of the introduction.
Firstly, because I chose to focus on the plant and symbiosis biology first.
While my work my at times be heavy on the methods section, I try to put the biology first.
And secondly because the definition of bioinformatics deserves a paragraph by itself before we dive in deeper.
The typical image of bioinformatics revolves around computer science and application of tools, more than biology.
Too often, bioinformaticians are seen as "number crunching by nerds who look at black terminal screens all day."
Now there is truth in that definition, ask any of my old colleagues about how they picture me.
But it doesn't quite do justice to the field as a whole.
One could similarly claim that ecologists only spend time in the field determining plant species, or that molecular biologist train all day to move miniature amounts of water around.
These statements are perhaps ironic, and they have a bit of truth in them.
But they are not very helpful for understanding the bigger picture behind these stereotypical acts.
The same goes for bioinformatics.

The original definition of bioinformatics is much more interesting and helpful to understand bioinformatic works.
**Bioinformatics is the study of information processes in biological systems** [@Hesper1970; @Hogeweg2011]**.** 
A bioinformatician may read that information from DNA with genomics or meta-genomics.
We study how that information is transmitted within cells via RNA perhaps with RNAseq, and across millions of years of evolution with phylogenetics.
We study how information is used to make proteins with proteomics and structural bioinformatics.
We study how information is used to make decisions in a cell, and how this all fits together in a biological system.

In this work, we use bioinformatics to inquire the information storage or processing of _Azolla_ and associated microbes.
This does come down to a lot of computer work and number crunching, counting of molecules and comparing their sequences to each other.
But the tedious counting of molecules is a means to an end: understanding the system as a whole.
In our case that means inquiring and getting to understand the identity and metabolic potential of all _Azolla_ associated microbes.
Or alternatively to find out how reproduction cycle genes in _Azolla_ compare to homologous genes in seed plants.

I do not claim to address all listed bioinformatics questions for the _Azolla_ symbiosis, and certainly not that I understand the system as a whole.
Instead, I mean to set the context in which I am working.
The _Azolla_ genome was the first genome to be ever published.
With fern genomics we are just starting to delve into bioinformatics.
It is a long-term goal that my research helps to move towards better genomic understanding of _Azolla_ and symbioses in general." -->
Genomic knowledge and know-how of the system, is merely a step towards that end-goal of system understanding.

## Genomics for breeding novel crops

**The practical use of bioinformatics in breeding needs little defense.**
<!-- This opening statement sets the stage effectively, but it could be improved by briefly mentioning specific advances or successes in bioinformatics-driven breeding, which would naturally lead into the subsequent discussion. -->
**Traditionally, plant breeding relied on phenotypic selection over multiple generations.**
<!-- This sentence introduces the historical context well. However, it could benefit from immediately connecting this to the challenges of this approach, such as time consumption and variability in outcomes, which you then discuss in the following sentence. -->
**This process can take decades or lifetimes depending on how fast a plant can produce offspring.**
<!-- This is a strong continuation, highlighting the limitations of traditional breeding. It might be useful to mention here how such long timelines can hinder the rapid development of crops in response to new agricultural challenges. -->
**However, with the advent of genomics and bioinformatics, this timeline can be drastically sped-up.**
<!-- This sentence transitions well to modern methods. You might consider briefly noting how specific bioinformatics tools or techniques, like CRISPR or next-generation sequencing, have contributed to this acceleration, which will set up the discussion of these tools later. -->
**Massive genome sequencing projects have enabled precision trait selection via techniques such as GWAS.**
<!-- This sentence introduces an important technique. However, since GWAS may not be familiar to all readers, a brief explanation here or in a parenthetical could help maintain the flow while ensuring clarity. -->
**Sequencing a cross' offspring enables accelerating breeding cycles.**
<!-- This follows logically from the previous sentence, but it could be enhanced by explaining how sequencing informs decisions on which traits to select, which would tie into the broader theme of precision in modern breeding. -->
**Finally, genomics has enabled molecular biologists to begin to unravel the regulatory networks that govern a crop's growth.**
<!-- This is a critical point, but it would be more impactful if followed by an example of a specific regulatory network or pathway that has been elucidated, thus illustrating the practical applications of these genomic insights. -->
**Despite this acceleration, breeding via crossing offspring is still slow and even detrimental to a crop's gene pool.**
<!-- This sentence introduces a key challenge in breeding. It would be beneficial to expand slightly on why reduced genetic diversity is problematic, setting up the need for newer methods that maintain or even enhance genetic variability. -->
**Repeated selection of certain traits has diluted out genetic variation in crops.**
<!-- This is a crucial observation that connects directly to the previous sentence. A brief example of a crop that has suffered from reduced genetic diversity would reinforce this point and smoothly transition to discussing solutions. -->
**The reduced gene pool has led to tastier crops and bigger yields, but also made crops vulnerable to biotic and abiotic stresses.**
<!-- This sentence effectively presents the trade-offs in traditional breeding. To deepen the impact, consider mentioning specific types of stresses (e.g., disease, drought) and how these vulnerabilities have manifested in real-world scenarios. -->
**Reintroducing these traits of wild, non-domesticated strains via traditional crossing is challenging and slow.**
<!-- This sentence connects well to the problem of reduced genetic diversity. To strengthen the argument, it might be useful to briefly touch on why traditional crossing is slow and how modern techniques could address this, leading into the next point. -->
**However, with bioinformatic insights and modern molecular breeding, a solution is at hand.**
<!-- This is a strong transition. To maintain the momentum, consider specifying what these "bioinformatic insights" might include, such as genome-wide association studies or marker-assisted selection, which would tie back to earlier mentions of GWAS. -->
**As a response to the genetic variation problem, researchers identified several key genes that needed disabling for the domestication of tomato.**
<!-- This example is well-placed and effectively illustrates the application of genomics in breeding. It would be even more impactful if followed by a brief explanation of how these genes were identified, perhaps linking back to bioinformatic methods discussed earlier. -->
**They took a wild tomato variety and disabled these genes with gene-editing techniques [@Li2018b].**
<!-- This sentence is clear, but the impact could be enhanced by briefly mentioning the specific gene-editing technique used, such as CRISPR, which would also serve to educate readers less familiar with these technologies. -->
**The result was an edible tomato, not quite up to commercial standards, but edible non-the-less.**
<!-- This is an interesting outcome that highlights both the successes and limitations of early efforts. It might be useful to briefly discuss what specific improvements are needed to meet commercial standards, setting up the broader discussion of crop domestication. -->
**Millennia of selection and crossing were reproduced in the lab in a matter of months.**
<!-- This is a powerful statement that underscores the potential of modern techniques. To build on this, consider adding a sentence that speculates on how such rapid progress could revolutionize breeding practices across different crops, including _Azolla_. -->
**Additionally, this allows for keeping more genetic variability in the novel tomato variety's gene pool.**
<!-- This is a key advantage that addresses earlier concerns about genetic diversity. To reinforce the point, you could briefly mention how maintaining genetic variability contributes to resilience against environmental changes and diseases. -->
**When researching novel crops, we should be inspired by this story.**
<!-- This motivational statement works well, but it could be made more specific by linking it directly to your research on _Azolla_, suggesting that similar methods could be applied to enhance its domestication. -->
**A process similar to that of tomato was achieved in an orphan crop, ground cherry; a species relatively close to tomato [@Lemmon2018a].**
<!-- This is a good additional example that reinforces your argument. However, it might be helpful to define what an "orphan crop" is for readers who might not be familiar with the term, thus making the example more accessible. -->
**With knowledge of domestication gene targets in tomato, the orphaned crop's undesirable characteristics were gene-edited.**
<!-- This sentence continues the narrative effectively. It might be strengthened by specifying what the "undesirable characteristics" were, which would provide a clearer picture of the improvements achieved. -->
**The process resulted in a higher-yielding crop, without loss of the genetic diversity and stress resilience of the wild crop.**
<!-- This is an important outcome that ties back to earlier concerns about genetic diversity. It could be enhanced by briefly discussing the broader implications of maintaining stress resilience in the context of climate change or other environmental pressures. -->
**It must be noted that _Azolla_ researchers lack a genome assembly and genomic understanding of the quality of tomato.**
<!-- This is a critical caveat that appropriately tempers expectations. To make it more impactful, consider elaborating on how this gap in knowledge limits current breeding efforts for _Azolla_ and what steps could be taken to address it. -->
**More importantly, we lack gene editing tools that are essential in the tomato example.**
<!-- This sentence further highlights the challenges. It could be improved by briefly discussing which specific tools are missing and how developing these tools could unlock new possibilities for _Azolla_ research. -->
**But these examples demonstrate that with the right genomic insight, and a robust gene-editing protocol, domestication of novel crops is around the corner.**
<!-- This is a strong and optimistic conclusion to this section. You might strengthen it by directly linking it to your own research, suggesting how your work contributes to laying the groundwork for such advances in _Azolla_. -->
**Future researchers might be able to work on _Azolla_'s lesser-than-optimal traits with gene editing backed by genomics [@Schluepmann2022].**
<!-- This is a forward-looking statement that naturally follows the previous discussion. To enhance its impact, consider specifying which "lesser-than-optimal traits" are most pressing and how addressing them could make _Azolla_ a more viable crop. -->
**They could try to increase its palatability, reduce its invasiveness, and increase its pest resistance, for example.**
<!-- This sentence provides concrete examples of potential improvements. To deepen the discussion, you could briefly touch on the challenges associated with each of these goals and how genomics might help overcome them. -->
**Control of the reproductive cycle of a plant is essential for its domestication (See chapter \ref{it_takes_two}).**
<!-- This sentence introduces an important aspect of breeding. To strengthen the connection to the rest of the discussion, you might explain why controlling the reproductive cycle is particularly challenging for _Azolla_ and how genomic insights could help. -->
**With genomic knowledge, the pathways involved in reproduction may be better understood and possibly manipulated.**
<!-- This is a logical continuation. To make it more concrete, consider providing a specific example of a reproductive pathway that could be targeted, which would tie into the broader theme of using genomics for crop improvement. -->
**Before any reader is disappointed, this thesis is not describing editing of either the fern or the symbionts.**
<!-- This sentence sets clear expectations for the reader. It might be more effective if rephrased to maintain a formal tone, such as "It is important to clarify that this thesis does not focus on genetic editing of either the fern or its symbionts." -->
**My colleagues have tried, and made small steps forward, but did not achieve robust genetic editing.**
<!-- This is an honest and realistic statement. To add value, you could briefly discuss the nature of these small steps and what challenges still need to be overcome, providing a clear picture of the current state of research. -->
**These advanced techniques need a genomic basis to be achieved.**
<!-- This is a critical point that reinforces the importance of foundational research. You might enhance it by specifying what kind of genomic data is needed, such as high-quality genome assemblies or functional annotations, and how these would directly support the development of gene-editing protocols. -->
**That basis, the genomics of the _Azolla_ symbiosis, is what I work on in this thesis.**
<!-- This sentence effectively ties your research to the broader goals discussed. To make it more impactful, you could briefly mention how the genomic insights you are generating will contribute to overcoming the challenges mentioned earlier. -->
**When I joined the _Azolla_ lab in my Masters, I extracted and transported the DNA that would later be sequenced and assembled into the first _Azolla filiculoides_ genome by [@Li2017].**
<!-- This personal anecdote adds a human element to the narrative, which is engaging. However, to maintain a clear focus, it might be helpful to briefly explain how this experience influenced your research trajectory and what specific role you played in the genome assembly process. -->
**The _Azolla filiculoides_ genome was the first fern ever to have its genome sequenced.**
<!-- This is a significant milestone. To underscore its importance, consider mentioning the broader implications of having this genome available for fern research and how it opens up new possibilities for studying _Azolla_ and related species. -->
**In this thesis, we use that genome for gaining insight in the workings of _Azolla_.**
<!-- This is a clear statement of purpose. It would be beneficial to elaborate slightly on what specific aspects of _Azolla_'s biology you are investigating using the genome, linking it back to the broader goals of your research. -->
**We relate it to existing knowledge of other crops, and speculate how we may use it in the future to manipulate the symbiosis.**
<!-- This sentence effectively transitions to future applications. To make the connection stronger, consider providing a specific example of how insights from other crops have informed your understanding of _Azolla_ and what specific manipulations might be possible as a result. -->
**Studying fern genomics is a special challenge, for we have no other ferns' genome to compare with.**
<!-- This sentence introduces an important challenge. It could be improved by briefly discussing the implications of this lack of comparative data, such as difficulties in identifying gene functions or evolutionary relationships, and how you plan to address this challenge in your research. -->
**To uncover the function of any gene, we employ phylogenetics.**
<!-- This is a good introduction to your methodological approach. You might enhance it by briefly explaining why phylogenetics is particularly useful in this context, especially given the challenges mentioned in the previous sentence. -->
**By comparing DNA sequences of many versions of the same gene, we can calculate the probable evolutionary history of those sequences.**
<!-- This sentence clearly explains the method. To strengthen the connection to your broader research, consider adding a sentence that discusses how understanding the evolutionary history of genes can inform their functional annotation and relevance to the _Azolla_ symbiosis. -->
**This allows us to infer the function of a protein-coding sequence in the context of others.**
<!-- This is a logical continuation. To deepen the reader's understanding, you could briefly mention how these functional inferences are validated or what additional steps might be needed to confirm the predicted functions. -->
**In chapter \ref{one_two_tree} I describe this method in more detail.**
<!-- This sentence directs the reader to further details, which is useful. To maintain the narrative flow, you might want to briefly preview what readers can expect to learn from that chapter, such as specific examples of genes whose functions were inferred using phylogenetics. -->
**Breeding targets can be selected once the probable function of several _Azolla_ genes is established, and a gene editing protocol is in working order.**
<!-- This sentence effectively ties the discussion of gene function to practical outcomes. To make it more concrete, consider mentioning what specific traits or pathways might be targeted for improvement once these functions are established. -->
**Possible targets may include genes for yield stability and pest resistance.**
<!-- This is a good start to specifying potential targets. It might be even stronger if you briefly discuss why these particular traits are important for _Azolla_ and how improving them could enhance its viability as a crop. -->
**Alternatively, undesirable compounds may be removed, and desirable ones may be made more abundant.**
<!-- This sentence adds further potential applications. To deepen the discussion, consider providing examples of specific undesirable compounds in _Azolla_ that might be removed, and what desirable traits could be enhanced, tying this back to the goals of crop domestication. -->
**Nutrient acquisition and accumulation of, for example, phosphorus may be enhanced.**
<!-- This is a specific example that helps ground the discussion. To build on this, you could briefly explain why enhancing phosphorus accumulation is particularly beneficial and how it ties into broader agricultural or environmental goals. -->
**Since growing gene-edited crops remains controversial, it remains a research tool for now.**
<!-- This is an important point to acknowledge. To enrich the discussion, consider briefly mentioning the nature of the controversies surrounding gene-edited crops, such as regulatory, ethical, or public perception issues, and how these might impact the application of your research. -->
**Removing a gene, or making it overactive remains the standard way to prove the function of any one gene.**
<!-- This sentence explains a key aspect of gene function validation. To strengthen the narrative, you might briefly mention how this approach fits into the broader research process, such as by leading to potential applications or further experimentation. -->
**Establishing a gene editing protocol in _Azolla_ will provide the research community with a tool to do functional genomics in ferns backed by the context of the _Azolla_ genome.**
<!-- This is a strong statement of the potential impact of your work. To add depth, consider discussing how such a protocol could open up new research avenues not just for _Azolla_, but for other ferns or related plants as well. -->
**The only fern in which any kind of DNA modification has been established, does not have a genome sequence available.**
<!-- This is a critical point that underscores the novelty and importance of your work. To tie it back to the broader discussion, you could briefly mention how having a genome sequence available for _Azolla_ not only aids in functional genomics but also positions _Azolla_ as a model system for fern research. -->

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

## Genomics for breeding a symbiosis

Molecular breeding began with the study of DNA; a field that was later called genomics.
<!-- This opening sentence effectively sets the historical context for the discussion. To make the transition smoother, you could briefly mention how genomics laid the foundation for more advanced techniques like metagenomics, which are central to this section. -->
It is then only logical to begin symbiosis breeding with meta-genomics.
<!-- This sentence follows logically from the previous one, but to strengthen the connection, consider explaining why metagenomics is particularly well-suited for studying symbiosis, perhaps by mentioning its ability to analyze complex microbial communities. -->
Metagenomics is the study of all DNA associated with any organ or organism.
<!-- This is a clear definition. However, to enhance the reader's understanding, it might be helpful to briefly contrast metagenomics with other genomic techniques, such as single-organism genomics, to highlight what makes metagenomics unique. -->
It differs from microbiome profiling.
<!-- This is an important distinction. To clarify the difference further, consider briefly describing what microbiome profiling entails (e.g., 16S rRNA gene sequencing) and why metagenomics offers a more comprehensive view. -->
The latter are most often 16S marker gene studies.
<!-- This sentence correctly identifies a common method used in microbiome profiling. It could be more impactful if you explain that 16S studies typically provide only taxonomic information, whereas metagenomics reveals functional potential by analyzing the entire genome. -->
These only provide insight into what organisms are associated with a certain organ or organism.
<!-- This sentence succinctly explains the limitation of 16S studies. To enhance the comparison, you might add that metagenomics allows for the reconstruction of microbial genomes, offering insights into metabolic pathways and interactions within the symbiosis. -->
Metagenomics aims to reconstruct the full genomes of all those organisms, revealing their full metabolic potential.
<!-- This is a strong statement that highlights the advantages of metagenomics. To deepen the discussion, you could mention that this approach not only identifies "who is there" but also "what they are capable of doing," which is crucial for understanding symbiosis. -->
With metagenomics, we can investigate the toolkit of all symbionts associated with a certain host, and better understand their function.
<!-- This sentence ties the methodology to the broader research goals effectively. To reinforce this, you could provide a brief example of how understanding the metabolic toolkit of symbionts could inform breeding strategies for improving symbiotic efficiency or resilience. -->
By sequencing the genomes of both the host and the symbiont, researchers can identify genes involved in key symbiotic functions.
<!-- This sentence is clear and informative. To strengthen the narrative, consider specifying what key symbiotic functions you are particularly interested in, such as nutrient exchange or stress tolerance, and how identifying these genes could directly impact breeding efforts. -->
These can include nutrient exchange, stress tolerance, and pathogen resistance.
<!-- This is a good list of functions. To add depth, you could briefly explain why these particular functions are important for the success of a symbiosis and how improving them could benefit the host plant. -->
The genes and pathways that are present or absent allow for directed hypothesis generation.
<!-- This is a strong statement that connects genomic data to the research process. To enhance the impact, consider providing an example of a specific hypothesis that could be generated from metagenomic data in the context of symbiosis breeding. -->
For example, it allows us to investigate any microbe's metabolic potential and relate this to that of other microbes' or to the host's metabolism.
<!-- This sentence provides a concrete example of how metagenomic data can be used. To deepen the discussion, you could briefly mention how this information could be used to select or engineer symbionts that complement the host's metabolic needs, thereby enhancing the symbiosis. -->
In the _Azolla_ symbiosis specifically, we hypothesize that symbiosis partners may actually leach off nitrogen fixed by _T. azollae_ in chapter \ref{foul_play}.
<!-- This sentence ties your research directly to the thesis, which is effective. To make the hypothesis clearer, you might briefly explain the potential significance of nitrogen leaching in the symbiosis and how this could influence breeding strategies. -->
In the future, metagenomic insights may allow for the targeted manipulation of genes in symbionts to enhance some performance or plant productivity.
<!-- This is a forward-looking statement that effectively connects metagenomics to practical applications. To strengthen this point, you could mention specific traits or functions that could be targeted for enhancement, such as improving nitrogen fixation or increasing stress tolerance. -->
Alternatively, understanding the niche of any microbe in a consortium, one might be able to swap out one microbe for another to add or remove metabolic potential.
<!-- This is an intriguing idea that adds a layer of complexity to the discussion. To clarify, consider briefly discussing the challenges associated with swapping microbes, such as ensuring the stability of the microbial community or the compatibility of the new microbe with the host. -->
Microbiome editing is a field much younger than editing single organisms.
<!-- This sentence introduces the concept of microbiome editing well. To enhance the discussion, you could briefly explain what makes microbiome editing more challenging compared to editing single organisms, such as the complexity of interactions within the microbial community. -->
Even when working with a single strain of a single organism, successful editing is rare.
<!-- This statement emphasizes the difficulty of genetic editing. To build on this, you might mention specific factors that contribute to the rarity of successful editing, such as off-target effects or difficulties in delivering editing tools to the target cells. -->
A protocol to do so often includes steps to kill or remove cells that were not edited.
<!-- This is a good explanation of a key challenge in genetic editing. To deepen the discussion, consider mentioning the implications of this need for selective pressure, such as potential impacts on the viability or functionality of the edited organism. -->
When editing a microbiome, or genes of a microbiome member, we must first assume we can grow this microbe in isolation.
<!-- This sentence introduces a critical assumption in microbiome editing. To strengthen the point, you might briefly discuss why isolating and culturing symbiotic microbes can be particularly challenging and how this impacts the feasibility of microbiome editing. -->
Then assume that a transformation or editing protocol is available.
<!-- This is a logical next step in the process. To add depth, consider explaining the challenges of developing such protocols, particularly for non-model organisms or microbes that are difficult to culture. -->
And finally assume that the newly transformed strain can replace the original and retake the niche of its wild type predecessor.
<!-- This is an important consideration. To enhance the discussion, you could mention the factors that influence whether a transformed strain can successfully establish itself within an existing microbial community, such as competition with other microbes or compatibility with the host environment. -->
An alternate approach is taking a similar strain or species with desired traits, and introducing it into an existing consortium.
<!-- This alternative approach is well-explained. To enrich the narrative, you might discuss the potential advantages and disadvantages of this approach compared to directly editing existing community members, such as ease of implementation versus potential ecological impacts. -->
This is a challenging process and requires insights into the consortium's ecology to succeed [@Albright2022; @Bai2023].
<!-- This sentence effectively emphasizes the complexity of microbiome editing. To build on this, you could briefly mention what specific ecological insights are necessary, such as understanding the interactions between microbes or the role of environmental factors in shaping the community. -->
For _Azolla_ specifically, we have managed to grow several strains of bacteria in isolation (unpublished results).
<!-- This is a significant achievement that contributes directly to the feasibility of microbiome editing in _Azolla_. To strengthen the point, consider briefly discussing what insights or advantages were gained from being able to culture these bacteria, and how this will inform future research efforts. -->
We have not yet managed to re-introduce microbes to the _Azolla_ leaf pockets.
<!-- This sentence honestly acknowledges a current limitation. To enhance the narrative, you could discuss the challenges encountered in attempting to re-introduce microbes and what steps you plan to take to overcome these hurdles. -->
This is an essential step to stably modify the _Azolla_ microbial community.
<!-- This sentence highlights the importance of re-introducing microbes. To deepen the discussion, you might explain why stable modification of the microbial community is critical for achieving the goals of symbiosis breeding, such as enhancing specific symbiotic functions. -->
While _Azolla_ microbiome editing is a spectacular perspective of what might be possible in the future, we are not there yet.
<!-- This sentence sets realistic expectations. To maintain momentum, you could follow up with a brief discussion of the next steps or research goals that need to be achieved to move closer to this future possibility. -->
Instead, I focus here on identifying and describing the symbiosis partners.
<!-- This is a clear statement of your current research focus. To tie it back to the broader discussion, you might explain how identifying and characterizing these partners lays the groundwork for future manipulation or enhancement of the symbiosis. -->
Specifically in chapter \ref{forever_together}, I use sequencing data of several _Azolla_ species to retrieve microbial genomes associated with _Azolla_ as a whole genus.
<!-- This sentence effectively directs the reader to a specific chapter for more detailed information. To strengthen the narrative, consider briefly summarizing the key findings or insights from this work and how they contribute to the overall goals of your research. -->
We later venture into meta-transcriptomics to inquiry what the active processes are in these microbes, but gain little signal to what genes are active in these microbes (Chapter \ref{it_takes_two}).

<!-- Match generalness and Azolla-specificness of the last two sections to each other. I guess that's not the case now. -->

<!-- move shorter gene ethics section here? -->

## Introducing bioinformatics to a lab

The _Azolla_ lab was housed in the molecular plant physiology group at Utrecht University before the former two were dissolved.
<!-- This opening sentence provides necessary context about the lab's history. To make it more relevant to the methodology, consider briefly mentioning the lab's initial focus and how the transition to incorporating bioinformatics began. -->
It was quite a challenge to introduce bioinformatics techniques to a small lab of at most three employees with no bioinformatics history.
<!-- This sentence effectively introduces the challenges faced. To enhance the narrative, you could briefly describe the specific obstacles, such as the lack of computational resources or expertise, which would set up the discussion of how these were overcome. -->
This process started already during my Masters, when I started working on _Azolla_.
<!-- This personal connection adds depth to the narrative. To strengthen the point, consider elaborating on how your involvement during your Master’s degree influenced the lab's decision to incorporate bioinformatics, perhaps by highlighting a specific project or outcome. -->
It was a challenge in means of infrastructure, like storage and computing power.
<!-- This sentence identifies key logistical challenges. To enrich the discussion, you could mention how these challenges were addressed, such as through securing funding, collaborating with other groups, or acquiring new equipment. -->
But this was quickly solved with some money from the group to build a computer and with hospitality of the local theoretical biology and bioinformatics group.
<!-- This sentence effectively explains how the challenges were addressed. To add more detail, you could briefly describe the role of the theoretical biology and bioinformatics group in supporting this transition, whether through shared resources, expertise, or collaborative projects. -->
The main challenge was building the know-how.
<!-- This is a critical point. To provide a more comprehensive view, consider discussing the specific types of bioinformatics expertise that were needed, such as programming skills, data analysis techniques, or specific software knowledge, and how these were developed. -->
As a computer savvy student at the time, with no bioinformatics training whatsoever, I was lucky to attend some PhD courses on bioinformatics techniques.
<!-- This personal experience adds a relatable element to the narrative. To enhance the impact, you might briefly mention how these courses influenced your approach to bioinformatics in your research and what specific skills or techniques you gained. -->
Additionally, I was lucky to get advice from collaborators, specifically those in chapter \ref{foul_play}, and from bioinformaticians and system administrators in the department.
<!-- This sentence emphasizes the importance of collaboration. To build on this, you could discuss how these collaborations shaped the development of bioinformatics capabilities in the lab, perhaps by providing specific examples of advice or techniques that were particularly valuable. -->
With some support and enthusiasm, together we managed to publish a first bioinformatics-centered paper within two years after the project started.
<!-- This is a significant achievement that highlights the rapid progress made. To provide more context, you could briefly summarize the key findings or contributions of this paper, and how it demonstrated the value of integrating bioinformatics into the lab's research. -->
Later, during my PhD, we diverged the bioinformatics toolkit of the lab quite a bit.
<!-- This sentence indicates further development of the lab's capabilities. To deepen the discussion, consider providing examples of specific tools or techniques that were added to the lab's repertoire, and how these expanded the scope of the research that could be conducted. -->
Despite the quick introduction of bioinformatics in the _Azolla_ lab, there was so much work to be done.
<!-- This sentence acknowledges the ongoing challenges. To maintain the momentum, you could briefly outline the key areas where further development was needed, such as data management, analysis pipelines, or integrating bioinformatics with wet lab work. -->
As a lab, we wanted to improve upon the annotation of the existing _A. filiculoides_ genome assembly, sequence metagenomes and metatranscriptomes of small experimental _Azolla_ ecosystems (mesocosms), develop meta-transcriptomics or dual-transcriptomics protocols, and many more plans.
<!-- This sentence provides a comprehensive overview of the lab's goals. To make it more impactful, consider elaborating on why these specific areas were prioritized, how they align with the lab's broader research objectives, and what challenges were anticipated in achieving them. -->
These bioinformatics techniques would help us answer questions relevant for _Azolla_ domestication and general understanding of the symbiosis.
<!-- This is a clear statement of purpose. To tie it more closely to the methodology, you could mention how these techniques specifically contribute to addressing the research questions posed in earlier sections, and what outcomes you expect from their application. -->
But we struggled with the broadness of all these questions.
<!-- This sentence introduces a key challenge. To provide more insight, consider discussing why the broadness of the questions posed difficulties, such as by requiring diverse expertise, complex data integration, or interdisciplinary approaches, and how you attempted to manage this complexity. -->
Each technique often requires a different specialized protocol to prepare the experimental material in a proper way.
<!-- This is an important point that highlights the complexity of the work. To deepen the discussion, you could provide an example of a specific technique and the challenges associated with preparing the material for it, which would illustrate the need for careful planning and coordination. -->
Preparations of sequencing libraries are costly, as is sequencing itself.
<!-- This sentence highlights a practical challenge. To enhance the narrative, you could briefly discuss how these costs impacted the lab's research planning or prioritization, and whether any strategies were employed to mitigate these costs, such as through collaborations or funding applications. -->
Then each technique requires special bioinformatic tools, each with their own manual and intricacies.
<!-- This sentence emphasizes the technical challenges. To provide more context, consider mentioning how you and your colleagues approached learning and implementing these tools, perhaps by developing standard operating procedures, collaborating with experts, or attending specialized training. -->
In the end, we did manage as a team to do metagenomics, transcriptomics, small RNA sequencing, and metatranscriptomics.
<!-- This sentence highlights the success achieved despite the challenges. To deepen the impact, you might briefly summarize the key findings or insights gained from these techniques, and how they contributed to the lab's research goals. -->
We contributed to a new genome annotation, started to sequence with a nanopore device, and delved into phylogeny.
<!-- This sentence effectively lists the accomplishments. To enhance the narrative, consider explaining the significance of each achievement, such as how the new genome annotation improved the understanding of _Azolla_, or how nanopore sequencing and phylogenetics added new dimensions to the research. -->
Even with a small team, and limited experience, a lot is possible.
<!-- This sentence is an encouraging reflection on the team's achievements. To make it more actionable, you could discuss specific strategies or practices that helped the team succeed, such as fostering a collaborative environment, prioritizing key tasks, or leveraging external resources. -->
However, without a transformation protocol for any of the symbiosis partners, bioinformatics often remains a descriptive discipline.
<!-- This sentence acknowledges a limitation in the current work. To provide a more balanced perspective, you might discuss how descriptive bioinformatics still contributes valuable insights, such as by identifying potential targets for future transformation efforts or advancing the understanding of symbiosis mechanisms. -->
As I and my colleagues have struggled with starting bioinformatics in a molecular context, so have our students.
<!-- This sentence introduces an important consideration regarding education and training. To deepen the discussion, you could briefly describe the specific challenges students faced, such as learning new software, understanding complex data, or integrating bioinformatics with experimental work, and how the lab addressed these challenges. -->
The _Azolla_ lab was a molecular biology lab, working on a novel crop with lots of opportunities for sustainability-related research.
<!-- This sentence provides context about the lab's broader mission. To strengthen the connection to the methodology, you might discuss how the lab's focus on sustainability influenced the choice of bioinformatics techniques or research questions, and how these efforts align with broader environmental or agricultural goals. -->
We have learned the hard way that this does not attract your typical bioinformatics-trained student.
<!-- This is an honest observation that adds depth to the narrative. To make it more constructive, consider discussing how the lab adapted its approach to attract and train students, perhaps by developing interdisciplinary projects, offering targeted training, or collaborating with bioinformatics departments. -->
Yet, also students in the lab needed to analyze bioinformatics-related data.
<!-- This sentence emphasizes the necessity of bioinformatics skills. To enhance the narrative, you could briefly describe how the lab integrated bioinformatics training into student projects, and what resources or support were provided to help students succeed in this area. -->
The basic biology curriculum contains little coding, and to this day, biology students can easily finish the bachelor with minimal coding experience.
<!-- This sentence highlights a gap in the education system. To provide more context, you might discuss the implications of this gap for modern biological research, particularly in fields like genomics and bioinformatics, and how the lab has worked to bridge this gap for its students. -->
With the current increase of datasets their size, this seems undesirable to me.
<!-- This sentence effectively conveys your concern about the lack of coding skills in biology education. To strengthen the point, consider providing examples of how large datasets are becoming more common in biological research, and why coding skills are essential for handling and analyzing these data. -->
Teaching students the basics of coding distracts from the biological content of their internships.
<!-- This sentence introduces a key challenge in training students. To provide a more balanced perspective, you might discuss how the lab has worked to integrate coding instruction with biological research, ensuring that students gain both the necessary technical skills and a deep understanding of their biological projects. -->
Additionally, it provides a lot of strain on the host lab.
<!-- This sentence acknowledges the burden on the lab. To enhance the narrative, consider discussing how the lab managed this strain, perhaps by integrating bioinformatics training into the early stages of student projects, providing mentorship, or creating streamlined workflows that allowed students to learn coding in a more structured and less time-consuming way. -->
But the students still need to be educated to do the bioinformatics work for their internship and later in their careers.
<!-- This is a crucial point about the necessity of bioinformatics education. To make it more impactful, you could discuss the long-term benefits for students who acquire these skills, such as improved employability and the ability to tackle more complex research questions, thereby motivating the effort required to teach them. -->
What we as a team have learned from these experiences is that introducing bioinformatics into a molecular biology lab is not just about acquiring the necessary tools and infrastructure.
<!-- This sentence introduces a reflective conclusion, which is valuable. To deepen the reflection, consider adding that it also requires a cultural shift within the lab, where computational work is valued equally with experimental work, and where continuous learning and adaptation are encouraged. -->
It also involves creating a supportive environment where students and researchers can develop the computational skills needed to analyze the increasingly complex datasets generated in modern biological research.
<!-- This sentence effectively wraps up the section. To strengthen the narrative, you might want to emphasize how this supportive environment was cultivated in your lab, possibly by highlighting specific initiatives such as collaborative projects, peer learning, or ongoing professional development opportunities. -->
Our experience has shown that with the right support, even labs without a prior history in bioinformatics can successfully integrate these essential techniques into their research.
<!-- This final sentence is optimistic and encouraging. To make it even more actionable, you could suggest that other labs facing similar challenges could benefit from seeking out collaborations, investing in training, and gradually building their bioinformatics capacity, just as your lab has done. -->

As a wet-lab by training, moving to the computer lab came with challenges.
<!-- This sentence effectively sets up the transition from traditional wet-lab work to bioinformatics. To deepen the narrative, consider briefly outlining some of the specific challenges you encountered, such as adapting to new workflows, learning programming languages, or integrating computational work with experimental data. -->
One major one was documentation and lab journaling.
<!-- This sentence introduces a critical aspect of research—documentation. To enhance the discussion, you could briefly mention why proper documentation is especially important in bioinformatics, where the complexity of data and analyses can easily lead to errors or difficulties in reproducing results. -->
It has always surprised me that despite the obviousness of lab journaling a wet lab experiment, students and staff hardly kept notes when doing computer work.
<!-- This observation highlights an important issue in the lab's transition to bioinformatics. To build on this point, you might discuss how this lack of documentation affected the research process, such as by making it difficult to track progress, troubleshoot issues, or replicate analyses. -->
Admittedly, I have struggled with this myself during my PhD.
<!-- This honest reflection adds a personal touch to the narrative. To make it more instructive, you could briefly describe specific instances where the lack of documentation created challenges for you, and how you addressed these issues over time. -->
Physical written journals, word documents, long comment-lines in scripts, I have tried all these things.
<!-- This sentence effectively conveys the experimentation with different documentation methods. To deepen the discussion, consider briefly evaluating the strengths and weaknesses of each approach, which would provide insights into why you ultimately settled on certain methods over others. -->
Bioinformatics education is relatively young compared to that for molecular biology.
<!-- This sentence provides important context for the challenges faced in documentation. To strengthen the narrative, you might discuss how this relative youth of the field contributes to the lack of standardized practices in areas like documentation and how this is gradually changing as the field matures. -->
Maybe we need to learn biologists still how to properly keep notes on development, code and the underlying biology in a computer lab project.
<!-- This sentence suggests a critical area for improvement in bioinformatics training. To make it more actionable, consider proposing specific strategies for teaching these skills, such as incorporating documentation best practices into bioinformatics curricula, providing templates or guidelines, or emphasizing the importance of documentation in research outputs. -->
In the end, I settled upon splitting the development of code from the interpretation of results.
<!-- This sentence introduces a practical solution. To enrich the narrative, you could briefly explain the reasoning behind this approach—how separating these tasks helped improve clarity, organization, or the overall research process. -->
I committed to writing read-me files in project folders and documenting changes in version control software like Git.
<!-- This is a strong and specific example of good practice. To enhance the impact, you might briefly discuss the benefits of using version control in bioinformatics, such as enabling collaboration, tracking changes, and ensuring the reproducibility of analyses. -->
Biological results, interpretations, and speculations I kept in a note-taking piece of software.
<!-- This sentence highlights a complementary documentation strategy. To provide more context, you could mention why this software was particularly effective for organizing your thoughts and insights, and how it helped integrate the biological aspects of your work with the computational components. -->
This dislodged the interpretation from the data files, but allows for more natural combining of results and ideas from various coding projects.
<!-- This sentence acknowledges a trade-off in your approach. To deepen the discussion, consider explaining how you managed this disjunction, such as by regularly cross-referencing your notes with your data files or by maintaining a clear organizational structure in your projects. -->


<!-- some of the tools and good practices? jupy and R servers, web bases, notebooks!, small shared facility for students and staff to -->

I am quite content with what we have achieved with _Azolla_ genomics.
<!-- This sentence provides a reflective conclusion to the section. To strengthen the narrative, you could briefly summarize the key achievements that you are most proud of, such as specific discoveries, successful implementation of new techniques, or contributions to the field of symbiosis research. -->
Especially considering the lab started from scratch only in 2014, and despite all limitations and challenges posed to us in my almost 7 years at the lab as a student, PhD candidate and part-time teacher.
<!-- This sentence emphasizes the lab's rapid progress and resilience. To make it more impactful, you might highlight specific challenges that were overcome, such as technical limitations, funding constraints, or the steep learning curve associated with adopting bioinformatics, and how these were addressed by the team. -->
There is a lot more work to do, to understand and manipulate the symbiosis.
<!-- This sentence looks to the future, which is a good way to conclude. To add depth, you could briefly outline the most pressing questions or research goals that remain, and how the groundwork laid by your research might facilitate future advancements in these areas. -->
I hope that other labs globally may pick up our work and find it useful for their own experiments.
<!-- This final sentence is optimistic and forward-looking. To enhance the narrative, you could discuss how the work you've done, including the documentation practices and methodologies you've developed, could serve as a model or resource for other labs, potentially accelerating progress in the study of _Azolla_ and symbiosis more broadly. -->

<!-- 
Through advanced sequencing technologies, this research characterizes the genomes of both _Azolla_ and _Nostoc azollae_, revealing the genetic basis of their symbiotic interaction.
Metagenomic approaches further elucidate the broader microbial community associated with _Azolla_, identifying other potential endophytes that contribute to the fern's growth and resilience.
By integrating genomic and metagenomic data, this work seeks to deepen our understanding of the molecular mechanisms driving the _Azolla_-_Nostoc_ symbiosis and to explore its applications in enhancing agricultural sustainability. 
-->

# Outline of this thesis

**Chapter \ref{general_intro}** (\nameref{general_intro} on page \pageref{general_intro}) is the current chapter.
I attempted to take a broader vantage point and less jargon than the remaining chapters.
A lesser-than-formal tone hopefully made this chapter more fun to read to the broader scientific audience interested in my work.

**Chapter \ref{foul_play}** (\nameref{foul_play} on page \pageref{foul_play}) details the initial discovery of prokaryotic DNA sequences in the _A. filiculoides_ genome assembly.
These bacteria associated with _Azolla_ were the main inspiration of this PhD project.
We identify near complete bacterial genomes in whole contigs of this assembly and study these further.
These bacteria are confirmed to be present in _A. filiculoides_ taken from the wild as well as from the lab.
The Non-cyanobacterial prokaryotes are confirmed to be associated with all _Azolla_ species for which WGS data is available.
They may be the same or very related microbes.
Finally, we study the metabolic pathways encoded within these genomes and hypothesise they might denitrify Nitrogen rich compounds within the _A. filiculoides_ leaf pocket.
This hypothesis is falsified however, denitrification occurs only in microbes living epiphytically on _A. filiculoides_.

In **chapter \ref{hidden_treasures}** (\nameref{hidden_treasures} on page \pageref{hidden_treasures}), I build further on the work of chapter \ref{foul_play}.
This chapter details a workflow to enrich and study the genomes of bacteria associated with all sequenced _Azolla_ species.
The workflow thoroughly removes plant DNA reads, and then assembles those of the remaining microbes.
The process of separating distinct microbial genomes (binning) required extra binning signals and manual curation for these were not part of the original experimental design.
Each represented species of the _Azolla_ genus yielded between 12 and 22 associated bacterial genomes.
The majority of these genomes belong only to six taxonomical orders present in the majority of the entire _Azolla_ genus: Burkholderiales, Caulobacterales, Nevskiales, Nostocales, Rhizobiales and Sphingomonadales.
The systematic presence of these taxonomic groups suggests they be selected for in the _Azolla_ symbiosis and they may be vertically transferred over host generations as is the main symbiont _N. azollae_.

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

<!-- **Chapter \ref{partners_and_passengers}** (\nameref{partners_and_passengers} on page \pageref{partners_and_passengers}) is likely not going to happen... -->

**Chapter \ref{it_takes_two}** (\nameref{it_takes_two} on page \pageref{it_takes_two}) provides building blocks for understanding and regulating the sexual reproduction and mode of transmission of the _Azolla_ & _N. azollae_ symbiosis.
Such understanding is a pre-requisite for agricultural application of a novel crop symbiosis.
Several _Azolla_ specimens collected all over the Netherlands were all the same species for they produced viable offspring.
We found that FR light and sporophyte density were main initiators of sexual reproduction while nitrogen availability was an inhibitor.
FR-responsive transcripts included MIKCC homologues of CMADS1 and miR319-controlled GAMYB transcription factors in the fern, transporters in _N. azollae_, and ycf2 in chloroplasts.
Phylogenomic analyses of MIKCC transcription factors suggested that control of flowering and flower organ specification may have originated from the diploid to haploid phase transition in the homosporous common ancestor of ferns and seed plants.

Sexual reproduction of the symbiosis requires that the symbiont is systematically stored in dissemination stages to reinoculate the next generation of hosts.
Contrasting earlier theories, we propose that _N. azollae_ does not colonise developing megasporocarps travelling from leaf pockets to megasporocarps via small channels.
Instead, we theorise that they colonise early sporocarp initials of both types, but are only retained in megasporocarps.
This method of transmission is identical to colonisation of leaf primordia, hence requires no separate machinery and explains consistent observation of _N. azollae_ in very young microsporocarps.

**Chapter \ref{phylogeny_workflow}** (\nameref{phylogeny_workflow} on page \pageref{phylogeny_workflow}) describes a workflow for creating large and state-of-the-art phylogenetic trees of gene families; exemplified in land plants.
Studying fern genetics, the _Azolla_ lab often deals with fern genes that are homologous (similar in sequence) to a seed plant gene.
With phylogeny, we aim to assess the evolution of a gene family and orthology/paralogy of _Azolla_ genes to model species their genes.
While many user friendly methods exist to create phylogenetic trees, these are often either closed-source, or their performance is limited.
Here I created a workflow for basic phylogeny inference with state-of-the-art open source tools, unlimited in their performance.
This workflow is aimed at user skilled in reading a phylogeny, but not in using the CML tools to use the latest software to build them.
It covers data-selection, multiple sequences alignment, alignment trimming, and tree inference.
Additionally, it provides tools to create semi-automatic mark-up for phylogenetic trees in the iToL web interface.

## Appendices

Academics are more than just scientists.
They are often also teachers on universities and leaders and administrators in academic organs.
During my PhD, I attempted to incorporate that broader academic experience in my work.
The doctorate remains intrinsically a scientific degree and this thesis is first and foremost a scientific document.
Still, I add three appendices that give a glimpse in my "extracurricular" activities.
My thesis; the culmination of my PhD, simply would not be complete without them.

Firstly, **Appendix \ref{BKO}** summarises my basic University Teaching Qualification (bUTQ or BKO) application.
About a quarter of My PhD I spend on teaching and developping myself as a Teacher.
This effort was rewarded with a bUTQ or BKO in Dutch.
The full portfolio is too lengthy to include, so this chapter summarises the original document.
Secondly, an example of teaching material that is completely of my own design is included in **Appendix \ref{metagenomics_practical}** (\nameref{metagenomics_practical} on page \pageref{metagenomics_practical}) as mentioned before.
In this practical, students do all major steps of chapter \ref{hidden_treasures} in a day or two.
Finally, I include a short narrative CV on my non-science and non-teaching activities during my PhD and what I gained from them.


<!-- add other appendeces  -->


<!-- gemini: Clearer Thesis Statement: While the introduction effectively sets the stage for the thesis, a more explicit thesis statement would be helpful. Consider adding a sentence or two at the end of the introduction summarizing the main research questions or objectives of your thesis. -->

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
