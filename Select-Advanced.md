## 1. The PADS

Generate the following two result sets:

Query an alphabetically ordered list of all names in OCCUPATIONS, immediately followed by the first letter of each profession as a parenthetical (i.e.: enclosed in parentheses). For example: AnActorName(A), ADoctorName(D), AProfessorName(P), and ASingerName(S).
Query the number of ocurrences of each occupation in OCCUPATIONS. Sort the occurrences in ascending order, and output them in the following format:
```
There are a total of [occupation_count] [occupation]s.
```

where [occupation_count] is the number of occurrences of an occupation in OCCUPATIONS and [occupation] is the lowercase occupation name. If more than one Occupation has the same [occupation_count], they should be ordered alphabetically.  

Note: There will be at least two entries in the table for each type of occupation.

Input Format

![image](https://user-images.githubusercontent.com/66794160/224460880-b8e95bf8-83ca-46f2-ad5e-41d4272dcbb2.png)

The OCCUPATIONS table is described as follows:  Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

Sample Input

An OCCUPATIONS table that contains the following records:

![image](https://user-images.githubusercontent.com/66794160/224460904-82ee6cdf-afc9-4852-a228-067587f36911.png)

Sample Output 

```
Ashely(P)
Christeen(P)
Jane(A)
Jenny(D)
Julia(A)
Ketty(P)
Maria(A)
Meera(S)
Priya(S)
Samantha(D)
There are a total of 2 doctors.
There are a total of 2 singers.
There are a total of 3 actors.
There are a total of 3 professors.
```
Explanation

The results of the first query are formatted to the problem description's specifications.
The results of the second query are ascendingly ordered first by number of names corresponding to each profession (2<=2<=3<=3), and then alphabetically by profession (doctor<=singer, and actor<=professor). 

Solution : 

```sql
(SELECT CONCAT(NAME, '(', SUBSTRING(OCCUPATION, 1, 1), ')' ) AS NAMES
FROM OCCUPATIONS) 
UNION
(SELECT CONCAT('There are a total of ', COUNT(OCCUPATION),' ', LOWER(OCCUPATION), 's.' ) 
FROM OCCUPATIONS 
GROUP BY OCCUPATION)
ORDER BY NAMES ASC;
```

## 2. Occupations

Pivot the Occupation column in OCCUPATIONS so that each Name is sorted alphabetically and displayed underneath its corresponding Occupation. The output column headers should be Doctor, Professor, Singer, and Actor, respectively.

Note: Print NULL when there are no more names corresponding to an occupation.

Input Format

The OCCUPATIONS table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224525356-965b481f-d8bc-4ce4-9922-83a531f9be78.png)

Occupation will only contain one of the following values: Doctor, Professor, Singer or Actor.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224525360-07d9005e-3c9f-40b8-a2b7-300d307e97a2.png)

Sample Output

```
Jenny    Ashley     Meera  Jane
Samantha Christeen  Priya  Julia
NULL     Ketty      NULL   Maria
```

Explanation

The first column is an alphabetically ordered list of Doctor names.
The second column is an alphabetically ordered list of Professor names.
The third column is an alphabetically ordered list of Singer names.
The fourth column is an alphabetically ordered list of Actor names.
The empty cell data for columns with less than the maximum number of names per occupation (in this case, the Professor and Actor columns) are filled with NULL values.

Solution : 

```sql
CREATE VIEW PROFESSION AS (
    SELECT 
        CASE WHEN OCCUPATION = 'Doctor' THEN NAME END AS 'Doctor',
        CASE WHEN OCCUPATION = 'Professor' THEN NAME END AS 'Professor',
        CASE WHEN OCCUPATION = 'Singer' THEN NAME END AS 'Singer',
        CASE WHEN OCCUPATION = 'Actor' THEN NAME END AS 'Actor',
        ROW_NUMBER() OVER (PARTITION BY OCCUPATION ORDER BY NAME) as CATEGORY
    FROM OCCUPATIONS
);
SELECT MAX(Doctor),MAX(Professor),MAX(Singer),MAX(Actor) FROM PROFESSION 
GROUP BY CATEGORY
```
## 3.Binary Tree Nodes

