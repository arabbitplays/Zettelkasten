# Database Indices

## Introduction

- indices are data structures used to make DB calls faster that use a certain column
	- eg. this creates an index for table test1 over the column id, making queries like `SELECT content from test1 WHERE id = constant` faster
	- other queries involving the id column like UPDATE or DELETE too
```postgreSQL
CREATE INDEX test1_id_index ON test1 (id);
```
- check out https://www.postgresql.org/docs/current/performance-tips.html for information on how to find out, if an index is used
- there can also be <mark style="background: #FFB86CA6;">multicolumn indexes</mark> 
	- they can optimize queries like `SELECT name FROM test2 WHERE major = constant AND minor = constant`
	- they can be used for queries involving any of the columns
```postgreSQL
CREATE INDEX test2_mm_idx ON test2 (major, minor);
```

## B-Tree

- this is the standard type of index, that is created if no index type is specified
- under the hood this is a binary search tree -> column has to be sortable
	- supports all range queries `< <= = >= >`, `IS NULL` and `IS NOT NULL` 
		- `LIKE` works when the pattern is a constant and at the beginning
			- so `col LIKE 'foo%'` works
			- but `col LIKE '%bar'` not 

## Hash

- works by storing a 32-bit hash of the value
- supports only equality comparisons `=`

## GiST

- this is not a single king of index but rather an infrastructure for different indexing strategies
	- thus the supported operators depend on the implemented strategy
	- many are implemented in community extensions
- in general meant for geometric types 
- can also optimize nearest neighbor queries like this 
```postgreSQL
SELECT * FROM places ORDER BY location <-> point '(101,456)' LIMIT 10;
```

## General inverted index (GIN)

- these are "inverted indexes" for data values that contain multiple components (like arrays or json)
	- has a separate index for each component and handle queires well that test for the presence of specific component values
- like with GiST there can be user defined strategies, but the standard implementation supports `<@ @> = &&` for arrays (contains, equals and "do they overlap")

## Block range index (BRIN)

- they store summaries of physical block ranges in the table
	- thus especially good when the column value is correlated with the position in the table
- supports `< <= = => >`

---

Origin: https://www.postgresql.org/docs/current/indexes-intro.html
References: 
Tags: 
Created: 17.06.2026

