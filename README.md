Integrating geographic analysis in transport planning workflows: a review of open source options
================
Robin Lovelace
2019-06-03

``` r
# get citations
refs = RefManageR::ReadZotero(group = "418217", .params = list(collection = "JFR868KJ", limit = 100))
```

    ## Ignoring entry 'r_core_team_r:_2019'  (line2) because:
    ##  A bibentry of bibtype 'Article' has to specify the field: c("journaltitle", "journal")

``` r
RefManageR::WriteBib(refs, "software.bib")
```

    ## Writing 66 Bibtex entries ...

    ## OK
    ## Results written to file 'software.bib'

Abstract
========

Software for working with geographic data has long been used in transport planning. Transport is an inherently geographic activity, involving movement through space, from one location to another, along a more or less complicated trajectory. One would therefore expect that geographic data structures and analysis would be a *vital and inbuilt* part of transport planning software. This has not historically been the case, however, and a dichotomy between 'geographic/non-geographic' components of transport planning analysis persists: workflows in academic, public sector and private consultancy transport planning contexts still tend to separate vital geographic processing and map making stages from the rest of the analysis. This paper argues that such a division is damaging to transport planning in three main ways, by: (1) reducing researcher effectiveness and slows down work due to the time-consuming process of 'context switching'; (2) inhibiting reproducibility, by requiring transport planners to learn, install and manage different programs for geographic and non-geographic aspects of their job; and, more fundamentally, (3) preventing transport planners, decision makers and others who use the outputs of transport planning from seeing vital geographic relationships, concepts and consequences, by implicitly encouraging geographic work to be considered as an 'add-on'. Building on this critique, I outline solutions using popular and free open source software ecosystems (R, Python and QGIS) that enable geographic components of data analysis, modelling and visualisation to be *embedded within* transport planning workflows.

Introduction
============

Data preprocessing and analysis stages are generally done in dedicated transport planning and spreadsheet software. Geographic analysis and cartographic visualisation stages are generally done in a dedicated 'geographic information system' (GIS).

<!-- This stuff could go in the introduction. -->
The paper traces how this undesirable situation has arisen due to historical specialisation and monopolisation of transport planning software, based on existing literature, before outlining an integrated approach that combines data analysis and geographic processing stages in a single workflow. Three software ecosystems (R, Python and QGIS) are reviewed in detail; alternative current and potential future approaches, including 'cloud lock in' are discussed; and the relative merits of different approaches are discussed. Building on this discussion, I argue that integrating data analysis and geographic processing in a single analysis has major advantages and outlines concrete steps that researchers, public sector transport planners, and transport planning analysts and consultants can use. The paper concludes that 'integrated approach' can support efficient, scalable and reproducible transport planning workflows which can provide a strong and transparent evidence base needed for rapid transition away from fossil fuels in the transport sector.

The geographic and non-geographic division of labour in Transport Planning
==========================================================================

Integrating geographic analysis in transport planning with open source software
===============================================================================

R
-

(<span class="citeproc-not-found" data-reference-id="rcoreteam_language_2019">**???**</span>)

Python
------

(Rossum 1995)

QGIS
----

(QGIS Development Team 2019)

Conclusion
==========

References
==========

QGIS Development Team. 2019. “QGIS Geographic Information System.” <http://qgis.osgeo.org>.

Rossum, Guido. 1995. “Python Reference Manual.” Amsterdam, The Netherlands, The Netherlands: CWI (Centre for Mathematics; Computer Science).
