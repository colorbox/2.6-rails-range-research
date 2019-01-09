Research for ruby 2.6 infinite range in ActiveRecord range

## postresql
```
User.where(id: (0..)).to_sql
=> "SELECT \"users\".* FROM \"users\" WHERE \"users\".\"id\" BETWEEN 0 AND NULL"
```

## sqlite3
```
irb(main):015:0> User.where(id: (0..)).to_sql
=> "SELECT \"users\".* FROM \"users\" WHERE \"users\".\"id\" BETWEEN 0 AND NULL"
```

## mysql
```
User.where(id: (0..)).to_sql
=> "SELECT `users`.* FROM `users` WHERE `users`.`id` BETWEEN 0 AND NULL"
```

