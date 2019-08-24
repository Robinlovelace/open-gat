Integrating geographic analysis in transport planning: origins, software
and open source solutions
================
2019-08-24

<!-- should be integrated in transport planning tools. -->

<!-- --- software for transport data analysis, modelling and visualisation --- -->

<!-- workflows in academic, public sector and private consultancy transport planning contexts still tend to separate vital geographic processing and map making stages from the rest of the analysis. -->

# Abstract

<!-- Tools for geographic analysis have long been used in transport planning. -->

<!-- , alongside other (typically primarily economic and engineering) considerations. -->

Transport is inherently geographic. Movement of people, goods and
electrons, between points and polygons along linear ways in spatial
networks, is a defining feature of civilisation. Decarbonising transport
systems is vital for the future. Sustainable transport interventions are
most effective when they are located intelligently.  
Geographic analysis therefore has a huge amount to offer transport
planning and, more specifically, to transport planning tools. Yet
geographic analysis is often treated as an optional ‘add-on’, conducted
in different programs than those typically used in practice for
transport data analysis and modelling. This dichotomy, between
‘geographic’ and ‘non-geographic’ analysis in transport planning is
undesirable because it: (1) reduces researcher effectiveness due to the
time-consuming process of ‘context switching’; (2) prevents
reproducibility, requiring installation and management of geographic and
non-geographic tools; and (3) hides vital geographic components in
transport plans, with adverse consequences for interventions that can
benefit from being placed where they are most needed. These premises are
described in the wider context of transport planning research and the
landscape of transport planning software, which is dominated by
proprietary products. The paper then shifts gear, to focus on open
source solutions. Three emerging software ecosystems for integrating
geographic analysis in transport planning (data analysis and modelling)
workflows are reviewed in depth: the statistical programming language R,
the general purpose programming language Python, and the geographic
information system QGIS. Each ecosystem is found to provide numerous
‘tools of the trade’ for integrating geographic analysis in transport
research, some of which are already being used in practice. In addition
to integrating geographic considerations, the shift to such open source
solutions will have wider benefits for reproducibility, transparency and
democratic accountability in transport planning.
<!--  transport planning experts and the public alike, -->
<!-- Ultimately, by highlighting cost effective and geographically targeted interventions, integrating geographic analysis in transport planning could lead to better decision making. -->
<!-- and support the global efforts to transition away from fossil fuels and towards a healthy, low carbon transport system. -->

<!-- ### Notes/questions -->

<!-- This paper is work in progress and its focus has shifted over time. -->

<!-- A previous working title was "Integrating geographic analysis in transport planning: new open source tools for the trade". -->

<!-- The need to integrate geographic analysis in transport planning is still a central theme of the paper but the focus is now on solutions, in the form of open source software. -->

<!-- Does the paper now have too much on the importance on integrating geographic analysis in transport planning, given the new emphasis? -->

<!-- And are there any other open source software projects I should include, within or in addition to the overview of the three ecosystems selected? -->

# Introduction

<!-- : the importance of geographic analysis in transport planning -->

<!-- Should that heading omit the "Introduction:" part? -->

Transport planning is an applied discipline involving the design and
placement of physical infrastructure, especially ways, including
highways, railways, cycleways and footways (O’Flaherty and Bell 1997;
Parkin 2018). It also involves visioning transport futures and making
the economic and political case for change (Timms, Tight, and Watling
2014). Successful transport plans are therefore a combination of
geographically specific recommendations (e.g. “build this way here”) and
long-term strategies guided by citywide, regional and even national
visions (e.g. “imagine the benefits of making the city free from private
cars by 2030”). The rewards can be great: transport planners who have
designed — and helped to implement — plans appropriate to the needs of
an area leave a legacy that will benefit people and the environment for
generations to come.\[1\]

Transport planning can be considered as “more of an art than a
technique”, although *good* transport plans also rely on robust
analysis and modelling of sometimes large and usually spatial input
datasets (Dios Ort’uzar and Willumsen 2001). Ways and other pieces of
transport infrastructure must *go somewhere* to optimise their ability
to take people *where they want to go*, yet the importance of geography
in transport systems is often overlooked (Rodrigue, Comtois, and Slack
2013). Transport planning is embedded within broader democratic
processes *and* local geographic contexts.

Effective transport planning is inherently embedded within democratic
processes (to the extent that democracy exists in the area where
transport plans are commissioned) because it determines how public
spaces and other shared resources are used, affecting everyone in
society. If transport plans are developed by unaccountable technocrats
with little understanding of their impacts, the results can be severe:
the transport system now is the “leading cause of death for children and
young adults aged 5-29 years” through road traffic casualties alone,
with 1.35 million people killed and tens of millions injured and
disabled each year (World Health Organization 2018). The air pollution
impacts could be even greater, with a growing body of research linking
air pollution to Alzheimer’s disease, lung cancer and heart disease
among hundreds of millions of sufferers worldwide (Kampa and Castanas
2008; Kilian and Kitazawa 2018). Transport is responsible for a quarter
of global greenhouse gas emissions and growing (Harrison and Hester
2017), and is one of the hardest sectors to decarbonise (Moriarty and
Honnery 2008), meaning that evidence-based plans to reduce transport
energy use is an urgent priority affecting the global population,
especially the projected 1.4 billion people who will live in low
elevation (less than 10 m above sea level) coastal zones by 2060
(Neumann et al. 2015).

Transport planning is inherently embedded within local geographic
contexts because transport systems, and the networks of physical
infrastructure that underpins them, are highly localised (Barth’elemy
2011; Levinson 2012) and to some degree dynamic (Xie and Levinson 2011)
phenomena. Transport planning is therefore fundamentally a *spatial
activity*. Perhaps in response to an upsurge in the amount of geographic
transport data available, interest in Transport Geography seems to have
grown over the last decade relative to other terms, according to data
obtained using the **gtrendsR** package (Massicotte and Eddelbuettel
2019) from Google Trends (Figure 1). It is interesting to compare this
growth with relative levels of interest in ‘geographic information
systems’ and ‘spatial planning’, both of which seem to have seen
relative declines over time, notwithstanding the limitations associated
with search data (Mellon
2014).

<img src="google-trends.png" title="Relative level of interest in search terms related to 'geographic information systems', 'geocomputation' and 'transport geography' inferred from google search data, obtained with the gtrendsR R package. Code to reproduce the plot is hosted in this paper's code repository." alt="Relative level of interest in search terms related to 'geographic information systems', 'geocomputation' and 'transport geography' inferred from google search data, obtained with the gtrendsR R package. Code to reproduce the plot is hosted in this paper's code repository." width="70%" />

