- SQL (*Structure Query Language*) is a programming Language used to interact with relational databases.
- It is used to perform CRUD operations.
	- *Create*
	- *Read*
	- *Update*
	- *Delete*
##### SQL vs SEQUEL
- Earlier it was known as *Structured English Query Language* Developed by IBM
```
**create database** name
use name

%% drop to delete a db %%

CREATE DATABASE College
USE College

create table student (
col_names type constraint
col_name2 type constraint
);

```

### SQL Datatypes
- There are many
- VARCHAR, CHAR - Both for the same purpose but varchar is efficient since its only take the memory that's required. Char occupied the complete what's initialized with even when unused.
- **Signed & Unsigned** - For numeric to define positive negative
	- TINYINT has range of 255, `TINYINT UNSIGNED` (0 to 255), `TINYINT` (-18 to 127)
	- So one advantage is we can increase the range of certain datatypes

# Types of SQL Commands
- **DDL** (Data *Definition* Language)
	- create, alter, rename, truncate, drop
- **DQL** (Data *Query* Language)
	- select
- **DML** (Data *Manipulation* Language)
	- insert, update, delete
- **DCL** (Data *Control* Language)
	- To grant to revoke permissions to users
- **TCL** (Transaction *Control* Language)
	- start transaction, commit, rollback