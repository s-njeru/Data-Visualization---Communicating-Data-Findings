# Ford GoBike Dataset Exploration Title
## by Stella Njeru


## Dataset
The dataset I will be analyzing is from Ford GoBike System. It contains information on a bike sharing system in the San Francisco Bay area. This dataset has 183412 rows and 16 columns.

Features in this dataset are:

- duration_sec: trip duration in seconds             
- start_time: trip start time               
- end_ti
me: trip end time                 
- start_station_id: id of station the trip started         
- start_station_name: name of location the trip started       
- start_station_latitude: start station latitude   
- start_station_longitude: start station longitude    
- end_station_id: id of station the trip ended            
- end_station_name: name of location the trip ended          
- end_station_latitude: end station latitude       
- end_station_longitude: end station longitude      
- bike_id: identification no assigned to the bike hired                  
- user_type: type of user('subscriber' is a member of the biking service; 'customer' is a casual user of the biking service)        - member_birth_year: when member was born        
- member_gender: member gender            
- bike_share_for_all_trip: was trip a bike share

Before starting my exploration, I took the data wrangling steps below in preparation for my exploratory analysis.

1. There was 8265 missing data in the member_birth_year and member_gender columns and 197 missing values in the start_station_id, start_station_name, end_station_id and end_station_name. The missing data is < 5% of the 183412 records thus statistically insignificant and was dropped.
2. Incorrect data types on 8 columns: start_station_id, end_station_id, bike_id, user_type, member_gender, bike_share_for_all_trip, start_time, end_time. These will be corrected with the astype and to_datetime functions. The id columns were formatted to string. user_type, member_gender and bike_share_for_all_trip were formatted to category datatype. start_time and end_time were formatted to datetime columns.
3. 3 derived columns were created from start_time column. Hour of day, day of week and whether the day was a weekend or weekday.
4. User Age was derived from member_birth_year by finding the difference between the year the data was collected(2019) and member_birth_year and stored as an integer.
5. Trip duration in minutes was derived from duration_sec column by division by 60.
6. Unwanted columns were dropped: duration_sec, member_birth_year, start_time, end_time, start_station_latitude, start_station_longitude, end_station_latitude, end_station_longitude using drop function

## Summary of Findings

The questions I asked in this dataset are as listed below

###  Questions
#### Univariate Exploration
1.	Is this service used more by subscribers than customers?
2.	Which gender took more trips?
3.	Did users of the Ford GoBike system use the bike share option often?
4.	What hours of the day have the most trips?
5.	What days of the week have the most trips?
6.	What is the age distribution of our users in the month of February 2019?
7.	From the dataset, how long did the trips last?

#### Bivariate Exploration
8.	Is there an existing linear relationship between a user age and the trip duration?
9.	Do the different user types make most of their trips on different times of the day?
10.	Does the user type behaviour vary on weekends compared to weekdays?
11.	What is the relationship between the categorical variables and member age?
12.	What is the relationship between the categorical variables and trip duration?
13.	What is the average trip duration on different days of the week?
14.	What is the average trip duration on different times of the day?
15.	For the trips made between 2am and 3.59am, do both user types depict such behaviour throughout the week?

#### Multivariate Exploration
16.	Does the average trip duration vary with user type throughout the day?
17.	How does the average trip duration vary with gender across the week?
18.	How different a behaviour do both user types have hourly throughout the week?



### Findings
#### Univariate Findings
1.	90.53% of users in the San Francisco Bay Area are subscribers while 9.47% are casual customers
2.	There are more males than females who made trips. We have 74.59% males, 23.32% females and 2.08 'other' gender.
3.	Most users did not use the bike share option for their trips.
4.	Majority of the tips are seen to be taken between the 0700Hrs and 0959Hrs, and in the evening, between 1600Hrs to 1859Hrs. Most trips are taken immediately before and after working/school hours. The trips taken during working hours are seen to be around a constant value(7500) and those after 1859Hrs gradually decrease.
5.	Most trips were made on Thursday and Tuesday, with weekdays having more trips than weekends. Seeing as a lot of trips were made during commute hours to and from work, this distribution on day of week adds up.
6.	User age distribution with is skewed to the right. Majority of the users approximately fall between 24 to 40 yrs. old.
7.	The trip distribution with a log transform better shows the distribution of trip duration. It is skewed to the right as well, with majority of the trips seen between 5 - 18 minutes. Most users ride these bicycles for a short duration, with 97.6% of the rides being 35 minutes or less. A normal distribution is observed between 0 and approximately 75 mins

