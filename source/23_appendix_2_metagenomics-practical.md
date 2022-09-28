# Metagenomics practical
\label{metagenomics_practical}

## Development of this practial
In the first year of my PhD, I got the opportunity to design a metagenomics practical for Master students with a life sciences background.
The practical introduces the Bash language and tries to learn the main concepts behind metagenomics through a hands-on approach.
Together with a colleague, Margot Schuller, we made a first version based on the data of chapter \ref{fould_play} and tested it during the course.
During the years that followed, I taught and itteratively improved this practical twice a year.
In the before-last year of my PhD, I took up the challenge of coordinating the entire course: Introduction to bioinformatics for Life Sciences (IntroBioinfo).

### Cognitive load theory
The practical is developed with the data from chapter 2, but with the methods in mind of chapter 3.
As I say to the students of the course, during this practical you will re-do the analyses of my first chapter, but better, and within a day or two.
That is quite a challenge, on two completely different fronts.
Firstly, the conceptual front.
Understanding metagenomics, the basic question behind the methodology and the assumptions and simple algorithmics to answer that question.
This already, can be a substantial challenge.
Secondly, the coding required to process the data.
When it comes to bioinformatics education in the Masters, I am a big advocade of learning by doing.
Hence, I want the students of the course actually doing the work, bringing the concepts into practice.
I attempt to sepparate these challenges in time, and supply sufficient reflection time in between the theory and practical.
This is true for the majority of the IntroBioinfo course.
The best version of the course employed a pre-recorded lecture, watched by students a day in advance.
The day after, an expert in the field answered any questions that may have arisen during that lecture.
Next, I shortly explain the practical, and students get hands-on time.
Coginitive load theory inspired me to separate these two aspects of the course.
The reasoning behind this measure, is that the main concepts from the lecture -the essential background to understand the practical- are stored somewhere in recent-long-term memory.
This leaves the students armed with a basic understanding of the goal of the practical and the main concepts of how to get there.
During the practical then, the limited amount of working memory of a human brain can be used to tackle coding questions more easily, without also being bothered by questions like why am I doing this exactly, or what do I achieve with this small step.

### Context and course design
In the context of the course, I taught metagenomics as the third topic and made sure important skills were covered in the days before.
The first day, I introduce bioinformatics in general and teach some basic BASH coding, required for the rest of the course.
After letting this settle in long term memory over night, I continue with "general" genomics.
Like with metagenomics, students have watched a pre-recorded lecture the day before.
The genomics practical is a linear workflow in BASH.
Hence, it's a substantial but reasonable increase in difficulty from the first day.
The metagenomics practical on the other hand, is less linear and includes aggregation of data and refering back to files generated some time earlier.
Hence students have learned about genomics and basic bash by the timethey are confronted with the concepts of metagenomics, non-linear workflows, and medium-advanced bash skills like variables and loops.
Also thematically, the level of abstraction increases.
In genomics, we study a single genome which was a given.
In metagenomics we study multiple genomes, and learn more aboutthey are re-constructed.
The days after, we delve into phylogenetics/comparative genomics, answering the question how to organise and compare all this biological data on the DNA level.
The weeks after, we move futher in the central dogma studying differential expression of mRNA and proteomics.
In the section structural biology, these different levels of the central dogma are then unified again, before we move on to analytics and algorithmic thinking, and network analyses.

`figure genomics practical A, metagenomics practical B`

### Open education
The practical is openly available and GitHub, with instructions and recorded tutorials on youtube for those who would be interested in trying it out.
The GitHub repository contains instructions on how to install the software and get the data.
I chose open source tools only, as is common in the field.
Software is installed and maintained via the conda framework, and I teach students to exercise code in JuPyter notebooks; mixing code and documentation in a single interface. `figure`
Find the repository at [GitHub.com/lauralwd/metagenomicspractical](https://github.com/lauralwd/metagenomicspractical/) and a dedicated website at [lauradijkhuizen.com/metagenomicspractical](https://lauralwd.github.io/metagenomicspractical/).
I have now way of knowing if people other than my students use this practicle, but it does seem the case based on comments on my youtube video's, and a MSc thesis from .. that refers to this practical and uses its data.

![Screenshot of ](source/figures/mgp_jupy_1.png){#fig:mgp_jupy_1}

![Screenshot of ](source/figures/mgp_jupy_2.png){#fig:mgp_jupy_2}

## Learning goals and audience
This practal is aimed at Master's students in Life Sciences with minimal experience in bioinformatics and bachelor level experience in (micro)biology.
However, I also found it suited for bachelor students with bioinformatics experience within a single day time frame.
When supplied with several days and sufficient supervision, bachelors students with programming experience also succesfully completed the practical.
This practical starts by discussing a metagenomics workflow from a biological context, acquiring sequencing data and genome assembly.
Metagenome assembly is rather a resource- and time-intensive process; hence I have done this already. `figure`
Then, the student takes over.
In a nutshell, students extract individual microbial genomes from the metagenome assembly, check their quality, and annotate genes coded in these genomes. `figure`
This practical includes the following steps (and depends on the following tools):

1. (back)mapping (bwa+samtools)
2. binning (MetaBAT)
3. quality control of bins (CheckM)
4. annotation (Prokka)
5. BONUS: phylogeny reconstruction (IQTree)

Answers and prefilled code are available in a separate branch of the GitHub repository called 'example'.
Renders of the empty and pre-filled workflow are available as a GitHub pages website in the 'gh-pages' branch and online at the practical webpage [here](https://lauralwd.github.io/metagenomicspractical/).

![Metagenome assembly of _Azolla filiculoides_ associated bacteria. Data was taken from chapter \ref{foul_play} and assembled with SPAdes (@Nurk2017). The metagenome assembly graph was visualised with Bandage. A fasta file resemling the sequences of this graph was one of the main inputs of this practical.](source/figures/mgp_assembly.png){#fig:mgp_assembly}

After this practical, a student should be able to name and explain the steps of a simple metagenomics workflow.
Starting at acquiring sequencing data, all the way to annotating individual draft genomes.

 - A student can highlight the differences between 'regular' genome sequencing data and assemblies versus metagenomic sequencing data and assemblies (lecture).
 - A student can explain parts of the workflow and their interdependencies from biological and technical perspectives.
 - A student can replicate the workflow taken during the practical on new data sets; being able to plot metabolic capabilities encoded in a metagenome.
 - A student can design similar workflows for different metagenomic questions.
 - A student can explain what binning signals are, why they are used and how you used them during the practical.

If not already, a student will understand the basics of the bash computer language and be able to run bio-informatic programmes in loops.

![Nitrogen metabolism of bacteria ssociated with _Azolla filiculoides_. Data was taken from chapter \ref{fould_play} and processed according to the metagenomics practical described in this appendix. This figure is one of the final results of the practical.](source/figures/mgp_nitrogen_metabolism.png){#fig:mgp_nitrogen_metabolism)
