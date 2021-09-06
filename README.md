## Introduction
There are many factors that can affect a house's price, including the square footage, the location, and even the value of the surrounding properties.  The purpose of this project is to come up with a model that could reliably predict the price of a property, given a list of its characteristics. Since each home doesn't exist in a vacuum, its very likely that the price is affected by the combination and interaction of different features.

The King's County housing dataset from May 2014 to May 2015 was used for modeling and as such, this model can only be considered valid for this particular dataset. 

## Methodology

### The Dataset
The Kings County housing dataset from May 2014 to May 2015 contains the following datapoints.
* **id** - unique identified for a house
* **dateDate** - house was sold
* **pricePrice** -  is prediction target
* **bedroomsNumber** -  of Bedrooms/House
* **bathroomsNumber** -  of bathrooms/bedrooms
* **sqft_livingsquare** -  footage of the home
* **sqft_lotsquare** -  footage of the lot
* **floorsTotal** -  floors (levels) in house
* **waterfront** - House which has a view to a waterfront
* **view** - Has been viewed
* **condition** - How good the condition is ( Overall )
* **grade** - overall grade given to the housing unit, based on King County grading system
* **sqft_above** - square footage of house apart from basement
* **sqft_basement** - square footage of the basement
* **yr_built** - Built Year
* **yr_renovated** - Year when house was renovated
* **zipcode** - zip
* **lat** - Latitude coordinate
* **long** - Longitude coordinate
* **sqft_living15** - The square footage of interior housing living space for the nearest 15 neighbors
* **sqft_lot15** - The square footage of the land lots of the nearest 15 neighbors

A new feature was also added to the dataset; distance form shoreline metric was calcualted via the Haversine function using coastline coordiantes, obtianed by geojson files, with property coordinates. 

### Exploring the Data

Looking at the dataset, the features given are given pricing, geographical data, size of the property, the condition and the grade of the property. Preliminary analysis of the data seems to suggest that the location of the property is one of the strongest indicators for pricing, an investigation is performed to identify what is important about the location.
![image.png](img_01.png)

Since this housing market is close to a body of water, the analysis will look at the relationship between the distance from the shoreline and the price. The scatterplot below plots the relationship seen in the heatmap previously, that there is an increase in price for properties the closer they are to the shoreline.

![image.png](img_02.png)

Next, properties that have the waterfront label will be investigated.  This means that not only are they close to the water, but they are also facing the water as well. Waterfront facing properties on average have a higher value than their non-waterfront facing neighbors. 
![image.png](img_03.png)

As the size of the property increases, so to does the value of the property. This relationship is supported in both waterfont and non-waterfront properties. 

![image.png](img_04.png)

## The Model

The following features were selected for our model because of their importance to model performance 
![image.png](img_05.png)

The housing market analysis was split into two different models, one group for houses over one million, and one group for houses under one million.  These two categories of housing criteria would have clients with different needs.  One looking for a property for under one million, will typically have standard features, while someone looking to sepnd over a million on a house may require custom built finishes or higher quality finishes yeidling in elevated prices.

Feature binning was performed on the grades and the distance from the coast. Grade was grouped into three groups: less than 7, between 7 and 8, and greater than 8. Distance from coast was grouped as those within a quarter of a mile of the coast, and those that are not. 

### Under One Million
The R-Squared and Adjusted R-Squared values are .934 and .933.

The coefficients all have significant p values.
As age, square footage or grade, increase, so too does the value.
Waterfront facing or renovated properties have a higher value than each of their counterparts.
Properties that are further than .25 miles away from a shoreline have a lower value than those that are closer.

![image.png](img_06.png)

The QQ plot is very linear, with very minor deviation at the tails. 

![image.png](img_07.png)

### Over One Million
The model for homes over one million has an almost identical relationship as the model for the homes under one million, with the difference being in the values of the coefficients and the R-Squared values. 

The R-Squared and Adjusted R-Squared values are .924 and .923.
![image.png](img_08.png)

The QQ plot for these homes is not as linear as the one for homes under one million, however the deviation is largely concentrated at the tails. This does suggest that there might be some outliers that weren't removed or accounted for in this model. 
![image.png](img_09.png)

## Conclusions

#### 1) Waterfront Properties have High Value
The highest valued properties are those that are facing the waterfront. If a waterfront property is desired, expect to pay a higher price for the luxury of the waterfront.

#### 2) Properties Close to the Coast Have Higher Value
Related to waterfront properties are those that are closer to the coast, but aren't necessarily facing the water itself. These properties are also highly valued, resulting in the areas immediately surrounding a shoreline to have a higher value than would be normally expected.

#### 3) The Grade Matters
The grade of the home has a significant effect on the value of the home, and those looking to sell their home for a higher value should seek out ways to increase the grade of their home. 

## Future Work
Future work for this project would include looking more in detail with the geographical data, such as looking at the distance from major highways, cities, or airports. Also consider lookoing at crime statistics for each of the neighborhoods to asses the impact on pricing values. 

Finally, looking at population statistics for each of the neighborhoods would also be interesting. How would the population densities affect the price and if that could be used as an approximation for demand?







