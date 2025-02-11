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
We use the (ORDER BY) function to sort the cinemas available in a ascending or descending order, as for our case we want to see the highest so we use DESC order and limit our results
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

