\chapter{Metagenomics practical}
\label{metagenomics_practical}

## Development of this practical
In the first year of my PhD, I got the opportunity to design a metagenomics practical for Master's students with a life sciences background.
The practical introduces the Bash language and tries to learn the main concepts behind metagenomics through a hands-on approach.
Together with a colleague, Margot Schuller, we made the first version based on the data of chapter \ref{foul_play} and tested it during the course.
During the years that followed, I taught and iteratively improved this practical twice a year.
In the before-last year of my PhD, I took up the challenge of coordinating the entire course: Introduction to bioinformatics for Life Sciences (IntroBioinfo).

### Cognitive load theory
This practical sets the bar high for students with ample experience.
In order to teach it effectively, I learned about and used cognitive load theory in redesigning the practical.
The exercises are based on the data from chapter \ref{foul_play}, but with the methods in mind of chapter \ref{hidden_treasures}.
As I say to my students, during this practical, you will re-do the analyses of my first research chapter, but better and within a day or two.
Specifically, students will recreate figure 5 from the first research chapter of this thesis (+@fig:fig:fig2_4) and surpass the level of insight we gained in the same chapter.

This task is quite a challenge on two completely different fronts.
Firstly, the conceptual front.
This front encompasses understanding metagenomics, the basic question behind the methodology, underlying assumptions, and simple algorithmics to achieve an answer to that question.
This understanding alone can be a substantial challenge.
The second challenge is the coding required to process the data.
Regarding bioinformatics education in the Masters, I greatly advocate learning by doing.
Hence, I want the students of the course actually doing the work, bringing the concepts into practice.
I attempt to separate these challenges in time and supply sufficient reflection time between the theory and the practical.

This reasoning is applied to the majority of the IntroBioinfo course.
The best version of the course employed a pre-recorded lecture, watched by students a day in advance.
The day after, an expert in the field answered any questions that may have arisen during that lecture.
Next, I shortly explain the practical, and students get hands-on time.
Cognitive load theory inspired me to separate these two aspects of the course.
The reasoning behind this measure is that the main concepts from the lecture -the essential background to understanding the practical- are stored somewhere in recent long-term memory.
This organisation leaves students armed with a basic understanding of the practical's goal and the main concepts.
During the practical, studens can use the limited amount of working memory of a human brain to tackle coding questions more easily, without being bothered by questions like why am I doing this exactly, or what do I achieve with this small step?

### Context and course design
In the context of the course, I taught metagenomics as the third topic and ensured important skills were covered the days before.
On the first day, I introduced bioinformatics in general and taught some basic BASH coding required for the rest of the course.
After letting this settle in long-term memory overnight, I continue with "general" genomics.
As for the metagenomics part, students watched a pre-recorded lecture the day before.
The genomics practical is a linear workflow in BASH (+@fig:mgp_workflow).
Hence, it's a substantial but reasonable increase in difficulty from the first day.
On the other hand, the metagenomics practical is less linear and includes aggregation of data and referring back to files generated sometime earlier.
Hence students have learned about genomics and basic bash by the time they are confronted with the concepts of metagenomics, non-linear workflows, and medium-advanced bash skills like variables and loops.
Also, the level of abstraction increases thematically.
In genomics, we study a single genome which was a given.
In metagenomics, we study multiple genomes and learn more about how they are re-constructed.
The days after, we delve into phylogenetics/comparative genomics, answering how to organise and compare all this biological data on the DNA level.
In the weeks after, we move further in the central dogma studying the differential expression of mRNA and proteomics.
In the section on structural biology, these different levels of the central dogma are then unified again before we move on to analytics, algorithmic thinking, and network analyses.

