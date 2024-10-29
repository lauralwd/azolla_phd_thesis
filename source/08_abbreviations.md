<!-- start new chapter but don't increase counter -->
\chapter*{Abbreviations}
<!-- but do add this chapter to the ToC -->
\addcontentsline{toc}{chapter}{Abbreviations}
<!-- no minitoc -->
\adjustmtc

<!-- Force page nr on first page of this chapter -->
\thispagestyle{toc}

<!--
Might also be done with:
\usepackage{glossaries}
\makeglossaries -->

\begin{tabbing}

\textbf{ACRONYM}~~~~~~~~~~~~ \= \textbf{A} \textbf{C}oncise \textbf{R}epresentation \textbf{O}f \textbf{N}umerous \textbf{Y}arning \textbf{M}arkings \\
\textbf{ANI}  \>  \textbf{A}verage \textbf{N}ucleotide \textbf{I}dentity \\
\textbf{BASH} \>  \textbf{B}ourne \textbf{A}gain \textbf{Sh}ell \\
\textbf{CML}   \>  \textbf{C}om\textbf{M}and \textbf{L}ine \\
\textbf{CO$_2$} \> \textbf{C}arbon \textbf{D}ioxide \\ 
\textbf{CSP}  \>  \textbf{C}ommon \textbf{S}ymbiosis \textbf{P}athway \\
\textbf{CPU}  \>  \textbf{C}entral \textbf{P}rocessing \textbf{U}nit \\
\textbf{DOI}  \>  \textbf{D}igital \textbf{O}bject \textbf{I}dentifier \\
\textbf{FAIR}  \>  \textbf{F}indable \textbf{A}ccessible \textbf{I}nteroperable \textbf{R}esearchable \\
\textbf{FR}   \>  \textbf{F}ar-\textbf{R}ed (light) \\
\textbf{GUI}  \>  \textbf{G}raphical \textbf{U}ser \textbf{I}nterface \\
\textbf{INDEL} \>  \textbf{Ins}ertion \textbf{Del}etion \\
\textbf{IS elements} \> \textbf{I}nsertion \textbf{S}equences \\
\textbf{MAG}  \>  \textbf{M}etagenome \textbf{A}ssembled \textbf{G}enome \\
\textbf{ML}   \>  \textbf{M}aximum \textbf{L}ikelyhood phylogeny inference\\
\textbf{MSA}  \>  \textbf{M}ulitple \textbf{S}equence \textbf{A}lignment \\
\textbf{NCBI} \>  \textbf{N}ational \textbf{C}entre for \textbf{B}iotechnology \textbf{I}nformation of the United States \\
\textbf{NJ}   \>  \textbf{N}eighbour \textbf{J}oining phylogeny inference \\
\textbf{ORF}  \>  \textbf{O}pen \textbf{R}eading \textbf{F}rame \\
\textbf{PCR}  \> \textbf{P}olymerase \textbf{C}hain \textbf{R}eaction \\
\textbf{RAM}  \>  \textbf{R}andom \textbf{A}ccess \textbf{M}emmory \\
\textbf{SAM}  \>  \textbf{S}hoot \textbf{A}pical \textbf{M}eristem \\
\textbf{SH-aLRT} \> \ \textbf{S}himodaira-\textbf{H}asegawa \textbf{a}proximate \textbf{L}ikelihood \textbf{R}atio \textbf{T}est \\
\textbf{SRA}  \>  \textbf{S}hort \textbf{R}ead \textbf{A}rchive maintained by NCBI \\
\textbf{WGS}  \>  \textbf{W}hole \textbf{G}enome \textbf{S}equencing \\
\textbf{WSL}  \>  \textbf{W}indows \textbf{S}ublayer for \textbf{L}inux \\

\end{tabbing}



<!-- close the last page of this section as required for removing the thumb index on next "part page" -->
\newpage
\null
<!-- don't show page nrs on cleardouble page -->
\pagestyle{plain}
<!-- stop the thumbmarking scheme (partwise) and start it (chapterwise) in the next chapter -->
\stopthumb
<!-- clear double page so that the chapters start nicely on a new right page -->
\cleardoublepage
