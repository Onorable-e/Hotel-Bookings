![Hotel booking](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/0c8f487a-a892-4a6f-bf4e-aef73e29f3df) 

This is a guided project in my data analytics (Power BI) class with [Datafied Academy](https://github.com/Datafyde) - Data Heroes Cohort. <br>

# Problem Statement 
In the dynamic hospitality industry, data-driven decision-making has become an indispensable tool for optimising operations and enhancing customer satisfaction. In this context, there is a need to analyse the dataset to unravel insights that will show patterns, trends, and factors influencing booking behaviours. This analysis is essential to discern the complexity of customer preferences, streamline operational processes and ultimately enhance overall service delivery.

# Dataset Overview 
The dataset contains various aspects of hotel bookings collected over 3 years (2018 - 2020), ranging from booking details to guest demographics. Each entry contains essential information like the Average Daily Rate (ADR), number of guests, booking agency, arrival details, room assignments, and more. 

Data Source: [Hotel Dataset](https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand/data)

# Project Objective 
The project's objective was to help optimise business operations through data-driven insights by analysing the booking records and creating dashboard(s) that provide valuable insights. The dashboard should contain insightful charts, graphs, and tables to convey information effectively, thereby enabling informed decision-making on optimising operations. 

# Business Questions and Metrics
We defined specific business questions that should be answered. Examples of questions include: <br>
- Who are the people booking? <br>
- Which of our customers are cancelling their bookings? <br>
- Where do we have the most bookings? <br>
- Out of the total bookings, how many were successful and unsuccessful? <br>

# Key Performance Indicators (KPIs)
We also defined metrics and KPIs that will help answer the business questions. Examples include: <br>
- Total booking <br>
- Total cancellation/cancellation rate <br>
- Successful booking: Total booking where the reservation status is checked out. Unsuccessful booking: Total booking where the reservation status is cancelled or no show. <br>

# Data Inspection
We inspected the dataset so as to understand the data, detect errors and inconsistencies such as differences in data formats and data types. The following insights were obtained after inspecting the data: 

- Shape of dataset: The dataset has 32 columns for each year and several rows.<br>
- The data set contains over 3000 missing values in the agent column and over 20000 in the company columns. <br>
- The dataset contains duplicates. <br>
- Outliers were noticed in the previous cancellation column. <br> 
- The data does not look consistent. For example, the lead time which is the number of days that elapsed between the entering date of the booking into the PMS and the arrival date had some values that were not within reasonable range. Also, columns; is_repeated_guest, previous_cancellations, and previous_bookings_not_canceled are inconsistent. <br>
- The data types for some of the columns are not consistent with the data types that they contain. <br>

The data inspection helped to identify areas to focus on when cleaning the data.

# Data Cleaning 
From our data inspection, errors and inconsistencies were addressed. For example, the columns with the wrong data types/formats were converted to the right ones.<br>
Some other steps taken during the data cleaning are as follows:   
- The different tables representing each year (2018 - 2020) were merged as a new table and renamed "Hotel Bookings". <br>
- Duplicates were removed: a new column (check duplicates) was created with the values from all the columns. Then the duplicates were removed from the column (check duplicates). <br>
- An arrival date column was created by merging the day, month, and year of arrival date. <br>
- The values 1 and 0 in the is_cancelled column were replaced with "Cancelled" and "Not Cancelled" respectively. <br>
- The values 1 and 0 in the is_repeat_guest column were replaced with "Repeat guest" and "New guest" respectively. <br>
- The NULL in the agent and company columns were replaced with an empty string. <br>
- The year, month name, day, and week of the year were extracted from the reservation_status_date column. <br>

### Dataset after cleaning
![After data cleaning](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/fb179a38-fea4-4c2c-aa15-ee15326c0fce)

# Data Modelling and Relationships
Dimension tables were created to enable users to slice and dice data and even drill down into hierarchies and generate insightful reports based on the defined relationships in the model.<br>

The following dimension tables were created:

### Location Dimension Table
- The location dataset was sourced from [statistic time](https://statisticstimes.com/geography/countries-by-continents.php).<br>
- The following columns were extracted from the data; Code, Country name, Region, and Continent.<br>
- The country name column was inspected for null value by filtering.
  
### Hotel Dimension Table 
The hotel dimension table was created from the merged dataset named "Hotel Bookings". The following steps were taken in creating this dimension:
- The data (Hotel Bookings) was duplicated. <br>
- All the transformation steps that came with the dataset were removed. <br>
- All the columns were removed except the hotel column. <br>
- All the duplicates from the hotel column were removed leaving just distinct values. <br>
- An ID column was created by using 'column from example' on the add column tab. <br>

NB: The ID for the resort hotel is 'HT01' while that for the city hotel is 'HT02'.

### Date Dimension Table
The date table was created from the 'Arrival_date' column using DAX and it consists of the year, month name, day, and week number. 

### Relationships
A star schema was designed leading to a one-to-many relationship between the fact table and the dimension tables.  

![Data modelling and relationship](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/53bf7370-89cb-40e2-b776-1d6115b122a5)

# Visuals and Charts
The metrics and insights were represented using appropriate chart formats (e.g., donut chart, map, and bar charts). For more in-depth information, interactive elements including slicer options, tooltips, and filters were employed.

![Dashboard Visuals](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/0e15cd10-53bb-4cda-860f-fc07d209cddb)

# Insights
From the visuals created, Important insights and trends were highlighted. Some of these include:
- There is about 26.6% cancelation rate across the years (2018 - 2020).<br>
- 3 out of 10 bookings were cancelled.<br>
- Out of the total bookings, 49.1% had special requests.
- Transient customer type has the highest bookings while group bookings are the least.
- TA/TO distribution channel has the highest booking.
