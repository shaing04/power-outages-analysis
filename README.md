# Power Outages: An Analysis and Prediction Model
UCSD DSC 80 Data Science Project


### [Github Link](https://github.com/shaing04/power-outages-analysis)

### By: Susana Haing, Sonali Singh

## Introduction 
In this project, we examined [data](https://engineering.purdue.edu/LASCI/research-data/outages) through Purdue University's Laboratory for Advancing Sustainable Critical Infrastructure of power outages in the United States from January 2000 to July 2016. 

The data includes information about each major power outage, including but not limited to: geographical location, climate/weather, outage cause, and the number of people affected. 

Our overarching research question is: How do different causes affect power outages? We will do a deeper dive into how the different causes of power outages within the dataset will affect the length of a power outage. 

After determining whether there exists a causal relationship, we will also build a model that will predict the length of a power outage given different features. This is important as more often than not, customers want to know how long their power outages will last, whether it was due to maintenance or an unintentional outage. Being able to provide a good estimate of how long a power outage will last based on the various circumstances such as weather and location, can allow power companies to better inform their consumers.

For our analysis, we will be focusing on the following variables. 

<div id="div3">
        <br>
        <table border="1">
            <tr class="heading">
                <th>Variable</th>
                <th>Description</th>
            </tr>
            <tr class="row1">
                <td>YEAR</td>
                <td>The year an outage occurred</td>
            </tr>
            <tr class="row2">
                <td>MONTH</td>
                <td>The month an outage occurred</td>
            </tr>
            <tr class="row3">
                <td>U.S._STATE</td>
                <td>The specific US State the power outage occurred in</td>
            </tr>
            <tr class="row4">
                <td>NERC.REGION</td>
                <td>North American Electric Reliability Corporation regions of an outage</td>
            </tr>
            <tr class="row5">
                <td>CLIMATE.REGION</td>
                <td>The 9 climate regions in the United States defined by the National Centers for Environmental Information</td>
            </tr>
            <tr class="row6">
                <td>OUTAGE.START.DATE</td>
                <td>The date an outage started</td>
            </tr>
            <tr class="row7">
                <td>OUTAGE.START.TIME</td>
                <td>The time an outage started</td>
            </tr>
            <tr class="row8">
                <td>OUTAGE.RESTORATION.DATE</td>
                <td>The date an outage was resolved</td>
            </tr>
            <tr class="row9">
                <td>OUTAGE.RESTORATION.TIME</td>
                <td>The time an outage was resolved</td>
            </tr>
            <tr class="row10">
                <td>CAUSE.CATEGORY</td>
                <td>Different causes of any given power outage</td>
            </tr>
            <tr class="row11">
                <td>CLIMATE.CATEGORY</td>
                <td>Whether it was cold, hot, or normal climate during the time of the outage</td>
            </tr>
            <tr class="row12">
                <td>OUTAGE.DURATION</td>
                <td>The amount of time an outage lasted in minutes</td>
            </tr>
            <tr class="row13">
                <td>CUSTOMERS.AFFECTED</td>
                <td>The number of customers affected by an outage</td>
            </tr>
            <tr class="row14">
                <td>POPDEN_URBAN</td>
                <td>Population density of urban areas (# persons per square mile)</td>
            </tr>
        </table>
    </div>


## Data Cleaning and Exploratory Data Analysis 
The original dataset comes with 57 total different variables, but we will focus only on the above columns for analysis and relevance sake.

Additionally, rather than having the start and restoration columns be separated by date and time, we will condense them into one column each. 
So 'OUTAGE.START.DATE' and 'OUTAGE.START.TIME' will be condensed into 'OUTAGE.START', and 'OUTAGE.RESTORATION.DATE' and 'OUTAGE.RESTORATION.TIME' will be condensed into 'OUTAGE.RESTORATION'. And after condensing, we will drop the 'OUTAGE.START.DATE', 'OUTAGE.START.TIME', 'OUTAGE.RESTORATION.TIME', and 'OUTAGE.RESTORATION.DATE' columns as they are now duplicate columns.

We also replaced any 0 values in the 'OUTAGE.DURATION' column with NaN values. This is because if it is listed in the dataset, then it must be a major power outage, and any major power outage having a duration of 0 minutes makes no sense, so the 0 was more likely to have resulted from some sort of error and is therefore, an inaccurate representation of the data.


## Univariate Analysis
Now let's take a look at how the power outages are distributed across the 50 states. We can visualize this with a choropleth map, which will show by color, the number of power outages each state has and also show which states have the most and least number of power outages.

<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets/outages_map.html" width="100%" height="600" frameborder = "0"></iframe>
</div>

Next, we wanted to see how the number of power outages have changed over time. 
<div style="width: 100%; margin: 0 auto;">
    <iframe src="assets/outages_overtime.html" width="100%" height="600" frameborder = "0"></iframe>
</div>

We also wanted to see the number of power outages across the different climate regions. 
<div style="width: 100%; margin: 0 auto;">
    <iframe src="assets/outages_climate_region.html" width = "100%" height = "600" frameborder = "0"></iframe>
</div>

## Bivariate Analysis

First, we wanted to take a look at how the 'OUTAGE.DURATIONS' were distributed across the different 'CLIMATE.REGION's.
<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets/outage_duration_climateregion.html" width="100%" height="600" frameborder = "0"></iframe>
</div>

We also wanted to look at how the outage durations were distributed across the different cause categories. 
<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets/outage_duration_cause_cat.html" width="100%" height="600" frameborder = "0"></iframe>
</div>

## Grouping and Aggregation 

First we wanted to take a look at comparing the average duration of each cause category with the median, max, and also see the total number of outages in each cause category.
<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets\agg_summary_table.html" width="100%" height="260" frameborder = "0"></iframe>
</div>

We also wanted to see the number of times each region experienced a specific type of power outage. 
<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets/pivot_table_year.html" width="100%" height="300" frameborder = "0"></iframe>
</div>

## Methods of Missingness 


## Hypothesis Testing 
We will be testing if the 'CAUSE.CATEGORY' has an affect on the length of a power outages. In particular, we will be testing if Severe Weather has an affect, and if it doesn't, we will test which 'CAUSE.CATEGORY' does have an affect.

**Null Hypothesis:** Severe weather has no effect on the length of a power outage.

**Alternative Hypothesis:** Severe weather has an effect on the length of a power outage (either causing a shorter or longer poewr outage).

**Test Statistic:** Difference in means

To do so, we will be performing a permutation test to determine whether our hypothesis holds or not. 

<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets/permutation_test.html" width="100%" height="400" frameborder = "0"></iframe>
</div>

Results: 
Observed difference: 2537.81 minutes
Permutation p-value: 0.0000

Since the p-value is 0.0, we can conclude that we will REJECT the null hypothesis as severe weather does significantly affect outage duration. 

## Modeling 
## Framing a Prediction Problem 
## Baseline Model 
## Final Model
## Fairness Analysis


## Conclusion
