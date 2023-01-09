# Amazon Vine Analysis
Data bootcamp week 17 - big data and AWS

## Overview
This independent challenge exercise involved selecting a product-specific dataset of Amazon reviews; using PySpark to extract and transform the data; connecting to an AWS Relational Database Service (RDS); and loading the data into pgAdmin. I chose a dataset with [book reviews](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Books_v1_02.tsv.gz).


The dataset included a column about whether the reviewer was part of the [Amazon Vine program](https://www.amazon.com/vine/about). This column allows for comparison between paid and unpaid reviews. A second part of the challenge was to examine the data for bias based on participation in the Amazon Vine program.

## Results
The database included several tables, one of which had information about whether a review was part of the Vine Program. I exported that table from pgAdmin to Pandas for analysis. As specified in the challenge instructions, I refined the Vine program data as follows:

* Filtered out all rows where the total number of votes was less than 20.
![screenshot of dataframe showing filter for total number of votes >=20](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/filter1.png)

* From there, filtered for rows where the the number of "helpful votes" was at least 50% of the total votes.
![screenshot of dataframe showing filter for helpful votes / total number](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/filter2.png)

* From there, created separate dataframes based on participation in the Vine program.
![screenshot of dataframe showing filters for vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/filter3.png)

After these filtering steps, I was able to answer the following questions.

__1. How many Vine reviews and non-Vine reviews were there?__

As shown in the image below, there were 43 Vine reviews and 7,791 non-Vine reviews.
![screenshot of dataframe showing totals for vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/total_vine_or_not.png)

__2. How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?__

As shown in the image below, there were 24 five-star Vine reviews and 4,475 non-Vine reviews.
![screenshot of dataframe showing totals for five-star reviews based on vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/total_five_star_paid_unpaid_count.png)

__3. What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?__

As shown in the image below, 55.8% of Vine reviews received five stars, and 57.4% of non-Vine reviews received five stars.
![screenshot of dataframe showing percentage of five-star reviews based on vine = Y and vine = n](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/total_five_star_paid_unpaid_percentage.png)

## Summary
The aim of the analysis described in the Results section was to see if there was bias based on participation in the Amazon Vine program. That is, did participation in the Vine program result in more positive reviews? It's an important question, because payment could very easily influence a reviewer's perception of a product.

For the book dataset analyzed here for five-star reviews, there does not appear to be a positivity bias from the Vine program. If there were positivity bias, we would expect to see a greater percentage of Vine reviews with five stars than in the non-Vine reviews. But at 55.8% (Vine) and 57.4% (non-Vine), the difference is slight.

### Further Analysis
Five-star ratings are not the only indication of positivity, though. As shown below, there are differences in how the ratings are distributed. No Vine review received less than three stars, while 16% of the non-Vine reviews (1,245 out of 7,791) received one or two stars. So although it does not appear that Vine reviewers are more likely to give five stars, they do seem less likely to give lower ratings. 

![screenshot of dataframe showing count of each number of stars, for paid vs unpaid reviews](https://github.com/larabjork/amazon-vine-analysis/blob/main/images/paid_not_count_star_type.png)

Further analysis should involve similar studies from other datasets, to understand whether the distribution of star ratings is the same for the Vine program across all product categories, or is it specific to any subset of categories, when compared to non-Vine program reviews. 