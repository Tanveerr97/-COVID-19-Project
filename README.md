# -COVID-19-Project
Creating a project where you manipulate COVID-19 data using SQL and then visualize it in Power BI is a great way to combine data analysis and visualization skills.
"Power BI Dashboard: Analyzing Global COVID-19 Confirmed Cases and Death Rates by Country"
Creating a project where you manipulate COVID-19 data using SQL and then visualize it in Power BI is a great way to combine data analysis and visualization skills.
 SQL -managing and manipulating databases
-- order by the total confirmed cases in ascending order, then by deaths and active cases in descending order
SELECT Country, 
 SUM(Confirmed) AS total_confirmed, 
 SUM(Deaths) AS total_deaths, 
 SUM(Active) AS total_active
FROM new_schema.countrywise
GROUP BY Country
ORDER BY total_confirmed DESC, total_deaths DESC, total_active DESC;

/*Looking at Total Cases vs Population*/

SELECT Country,population,
 SUM(Confirmed) AS total_cases, 
 SUM(Deaths) AS total_deaths, 
 (SUM(Confirmed) / Population) * 100 AS death_percentage
FROM new_schema.countrywise
WHERE Country = 'Australia'
GROUP BY Country, Population
ORDER BY Country, Population;

/*Looking at Countries with Highest Infection rate compared to Population*/

select Country , population , max(Confirmed) , 
 max(Confirmed/population)*100 as Countrypercent_population_infected
from new_schema.countrywise
group by Country, population 
order by Countrypercent_population_infected desc;
-- filter data on the basic of weekly updates
SELECT 
 Country, 
 Confirmed_last_week,
 `1_week_change`,
 `1_week_%_increase`
FROM new_schema.countrywise
WHERE Confirmed_last_week > 300000 -- Example filter for confirmed cases
 AND `1_week_change` > 15000    -- Example filter for cases with significant change
 AND `1_week_%_increase` > 5    -- Example filter for cases with more than 5% increase
ORDER BY `1_week_%_increase` desc;
-------------------------------------------------------------------------------------
Using Power BI to visualize COVID-19 cases and confirmed deaths
(1)https://lnkd.in/eeJqqrqS
(2)https://lnkd.in/ezfWkA4w
(3)https://lnkd.in/eTZgmpgi
download the dataset from
https://covid19.who.int/
https://covid19.who.int/
hashtag#powerbi hashtag#sql hashtag#dataanalyst

![Image](https://github.com/user-attachments/assets/48fc1f6d-d46e-4e77-9953-71b052a94f71)
