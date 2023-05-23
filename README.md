# hive_interview_preparation

## Theorical Questions Section

### Theorical Question 1

Do hive have OLTP features ?

<details><summary><b>Answer</b></summary>

![Image](img/hiveIsNotOLTP.png "hiveIsNotOLTP")

![Image](img/hbase_hive_is_not_oltp.png "hbase_hive_is_not_oltp")

</details>

<details><summary><b>Source</b></summary>
programming hive
</details>

### Theorical Question 2

Why jive could misinterpret data ?

<details><summary><b>Answer</b></summary>

When you write data to a traditional database, either through loading external data,
writing the output of a query, doing UPDATE statements, etc., the database has total
control over the storage. The database is the “gatekeeper.” An important implication
of this control is that the database can enforce the schema as data is written. This is
called schema on write.

Hive has no such control over the underlying storage. There are many ways to create,
modify, and even damage the data that Hive will query. Therefore, Hive can only en-
force queries on read. This is called schema on read.

So what if the schema doesn’t match the file contents? Hive does the best that it can to
read the data. You will get lots of null values if there aren’t enough fields in each record to match the schema. If some fields are numbers and Hive encounters nonnumeric
strings, it will return nulls for those fields. Above all else, Hive tries to recover from all errors as best it can.

</details>

<details><summary><b>Source</b></summary>
programming hive
</details>