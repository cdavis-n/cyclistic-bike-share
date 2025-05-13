# Cyclistic Bike-Share Data Analysis

## 1. Introduction 
This is a case study for the Google Data Analyst Certification on Coursera. 
In this case study, I worked for a fictional company, Cyclistic, along with some key team members. 

### 1.1 Scenario
I am a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, my team wants to understand  **_How casual riders and annual members use Cyclistic bikes differently_**.
From these insights, my team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations. 

### 1.2 About the Company
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geo tracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments.
##### Pricing Plans & Memberships
  There are 3 types of plans: Single-ride passes, Full-day passes, and Annual memberships.
  * Member = Annual membership
  * Casual = Single-ride passes or/and Full-day passes

## 2. Problems
Cyclistic wants to increase the profit. Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, the director of marketing believes that maximizing the number of annual members will be key to future growth.
Rather than creating a marketing campaign that targets all-new customers, she believes there is a solid opportunity to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Business Task: **_Design marketing strategies aimed at converting casual riders into
annual members_**

In order to do it, I needed to better understand:
  * How annual members and casual riders use Cyclistic bikes differently
  * Why casual riders would buy Cyclistic annual memberships
  * How Cyclistic can use digital media to influence casual riders to become members


## 3. Solutions
In the analysis process, I used free version of BigQuery and Tableau. Therefore, there are limitations of features that I can use. 
### 3.1 Data Collection
In this case study, two kinds of public data are used for analysis. The Range of the time is from March 2024 to February 2025.
  * Cyclistic users' trip data from DIVVY
  * Weather data from visualcrossing

12 CSV files of Trip data and a CSV file of weather data were analyzed. 

### 3.2 Data Cleaning 
##### 1. Clean data in Excel
   * _Error 1: Lots of station locations are uncertain due to the rounded-up latitude and longitude._ <br>
     Some data can be fixed in this process since the combination of rounded numbers of latitude and longitude are unique. However, most of them are uncertain and cannot define the station location. Although it is ideal that I remove the data for analysis, the amount of data that missing information of station's location is too much. Therefore, instead of removing the whole data from the dataset, I decided to not use the station locations’ data for my analysis. If the data is accurate, I could have analyzed the trend of location users use the service. In this case study, I changed approaches to find out the trend. 
       
           
   * _Error 2: Trip lengths are zero or less than 1 minute._ <br>
     The share-bike service usually charges a certain cost per minute meaning it would be a non-profitable record. If the location where user started and ended the service is not changed, then user might try to use it but somehow the bike is not used. Or the bike geo tracking system would have issues. Either way, these irregular cases should not be considered for the analysis. 
     
##### 2. Combine 12 months of data into one dataset in BigQuery
   Initially the plan was to clean the data in Excel, and make one dataset using insert and calculate the length of ride time in BigQuery. However, due to the limitation of features in the free version of BigQuery, I cannot use the insert feature in BigQuery. Moreover, there is maximum size that I can manage the data in BigQuery, so I handle minimum data that I need to use for analysis.

###### Combine all data into one in BigQuery: 
```sql
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_03` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_04` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_05` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_06` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_07` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_08` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_09` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_10` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_11` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2024_12` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2025_01` 
UNION ALL
SELECT  * 
FROM `mystic-span-430219-u1.bike_share.2025_02` 
```

###### Combined data looks like:   
![image](https://github.com/user-attachments/assets/de686411-b335-4ea5-b33c-8b6befac5907)


After importing the combined data into Tableau, the length of riding time are calculated using the calculated field. 

### 3.3 Data Analysis 
###### Users
Member's number of trips is larger than the casual users' count. However, the Casual users' lengths of trip time are slightly longer than annual members. From this data, I can say that Casual users don't use it a lot, but they tend to use the service longer than members when they use the bike-share service. Members tend to use the service regularly for fleeting time of period of trip time. Members could be more likely to use for commuting.

###### Ride Types 
Members use both classic bikes and electric bikes pretty much evenly. The usage of electric bikes (52.6%) is slightly larger than classic bikes (45.7%). This could be because they tend to use the share-bike service regularly and electric bikes are more likely to ride with less physical energy loss. Casual users use both classic bikes and electric bikes at the same level as well. The difference between casual user and Member is the trip time. Although there is not significant difference between classic bikes and electric bikes in both trip time and trip count for member, casual users tend to use classic bikes longer than electric bikes. From this data, casual users could use the bike-share service for fun such as exploring the town or exercising.
 
###### Different Time
The ride time in winter is way shorter than other seasons. Members tend to stably use the bike-share service except during winter. From May to September, casual users use the bike-share service longer than members.
Both users' peak season, month and time for the ride time are the same: summer, September, and 5 pm. On the other hand, the peak of day for Casual users is Saturday although members use the service on the Wednesday at the most.

###### Weather
From the data, I would say that windspeed would not relate to the length of bike-share service users have. However, temperature seems relate with the duration of the service they get for Casual users. From 70°F to 80°F, more Casual users used the bike share service. 
Also, weather conditions are related to the bike-share service, especially casual users. In sunny/cloudy conditions, larger trips count and longer average trip time for casual users. In the case of member, when the temperature is above 50°F, in any whether condition, they use the bikeshare service stably.


### 3.4 Data Visualization
Click for Tableau dashboard here:  [Cyclistic bike-share Dashboard](https://public.tableau.com/views/Cyclisticbike-share_17440532096660/Overview?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


![Overview](https://github.com/user-attachments/assets/f539e9f0-4a35-4c38-9f0d-83afacc9ab70)

## 4. Conclusion
Based on my research, I have identified that annual members, and casual members use the bike-share service for different purposes. My analysis shows that annual members tend to use the service regularly and stably with short ride time each time compared with casual members; the purpose of using Cyclistic bike-share service would be more likely for commuting. This is because their average ride time and count didn't change a lot yearly regardless of weather conditions. On the other hand, it seems that casual members tend to use the service for recreation since the usage of the bike-share service and their ride time depend on the weather condition and time. 
Since annual members tend to use the service regularly, it would be good if the marketing team focused on promoting people who commute to facilities near the dock stations such as University students or workers. 
Also, casual riders would buy Cyclistic annual membership if they can find the advantage of purchasing it even though they would not use it more likely only on weekends and in warm weather. For example, annual members don't need to pay unlock fee when they unlock the bikes from dock and don't need to pay the cost for the first one hour. I will need further research into whether those services will make a profit communicating with Cyclistic’s finance analysts and knowing how much cost company needs to pay to maintain a bike. If these features can make profit, then they can be used as promotion to casual members.

## 5. Next Steps 
My recommendations are: 
* Promoting Cyclistic bike-share service targeting students and their parents, and people working at facilities near the dock stations
* Further research on the potential profit from the annual members' benefit such as free unlock fee and the first hour



