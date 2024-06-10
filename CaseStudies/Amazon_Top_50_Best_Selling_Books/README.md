
**Data analysis on Amazon Top 50 Best Selling Books**


## Purpose

This is my capstone project of the Google Data Analytics Professional Certificate which I followed through Coursera. Under this project, I access the public dataset provided by a fictional company.I will share my insights and provide informed recommendations on the marketing strategies that will contribute to the company’s remarkable success.In this project, following steps will be followed: **Ask, Prepare, Process, Analyze, Share, Act.**

## Ask

The primary goal is to comprehend how fiction and non-fiction books perform on the Amazon platform through historical bestseller data. This knowledge empowers the marketing team to develop targeted strategies for promoting client books, considering genre-specific characteristics. By analyzing past data, we aim to identify trends and factors influencing a book's climb to bestseller status. These insights will be compiled into actionable recommendations presented to the executive team for approval.


## Prepare

The dataset utilized in this case study can be accessed through the following link: https://www.kaggle.com/datasets/sootersaalu/amazon-top-50-bestselling-books-2009-2019 

Data Source: Historical Amazon bestseller data containing information like:



*   Book Title
*   Author
*   User Rating
*   Number of Reviews
*   Price
*   Year Published
*   Genre (Fiction/Non-fiction)

## Process

During this stage, the focus is on data cleansing and preparation. Within this phase, the following steps were undertaken:

## Analyze

Having completed the preparation and processing of the data, we can now proceed with the analysis phase. The objective of this phase is to identify patterns and extract valuable insights from the data.


### **1.Comparison between Fiction and NonFiction**

In this, we are in the process of identifying the number of Fiction and NonFiction.. 


#### The SQL query that is used for this is as follows:


```
SELECT Genre, COUNT(Genre) as count
FROM bestsellers
GROUP BY Genre;
```



#### Corresponding dashboard:
![Chart](https://github.com/ChilupuriArchana/Portfolio/blob/main/CaseStudies/Amazon_Top_50_Best_Selling_Books/images/1.png?raw=true)

#### Observation

It is evident from the data that the majority are non fiction books.
