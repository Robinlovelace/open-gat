Integrating geographic analysis in transport planning with open source
software
================
Robin Lovelace
2019-07-06

# Abstract

Software for working with geographic data has long been used in
transport planning. Transport is an inherently geographic activity,
involving movement through space, from one location to another on the
face of the Earth, along more or less complicated trajectories defined
by ways (highways, cycleways, footways etc) that can be defined as a
spatial network. One would therefore expect that geographic data
structures and analysis would be a *vital and inbuilt* part of transport
planning software. This has not historically been the case, however. A
dichotomy between ‘geographic/non-geographic’ components of transport
planning analysis persists: workflows in academic, public sector and
private consultancy transport planning contexts still tend to separate
vital geographic processing and map making stages from the rest of the
analysis. This paper argues that this division inadvertently damages
transport planning in three main ways, by: (1) reducing researcher
effectiveness and slows down work due to the time-consuming process of
‘context switching’; (2) inhibiting reproducibility, by requiring
transport planners to learn, install and manage different programs for
geographic and non-geographic aspects of their job; and, more
fundamentally, (3) preventing transport planners, decision makers and
others who use the outputs of transport planning from seeing vital
geographic relationships, concepts and consequences, by implicitly
encouraging geographic work to be considered as an ‘add-on’. Building on
this critique, this paper outlines solutions using popular and free open
source software ecosystems (R, Python and QGIS) that enable geographic
components of data analysis, modelling and visualisation to be *embedded
within* transport planning workflows. This process of integrating
geographical analyis has implications that go beyond academic transport
research: more explicit inclusion of geography in transport planning
will lead to better decision making, something that is vital in the
context of the global transition away from the private motor car that
the climate, obesity and air pollution crises demand.

# Introduction

Transport planning is an applied discipline involving not only the
design of ways — including highways, railways, cycleways and footways —
but also envisioning the future and making the case for change
(O’Flaherty and Bell 1997). Successful transport plans are long-term
strategies guided by citywide, regional and even national visions that
will have material benefits for people and the local and global
environment for generations to come. But transport plans are also
inherently spatial: the ways and other pieces of transport
infrastructure must *go somewhere* to optimise their ability to take
people *where they want to go* (Rodrigue, Comtois, and Slack 2013).

Transport planning is thus embedded within broad democratic processes
*and* local geographic contexts. Effective transport planning is
inherently democratic because it determines about how public space is to
be used, with impacts for generations to come. If transport plans are
developed by unacountable technocrats with little understanding of
transport’s impacts on other economies, the results can be severe: the
transport system now is the “leading cause of death for children and
young adults aged 5-29 years” through road traffic casualties alone,
with 1.35 million people killed and tens of millions injured and
disabled each year (World Health Organization 2018). The air pollution
impacts could be even worse, with a growing body of research linking air
pollution to Alzheimer’s disease, lung cancer and heart disease among
hundreds of millions of sufferers worldwide (Kampa and Castanas 2008;
Kilian and Kitazawa 2018). Transport is responsible for a quarter of
global greenhouse gas emissions and growing (Harrison and Hester 2017),
and is one of the hardest sectors to decarbonise (Moriarty and Honnery
2008), meaning that evidence-based plans to reduce transport energy use
is an urgent priority affecting the global population and especially the
projected 1.4 billion people who will live in low elevation (less than
10 m above sea level) coastal zones by 2060 (Neumann et al. 2015).

Despite their global impacts, transport systems and the networks of
physical infrastructure that underpin them are also highly localised
(Barth’elemy 2011; Levinson 2012) and to some degree dynamic (Xie and
Levinson 2011) phenomena. This growing understanding of the fundamental
nature of transport planning as a *spatial activity*, coupled with an
upsurge in the amount of geographic transport data available, could
explain why relative levels of interest in Transport Geography has grown
over the last decade against a backdrop of low and falling levels of
interest in purely geographic concepts such as ‘geographic information
systems’ and ‘geocomputation’, at least according to data from Google
Trends. Figure 1, generated using reproducible code thanks to the
**gtrendsR** R package (Massicotte and Eddelbuettel 2019), suggests that
inferred interest in Transport Geography may surpass inferred interest
in GIS within the next few years, notwithstanding the limitations
associated with search data (Mellon 2014).

