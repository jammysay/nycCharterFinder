# nycCharterFinder
## Map of NYC charter school campuses

**2026–27 school year · November 4, 2026 snapshot · Partial campus coverage**

[Open the zoomable map on GitHub](nyc-charter-schools.geojson). Select a pin to see the campus names at that location. Campuses sharing a mapped location appear under one pin.

The map represents **all 286 operating NYC charter schools** in NYSED's October 20 roster. It includes **418 campus records** in the working roster across **384 pins**. 

Note: some schools have multiple campus locations, and some locations house multiple schools - this accounts for the discrepancy between the number of schools, campuses and pins.

| Borough | Mapped campus records | Pins |
| --- | ---: | ---: |
| Bronx | 145 | 133 |
| Brooklyn | 133 | 126 |
| Manhattan | 80 | 71 |
| Queens | 50 | 46 |
| Staten Island | 10 | 8 |
| **Total** | **418** | **384** |

### Data sources

- [NYSED October 20, 2026 operating roster](https://www.nysed.gov/sites/default/files/programs/charter-schools/allchartersissued102026.pdf) establishes school scope and state identifiers. The NYC roster contains a total of 286 charter schools Open with Students in School Year 2026-27 (190 SUNY, 60 Regents, and 36 NYC DOE charters).
- [NYC Charter School Finder](https://findnyccharterschools.org/) supplied the live campus listings. The capture enumerated 421 unique listing IDs over 38 borough result pages, using a repeat Bronx pass to reconcile pagination overlap. Three listings were samples. The [Charter Center Data Hub](https://nyccharterschools.org/data-hub/) supplied 415 campus records. The Finder's embedded export provided an older building-code crosswalk.
- [NYC Public Schools LCGMS](https://infohub.nyced.org/in-our-schools/operations/lcgms) supplied the November 4 school and building identifiers. The [reconciliation log](rosters/reconciliation.csv) records the evidence used for aliases, moves, closures, and unresolved records.
- [NYC GeoSearch](https://geosearch.planninglabs.nyc/docs/) supplied address points where available. The [campus roster](rosters/campuses.csv) records the source for each coordinate, including documented alternatives. The Williamsburg high school point is from [OpenStreetMap](https://www.openstreetmap.org/copyright) and its address was corroborated by SUNY. Borough checks use [NYC Planning borough boundaries](https://data.cityofnewyork.us/City-Government/Borough-Boundaries/gthc-hcne/data). Marble Hill uses its legal borough, Manhattan, and retains Bronx mailing addresses.

### Validation

[Read the machine-readable eval results](rosters/eval-results.json) or run `python3 validate.py --report` from the repository root. Run `python3 validate.py` for the strict complete-release gate. No third-party Python packages are required.

| Check | Result |
| --- | --- |
| School coverage | 286/286 operating NYSED school IDs, with counts reconciled by authorizer |
| Finder capture and audit | All 421 unique listing IDs accounted for |
| Campus coverage | 418/418 working roster entries mapped, with zero unexpected or duplicate records |
| Address and borough | Each mapped point matches its reference coordinates and falls inside its legal borough |
| Shared sites | 418 records across 384 unique coordinates |
| Negative controls | All six detected, including missing school, missing campus, closed school, duplicate, wrong school, and wrong borough |
| Complete-release gate | Failed pending resolution of campus discrepancies |
| GitHub preview | Pending authenticated upload and preview check |


The campus count is provisional because **41 source discrepancies** remain open. A discrepancy is a source record that needs adjudication and does not necessarily represent a missing campus. Filter the [reconciliation log](rosters/reconciliation.csv) to `decision=unresolved` for the named campus records and evidence that still need review.
