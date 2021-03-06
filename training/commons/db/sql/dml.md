---
title: SQL - DML
description: Data Manipulation Language concepts
published: true
date: 2021-02-03T16:58:09.113Z
tags: 
editor: markdown
dateCreated: 2021-02-03T11:51:22.423Z
---

# Query Structure 
### SELECT, FROM, WHERE, GROUP, HAVING, ORDER


| COMMAND                                                                                                                      	| DESCRIPTION                                                                                                                                                                                                                                                                                   	|
|------------------------------------------------------------------------------------------------------------------------------	|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| SELECT [ TOP <n°\|%> ]⚠️* <br>    Attribute/s [AS Alias1], <br>    AggrFunct/s() [AS Alias2],<br>    NumberOfElelemtsToSelect 	| Expression can be the column/s or some aggregate function’s result. Alias is an alias of selection.<br>With TOP only the top number or % of results is selected.<br>⚠️Alternative to TOP is LIMIT (from,to) at the end.<br>Select a certain number of elements with integers.                  	|
| FROM Table1 [AS T1], Table2 [AS T2], ...                                                                                     	| If many, the ✖️ is executed. T1 is an alias for table1. <br>A condition in the where clause is equivalent to a join.                                                                                                                                                                           	|
| [ WHERE <br>    Condition/s,<br>    Condition/s(withNestedSQLQueries) ]                                                      	| Conditions are on the attributes (columns).<br>⚠️Conditions may NOT contain aggregate functions, which are only allowed in the having statement.<br>⚠️But confrontations with other SQL queries that themselves contain aggregate functions are allowed!                                        	|
| [ GROUP BY Attr/s <br>    [HAVING AggrFunct()] ]                                                                             	| Outputs only distinct rows. If multiple attr.s, there will be more rows (1a, 1b, 2a...). ⚠️Grouping is computed before aggregate functions. <br>⚠️All grouped attributes should also always appear in the select statement AND VICE VERSA!<br>having applies aggregate functions to each group. 	|


**- Fully Qualified Names:** Unambiguous access to elements can be done via dot-notation: TABLE1.COLUMN1


# Keywords
### Special selections, Null, IfNull, Coalesce, Pattern matching

|            COMMAND           	|                                DESCRIPTION                                	|
|:----------------------------:	|:-------------------------------------------------------------------------:	|
| SELECT DISTINCT Attribute... 	| Omits duplicates in the selection. Use when attribute is NOT primary key! 	|
| SELECT * ...                 	| Selects all columns/attributes.                                           	|
| IS [NOT] null                	| Verify (non) nullity of an attribute.                                     	|
| IFNULL(Attr, altValue)       	| Provides alternative value in case Attribute is null. (MySQL)             	|
| COALESCE(Attr1, Attr2, ...)  	| Returns the first non-null value in a list. (MySQL)                       	|
| ISNULL(Attr, altValue)       	| Provides alternative value in case Attribute is null. (SQLServer)         	|
| Attribute LIKE ‘pattern’     	| Pattern-matches: ’%’ (any string) and/or ’_’ (any char). Ex: %blabla%     	|

# Operators

- **Boolean**: 			AND, OR, NOT.
- **Comparison**:			=, <> (not equal), <, <=, >, >=.
- **Simple predicates**: 		TRUE, FALSE, BETWEEN (ex: attr BETWEEN val1 AND val2)
- **String concatenation operator**: 	||

# Join

|                       COMMAND                       	|                               DESCRIPTION                              	|
|:---------------------------------------------------:	|:----------------------------------------------------------------------:	|
| FROM Table1 [AS T1] [type] JOIN Table2 [AS T2] <br> < ON T1.attr = T2.attr \| WHERE T1.attr = T2.attr >      	| Needs an ON statement or a WHERE matching.<br> Otherwise use NATURAL JOIN. 	|

<br>

