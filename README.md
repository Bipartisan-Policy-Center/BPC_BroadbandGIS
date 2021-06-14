# Resources for Broadband Mapping project

## [M-lab data](https://www.measurementlab.net/visualizations/)
Mlab is an online, open-source speed test which publishes their data to Google
BigQuery - it is maintained by `Code for Science and Society`. This data is 
aggregated over a number of speed tests performed by users themselves and are 
pretty likely to suffer from some sampling bias, not to mention some relatively
sparse data in rural areas where density is lower. Additionally we might see
some issues arise from non-Broadband related bottlenecks (routers, clients, etc).

Still, at some point, it might be worth spatially joining this over some areas of
interest to see what kinds of discrepancies exist (especially if we are unable
to find an FCC dataset that has contractual speeds instead of advertised speeds).

## [FCC Form 477 data](https://www.fcc.gov/general/explanation-broadband-deployment-data)
This is data of form 477 submissions by ISP's with fields for census blockgroup, 
advertised up and downspeed, and type of service. According to the explanation 
page, contractual up and downspeed should be present but is not! That's a real 
shame since both are likely to be inflated, but contractual is likely to be much
closer to the real thing. 

These data are reported December and June - June 2019 data are the last time 
contractual up and downspeed were reported. Since this is relatively recent, we
can use this for analysis purposes, with the hope that internal docs can be updated
when/if the Biden FCC starts reporting contractual speed again (fingers crossed).

## [Microsoft Broadband Usage Percentages](https://github.com/microsoft/USBroadbandUsagePercentages)
Interesting project from Microsoft comparing actual downspeed/upspeed from 
anonymized microsoft devices, aggregated to the county level. Obviously this 
is just windows devices, but probably a more representative dataset than M-lab.
Since this is aggregated at county level, we wouldn't need a fancy spatial join,
we could join these together using the first 5 digits of the census GEOID. 

## [Census block shapefiles](https://www.census.gov/cgi-bin/geo/shapefiles/index.php?year=2020&layergroup=Blocks+%282020%29)
Only available in state by state chunks. Sure would be convenient to get all of the
US in one fell swoop but it seems we can only get that down to blockgroup. In any
case, if we could get all the data in state chunks, we can have a congressional 
area or county or other GEOID input which will fetch the proper FCC data, join
against the proper TIGER data, join the proper census/acs data, all of which will
(hopefully) be less computationally intense than doing it nationally. 

## [Understanding GEOIDs](https://www.census.gov/programs-surveys/geography/guidance/geo-identifiers.html#:~:text=GEOIDs%20are%20numeric%20codes%20that,area%20has%20a%20unique%20GEOID.)
Documentation for how to read 12-digit GEOIDS.

## [TIGER shapefile documentation](https://www2.census.gov/geo/pdfs/maps-data/data/tiger/tgrshp2020/TGRSHP2020_TechDoc.pdf)
Description of TIGER shapefile columns and methodology. Brief description of 
columns:
[ColumnDescriptions]!(img/reference/TigerCols.png)