The growing research interest in the subject is also reflected in
teaching. Modules dedicated to Transport Geography have been advertised
at the Universities of Aberdeen and Hofstra and, at the University of
Leeds the Masters module Sustainable Spatial Planning and Analysis
([SSPA](https://github.com/ITSLeeds/SSPA)) is focussed on GIS skills for
transport planning (declaration of interest: I teach on this module),
and there are even dedicated 3 year degrees Transport Geography.

The paper outlines the relationship between geographic analysis and
transport planning, in relation to the history of geographic thinking in
transport research and practice (in Section 3) and the resulting
specialisation and monopolisation of particular transport planning
software products (outlined in Section 4). The focus of the paper is
Section 5, which reviews open source software ecosystems that enable an
integrated approach, which combines non geographically explicit stages
(e.g. modelling) and geographic processing stages *in a single
workflow*. Three software ecosystems (R, Python and QGIS) are reviewed
in detail; alternative current and potential future approaches,
including ‘cloud lock in’ are discussed; and the relative merits of
different approaches are discussed. Building on this discussion, Section
6 concludes by returning to the importance of integrating geographic
analysis in transport planning workflows. Before proceeding with the
main task of this paper — to review new tools for integrating geographic
analysis in transport planning, and provide guidance to transport
researchers and practitioners tackling 21<sup>st</sup> Century
challenges — it is worth taking a step back, to think about the key
policy drivers of 21<sup>st</sup> century transport
planning.

<!-- and outlines concrete steps that can be taken to accelerate the transition to open source software in transport planning in support of policies that accelerate the transition away from fossil fuels. -->

# Policy drivers for geographic analysis in transport planning

The history of transport modelling shows that transport planning
software was originally designed to plan for “increased use of cars
\[for personal travel\], and trucks for deliveries and goods movement”
(Boyce and Williams 2015). Despite the fact that policy drivers have
changed dramatically — with climate change mitigation, air quality
improvement and public health prioritised in the ‘sustainable mobility
paradigm’ (Hickman, Ashiru, and Banister 2011) — incumbent transport
software still largely based on tools focussed on motor traffic,
emphasising travel time savings and (de)congestion effects of
interventions at relatively low levels of geographic resolution. Tools
for 21<sup>st</sup> Century transport planning will need to tackle very
different questions, such as: What are the barriers preventing people
from switching to more sustainable modes of transport, and where are
these barriers located? How are transport behaviours likely to shift in
the future, in response to technological changes including autonomous
vehicles and the continued rise of online working? Where will different
types of intervention be most effective? And how can citizens be engaged
in transport decisions? Tools that can help answer these questions are
becoming an increasingly important part of the transport planner’s
cabinet (te Brömmelstroet and Bertolini 2008).

To illustrate this point, imagine being the mayor of a major city that
has declared a ‘climate emergency’ and being given the task of leading
the transition away from fossil fuels (Hadfield and Cook 2019). Policies
such as carbon taxes would undoubtedly have geographic implications, but
the intervention itself (charging a fixed price for the extraction and
sale of atmosphere polluting substances) could be essentially
non-geographic. Notwithstanding changes to national policies relating to
transport, transport planning options, by contrast, are inherently
spatial. Even high level national plans for a walking and cycling
revolution must be implemented locally, down to the level of streets, as
illustrated by the still ongoing local implementation of Dutch cycling
ambitions (Pucher and Buehler 2008). The political-democratic and
local-geographic aspects of transport planning can be considered in
isolation, but an integrated approach is necessary for effective
policies (Hull 2008). This is well illustrated by prominent Mayoral
transport policies in cities such as London\[2\], Paris\[3\], and
Bogotá\[4\].

With such issues — climate change, air pollution, obesity and social
inequalities — high on the political agenda, and the benefits for ‘early
adopters’ of evidence-based interventions to accelerate the shift away
from the motor car in cities such as London, Paris and Bogotá, pressure
is growing on local, city and national transport planning departments to
act. But what should they do? This *policy* question raises important
*research* questions: Which methods are most suitable for designing
future transport systems? What is the evidence base, and analysis, that
should be used to inform transition towards a healthy, zero carbon
transport system? Which interventions, from the multitude of options
available, are most likely to be effective? And where are different
types of intervention most likely to succeed? The premise of this paper
is that new approaches, enabled by software, are needed to provide
answers to these questions. 21<sup>st</sup> Century demands for
transport planning cannot be delivered by 20<sup>th</sup> century
technology. Could open source solutions are poised to bridge the gap
between the geographic and the — historically dominant — non-geographic
aspects of transport planning? Planning for sustainable modes, walking
and cycling in particular, requires analysis at higher geographic
resolutions than planning for motor traffic. Furthermore, the policy
context increasingly demands transparency and citizen involvement in the
decision-making process. Only open source ecosystems, of the type
outlined in Section @ref(new-tools-of-the-trade) can deliver true
transparency and encourage ‘citizen science’ for everyone. These policy
drivers make an exploration of open source options for transport
planning workflows timely.

Additional drivers of change in transport planning software include new
datasets and technologies. Technological change has historically driven
innovation in transport planning tools (Boyce and Williams 2015) and the
rate of change now is faster than ever. With unprecedented access to
increasingly detailed datasets on transport behaviours and
infrastructure, transport planners today require tools that enable them
to make sense of this ‘data revolution’ (Transport Systems Catapult
2015). The sheer volume and complexity of new datasets require new
approaches that can scale and integrate multiple data sources (Lovelace
et al. 2016). Advances in software and hardware allow not only for
current transport systems to be modelled at high temporal and geographic
resolution, but for future scenarios and ‘model experiments’ to be
developed, which can support identification and implementation of the
most effective interventions (Klosterman 1999).

With the explosion in open source software, which has come to dominate
data science, policy, data and technological drivers are pushing
geographic analysis to be better integrated in transport planning tools,
alongside wider shifts for towards more data driven, transparent and
democratically accountable transport planning workflows. At present this
dream is far from reality, despite a long history of geographic thinking
and geographic methods in transport planning, outlined in the next
section.

<!-- Transport planning has been slow to adapt to the data revolution and, while it evolves to enable a wider range of input data sources and analysis 'in the cloud', the open source element is conspicuously lacking. -->

<!-- To understand and effectively challenge the incumbent software landscape (which is described in Section xx) it is worth understanding something of the history that led to this situation. -->

# Geographic analysis and transport planning

The concept of integrating geographic data analysis in transport
planning is not new, although tools and datasets for doing so
quantitatively are. Geographic perspectives have contributed to
transport thinking for over 100 years, as documented in papers on
geographic considerations in railway design and other transport
engineering challenges (Farnham 1912; Buxton 1908). Since then, the
importance of geographic analysis in transport planning has only grown,
with the realisation that interventions in the transport system are most
effective when they are placed where they are most needed:
infrastructure designs and localised policies are most effective when
they account for the geographic distribution of intricate spatial
networks and interacting places of transport supply and demand
(Rodrigue, Comtois, and Slack 2013; Loidl et al. 2016; Lovelace et al.
2017).

In the inter-war period (1918-1939) disciplinary homes for transport
research had yet to emerge and geographic analysis was limited by lack
of datasets and computers on which to process them. The term ‘transport
geography’ itself only became widespread in the 1950s, as noted in a
report commissioned by the US Office of Naval Research: “geographers,
both in Europe and America, are coming to recognize that the study of
the connections between areas and of spatial interchange can provide a
new and deeper insight into the meaning of areal differentiation”
(Ullman and Mayer 1954). In the pre-computing age the relationship
between geographic analysis and transport planning was characterised by
growing interest in the topic, an understanding of the importance of
geographic considerations in the design and evolution of transport
systems, but lack of data and computational resources.\[5\]

At the turn of the computing age in the 1950s and 1960s transport
planners, whose primary task was often to enable rapid growth in car
ownership and use, quickly saw the potential for computational tools to
assist their work (Boyce and Williams 2015): “essential to \[new methods
in transport planning\] were new computational capabilities, the first
mainframe computers, unprecedented in memory and speed \[yet\] tiny from
today’s perspective”. As *Forecasting Urban Travel* (Boyce and Williams
2015) recounts, geographic questions were at the forefront of many
planners’ minds and a key task for the early transport models was to
visualise and model the results of large origin-destination surveys to
help decide where new highways should be constructed.

The origins of this ‘computational transport planning’ activity, in
which geographic analysis was an integral part, were publicly funded
transport planners and engineers solving real real world problems.
However academics, and quantitative geographers in particular, soon
started working with newly available transport datasets. An important
development was the emergence of spatial interaction models, which were
formally defined, refined and implemented throughout the 1960s and 1970s
(Wilson 1967, 1971). It is notable that Alan Wilson, whose research
influenced both transport planning and academic practice, worked in both
the public sector (for the UK’s Ministry of Transport) and academia (the
University of Leeds) while writing each paper. Most academic research at
the interface between transport planning and geographic research is far
less ‘practitioner facing’ and, if anything, it seems that tools used in
geographic analysis of transport systems in practice since the 1970s
have diverged from academic
research.

<!-- perhaps explaining why the field of Transport Geography, which emerged in the 1960s and grew rapidly since then [@hay_transport_1979], has (to the author's knowledge) had relatively few other notable impacts on transport planning practice. -->

By the late 1970s, there was enough research for review papers
reflecting on the status of Transport Geography as a self-standing
branch of Geography (Rimmer 1978). A book on the transport geography of
India provides an insight into the field at the time, with a focus on
infrastructure and statistics, transport geography sat firmly in the
quantitative tradition of geographic research (Raza and Aggarwal 1986),
despite Rimmer (1979) criticism that much of the field ignored the wider
impacts of transport systems. Geographic analysis in transport research
was given a substantial boost in the 1990s, with the first publication
of the Journal of Transport Geography (Knowles 1993). Transport
Geography has subsequently come to be defined as a branch of geography.
Notwithstanding influential methodological and review papers proving
transport planners with insight into the state-of-the-art (e.g.
Mart’ınez and Viegas 2013), the level of engagement between academic
transport geographers and transport planning practitioners is debatable
(although the same could also be said of academic planners).

Around the turn of the century, there were attempts to define a more
applied geographic information systems (GIS) approach transport
research. Labelled GIS-T, the field was posited as an academic field at
the interface between transport planning and GIS (Miller 1999). Although
the label gained limited traction in academia or practice, Harvey
Miller’s call for a shift to methods and tools has been answered in
the 2000s and 2010s by researchers who have developed ideas and software
that transport planners can actually use, including the Australian
Research Infrastructure Network (AURIN), which is widely used for
transport planning and public health research in Australia (Pettit et
al. 2014) and the Propensity to Cycle Tool (PCT, publicly available,
including source code, at [www.pct.bike](https://www.pct.bike)) (Goodman
et al.
2019).

<!-- Search term for interwar period: https://scholar.google.co.uk/scholar?q="transport+geography" -->

<!-- something on the lack of open source? -->

<!-- https://www.abdn.ac.uk/registry/courses/undergraduate/2016-2017/geography/gg4016
https://people.hofstra.edu/jean-paul_rodrigue/course_transport.html
 in Geography with Transport Studies BA advertised by the University of Leeds
-->

<!-- The paper concludes that 'integrated approach' can support efficient, scalable and reproducible transport planning workflows which can provide a strong and transparent evidence base needed for rapid transition away from fossil fuels in the transport sector. -->

# The landscape of transport planning software

Before describing the existing landscape, it is worth outline what
transport planning software is. Software for transport planning can be
grouped by the scale at which it operates, with broad categories being
‘micro’ and ‘macro’ models (Kotusevski and Hawick 2009). ‘Microscopic’
transport models represent individual vehicles on the road network and
are therefore able to represent localised phenomena such as traffic
congestion. Macro models, by contrast, represent aggregates of vehicular
traffic over large spatial scales, with a focus on the implications of
future changes in transport behaviour and infrastructure on flow at the
route network level. Of course the distinction is, in reality, an
oversimplification: there is a continuum between micro and macro
transport modelling software. With advances in computer hardware and
software, an increasing number of developers are attempting to combine
both approaches into a single system. In this paper we focus on macro
models, and their geographic representation, rather than micro models.

The geographic and non-geographic division of labour is a result of the
history of transport planning software. This history is detailed in
Chapter 10 of *Forecasting Urban Travel* (Boyce and Williams 2015).
Titled “Computing environment and travel forecasting software”, the
chapter provides a unique insight into the software packages that have
been popular in transport planning over the years. Of course, software
development has always depended on the physical hardware on which it
runs and the early days of transport planning software were
characterised by bespoke programs running on mainframe computers and
maintained by domain experts. Transport planning bodies and researchers
in the USA led developments in the 1960s and 1970s when computers first
started to be used for transport planning, when the main problem that
they addressed was how to deal with the explosive growth in car
ownership and use that was taking place during those decades. More
overtly political factors also influenced the direction of transport
planning software: “certain private firms complained to US DoT
\[Department of Transport\] that its agencies were developing software
in competition with the private sector”, leading to the abandonment of
publicly funded transport planning software development projects,
notably UTPS (Boyce and Williams 2015).\[6\] This transfer of transport
planning software development to the private sector contrasts with the
history of GIS, in which open source solutions have come to dominate .
The example of GRASS (Geographic Resources Analysis Support System)
illustrates this point and helps explain the dominance of proprietary
software in transport planning. Like UTPS, GRASS was a publicly funded
software project. Unlike UTPS, it was made freely available to the
public and was open sourced (in 1999), meaning that it has been under
continuous development by state, academic and commercial organisation
since 1982 (Neteler and Mitasova 2008). Would the landscape of transport
planning software have been different if the DoT had continued to fund
software development projects? That question is outside the scope of
this paper. What is certain, however, is that software used in transport
planning over the past three decades has been dominated by companies and
that the sector has been slow to adopt open an open source approach.

In response to the ‘siloed’ development of GIS and transport software,
there have been calls for greater integration. Loidl et al. (2016),
building on the observation that “geography and GIS remained a niche
topic within traditional transport modeling”, made a case for
strengthening the ‘spatial perspective’ in transport modelling. The
paper emphasised the growing importance of well-defined data types,
disaggregating detailed (and difficult to interpret) transport model
outputs, and geographic data visualisation and concluded that much
further research is needed: “future research and development is needed
to combine geospatial functionalities with transport modeling, while
providing an efficient, interactive, visual interface for data
exploration, manipulation, analysis and visualization” (Loidl et al.
2016). Although the paper focussed on conceptual issues rather than
software per-se, it did identify mention four open source programming
languages that could provide the foundation for future developments, two
of which (R and Python) are covered in the next section.

Data preprocessing and analysis stages are generally done in dedicated
transport planning and spreadsheet software. Geographic analysis and
cartographic visualisation stages are often done in a dedicated (GIS).
Some prominent transport planning software products, and levels of
support for geographic data analysis, are summarised in Table
1.

| Software | Company/Developer  | Licence           | I | G | R | RNA | SV | IV | EX |
| :------- | :----------------- | :---------------- | :- | :- | :- | :-- | :- | :- | :- |
| Visum    | PTV                | Proprietary       | Y | Y | Y | Y   | Y  | ?  | ?  |
| MATSim   | TU Berlin          | Open source (GPL) | Y | ? | Y | Y   | Y  | ?  | ?  |
| TransCAD | Caliper            | Proprietary       | Y | Y | Y | Y   | Y  | ?  | ?  |
| SUMO     | DLR                | Open source (EPL) | Y | ? | ? | Y   | Y  | ?  | ?  |
| Emme     | INRO               | Proprietary       | Y | Y | Y | Y   | Y  | ?  | Y  |
| Cube     | Citilabs           | Proprietary       | Y | ? | ? | Y   | Y  | ?  | ?  |
| sDNA     | Cardiff University | Open source (GPL) | Y | Y | Y | Y   | ?  | ?  | ?  |

Sample of transport modelling software in use by practitioners. Note:
citation counts based on searches for company/developer name, the
product name and ‘transport’. The columns I, G, R, RNA, SV, IV and EX
refer to Import of a wide range of geographic data formats, Geographic
capabilities such as buffer calculations and intersections, Route
calculation, Route Network Analysis, Static Visual outputs, Interactive
Visual outputs for web publication, and Export to a wide range of
geographic data formats, with ? meaning partial support (e.g. via add-on
software). Data source: Google Scholar searches, October 2018.

Table 1 shows that popular transport planning tools have differing
levels of geographic capabilities. It should be noted that the
geographic capabilities were assessed based on reading of publicly
available manuals (to be linked to in an appendix accompanying this
paper) and that each software product is actively developed, meaning
that the results may change with additional information and subsequent
releases. An interesting pattern is that the open source options —
MATSim, SUMO and sDNA — all have limited ‘in house’ geographic
capabilities. This can be explained by the ‘Unix philosophy’, the second
tenet of which is modularity, meaning that “each program should do one
thing well”, reducing duplication of effort and allowing the best tool
to be used for each job (Gancarz 2003). The next section describes the
this modularity in more detail, including outstanding support for
geographic data in open source software.

A major barrier affecting the current landscape of transport planning
tools is accessibility and reproducibility: All the proprietary products
are expensive (costing hundreds of dollars for a single licence),
ensuring that only a small fraction of transport planners, let alone the
public, has access to them. Another barrier associated with the
proprietary options is platform dependence: as far as the author can
tell, they all run only on the proprietary operating system Windows,
preventing use in on other operating systems such as Linux, Mac and
FreeBSD. A final issue affecting reproducibility with the proprietary
options listed in Table 1 is that they all have a prominent Graphical
User Interface (GUI) (although they increasingly offer a command line
interface, enabling scripting). As is the case with GUI based GIS
software, this has the “unintended consequence of discouraging
reproducibility” by enabling the user to get to a solution without
writing a script that others can use (Lovelace, Nowosad, and Meunchow
2019).

Another barrier, which may affect the open source options listed in
Table 1 more than the proprietary options, is that they can be (in the
author’s experience) difficult to install and use. This creates an
additional barrier to the integration of geographic analysis in
transport planning for people, especially the majority of people who
have limited computing skills.

A final barrier, which may be more social and organisational than
software-related (although discerning cause and effect is difficult), is
that organisations’ GIS and Transport functions tend to be siloed into
their respective departments/teams with little communication between
them, meaning that transport planners may not have access to the latest
geographic data or software.\[7\] A software-related issue is that, if
transport planners and GIS analysts are using different programs for
their work, transport planners will be less likely to collaborate with
people with geographic analysis skills or identify potential geographic
solutions to their domain-specific problems. To what extent can these
barriers be overcome by open source software ecosystems? That is the
topic of the next section.

# New tools of the trade

The previous sections support and expand on the two main premises of
this paper: that geographic analysis has much to offer transport
planning, and that the incumbent proprietary software products are not
well suited to tackle 21<sup>st</sup> Century transport planning needs.
In this section the paper shifts gear, and moves onto solutions. It
outlines the growth of free and open source software (FOSS) and how the
movement can provide the foundations for more democratic and transparent
transport planning workflows that bridge the ‘geographic gap’ in
transport planning data analysis, modelling and visualisation. The focus
is on three software ‘ecosystems’ — R, Python and QGIS — that are
particularly promising for integrated geographic analysis in transport
planning.

Before exploring these ecosystems, it is worth first taking a step back
and considering the open source software landscape and what ‘open
source’ actually means. This overview also helps explain why R, Python
and QGIS were selected from the range of open source options for closer
attention.

<!-- Despite the central role that open source software plays, powering the majority of the world's servers... -->

Open source software differs from proprietary software in that users are
free to see, download and modify the underlying source code that defines
it. Freedom is central to open source software, which is sometimes
referred to simply as ‘free software’, defined by the Free Software
Foundation ([FSF](https://www.fsf.org/about/what-is-free-software)) as
follows:

> software that gives you the user the freedom to share, study and
> modify it.

This adaptability is conducive to collaboration, the creation of
mutually supportive user/developer communities and rapid evolution,
making open source software ecosystems fast moving and highly diverse.
It is impossible to discuss all software options that could be used for
geographic transport planning: there are literally thousands of software
projects, written in hundreds of programming languages, many of which
are no longer actively maintained. Transport planners should use
solutions that are future proof and actively maintained — such as R,
Python and QGIS.

A key advantage of ecosystems based on a *command line interface* (CLI),
such as R and Python, rather than ecosystems based on a *graphical user
interface* (GUI), such as QGIS, is reproducibility. A programming
approach, in which the user interacts with the computer primarily by
typing code, enables others to see and potentially reproduce analysis
just by sharing the underlying code. Programming also provide great
flexibility: the user is not constrained by the options provided in the
GUI. The downside of CLIs is that they can take time to learn,
especially for people who have been trained on GUI-based software such
as Microsoft Word. Transport data analysis has much in common with the
broadly defined field of ‘data science’, and many of the tools developed
for this purpose (including those in the R and Python ecosystems
detailed below) have great potential for transport planning. Other open
source ecosystems include those surrounding the languages JavaScript,
Julia and Rust, and the GUI-based Java application
[IRIS](http://iris.dot.state.mn.us/). Promising as these, and many
other, open source projects are, R, Python and QGIS were selected due to
their maturity, wide uptake in industry and academia for data science
(for R and Python, meaning a large user community) and geographic
analysis (for QGIS). They have also seen impressive growth in popularity
over the past decade, suggesting they are future proof, as illustrated
in Figure
2.

<img src="google-trends-facet.png" title="Relative number of searches for terms related to open source (R and Python) and proprietary-based (VBA) programming languages (left) and open source programs (Pychame, QGIS, RStudio) that can be used for transport planning. Code to reproduce the plot is hosted in this paper's code repository." alt="Relative number of searches for terms related to open source (R and Python) and proprietary-based (VBA) programming languages (left) and open source programs (Pychame, QGIS, RStudio) that can be used for transport planning. Code to reproduce the plot is hosted in this paper's code repository." width="70%" />

Each open source ecosystem, and it’s potential to be used for geographic
analysis in transport planning, is outlined below.

## R

R is a “a language and environment for statistical computing and
graphics” (R Core Team 2019). First announced and released as a binary
program in 1993 by University of Aukland statisticians Robert Gentleman
and Ross Ihaka, the project was only open sourced and released under the
conditions of the GNU General Public License (GPL) in 1995, thanks to
input from one of R’s first international collaborators, Martin Mächler
of ETH Zurich (Ihaka 1998). This history highlight’s how open source
software development is an inherently collaborative process, usually
involving people from many different countries and backgrounds.

R has several strengths from the perspective of transport planning,
including its proficiency with temporal and geographic data, outstanding
visualisation capabilities, and support for a very wide range of
statistical techniques, many of which are useful in transport problems
(Lovelace and Ellison 2018). Out of the box R is a statistical powertool
that can solve a wide range of problems, including generalised linear
models (GLMs, implemented with the function `glm`) and constrained
optimisation problems that appear frequently in transport research.
Additional capabilities are supported by 10,000+ packages that can be
installed from a central repository with commands such as
`install.packages("stplanr")`.\[8\]

A good example of a transport problem that R’s statistical capabilities
are well suited to solving is mode choice. Unimodal models estimating
mode share (or the logit thereof) can use R’s inbuilt statistical
capabilities, as demonstrated in the Propensity to Cycle Tool project
(Lovelace et al. 2017). More sophisticated multinomial models are needed
when estimating mode share across multiple travel options such as walk,
cycle, bus (Mart’ın and P’aez 2019). R has mature support for such
models via the `multinom` function in the longstanding package `nnet`
(Venables and Ripley 2002), as demonstrated by [Germán
Rodríguez](https://data.princeton.edu/wws509/r/c6s2). Subsequent
packages provide additional methods for estimating mode split (Hasan,
Wang, and Mahani 2016; Croissant 2019). Appollo and mlr3 are recently
developed examples of R packages providing support for sophisticated
choice models and cutting edge machine learning functionality,
respectively.

<!-- [@hess_apollo_2019;@bischl_mlr:_2016]. -->

R is well known for having outstanding statistical analysis and
modelling capabilities, of the type useful in transport planning. Less
known is that R also has a mature ecosystem for working with geographic
data, making it well suited to the task of integrating geographic
analysis in transport planning: R excels at doing modelling *and*
geographic analysis. This is particular interest here because, as
outlined in previous sections, ‘context switching’ between programs for
statistical and geographic analysis is time consuming.\[9\] Support for
geographic data and methods have a long history in R (Rowlingson et al.
2003; Bivand 2006; Pebesma et al. 2015; Bivand, Pebesma, and
G’omez-Rubio 2013). The development of R’s spatial capabilities are
well documented elsewhere \[link to other articles in the special
edition\]. However, a few advances are worth mentioning due to their
relevance to transport transport planning. The package `sf` (Pebesma
2018) provides a unified and high performance system for working
geographic lines (in addition to its support for points and polygons),
which can be used to represent roads. Building on `sf`, the package
`stplanr` (Lovelace and Ellison 2018) provides many functions for
working with geographic transport data, including `overline` which
enables thousands routes to be aggregrated to create route networks
(Morgan and Lovelace, in press) and `dl_stats19`, which has evolved into
the `stats19` package (Lovelace et al. 2019). Geographic data
visualisation, cartography, is another area where R excels, with
packages such as `tmap` (Tennekes 2018) providing powerful functions for
map making. These and many other packages for working with geographic
data in R are described in detail in *Geocomputation with R* (Lovelace,
Nowosad, and Meunchow 2019). Chapter 12 this of this open source book is
dedicated to transport applications, and provides a good starting point
for learning more about using R’s impressive geographic capabilities for
transport planning.

## Python

Python is a general-purpose programming language originally conceived in
the late 1980s and first released in 1991 (Rossum 1995). The language
was designed from a computer science perspective, with a focus on code
elegance and consistency, rather than R’s focus on statistical
functionality. However, Python has become very popular for data analysis
and ‘data science’ thanks to packages such as
[Pandas](https://github.com/pandas-dev/pandas), and SciKitLearn
(McKinney 2017). Due to its range of features, large open source
community, and flexibility, Python has been used as a ‘glue’ language to
interact with many other software systems. It is a highly diverse
language that is widely used in domains ranging from web development
(Grinberg 2018), to computer vision and (Zafar et al. 2018) text
analysis (Bengfort, Bilbro, and Ojeda 2018).

Of particular interest here is Python’s support for geographic data.
There are dozens of geographic projects written in Python, ranging from
the use of the language to teach low level geographic concepts and
algorithms (Xiao 2016) to its use as an interface to libraries such as
GDAL. Dozens of Python packages have been published for solving specific
geographic problems, ranging from the processing of scientific
gravimetric measurements (McCubbine et al. 2018) to handling remote
sensing data for Ireland (Serbin and Green 2018), both of which could
have transport applications. Furthermore, Python is used as the language
of choice of choice for command-line interfaces to the popular
proprietary GIS ArcMAP (Zandbergen 2015).

More general purpose package for handling spatial datasets that could be
used for transport research include [GeoPandas](http://geopandas.org/),
for handling vector data such as roads and
[rasterio](https://rasterio.readthedocs.io/en/stable/) for handling
raster datasets. Building on such foundations, a number of Python
developers have written packages with a transport focus. This include
OSMnx (Boeing 2017), for downloading and analysing street network data
from OpenStreetMap and the recent and ambitious project (Pappalardo et
al. 2019) which, despite limited documentation at the time of writing,
sets out to create a framework for modelling transport systems.

Because Python is a general purpose language, it has been used as the
basis of transport applications that go beyond the transport planning
remit of this paper. A couple of projects are worth mentioning to give
an indication of the wider Python transport ecosystem.
[Itinerum](https://github.com/TRIP-Lab) is an open source travel survey
development project, which includes a backend written in Python and
smartphone apps (Patterson et al. 2019). A similar project is
[E-mission](https://github.com/e-mission) (Shankari et al. 2018) the
backend of which is partly written in Python.

## QGIS

QGIS is a cross-platform desktop GIS application with a huge user base
(likely the most popular GIS software in the world) and more than 1000
community supported plugins (QGIS Development Team 2019). QGIS itself is
written primarily in C++ and Python, meaning that there is strong
symbiosis between the Python and QGIS ecosystems. In fact the majority
of QGIS plugins are written in Python, meaning that Python developers
can use QGIS as a platform for providing users with a graphical user
interface and, conversely, QGIS users can learn to use a CLI, via QGIS’s
Python console.

A good example of the flexibility of QGIS’s plugin model, and
illustrating the wider point that open source software tends to be
modular and do ‘one thing well’, is that sDNA, mentioned in Section
@ref(the-landscape-of-transport-planning-software) can be used in QGIS
via the sDNA plugin (Cooper and Chiaradia 2015). Indeed, the open source
transport modelling framework MATSim also benefits from being used
alongside QGIS, for road network editing and visualisation (Horni,
Nagel, and Axhausen 2016). QGIS plugins and extensions specifically
designed for transport planning applications include the AwaP-IC
walkability analysis plugin (Majic and Pafka 2019), extensions to QGIS’s
Processing model development framework for assessing road network
completeness (Sehra, Singh, and Rai 2017) and the ORS (OpenRouteService)
plugin, for multi-modal routing.

QGIS can also be used as a self-standing application for transport data
analysis. Ilayaraja (2013), for example, used QGIS as the platform of
choice for analysing street networks using the [Road Graph
plugin](https://docs.qgis.org/2.14/en/docs/user_manual/plugins/plugins_road_graph.html),
which ships with QGIS by default. Dong et al. (2016), to provide another
example, used QGIS as the basis of geographic analysis of route network
efficiency. Hundreds of other transport planning projects have used QGIS
for the mapping and geographic analysis component of the work and, due
to the application’s user friendly GUI, it is rapidly gaining in
popularity among government transport planning departments, including
Transport for Wales and Transport for Greater Manchester.

# Conclusion

Geographic analysis is an important yet often under-appreciated aspect
of transport planning, and looks set to play a more prominent role in
transport policy-making due to technological, data and policy drivers of
change. In the context of the obesity crisis, air pollution concerns and
the ‘climate emergency’ that has been declared by some city authorities,
many transport planners have been tasked with discouraging energy
intensive modes, particularly car use, and enabling more walking and
cycling (Hickman, Ashiru, and Banister 2011) . Furthermore, in the age
of evidence-based policy, open data and citizen science, there is an
onus on practitioners to provide solutions that are transparent,
accessible and, increasingly, participatory \[@\] .

This poses a challenge to incumbent transport planning software which is
expensive and thereby inaccessible to most people, monolithic and (to a
greater or lesser extent) limited in terms of geographic capabilities,
particularly in relation to publicly accessible interactive
visualisation and adaptability. Partly in response to these pressures
and challenges, a number of open source transport planning tools have
emerged, notably MATSim, SUMO and sDNA. Following the Unix philosophy of
modularity (Gancarz 2003), each of these tools has a particular niche.
However, despite a long history of geographic thinking in transport
planning and calls to strengthen the links between GIS and transport
software (Loidl et al. 2016) but none of the open source solutions
reviewed provide ‘in house’ GIS capabilities of the type needed for an
integrated transport planning workflow in which a single piece of
software can be used to import a range data, undertake statistical
analysis and modelling and plot the results in interactive maps,
e.g. for the design and modelling of new walking and cycling networks.

With a view to the future of transport planning software, three
established ‘software ecosystems’, each of which has a substantial
following and large community of developers building extensions, were
reviewed with respect to their capacity to support geographic analysis
in transport planning. The literature shows that R, Python and QGIS
communities have already developed several tools for transport planning
that, when combined with other open source solutions, can solve a very
wide range of spatial transport planning problems. Although each
ecosystem is mature (yet still growing), their use in transport planning
is still in a nascent phase, suggesting that much innovation, evolution
and consolidation will occur before any strong conclusions about which
is most appropriate for different transport planning tasks can be made.
However, tentative guidance can be made, based on the origins and
direction of each project: for statistically-orientated projects in
which interactive online visualisation is vital, R provides a strong
foundation; for applications in which general purpose languages and
interoperability with other frameworks, and integration with other
software frameworks, Python may be the most appropriate option; and when
a user friendly interface and rapid map making without need for
programming skills are required, QGIS may be suitable. There is a huge
amount of overlap between the three ecosystems and, in practice, the
prior experience and preferences of transport planners may be more
important than functionality.

As the FOSS philosophy described in Section @ref(new-tools-of-the-trade)
emphasises, open source software by its very nature is collaborative,
innovative and evolving (Gancarz 2003), allowing it to out-compete and
eventually dominate in sectors from machine learning to web development.
The review of capabilities in open source software communities clearly
shows that high-performance and innovative solutions are already
available in the ‘ecological niche’ of geographic analysis for transport
planning. Given the nascent nature of many of the transport-oriented
packages, plugins and extensions in each ecosystem, fruitful directions
of research would explore the relative merits of different options, and
combinations of options, in terms of computer and programmer efficiency.
Furthermore, the modular and ‘pluginable’ nature of open source software
suggests there are great opportunities for integration: could there be R
and Python interfaces to MATSim, SUMO and sDNA? And from a research
perspective, how can the growth of open source solutions for geographic
transport data analysis be monitored to identify ‘tipping points’ in
practitioners’ uptake of open source solutions?

These considerations wider questions, about if and when will open source
software rise to ascendancy in the wider field of transport planning.
Returning to the most urgent policy driver of climate change mitigation,
it is clear than a step change is needed in transport interventions. If
these interventions are made on the basis of analysis undertaken in open
source software — enabling rigorous, transparent and reproducible
evidence that can easily be repeated in new settings and when new
datasets become available — they are all the more likely to succeed. In
this sense it may not be an exaggeration to say that open source
software can save the world.

# References

<div id="refs" class="references">

<div id="ref-barthelemy_spatial_2011">

Barth’elemy, Marc. 2011. “Spatial Networks.” *Physics Reports* 499
(1–3): 1–101.

</div>

<div id="ref-bengfort_applied_2018">

Bengfort, Benjamin, Rebecca Bilbro, and Tony Ojeda. 2018. *Applied Text
Analysis with Python: Enabling Language-Aware Data Products with Machine
Learning*. " O’Reilly Media, Inc.".

</div>

<div id="ref-bivand_implementing_2006">

Bivand, Roger. 2006. “Implementing Spatial Data Analysis Software Tools
in R.” *Geographical Analysis* 38 (1): 23–40.
<https://doi.org/10.1111/j.0016-7363.2005.00672.x>.

</div>

<div id="ref-bivand_applied_2013">

Bivand, Roger, Edzer J Pebesma, and Virgilio G’omez-Rubio. 2013.
*Applied Spatial Data Analysis with R*. Vol. 747248717. Springer.

</div>

<div id="ref-boeing_osmnx:_2017">

Boeing, Geoff. 2017. “OSMnx: New Methods for Acquiring, Constructing,
Analyzing, and Visualizing Complex Street Networks.” *Computers,
Environment and Urban Systems* 65 (September): 126–39.
<https://doi.org/10.1016/j.compenvurbsys.2017.05.004>.

</div>

<div id="ref-boyce_forecasting_2015">

Boyce, David E., and Huw C. W. L. Williams. 2015. *Forecasting Urban
Travel: Past, Present and Future*. Edward Elgar Publishing.

</div>

<div id="ref-buxton_balkan_1908">

Buxton, Noel. 1908. “Balkan Geography and Balkan Railways.” *The
Geographical Journal* 32 (3): 217–34.

</div>

<div id="ref-cooper_sdna:_2015">

Cooper, Crispin, and Alain J. Chiaradia. 2015. “sDNA: How and Why We
Reinvented Spatial Network Analysis for Health, Economics and Active
Modes of Transport.” University of Cardiff.

</div>

<div id="ref-croissant_mlogit:_2019">

Croissant, Yves. 2019. *Mlogit: Multinomial Logit Models*.
<https://CRAN.R-project.org/package=mlogit>.

</div>

<div id="ref-ortuzar_modelling_2001">

Dios Ort’uzar, Juan de, and Luis G. Willumsen. 2001. *Modelling
Transport*. John Wiley; Sons.

</div>

<div id="ref-dong_population-weighted_2016">

Dong, Lei, Ruiqi Li, Jiang Zhang, and Zengru Di. 2016.
“Population-Weighted Efficiency in Transportation Networks.”
*Scientific Reports* 6 (May): 26377.
<https://doi.org/10.1038/srep26377>.

</div>

<div id="ref-farnham_relation_1912">

Farnham, Amos W. 1912. “The Relation of Some Recent Engineering Problems
to Geography.” *Journal of Geography* 11 (2): 40–45.

</div>

<div id="ref-fox_main_1923">

Fox, Florence C. 1923. *Main Streets of the Nation a Series of Projects
on Highway Transport for Elementary Schools*. Department for the
Interior.

</div>

<div id="ref-gancarz_linux_2003">

Gancarz, Mike. 2003. *Linux and the Unix Philosophy*. Digital Press.

</div>

<div id="ref-goodman_scenarios_2019">

Goodman, Anna, Ilan Fridman Rojas, James Woodcock, Rachel Aldred,
Nikolai Berkoff, Malcolm Morgan, Ali Abbas, and Robin Lovelace. 2019.
“Scenarios of Cycling to School in England, and Associated Health and
Carbon Impacts: Application of the ‘Propensity to Cycle Tool’.” *Journal
of Transport & Health* 12 (March): 263–78.
<https://doi.org/10.1016/j.jth.2019.01.008>.

</div>

<div id="ref-greenshields_studying_1936">

Greenshields, Bruce D. 1936. “Studying Traffic Capacity by New Methods.”
*J. Appl. Psychol* 20 (3): 353–58.

</div>

<div id="ref-grinberg_flask_2018">

Grinberg, Miguel. 2018. *Flask Web Development: Developing Web
Applications with Python*. " O’Reilly Media, Inc.".

</div>

<div id="ref-hadfield_financing_2019">

Hadfield, Paris, and Nicole Cook. 2019. “Financing the Low-Carbon City:
Can Local Government Leverage Public Finance to Facilitate Equitable
Decarbonisation?” *Urban Policy and Research* 37 (1): 13–29.
<https://doi.org/10.1080/08111146.2017.1421532>.

</div>

<div id="ref-harrison_environmental_2017">

Harrison, R. M., and R. E. Hester. 2017. *Environmental Impacts of Road
Vehicles: Past, Present and Future*. Royal Society of Chemistry.

</div>

<div id="ref-hasan_fast_2016">

Hasan, Asad, Zhiyu Wang, and Alireza S. Mahani. 2016. “Fast Estimation
of Multinomial Logit Models: R Package Mnlogit.” *Journal of Statistical
Software* 75 (1): 1–24. <https://doi.org/10.18637/jss.v075.i03>.

</div>

<div id="ref-hickman_transitions_2011">

Hickman, Robin, Olu Ashiru, and David Banister. 2011. “Transitions to
Low Carbon Transport Futures: Strategic Conversations from London and
Delhi.” *Journal of Transport Geography*, Special section on Alternative
Travel futures, 19 (6): 1553–62.
<https://doi.org/10.1016/j.jtrangeo.2011.03.013>.

</div>

<div id="ref-horni_multi-agent_2016">

Horni, Andreas, Kai Nagel, and Kay W. Axhausen. 2016. *The Multi-Agent
Transport Simulation MATSim*. Ubiquity Press.
<https://www.ubiquitypress.com/site/books/10.5334/baw/>.

</div>

<div id="ref-hull_policy_2008">

Hull, Angela. 2008. “Policy Integration: What Will It Take to Achieve
More Sustainable Transport Solutions in Cities?” *Transport Policy*, New
Developments in Urban Transportation Planning, 15 (2): 94–103.
<https://doi.org/10.1016/j.tranpol.2007.10.004>.

</div>

<div id="ref-ihaka_r:_1998">

Ihaka, Ross. 1998. “R: Past and Future History.” *Computing Science and
Statistics* 392396.

</div>

<div id="ref-ilayaraja_road_2013">

Ilayaraja, K. 2013. “Road Network Analysis in Neyveli Township,
Cuddalore District by Using Quantum GIS.” *Indian Journal of Computer
Science and Engineering* 4 (1).

</div>

<div id="ref-kampa_human_2008">

Kampa, Marilena, and Elias Castanas. 2008. “Human Health Effects of Air
Pollution.” *Environmental Pollution*, Proceedings of the 4th
International Workshop on Biomonitoring of Atmospheric Pollution (With
Emphasis on Trace Elements), 151 (2): 362–67.
<https://doi.org/10.1016/j.envpol.2007.06.012>.

</div>

<div id="ref-kilian_emerging_2018">

Kilian, Jason, and Masashi Kitazawa. 2018. “The Emerging Risk of
Exposure to Air Pollution on Cognitive Decline and Alzheimer’s
Disease–Evidence from Epidemiological and Animal Studies.” *Biomedical
Journal*.

</div>

<div id="ref-klosterman_what_1999">

Klosterman, R. E. 1999. “The What If? Collaborative Planning Support
System.” *Environment and Planning B: Planning and Design* 26 (3):
393–408. <https://doi.org/10.1068/b260393>.

</div>

<div id="ref-knowles_research_1993">

Knowles, Richard D. 1993. “Research Agendas in Transport Geography for
the 1990s.” *Journal of Transport Geography* 1 (1): 3–11.
<https://doi.org/10.1016/0966-6923(93)90033-V>.

</div>

<div id="ref-kotusevski_review_2009">

Kotusevski, G., and K. A. Hawick. 2009. “A Review of Traffic Simulation
Software.” *Research Letters in the Information and Mathematical
Sciences* 13: 35–54. <https://mro.massey.ac.nz/handle/10179/4506>.

</div>

<div id="ref-levinson_network_2012">

Levinson, David. 2012. “Network Structure and City Size.” *PloS One* 7
(1): e29721. <https://doi.org/10.1371/journal.pone.0029721>.

</div>

<div id="ref-loidl_gis_2016">

Loidl, Martin, Gudrun Wallentin, Rita Cyganski, Anita Graser, Johannes
Scholz, and Eva Haslauer. 2016. “GIS and Transport
Modeling—Strengthening the Spatial Perspective.” *ISPRS International
Journal of Geo-Information* 5 (6): 84.
<https://doi.org/10.3390/ijgi5060084>.

</div>

<div id="ref-lovelace_big_2016">

Lovelace, Robin, Mark Birkin, Philip Cross, and Martin Clarke. 2016.
“From Big Noise to Big Data: Toward the Verification of Large Data
Sets for Understanding Regional Retail Flows.” *Geographical Analysis*
48 (1): 59–81. <https://doi.org/10.1111/gean.12081>.

</div>

<div id="ref-lovelace_stplanr:_2018">

Lovelace, Robin, and Richard Ellison. 2018. “Stplanr: A Package for
Transport Planning.” *The R Journal* 10 (2): 7–23.
<https://doi.org/10.32614/RJ-2018-053>.

</div>

<div id="ref-lovelace_propensity_2017">

Lovelace, Robin, Anna Goodman, Rachel Aldred, Nikolai Berkoff, Ali
Abbas, and James Woodcock. 2017. “The Propensity to Cycle Tool: An Open
Source Online System for Sustainable Transport Planning.” *Journal of
Transport and Land Use* 10 (1). <https://doi.org/10.5198/jtlu.2016.862>.

</div>

<div id="ref-lovelace_stats19:_2019">

Lovelace, Robin, Malcolm Morgan, Layik Hama, and Mark Padgham. 2019.
“Stats19: A Package for Working with Open Road Crash Data.” *Journal
of Open Source Software*. <https://doi.org/10.21105/joss.01181>.

</div>

<div id="ref-lovelace_geocomputation_2019:1">

Lovelace, Robin, Jakub Nowosad, and Jannes Meunchow. 2019.
*Geocomputation with R*. CRC Press. <http://robinlovelace.net/geocompr>.

</div>

<div id="ref-majic_awap-icopen-source_2019">

Majic, Ivan, and Elek Pafka. 2019. “AwaP-IC—an Open-Source GIS Tool for
Measuring Walkable Access.” *Urban Science* 3 (2): 48.

</div>

<div id="ref-martin_individual_2019">

Mart’ın, Bel’en, and Antonio P’aez. 2019. “Individual and Geographic
Variations in the Propensity to Travel by Active Modes in
Vitoria-Gasteiz, Spain.” *Journal of Transport Geography* 76: 103–13.

</div>

<div id="ref-martinez_new_2013">

Mart’ınez, L. Miguel, and Jos’e Manuel Viegas. 2013. “A New Approach to
Modelling Distance-Decay Functions for Accessibility Assessment in
Transport Studies.” *Journal of Transport Geography* 26: 87–96.
<https://doi.org/10.1016/j.jtrangeo.2012.08.018>.

</div>

<div id="ref-massicotte_gtrendsr:_2019">

Massicotte, Philippe, and Dirk Eddelbuettel. 2019. *gtrendsR: Perform
and Display Google Trends Queries*.
<https://github.com/PMassicotte/gtrendsR>.

</div>

<div id="ref-mccubbine_gsolve_2018">

McCubbine, Jack, Fabio Caratori Tontini, Vaughan Stagpoole, Euan Smith,
and Grant O’NABrie. 2018. “Gsolve, a Python Computer Program with a
Graphical User Interface to Transform Relative Gravity Survey
Measurements to Absolute Gravity Values and Gravity Anomalies.”
*SoftwareX* 7: 129–37.

</div>

<div id="ref-mckinney_python_2017">

McKinney, Wes. 2017. *Python for Data Analysis: Data Wrangling with
Pandas, NumPy, and IPython*. 2 edition. Sebastopol, California: O’Reilly
Media.

</div>

<div id="ref-mellon_internet_2014">

Mellon, Jonathan. 2014. “Internet Search Data and Issue Salience: The
Properties of Google Trends as a Measure of Issue Salience.” *Journal of
Elections, Public Opinion and Parties* 24 (1): 45–72.
<https://doi.org/10.1080/17457289.2013.846346>.

</div>

<div id="ref-miller_potential_1999">

Miller, Harvey J. 1999. “Potential Contributions of Spatial Analysis to
Geographic Information Systems for Transportation (GIS-T).”
*Geographical Analysis* 31 (4): 373–99.
<https://doi.org/10.1111/j.1538-4632.1999.tb00991.x>.

</div>

<div id="ref-moriarty_prospects_2008">

Moriarty, Patrick, and Damon Honnery. 2008. “The Prospects for Global
Green Car Mobility.” *Journal of Cleaner Production* 16 (16): 1717–26.
<https://doi.org/10.1016/j.jclepro.2007.10.025>.

</div>

<div id="ref-neteler_open_2008">

Neteler, Markus, and Helena Mitasova. 2008. *Open Source GIS: A GRASS
GIS Approach*. Third. New York, NY: Springer.

</div>

<div id="ref-neumann_future_2015">

Neumann, Barbara, Athanasios T. Vafeidis, Juliane Zimmermann, and Robert
J. Nicholls. 2015. “Future Coastal Population Growth and Exposure to
Sea-Level Rise and Coastal Flooding-a Global Assessment.” *PloS One* 10
(3): e0118571.

</div>

<div id="ref-oflaherty_transport_1997">

O’Flaherty, Coleman, and Michael GH Bell. 1997. *Transport Planning and
Traffic Engineering*. Elsevier.

</div>

<div id="ref-pappalardo_scikit-mobility:_2019">

Pappalardo, Luca, Gianni Barlacchi, Filippo Simini, and Roberto
Pellungrini. 2019. “Scikit-Mobility: An Open-Source Python Library for
Human Mobility Analysis and Simulation.” *arXiv:1907.07062 \[Physics\]*,
July. <http://arxiv.org/abs/1907.07062>.

</div>

<div id="ref-parkin_designing_2018">

Parkin, John. 2018. *Designing for Cycle Traffic: International
Principles and Practice*. ICE Publishing.
<https://www.icevirtuallibrary.com/isbn/9780727763495>.

</div>

<div id="ref-paterson_horse_1926">

Paterson, James. 1926. “Horse Transport and Motor Transport.” *RSA
Journal* 74 (3837): 689–702.

</div>

<div id="ref-patterson_itinerum:_2019">

Patterson, Zachary, Kyle Fitzsimmons, Stewart Jackson, and Takeshi
Mukai. 2019. “Itinerum: The Open Smartphone Travel Survey Platform.”
*SoftwareX* 10 (July): 100230.
<https://doi.org/10.1016/j.softx.2019.04.002>.

</div>

<div id="ref-pebesma_simple_2018">

Pebesma, Edzer. 2018. “Simple Features for R: Standardized Support for
Spatial Vector Data.” *The R Journal*.
<https://journal.r-project.org/archive/2018/RJ-2018-009/index.html>.

</div>

<div id="ref-pebesma_software_2015">

Pebesma, Edzer, Roger Bivand, Paulo Justiniano Ribeiro, and others.
2015. “Software for Spatial Statistics.” *Journal of Statistical
Software* 63 (1): 1–8.
<http://brage.bibsys.no/xmlui/bitstream/id/320781/Pebesma_Bivand_Ribeiro.pdf>.

</div>

<div id="ref-pettit_australian_2014">

Pettit, C.J., J Barton, X Goldie, R Sinnott, R Stimson, and T Kvan.
2014. “The Australian Urban Intelligence Network Supporting Smart
Cities.” In *Smart Cities and Planning Support Systems*, edited by S
Geertma, J Stillwell, J Ferreira, and J Goodspeed. Springer.

</div>

<div id="ref-pucher_making_2008">

Pucher, John, and Ralph Buehler. 2008. “Making Cycling Irresistible:
Lessons from the Netherlands, Denmark and Germany.” *Transport Reviews*
28 (4): 495–528. <https://doi.org/10.1080/01441640701806612>.

</div>

<div id="ref-qgis_development_team_qgis_2019">

QGIS Development Team. 2019. “QGIS Geographic Information System.”
<http://qgis.osgeo.org>.

</div>

<div id="ref-raza_transport_1986">

Raza, Moonis, and Yash Aggarwal. 1986. *Transport Geography of India:
Commodity Flows and the Regional Structure of the Indian Economy*.
Concept Publishing Company.

</div>

<div id="ref-r_core_team_r:_2019">

R Core Team. 2019. “R: A Language and Environment for Statistical
Computing.” <https://www.R-project.org/>.

</div>

<div id="ref-rimmer_redirections_1978">

Rimmer, Peter J. 1978. “Redirections in Transport Geography.” *Progress
in Geography* 2 (1): 76–100.

</div>

<div id="ref-rodrigue_geography_2013">

Rodrigue, Jean-Paul, Claude Comtois, and Brian Slack. 2013. *The
Geography of Transport Systems*. Third. London, New York: Routledge.

</div>

<div id="ref-rossum_python_1995">

Rossum, Guido. 1995. “Python Reference Manual.” Amsterdam, The
Netherlands, The Netherlands: CWI (Centre for Mathematics; Computer
Science).

</div>

<div id="ref-rowlingson_rasp:_2003">

Rowlingson, Barry, Adrian Baddeley, Rolf Turner, and Peter Diggle. 2003.
“Rasp: A Package for Spatial Statistics.” In *Proceedings of the 3rd
International Workshop on Distributed Statistical Computing*, edited by
Kurt Hornik.
<https://www.r-project.org/conferences/DSC-2003/Proceedings/RowlingsonEtAl.pdf>.

</div>

<div id="ref-sehra_assessing_2017">

Sehra, Sukhjit, Jaiteg Singh, and Hardeep Rai. 2017. “Assessing
OpenStreetMap Data Using Intrinsic Quality Indicators: An Extension to
the QGIS Processing Toolbox.” *Future Internet* 9 (2): 15.

</div>

<div id="ref-serbin_open-sourced_2018">

Serbin, Guy, and Stuart Green. 2018. “Open-Sourced Remote Sensing Data
Management with the Irish Earth Observation (IEO) Python Module.”
*Preprints.org*, May.
<https://doi.org/10.20944/preprints201805.0470.v1>.

</div>

<div id="ref-shankari_e-mission:_2018">

Shankari, K., Mohamed Amine Bouzaghrane, Samuel M. Maurer, Paul Waddell,
David E. Culler, and Randy H. Katz. 2018. “E-Mission: An Open-Source,
Smartphone Platform for Collecting Human Travel Data.” *Transportation
Research Record* 2672 (42): 1–12.
<https://doi.org/10.1177/0361198118770167>.

</div>

<div id="ref-te_brommelstroet_developing_2008">

te Brömmelstroet, Marco, and Luca Bertolini. 2008. “Developing Land Use
and Transport PSS: Meaningful Information Through a Dialogue Between
Modelers and Planners.” *Transport Policy* 15 (4): 251–59.
<https://doi.org/10.1016/j.tranpol.2008.06.001>.

</div>

<div id="ref-tennekes_tmap:_2018">

Tennekes, Martijn. 2018. “Tmap: Thematic Maps in R.” *Journal of
Statistical Software, Articles* 84 (6): 1–39.
<https://doi.org/10.18637/jss.v084.i06>.

</div>

<div id="ref-timms_imagineering_2014">

Timms, Paul, Miles Tight, and David Watling. 2014. “Imagineering
Mobility: Constructing Utopias for Future Urban Transport.” *Environment
and Planning A* 46 (1): 78–93. <https://doi.org/10.1068/a45669>.

</div>

<div id="ref-transport_systems_catapult_transport_2015">

Transport Systems Catapult. 2015. “The Transport Data Revolution.”
Government. Transport Systems Catapult.
<https://ts.catapult.org.uk/wp-content/uploads/2016/04/The-Transport-Data-Revolution.pdf>.

</div>

<div id="ref-trewartha_japanese_1934">

Trewartha, Glenn T. 1934. “Japanese Cities Distribution and Morphology.”
*Geographical Review* 24 (3): 404–17. <https://doi.org/10.2307/208912>.

</div>

<div id="ref-ullman_transportation_1954">

Ullman, Edward L., and Harold M. Mayer. 1954. “Transportation
Geography.” WASHINGTON UNIV SEATTLE.

</div>

<div id="ref-venables_modern_2002">

Venables, W. N., and B. D. Ripley. 2002. *Modern Applied Statistics with
S*. Fourth. New York: Springer. <http://www.stats.ox.ac.uk/pub/MASS4>.

</div>

<div id="ref-wilson_statistical_1967">

Wilson, AG. 1967. “A Statistical Theory of Spatial Distribution Models.”
*Transportation Research* 1 (3): 253–69.

</div>

<div id="ref-wilson_family_1971">

———. 1971. “A Family of Spatial Interaction Models, and Associated
Developments.” *Environment and Planning* 3 (January): 1–32.
<http://www.environment-and-planning.com/epa/fulltext/a03/a030001.pdf>.

</div>

<div id="ref-world_health_organization_global_2018">

World Health Organization. 2018. *Global Status Report on Road Safety
2018*. S.l.
<https://www.who.int/violence_injury_prevention/road_safety_status/2018/en/>.

</div>

<div id="ref-xiao_gis_2016">

Xiao, Ningchuan. 2016. *GIS Algorithms: Theory and Applications for
Geographic Information Science & Technology*. London.
<https://doi.org/10.4135/9781473921498>.

</div>

<div id="ref-xie_evolving_2011">

Xie, Feng, and David Levinson. 2011. *Evolving Transportation Networks*.
Transportation Research, Economics and Policy. New York:
Springer-Verlag. <https://www.springer.com/gp/book/9781441998033>.

</div>

<div id="ref-zafar_hands-convolutional_2018">

Zafar, Iffat, Giounona Tzanidou, Richard Burton, Nimesh Patel, and
Leonardo Araujo. 2018. *Hands-on Convolutional Neural Networks with
TensorFlow: Solve Computer Vision Problems with Modeling in TensorFlow
and Python*. Packt Publishing Ltd.

</div>

<div id="ref-zandbergen_python_2015">

Zandbergen, Paul A. 2015. *Python Scripting for ArcGIS*. Esri press.

</div>

</div>

1.   Articles about successful transport planners illustrate the point.
    Ben Hamilton-Baillie (1955 - 2019), for example, was an influential
    transport planner and street designer whose obituary stated that
    “hundreds of thousands of people who are safer and happier as a
    result of his achievements” (Tim Stornor, quoted in
    [TransportExtra](https://www.transportxtra.com/publications/local-transport-today/news/60655/obituary-ben-hamilton-baillie/)).

2.  Transport is a major electoral issue in London and the current
    Mayor, Sadiq Kahn, has made tackling air pollution a policy
    priority. See
    [tfl.gov.uk/corporate/about-tfl/the-mayors-transport-strategy](https://tfl.gov.uk/corporate/about-tfl/the-mayors-transport-strategy).

3.   The current Mayor of Paris, Anne Hidalgo, sees transport as a
    priority and has plans to make public transport free. See
    [paris.fr](https://www.paris.fr/rechercher/transport).

4.   Bogotá has an innovative and prominent transport policy, led by the
    two times mayor Enrique Peñalosa, who has led the roll-out of major
    bus and cycleway projects in the city. See
    [sitp.gov.co](https://www.sitp.gov.co/).

5.   Paterson (1926), for example, speculated quite accurately on the
    continued rise of motor traffic at the expense of horse powered
    transport during the 20<sup>th</sup> Century, noting the importance
    of geographic factors in determining mode choice, down to the street
    level: “Many streets, like our Bond Street, Watling Street or
    Lombard Street, and in Seville, the Calle de las Sierpes or Kalver
    Straat in Amsterdam, may be unsuited to motor traffic, and frontage
    values may be so high that widening can hardly be considered.” In a
    geographic review of Japanese cities Trewartha (1934) also alluded
    to the relationship between geography and mode choice: “widening and
    paving of \[roads\] have (sic) been accomplished \[allowing\]
    numerous taxis, motor busses, and tram cars contrasting with the
    slow human and animal-drawn carts and the ubiquitous bicycle”. Rapid
    industrialisation during the largely unconscious build-up to World
    War II was associated with major road building schemes in many
    developed regions, demanding the practical application of new
    methods from a range of disciplines (e.g. Greenshields 1936). In the
    USA, highway engineering even became a recommended case study for
    geography lessons (Fox 1923).

6.   UTPS stands for the UMT (Urban Mass Transportation Administration,
    an agency of the DoT responsible for transport planning)
    Transportation Planning System (UTPS) and PLANPAC

7.   Thanks to Crispin Cooper, author of sDNA, for raising this barrier.

8.   Like Python packages, R packages are analogous to Apps on
    smartphones and plugins in QGIS (described below), that provide new
    functionality. Many implement recently developed statistical and
    computational techniques (some of which are accompanied by papers
    describing new methods in academic journals such as the *Journal for
    Statistical Software*) or provide interfaces to software written in
    other languages, meaning that R can provide transport researchers
    with access to many cutting-edge methods via a single system.

9.   The author has first hand experience of the costs of
    context-switching: during my PhD I used R for the statistical and
    modelling analysis, and then switched to QGIS for geographic
    analysis and visualisation. While this approach worked well, the
    cognitive burden of having to learn and manage two substantial
    programs was substantial.