- **Join types**:  (⚠️Note: certain joins can produce duplicates and/or many null fields.)
	- **inner (default)**: returns only common results.
	- **left [outer^1^]**: returns all results of Table1 and only joint results of Table2.
	- **right [outer]**: returns all results of Table2 and only joint results of Table1.
	- **full [outer]**: (⚠️Not supported by MySQL - Use union all) returns all results with duplicates.
	- **NATURAL JOIN**: matches equally named columns. Do not use ON statement.
  <br>
- **Self-join**: when self joining, make sure to use aliases.
	- **example**: select X.attr, Y.attr from Table1 as X, Table1 as Y where…

---
^1^  “Outer” is optional and doesn’t change the meaning of the join. It’s the same with or without it.

# Aggregate Functions
### count, sum, max, min, avg

| COMMAND         	| DESCRIPTION                                                	| NOTES                                       	|
|-----------------	|------------------------------------------------------------	|---------------------------------------------	|
| count 	| ( * \| [distinct\|all] AttrList ) 	| all: will only count non-null values.                                         	|
| sum   	| ( [distinct\|all] AttrList )      	| all: will only count non-null values.<br>distinct: useful only in sum or avg. 	|
| max   	| ( [distinct\|all] AttrList )      	| all: will only count non-null values.<br>distinct: useful only in sum or avg. 	|
| min   	| ( [distinct\|all] AttrList )      	| all: will only count non-null values.<br>distinct: useful only in sum or avg. 	|
| avg   	| ( [distinct\|all] AttrList )      	| all: will only count non-null values.<br>distinct: useful only in sum or avg. 	|

- ⚠️They are computed last!
- ⚠️NO nested aggregate functions are allowed!!! NO: (select avg(count(*)))
	- Use an intermediate view instead.
- ⚠️Remember! AggrFuncts only return single scalar values! 
	- The result of a query with an aggregate function is called a “Target List”.
	- ⚠️Target Lists must be homogenous with the tables that they query!
		- Example: extract order with max price from the orders containing “ABC”.
			- ORDER(CodOrd, CodCli, Date, Price)
			- DETAIL(CodOrd, CodProd, Q)
		- NO: 	select Date, max(Price) ← Non homogenous (which date is paired with result?!)
						from Order, Detail
						where Order.CodOrd = Detail.CodOrd and CodProd = ‘ABC’
		- YES1: 	select Date, Price
							from Order, Detail
							where Order.CodOrd = Detail.CodOrd and CodProd = ‘ABC’ 
							and Price = ( select max(Price) from Order )
		- YES2: Another solution could be to use GROUP BY on the attr that is not an AggrFunct:
						select Date, max(Price)
						from Order
						group by Price

# Query Sets
### union, intersect, except

| COMMAND         	| DESCRIPTION                                                	| NOTES                                       	|
|-----------------	|------------------------------------------------------------	|---------------------------------------------	|
| union [all]     	| Union of both query results. Useful when “or” is asked.    	| Duplicates are omitted unless all is added. 	|
| intersect [all] 	| Intersection of query results. Useful when “and” is asked. 	| Duplicates are omitted unless all is added. 	|
| except [all]    	| Difference of query results. Useful when “but” is asked.   	| Duplicates are omitted unless all is added. 	|

- ⚠️Selected attributes are matched by positional notation! Attributes should correspond in both queries!

	- Only the first query’s attribute names are the ones labelling the resulting table. Possible Mismatch!
  

# Nested Queries
### ANY, ALL, IN, EXISTS

- Inside where or having there can be predicates that operate on another SQL query, but there can also be subqueries within selections, or, more commonly, in from statements.