You are given a table, BST, containing two columns: N and P, where N represents the value of a node in Binary Tree, and P is the parent of N.

![image](https://user-images.githubusercontent.com/66794160/224525942-a5e52a1a-a70f-4b8e-a8bb-efbfa9115b0b.png)

Write a query to find the node type of Binary Tree ordered by the value of the node. Output one of the following for each node:

Root: If node is root node.
Leaf: If node is leaf node.
Inner: If node is neither root nor leaf node.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224525964-1972dd13-7a9e-4f47-bdfe-8f80fc31cfab.png)

Sample Output
```
1 Leaf
2 Inner
3 Leaf
5 Root
6 Leaf
8 Inner
9 Leaf
```

Explanation

The Binary Tree below illustrates the sample:

![image](https://user-images.githubusercontent.com/66794160/224525989-d50a0da9-4268-4568-bdd2-6afaf724e150.png)

Solution :

```sql
SELECT N, 
CASE WHEN P IS NULL THEN 'Root' 
WHEN N NOT IN (SELECT DISTINCT P FROM BST WHERE P IS NOT NULL) 
THEN 'Leaf' ELSE 'Inner' 
END AS RESULT FROM BST 
ORDER BY N;
```

## 4. New Companies

Amber's conglomerate corporation just acquired some new companies. Each of the companies follows this hierarchy: 

![image](https://user-images.githubusercontent.com/66794160/224526064-d18813e0-3a69-41e2-a86d-f52045f17b9a.png)

Given the table schemas below, write a query to print the company_code, founder name, total number of lead managers, total number of senior managers, total number of managers, and total number of employees. Order your output by ascending company_code.

Note:

The tables may contain duplicate records.
The company_code is string, so the sorting should not be numeric. For example, if the company_codes are C_1, C_2, and C_10, then the ascending company_codes will be C_1, C_10, and C_2.

Solution :

```sql
SELECT C.COMPANY_CODE, C.FOUNDER,
       COUNT(DISTINCT L.LEAD_MANAGER_CODE),
       COUNT(DISTINCT S.SENIOR_MANAGER_CODE),
       COUNT(DISTINCT M.MANAGER_CODE),
       COUNT(DISTINCT E.EMPLOYEE_CODE)
FROM COMPANY AS C 
JOIN LEAD_MANAGER AS L 
ON C.COMPANY_CODE = L.COMPANY_CODE
JOIN SENIOR_MANAGER AS S
ON L.LEAD_MANAGER_CODE = S.LEAD_MANAGER_CODE
JOIN MANAGER AS M 
ON M.SENIOR_MANAGER_CODE = S.SENIOR_MANAGER_CODE
JOIN EMPLOYEE AS E
ON E.MANAGER_CODE = M.MANAGER_CODE
GROUP BY C.COMPANY_CODE, C.FOUNDER
ORDER BY C.COMPANY_CODE;
```

## 5. Type of Triangle

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.
Input Format

The TRIANGLES table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224529732-1bb2ec8d-0df0-4162-99d1-0143e29e0a03.png)

Each row in the table denotes the lengths of each of a triangle's three sides.

Sample Input

![image](https://user-images.githubusercontent.com/66794160/224529739-52e2896d-7002-4bf8-a802-013b6ae48e5b.png)

Sample Output
```
Isosceles
Equilateral
Scalene
Not A Triangle
```
Solution : 

```sql
SELECT 
    CASE 
        WHEN (A = B AND B = C) THEN "Equilateral"
        WHEN (A + B <= C OR A + C <= B OR B + C <= A) THEN "Not A Triangle"
        WHEN (A = B AND B <> C) OR (A = C AND C <> B) OR (B = C AND C <> A) THEN "Isosceles"
        WHEN (A <> B AND B <> C) THEN "Scalene"
    END AS TRIANGLE
FROM TRIANGLES;
```
