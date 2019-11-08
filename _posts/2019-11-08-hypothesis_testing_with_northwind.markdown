---
layout: post
title:      "Hypothesis Testing with Northwind "
date:       2019-11-08 10:24:05 +0000
permalink:  hypothesis_testing_with_northwind
---

This project was focused on data from Northwind, which is a fictional companany that deals with importing and exporting goods internationally. The main objective was to explore the data using SQL queries. After this data scrubbing was finished, questions about the data would be asked. The first question was given and it centered on whether or not discounts had any statistical significance on the quantity of products in an order. 

Then, in order to answer this question, different statistical tests such as Welch's T-test and ANOVA would be utilized to answer these questions. Welch's T-test is a two-sample location test which is used to test the hypothesis between two groups that are equal or unequal. It is considered more reliable. ANOVA or the Analysis of Variance Test is a way to find out if results are significant. It can help you figure out if you need to reject the null hypothesis or accept the alternate hypothesis. Functions would be created and used throughout the coding proess to show Cohen's d. This is an effect size used to indicate the standardized difference between two means. 

In order to conduct these types of tests it is necessary to import statsmodels and other libraries. 

```
from scipy import stats 
import itertools 
import statsmodels.api as sm 
from statsmodels.formula.api import ols

```
Before forming the questions, looking at all the tables in the Northwind schema is important. Make several SQL statments like the one shown below in order to fully understand all the data that is available to analyze. 

``` 
c.execute("""SELECT * FROM 
OrderDetail""")
c.fetchall()

```
After the exploratory data phase of the project, questions could be asked about the data. The focus of this project was centered around cost. I wanted to know more about the effects of discounts regionally and through use of local shipping methods. I also wanted to know the difference between two countries in particular when it came to discounts. In this post, I will be writing more about the first question. 

There are four questions all together that was asked in this statistical analysis.

1.) Does discount amount have a statistically significant effect on the quantity of a product in an order? If so, at what level(s) of discount?

2.) Is there a significant difference in discounts given by employees from the United States and British Isles?.

3.) Is there a significant difference in total cost of orders by region?.

4.) Is there a significant difference in using local shipping in terms of cost for carriers?.

```
sns.distplot(df['Quantity'], hist='density')
plt.title('Quantity Distribution', fontsize=16)
plt.xlabel('Quantity', fontsize=16)

sns.distplot(df['Discount'], hist='density')
plt.title('Discount Distribution', fontsize=16)
plt.xlabel('Discount', fontsize=16)
```
Making histograms to see the particular distributions of both quantity and discount is the first step in answering the given question. The OrderDetail table in the Northwind schema was isolated and manipulated through SQL queries. 

In comparion to a normal distribution, both graphs on discount and quantity were skewed. The quantity distribution is more positivly skewed in comparison to the discount one. The bins for the discount histogram are set in increments (5%, 10%, 15%, 20%, 25%).The discounts themselves show little difference in terms of products being ordered. The only major differenence in this graph is that there were more products in orders with no discount at all.

```
df_orderdis = pd.read_sql_query("""SELECT Quantity, Discount FROM [OrderDetail] WHERE Discount >0""", conn)
df_orderno = pd.read_sql_query("""SELECT Quantity, Discount FROM [OrderDetail] WHERE Discount ==0""", conn)
print(df_orderdis.describe())
print(df_orderno.describe())
df_orderdis.head()

```
In the above piece of code, new variables were created in order to find the descriptive statistics and mean on average for both discount and no discount.
```
dfw = welch_t(df_orderdis.Quantity,df_orderno.Quantity)
d = cohen_d(df_orderdis.Quantity,df_orderno.Quantity)
```
We will be using the t-test to find out if the null or alternative hypothesis was correct. The null hypothesis was stated to be that there is no difference in order quantity due to discount. The alternative hypothesis was that there is an increase in order quantity due to discount. Results of the test shows that there is a statistically significant difference in quantities between orders with no discount and applied discounts of 5%, 10%, 15%, 20%, 25% so we reject the null hypothesis. 


