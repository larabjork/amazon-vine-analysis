# Amazon Vine Analysis
Data bootcamp week 17 - big data and AWS

## Overview
This independent challenge exercise involved selecting a product-specific dataset of Amazon reviews; using PySpark to extract and transform the data; connecting to an AWS Relational Database Service (RDS); and loading the data into pgAdmin. 

The dataset included a column about whether the reviewer was part of the [Amazon Vine program](https://www.amazon.com/vine/about). This column allows for comparison betwee paid and unpaid reviews. A second part of the challenge was to examine the data for bias based on participation in the Amazon Vine program.

## Results
I exported the table with Amazon Vine information from pgAdmin to Pandas for analysis. As specified in the challenge instructions, I refined the Vine program data as follows:

* Filtered out all rows where the total number of votes was less than 20.
![screenshot of dataframe showing filter for total number of votes >=20](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/filter1.png)

* From there, filtered for rows where the the number of "helpful votes" was at least 50% of the total votes.
![screenshot of dataframe showing filter for helpful votes / total number](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/filter2.png)

* From there, created separate dataframes based on participation in the Vine program.
![screenshot of dataframe showing filters for vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/filter3.png)

After these filtering steps, I was able to answer the following questions.
__1. How many Vine reviews and non-Vine reviews were there?
As shown in the image below, there were 43 Vine reviews and 7,791 non-Vine reviews.
![screenshot of dataframe showing totals for vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/total_vine_or_not.png)

__2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?__
As shown in the image below, there were 24 five-star Vine reviews and 4,475 non-Vine reviews.
![screenshot of dataframe showing totals for five-star reviews based on vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/total_five_star_paid_unpaid_percentage.png)

__3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?__
As shown in the image below, 55.8% of Vine reviews received five stars, and 57.4% of non-Vine reviews received five stars.
![screenshot of dataframe showing percentage of five-star reviews based on vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/total_five_star_paid_unpaid_count.png)

## Summary
Is there any positivity bias for reviews in the Vine program?

What's one additional analysis you could do with the dataset to support this statement?