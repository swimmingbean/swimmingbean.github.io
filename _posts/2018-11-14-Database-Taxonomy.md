---
layout: post
title: Database Taxonomy
---
# Making sense of the many different databases

(!) WORK IN PROGRESS

Cassandra, HBase, Redis, PostgreSQL, MongoDB..with so many database names
dropped casually in conversation, getting a handle on the different types of
databases is the first step to cutting through the jargon. It helps to place new
beasts in context with the databases you already know and love and it helps you
select a DB appropriate for your needs.

![]({{ site.baseurl }}/images/database-taxonomy/animal-taxonomy-diagram.png)

## At a Glance
![]({{ site.baseurl }}/images/database-taxonomy/databases-classification.png)

## The Vocabulary

## Different ways of Modeling Data
### Relational database:
* Data is modeled in a tabular format as relations between rows and columns with data stored in each cell.
* Each row in a table has a unique identifier
* There are pre-defined relationships between data from different tables
* Usually have ACID properties

| Benefits | Caveats |
| :------- | :------ |
| highly structured data | fixed schema - schema changes require schema to versioned and some procedure to migrate data  when schema is updated|
| can be queried by SQL | |
| good for data integrity ||

### Document Oriented database:
* Non-relational database
* Stores data in JSON, XML or BSON documents
* No fixed schema

| Benefits | Caveats |
| :------- | :------ |
| good for semi-structured or unstructured data | does not exhibit ACID properties |
| individual documents can have structure but the structure is not required to be uniform across all documents ||
| easy to scale horizontally ||


### Key-value database:
* Also known as key-value stores.
* All data is stored as a collection of key+value pairs
* No fixed schema
* The keys are all unique. Specific DBs may require a specific format or length for the key
* Values can be any kind of structured or unstructured data

| Benefits | Caveats |
| :------- | :------ |
| No fixed schema | Cannot query data by value or part of value. Eg: return all entries that contain the text "Apple" |
| This model lends itself to scale horizontally by distributing data over many machines | Difficult to edit values. Not good for data that is changing frequently |
| Ease of data distribution makes it easy to scale DB on demand and to make the DB highly available | Not all data can be modeled as key-value pairs |
| Well suited to storing unstructured data| |

### Graph database:
* Data is stored as a set of nodes and a set of edges
* Nodes and edges can have attributes associated with them
* Relationships between data entities are as important (and have their own attributes) as the entities themselves
* Query results can be found by traversing the graph

| Benefits | Caveats |
| :------- | :------ |
| good for highly interconnected data - ie frequent many-to-many relationships | |
| | |

### Wide Column store database:
* Tabular with dynamic columns  - each row can have different columns
* Can be visualized as a 2-dimensional key-value store

## Attributes of Data
### Structured vs Semi-structured vs Unstructured data:
**Structured data** is data which can be stored in database SQL in table with rows and columns.
This data has a relational key and can be easily mapped into pre-designed fields

**Semi-structured data** is data like JSON or XML files that has some internal structure but is not a relational structured

**Unstructured** data is basically an opaque bag of bits. Eg: binary data, videos, images, text, sensor data

### Data normalization:

### SQL database:
Supports SQL (Structured Query Language)

### No SQL database:
* No SQL is a bit of a mis-nomer. It is better called "Not only SQL"
* Compared to relational DBs, non-sql DBs make it easier to spread data across multiple servers which allows for easier and cheaper storage of really large datasets
* Easier to distribute and replicate data means its easier to make the data highly available

### ACID properties:
Atomicity, Consistency, Isolation, and Durability

### CAP Theorem:

### Data Integrity:

### Distribution:

### Replication:

### Sharding:
