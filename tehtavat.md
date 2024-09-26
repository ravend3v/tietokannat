# Tietokanta-tehtavat

# Yhteen tauluun kohdistuvat kyselyt

### Tehtävä 1
SELECT * FROM goal;
![img.png](img.png)

### Tehtävä 2
SELECT name airport_type FROM airport WHERE iso_country = "FI";
![img_1.png](img_1.png)

### Tehtävä 3
SELECT name FROM airport WHERE iso_country = "FI" ORDER BY name ASC;
![img_2.png](img_2.png)

### Tehtävä 4
SELECT name, type FROM airport WHERE iso_country = "FI" ORDER BY type, name;
![img_3.png](img_3.png)

### Tehtävä 5
SELECT name FROM country WHERE name LIKE "F%";
![img_4.png](img_4.png)

### Tehtävä 6
SELECT name FROM country WHERE name LIKE "%F%";
![img_5.png](img_5.png)

### Tehtävä 7
SELECT location FROM game WHERE screen_name = "Vesa";
![img_6.png](img_6.png)

### Tehtävä 8
SELECT co2_consumed FROM game WHERE screen_name = "Ilkka";
![img_7.png](img_7.png)

### Tehtävä 9
SELECT DISTINCT co2_budget FROM game;
![img_8.png](img_8.png)

# Where-osan liitosehto

### Tehtävä 1
SELECT country.name AS "country name", airport.name AS "airport name" FROM airport, country WHERE airport.iso_country = country.iso_country AND country.name = "Iceland";
![img_9.png](img_9.png)

### Tehtävä 2
SELECT airport.name AS "airport name" FROM airport, country WHERE airport.iso_country = country.iso_country AND country.name = "France" AND airport.type = "large_airport";
![img_10.png](img_10.png)

### Tehtävä 3
SELECT country.name AS country_name, airport.name AS airport_name FROM airport, country WHERE airport.iso_country = country.iso_country AND country.continent = "AN";
![img_11.png](img_11.png)

### Tehtävä 4
SELECT elevation_ft FROM airport, game WHERE location = ident AND screen_name = "Heini";
![img_12.png](img_12.png)

### Tehtävä 5
SELECT elevation_ft * 0.3048 AS elevation_m FROM airport, game WHERE location = ident AND screen_name = "Heini";
![img_13.png](img_13.png)

### Tehtävä 6
SELECT name FROM airport, game WHERE location = ident AND screen_name = "Ilkka";
![img_14.png](img_14.png)

### Tehtävä 7
SELECT country.name FROM airport, game, country WHERE location = ident AND airport.iso_country = country.iso_country AND screen_name = "Ilkka";
![img_15.png](img_15.png)

### Tehtävä 8
SELECT name FROM goal, goal_reached, game WHERE game.id = game_id AND goal.id = goal_id AND screen_name = "Heini";
![img_16.png](img_16.png)

### Tehtävä 9
SELECT airport.name FROM airport, game, goal, goal_reached WHERE ident = location AND game.id = game_id AND goal.id = goal_id AND screen_name = "Ilkka" AND goal.name = "CLOUDS";
![img_17.png](img_17.png)

### Tehtävä 10
SELECT country.name FROM airport, country, game, goal, goal_reached WHERE ident = location AND airport.iso_country = country.iso_country AND game.id = game_id AND goal.id = goal_id AND screen_name = "Ilkka" AND goal.name = "CLOUDS";
![img_18.png](img_18.png)