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