![Summary of the workflow that students follow in the metagenomics practical. Tasks done by me as preparation are presented on a grey background (A), and tasks done by students during the practical on a white background (B). Green and Blue squares represent the FastQ input data. Bordeaux red squares represent computational tasks. Purple pentagons represent big-data input and output files, and grey-black squares represent human-readable tables. Yellow circles are final results, either figures or tables, that students produce during a practical and are typically found in a metagenomics manuscripts or papers.](source/figures/mgp_workflow.pdf){#fig:mgp_workflow}

### Open education
The practical is openly available and GitHub, with instructions and recorded YouTube tutorials for those interested in trying it out.
The GitHub repository contains instructions on installing the software and getting the data.
I chose open source tools only, as is common in the field.
Software is installed and maintained via the conda framework, and I teach students to exercise code in JuPyter notebooks; mixing various kinds of code and documentation in a single interface (See +@fig:mgp_jupy_1; +@fig:mgp_jupy_2 at the end of this appendix).
Find the repository at [GitHub.com/lauralwd/metagenomicspractical](https://github.com/lauralwd/metagenomicspractical/) and a dedicated website at [lauradijkhuizen.com/metagenomicspractical](https://lauralwd.github.io/metagenomicspractical/).
I have no way of knowing if people other than my students use this practicle, but it does seem to be the case based on comments on my youtube videos.
Additionally, the practical and its data were used for an MSc thesis from Aalborg University (@NiklasFichte2022).
Answers and pre-filled code are available in a separate branch of the GitHub repository called 'example' (+@fig:mgp_jupy_2).
Renders of the empty and pre-filled workflow are available as a GitHub pages website in the 'gh-pages' branch and online at the practical webpage [here](https://lauralwd.github.io/metagenomicspractical/).

![Metagenome assembly of _Azolla filiculoides_ associated bacteria. Data was taken from chapter \ref{foul_play} and assembled with SPAdes (@Nurk2017). The metagenome assembly graph was visualised with Bandage. A fasta file resembling the sequences of this graph was one of the main inputs of this practical.](source/figures/mgp_assembly.png){#fig:mgp_assembly}

## Practical overview, learning goals and audience
This practical is aimed at Master's students in Life Sciences with minimal experience in bioinformatics and bachelor-level experience in (micro)biology.
However, I also found it suited for bachelor's students with bioinformatics experience within a single day.
When supplied with several days and sufficient supervision, bachelor's students with programming experience also successfully completed the practical.
This practical starts by discussing a metagenomics workflow from a biological context, acquiring sequencing data and genome assembly.
Metagenome assembly is a resource- and time-intensive process; hence I have done this already (+@fig:mgp_assembly).
Then, the student takes over.
First, a short BASH introduction or refresher is included since I don't expect students to be fluent in the programming language.
In a nutshell, students extract individual microbial genomes from the metagenome assembly, check their quality, and annotate genes coded in these genomes (+@fig:mgp_nitrogen_metabolism).
This practical includes the following steps (and depends on the following tools):

1. (back)mapping (bwa+samtools)
2. binning (MetaBAT)
3. quality control of bins (CheckM)
4. annotation (Prokka)
5. BONUS: phylogeny reconstruction (IQTree)

![Nitrogen metabolism of bacteria associated with _Azolla filiculoides_. Data was taken from chapter \ref{foul_play} and processed according to the metagenomics practical described in this appendix. This figure is one of the final results of the practical and arguably an improvement over the published version (+@fig:fig:fig2_4).](source/figures/mgp_nitrogen_metabolism.png){#fig:mgp_nitrogen_metabolism}

After this practical, a student should be able to name and explain the steps of a simple metagenomics workflow.
Starting at acquiring sequencing data, all the way to annotating individual draft genomes.

 - A student can highlight the differences between 'regular' genome sequencing data and assemblies versus metagenomic sequencing data and assemblies (lecture).
 - A student can explain parts of the workflow and their interdependencies from biological and technical perspectives.
 - A student can replicate the workflow taken during the practical on new datasets, being able to plot metabolic capabilities encoded in a metagenome.
 - A student can design similar workflows for different metagenomic questions.
 - A student can explain what binning signals are, why they are used and how they used them during the practical.
 - If not already, a student will understand the basics of the bash computer language and be able to run bio-informatic programmes in loops.

### JuPyter examples
![Screenshot of a pre-filled JuPyter notebook page from the metagenomics practical involving Python code. This page was taken from the online example and answers pages.](source/figures/mgp_jupy_2.png){#fig:mgp_jupy_2}

![Screenshot of a JuPyter notebook page from the metagenomics practical involving BASH code. JuPyter notebook pages allow for background, instructions and code exercises to co-exist next to each other in a single environment.](source/figures/mgp_jupy_1.png){#fig:mgp_jupy_1}
