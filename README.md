# Power Outages: An Analysis and Prediction Model
UCSD DSC 80 Data Science Project


### [Github Link](https://github.com/shaing04/power-outages-analysis)

## Analyzing Power Outages: 
By: Susana Haing, Sonali Singh

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


## Exploratory Data Analysis
### Data Cleaning 
The original dataset comes with 57 total different variables, but we will focus only on the above columns for analysis and relevance sake.

Additionally, rather than having the start and restoration columns be separated by date and time, we will condense them into one column each. 
So 'OUTAGE.START.DATE' and 'OUTAGE.START.TIME' will be condensed into 'OUTAGE.START', and 'OUTAGE.RESTORATION.DATE' and 'OUTAGE.RESTORATION.TIME' will be condensed into 'OUTAGE.RESTORATION'. And after condensing, we will drop the 'OUTAGE.START.DATE', 'OUTAGE.START.TIME', 'OUTAGE.RESTORATION.TIME', and 'OUTAGE.RESTORATION.DATE' columns as they are now duplicate columns.

We also replaced any 0 values in the 'OUTAGE.DURATION' column with NaN values. This is because if it is listed in the dataset, then it must be a major power outage, and any major power outage having a duration of 0 minutes makes no sense, so the 0 was more likely to have resulted from some sort of error and is therefore, an inaccurate representation of the data.


### Univariate Analysis
Now let's take a look at how the power outages are distributed across the 50 states. We can visualize this with a choropleth map, which will show by color, the number of power outages each state has and also show which states have the most and least number of power outages.

<div style="width: 100%; margin: 0 auto;">
  <iframe src="assets/outages_map.html" width="100%" height="600" style="border: none;"></iframe>
</div>

Next, we wanted to see how the number of power outages have changed over time. 

<iframe src="assets/outages_overtime.html", width = "100%", height = "600"></iframe>

We also wanted to see the number of power outages across the different climate regions. 

<iframe src="assets/outages_clime_region.html", width = "100%", height = "600"></iframe>


### Bivariate Analysis

### Grouping and Aggregation 


## Methods of Missingness 


## Hypothesis Testing 


## Modeling 
### Framing a Prediction Problem 
### Baseline Model 
### Final Model
### Fairness Analysis


## Conclusion
