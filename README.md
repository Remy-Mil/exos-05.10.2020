# exos-05.10.2020

exercice 1:

postgres=> CREATE DATABASE db_1;
CREATE DATABASE
postgres=> CREATE TABLE users (id SERIAL PRIMARY KEY, name VARCHAR(30), password VARCHAR(30));
CREATE TABLE
postgres=> INSERT INTO users (name, password) VALUES ('alice', '123'), ('bob', '456'), ('charlie', '789');
INSERT 0 3
postgres=> SELECT \* FROM users;
id | name | password
----+---------+----------
1 | alice | 123
2 | bob | 456
3 | charlie | 789
(3 rows)

exercice 2:

postgres=> INSERT INTO users (name, password) VALUES ('dan', '101112'), ('eve', '131415'), ('faythe', '161718');
INSERT 0 3
postgres=> SELECT \* FROM users;
id | name | password
----+---------+----------
1 | alice | 123
2 | bob | 456
3 | charlie | 789
4 | dan | 101112
5 | eve | 131415
6 | faythe | 161718
(6 rows)

exercice 3:

postgres=> SELECT \* FROM users WHERE length(password) > 3 ;
id | name | password
----+--------+----------
4 | dan | 101112
5 | eve | 131415
6 | faythe | 161718
(3 rows)

exercice 4:

postgres=> ALTER TABLE users ADD COLUMN bio TEXT DEFAULT 'Hello, world';
ALTER TABLE
postgres=> SELECT \* FROM users
postgres-> ;
id | name | password | bio
----+---------+----------+--------------
1 | alice | 123 | Hello, world
2 | bob | 456 | Hello, world
3 | charlie | 789 | Hello, world
4 | dan | 101112 | Hello, world
5 | eve | 131415 | Hello, world
6 | faythe | 161718 | Hello, world
(6 rows)

exercice 5:

postgres=> UPDATE users SET bio = Concat('Hello, i am ', name);
UPDATE 6
postgres=> SELECT \* FROM users;
id | name | password | bio
----+---------+----------+---------------------
1 | alice | 123 | Hello, i am alice
2 | bob | 456 | Hello, i am bob
3 | charlie | 789 | Hello, i am charlie
4 | dan | 101112 | Hello, i am dan
5 | eve | 131415 | Hello, i am eve
6 | faythe | 161718 | Hello, i am faythe
(6 rows)

exercice 6:

postgres=> SELECT \* FROM users ORDER BY id DESC LIMIT 2
postgres-> ;
id | name | password | bio
----+--------+----------+----------------------------
6 | faythe | 161718 | Hello, I am PRENOM_DU_USER
5 | eve | 131415 | Hello, I am PRENOM_DU_USER
(2 rows)

exercice 7:

postgres=> SELECT \* FROM users WHERE ((id % 2) = 1);
id | name | password | bio
----+---------+----------+---------------------
1 | alice | 123 | Hello, i am alice
3 | charlie | 789 | Hello, i am charlie
5 | eve | 131415 | Hello, i am eve
(3 rows)

exercice 8:

postgres=> DELETE FROM users WHERE (id % 2 = 0);
DELETE 3

postgres=> SELECT \* FROM users;
id | name | password | bio
----+---------+----------+---------------------
1 | alice | 123 | Hello, i am alice
3 | charlie | 789 | Hello, i am charlie
5 | eve | 131415 | Hello, i am eve
(3 rows)

exercice 9:

postgres=> DROP TABLE users;
DROP TABLE
postgres=> \c postgres;
You are now connected to database "postgres" as user "db_user".
postgres=> DROP DATABASE db_1;
DROP DATABASE
postgres=>