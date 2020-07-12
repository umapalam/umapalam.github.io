---
layout: post
title:      "Visualization and Data "
date:       2019-06-24 10:02:21 -0400
permalink:  visualization_and_data
---


This blog post is written in conjunction with the module one final project. I found the project to be difficult in certain aspects. This was most especially true in terms of the visualization part. The overall goal of project one was to be able to create a regression model that helps predict how much a house would sell in King County. The initial step to starting this project was to import all the necessary libraries. This would include for example: pandas, seaborn, matplotlib and so on. Matplotlib was important because it would allow for visualizations to be made. 

My first thoughts after importing the library was to clean up the data. I would try to convert all the variables to numeric if they were not that already. This was done because machine learning processes are unable to function if the data type is not numeric. If would only give out errors. After checking the types, I would go on to check the null values. I remember there being four variables that contained null values. 

After taking care of the null values by either replacing them or dropping them, I would move on to the exploration part of the project. This was where the visualizations would come in. I did three different graphs thoughout this part. They were a bar chart, histogram and scatter plot. The bar chart was based on the square feet of basement within each house. I wanted to create two categories. Those two categories would be large and small. I found the quantile range for the variable 'sqft_basement', first .33 and then at .66 in order to differentiate the two categories. I also ended up making a for loop that iterate these categories to the matching value. This required the use of if, else statements. 

The second visualization was more simple. Even though it was a histogram I did not need to come up with a range for the bin sizes. The grades for each of the houses only extended to 12 so each grade had a bin within the graph. Histograms can be very tricky if it is not clear cut as this. Sometimes you would have to manipulate the data so that they are put in groupings. These groupings would be used to decide the bin sizes. 

The third visualization pictured in the following link: (http://drive.google.com/open?id=1dD72_GL3swnOFJnURI31dK-gBIIfjgwL), was one that I liked. I like scatter plots in that it is very simple to be able to tell whether or not two variables had a negative or positive relationship. This particular one had a positive relationship, where as the 'sqft_living' space increase so did the price of the individual house. This supports my idea that more space equally more money. Although, it was later that I found that some of my chosen variables for the regression were too close together and thus made the more unreliable. This could also have been caused by scaling issues. 

I probably could have improved on the last two visualizations. I now find that they could be too simplistic. This could be a reasonable error. I should have manipulated the data more so that I could understand it better. This is something to improve upon. I also noticed while looking back at the jupyter notebook that it was not very colorful which can perhaps take away from the impact of the images. Deciding on what to do for the figure size was also difficult in that sometimes the data on the graph appeared hard to see at times. This is also something to take into account, going forward. 





