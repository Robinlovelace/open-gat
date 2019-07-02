Integrating geographic analysis in transport planning workflows: a
review of open source options
================
Robin Lovelace
2019-07-02

# Abstract

Software for working with geographic data has long been used in
transport planning. Transport is an inherently geographic activity,
involving movement through space, from one location to another, along a
more or less complicated trajectory, following spatial networks. One
would therefore expect that geographic data structures and analysis
would be a *vital and inbuilt* part of transport planning software. This
has not historically been the case, however, and a dichotomy between
‘geographic/non-geographic’ components of transport planning analysis
persists: workflows in academic, public sector and private consultancy
transport planning contexts still tend to separate vital geographic
processing and map making stages from the rest of the analysis. This
paper argues that such a division is damaging to transport planning in
three main ways, by: (1) reducing researcher effectiveness and slows
down work due to the time-consuming process of ‘context switching’; (2)
inhibiting reproducibility, by requiring transport planners to learn,
install and manage different programs for geographic and non-geographic
aspects of their job; and, more fundamentally, (3) preventing transport
planners, decision makers and others who use the outputs of transport
planning from seeing vital geographic relationships, concepts and
consequences, by implicitly encouraging geographic work to be considered
as an ‘add-on’. Building on this critique, I outline solutions using
popular and free open source software ecosystems (R, Python and QGIS)
that enable geographic components of data analysis, modelling and
visualisation to be *embedded within* transport planning workflows.

# Introduction

Transport planning is an applied discipline involving not only the
design of ways — highways, railways, cycleways and footways — but also
envisioning the future and making the case for change (O’Flaherty and
Bell 1997). Successful transport plans are long-term strategies that
will have material benefits for people and the local and global
environment for generations to come. Transport planning is thus
inherently embedded within the democratic process: decisions about how
public space is to be used, with impacts for generations to come, cannot
be left to unacountable technocrats in functioning democracies as
illustrated, for example, by prominent Mayoral transport policies in
cities such as London\[1\], Paris\[2\], and Bogotá\[3\].

With issues such as climate change, air pollution, obesity and social
inequalities high on the political agenda, it is likely that many other
cities will adopt innovative transport strategies. This raises questions
of great relevance to researchers: how will future transport be
designed? and based on what evidence and analysis will interventions be
implemented? Both questions link to transport planning methodologies
which, as this paper outlines, increasingly require geographic analysis.
Furthermore, the policy context increasingly demands transparency and
citizen involvement in the decision-making process, which only software
that is open source and reliably deliver, making an exploration of open
source options for transport planning workflows timely.

Practical transport planning is evolving in response to the policy
drivers: transport policies that are evidence-based and grounded in
realistic models of change under different scenarios of the future are
far more likely to be successful than policies based on ideological
commitment and good intentions alone. With unprecedented access to
increasingly detailed datasets on transport behaviours and
infrastructure, transport planners today can ensure that their designs
are more evidence-based that ever. Furthermore, advances in software and
hardware allow not only for current transport systems to be modelled at
high temporal and geographic resolution, but for future scenarios and
‘model experiments’ to be developed, which can lead to identification
and implementation of the most effective interventions. With the
explosion in open source software, which has come to dominate data
science, there is now also a unique opportunity for transport planning
to become a more transparent and democratically accountable enterprise.

However, this dream of data driven, participatory and open transport
planning has yet to emerge. Transport planning as a discipline has been
slow to adapt to the ‘data revolution’ and, while it evolves to enable a
wider range of input data sources and analysis ‘in the cloud’, the open
source element of the dream is conspicuously lacking.

Something on incumbent software…

Data preprocessing and analysis stages are generally done in dedicated
transport planning and spreadsheet software. Geographic analysis and
cartographic visualisation stages are generally done in a dedicated
‘geographic information system’ (GIS).

<!-- This stuff could go in the introduction. -->

The paper traces how this undesirable situation has arisen due to
historical specialisation and monopolisation of transport planning
software, based on existing literature, before outlining an integrated
approach that combines data analysis and geographic processing stages in
a single workflow. Three software ecosystems (R, Python and QGIS) are
reviewed in detail; alternative current and potential future approaches,
including ‘cloud lock in’ are discussed; and the relative merits of
different approaches are discussed. Building on this discussion, I argue
that integrating data analysis and geographic processing in a single
analysis has major advantages and outlines concrete steps that
researchers, public sector transport planners, and transport planning
analysts and consultants can use. The paper concludes that ‘integrated
approach’ can support efficient, scalable and reproducible transport
planning workflows which can provide a strong and transparent evidence
base needed for rapid transition away from fossil fuels in the transport
sector.

# The geographic and non-geographic division of labour in Transport Planning

# Integrating geographic analysis in transport planning with open source software

## R

(R Core Team 2019)

## Python

(Rossum 1995)

## QGIS

(QGIS Development Team 2019)

# Conclusion

# References

<div id="refs" class="references">

<div id="ref-oflaherty_transport_1997">

O’Flaherty, Coleman, and Michael GH Bell. 1997. *Transport Planning and
Traffic Engineering*. Elsevier.

</div>

<div id="ref-qgis_development_team_qgis_2019">

QGIS Development Team. 2019. “QGIS Geographic Information System.”
<http://qgis.osgeo.org>.

</div>

<div id="ref-r_core_team_r:_2019">

R Core Team. 2019. “R: A Language and Environment for Statistical
Computing.” <https://www.R-project.org/>.

</div>

<div id="ref-rossum_python_1995">

Rossum, Guido. 1995. “Python Reference Manual.” Amsterdam, The
Netherlands, The Netherlands: CWI (Centre for Mathematics; Computer
Science).

</div>

</div>

1.  Transport is a major electoral issue in London and the current
    Mayor, Sadiq Kahn, has made tackling air pollution a policy
    priority. See
    [tfl.gov.uk/corporate/about-tfl/the-mayors-transport-strategy](https://tfl.gov.uk/corporate/about-tfl/the-mayors-transport-strategy).

2.   The current Mayor of Paris, Anne Hidalgo, sees transport as a
    priority and has plans to make public transport free. See
    [paris.fr](https://www.paris.fr/rechercher/transport).

3.   Bogotá has an innovative and prominent transport policy, led by the
    two times mayor Enrique Peñalosa, who has led the roll-out of major
    bus and cycleway projects in the city. See
    [sitp.gov.co](https://www.sitp.gov.co/).
