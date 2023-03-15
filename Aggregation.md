## 1. Revising Aggregations - The Count Function

Query a count of the number of cities in CITY having a Population larger than 100,000.

Input Format

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224531223-f39e27dd-5ad3-4d13-a0a8-9e3158833fe1.png)

Solution :

```sql
SELECT COUNT(ID) FROM CITY
WHERE POPULATION > 100000;
```

## 2. Revising Aggregations - The Sum Function

Query the total population of all cities in CITY where District is California.

Input Format

The CITY table is described as follows: 

![image](https://user-images.githubusercontent.com/66794160/224604792-579a2301-df4b-4445-88ea-6d6622c0e5af.png)

Solution :

```sql
SELECT SUM(POPULATION) FROM CITY
WHERE DISTRICT = 'CALIFORNIA';
```
## 3. Revising Aggregations - Averages

Query the average population of all cities in CITY where District is California.

Input Format

The CITY table is described as follows: 

![image](https://user-images.githubusercontent.com/66794160/224604792-579a2301-df4b-4445-88ea-6d6622c0e5af.png)

Solution :

```sql
SELECT AVG(POPULATION) FROM CITY
WHERE DISTRICT = 'CALIFORNIA';
```

## 4. Average Population

Query the average population for all cities in CITY, rounded down to the nearest integer.

Input Format

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224604792-579a2301-df4b-4445-88ea-6d6622c0e5af.png)

Solution :

```sql
SELECT ROUND(AVG(POPULATION)) FROM CITY;
```

## 5. Japan Population

Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

Input Format

The CITY table is described as follows

![image](https://user-images.githubusercontent.com/66794160/224604792-579a2301-df4b-4445-88ea-6d6622c0e5af.png)

Solution :

```sql
SELECT SUM(POPULATION) FROM CITY
WHERE COUNTRYCODE='JPN';
```

## 6. Population Density Difference

Query the difference between the maximum and minimum populations in CITY.

Input Format

The CITY table is described as follows: 

![image](https://user-images.githubusercontent.com/66794160/224604792-579a2301-df4b-4445-88ea-6d6622c0e5af.png)

Solution :

```sql
SELECT ( MAX(POPULATION) - MIN(POPULATION) ) FROM CITY;
```

## 7. The Blunder

Samantha was tasked with calculating the average monthly salaries for all employees in the EMPLOYEES table, but did not realize her keyboard's  key was broken until after completing the calculation. She wants your help finding the difference between her miscalculation (using salaries with any zeros removed), and the actual average salary.

Write a query calculating the amount of error (i.e.:  average monthly salaries), and round it up to the next integer.

Input Format

The EMPLOYEES table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224605979-00f0b429-ea8a-4147-b72c-e3605d57c519.png)

Note: Salary is per month.

Constraints
1000 < SALARY < 10^5

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224606018-9ea0d4d9-c2ed-4e0c-a528-62bea9bb1f92.png)

Sample Output

```
2061
```

Solution :

```sql
SELECT CEIL( AVG(MISCALC) -  AVG (WRONG) ) FROM 
(SELECT CAST(SALARY AS CHAR) AS MISCALC, REPLACE(SALARY, '0', '') AS WRONG FROM EMPLOYEES) AS DIFF ; 
```
