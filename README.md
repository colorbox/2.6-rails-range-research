```
User.where(id: (0..)).to_sql
=> "SELECT \"users\".* FROM \"users\" WHERE \"users\".\"id\" BETWEEN 0 AND NULL"
```
