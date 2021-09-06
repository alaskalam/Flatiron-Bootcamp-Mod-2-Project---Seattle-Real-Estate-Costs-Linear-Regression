## Introduction
There are many factors that can affect a house's price, including the square footage, the location, and even the value of the surrounding properties. What we wanted to do was come up with a model that could reliably predict the price of a property, given a list of its characteristics. Since each home doesn't exist in a vacuum, its very likely that the price is affected by the combination and interaction of different features.

We used the King's County housing dataset from May 2014 to May 2015 and as such, this model can only be considered valid for this particular dataset. 

## Methodology

### The Dataset
We used the Kings County housing dataset from May 2014 to May 2015 which contains the following datapoints.
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

We added a distance form shoreline metrix by creating a map of the coastline and used the latitude and longitude measurements to calculate the distance from the coastline for each property. 

### Exploring the Data

Looking at the dataset, we are given pricing, geographical data, size of the property, the condition and the grade of the property. Preliminary analysis of the data seems to suggest that the location of the property is one of the strongest indicators for pricing, we're going to start and looking at what exactly is important about the location.

![Avg%20sale%20price.png](attachment:Avg%20sale%20price.png)










