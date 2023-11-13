In this project I walk through SQL queries to run EXLORATORY data analysis about the occured accidents. I used MS SQL Server to answer 8 SQL queries in order to have better insights and have better image about the data. The whole project showcases Aggregation & Group By statements, changing columns data types, Trended Analysis / Subquery in a FROM clause, Pivoting into columns, Defining and setting variables to filter data, Categoring / Labelling data into a new column by using CASE WHEN THEN ELSE END AS statements.
The below code is the answer to Question 3 
-- Can you identify any trends in accidents based on the age of vehicle involved?
SELECT Agegroup, COUNT(accidentindex) AS 'Total Number of Accidents', AVG(agevehicle) AS 'AVG Vehicle Age' FROM
(SELECT accidentindex, agevehicle,
CASE 
	WHEN agevehicle between 0 and 5 then 'New'
	WHEN agevehicle between 6 and 10 then 'Regular'
ELSE 'Old'
END AS 'AgeGroup'
FROM vehicle) AS SUBQUERY
GROUP BY AgeGroup
