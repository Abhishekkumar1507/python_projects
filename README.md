## **Case Study: Cyclistic-Bike-Share-Analysis**

### **Scenario**
You are a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations.

### **About the Company**
In 2016, Cyclistic launched a successful bike-share offering. Since then, the program has grown to a fleet of 5,824 bicycles that are geo-tracked and locked into a network of 692 stations across Chicago. The bikes can be unlocked from one station and returned to any other station in the system anytime.

The project follows the six step data analysis process: **ask, prepare, process, analyze, share, and act**.

### **Ask an Effective Question** 
Three questions will guide the future marketing program:
 1. How do annual members and casual riders use Cyclistic bikes differently? 
 2. why would casual riders buy Cyclistic annual memberships?
 3. How can Cyclistic use digital media to influence casual riders to become members?
        
The director of marketing has assigned you the first question to answer: 
**How do annual members and casual riders use Cyclistic bikes differently?**

**Summary of Business Task**

The goal of this case study is to identify how do annual members and casual riders use Cyclistic bikes differently.
This comparison along with other tasks will later be used by marketing department for developing strategies aimed at converting casual riders into members.

**Stakeholders:**

Primary stakeholders: The director of marketing and Cyclistic executive team
Secondary stakeholders: Cyclistic marketing analytics team

### **Data Preparation**

The data that we will be using is Cyclistic’s historical trip data from last 12 months (Year 2021). The data has been made available by Motivate International Inc. on this [link](https://divvy-tripdata.s3.amazonaws.com/index.html) under this [license](https://www.divvybikes.com/data-license-agreement).

The dataset consists of 12 CSV files (each for a month) with 13 columns and more than 5 million rows.

ROCCC approach is used to determine the credibility of the data

-   **R**eliable – It is complete and accurate and it represents all bike rides taken in the city of Chicago for the selected duration of our analysis.
-   **O**riginal - The data is made available by Motivate International Inc. which operates the city of Chicago’s Divvy bicycle sharing service which is powered by Lyft.
-   **C**omprehensive - the data includes all information about ride details including starting time, ending time, station name, station ID, type of membership and many more.
-   **C**urrent – It is up-to-date as it includes data until end of May 2021
-   **C**ited - The data is cited and is available under Data License Agreement.

**Data Limitation**

A quick filtering and checking data for completeness shows that “start station name and ID” and “end station name and ID” for some rides are missing. Further observations suggest that the most missing data about “start station name” belongs to “electric bikes” as 201,975 out of 888,490 electric ride shares have missing data and it accounts for 22% of total electric-bike ride shares.

This limitation could slightly affect our analysis for finding stations where most electric-bikes are taken but we can use “end station names” to locate our customers and this can be used for further analysis and potential marketing campaigns.

### **Data Process**

Before we start analyzing, it is necessary to make sure data is clean, free of error and in the right format.
### **Tasks:**

 **1. Tools:** Python Programming is used for its ability to handle huge datasets efficiently.

 **importing the python libraries**
  import numpy as np
  import pandas as pd

**2. Organize**: Combined all 12 datasets into one.

Reading the csv dataset :
* jan_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q1_01.csv")
* feb_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q1_02.csv")
* mar_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q1_03.csv")
* apr_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q2_04.csv")
* may_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q2_05.csv")
* jun_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q2_06.csv")
* jul_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q3_07.csv")
* aug_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q3_08.csv")
* sep_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q3_09.csv")
* oct_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q4_10.csv")
* nov_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q4_11.csv")
* dec_2021 = pd.read_csv(r".\Divvy_Trips_2021\Divvy_Trips_2021_Q4_12.csv")


Concatenating Dataframes into single Dataframe :
dataset = [jan_2021, feb_2021, mar_2021, apr_2021, may_2021, jun_2021,jul_2021, aug_2021, sep_2021, oct_2021, nov_2021, dec_2021]
dataset = pd.concat(dataset)

**3. Sampling**: Due to limitation in computational power and efficiency purposes, I had to take a random sample without replacement out of 4,073,561 observations. Sample size is calculated as follow:
 - Population size: 5,595,063
 - Confidence level: 99.99%
 - Margin of Error: 0.01
 - Sample size: 37,577

       df.sample(n=37577,replace=False)


**4. Preparing for analysis**

- Added column called “ride_length and calculated the length of each ride
- Added new columns to calculate the following for each ride.
	- Date
	- Year
	- Month
	- Day
	- Day of the week
 - These columns provide additional opportunities to aggregate the data.

**5. Check data for errors**: A quick sorting and filtering shows that, there is a negative difference between two time periods (started_at and ended_at) which logically isn’t possible.
	Removed the rows where trip duration is negative.

**6. Clean column names and checked for duplicate records in rows.**

## **Data Analyze**
Performed data aggregation using Python Programming.

Further analysis were carried out to perform calculations, identify trends and relationships using PivotTable and grouping data.

## **Share Insights**
Matplotlib is used for data visualization and presenting key insights.

## **Act on Recommendation**
After analizing, we reached to the following conclusion:

- Casual riders take less number of rides but for longer durations.
- Casual Riders are most active on weekends, and the months of June and July.
- Casual riders mostly use bikes for recreational purposes.

Here are my top 3 recommendations based on above key findings:
1. Design riding packages by keeping recreational activities, weekend contests, and summer events in mind and offer special discounts and coupons on such events to encourage casual riders get annual membership.
2. Design seasonal packages, It allows flexibility and encourages casual riders to get membership for specific periods if they are not willing to pay for annual subscription.
3. Effective and efficient promotions by targeting casual riders at the busiest times and stations:
	- Days: Weekends
	- Months: February, June, and July
	- Stations: Streeter Dr & Grand Ave, Lake Shore Dr & Monroe St, Millennium Park


***Thanks for reading!***

