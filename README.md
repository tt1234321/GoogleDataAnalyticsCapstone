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

Querry 4
Calculating number of rides and average ride for usertype "Subscriber"

SELECT COUNT(usertype) AS NumberOfRides , AVG(tripduration) AS AvgRide FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` WHERE usertype = "Subscriber" LIMIT 1000

NumberOfRides	AvgRide
341906	833.4669178078134

Querry 5
Calculating average trip duration by gender.

SELECT gender, AVG(tripduration) As AverageTripDuration FROM `adroit-minutia-329609.GoogleCapstone.Trips2019Q1_example` GROUP BY gender LIMIT 1000

![image](https://user-images.githubusercontent.com/79140709/152153735-ea881492-c3df-4085-9b5e-3807e996a0fe.png)



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

