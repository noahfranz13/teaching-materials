# Introduction to Databases
This directory holds teaching materials for a TIMESTEP workshop on databases and SQL. This workshop was 1.5 hours long.

## Part 1: Mini-lecture
The slides in [intro-to-db.pdf](./intro-to-db.pdf) show the mini-lecture with background material on databases and SQL. These will be good to refer back to as a "cheat-sheet".

## Part 2: Activity

### Preparation
1. Navigate to https://sqliteviewer.app/ and upload the `astro-obsplan.sqlite` file in this folder. This will allow you to visualize the various database tables
2. To allow yourself to also practice queries, navigate to https://sqlime.org/ and upload the `astro-obsplan.sqlite` file in this folder using the `open file` button.

### Questions to get us started all together
1. Get all of the data from the `target` table
```
SELECT *
FROM target;
```
What do we see here? And, what do these columns tell us? 

2. Get all of the targets from the `target` table that are visible with the Mayall telescope on Kitt Peak (ASK: how can we do this?)
```
SELECT *
FROM target
WHERE dec > -20;
```

3. How many observations from the Mayall telescope do we store?

```
SELECT *
FROM observation
WHERE telescope_name = 'Mayall'
```

And count by hand, or use the SQL aggregation command `COUNT()`

```
SELECT COUNT(*)
FROM observation
WHERE telescope_name = 'Mayall'
```

4. How many observations do we store from a telescope in the northern hemisphere?

```
SELECT COUNT(*)
FROM observation
JOIN telescope
WHERE observation.tele_name = telescope.name
AND telescope.latitude > 0;
```

### Individual Activity (preferrably in smaller groups/tables)

1. How many tables in the database? (Hint: you can also just look at the SQLite viewer website!)
2. Get a table of all of the observations we store. Look through the data. What do you notice? How many observations are there?
3. How many telescope filters do we store? What are they?
4. You want to plan to observe on the NOT telescope, but it has a limiting magnitude of 18. Get all of the targets that you can observe (assume you can't observe targets with null values).
5. How many observations do we store from the Mayall telescope? How many days do they span? How many unique targets? (Hint: You can use `COUNT(DISTINCT X)` to get the total number of distinct values in a column `X`)
6. Get all southern telescopes that we store. How many observations do we store from the southern telescope(s)?
7. You are a transient astronomer interested in supernova *and* supernova remnants. Get a list of all targets that are either SN or SN remnants using a LIKE query. 
8. Of the SN and SN remnants from question 7, how many times have we observed these SN? 
9. You are an extragalactic astronomer planning your observations. Get a list of all of the galaxies in the target table. How many are there? What are some of their names? (Hint: it might be helpful to look carefully at the `type` column in the target table) (Hint 2: Remember that "AGN", "Quasar", and "Blazar" are also galaxies!)
10. Of the galaxies from the previous question, how many are visible from the Mayall telescope?
11. Repeat question 4, but now you are only planning to observe in r-band, so you only want targets that have r-band magnitudes stored!
12. Telescope time is limited, so you don't want to duplicate previous efforts. Get a list of all of the galaxies that have not been observed EVER with the Mayall telescope and all of the transients that have not been observed in the past 30 days (Hint: What's the MJD today? What is the MJD 30 days ago?). How many are there? What would you be interested in observing?

Bonus question: Each of you at the table should come up with another question and pose it to your group. How do you answer it using SQL commands?
