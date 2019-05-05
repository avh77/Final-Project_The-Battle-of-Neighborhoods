# Final-Project_The-Battle-of-Neighborhoods
What we can do when the nearest pharmacy is miles away? Sometimes it is vital to buy pills or drugs as soon as possible for anyone of us. For example, in case of bronchitis or diabetes, it is a question of life or death.
The entrepreneurs are also interested in the answer to the following question: “Where a new pharmacy may be opened?” The answer is a part of a pharmacy`s business plan. 
In this project I discover Canadian town Edmonton, Alberta. The town is characterized by large area and population and, subsequently low density of the population. Fortunately, the city create Web source “Open data portal”. The source contains all the census data of Edmonton I need for the research. The data will be imported from official source https://data.edmonton.ca/.
Pharmacies data will be imported via API from the Web source https://developer.foursquare.com/.  The source gives the full details about a venue including location, tips, and categories.
The imported data includes the numbers and the names of Neighborhoods, as well as quantity of population divided by age groups. It is interesting question: is there some correlation between percentage of age groups of local population and income of a local pharmacy, or by another words, who is more often buy medicaments – youth, middle age with children or the elderly? The answer at that question can founded using internal information of a pharmacy retail chain. This question can be decided for a particular drug store as part of its business plan. This is beyond the project.
There are no any information about the geographical position of the Neighborhoods. This information can be found at the same source from the other file. As the result I received the table that contains all the data about Neighborhoods in Edmonton. It includes Neighborhood`s names, inhabitants, coordinates, area. Some cells do not contain coordinates, this cells doe not contain information about population as well. When I saturated myself in a subject, I founded up that such neighborhoods are industrial, subsequently they are useless for the project. I cut them out of the table. Finaly, I received the DataFrame that contains all necessary information for estimation of distribution of inhabitants over the Edmonton area. The DataFrame has been visualized on the map of the town. 

At the map we can see blue bubbles of different size. The bubbles size similar to quantity of habitants in neighborhoods. As we can see, there is extremely high population density in the center of the city. The south, the south-west and the west are also have high level of population density. The north and the north-east inhabited evenly. The east and the north-west are almost deserted.
The next step of the discovery is acquisition and discovering of data about quantity and distribution of pharmacies in the city. For that purpose have been chosen Web-service https://developer.foursquare.com. The service gives to a developer wide range of possibilities to work with API data as well as to receive a venue information of a chosen category. In this research the following categories is used: Pharmacy, Apothecary, Drugstore as well as city molls (all the city molls contains a shop that sales drugs). A request has a limitation of maximum number of results. To overcome constraints it is possible to divide the town into few areas, and make request for every of them. Therefore a table of pharmacies have been received.
The table contains columns with excessive information for the research. This columns have been deleted (fig.6).
The pharmacies are visualized on the map of the city, green bubbles.
At the next step of the research the minimum distance between every neighborhood and a nearest pharmacy have been founded. The method geopy.distance is used for this purpose. As the result the DataFrame that contains distance from every neighborhood to every pharmacy was received. At the next step the minimum distance to the nearest pharmacy was founded and converted to meters. Finally, neighborhoods with distance to a nearest pharmacy less than 2500 meters (half an hour walk distance) were removed from the table. The remaining 74 neighborhoods have distance to a nearest pharmacy ranged from 2 536 to 8 858 meters.
The remote neighborhoods are visualized on the map of the city. The neighborhoods distributed in the north, the south-east and the west of Edmonton mostly.
The next question is the determination of quantity of needed pharmacies. It is obvious, that the quantity most has a proportion similar to existing quantity pharmacies serving nearest neighborhoods. This number of needed pharmacies is calculated and is 10.875.  As we can see, it should be opened 11 (10.875 rounded to nearest) new pharmacies. 
The next problem is to find coordinates of the new pharmacies. The good idea is to use K-Means Clustering for that purpose. The initialization method of the centroids k-means++ was used. The number of time the k-means algorithm run with different centroid seeds was 10, that is enough for this project. 
Finally, the table with coordinates of new pharmacies was received. The coordinates are the approximate positions where new pharmacies would be accessible for the population of remote neighborhoods. The new pharmacies are visualized on the map of the city (fig.9).
Note: if founded coordinates are match with an existing building, another closest place should be reviewed.

Reference indexes
-	International Pharmaceutical Federation – FIP (2017). Pharmacy at a glance – 2015-2017. The Hague, The Netherlands: International Pharmaceutical Federation
-	https://data.edmonton.ca/
-	https://developer.foursquare.com/ 
-	https://github.com/
-	https://pandas.pydata.org/
-	https://www.ibm.com/ 
