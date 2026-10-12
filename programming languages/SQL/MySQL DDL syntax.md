# (1) Create table
- Data type must be specified after the column
- table and column names must start with a letter
- alphabets and numbers and _, $, # characters are allowed only

## - Create table syntax^(1)^

```sql
create table table_name(
	column_name Datatype [not null/null] [default value]
	[primary key(column list)]
	[unique(column list)]
	[foreign key(column list)] references table_name(column list)]
		[on delete option] [on update option]
	[constraint name] [check(condition)]);
```

- one primary key set
- multiple unique key set
- multiple foreign key set
- multiple constraints
- [] can be omitted
- SQL statements aren't case sensitive
- commas separate each line

## - Integrity constraints^(1)^
- not null:
Column does not allow null values

- default:
The default value of a column

Strings are encased in single quotes

- check:
Specify constraints on specific attributes

- unique:
Keywords that specify alternate keys. They are unique, but null values are allowed

- primary key:
Specifies the primary key

- foreign key:
Must be followed by the references keyword to indicate which table it refers to

Prevents tuples from being arbitrarily deleted or modified in the referenced table

Options to specify how to handle deleting or updating tuples from the referenced table
on delete(update) no action: prevents tables from being deleted(updated)
on delete(update) cascade: delete(update) related tuples together
on delete(update) set null: changes the foreign key value of related tuples to null
on delete(update) set default: changes the foreign key value of related tuples to the default value

# (2) Alter table
## - Alter table syntax^(1)^


```sql
alter table table_name
	add column_name datatype [not null / null] [default value];
	modify column_name datatype [not null / null] [default value];
	modify column_name datatype [first / after column_name];
	drop column_name ;
	rename column old_column_name to new_column_name;
	add constraint_name;
	drop constraint_name;
```
# 
(3) Drop table
## - Drop table syntax^(1)^

```sql
drop table table_name;
```
# 

(4) Rename table
## - Rename table syntax^(1)^ 

```sql
rename table old_table to new_table;
alter table old_table rename new_table;
```


---
(1) database class