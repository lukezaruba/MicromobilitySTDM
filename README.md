# MicromobilitySTDM

# Spatiotemporal Data Mining of Micromobility Data in Minneapolis
### Final Project for GEOG 5543: Advanced Geocomputing
##### Luke Zaruba
###### December 14, 2022

<i>Micromobility has been a recent interest of transportation planners and urban residents alike. The most common implementation of micromobility in Minneapolis has been through motorized scooters from companies like Lime (Uber), Bird, or Lyft. There are comprehensive datasets available containing trip information for all scooters within the City, but using the data for understanding travel patterns and user behaviors have largely remained untouched. The data could have immense value to planners, residents, and other stakeholders, to inform future decision-making and more adequately prepare for how the urban landscape will change to accommodate greater volumes of scooters and other forms of micromobility. My solution is to use the powerful techniques of spatial data science to uncover these patterns and understand how users currently use the scooters.</i>

The ETL process for this analysis was fairly straighforward, consisting of: loading datasets into DataFrames/GeoDataFrames, casting to different data types, filtering out unnecessary data and columns, and geometry transformations. After the initial cleaning of the data, the nonspatial trips dataset is then jioned to the spatial centerlines dataset. This allows us to associate coordinates with each origin and destination. The final step is some additional cleaning that occurs on the joined DataFrame.
   
DBSCAN, or Density-Based Spatial Clustering of Applications with Noise, is a clustering algorithm that \"finds core samples of high density and expands clusters from them\" ([scikit-learn](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.DBSCAN.html), 2022). The primary reason that this model was selected to perform spatiotemporal data mining in this context was due to its ability to classify noise, which other clustering algorithms like K-Means, do not do. The model's implementation was simple, as can be seen by the code, of which only three lines are actually reaquired at a bare minimum. For more information on DBSCAN, scikit-learn offers a [guide](https://scikit-learn.org/stable/modules/clustering.html#dbscan) that breaks down the basics of DBSCAN and other clustering algorithms, as well.

Data visualization is of the utmost importance when exploring spatial data, but when the temporal dimension is added, things can get complicated quite easily. There are a multitude of options for different techniques to visualize spatiotemporal data, but ultimately there are not a ton of options within Python, making this an area that I would deem to be an important area of focus for the geospatial open-source development community. Although there are plenty of options to visualize spatial data, and a larger amount that can visualixe multimdimensional data quite well, when these two are combined together the options are limited.

With this is mind, I decided to display the data a few differnt ways, as described below.
1. Plotly 3D Scatterplot
2. Matplotlib 3D Line Plot
3. Matplotlib (& Contextily) Static 2D Cluster Map
4. Seaborn Animated Time Series KDEPlot

Each of these plot types has their own pros and cons, but ultimately there is no existing package in Python that combines the best parts of each of these plots.

In the future, I think there several ways that visualization could be improved, which are listed below.
1. Integration with Uber's H3
2. Using Voxels (like Esri's Space-Time Cube)
3. Animated Flow Maps
4. Animated Vector Fields
5. 3D Scatter/Line Plots with Geospatial Context (like Plotly with geospatial context embedded within it)
    
Additionally, here are some exciting projects that are making progess in the field of spatiotemporal visualization.
- [VASA](https://github.com/move-ucsb/VASA)
- [DynamoVis](https://github.com/move-ucsb/DynamoVis)
- [MovingPandas](https://github.com/anitagraser/movingpandas)
- [TransBigData](https://github.com/ni1o1/transbigdata)
- [scikit-mobility](https://github.com/scikit-mobility/scikit-mobility)
- [FlowMapper](https://flowmapper.org)
- [kepler.gl](https://docs.kepler.gl)
