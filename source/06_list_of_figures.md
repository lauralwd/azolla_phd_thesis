<!-- start new chapter but don't increase counter -->
\chapter*{List of Figures}
<!-- but do add this chapter to the ToC -->
\addcontentsline{toc}{chapter}{List of Figures}
<!-- no minitoc -->
\adjustmtc

\listoffigures

<!-- Force page nr on first page of this chapter -->
\thispagestyle{toc}



<!--
The \listoffigures will use short captions first, and the whole caption if none is present. To keep this list readable, ensure each figure has a short caption, e.g.
![main_text_caption](source/figures/my_image.pdf "short caption used in alt text and \listoffigures"){#fig:mylabel}{ width=50% }

See chapter 4 for more examples.
-->

\clearpage
