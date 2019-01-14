Research for ruby 2.6 infinite range in ActiveRecord range

## postresql
```
> User.where(id: (1..))
  SELECT  "users".* FROM "users" WHERE "users"."id" BETWEEN $1 AND $2 LIMIT $3  [["id", 1], ["id", nil], ["LIMIT", 11]]
=> #<ActiveRecord::Relation []>
```

## sqlite3
```
> User.where(id: (1..))
  User Load (0.2ms)  SELECT  "users".* FROM "users" WHERE "users"."id" BETWEEN ? AND ? LIMIT ?  [["id", 1], ["id", nil], ["LIMIT", 11]]
=> #<ActiveRecord::Relation []>
```

## mysql
```
> User.where(id: (1..))
  User Load (17.5ms)  SELECT  `users`.* FROM `users` WHERE `users`.`id` BETWEEN 1 AND NULL LIMIT 11
=> #<ActiveRecord::Relation []>
```

## Oracle

```
SELECT * FROM CUSTOMERS WHERE CUSTOMERS.ID BETWEEN 1 AND NULL;

no rows selected
```
