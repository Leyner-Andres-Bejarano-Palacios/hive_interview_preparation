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

### Theorical Question 3

What commands would you use in hive if givena table you want to get info about:

- Partition Information
- Retention
- Location
- Compressed

<details><summary><b>Answer</b></summary>

DESCRIBE FORMATTED

</details>

<details><summary><b>Source</b></summary>
https://docs.cloudera.com/HDPDocuments/HDP3/HDP-3.0.1/materialized-view/content/hive_describe_materialized_view.html
</details>

### Theorical Question 4

What is the difference between managed/internal tables and external tables ?

<details><summary><b>Answer</b></summary>

The tables we have created so far are called managed tables or sometimes called inter-
nal tables, because Hive controls the lifecycle of their data (more or less). As we’ve seen, Hive stores the data for these tables in a subdirectory under the directory defined by hive.metastore.warehouse.dir (e.g., /user/hive/warehouse), by default.
When we drop a managed table  Hive deletes the data in the table.

</details>

<details><summary><b>Source</b></summary>
programming hive
</details>


### Theorical Question 5

When would you use the hive command ALTER TABLE ... ADD PARTITION ?

<details><summary><b>Answer</b></summary>

ALTER TABLE ... ADD PARTITION is not limited to external tables. You can use it with
managed tables, too, when you have (or will have) data for partitions in directories
created outside of the LOAD and INSERT options we discussed above. You’ll need to
remember that not all of the table’s data will be under the usual Hive “warehouse”
directory, and this data won’t be deleted when you drop the managed table! Hence,
from a “sanity” perspective, it’s questionable whether you should dare to use this fea-
ture with managed tables.

</details>

<details><summary><b>Source</b></summary>
programming hive
</details>