![Relative level of interest in search terms related to ‘geographic
information systems’, ‘geocomputation’ and ‘transport geography’
inferred from google search data.](google-trends.png)

The concept of integrating geographic data analysis in transport
planning is not new. … Around the turn of the century, there were
attempts to define geographic information systems for transportation
(GIS-T) as a self-standing academic field (Miller 1999), something that
has not caught on.

Where is existing infrastructure and ‘demand’ (current and potential
travel) located? How will transport patterns shift in the future? And
where will different types of intervention be most effective? Tools that
can help answer these questions are becoming an increasingly important
part of the transport planner’s cabinet (te Brömmelstroet and Bertolini
2008).

To illustrate this point, imagine fundamental changes that could be made
to tax system in support a transition away from fossil fuels.
Interventions such as carbon taxes would undoubtedly have geographic
implications, but the intervention itself (charging a fixed price for
the extraction and sale of atmosphere polluting substances) could be
essentially non-geographic. Notwithstanding changes to national policies
relating to transport, transport planning interventions, by contrast,
are inherently spatial. Even high level national plans for a walking and
cycling revolution must be implemented locally, down to the level of
streets, as illustrated by the still ongoing local implementation of
Dutch cycling ambitions (Pucher and Buehler 2008). The
political-democratic and local-geographic aspects of transport planning
can be considered in isolation, but an integrated approach is necessary
for effective policies (Hull 2008). This is well illustrated by
prominent Mayoral transport policies in cities such as London\[1\],
Paris\[2\], and Bogotá\[3\].

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
answers to these questions. 21<sup>st</sup> century demands for
transport planning cannot be delivered by 20<sup>th</sup> century
technology and, this paper will argue, open source solutions are poised
to bridge the gap between the geographic and the — historically dominant
— non-geographic aspects of transport planning. The 21<sup>st</sup>
Century also requires new transport planning methodologies which, as
this paper outlines, increasingly involves geographic analysis.
Furthermore, the policy context increasingly demands transparency and
citizen involvement in the decision-making process, which only software
that is open source and reliably deliver, making an exploration of open
source options for transport planning workflows timely.

Methods for transport planning are by no means static. They are
constantly evolving in response to policy drivers and technological
change (Boyce and Williams 2015). Of course, transport policies that are
evidence-based and grounded in realistic models of change under
different scenarios of the future are far more likely to be successful
than policies based on ideological commitment and good intentions alone.
With unprecedented access to increasingly detailed datasets on transport
behaviours and infrastructure, transport planners today can make their
designs are more evidence-based that ever, provided they have access to
tools that enable them to make sense of this ‘data revolution’
(Transport Systems Catapult 2015). The sheer volume and complexity of
new datasets suggest approaches that can scale and integrate multiple
sources are needed (Lovelace et al. 2016). Furthermore, advances in
software and hardware allow not only for current transport systems to be
modelled at high temporal and geographic resolution, but for future
scenarios and ‘model experiments’ to be developed, which can support
identification and implementation of the most effective interventions
(Klosterman 1999). With the explosion in open source software, which has
come to dominate data science, there is now also a unique opportunity
for transport planning to become a more transparent and democratically
accountable enterprise.

This dream of data driven, participatory and open transport planning has
yet to emerge. Transport planning as a discipline has been slow to adapt
to the data revolution and, while it evolves to enable a wider range of
input data sources and analysis ‘in the cloud’, the open source element
of the dream is conspicuously lacking.
<!-- This stuff could go in the introduction. --> The paper traces how
this undesirable situation has arisen due to historical specialisation
and monopolisation of transport planning software, based on existing
literature and an understanding of landscape of tools used in practice
(covered in the next section), before outlining an integrated approach
that combines data analysis and geographic processing stages in a single
workflow. Three software ecosystems (R, Python and QGIS) are reviewed in
detail; alternative current and potential future approaches, including
‘cloud lock in’ are discussed; and the relative merits of different
approaches are discussed. Building on this discussion, the paper
concludes by returning to the importance of integrating data analysis
and geographic processing in a single analysis. This final section also
outlines concrete steps that researchers, public sector transport
planners, and transport planning analysts and consultants can take to
accelerate the transition to open source software in transport planning
which will, in turn, support policies that accelerate the transition to
a healthy and zero carbon transport
system.

