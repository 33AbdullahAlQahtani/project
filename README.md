# Project for Advanced Coding for AI & Databases
The project focuses on the writing queries in MySQL for our database that focuses on overall cenimas in The Kingdom of Saudi Arabia

# 1. :wrench: Creating our Database & Using it

```diff
CREATE DATABASE project;
```
![image](https://github.com/user-attachments/assets/9ce27be6-0f8c-4017-a7a3-3f324e19e289)

#Importing our Data into MySQL and Use it
afterwards we import our data into the database and use it so our queries will be tied to the given data from our database
Step 1: We right click on our Database/Schema and click on the option titled "Table Data Import Wizard"
![image](https://github.com/user-attachments/assets/85fb8b6f-97f5-4720-9acf-5a7f4f6e1c14)

Step 2: Then select the path of our csv/data file
![image](https://github.com/user-attachments/assets/63def7f5-a877-44d8-b117-5e203ff0bcfc)

Step 3: After clicking next lets name it
![image](https://github.com/user-attachments/assets/e8cbc3e1-63cc-4f10-ad36-d50163dbea7b)

Step 4: Now use the table to tie our queries to the data inside of the table
```diff
USE cinema;
```

# 2 :pencil2: Writing Our Queries/Functions/Triggers

In this part, it will be split into subtitles to make the it more organized, as this part is the backbone of the project which will provide the code of our queries
and the output of our queries

## 2.1 Find the top 5 Cinema with the Highest Rating
We use the |ORDER BY| function to sort the cinemas available in a ascending or descending order, as for our case we want to see the highest so we use DESC order and limit our results
using (limit 5;)
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT *
FROM cinema
ORDER BY rating DESC
LIMIT 5;
```
![image](https://github.com/user-attachments/assets/cd71a454-7afa-461f-9752-b3a90d9fee55)

## 2.2 Calculate the Sum of Reviews Perspective to the Rating and Order them By the Most to Least
For this query, we use the aggregate function of MySQL |SUM()| and |GROUP BY| to group the reviews respective to their ratings
and then we use |ORDER BY| to show them from the most reviews per rating to their least
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT rating, SUM(review_count) AS 'Total Reviews'
FROM cinema
GROUP BY rating
ORDER BY 'Total Reviews' DESC;
```
![image](https://github.com/user-attachments/assets/11a69e57-ea42-4189-96d3-5e1356771ce7)

## 2.3 Top 5 Cinemas with the Most Comments
This query require the use of |COUNT()|, |ORDER BY|, |LIMIT|, |GROUP BY|
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT name, COUNT(best_comment) AS comment_count
FROM cinema
GROUP BY name
ORDER BY comment_count DESC
LIMIT 5;
```
![image](https://github.com/user-attachments/assets/39abbfe8-daf2-482a-82cc-f4801bd02cb9)

## 2.4 Finding Cinemas Located in Jubail City
To do such a query, its really simple, we just use the condition |WHERE| With |LIKE|, as we are specifiying a condition to find something LIKE our condition
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT *
FROM cinema
WHERE name LIKE '%Jubail%';
```
![image](https://github.com/user-attachments/assets/d99f77ec-cace-44bf-b4b4-3bb79d0bb1cd)

## 2.5 Finding Cinemas with Rating Less than or Equal 3 in Riyadh
For this one, we use the condition statement |WHERE| and |LIKE|
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT name, rating, location
FROM cinema
WHERE rating <= 3 AND location LIKE '%Riyadh%';
```
![image](https://github.com/user-attachments/assets/dda58392-ac39-49ee-9ef1-9ae7aa51a00d)

## 2.6 Counting the Amount of VOX Cinemas Available in Our Table
USING aggregate |COUNT()| function and |WHERE/LIKE| we can determine how man vox cinema halls available or present in our data set
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT COUNT(name) AS count_name
FROM cinema
WHERE name LIKE '%VOX%' OR '%vox%';
```
![image](https://github.com/user-attachments/assets/b9805695-31b2-4b03-8e04-a530bd135a5a)

## 2.7 Counting the Amount of Cinema Halls per Genre From The Most to the Least
Same as our step of 2.6 functions but without a |WHERE| condition, and rather a |GROUP BY| and |ORDER BY|
```diff
USE project;
-- Abdullah Al-Qahtani
SELECT genre, COUNT(*) AS cinema_count
FROM cinema
GROUP BY genre
ORDER BY cinema_count DESC;
```
![image](https://github.com/user-attachments/assets/f995987a-4804-45cc-a31f-db0618db67b6)

## 2.8 Creating a Function if the Cinema have an Odd or Even Rating
For this we are creating a function by the following template:
(DELIMITER$$
CREATE FUNCTION function_name(variable)
RETURNS data_type
DETERMINISTIC
BEGIN
    RETURNS variable/condition;
END$$
DELIMITER ;)
```diff
USE project;
-- Abdullah Al-Qahtani
DELIMITER $$
CREATE FUNCTION ratingoddoreven(x INT)
RETURNS VARCHAR(5)
DETERMINISTIC
BEGIN
	RETURN IF(x % 2 = 0, 'Even', 'Odd');
END$$
DELIMITER ;
```
Deploying our Function:
```diff
SELECT name, rating, ratingoddoreven(rating) AS RatingOddorEven
FROM cinema
```
![image](https://github.com/user-attachments/assets/a1454d7f-e3ec-4025-b2d4-dc9d43483b01)
