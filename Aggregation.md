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

## 8. Top Earners

We define an employee's total earnings to be their monthly SALARY X MONTHS worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as 2 space-separated integers.

Input Format

The Employee table containing employee data for a company is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225412542-cad1715d-fe7c-4309-9be0-8a63d8544c98.png)

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is the their monthly salary.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/225412577-2597fa4d-552b-4209-a28d-0ba18132f497.png)

Sample Output

```
69952 1
```

Solution :

```sql
SELECT MAX(MONTHS*SALARY), COUNT(*) FROM EMPLOYEE
GROUP BY MONTHS*SALARY 
ORDER BY MONTHS*SALARY DESC LIMIT 1;
```

## 9. Weather Observation Station 2

Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of 2 decimal places.
The sum of all values in LONG_W rounded to a scale of 2 decimal places.
Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Output Format

Your results must be in the form:

```
lat lon
```

Solution :

```sql
SELECT ROUND(SUM(LAT_N),2), ROUND(SUM(LONG_W),2) FROM STATION;
```

## 10. Weather Observation Station 13

Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345. Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT ROUND(SUM(LAT_N),4) FROM STATION
WHERE LAT_N>38.7880 AND LAT_N<137.2345;
```

## 11. Weather Observation Station 14

Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than 137.2345. Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT ROUND(MAX(LAT_N),4) FROM STATION
WHERE LAT_N<137.2345;
```

## 11. Weather Observation Station 15

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than 137.2345 . Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT ROUND(LONG_W,4) FROM STATION
WHERE LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N < 137.2345);
```

## 12. Weather Observation Station 16

Query the smallest Northern Latitude (LAT_N) from STATION that is greater than 38.7780. Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT MIN(ROUND(LAT_N,4)) FROM STATION
WHERE LAT_N > 38.7780;
```

## 13. Weather Observation Station 17

Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than 38.7780. Truncate your answer to 4 decimal places.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT ROUND(LONG_W,4) FROM STATION
WHERE LAT_N = (SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780);
```

## 14. Weather Observation Station 18

Consider P1(a,b) and P2(c,d) to be two points on a 2D plane.

a happens to equal the minimum value in Northern Latitude (LAT_N in STATION).
b happens to equal the minimum value in Western Longitude (LONG_W in STATION).
c happens to equal the maximum value in Northern Latitude (LAT_N in STATION).
d happens to equal the maximum value in Western Longitude (LONG_W in STATION).
Query the Manhattan Distance between points P1 and P2 and round it to a scale of 4 decimal places.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT ROUND(ABS(MIN(LAT_N)-MAX(LAT_N)) + ABS(MIN(LONG_W)-MAX(LONG_W)), 4) FROM STATION;
```

## 15. Weather Observation Station 19

Consider P1(a,c) and P2(b,d) to be two points on a 2D plane.where (a,b) are the respective minimum and maximum values of Northern Latitude (LAT_N) and (c,d) are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION.

Query the Euclidean Distance between points P1 and P2 and format your answer to display 4 decimal digits.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/225469670-89991813-0a92-44de-8573-d41d7f73afe7.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Solution :

```sql
SELECT ROUND( SQRT (POWER(MAX(LAT_N)-MIN(LAT_N), 2) + POWER(MAX(LONG_W)-MIN(LONG_W),2 )),4) FROM STATION;
```
