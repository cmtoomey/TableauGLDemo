# TableauGL
This is a demo for using MapboxGL-derived styles in Tableau.

## Data Source
The data is pulled from the New York Times article *[N.C.A.A. Fan Map: How the Country Roots for College Football] (http://www.nytimes.com/interactive/2014/10/03/upshot/ncaa-football-fan-map.html)*

Stadium data comes from [here](https://www.google.com/maps/d/viewer?mid=z0P46k1OiKCw.kEuLSq0_6Uy4&hl=en_US)

## Mapbox Base Map 
Using Alteryx, I created a workflow to identify the #1 school for each ZIP code, and any zip codes with ties.
Using [this](https://docs.google.com/spreadsheets/d/1altTSFs8LWMh0OdYBoC8-yNEXq6eIYz2rk6kn3DLobw/edit#gid=0), I mapped Hex Codes to each school and added those as attributes to each school.
ZIP Codes were downloaded from [US Census Bureau](https://www.census.gov/geo/maps-data/data/cbf/cbf_zcta.html) and joined with the NYT, stadium and attribute data.

Once ZIP-level data was finalized, I created a merged shape for each team. This is effectively the *Fan Universe* for each school. I then calculated the center of each shape, to represent the **Center of the Universe** for each school. Alteryx then calculated the approximate area for each shape, as well as the distance between the **Center of the Universe** and each stadium.

All that data was then pushed into a Tableau Data Extract for visualization.

The final MapboxGL style can be found [here](https://api.mapbox.com/styles/v1/cmtoomey/cihcghyuc00bo4llza6mxm2um.html?title=true&access_token=pk.eyJ1IjoiY210b29tZXkiLCJhIjoiUWQyeTJqMCJ9.MFgvZXmgNt6WzrzP9kJgUA#0/0/0/0)

## Tableau Workbook
The basic idea of the workbook is to a) show where the fanbases are and how they are distributed; b) show how far the center of the fan universe is from the center of the football universe (in miles); c) show how much area is consumed by each fan base; d) let users search by State and ZIP to see the dominant teams, as well as the other teams that are popular and how popular they actually are relative to the most popular team. 
