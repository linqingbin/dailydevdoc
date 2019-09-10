# SQL

## Code sample

Create table
```sql
CREATE TABLE tablex(field1 varchar(20), field2 char(1));
```

Create index
```sql
CREATE INDEX index_name ON tablex (field1);
```

Delete index
```sql
ALTER TABLE tablex DROP INDEX index_name
```

Insert rows
```sql
INSERT INTO tablex VALUES("xx","1");
```

Update values
```sql
UPDATE TABLE tablex SET field1 = "" WHERE field2 = "m" ;
```

Delete rows
```sql
DELETE FROM tablex WHERE field2 = "m";
```

Delete table
```sql
DROP TABLE tablex;
```

## Debug

### Diffrence between union and union all
The `union` will delete duplicate rows but `union all` not.

## Referral
* [Impala SQL](https://www.cloudera.com/documentation/enterprise/5-5-x/topics/impala_langref_sql.html)
* [Spark SQL](https://spark.apache.org/docs/2.3.0/api/sql/)
* [Pyspark.sql](https://spark.apache.org/docs/latest/api/python/pyspark.sql.html)
* [PostgreSQL](https://www.postgresql.org/docs/current/index.html)
* [SQLServer2017](https://docs.microsoft.com/en-us/sql/sql-server/sql-server-technical-documentation?view=sql-server-2017)
* [SQlite SQL core functions](https://www.sqlite.org/lang_corefunc.html)
* [MySQL](https://dev.mysql.com/doc/refman/8.0/en/)