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
