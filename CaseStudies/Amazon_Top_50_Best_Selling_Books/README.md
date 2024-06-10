
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

### **2.Fiction and NonFiction YoY**


### This section will examine fiction and non-fiction books year over year.


### The SQL query that is used for this is as follows:


```
SELECT Year,Genre,COUNT(Genre) as count
FROM bestsellers
GROUP By Year,Genre;

```



#### Corresponding dashboard:

![Chart](https://github.com/ChilupuriArchana/Portfolio/blob/main/CaseStudies/Amazon_Top_50_Best_Selling_Books/images/2.png?raw=true)



#### Observation

Our empirical observations reveal a significant preference for non fiction books compared to fiction books.We can observe that from 2009 to 2010 there is decrease in fiction books then in 2014 increased after that decreased.We can observe that from 2009 to 2010 there is increase in non-fiction books then in 2014 decreased after that increased.


### 3.Top 10 authors with the highest number of selling books

This section will explore the top 10 authors with the highest number of selling books


#### The SQL query that is used for this is as follows:


```
SELECT Author,COUNT(Name) as 'Number of Best Selling Books'
FROM bestsellers
GROUP BY Author
ORDER BY count(Name) desc
OFFSET 0 ROWS FETCH NEXT 10 ROWS ONLY;
```



#### Corresponding dashboard:

![Chart](https://github.com/ChilupuriArchana/Portfolio/blob/main/CaseStudies/Amazon_Top_50_Best_Selling_Books/images/3.png?raw=true)


#### Observation

The dashboards illustrate the famous authors.


### 4.The total number of reviews in YoY.


### This section will explore the total number of reviews year over year for fiction and non-fiction books..


#### The SQL query that is used for this is as follows:


```
SELECT Year,Genre,SUM(Reviews) as total_number_of_reviews
FROM bestsellers
GROUP BY Year,Genre
ORDER BY Genre,SUM(Reviews) DESC

```



#### Corresponding dashboard:

![Chart](https://github.com/ChilupuriArchana/Portfolio/blob/main/CaseStudies/Amazon_Top_50_Best_Selling_Books/images/4.png?raw=true)



#### Observation

The dashboards illustrate that fiction books have more reviews compared to non-fiction books.


### 5.Average user rating of fiction and nonfiction books YoY

This section will explore the average rating of fiction and non-fiction books year over year

The SQL query that is used for this is as follows:


```
SELECT Year,Genre,ROUND(AVG(User_Rating),2) as total_user_rating
FROM bestsellers
GROUP BY Year,Genre
ORDER BY Genre,total_user_rating 

```



#### Corresponding dashboard:

![Chart](https://github.com/ChilupuriArchana/Portfolio/blob/main/CaseStudies/Amazon_Top_50_Best_Selling_Books/images/5.png?raw=true)



#### Observation

The dashboards provide a clear representation of the data. It can be inferred that ratings for fiction are more compared to non fiction.


