# Big Data: Amazon Vine Reviews Analysis
## Analysis Overview
### Purpose

To analyze the Amazon reviews of the product, of which in this project is the dataset of the luggage sold on Amazon, in order to determine the favourableness of those reviews which was written by the members of the Amazon Vine program (who receives product in exchange for the review). The ETL (Extract, Transform, Load) process is performed using PySpark on the raw dataset stored on the cloud database Amazon Web Service (AWS RDS), and the transformed dataset is loaded to the postgres database.


### Resources
+ **Languages:** PySpark, SQL
+ **Cloud-based notebook:** Google Colaboratory (Google Colab Notebook)
+ **Database platform:** Amazon Web Service (AWS)-RDS, PostgresSQL (pgAdmin)
+ **Raw Dataset:** Luggage's review dataset from [Amazon Product Review Datasets](https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt)


## Analysis Results

### 1. ETL Process (Deliverable 1)
+ **Script:** [Amazon_Reviews_ETL.ipynb](https://github.com/asama-w/Amazon_Vine_Analysis/blob/main/Amazon_Reviews_ETL.ipynb) 
+ The raw dataset of the review is extracted from the cloud database Amazon Web Service (AWS RDS), transformed using PySpark on Google Colab Notebook, and the final-transformed dataset is loaded to the pgAdmin as a postgres database. 

### 2. Bias of Vine Reviews Analysis (Deliverable 2)
+ **Script:** [Vine_Review_Analysis.ipynb](https://github.com/asama-w/Amazon_Vine_Analysis/blob/main/Vine_Review_Analysis.ipynb) 
+ There are 2 types of the Amazon product's reviews: Vine, and Non-Vine:
	+ **Vine (Paid):** reviews written by the members of the paid Amazon Vine program, whose products are sent by the manufacturers in turn for publishing a review.
	+ **Non-Vine (Unpaid):** reviews written by other customers who are not a part of the program.
+ To determine the trends of the vine reviews, and non-vine reviews, the reviews in the above transformed dataset (deliverable 1) is filtered before being analyzed by the following conditions to select reviews that are more likely helpful:
	+ Total votes count is equal to or greater than 20.
	+ Percentage of helpful votes is equal to or greater than 50.
+ This analysis of vine review favourable trend is performed using PySpark on Google Colab Notebook. 

#### Results
The following image shows the summary table of the review, categorized by Vine and Non-Vine type.
<img src= https://github.com/asama-w/Amazon_Vine_Analysis/blob/main/Additional_images/review_summary.png width="90%" height="90%">

+ There the total of **21 reviews** which are from **vine program (paid)**, and **6,690 reviews** which are **non-vine (unpaid)**.
+ **Vine (Paid)**: 10 out of 21 reviews or **47.62%** of the total vine reviews are the **5-star reviews**.
+ **Non-Vine (Unpaid):** 3,448 out of 6,690 reviews or **51.52%** of the total non-vine reviews are the **5-star reviews**.


## Analysis Summary

To conclude, based on the analysis's filtered dataset, the reviews are rather neutral, there is no positivity bias for the paid-reviews in the Vine program as 47.62% of the vine's reviews are 5-star, which is less than 50%. However, since the number of the vine's reviews are significantly smaller than the number of the non-vine's or the unpaid reviews, this conclusion on the bias aspect can be vague and may need more information about the reviews to uncover more trends. We can determine the average of the star rating to see if the reviews are on a positive or negative side, or perform the similar analysis on all of the reviews without filtering any review out to see whether the bias trend will change or not. We can also look into the vine program to find out the reason behind their small numbers of reviews.

The following image shows the average of the star-rating. From this information, the average star of vine's reviews is 4.3 out of 5, it can be now considered that there may be a positive bias towards the vine's review. Nevertheless, more analysis may be needed to support this.

<img src= https://github.com/asama-w/Amazon_Vine_Analysis/blob/main/Additional_images/avg_star_rating.png width="30%" height="30%">
