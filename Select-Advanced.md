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

