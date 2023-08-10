## 1. Revising the Select Query I 

Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224453988-fdc06158-8c3d-452c-b0fb-b80d1f273085.png)

Solution : 

```sql
SELECT * FROM CITY WHERE POPULATION > 100000 AND COUNTRYCODE = 'USA';
```

## 2. Revising the Select Query II 

Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

The CITY table is described as follows: 

![image](https://user-images.githubusercontent.com/66794160/224454123-95453c17-db89-4a3b-aa3a-f22bfc8a32df.png)

Solution : 

```sql
SELECT NAME FROM CITY WHERE COUNTRYCODE = 'USA' AND POPULATION > 120000;
```

## 3. Select All

Query all columns (attributes) for every row in the CITY table.

The CITY table is described as follows: 

![image](https://user-images.githubusercontent.com/66794160/224454328-58556077-5a15-4958-9e98-cb202d890323.png)

Solution : 

```sql
SELECT * FROM CITY;
```

## 4. Select By ID

![image](https://user-images.githubusercontent.com/66794160/224454485-8eedac58-dad4-4319-9d4b-deb9655ef3a8.png)

Solution : 

```sql
SELECT * FROM CITY WHERE ID = 1661; 
```

## 5. Japanese Cities' Attributes 

Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454538-1323de32-e6f0-4803-8291-6f407e01d699.png)


Solution : 

```sql
SELECT * FROM CITY WHERE COUNTRYCODE = 'JPN';   
```

## 6. Japanese Cities' Names

Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454538-1323de32-e6f0-4803-8291-6f407e01d699.png)

Solution : 

```sql
SELECT NAME FROM CITY WHERE COUNTRYCODE = 'JPN';          
```

## 7. Weather Observation Station 1

Query a list of CITY and STATE from the STATION table.
The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454683-d07dcb48-d62c-4600-bd1d-c74a156b3a47.png)

Solution : 

```sql
SELECT CITY,STATE FROM STATION;       
```

## 8. Weather Observation Station 3

Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454774-ac8904ed-c215-4f00-a037-768b8b849d09.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION WHERE MOD(ID,2)=0 ORDER BY CITY ASC;            
```

## 9. Weather Observation Station 5

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.
The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

where LAT_N is the northern latitude and LONG_W is the western longitude.

Sample Input

For example, CITY has four entries: DEF, ABC, PQRS and WXY.

Sample Output

```
ABC 3
PQRS 4
```
Explanation

When ordered alphabetically, the CITY names are listed as ABC, DEF, PQRS, and WXY, with lengths  and . The longest name is PQRS, but there are  options for shortest named city. Choose ABC, because it comes first alphabetically.

Note
You can write two separate queries to get the desired output. It need not be a single query.


Solution : 

```sql
(SELECT CITY, length(CITY) FROM STATION 
ORDER BY length(CITY), CITY LIMIT 1) UNION
(SELECT CITY, length(CITY) FROM STATION 
ORDER BY length(CITY) DESC LIMIT 1);
```

## 10. Weather Observation Station 6

Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE CITY LIKE 'a%' OR CITY LIKE 'e%' OR CITY LIKE 'i%' OR CITY LIKE 'o%' OR CITY LIKE 'u%'
ORDER BY CITY 
```

## 11. Weather Observation Station 7

Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u'
ORDER BY CITY 
```

## 12. Weather Observation Station 8

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)


Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE (CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u') 
AND (CITY LIKE 'a%' OR CITY LIKE 'e%' OR CITY LIKE 'i%' OR CITY LIKE 'o%' OR CITY LIKE 'u%')
ORDER BY CITY 
```

## 13. Weather Observation Station 9

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE CITY NOT IN (SELECT DISTINCT CITY FROM STATION 
                   WHERE CITY LIKE 'a%' OR CITY LIKE 'e%' OR CITY LIKE 'i%' OR CITY LIKE 'o%' OR CITY LIKE 'u%')
ORDER BY CITY
```

## 14. Weather Observation Station 10

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE CITY NOT IN (SELECT DISTINCT CITY FROM STATION 
                   WHERE CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u')
ORDER BY CITY
```

## 15. Weather Observation Station 11

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE CITY NOT IN (SELECT DISTINCT CITY FROM STATION 
                    WHERE (CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u') 
                    AND (CITY LIKE 'a%' OR CITY LIKE 'e%' OR CITY LIKE 'i%' OR CITY LIKE 'o%' OR CITY LIKE 'u%'))
ORDER BY CITY ;
```

## 16. Weather Observation Station 12

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

Input Format

The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224455052-348af53d-0306-4dcb-855e-61b477e964e8.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION 
WHERE CITY NOT IN (SELECT DISTINCT CITY FROM STATION 
                    WHERE (CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u') 
                    OR (CITY LIKE 'a%' OR CITY LIKE 'e%' OR CITY LIKE 'i%' OR CITY LIKE 'o%' OR CITY LIKE 'u%'))
ORDER BY CITY ;
```

## 17. Higher Than 75 Marks

Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

Input Format

The STUDENTS table is described as follows:  

![image](https://user-images.githubusercontent.com/66794160/224459244-7608d267-79f9-4525-8dfb-1ad66694c763.png)

The Name column only contains uppercase (A-Z) and lowercase (a-z) letters.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224459262-48e2745e-8ac6-41e2-b7a6-6727f3a13513.png)

Sample Output

```
Ashley
Julia
Belvet
```

Explanation

Only Ashley, Julia, and Belvet have Marks > 75 . If you look at the last three characters of each of their names, there are no duplicates and 'ley' < 'lia' < 'vet'.

Solution : 

```sql
SELECT NAME FROM STUDENTS 
WHERE MARKS > 75
ORDER BY SUBSTR(NAME,LENGTH(NAME)-2,3), ID;
```
## 18. Employee Names

Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Input Format

The Employee table containing employee data for a company is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224460518-50938a98-193f-4a9e-b362-252820dd6545.png)

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224460535-896ede2f-58ac-44c2-a154-1e8792cb8d7e.png)

Sample Output

```
Angela
Bonnie
Frank
Joe
Kimberly
Lisa
Michael
Patrick
Rose
Todd
```

Solution : 

```sql
SELECT NAME FROM EMPLOYEE 
ORDER BY NAME;
```

## 19. Employee Salaries

Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.

Input Format

The Employee table containing employee data for a company is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224460518-50938a98-193f-4a9e-b362-252820dd6545.png)

where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224460709-3c3d306e-999b-42d8-a972-c0c55531ebd0.png)

Sample Output

```
Angela
Michael
Todd
Joe
```

Solution : 

```sql
SELECT NAME FROM EMPLOYEE 
WHERE SALARY > 2000 AND MONTHS < 10
ORDER BY EMPLOYEE_ID;
```



