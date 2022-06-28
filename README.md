# Usability and Trade-offs of German-Public-Transport
## Background
This project deals with the Analysis of the trade-offs that consumers in Germany face when choosing between using public transport, often referred to ÖPNV in Germany, and choosing to use their own car.
The last decade has seen an enhanced emphasis on promoting ÖPNV (Public Transport) as a step towards reducing the carbon footprint associated with the transportation sector. However, at the level of the individual consumer using ÖPNV as opposed to a personal vehicle, comes with some concrete challenges:


1. The inflexibility associated with depending on ÖPNV, especially at night.

2. The higher costs associated with long-distance ÖPNV travel.

3. Unpredictable delays, especially in long-distance ÖPNV travel.

4. Longer travel time associated with ÖPNV within the city/town.

5. Relative inaccessibility of destinations that do not lie within the city boundaries with ÖPNV.  

In this Application, we are trying to quantify  the problem arising out of longer travel while using public transit in the different states of Germany. I have completed analysis for 4 states so far. Collarborators are welcome to work on the other states of Germany so that we can cover the whole of the country.




## Methodology

The calculation of the ÖPNV time penalty proceeds in three steps
1. Sampling of locations within the city/town.
2. Estimation of travel time between these locations for the two modes of transport.i.e when driving and when using ÖPNV (Public Transit)
3. Aggregating the  differences in travel time to arrive at the average of time penalty in minutes

### Step 1
The points of interest for our analysis at the level of the town/city are individual post-boxes. In Post-boxes are generally located near population centers. Thus, we use the location of post-boxes as a easy proxy for population density. The coordinates of the individual post boxes are acquired from the Open Street maps API (OSM). OSM is also our source of all shape files used for the final visualization.
We use one fourth of the post_boxes of the town/Gemeinde as our points of interest. This is because the number of API calls increase in a quadratic fashion.

### Step 2
The travel time between our post-boxes are acquired from the Bing-Maps API service. The travel times are estimated for 11 AM on a weekday (between March and April on 2022). To ensure comparability between the different states ( an ongoing project) ,  the data acquisition for this step is always done for the specific time (11 AM on a weekday). This is not the most elegant solution. This is driven by the constraint imposed the usage of Bing Maps. The estimation of travel time using Public transit is possible only at the current local time. We hope that Bing Maps would add a feature for estimating travel time at a particular time point for public transit as well.
### Step 3
The difference between the travel time for driving and public transport gives us the travel time penalty (in minutes) for a particular route. The Travel time penalty for the whole city/town is then the average over all the routes.

## Visualization
The visulization is created using the Python packages Folium and Geopandas.
The map can be viewed at this [Here](https://sites.google.com/view/ipss2022-kangkan/applications).
Below is a screenshot of the map that would be produced by the generated HTML.
<img width="828" alt="Github_screeshot" src="https://user-images.githubusercontent.com/10926018/176172245-09391daa-3a4b-4463-a969-0eda50c8cfc4.png">

