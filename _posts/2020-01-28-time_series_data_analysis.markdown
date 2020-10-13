---
layout: post
title:      "Time Series Data Analysis "
date:       2020-01-28 06:54:51 -0500
permalink:  time_series_data_analysis
---


The most basic definition of a time series data is a series of data points that are indexed in time and order. Some common examples of these kinds of data would be stock prices and temperature. One important thing to keep in mind about time series is that in order to do predictions of the data, the previous data points can not have a noticable trend, they have to be stationary. 

Learning about time series data was a slightly frustrating process. This was mainly due to trying to figure out how to convert the data that is loaded from a csv file to data that can be used for Sarima modeling. One method that I choose to focus on is going step by step. The first step was filtering the data and cleaning it of missing or null values so that it is  usable. 

The data is being used in this particular project would be housing and zipcode data. This is after importing all the necessary libraries needed for this analysis. The pandas library had the .melt function that could be used to convert the data. 

``` 
def melt_data(df4):
    melted = pd.melt(df4, id_vars=['Zipcode', 'City', 'State','County'], var_name='time')
    melted['time'] = pd.to_datetime(melted['time'], infer_datetime_format=True)
    melted = melted.dropna(subset=['value'])
    return melted.groupby('time').aggregate({'value':'mean'})

```
After this function was applied to the data, I made two different sets of dataframes. One for Orlando and another for Raleigh. This was so that I could later manipulate the data for modeling as well as to create plots of the data seperately. The index of each dataframe was changed to year-day-month. So this was the time and then there was a value to go along with each data point. 

```
Orlando_md = melt_data(Orlando)
Raleigh_md = melt_data(Raleigh)

```
Both plots for each dataframe were showing a high trend. That usually means that there is not a lot of stationarity in the data used so far and that going with the Sarima model is better than the Arima model. The Sarima model automatically takes care of this and seasonality when it is calculating. 

```
Orlando_md.plot(label ='Florida')
plt.legend()
plt.title('Orlando, Florida: Mean House Price from 2009 to 2018')
plt.ylabel('Mean House Price in USD')
plt.xlabel('Time')
plt.show()

```



