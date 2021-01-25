# Group 3: Project 1 - A comparison of pedestrian traffic in Melbourne CBD with eateries in surrounding area


Our project was to uncover the link between foot traffic in Melbourne CBD with the type of eateries in the surrounding area, their ratings and their price: **why do some eateries have higher user ratings than others** and does location and foot traffic have any statistical influence on this?

Contributors: Welan Chu, Catherine Sloan, Thomas Maina & Franz Kiel


# Files & Directory Structure

Our working files, resources and outputs can be found in the following structure:
 
## Resource directory

All external sources used to gather data in order to test our hypotheses (other than API calls within Jupyter Notebook.)
 - **COM_ftraffic_2019-all_locations.csv:** full dataset of 2019 City of Melbourne foot traffic as counted in **all** sensor locations. 
 - **PCS_Locations:** full dataset of City of Melbourne Pedestrian Counting System sensor locations, obtained in CSV format from City of Melbourne Open Data.

## Output directory

The Output contains all exported CSVs and visualisations (as PNGs) pertaining to the analysis of the datasets. 

### 1_pedestrian_csv

 - **censors2019_chosen3.csv:** Hourly pedestrian count data from 2019 filtered to the three locations in our analysis.     
 -  **censors2019_chosen3_cleaned.csv:** Hourly pedestrian count data from 2019 filtered to the three locations in our analysis, errorneous data removed (e.g. counts of -1)     
 - **censors2019_chosen3_dailyaverage.csv:** Hourly pedestrian count data from 2019 filtered to the three locations in our analysis and averaged into daily average counts.
 - **censors2019_chosen3_dailyaverage_transposed.csv:** Average daily pedestrian count data transposed by location, such that row labels are locations and columns are dates in 2019.

### 2_zomato_csv

-  **Zomato_Restaurants_All.csv:** full dataset of eateries from final 3 sensor locations, with no adjustments made to the *Type* column (i.e. no .replace() function to consolidate types.) 
 - **Zomato_Restaurants_All_Consolidated-Types.csv:** full dataset of eateries from final 3 sensor locations, with .replace() function to consolidate the *Type* column.

### 3_analysis_csv

 - **sensors3_averaged_rating_price_pedestrians.csv:** Averages of rating, price and daily pedestrian count for 2019, for the 3 locations.

### 4_post_presentation
 - **combined_sensor_rating_price_traffic.csv:** aggregated dataset of eateries from final 9 sensor locations, with the average (mean) for *Aggregate Rating*, *Price*, and *Daily Average (number of pedestrians per day for the entirety of 2019)*.
- **sensor_locs_final_9.csv:** aggregated dataset of final 9 sensor locations, with the average (mean) number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_high.csv:** aggregated dataset the three highest foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_high.csv:** aggregated dataset the three highest foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_med.csv:** aggregated dataset the three medium foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
- **sensor_locs_hourly_low.csv:** aggregated dataset the three lowest foot traffic sensor locations (out of the final 9 locations), with the average (mean) hourly number of pedestrians per day for the entirety of 2019.
-  **Zomato_Restaurants_All.csv:** full dataset of eateries from final 9 sensor locations, with no adjustments made to the *Type* column (i.e. no .replace() function to consolidate types.) 
 - **Zomato_Restaurants_All_Consolidated-Types.csv:** full dataset of eateries from final 9 sensor locations, with .replace() function to consolidate the *Type* column.

## 1_Pedestrian_Sensor_Notebooks

Contains the following notebooks:

 - **1_extracting_three_sensors_notcleaned.ipynb:** Jupyter Notebook used for extracting the raw CSV pedestrian count dataset into only three locations per our analysis.
 - **2_cleaning_three_sensors.ipynb:**    

## 2_Zomato_Notebooks

Contains the following notebooks:

 - **Zomato_Data.ipynb:** Jupyter Notebook used for retrieving eateries data from Zomato API.
 -  Note: a config.py file is required with appropriate API keys, refer to README in directory.

## 3_Analysis_Notebooks

Contains the following directories:

### 1_questions_1_2
Contains the following notebooks: 

 - **1_sensors_trafficlinegraph.ipynb:** Jupyter Notebook used for creating line graph of average daily pedestrians per location for 2019. 
 - **2_groupbysensor_appliedaverages_barcharts.ipynb:** Jupyter Notebook used for creating bar charts to analyse average ratings and price relative to average daily pedestrians per location for 2019.
 - **3_box_whisper_scatter_ANOVA.ipynb:** Jupyter Notebook used for creating box and whisker plots and scatter plots to analyse the correlation, mean and interquartile range of the average user rating and price rating compared to each location. An ANOVA was also performed to test whether the results supported or rejected the null hypothesis.

### 2_question_3
Contains the following notebooks: 

 - **eateries_type_analysis.ipynb:** Jupyter Notebook used for analysing the frequency of eatery types relative to average pedestrian counts per location, using bar charts and Google Maps marker locations to plot locations geographically.
 - Note: a config.py file is required with appropriate API keys, refer to README in directory.

