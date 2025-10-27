# Urban-Areas-Access-To-Public-Transportation
Proportion of population that has convenient access to public transport, by sex, age and persons with disabilities.

This dataset was gotten from [UN-HABITAT](https://data.unhabitat.org/pages/urban-transport)

## Overview
This dataset has an estimate percentage representation of how much access citizens' of various countries and territories/regions have to public transport. The criteria used to help determine the percentage estimates was by how accessible the access stops were to the public going upto 500 metres walking distance (for low capacity public transport systems) and upto 1000 metres (for high capacity public transport systems).
- I use MySQL to gather insights represented in the dataset.

## Analysis
- The data represented in the dataset was collected between 2012-2023, with 2020 being the year when most of the data was collected - having 2076 records out of the 2353 records present in the dataset (88%).
```sql
SELECT DISTINCT 
	DataReferenceYear, 
    COUNT(DataReferenceYear),
    ROUND((COUNT(DataReferenceYear)/(SELECT COUNT(*) FROM city_public_transport_access))*100, 2)
FROM city_public_transport_access
GROUP BY DataReferenceYear
ORDER BY DataReferenceYear;
```

<img width="422" height="265" alt="image" src="https://github.com/user-attachments/assets/649c176a-d4a0-4a28-9123-66bbccf7048d" />

- The Countries Top 10 leading interms of the score of how accessible public transport is to the public are:
  - Singapore - 99.9% Access
  - Israel - 99.8% Access
  - Maldives - 99% Access
  - Estonia- 98.25% Access
  - Liechtenstein - 97% Access
  - Luxembourg - 97% Access
  - Malta - 97% Access
  - Austria - 95.86% Access
  - Spain - 95.81% Access
  - United Kingdom of Great Britain and Northern Ireland - 95.61% Access
  ```sql
  SELECT 
  	DISTINCT CountryTerritoryName,
      AVG(`Share%`) AvgAccess
  FROM city_public_transport_access
  GROUP BY CountryTerritoryName
  ORDER BY AvgAccess DESC
  LIMIT 10;
  ```
  
  <img width="401" height="240" alt="image" src="https://github.com/user-attachments/assets/976be44f-7a73-4c2d-bbea-203607752a18" />

- Trailing 3 Countries
  - Equatorial Guinea - 4% Access
  - Liberia - 5% Access
  - Libya - 7% Access
  - Solomon Islands - 7% Access
  - Jordan - 7.5% Access
  - Northern Mariana Islands - 8% Access
  - Cameroon - 10.89% Access
  - Paraguay - 12% Access
  - Angola - 12.1% Access
  - Democratic Republic of the Congo - 12.14% Access
  ```sql
  SELECT 
  	DISTINCT CountryTerritoryName,
      AVG(`Share%`) AvgAccess
  FROM city_public_transport_access
  GROUP BY CountryTerritoryName
  ORDER BY AvgAccess ASC
  LIMIT 10;
  ```

  <img width="313" height="243" alt="image" src="https://github.com/user-attachments/assets/d6d7ac6d-4178-407b-8825-af1e9a506422" />

- Leading Cities in terms of public transport accessibility
  - 





