Research for ruby 2.6 infinite range in ActiveRecord range

## postresql
```
> User.where(id: (1..))
  SELECT  "users".* FROM "users" WHERE "users"."id" BETWEEN $1 AND $2 LIMIT $3  [["id", 1], ["id", nil], ["LIMIT", 11]]
=> #<ActiveRecord::Relation []>
```

```postgresql
posgre_development=# SELECT * FROM users WHERE users.id BETWEEN 0 AND NULL;
 id | created_at | updated_at 
----+------------+------------
(0 rows)
```

## sqlite3
```
> User.where(id: (1..))
  User Load (0.2ms)  SELECT  "users".* FROM "users" WHERE "users"."id" BETWEEN ? AND ? LIMIT ?  [["id", 1], ["id", nil], ["LIMIT", 11]]
=> #<ActiveRecord::Relation []>
```

```sqlite
sqlite> SELECT * FROM users WHERE users.id BETWEEN 0 AND 1;
1|2019-01-09 16:19:13.215559|2019-01-09 16:19:13.215559
sqlite> SELECT * FROM users WHERE users.id BETWEEN 0 AND NULL;
sqlite> 
```
result is null


## mysql
```
> User.where(id: (1..))
  User Load (17.5ms)  SELECT  `users`.* FROM `users` WHERE `users`.`id` BETWEEN 1 AND NULL LIMIT 11
=> #<ActiveRecord::Relation []>
```

```mysql
mysql> SELECT `users`.* FROM `users` WHERE `users`.`id` BETWEEN 0 AND NULL;
Empty set (0.00 sec)
```

## Oracle

```
SELECT * FROM USERS WHERE USERS.ID BETWEEN 1 AND NULL;

no rows selected
```
