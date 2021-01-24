# Group 3: Project 1 - A comparison of pedestrian traffic in Melbourne CBD with eateries in surrounding area


Our project was to uncover the link between foot traffic in Melbourne CBD with the type of eateries in the surrounding area, their ratings and their price: **why do some eateries have higher user ratings than others** and does location and foot traffic have any statistical influence on this?

Contributors: Franz Kiel, Catherine Sloan, Thomas Maina & Welan Chu


# Files & Directory Structure

Our working files, resources and outputs can be found in the following structure:

## Root directory

Contains the following notebooks: 

 - **Combined_Analysis:** Jupyter Notebook used for performing data and statistical analyses of City of Melbourne's Open Data Pedestrian Counting System dataset and Zomato's eateries dataset.   
 - **Pedestrian_Traffic_Data.ipynb:** Jupyter Notebook used for retrieving pedestrian foot traffic data from City of Melbourne's Open Data Pedestrian Counting System, via CSV files.
 - **Zomato_Data.ipynb:** Jupyter Notebook used for retrieving eateries data from Zomato API.
 
## Resource directory

All external sources used to gather data in order to test our hypotheses (other than API calls within Jupyter Notebook.)
 - **COM_ftraffic_2019-all_locations.csv:** full dataset of 2019 City of Melbourne foot traffic as counted in **all** sensor locations. 
 - **PCS_Locations:** full dataset of City of Melbourne Pedestrian Counting System sensor locations, obtained in CSV format from City of Melbourne Open Data.

## Output directory

The Output contains all exported CSVs and visualisations (as PNGs) pertaining to the analysis of the datasets. 

### CSV directory

 - **Zomato_Restaurants_All.csv:** full dataset of eateries from final 9 sensor locations, with no adjustments made to the *Type* column (i.e. no .replace() function to consolidate types.) 
 - **Zomato_Restaurants_All_Consolidated-Types.csv:** full dataset of eateries from final 9 sensor locations, with .replace() function to consolidate the *Type* column.
 - **combined_sensor_rating_price_traffic.csv:** aggregated dataset of eateries from final 9 sensor locations, with the average (mean) for *Aggregate Rating*, *Price*, and *Daily Average (number of pedestrians per day for the entirety of 2019)*.
- **sensor_locs_final_9.csv:** aggregated dataset of final 9 sensor locations, with the average (mean) number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_high.csv:** aggregated dataset the three highest foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_high.csv:** aggregated dataset the three highest foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_med.csv:** aggregated dataset the three medium foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_low.csv:** aggregated dataset the three lowest foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.

### PNG directory

 - Statistical analyses testing each question, represented through various plots. 

## Superseded directory


# Hypotheses

Our topic raised three questions, with the following hypotheses, null and alternative hypotheses to each being:

1.  **Do higher traffic areas have a higher zomato rating than low traffic areas?**

>**_Hypothesis:_**  If higher foot traffic influences zomato ratings, then higher foot traffic areas will have a higher average rating than lower foot traffic areas.
>
>**_Null Hypothesis:_**  If higher foot traffic does not influence zomato ratings, then higher foot traffic areas will not have a higher average rating than low foot traffic areas.
>
>**_Alternative Hypothesis:_** If higher foot traffic has any effect on zomato ratings, then higher foot traffic areas will have a different average rating than low foot traffic areas?

2.  **Does foot traffic influence the price of eatery?** 

>**_Hypothesis:_** If higher foot traffic influences zomato ratings, then higher foot traffic areas will have a higher average price rating than lower foot traffic areas. 
>
>**_Null Hypothesis:_**  If higher foot traffic does not influence zomato ratings, then higher foot traffic areas will not have a higher average price rating than low foot traffic areas.
>
>**_Alternative Hypothesis:_** If higher foot traffic has any effect on zomato ratings, then higher foot traffic areas will have a different average price rating than low foot traffic areas?

3.  **Does foot traffic determine the type of eatery?**
   
>**_Hypothesis:_**  If foot traffic influences the type of eatery, then daytime-centric eateries will be more prevalent in high-daytime foot traffic areas and likewise nighttime-centric eateries to high nighttime foot traffic.
>
>**_Null Hypothesis:_** If foot traffic does not influence the type of eatery, then there will be no difference in the spread of eatery types relative to peak times of foot traffic.
>
>**_Alternative Hypothesis:_** If foot traffic influences the type of eatery, then this may vary between location types (e.g. office areas, shopping areas, tourism areas)?

# Data sources


City of Melbourne Open Data - Pedestrian Count System:
-   **url:** http://www.pedestrian.melbourne.vic.gov.au/#
-   **date retrieved:** 17 January 2021 
-   **data format (csv, json, api):** csv Files
-   **organisation:** City of Melbourne  
-   **how data was retrieved:** CSV downloaded direct from source via links.

Zomato API - Restaurants Search URL:
-   **url:** https://developers.zomato.com/api   
-   **date retrieved:** 16 January 2021
-   **data format (csv, json, api):** API <https://developers.zomato.com/api/v2.1/search?>    
-   **organisation:** Zomato Media Pty Ltd
-   **how data was retrieved:** API calls using Python requests.get() and stored as .json()

# Data Wrangling

This process required combining three sources of data: the City of Melbourne's Open Data Pedestrian Count System containing number of pedestrians per hour per day (we focused on 2019 data only, as 2020 data was an exceptional year and thus unreliable,) City of Melbourne's sensor location dataset which cotained information such as latitude and longitude of each sensor, which we could then use to do an API search of Zomato's data around the sensor latitudes and longitudes that we wanted.

The data wrangling process was handled in **Jupyter Notebook**, unless noted otherwise, and applies to notebooks produced for the **Thursday Presentation** as well as **post-presentation**, unless noted otherwise. 

## City of Melbourne Open Data: Pedestrian Count System

 1. Having retrieved the full hourly dataset from City of Melbourne's Open Data website a multiple CSV files per month (i.e. hourly data for January 2019, February 2019, March 2019, etc.) the datasets were combined in Microsoft Excel. During this process, it was found that there were some inconsistencies in column names/arrangement between some months, and so manual cleanup within excel was performed to tidy up the data as a consolidated CSV file.
 2. Following step 1, the CSV file was then imported to Jupyter Notebook and reduced to 3 sensors **(for Thursday's Presentation)** and then exported as a new CSV file.
 3. The new, reduced CSV file, was then imported to a new Jupyter Notebook, and count and datatypes tested to confirm number of datapoints and the data types of each column. 
 4. Faulty data was discovered (pedestrian counts of -1), which were removed from the dataframe by performing a conditional loc search on all columns where the values did not equal -1. This was confirmed through a count and checking the minimum and maximum values remaining in the dataframe.
 5. The cleaned dataframe was then grouped by date and averaged to get the average per day count (aggregating the hourly rows into a single day average)
 6. The dataframe was then transposed such that the locations became the index and the dates became the columns, in order to perform a statistical analysis using the .describe() method on the dataframe.

## City of Melbourne Open Data: Pedestrian Count System Location Dataset

 1. The dataset was retrieved online at: https://data.melbourne.vic.gov.au/Transport/Pedestrian-Counting-System-Sensor-Locations/h57g-5234 on 15 January 2021 as a CSV file. No further cleaning of the data was required in this form.
