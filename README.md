# Olympic_games_analysis

![](https://github.com/najirh/netflix_sql_project/blob/main/logo.png](https://github.com/Aniltamang07/Olympic_games_anlysis/blob/main/Olympic_games.png))

## Overview
This project involves a comprehensive analysis of olympic Games using SQL. The goal is to extract valuable insights from the dataset. The following README provides a detailed account of the project's objectives, questions, solutions, findings, and conclusions.

## Objectives

- Analyze the most athlete from the countries.
- Identify the Female Percentage in the olympic.
- List and analyze content based on year, country and number of events.
- Explore the number of events happend over the year.

## Dataset

The data for this project is sourced from the Kaggle dataset:

- **Dataset Link:** [Olympic Dataset](https://www.kaggle.com/datasets/shivamb/netflix-shows?resource=download)


##  Anlysis from the dataset

### 1. How many athletes compete in year 2000?

```sql
SELECT COUNT( distinct ID) AS num_athlete
FROM athlete_events
WHERE year = 2000;
```

**Objective:** Find number of athlete compete in the year of 2000.

### 2. Which countries send the most athletes to the olympics?

```sql
SELECT region, count(ID) AS Num_athlete
 FROM athlete_events e
LEFT JOIN country_definitions c
ON e.noc = c.noc
GROUP BY region
ORDER BY Num_athlete DESC;
```

**Objective:** find the numnbers of athlete send the countries.

### 3.  Which country won most medals?

```sql
SELECT Medal, region, count(ID) AS Num_athlete
 FROM athlete_events e
LEFT JOIN country_definitions c
ON e.noc = c.noc
WHERE Medal<> "NA"
GROUP BY medal
ORDER BY num_athlete DESC;
```

**Objective:** find which country won the most medals in olympic.

### 4. Find the number of Genders In Olympic?

```sql
SELECT COUNT(ID) AS num_athlete, sex
FROM athlete_events
GROUP BY sex
ORDER BY num_athlete DESC;

```

**Objective:** Identify the numbers of gender in olympic.

### 5. Identify the % of athletes who were female over time

```sql
SELECT round(((SELECT Count(sex)
FROM athlete_events 
WHERE sex = "F")/ count(sex))*100,2)
AS "female%" 
FROM athlete_events;
```

**Objective:** Find the female Percentage in olympic.

### 6. Top 5 Sports played in olympic?

```sql
SELECT sport, Count(sport) AS num_sports
FROM athlete_events
GROUP BY sport
ORDER BY num_sports DESC
LIMIT 5;
```

**Objective:** Retrieve The most 5 played sports in olympic.

### 7. Average age of the players in olympic?

```sql
Select Round(AVG(age),0)
 AS "Average age of players"
 From athlete_events;
```

**Objective:** Find the average age of the players'.

### 8. which year most events happen?

```sql
SELECT year, count(DISTINCT event)
AS num_events
FROM athlete_events
GROUP BY year
ORDER BY num_events DESC;
```

**Objective:** Find which year most events happened.



## Findings and Conclusion

- **Content Distribution:** The dataset contains a all the records of the olympic games from 1896 to 2016.
- **Common Ratings:** finds the female and male ratio in the olympic games.
- **Geographical Insights:** The top countries and the medals won by them.

This analysis provides a comprehensive view of olympic_games and can help gain knowledge about previous olympic records


