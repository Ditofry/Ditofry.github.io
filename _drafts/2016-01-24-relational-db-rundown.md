---
layout: post
title:  "Relational Databases rundown"
categories: sql code reference
---
## General
Superkey is any set of attributes that could be used to uniquely identify a record.
Candidate key is a minimal set of attributes is a minimal set of keys used to identify
a record.
Primary key is the main key that we'll be using to identify rows in a database.
Relational model is based on Set Theory, in SQL no to rows can be identical.
Surrogate vs. Natural Keys

## Open Source Relational Databases
### SQLite
SQLite is often not given the credence that it deserves since it's frequently used as a
substitute for a "real" database until the application using said database is ready for
some RILL DATA!!!  What's great about SQLite is subtly evidenced in this very use-case, however.
Many frameworks ship with SQLite as a test database because **it's so simple to embed.**
There's no way it should be used as a production database for a centralized application
architecture that serves lots of users as an API or Web Application, but it does work
wonderfully as a production embedded data store, say in a mobile app.  It's also insanely
easy to implement cross-platform as it's C-based and completely self-contained.
### PostgreSQL
### MySQL

## Joins

### Inner Join
Only records that match are returned
**JOIN** is really just a shortcut for **INNER JOIN**, which is the "middle" or overlap of the
van diagram

### Outer Join
May return records that do not match the filter condition.
LEFT JOIN, RIGHT JOIN syntax signifies which table has "optional" values

## ACID
Atomic - transactions are all or nothing
Consistent - all transactions must leave database in a valid state as per constraints
Isolated - ordering is preserved in the of concurrency
Durable -

## MySQL Commands

**Run Command Line Tool**
mysql --user=*username* --password=*pwd* (optional)db_name
mysql> CREATE DATABASE example_name;
