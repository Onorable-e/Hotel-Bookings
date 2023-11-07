![image](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/987806d2-f9de-4d33-afef-532be11aea64)![Hotel booking](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/b40c430e-11c1-4a78-9135-e58f252ed054)

This is a guided project in my data analytics (Power BI) class with Datafied Academy. <br>
# Problem Statement 
In the dynamic hospitality industry, data-driven decision-making has become an indispensable tool for optimising operations and enhancing customer satisfaction. As a budding data analyst, my task is to leverage Power BI to transform and analyse the dataset containing valuable information about hotel bookings.

# Dataset Overview 
The dataset contains various aspects of hotel bookings collected over 3 years (2018 - 2020), ranging from booking details to guest demographics. Each entry contains essential information like the Average Daily Rate (ADR), number of guests, booking agency, arrival details, room assignments, and more. 

## Project Objective 
The project's objective was to help enhance hotel revenue and customer experience through data-driven insights by analysing the booking records and creating dashboard(s) that provide valuable insights. The dashboard should contain insightful charts, graphs, and tables to convey information effectively, thereby enabling informed decision-making on enhancing hotel revenue and customer experience. 

## Business Questions and Metrics
We defined specific business questions that should be answered. Examples of questions include: <br>
- Who are the people booking? <br>
- Which of our customers are canceling their bookings? <br>
- Where do we have the most bookings? <br>
- Out of the total bookings, how many were successful and unsuccessful? <br>

## Key Performance Indicators (KPIs)
We also defined metrics and KPIs that will help answer the business questions. Examples include: <br>
- Total booking <br>
- Total cancellation/cancellation rate <br>
- Successful booking: Total booking where the reservation status is checked out. Unsuccessful booking: Total booking where the reservation status is canceled or no show. <br>

## Dataset
![Dataset Screenshot](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/6f624268-1f33-482b-8464-1482926fadbc)

## Data Inspection
- Shape of dataset: The dataset has 32 columns for each year and several rows.<br>
- The data set contains over 3000 missing values in the agent column and over 20000 in the company columns. <br>
- The dataset contains duplicates. <br>
- Outliers were noticed in the previous cancelation column. <br> 
- The data does not look consistent. For example, the lead time which is the number of days that elapsed between the entering date of the booking into the PMS and the arrival date had some values that were not within reasonable range. Also, columns; is_repeated_guest, previous_cancellations, and previous_bookings_not_canceled are inconsistent. <br>
- The data types for some of the columns are not consistent with the data types that they contain. <br>
  
## Data Cleaning 
- The different tables representing each year (2018 - 2020) were merged as a new table and renamed "Hotel Bookings". <br>
- Duplicates were removed: a new column (check duplicates) was created with the values from all the columns. Then the duplicates were removed from the column (check duplicates). <br>
- An arrival date column was created by merging the day, month, and year of arrival date. <br>
- The values 1 and 0 in the is_cancelled column were replaced with "Cancelled" and "Not Cancelled" respectively. <br>
- The values 1 and 0 in the is_repeat_guest column were replaced with "Repeat guest" and "New guest" respectively. <br>
- The NULL in the agent and company columns were replaced with an empty string. <br>
- The year, month name, day, and week of the year were extracted from the reservation_status_date column. <br>

### Dataset after cleaning
![After data cleaning](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/fb179a38-fea4-4c2c-aa15-ee15326c0fce)

## Data Modelling and Relationships
Dimension tables were created and they include:

### Location Dimension Table
- The location dataset was sourced from [statistic time](https://statisticstimes.com/geography/countries-by-continents.php)<br>
- The following columns were extracted from the data; Code, Country name, Region, and Continent.<br>
- The country name column was inspected for null value by filtering.
  
### Hotel Dimension Table 
The hotel dimension table was created from the merged dataset named "Hotel Bookings". The following steps were taken in creating this dimension:
- The data (Hotel Bookings) was duplicated. <br>
- All the transformation steps that came with the dataset were removed. <br>
- All the columns were removed except the hotel column. <br>
- All the duplicates from the hotel column were removed leaving just distinct values. <br>
- An ID column was created by using 'column from example' on the add column tab. <br>

NB: The ID for the resort hotel is 'HT01' while that of the city hotel is 'HT02'.

### Date Dimension Table
The date table was created from the 'Arrival_date' column using DAX. 

### Relationships
A one-to-many relationship between the fact table and the dimension tables was created. 

![Data modelling and relationship](https://github.com/Onorable-e/Hotel-Bookings/assets/139487541/53bf7370-89cb-40e2-b776-1d6115b122a5)
