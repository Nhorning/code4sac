# Code for Sacramento - Neighborhood Portal Project
![Sac311](https://github.com/walteryu/code4sac/blob/master/sac311/images/sac311_logo.png)

### City of Sacramento - 311 Service Call Analysis
Code for Sacramento is develop a neighborhood portal application; as a result, this notebook evaluates the City of Sacramento 311 service call dataset for insights and trends which may be helpful in developing useful features. This notebook will focus on an initial analysis and identifying potential issues related to users and their neighborhoods.  

### Conjecture  
Per discussion with City of Sacramento staff, 311 service calls are a relatively stable source for identify potential issues/needs of neighborhoods. Included are time and location data which will be useful for identifying trends.  

### Findings  
1. Conventional statistical and machine learning methods were not a good fit for analyzing service call data due to its highly categorial nature; almost all variables were categorical with exception of time/location data.  
2. Exploratory data analysis and logistic regression were used to confirm this finding; spatial analysis was used to yield better results.  
3. Clustering and density plots were developed in the GeoDa software application to identify natural concentrations of service calls by zipcode.  

### Dataset
311 service call dataset from City of Sacramento; summary statistics for the full and partial datasets are listed below. The data is available in geospatial, tabular or API format; the tabular format is used for this analysis to identify important neighborhoods and trends which are relevant to developing the application.  

* [311 Service Call Dataset](https://data.cityofsacramento.org/datasets/08794a6695b3483f889e9bef122517e9_0)

### Installation
1. Notebook is written in R markdown, so be sure that R Studio is installed then clone this repository.
2. Load notebook in R Studio, run/download dependencies.
3. For spatial analysis, download and start the GeoDa [spatial analysis tool](https://geodacenter.github.io/download.html) which was developed by the University of Chicago [Spatial Data Science Program](https://spatial.uchicago.edu/).

### Methodology
1. Exploratory data analysis (EDA) and model fits showed that spatial and temporal analysis would be more appropriate methods of analysis.
2. As a result, spatial analysis with R and GeoDa were used to identify trends.
3. Findings are documented within the notebook; additional analysis was completed in GeoDa.

### Citations
1. Spatial Data Science with R [textbook](https://rspatial.org/)
2. GeoDa Spatial Analysis [software](https://geodacenter.github.io/index.html)
3. HES CSCI E-63c [course material](https://www.extension.harvard.edu/course-catalog/courses/elements-of-data-science-and-statistical-learning-with-r/15123)
4. ISLR [textbook](https://www-bcf.usc.edu/~gareth/ISL/)
5. ESLR [textbook](https://web.stanford.edu/~hastie/ElemStatLearn/)

### Spatial Analysis - Scatterplot and Clustering
[GeoDa](https://geodacenter.github.io/) is a GUI-based tool which allows users to complete spatial analysis without coding in R or Python. As a result, it is a good analysis tool to create reproducible work with a minimal barrier to entry for the audience. Software installation can be completed on their website (see citations) without executable programs for each major OS.  

Initial plot was completed using a scatterplot of 5k service locations on a basemap as shown below; service calls (shown in green) are clustered in the downtown and Pocket neighborhood areas with smaller clusters in other neighborhoods:

**Figure 1 - Scatterplot of 311 Service Calls (5k Records in Green)**
![5k_plot](https://github.com/walteryu/code4sac/blob/master/sac311/images/sac311_5k_plot.png)

Next, a [KNN cluster](https://en.wikipedia.org/wiki/K-means_clustering) plot was created based on zipcode and confirmed the initial clustering identified in the scatterplot. Again, larger clusters of calls (shown in shades of blue/green) were observed within the downtown and Pocket neighborhood areas:

**Figure 2 - KNN Cluster Plot of 311 Service Calls (5k Records in Blue/Green)**
![5k_zip_kmeans](https://github.com/walteryu/code4sac/blob/master/sac311/images/sac311_5k_zip_kmeans.png)

Finally, a [Jenks natural breaks optimization](https://en.wikipedia.org/wiki/Jenks_natural_breaks_optimization) plot was created based on zipcode and confirmed the initial clustering identified in the scatterplot. Again, larger clusters of calls (shown in shades of orange/brown) were observed within the downtown, Pocket and Natomas neighborhood areas:

**Figure 3 - Natural Breaks Plot of 311 Service Calls (5k Records in Orange/Brown)**
![5k_zip_kmeans](https://github.com/walteryu/code4sac/blob/master/sac311/images/sac311_5k_zip_breaks.png)

### Spatial Analysis - Unique Values
Additional spatial analysis was completed based on unique values to identify additional trends; specifically, a unique values plot was created based on the first category of service calls which consists of the main categories of calls. The plot density is high and does not show a district pattern; however, the legend reveals that the data distribution is dominated by solid waste/trash/dumping (~4k records) followed by water (~200 records) and animal care (~200 records):

**Figure 4 - Unique Values Plot of 311 Service Calls (5k Records by First Category)**
![5k_zip_kmeans](https://github.com/walteryu/code4sac/blob/master/sac311/images/sac311_5k_cat1_unique.png)

Another unique values plot was created based on the second category of service calls which the subcategories of calls. The plot density is high and does not show a district pattern; however, the legend reveals that the data distribution is dominated by undefined values (~2k records) followed by several solid waste-related categories (~200 records per category):

**Figure 5 - Unique Values Plot of 311 Service Calls (5k Records by Second Category)**
![5k_zip_kmeans](https://github.com/walteryu/code4sac/blob/master/sac311/images/sac311_5k_cat2_unique.png)

### Recommendations
The objective of this study was to identify trends for developing useful features into the Portal application; as a result the follow recommendations are provided based on results of statistical and spatial analysis:

1. Service Call Clusters - Service calls were grouped into the downtown, Pocket and Natomas neighborhoods; as a result, these areas are recommended as focus areas to organize neighborhoods followed by the other groups observed in the spatial analysis plots.
2. Service Call Categories - Solid waste, trash and dumping-related calls were the majority of calls; as a result, this should be an areas of focus for communities when providing them support of their issues.
