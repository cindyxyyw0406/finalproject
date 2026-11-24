# BST260 Final Project Proposal

Dear BST260 Teaching Team, Fall 2026,

I plan to write two vignettes using CDC datasets introduced in BST260
and distributed with my `finalproject` package. The first compares
typical outbreak size with the burden of the largest outbreaks. The
second examines whether the jurisdictions with the highest current
homicide death rates also experienced the largest recent increases.

## Vignette 1 — Outbreak size in drinking water and treated recreational water

**Research question.** Among reported waterborne outbreaks, which
exposure group has larger typical outbreaks, and in which group do the
largest outbreaks account for a greater share of reported illnesses?

I will use `waterborne`, the package snapshot of records from the [CDC
National Outbreak Reporting
System](https://data.cdc.gov/api/v3/views/5xkq-dg7x/query.json). I will
convert the list to an outbreak-level table, keep records with water as
the primary transmission mode, and compare outbreaks labeled exclusively
as drinking water or treated recreational water. I will convert reported
illness counts to numbers and document exclusions for mixed exposure
categories and missing or invalid counts.

For each exposure group, I will report the number of outbreaks, the
median and interquartile range of illnesses per outbreak, and the 90th
percentile. I will also rank outbreaks by illness count and divide the
combined illnesses in the largest 10% of outbreaks, rounded up to a
whole outbreak, by the total reported illnesses in that group. A boxplot
with a log scale for positive counts will show how the distributions
differ, and I will report any zeros separately. These summaries capture
different features of the data. A group can have a smaller median
outbreak and still have more of its reported illnesses concentrated in a
few large outbreaks.

Differences in detection and reporting may affect which outbreaks appear
in the data. The comparison describes reported outbreaks, and the
dataset lacks the exposed population counts needed to estimate
individual illness risk.

## Vignette 2 — High homicide death rates and large increases across jurisdictions

**Research question.** How much do the ten jurisdictions with the
highest age-adjusted homicide death rates in 2024 overlap with the ten
that experienced the largest increases from 2019 to 2024?

I will use `cdcmurd`, the package snapshot of the [CDC/NCHS homicide
mortality
tables](https://www.cdc.gov/nchs/state-stats/deaths/homicide.html),
which includes the 50 states and Washington, D.C. I will check for
duplicate jurisdiction-year records and missing rates, pair each
jurisdiction’s 2019 and 2024 observations, and calculate the change in
deaths per 100,000 as the 2024 rate minus the 2019 rate.

I will summarize the distributions of the 2024 rates and the paired
changes with medians and interquartile ranges. I will compare the two
top-ten lists, include ties at either cutoff, and report the overlap. A
labeled scatterplot of 2024 rate against change since 2019 will show
jurisdictions that stand out on one or both measures. For selected
jurisdictions that appear in only one group, I will plot annual rates
from 2019 through 2024 to show whether the endpoint comparison reflects
a sustained rise, a temporary spike, or a high rate that was already
present in 2019.

I will report death counts alongside rates for highlighted jurisdictions
because rates based on few deaths can fluctuate substantially. The
analysis will describe changes over time without attributing them to a
particular policy or event.

Both vignettes will document the data sources and cleaning decisions and
present their findings and limitations on my pkgdown site.

## AI use

I used ChatGPT to assess whether my proposed analyses were feasible.

**Vignette 1 — Waterborne outbreaks**

- What would it mean if one exposure group had a lower median number of
  illnesses per reported outbreak but a higher share of illnesses
  attributable to its largest 10% of outbreaks?
- If one exposure group has far fewer reported outbreaks, how sensitive
  is the top-10% illness share to rounding up and to a single unusually
  large outbreak? What simple sensitivity check could I report?
- How should I summarize the records excluded for mixed exposure
  categories or for missing or invalid illness counts? What can the
  pattern of exclusions tell me about how to interpret the comparison?

**Vignette 2 — Homicide death rates across jurisdictions**

- If I include all ties at the cutoff for either top-ten list, how
  should I report the size of each group and the number of jurisdictions
  in both?
- Could comparing only 2019 and 2024 make a temporary spike look like a
  sustained increase? How could I use annual rates to show the
  difference for selected jurisdictions?
- How should I present death counts alongside age-adjusted rates when a
  jurisdiction ranks high but has few deaths? What caveat should I give
  when interpreting its rank or rate change?
