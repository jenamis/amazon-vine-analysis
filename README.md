# Amazon Review Analysis

## Overview
The purpose of this project was to analyze Amazon reviews written by members of the Amazon Vine program, which provides products to members and requires them to write a review, compared with reviews written by Amazon customers who were not members of the Vine program. The analysis looked specifically at reviews of Amazon products in the furniture category, and sought to determine whether there appeared to be bias toward favorable reviews from Vine members based on the dataset.

## Results
All analysis was performed using the furniture dataset accessed from [Amazon review datasets](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt). A [script in PySpark](Amazon_Reviews_ETL.ipynb) was used to extract the dataset, transform the data, connect to an Amazon Web Services (AWS) Relational Database Service (RDS) instance, and load the data into four tables in pgAdmin. A [Python script using Pandas in Jupyter Notebook](Vine_Review_Analysis.ipynb) was then used to analyze the [transformed dataset of furniture reviews](Resources/vine_table.csv) written by Vine members and non-Vine members and compare the percentage of favorable (5-star) reviews from each group. The analysis was limited to reviews with at least 20 “total votes” and where the ratio of “helpful votes” to “total votes” was at least 0.5.

The results of the analysis are shown in the table below and outlined as follows:
-    Out of a total of 18,155 furniture reviews with at least 20 “total votes” and a “helpful votes” to “total votes” ratio of at least 0.5, **136** reviews were written by members of the Vine program and **18,019** were written by customers who were not members of the Vine program.
-    Out of 136 reviews written by members of the Vine program, **74** (**54%**) were 5-star reviews.
-    Out of 18,019 reviews written by customers who were not members of the Vine program, **8,482** (**47%**) were 5-star reviews.

![img1](Resources/ Vine_Review_Summary.png)


## Summary
There was a seven percentage point difference in reviews giving 5 stars when comparing those written by members of the Vine program and those written by customers who were not members of the Vine program, suggesting there may be positivity bias for reviews in the Vine program. It is important to note that the total number of reviews written by Vine members was significantly less than the total number written by non-Vine members. An additional analysis that would be beneficial for examining the question of positivity bias in the Vine program is a one-sided two-sample t-test with an alternative hypothesis that the mean star rating for the sample of Vine reviews is greater than the mean star rating for the sample of non-Vine reviews.
