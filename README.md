# East Coast v West Coast Airbnb Analysis

# Table of Contents:
1. [Project Overview](#project-overview)
2. [Results](#results)
3. [Summary](#summary)

# Project Overview
This project aims to explore listing data from Airbnb's [Boston](https://www.kaggle.com/datasets/airbnb/boston) and [Seattle](https://www.kaggle.com/datasets/airbnb/seattle), provided by [Kaggle](https://www.kaggle.com/), to determine the following questions:

 1. What month is the best to travel? 
 2. Is there much variance between neighborhoods? Or coasts?
 3. What factors determine the price of an airbnb?

We will use Boston to represent the east coast and Seattle, the west. The data is far from thorough enough, but we will use it to provide some insight into the questions that we have laid out. To determine the third question we will utilize supervised machine learning to evaluate what the most important factors in pricing are. 


# Results

## Important Disclosures

The datasets that were utilized both span the course of 12 months, though the Boston data cover September 2016 through August 2017. Information from Seattle's January and Boston's September should be observed with some skepticism. 

## Data Preprocessing 

After downloading the datasets from Kaggle we imported the review, calendar, and listing csvs into our Jupyter Notebook. While the dataset was rich in information, most of it would be unnecessary for our project. While other columns needed to be processed in order to extract useful information, e.g., the date related columns needed to be coverted using datetime and strptime while the 'available' column needed to be converted from t/f to binary. This processes had to be repeated for each dataset. 

After processing the information we were ready to create our visualizations to answer our questions. First, we wanted to figure out what was the best time to travel. In order to answer this question it was decided that availability rate of Airbnbs were inversely related to the best, and least crowded, time to travel. Here we see that units are easily available throughout the year in both Seattle and Boston, with some swell in the summer months. 

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/number_of_listings.PNG" width="300">

Next we wanted to check if there was any difference in price throughout the year. From the charts here we can see that the average price of an Airbnb increases with the summer swell in both Seattle and Boston. In Boston, we are also able to observe a sharp decrease in availability and an increase in price from April to October. 

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/average_price.PNG" width="300">

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/availability_rate.PNG" width="300">

Looking at the top 5 highest per night price we see a trend: near water and the city.

#### Seattle

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/seattle_top_5.PNG" width="300">

#### Boston

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/boston_top_5.PNG" width="300">

The cheapest 5 are much less decentralized, but follow a trend of being outside the city and far from water. 

#### Seattle

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/seattle_bottom_5.PNG" width="300">

#### Boston

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/boston_bottom_5.PNG" width="300">

Next, we wanted to know if there was much variation between neighborhoods within each airbnb market. Similar to the first question, we had to clean up our data in order to extract important information from it. We selected the following columns: 'review_scores_value','accommodates', 'bathrooms', 'bedrooms', 'beds', 'cancellation_policy', "id" 'host_is_superhost', 'extra_people', 'property_type', 'room_type', 'price', 'neighbourhood_cleansed' and created a new dataframe for each market as well as standardizing the pricing data. 

What we learned was that there was great variation between the prices of airbnb listings
TODO

## Compiling, Training, and Evaluating the Model

For our third question we wanted to know to what affect does certain factors affect pricing in Airbnbs (e.g., review scores, extra people, number of (beds, bathrooms), or even if the host is a superhost). To accomplish this we needed to create a learning model that would evaluate this for us. After creating a heatmap to see the strength of relationship between certain variables. We are able to see that 'review scores value' share the weakest relationship with the rest of the variables, and was thus dropped, while 'accommodates', 'bathrooms', 'bedrooms', and 'beds' share the strongest relationship with the price.

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/boston_heatmap.PNG" width="300">

We decided to move forward with the random forest regressor to sample our data. From our results we were able to determine that the leading factor in either market was the number of bedrooms and bathroom. 

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/training.PNG" width="300">

<img src="https://github.com/nguyenauloi/final_project/blob/main/resources/imgs/seattle_importances.PNG" width="300">

## Under Construction

Future additions to this project will be the following:
 - Using BeautifulSoup to scrape from websites like Kayak
 - Store data in PostgreSQL & AWS
 - Create website/app that would calculate the price  of your trip based on future airline data and historical Airbnb prices at the click of a button

# Summary

It seems redundant, but the best value comes from renting airbnb during the winter months and to rent away from metropolises. This seems to stay consistent across different markets (cities).

[Tableau Link](https://public.tableau.com/views/final_project_16715086367700/Story2?:language=en-US&:display_count=n&:origin=viz_share_link)
