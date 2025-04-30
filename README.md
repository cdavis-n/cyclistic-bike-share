# Cyclistic Bike-Share Data Analysis

## 1. Introduction 
This is a case study for the Google Data Analyst Certification on Coursera. 
In this case study, I worked for a fictional company, Cyclistic, along with some key team members. 

### 1.1 Scenario
I am a junior data analyst working on the marketing analyst team at Cyclistic, a bike-share
company in Chicago. 
The director of marketing believes the company’s future success
depends on maximizing the number of annual memberships. Therefore, my team wants to understand 
**_how casual riders and annual members use Cyclistic bikes differently_**.
From these insights, my team will design a new marketing strategy to convert casual riders into annual
members. But first, Cyclistic executives must approve your recommendations, so they must be
backed up with compelling data insights and professional data visualizations. 

### 1.2 About the Company
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown
to a fleet of 5,824 bicycles that are geo tracked and locked into a network of 692 stations across
Chicago. The bikes can be unlocked from one station and returned to any other station in the
system anytime. Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to
broad consumer segments.
##### Pricing Plans & Memberships
  There are 3 types of plans: Single-ride passes, Full-day passes, and Annual memberships.
  * Member = Annual memberships
  * Casual = Single-ride passes or/and Full-day passes

## 2. Problems
Cyclistic wants to increase the profit. Cyclistic’s nance analysts have concluded that annual members are much more profitable
than casual riders. Although the pricing flexibility helps Cyclistic attract more customers,
the director of marketing believes that maximizing the number of annual members will be key to future growth.
Rather than creating a marketing campaign that targets all-new customers, she believes
there is a solid opportunity to convert casual riders into members. She notes that casual riders
are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Business Task: **_Design marketing strategies aimed at converting casual riders into
annual members_**

In order to do it, I needed to better understand:
  * How annual members and casual riders use Cyclistic bikes differently
  * Why casual riders would buy Cyclistic annual memberships
  * How Cyclistic can use digital media to influence casual riders to become members


## 3. Process 
In the analysis process, I used free version of BigQuery and Tableau. Therefore, there are limitations of features that I can use. 
### 3.1 Data Collection
In this case study, 2 kinds of public data are used. The Range of the time is from March 2024 to February 2025.
  * Cyclistic users' trip data from DIVVY
  * Weather data from visualcrossing
12 CSV files of Trip data and a CSV file of weather data were used. 

### 3.2 Data Cleaning 
##### 1. Clean data in Excel
   * _Error 1: Lots of station locations are uncertain due to the rounnded up latitude and longitude._<br>
      Some data can be fixed since the combination of rounded numbers of latitude and longitude are unique. However, most of them are uncertain and cannot define the station location.
      Although it is ideal that I remove the data for analysis, the amount of data that missing information of station's location is too much. Therefore, instead of removing the whole data from dataset, I decided to not using station location data for my analysis.
      If the data is accurate, I could have analyzed about the trend of location users use the service. IN this case study, I changed approaches to find out the trend. 
       
           
   * _Error 2: Trip length are zero or less than 1 minute._<br>
     Share-bike service usually charges the certain cost per minute meaning it would be non-profitable record.
     If location where user started and ended the service is not changed, then user might try to use it but somehow the bike is not used. Or bike geo tracking system would be broken.
     Either way, these irregular cases should not be included for the analysis. 
     
##### 2. Combine 12 months of data into 1 dataset in BigQuery
   Initial plan was cleaning the data in excel, making 1 dataset using insert and calculate the length of ride time in BigQuery.
   However, due to the limitation of features in free version of BigQuery, I cannot use the insert seature in BigQuery. 
   Moreover, there is maximum size that I can handle the data in BigQuery, so I handle minimum data that I need to use for analysis.

###### Cleaned Data looks like:   



#####

### 3.5 Data Analysis 
#### Trip Count by User 
##### Data
##### Method
##### Analysis

### 3.4 Data Visualization
![Overview](https://github.com/user-attachments/assets/f539e9f0-4a35-4c38-9f0d-83afacc9ab70)

### 3.6 Presenting the Data


## 4. Solutions


## 5. Conclusion


## 6. Next Steps 