## 4_Post_Presentation

Contains the following notebooks: 

 - **Combined_Analysis.ipynb:** Jupyter Notebook used for performing data and statistical analyses of City of Melbourne's Open Data Pedestrian Counting System dataset and Zomato's eateries dataset.   
 - **Ped_Count_2019_PostPres.ipynb:** Jupyter Notebook used for retrieving pedestrian foot traffic data from City of Melbourne's Open Data Pedestrian Counting System, via CSV files.
 - **Zomato_Data_PostPres.ipynb:** Jupyter Notebook used for retrieving eateries data from Zomato API.
 -  Note: a config.py file is required with appropriate API keys, refer to README in directory.



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
 2. Following step 1, the CSV file was then imported to Jupyter Notebook and reduced to 3 sensors **(for Thursday's Presentation)** and then exported as a new CSV file. These locations were chosen as it was found that they had different levels of foot traffic: one was high, medium and low, and they were far enough apart that they would not overlap in terms of restaurant data and may provide insight into different locations types: 
	 - Bourke Street Mall: retail/commercial district
	 - Queen Vic Market/Elizabeth St: retail/tourist district
	 - Flinders St/Spark La: office district
	
 3. The new, reduced CSV file, was then imported to a new Jupyter Notebook, and count and datatypes tested to confirm number of datapoints and the data types of each column. 
 4. Faulty data was discovered (pedestrian counts of -1), which were removed from the dataframe by performing a conditional loc search on all columns where the values did not equal -1. This was confirmed through a count and checking the minimum and maximum values remaining in the dataframe.
 5. The cleaned dataframe was then grouped by date and averaged to get the average per day count (aggregating the hourly rows into a single day average.)
 6.  The dataframe was then transposed such that the locations became the index and the dates became the columns, in order to perform a statistical analysis using the .describe() method on the dataframe.

## City of Melbourne Open Data: Pedestrian Count System Location Dataset

 1. The dataset was retrieved online at: https://data.melbourne.vic.gov.au/Transport/Pedestrian-Counting-System-Sensor-Locations/h57g-5234 on 15 January 2021 as a CSV file. No further cleaning of the data was required in this form.

## Zomato API restaurant search

 1. Import City of Melbourne's sensor location csv data as a pandas dataframe.
 2. Do a .loc() search to filter down to only three locations. 
 3. Run a looped API call to extract maximum 40 restaurants within 50 metres of the three sensor locations and append as JSON to an empty list. A loop is required as Zomato only provides 20 results per call, and in order to loop through more data, it is required to set the "start" variable as an integer in multiples of 20.
 4. Following step 3, run a loop to extract only relevant data (e.g. name, rating, cuisine type, etc.) by appending said data into empty lists. 
 5. Once all data is extracted, combine all lists into a Pandas dataframe and drop duplicates, confirming results using a .count() on the dataframe.
 6. In order to ensure that the datatypes were numeric, the columns "Aggregate Rating," "Latitude" and "Longitude" were set as float using the .astype(float) method.
 7. The dataframe was then ready to extract to be used to test the first and second question's hypotheses. 
 8. In order to test the third question, the cuisine type or "Type" column contained "dirty" data, which had multiple types per restaurant and needed to be consolidated into 8 overarching categories: Bakery, Beverages, Cafe and Fast Food for daytime-predominant eateries, and Bar, Desserts, Pub and Restaurants as nighttime-predominant eateries. It is noted that this broad generalisation is a limitation in the analysis as these categories may contain restaurants that do not fit discretely into "day" or "night" but are a blend of both.


## Merging datasets

 With each dataset neatly exported into CSV format, the datasets are merged to perform data analyses to evaluate our hypotheses.
 
 1. **Question 1 & 2 hypothesis test:** Zomato CSV data was imported into a new Jupyter Notebook and the data grouped by sensor and the mean "Aggregate Rating" and "Price" calculated for each location 
 2. The pedestrian foot traffic data was then imported and the mean calculated for each location and saved as a Pandas series. 
 3. A new column in the dataframe from step 1 was assigned the pandas series from step 2 create an expanded dataframe that contained datasets from both CSVs.
 4. From this CSV, a number of visualisations were created, including scatter plots, box and whisker plots  and bar charts to identify the correlation (if any) between traffic and ratings / price. 
 5. **Question 3 hypothesis test:** Zomato CSV data was imported into a new Jupyter Notebook and the data filtered into three separate dataframes per location. The .value_counts() method was applied and sorted alphabetically using .sort_index() method and then the index reset using reset_index() method. 
 6. Each location-based dataframe was then re-merged to create one combined dataframe with value counts of each eatery type. 
 7. This dataframe was transposed to allow for bar graphing the results with locations along the x-axis and eatery types as the categories to be measured, with number of eateries as the y-axis.

# Data Exploration & Analysis

The data shows that Bourke Street Mall  (BSM) has the highest foot traffic of the three locations, followed by Queen Victoria Market & Elizabeth Street intersection (QVM), and Flinders Street & Spark Lane (Flin) intersection with the lowest.

### Question 1: Pedestrian Foot Traffic vs Rating
Based on our analyses, as evidenced in the box and whisker plot, BSM had the biggest range of ratings and lowest mean rating, while QVM had the highest mean rating and shortest range of ratings. 

When analysing each restaurant's ratings individually in comparison to foot traffic, as evidenced in the scatter plot, the correlation coefficient (r.) is quite weak at -0.188, indicating that there is generally a negative correlation between ratings and foot traffic. That is, the lower the foot traffic, the higher the rating is likely to be. However, the coefficient of determination (r squared) is very low, at 0.035, indicating that the linear regression is a poor predictor of ratings to foot traffic.

This appears to be supported by the ANOVA, with a p-value greater than 0.05, indicating there is no statistical significance and that we may retain the null hypothesis.

### Question 2: Pedestrian Foot Traffic vs Price
Based on our analyses, as evidenced in the box and whisker plot, all locations had, coincidentally, the same mean price of 2, while Flin appears to have the highest price rating and BSM having the lowest. This appears to suggest that the lowest foot traffic areas have the priciest restaurants, while the highest foot traffic areas have the cheapest restaurants.

When analysing each restaurant's ratings individually in comparison to foot traffic, as evidenced in the scatter plot, the correlation coefficient (r) is weak at -0.260, indicating that there is generally a slight negative correlation between prices and foot traffic. That is, the lower the foot traffic, the higher the price is likely to be. However, the coefficient of determination (r squared) is very low, at 0.067, indicating that the linear regression is a poor predictor of ratings to foot traffic. It is noted, however, that the correlation is slightly greater than for the user ratings-foot traffic scatter plot, indicating price-foot traffic can be determined with slightly better accuracy with the linear regression analysis.

The ANOVA assessment yields a p-value less than 0.05, indicating there is some statistical significance and that we may reject the null hypothesis.

### Question 3: Pedestrian Foot Traffic vs Eatery Type
Based on our analyses, there appears to be insufficient evidence to correlate any type or day/nighttime types to foot traffic, with some exceptions being the *Beverages, Fast Food* and *Bar* types having fairly strong coefficients of determination (r squared) of 0.938, 0.624 and 0.981 respectively, suggesting the linear regression lines are good predictors of whether type is influenced by foot traffic.

Interestingly, evidenced in the stacked bar charts, BSM, which had the highest evening/nighttime peak traffic of all three locations, had the lowest nighttime eatery types and the highest daytime eatery times. Meanwhile QVM had the highest overall nighttime types despite having its peak foot traffic during the day. 

The ANOVA assessment suggests that the p-value for both daytime and nighttime types is less than 0.05, this indicates some statistical significance and that we may reject the null hypothses.

# Limitations

One limitation of our analysis is that we had to define the type of eateries ourselves. The zomato API categorised each restaurant into a very specific type such as ‘Fast Food, Japanese, Sushi’. We condensed these down to 8 broader types.

A second limitation is that we only chose 3 sensor locations, with more time we would have increased our foot traffic data by looking at more sensors. We would also increase our restaurant data by increasing the radius from 50 metres from each sensor. With more data our analysis would then be more accurate and reliable.

With more preparation time we could establish time series profiles, i.e. at what time of the day did the sensors have high foot traffic. Some areas are frequented by commuters and others by people going out for dinner; could also look at weekdays vs weekend.

The foot traffic data is recorded every hour for each sensor, i.e. 24*365 = 8,760 data point per year. As the Zomato restaurant data doesn’t include a time series component, we couldn’t use this level of granularity. We used the mean function to reduce it to a single value per sensor.
# Conclusions
We were surprised by some of the findings we made throughout our project. Particularly within question 3, pedestrian foot traffic vs eatery type. We predicted that locations with significant foot traffic throughout the day would have the seen the results from locations with significant foot traffic at night time and vice versa. An explanation for this is that there is no evidence to suggest that the reason why Bourke St Mall is busier at night time is due to people looking for evening drinks or food, perhaps this is a popular location in the evening for another reason, such as a popular route home. Similar for Queen Vic Market, this is likely to be busy throughout the day for shopping as apposed to an area to eat. It could have a good reputation for evening drinks to explain the results we see. 
This is a limitation of only looking at one sensor for each type of area. For our results to be more meaningful we would have to look at more locations with high foot traffic in the evening compared to high foot traffic in the day time. Different locations with high foot traffic in the evening may see more bars, beverages and fast food type eateries. 
To conclude, given more time we would have liked to investigate more locations for our presentation and also increase the radius from the sensor points to include more data. With a more fluid Github workflow this would have been more achievable in the time that we did have. With more practice working in groups and branches, hopefully we can achieve a better analysis for future projects. 