#### Bivariate Findings
8.	From the age distribution we had earlier, most users are aged between 24 and 40 years. From this scatterplot, we see that longer trip durations are taken by people who are 60 and below. Members older than 60 years take shorter trips. However, there is no linear relationship between the 2 variables even with a log transform.
9.	Both user types are seen to mostly use the bike share service when people ideally commute to and from work.
10.	Both user types display the same behaviour on weekdays and weekends. On weekdays, most trips are made around work-home commute hours. On weekends, majority of the trips are taken between 1000Hrs and 1859Hrs. Most trips are taken by subscribers of the service in comparison to casual customers.
11.	On average:
    •	Majority of customers and subscribers fall around the same age group.
    •	While the majority age based on gender is around the same value, the older bike riders appear to be males.
    •	Majority of users that used the bike share for their entire trip appear to be younger than those that did not use bike share.
    •	Majority of users on weekends (especially Sunday) are younger compared to weekdays.
12.	 On average:
    •	Casual risers have longer trips than customers
    •	Male riders typically have shorter trips than female riders evident by a lower mean in male trips as well as a shorter inter quartile range.
    •	Bike sharing trips run for a shorter duration than non-bike-share rides.
    •	Weekend trips are typically longer that weekday trips.
13.	Trip durations are shorter on weekday than on weekends. From earlier investigation, we saw that trips on weekdays are mostly taken during typical work/school-home commute hours. On weekends, trips are longer showing usage could be for leisure purposes.
14.	There seems to be unexpected behaviour between 0200Hrs and 0359Hrs in the morning. The average trip duration is significantly higher than it is throughout the day.
15.	The rides that are taking place between 0200Hrs and 0359Hrs, are primarily from subscribers on Friday, Saturday and Sunday, but both user types have a significant increase in usage within the 2 hours from Friday to Sunday.  

#### Multivariate Findings
16.	Earlier, we saw that subscribers take more trips than casual customers. From this view, however, it is evident that casual customers take longer trips on average compared to subscribers, especially on weekends.
17.	Member gender categorized as 'Other' is seen to go on longer rides on average. Females take longer trips than males and less than 'Other'.
18.	Subscribers primarily use the biking service on weekdays between 0700Hrs to 0959Hrs in the morning and between 1600 Hrs and 1859Hrs.  On weekends, heavier usage is seen between 1000Hrs to 1759Hrs. Customers on the other hand, are seen to have heavy usage in the same hours as subscribers on weekdays but tend to use the service more in between the commute hours to and from work. On weekends, they have are seen to use the service a lot between 1000Hrs and 1659Hrs. From user behaviour, demand is highest on Thursday at around 1700Hrs.


## Key Insights for Presentation

For the presentation, my focus is on trip duration, busiest hours on different days, and user behavior. I chose these because after the exploratory phase of the analysis, these aspects stood out. The busiest hours throughout the day showed when demand was highest and coupling this with user behavior across different days showed that these were the key featutes to understanding the dataset. 

I start out visualizing user behavior on different hours of the day to understand their usage of the bike service on weekdays and weekends by use of faceted line plots.I then proceed to looking at the trend of average duration of the trips throughout the week. This is followed by a deeper dive into the average trip duration throughout the day to identify exceptions from the understanding created up to this point. This will then inform the best time to perform maintenance on the service, visualized by a countplot on hourly trip distribution. Finally, I compare user behavior on diferent hours on the days of the week to see whether people that subscribe to the service have different trip habits compared to casual customers using a heatmap.

