# Predicting the Best airbnb Listing Price 

_Author: Evonne Tham_

---
![](https://assets.bwbx.io/images/users/iqjWHBFdfxIU/iKAhd1KFQDfw/v0/-1x-1.jpg)


## Executive Summary

Airbnb is a online marketplace company that offers arrangement for lodging, homestays, or tourism experiences. It has become the world’s largest marketplaces with many travelers from all around the world, using it for the unique and authentic experience. As of 2020, Airbnb has over 7 million listings across the world, all powered by local hosts.

By sharing with travelers, this provides opportunity for homeowners to make more income from their homes. However with the constant increase of listings, hosts or even property managers are now face with a lot more competitors. Hence, getting the right listing price is crucial. If listing price is set too low, you will be missing out on a lot of potential income, and if listing price is set a tad bit higher you might lose a booking to other competitors. 

<br>
<br>

![title](./image/airbnb_site.png)

_Image Source: Airbnb Site_

<br>
<br>


Although Airbnb itself has a tool called the Smart Pricing, it generalises way too much and Hosts ended up earning way lesser because Airbnb’s best interest is to book a listing as much as possible rather than not at all. This means they will lower your prices. On top of that there are third party pricing tools (e.g. AirDNA, alltherooms, Guesty) that are available to help price these properties, but these tools can get quite pricey especially for people who are just starting out. 

In order to solve this problem, the data (detail can be found below) from Toyko, one of the most popular cities for Airbnb booking experiences was utilized. Through cleaning and analysizing, regression models such as Linear Regression, Elastic Net, Support Vector Machine and XGBoost, were built to predict the best price of the listing in Toyko with respect to featurees such as the property or room type, location, amenities etc. Model performance is be guided by R-Square and RMSE, and the model should at least improve upon baseline by 10%, where baseline is defined as the mean of the listing price.

Through data cleaning, Exploratory Data Analysis (EDA), feature engineering and hyperparameter turning, XGBoost was found to be the best model with a $R^2$ score of 0.8 and a $RMSE$ score of 9759.15. In other word, the model account for 80% of the variance in the target variable with an average error of 9759.15¥ in terms of predicting the listing's price. The top features that has the most influence on the price of a listing are Room type - Entire home/apt, minimum night, cleaning fee, the distance away from city center (Tokyo), and how many listing does a hosts has. 

___Citation:___
- https://airhostacademy.com/airbnb-smart-pricing/
- https://news.airbnb.com/about-us/
- https://news.airbnb.com/fast-facts/
- https://ipropertymanagement.com/research/airbnb-statistics


---
## Content
- [Initial Exploratory Data Analysis and Cleaning](./codes/01_Data_Cleaning_and_EDA.ipynb)
- [Full Exploratory Data Analysis](./codes/02_Full_EDA.ipynb)
- [Feature Engineering and Model Benchmarks](./codes/03_Feature_Engineering_and_Model_Benchmarks.ipynb)
- [Model Tuning](./codes/04_Model_Tuning.ipynb)
- [Production Model](./codes/05_Production_Model.ipynb)

---
## Risks & Assumptions

- The data is not tempered and it accurate in producing a non-commercial derivation to allow public analysis, discussion and community benefit. 
- Some reviews may be "spam" allowed by Airbnb. Analysis suggests that spam reviews are small and do not affect the statistics.
- The Airbnb calendar for a listing does not differentiate between a booked night vs an unavailable night, therefore these bookings have been counted as "unavailable". This serves to understate the Availability metric because popular listings will be "booked" rather than being "blacked out" by a host.

---
### Data Source

Source of data of airbnb in Tokyo, Kantō, Japan, can be found on the InsideAirbnb site, [here](http://insideairbnb.com/get-the-data.html). 
It is sourced from publicly from the Airbnb site.

Within the country dataset 

**Target variable:** Price

**And some of the features are:** 

- `calendar`: Provide detail about booking for the next year, containing 7 attributes:
    - `date` (datetime)
    - `available` (categorical)
    - `price` (numeric)
    - `adjusted_price` (numeric)
    - `minimum_nights` (numeric)
    - `maximum_nights` (numeric)
    
    
- `listing`: Detailed Tokyo listings data containing 106 attributes of each listing. Some of them used in analysis are:
    - `price` (numeric)
    - `property_type`(categorical)
    - `room_type`(categorical)
    - `neighbourhood`(categorical)
    - `amenities`(text)
    - `review_scores`(categorical)
    - `accommodates`(categorical)
    - `host_is_superhost`(boolean)



- `reviews`: Detailed reviews given by guests, containing 6 attributes
    - `listing_id` (numeric)
    - `date` (datetime)
    - `comment`(text)


- `neighbourhood`: Neighbourhood list for geo filter. Sourced from city or open source GIS files.

---
## Recommendation For Future Analysis
In order to improve the model in the future, further analysis in other aspects could be done. Firstly people tend to favor aesthetically pleasing photos, which is one of the most prominent feature that most of the Airbnb Hosts rely on. Hence image analysis can come into play to analyse the quality of the photo.

Secondly NLP, analysis can be utilized on features like the description that Hosts themselves provided and reviews that were left by guests after their stay as these consist tons of information such as the distance away from metro, bars or convenient store nearby which can be extracted. 

Thirdly a more sophisticated geoanalysis could also be done here, where on top of the existing distance from the city center that was done in this project, further analysis on the distance from other important landmarks such as the National Mall or other locations where major tourist events happens can be done.

Lastly, we can look further into how to optimize revenue through the analyse the number of bookings within a particular year. Because best listing price do not equal more revenue. 