| COMMAND                                                                          	| DESCRIPTION                                                                                                                                                                                                                                                                                             	|
|----------------------------------------------------------------------------------	|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| select Attr1, Attr2, (SQLQuery...                                                	| Useful if you want to emulate a join.                                                                                                                                                                                                                                                                   	|
| select Attr1, Attr2, <br>    from (SQLQuery...                                   	| More common use of subquery.                                                                                                                                                                                                                                                                            	|
| [where \| having] AttrExpr <=\|<>\|<\|<=\|>\|>=> <br>    (SQLQuery...            	| Confronts AttrExpr directly with the SQLQuery.                                                                                                                                                                                                                                                          	|
| [where \| having] AttrExp <=\|<>\|<\|<=\|>\|>=> <any\|all>  <br>    (SQLQuery... 	| any: predicate is true if at least one row of the query’s result satisfies the comparison.<br>all: predicate is true if all the rows of the query’s result satisfy the comparison.<br>(“>= all” finds only the maximum value)                                                                           	|
| [where \| having] AttrExpr <in\|not in><br>    ( <valueSet \| SQLQuery...>       	| in: predicate is true if there is at least one row in the nested query satisfying AttrExpr.<br>(“in” equivalent to: “= any”)<br>not in: true if there are no rows in the nested query satisfying AttrExpr.<br>(“not in” equivalent to: “<> all”)<br>⚠️Schemas in in/not-in statement must be compatible! 	|
| where exists (SQLQuery...                                                        	| Returns true if there are elements in the subquery.  

- Nested queries that check multiple attributes at once require use of a Tuple Constructor:
	- where (Attr1, Attr2, ...) in ( select Attr1, Attr2, ... from ... );
- in|not in can also match multiple AttrExpr directly with a set of different values (equivalent to an OR):
	- where Attr1 in (1,4,5,...);

# Buckets
### CASE-WHEN-THEN-ELSE-END-AS

| COMMAND                                                                                                                                                        	| DESCRIPTION                                                                                                	|
|----------------------------------------------------------------------------------------------------------------------------------------------------------------	|------------------------------------------------------------------------------------------------------------	|
| select Attr <br>    case when (condition1) then “value1”<br>    case when (condition2) then “value2”<br>    else “defaultValue”<br>    end<br>as newColumnName 	| Adds in the result a column to the data retrieved containing the element declared after the matching THEN. 	|

# Window Functions
### OVER - PARTITION BY

- Window functions are functions that, for each row from a query, perform a calculation using rows related to that row. In other words they perform aggregate-like operations on a set of query rows. However, while an aggregate function groups query rows into a single result row, a window function produces a result for each query row.

# Editing Commands
### INSERT, DELETE, UPDATE

- All commands can operate on sets of tuples (set-oriented). Commands conditions can reference external tables.

| COMMAND                                                                                                                                                                                 	| DESCRIPTION                                                                                                                                                                                                                        	|
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------	|
| insert into TableName <br>    [(Attr1, Attr2)]<br>    < values (ValuesList1) \| SQLQuery1 ><br>    < values (ValuesList2) \| SQLQuery2 >                                                	| Values are matched via positional notation.<br>Without AttributeList all attributes are considered.<br>If AttributeList doesn’t contain all attributes, the others are set to default (if there is a default) or null.             	|
| delete from TableName [where Condition]                                                                                                                                                 	| Deletes all (cascaded) tuples that satisfy the condition.<br>Without the where statement, all tuples are deleted.                                                                                                                  	|
| update TableName set<br>    Attribute1 = <val\|SQLQuery\|null\|default>,<br>    ...<br>    [where Condition]                                                                            	| ⚠️Order of commands is significant, them being executed sequentially. There can be attributes updated twice! Where condition is necessary for selecting which rows to update.                                                       	|
| update TableName set<br>    Attribute1 = AttrExpr containing “X.Attr”,<br>    Attribute2 = AttrExpr containing “X.Attr”<br>    ...<br>    from (SQLQuery) as X<br>    [where Condition] 	| When using an SQL subquery to gather a value which you’ll need to calculate the new values to set on the attributes, if the attributes are many and the subquery is always the same, you can make the subquery only once, like so. 	|

- EMPTYING A TABLE: To empty a table without deleting it there are two ways:
	- by using “delete from TableName“ without any other specification: however, any serialized (or auto-incremented) index will resume from its latest value, and won’t be reset.
	- by using “truncate table TableName” which actually erases all memory of the table leaving only its structure, making it as new and resetting auto-incrementers. ⚠️truncate actually belongs to the DDL!
  
# Practical Notes

- COMMITTING CHANGES: In some db-environments and languages (like Oracle) it might be necessary to always commit all DML commands in order for them to take effect by using the command: “commit”.
