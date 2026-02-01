# Introduction to Databases

## Part 1: Mini-lecture
The slides in intro-to-db.pdf show the mini-lecture with background material on databases and SQL. These will be good to refer back to as a "cheat-sheet".

## Part 2: Activity

### Interactive Queries Together

#. Get all of the data from the `target` table
```
SELECT *
FROM target;
```
What do we see here? And, what do these columns tell us? 

#. Get all of the targets from the `target` table that are visible with the Mayall telescope on Kitt Peak (ASK: how can we do this?)
```
SELECT *
FROM target
WHERE dec > -20;
```

#. How many observations from the Mayall telescope do we store?

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

#. How many observations do we store from a telescope in the northern hemisphere?

```
SELECT COUNT(*)
FROM observation
JOIN telescope
WHERE observation.tele_name = telescope.name
AND telescope.latitude > 0;
```

### Group Activity
