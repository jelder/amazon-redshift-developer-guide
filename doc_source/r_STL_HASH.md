# STL\_HASH<a name="r_STL_HASH"></a>

Analyzes hash execution steps for queries\.

This table is visible to all users\. Superusers can see all rows; regular users can see only their own data\. For more information, see [Visibility of Data in System Tables and Views](c_visibility-of-data.md)\.

## Table Columns<a name="r_STL_HASH-table-columns"></a>

[\[See the AWS documentation website for more details\]](http://docs.aws.amazon.com/redshift/latest/dg/r_STL_HASH.html)

## Sample Queries<a name="r_STL_HASH-sample-queries"></a>

The following example returns information about the number of partitions that were used in a hash for query 720, and indicates that none of the steps ran on disk\. 

```
select slice, rows, bytes, occupied, workmem, num_parts, est_rows, num_blocks_permitted
from stl_hash
where query=720 and segment=5
order by slice;
```

```
 slice | rows | bytes  | occupied | workmem  | num_parts | est_rows | num_blocks_permitted
-------+------+--------+----------+----------+-----------+----------+----------------------
     0 |  145 | 585800 |        1 | 88866816 |        16 |        1 |                   52
     1 |    0 |      0 |        0 |        0 |        16 |        1 |                   52
(2 rows)
```