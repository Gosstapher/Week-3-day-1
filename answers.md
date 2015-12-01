# Section 1 #

# Question 1 Select the names of all users. #

SELECT * FROM users;

 id |       name       
----+------------------
  1 | Rick Henri
  2 | Jay Chetty
  3 | Keith Douglas
  4 | Callum Dougan
  5 | Andrew Insley
  6 | Daniel Gillespie
  7 | Bethany Fraser
  8 | Nick Ridell
  9 | Evelyn Utterson
 10 | Sky Su
 11 | Nicholas Hill
 12 | Michael McLeod
 13 | Callum Hogg
 14 | Chris Sloan
 15 | Gary Carmichael
 16 | Oscar Brooks
 17 | Ross Galloway
 18 | Paul MacLean
 19 | Stuart Ramsay
 20 | Peter Forbes
 21 | Euan Walls
 22 | Aine Dunphy
(22 rows)


# Question 2 Select the names of all shows that cost less than £15. #

SELECT name FROM shows WHERE price <= '15.00';

             name             
------------------------------
 Le Haggis
 Paul Dabek Mischief 
 Best of Burlesque
 Two become One
 Urinetown
 Two girls, one cup of comedy
(6 rows)


# Question 3 Insert a user with the name "Val Gibson" into the users table. #

INSERT INTO "users" (name) VALUES ('Val Gibson');

INSERT 0 1


# Question 4 Select the id of the user with your name. #

fringe_shows=# SELECT id FROM users WHERE name = 'Daniel Gillespie';
 
 id 
----
  6
(1 row)


# Question 5 Insert a record that Val Gibson wants to attend the show "Two girls, one cup of comedy". #

fringe_shows=# INSERT INTO "shows_users" (show_id, user_id) VALUES (12, 23);

INSERT 0 1

# Question 6 Updates the name of the "Val Gibson" user to be "Valerie Gibson".

fringe_shows=# UPDATE users SET name = 'Valerie Gibson' WHERE id = 23;

UPDATE 1


# Question 7 Deletes the user with the name 'Valerie Gibson'. #

DELETE FROM users WHERE id = 23;

DELETE 1


# Question 8 Deletes the shows for the user you just deleted. #

fringe_shows=# DELETE FROM shows_users WHERE user_id = 23;

DELETE 1


# Section 2 #

# Question 1 Select the names and prices of all shows, ordered by price in ascending order. #

fringe_shows=# SELECT name, price FROM shows ORDER BY price ASC;

                   name                    | price 
-------------------------------------------+-------
 Two girls, one cup of comedy              |  6.00
 Best of Burlesque                         |  7.99
 Two become One                            |  8.50
 Urinetown                                 |  8.50
 Paul Dabek Mischief                       | 12.99
 Le Haggis                                 | 12.99
 Joe Stilgoe: Songs on Film â€“ The Sequel | 16.50
 Game of Thrones - The Musical             | 16.50
 Shitfaced Shakespeare                     | 16.50
 Aaabeduation â€“ A Magic Show             | 17.99
 Camille O'Sullivan                        | 17.99
 Balletronics                              | 32.00
 Edinburgh Royal Tattoo                    | 32.99
(13 rows)


# Question 2 Select the average price of all shows. #

fringe_shows=# SELECT AVG(price) FROM shows;

         avg         
---------------------
 15.9569230769230769
(1 row)



# Question 3 Select the price of the least expensive show. #

fringe_shows=# SELECT MIN(price) FROM shows;

 min  
------
 6.00
(1 row)


# Question 4 Select the sum of the price of all shows. #

fringe_shows=# SELECT SUM(price) FROM shows;

  sum   
--------
 207.44
(1 row)


# Question 5 Select the sum of the price of all shows whose prices is less than £20. #

fringe_shows=# SELECT SUM(price) FROM shows WHERE price <= '20.00';

  sum   
--------
 142.45
(1 row)


# Question 6 Select the name and price of the most expensive show. #

fringe_shows=# SELECT name, price FROM shows WHERE price = (SELECT MAX(price) FROM shows);

          name          | price 
------------------------+-------
 Edinburgh Royal Tattoo | 32.99
(1 row)


# Question 7 Select the name and price of the second from cheapest show. #

fringe_shows=# SELECT name, price FROM shows WHERE price = (SELECT MIN(price) FROM shows WHERE price NOT IN (SELECT MIN(price) FROM shows));

       name        | price 
-------------------+-------
 Best of Burlesque |  7.99
(1 row)


# Question 8 Select the names of all users whose names start with the letter "N". #

fringe_shows=# SELECT name FROM users WHERE name LIKE 'N%';

     name      
---------------
 Nick Ridell
 Nicholas Hill
(2 rows)


# Question 9 Select the names of users whose names contain "mi" #

fringe_shows=# SELECT name FROM users WHERE name LIKE '%mi%';

      name       
-----------------
 Gary Carmichael
(1 row)


# Section 3 #

# Question 1 Select the time for the Edinburgh Royal Tattoo. #

SELECT shows.name, times.time FROM shows JOIN times ON shows.id = times.show_id WHERE shows.name = 'Edinburgh Royal Tattoo';

          name          | time  
------------------------+-------
 Edinburgh Royal Tattoo | 22:00
(1 row)


# Question 2 Select the number of users who want to see "Shitfaced Shakespeare". #



















