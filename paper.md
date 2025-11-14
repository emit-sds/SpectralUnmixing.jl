---
title: 'SpectralUnmixing: A general julia package for unmixing spectroscopy data'
tags:
  - Julia
  - Imaging Spectroscopy
  - EMIT
  - Remote Sensing
  - Earth Science
authors:
  - name: Philip G. Brodrick
    orcid: 0000-0000-0000-0000 # todo
    affiliation: "1" # (Multiple affiliations must be quoted)
  - name: Francisco Ochoa
    orcid: 0000-0000-0000-0000 # todo
    affiliation: "2" # (Multiple affiliations must be quoted)
  - name: Gregory Okin
    orcid: 0000-0000-0000-0000 # todo
    affiliation: "2" # (Multiple affiliations must be quoted)
  - name: David Thompson
    orcid: 0000-0000-0000-0000 # todo
    affiliation: "1" # (Multiple affiliations must be quoted)
affiliations:
 - name: Jet Propulsion Laboratory, California Institute of Technology, USA
   index: 1
 - name: University of California, Los Angeles, USA
   index: 2
date: 15 July 2022
bibliography: paper.bib
---

# Summary

On the Earth's surface, mixtures are the norm rather than the exception.
Taken to the limit, virtually every surface can be split into multiple constituents.
Spectral unmixing is the remote sensing retireval process that attempts to 
qauntitately determine the relative fractions of different components that
make up a surface, based on optical data. Imaging spectroscopy, in particular,
has demonstrated the capacity for robust fractional retrievals across a wide range
of domains. 

Spectral unmixing is typically performed using the assumption of linear mixtures.
Some set of candidate 'endmembers' - constituents with known absolute quantities (often pure)
and spectral signatures are provided, and each pixel within an image is linearly
unmixed with these endmembers to retrieve the relative contribution of each. This
reduces to a simple linear algebra inversion at its core, where the known reference 
library can be inverted and multiplied by modeled reflectances to produce mixture fractions.
Details arise however around the nature of the selection of endmembers, with strategies 
ranging from bootstrapping `[@asner:2000]`, combinatorial selection `[@roberts:2001; @franke:2009]`, and dimensionality 
reduction (XXX).  The exact inversion strategy used is also an open and 
problem-speicifc decision, with candidates ranging from direct algebraic inversion 
to a constrained and regularized optimization.

# Statement of need

`SpectralUnmixing` is a Julia package for all types of spectral unmixing strategies,
forcused on imaging spectroscopy data.  The code was designed for NASA's Earth
Surface Mineral Dust Source Investigation (EMIT), when during the algorithm
design phase of the mission it became evident that there was not an optimized
codebase that provided parallel, flexible, unmixing strategies.  In particular,
no central framework existed in which multiple unmixing strategies could be
tested against one another.  `SpectralUnmixing` addressed this issue by drawing
on a huge amount of existing literature, and putting the different proposed
stragies together into a single codebase.  This has already supoprted the 
development of new strategies by combining different pieces of the overal
unmixing problem in new ways, and can continue to provide this type of
coupled flexibility and operational capacity into the future.  `SpectralUnmixing`
draws off of a rich set of Julia packages for linear algebra, optimization,
remote sensing data IO, and more.

While this code was designed to be used operationally for the EMIT mission,
it was also designed to be able to be quickly adapted for different researchers
needs.  A script front-end allows for arguments to be passed in easily and
different options and datasets to be coupled together for rapid testing. Students,
educators, professional researchers, and operational missions can all benefit
from this codebase.

# Citations

Citations to entries in paper.bib should be in
[rMarkdown](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html)
format.

If you want to cite a software repository URL (e.g. something on GitHub without a preferred
citation) then you can do it with the example BibTeX entry below for @fidgit.

For a quick reference, the following citation commands can be used:
- `@author:2001`  ->  "Author et al. (2001)"
- `[@author:2001]` -> "(Author et al., 2001)"
- `[@author1:2001; @author2:2001]` -> "(Author1 et al., 2001; Author2 et al., 2002)"

# Figures

Figures can be included like this:
![Caption for example figure.\label{fig:example}](figure.png)
and referenced from text using \autoref{fig:example}.

Figure sizes can be customized by adding an optional second parameter:
![Caption for example figure.](figure.png){ width=20% }

# Acknowledgements

We acknowledge contributions from Brigitta Sipocz, Syrtis Major, and Semyeong
Oh, and support from Kathryn Johnston during the genesis of this project.

# References