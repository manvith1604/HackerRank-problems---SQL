1. Revising the Select Query I

Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224453988-fdc06158-8c3d-452c-b0fb-b80d1f273085.png)

Solution : 

```sql
SELECT * FROM CITY WHERE POPULATION > 100000 AND COUNTRYCODE = 'USA';
```

2. Revising the Select Query II

Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454123-95453c17-db89-4a3b-aa3a-f22bfc8a32df.png)

Solution : 

```sql
SELECT NAME FROM CITY WHERE COUNTRYCODE = 'USA' AND POPULATION > 120000;
```

3. Select All

Query all columns (attributes) for every row in the CITY table.

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454328-58556077-5a15-4958-9e98-cb202d890323.png)

Solution : 

```sql
SELECT * FROM CITY;
```

4. Select By ID

![image](https://user-images.githubusercontent.com/66794160/224454485-8eedac58-dad4-4319-9d4b-deb9655ef3a8.png)

Solution : 

```sql
SELECT * FROM CITY WHERE ID = 1661; 
```

5. Japanese Cities' Attributes

Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.

The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454538-1323de32-e6f0-4803-8291-6f407e01d699.png)


Solution : 

```sql
SELECT * FROM CITY WHERE COUNTRYCODE = 'JPN';   
```

6. Japanese Cities' Names

Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN.
The CITY table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454538-1323de32-e6f0-4803-8291-6f407e01d699.png)

Solution : 

```sql
SELECT NAME FROM CITY WHERE COUNTRYCODE = 'JPN';          
```

7. Weather Observation Station 1

Query a list of CITY and STATE from the STATION table.
The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454683-d07dcb48-d62c-4600-bd1d-c74a156b3a47.png)

Solution : 

```sql
SELECT CITY,STATE FROM STATION;       
```

8. Weather Observation Station 3

Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
The STATION table is described as follows:

![image](https://user-images.githubusercontent.com/66794160/224454774-ac8904ed-c215-4f00-a037-768b8b849d09.png)

Solution : 

```sql
SELECT DISTINCT CITY FROM STATION WHERE MOD(ID,2)=0 ORDER BY CITY ASC;            
```



