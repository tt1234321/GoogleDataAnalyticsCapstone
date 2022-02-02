# GoogleDataAnalyticsCapstone
Coursera Google Data Analytics Certifficate

##### This repository will contain my work for the Coursera course and capstone project of Coursera Google Data Analytics Certifficate.
Several RMD files with R code in RStudiowere uploaded, and for better readibility knits of RStudio in pdf were also duplicated.<br>
As in the course description, analytics-based scenario was chosen for this case study. The following  approach to act on the data from the scenario has been applied:ask questions, prepare, process, analyze, visualize and act . For capstone and case study please refer to [coursera course description](https://www.coursera.org/learn/google-data-analytics-capstone?specialization=google-data-analytics) and also [case study scenario](Capstone_Scenario_CaseStudy.pdf).




#### Links to the code in R (export from RStudio to pdf file): 

<img width="100" alt="image" src="https://www.rstudio.com/wp-content/uploads/2018/10/RStudio-Logo-Flat.png">

[Rstudio - Part 1. Data collection and creation of dataframe](GoogleCapstoneTT_Part1_CreateRawDataframe.pdf)

[Rstudio - Part 2. Processing data from  row data to clean data](GoogleCapstoneTT_Part2_FromRawDataToClean.pdf)

[Rstudio - Part 3. Browsing data and descriptive data analysis](GoogleCapstoneTT_Part3_FromCleanDataToAnalysis.pdf)

[Rstudio - Part 4. Basic data visualisations](GoogleCapstoneTT_Part4_DatVis.pdf)

#### Links to my work in Taubleau is published below

<img width="200" alt="image" src="https://public.tableau.com/s/sites/default/files/media/Tableau-Public-Logo-for-Intro-Blog.png">




[Tableau - Part 1. Number of trips analysis and visualisation dashboard](https://public.tableau.com/app/profile/tomasz.tomaszewski4391/viz/GoogleCapstoneNoOfTrips/DashboardNumberofTrips)

[Tableau - Part 2. Average trip duration analysis and visualisation dashboard](https://public.tableau.com/app/profile/tomasz.tomaszewski4391/viz/GoogleCapstoneAverageTrips/DashboardAverage)

[Tableau - Part 3. Most popular rental stations analysis and visualisation dashboard](https://public.tableau.com/app/profile/tomasz.tomaszewski4391/viz/GoogleCapstoneAverageTrips/DashboardAverage)


#### SQL work in Google Big Querry:

<img width="200" alt="image" src="https://www.vectorlogo.zone/logos/google_bigquery/google_bigquery-ar21.png">


Utilisation of SQL skills has been practiced in Google Big Querry platform. Since my personal account has a file upload limitations I was not able to  upload my preperad csv file with cleaned dataframe. For the exercise purpose smaller file was uploaded (monthly data only) and the work was performed on this dataset.

Querry 1
Calculate basic metrics (AVG, MIN, MAX)

SELECT AVG(tripduration) As Average, MIN(tripduration) AS Min, MAX(tripduration) AS Max FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` LIMIT 1000

Average	Min	Max
1016.3420339716529	61.0	1.06284E7


Querry 2
Calculating number of rides by user type

SELECT COUNT(usertype) AS NumberOfRides , usertype FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` GROUP BY usertype LIMIT 1000

NumberOfRides	usertype
341906	Subscriber
23163	Customer

Querry 3
Calculating number of rides and average ride for usertype "Customer"

SELECT COUNT(usertype) AS NumberOfRides , AVG(tripduration) AS AvgRide FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` WHERE usertype = "Customer" LIMIT 1000

NumberOfRides	AvgRide
23163	3715.7375987566475

![image](https://user-images.githubusercontent.com/79140709/152154053-fa4bcb03-3ee0-4b36-a6a8-5a175ee04660.png)


Querry 4
Calculating number of rides and average ride for usertype "Subscriber"

SELECT COUNT(usertype) AS NumberOfRides , AVG(tripduration) AS AvgRide FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` WHERE usertype = "Subscriber" LIMIT 1000

NumberOfRides	AvgRide
341906	833.4669178078134

![image](https://user-images.githubusercontent.com/79140709/152153938-1525f102-9e65-49ac-abce-5718000962b4.png)


Querry 5
Calculating average trip duration by gender.

SELECT gender, AVG(tripduration) As AverageTripDuration FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` GROUP BY gender LIMIT 1000

gender	AverageTripDuration
Male	840.0283148972994
	3838.052356552175
Female	918.820586389315


![image](https://user-images.githubusercontent.com/79140709/152153735-ea881492-c3df-4085-9b5e-3807e996a0fe.png)


Querry 6
Calculating 10 longest trips.

SELECT from_station_name AS station, tripduration FROM  `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` ORDER BY tripduration DESC LIMIT 10

station	tripduration
Leavitt St & North Ave	1.06284E7
Central Park Ave & Ogden Ave	6096430.0
Wentworth Ave & 63rd St	5646180.0
Wabash Ave & Cermak Rd	4859470.0
Wells St & Elm St	3926850.0
State St & Van Buren St	3406960.0
Dearborn St & Erie St	3095670.0
LaSalle Dr & Huron St (*)	2592880.0
Dearborn St & Erie St	2358950.0
Greenview Ave & Jarvis Ave	1887870.0


![image](https://user-images.githubusercontent.com/79140709/152157167-86265f43-92d6-4abe-9a93-b8caf3772400.png)


Querry 7
Calculating 10 most popular start stations.

SELECT from_station_name AS Station,COUNT(trip_id) AS NumberOfTrips FROM  `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` GROUP BY from_station_name ORDER BY NumberOfTrips DESC  LIMIT 10

Station	NumberOfTrips
Clinton St & Washington Blvd	7699
Clinton St & Madison St	6565
Canal St & Adams St	6342
Columbus Dr & Randolph St	4655
Canal St & Madison St	4571
Kingsbury St & Kinzie St	4395
Michigan Ave & Washington St	3992
Franklin St & Monroe St	3516
LaSalle St & Jackson Blvd	3252
Dearborn St & Monroe St	3246


![image](https://user-images.githubusercontent.com/79140709/152158630-4285196a-5324-443c-8b60-4b5bceb7033c.png)



#### Screenshot of Google BigQuerry workspace. Some results were saved as a tables for further analysis.


![image](https://user-images.githubusercontent.com/79140709/152158849-e8ce8b10-556d-467d-9178-6fd0cf90d7cd.png)










Number of rides by membership type

pd.read_sql('''
SELECT
member_casual,
COUNT(ride_id) AS number_of_rides
FROM MAINdivvy2
GROUP BY member_casual;
''', con=cony)
Average ride length by membership type

pd.read_sql('''
SELECT
member_casual,
ROUND(AVG(ride_length)/60,1) AS avr_ride_length_min
FROM MAINdivvy2
GROUP BY member_casual;
''', con=cony)
Number of rides by weekday, by membership type

pd.read_sql('''
SELECT
day_of_week,
member_casual,
COUNT(ride_id) AS number_of_rides
FROM MAINdivvy2
GROUP BY day_of_week, member_casual
ORDER BY member_casual, day_of_week;
''', con=cony)
Average ride duration by month, by member type

pd.read_sql('''
SELECT
STRFTIME('%m', started_at) AS month,
ROUND(AVG(ride_length/60),1) AS avg_ride_length_min,
member_casual
FROM MAINdivvy2
GROUP BY month, member_casual
ORDER BY member_casual, month;
''', con=cony)


Number of rides by membership type

pd.read_sql('''
SELECT
member_casual,
COUNT(ride_id) AS number_of_rides
FROM MAINdivvy2
GROUP BY member_casual;
''', con=cony)
Average ride length by membership type

pd.read_sql('''
SELECT
member_casual,
ROUND(AVG(ride_length)/60,1) AS avr_ride_length_min
FROM MAINdivvy2
GROUP BY member_casual;
''', con=cony)
Number of rides by weekday, by membership type

pd.read_sql('''
SELECT
day_of_week,
member_casual,
COUNT(ride_id) AS number_of_rides
FROM MAINdivvy2
GROUP BY day_of_week, member_casual
ORDER BY member_casual, day_of_week;
''', con=cony)
Average ride duration by month, by member type

pd.read_sql('''
SELECT
STRFTIME('%m', started_at) AS month,
ROUND(AVG(ride_length/60),1) AS avg_ride_length_min,
member_casual
FROM MAINdivvy2
GROUP BY month, member_casual
ORDER BY member_casual, month;
''', con=cony)

