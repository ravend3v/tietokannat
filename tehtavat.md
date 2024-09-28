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

# Join harjoitukset

### Tehtävä 1
SELECT country.name AS "country name", airport.name AS "airport name" FROM country INNER JOIN airport ON airport.iso_country = country.iso_country  WHERE country.name = "Finland" AND scheduled_service = "yes";
![img_19.png](img_19.png)

### Tehtävä 2
SELECT screen_name, airport.name FROM game INNER JOIN airport ON location = ident;
![img_20.png](img_20.png)

### Tehtävä 3
SELECT screen_name, country.name FROM game, airport INNER JOIN country ON location = ident WHERE airport.iso_country = country.iso_country;
![img_21.png](img_21.png)

### Tehtävä 4
SELECT airport.name, screen_name FROM airport LEFT JOIN game ON ident = location WHERE name like "%Hels%";
![img_22.png](img_22.png)

### Tehtävä 5
SELECT name, screen_name FROM goal LEFT JOIN goal_reached ON goal.id = goal_id LEFT JOIN game ON game.id = game_id;
![img_23.png](img_23.png)

# Sisäkysely harjoitukset

### Tehtävä 1
SELECT name FROM country WHERE iso_country IN(SELECT iso_country FROM airport WHERE name like "Satsuma%");
![img_24.png](img_24.png)

### Tehtävä 2
SELECT name FROM airport WHERE iso_country IN(SELECT iso_country FROM country WHERE name = "Monaco");
![img_25.png](img_25.png)

### Tehtävä 3
SELECT screen_name FROM game WHERE id IN(SELECT game_id FROM goal_reached WHERE goal_id IN(SELECT id FROM goal WHERE name = "CLOUDS"));
![img_26.png](img_26.png)

### Tehtävä 4
SELECT country.name FROM country WHERE iso_country NOT IN(SELECT airport.iso_country FROM airport);
![img_27.png](img_27.png)

### Tehtävä 5
SELECT name FROM goal WHERE id NOT IN(SELECT goal.id FROM goal, goal_reached, game WHERE game.id = game_id AND goal.id = goal_id AND screen_name = "Heini");
![img_28.png](img_28.png)

# Koostetieto kyselyt 

### Tehtävä 1
SELECT max(elevation_ft) FROM airport;
![img_29.png](img_29.png)

### Tehtävä 2
SELECT continent, count(*) FROM country GROUP BY continent;
![img_30.png](img_30.png)

### Tehtävä 3
SELECT screen_name, count(*) FROM game, goal_reached WHERE id = game_id GROUP BY screen_name;
![img_31.png](img_31.png)

### Tehtävä 4
SELECT screen_name FROM game WHERE co2_consumed IN(SELECT min(co2_consumed) FROM game);
![img_32.png](img_32.png)

### Tehtävä 5
SELECT country.name, count(*) FROM airport, country WHERE airport.iso_country = country.iso_country GROUP BY country.iso_country ORDER BY count(*)DESC LIMIT 50;
![img_33.png](img_33.png)

### Tehtävä 6
SELECT country.name FROM airport, country WHERE airport.iso_country = country.iso_country GROUP BY country.iso_country HAVING count(*)>1000;
![img_34.png](img_34.png)

### Tehtävä 7
SELECT name FROM airport WHERE elevation_ft IN (SELECT max(elevation_ft) FROM airport);
![img_35.png](img_35.png)

### Tehtävä 8
SELECT name FROM country WHERE iso_country IN (SELECT iso_country FROM airport WHERE elevation_ft IN (SELECT max(elevation_ft) FROM airport));
![img_36.png](img_36.png)

### Tehtävä 9
SELECT count(*) FROM game, goal_reached WHERE id = game_id AND screen_name = "Vesa" GROUP BY screen_name;
![img_37.png](img_37.png)

### Tehtävä 10
SELECT name FROM airport WHERE latitude_deg IN (SELECT min(latitude_deg) FROM airport);
![img_38.png](img_38.png)


# Päivityskyselyt

### Tehtävä 1
UPDATE game SET location = (SELECT ident FROM airport WHERE name = "Nottingham Airport"), co2_consumed = co2_consumed+500 WHERE screen_name = "Vesa";
![img_39.png](img_39.png)

### Tehtävä 3
DELETE FROM goal_reached;
SELECT * FROM goal_reached;
![img_40.png](img_40.png)

### Tehtävä 4
DELETE FROM game;
SELECT * FROM game;
![img_41.png](img_41.png)

# Tietokannan suunnittelu tehavat
![img_42.png](img_42.png)