<!-- The paper concludes that 'integrated approach' can support efficient, scalable and reproducible transport planning workflows which can provide a strong and transparent evidence base needed for rapid transition away from fossil fuels in the transport sector. -->

# The landscape of transport planning software

The geographic and non-geographic division of labour in Transport
Planning

Data preprocessing and analysis stages are generally done in dedicated
transport planning and spreadsheet software. Geographic analysis and
cartographic visualisation stages are generally done in a dedicated
‘geographic information system’ (GIS).

# Tools for integrated geographic analysis

## R

(R Core Team 2019)

(Bivand 2006)

(Pebesma et al. 2015)

(Bivand, Pebesma, and G’omez-Rubio 2013)

## Python

(Rossum 1995)

## QGIS

(QGIS Development Team 2019)

# Conclusion

# References

<div id="refs" class="references">

<div id="ref-barthelemy_spatial_2011">

Barth’elemy, Marc. 2011. “Spatial Networks.” *Physics Reports* 499
(1–3): 1–101.

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

<div id="ref-boyce_forecasting_2015">

Boyce, David E., and Huw C. W. L. Williams. 2015. *Forecasting Urban
Travel: Past, Present and Future*. Edward Elgar Publishing.

</div>

<div id="ref-harrison_environmental_2017">

Harrison, R. M., and R. E. Hester. 2017. *Environmental Impacts of Road
Vehicles: Past, Present and Future*. Royal Society of Chemistry.

</div>

<div id="ref-hull_policy_2008">

Hull, Angela. 2008. “Policy Integration: What Will It Take to Achieve
More Sustainable Transport Solutions in Cities?” *Transport Policy*, New
Developments in Urban Transportation Planning, 15 (2): 94–103.
<https://doi.org/10.1016/j.tranpol.2007.10.004>.

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

<div id="ref-levinson_network_2012">

Levinson, David. 2012. “Network Structure and City Size.” *PloS One* 7
(1): e29721. <https://doi.org/10.1371/journal.pone.0029721>.

</div>

<div id="ref-lovelace_big_2016">

Lovelace, Robin, Mark Birkin, Philip Cross, and Martin Clarke. 2016.
“From Big Noise to Big Data: Toward the Verification of Large Data
Sets for Understanding Regional Retail Flows.” *Geographical Analysis*
48 (1): 59–81. <https://doi.org/10.1111/gean.12081>.

</div>

<div id="ref-massicotte_gtrendsr:_2019">

Massicotte, Philippe, and Dirk Eddelbuettel. 2019. *gtrendsR: Perform
and Display Google Trends Queries*.
<https://github.com/PMassicotte/gtrendsR>.

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

<div id="ref-pebesma_software_2015">

Pebesma, Edzer, Roger Bivand, Paulo Justiniano Ribeiro, and others.
2015. “Software for Spatial Statistics.” *Journal of Statistical
Software* 63 (1): 1–8.
<http://brage.bibsys.no/xmlui/bitstream/id/320781/Pebesma_Bivand_Ribeiro.pdf>.

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

<div id="ref-r_core_team_r:_2019">

R Core Team. 2019. “R: A Language and Environment for Statistical
Computing.” <https://www.R-project.org/>.

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

<div id="ref-te_brommelstroet_developing_2008">

te Brömmelstroet, Marco, and Luca Bertolini. 2008. “Developing Land Use
and Transport PSS: Meaningful Information Through a Dialogue Between
Modelers and Planners.” *Transport Policy* 15 (4): 251–59.
<https://doi.org/10.1016/j.tranpol.2008.06.001>.

</div>

<div id="ref-transport_systems_catapult_transport_2015">

Transport Systems Catapult. 2015. “The Transport Data Revolution.”
Government. Transport Systems Catapult.
<https://ts.catapult.org.uk/wp-content/uploads/2016/04/The-Transport-Data-Revolution.pdf>.

</div>

<div id="ref-world_health_organization_global_2018">

World Health Organization. 2018. *Global Status Report on Road Safety
2018*. S.l.
<https://www.who.int/violence_injury_prevention/road_safety_status/2018/en/>.

</div>

<div id="ref-xie_evolving_2011">

Xie, Feng, and David Levinson. 2011. *Evolving Transportation Networks*.
Transportation Research, Economics and Policy. New York:
Springer-Verlag. <https://www.springer.com/gp/book/9781441998033>.

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
