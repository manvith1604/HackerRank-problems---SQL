## 1. Population Census

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format

The CITY and COUNTRY tables are described as follows:

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/38dbddaf-2bd8-4595-9662-96ea918b0930)

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/b410cc7a-cd43-4104-9196-483e10bb5ea1)

Solution: 

```sql
SELECT SUM(CI.POPULATION) FROM CITY CI, COUNTRY CO
WHERE CI.COUNTRYCODE = CO.CODE AND CO.CONTINENT = 'Asia';
```

## 2. African Cities

Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format

The CITY and COUNTRY tables are described as follows: 

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/2f4e7ba7-24c4-47d0-bc03-11d08862c0a9)

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/7eec1204-0652-47d0-bfc1-1ae915135878)

Solution: 

```sql
SELECT CI.NAME FROM CITY CI, COUNTRY CO
WHERE CI.COUNTRYCODE = CO.CODE AND CO.CONTINENT = 'Africa';
```

## 3. Average Population of Each Continent

Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

Input Format

The CITY and COUNTRY tables are described as follows:

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/2f4e7ba7-24c4-47d0-bc03-11d08862c0a9)

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/7eec1204-0652-47d0-bfc1-1ae915135878)

Solution: 

```sql
SELECT CO.CONTINENT, FLOOR(AVG(CI.POPULATION)) FROM CITY CI, COUNTRY CO
WHERE CI.COUNTRYCODE = CO.CODE 
GROUP BY CO.CONTINENT;
```

## 4. The Report

You are given two tables: Students and Grades. Students contains three columns ID, Name and Marks.

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/5bf4e18a-ecb0-451e-aa94-7b89ed40a40b)

Grades contains the following data:

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/0c01ab0d-badf-4529-bcb8-55e820cdef1c)

Ketty gives Eve a task to generate a report containing three columns: Name, Grade and Mark. Ketty doesn't want the NAMES of those students who received a grade lower than 8. The report must be in descending order by grade -- i.e. higher grades are entered first. If there is more than one student with the same grade (8-10) assigned to them, order those particular students by their name alphabetically. Finally, if the grade is lower than 8, use "NULL" as their name and list them by their grades in descending order. If there is more than one student with the same grade (1-7) assigned to them, order those particular students by their marks in ascending order.

Write a query to help Eve.

Sample Input

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/50add442-4da2-4567-ad4c-8f85de8617bd)

Sample Output

```
Maria 10 99
Jane 9 81
Julia 9 88 
Scarlet 8 78
NULL 7 63
NULL 7 68
```

Note

Print "NULL"  as the name if the grade is less than 8.
 
Explanation

Consider the following table with the grades assigned to the students:

![image](https://github.com/manvith1604/HackerRank-problems---SQL/assets/66794160/deef4f6b-a5b5-415a-8c11-da30f5a1e398)

So, the following students got 8, 9 or 10 grades:

Maria (grade 10)
Jane (grade 9)
Julia (grade 9)
Scarlet (grade 8)


Solution: 

```sql
SELECT CO.CONTINENT, FLOOR(AVG(CI.POPULATION)) FROM CITY CI, COUNTRY CO
WHERE CI.COUNTRYCODE = CO.CODE 
GROUP BY CO.CONTINENT;
```
