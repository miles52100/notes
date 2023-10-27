# Databases

A basic distinction is between *relational* and *non-relational* databases.


## Relational databases

Stores data in relational tables.
Tables defined by columns and rows
Each row identified by unique key, so can link rows in different tables
Each table includes a primary key, identifying the info. found within the table, e.g., one table might have the key 'customer information' that relates to info in a different table with key 'order information'.


Separates the logical structures of tables and indexes from physical storage. So you can make changes to physical storage but leave the logical structure unchanged.

Relational databases infer a focus on relationships 
bewteen data in a particular way. The relational focus is between the columns of data tables and not between the data points.

Complex queries in relational databases require complex joins on data tables, so is a somewhat slower process than similar queries on a graph based database.


### Main Use cases
Transaction-focused:
  - online transactions
  - accounting.




## Non-relational databases
A graph-database stores data as a graph
What distinguishes graph-databases from other database technologies is they **document and prioritise the relationships between data**

Designed for flexibility and scalability

An additional benefit from this emphasis is that mapping relationships makes graph databases a good fit for data visualisation.

### Main Use cases
Relationship heavy needs: 
  - fraud detection 
  - recommendation engines.


## Knowledge Graphs
Frequently cited examples of Knowledge Graphs, KGs, are Facebook and LinkedIn.
The information about the people is valuable, but the connections between those entities is even more valuable.


Graph databases store relationships in a triple format: subject, predicate and object.

E.g.
Subject       Predicate        Object
Diabetes      In and           Insulin
              indication for

Sir Frederick Discovered       Insulin
G Banting


Other database technologies have been designed for efficiency in terms of storage, management and retrieval of data, often with batch processing in mind. Graph databases are increasingly being used for machine learning applications and are designed to facilitate browsing to reveal unusual patterns and connections. The applications are so groundbreaking and far-reaching that an entirely new field of graph data science has emerged.


### From graph databses to KGs

A KG, also known as a sematic network, represents a network of real-world entities - i.e. objects, events, situations, or concepts - and illustrates the realtionship between them. This information is usually stored in a graph database and visualized as a graph structure, prompting th term 'graph'.

Graphs databases have their own query languages (GQLs)
that allow seamless access to the relationships in the database.
 - SPARQL
 - Cypher
 - Gremlin

are some examples of GQLs.

GQLs are typically used to find relationships, and those relationships are displayed in a KG

KGs give you the tools to analyze and visualise the information in a graph database.

For DL learning on graphs see [Geometric Deep Learning](../data_science_notes/geometric_deep_learning.md) notes.


---
---
# PWD Example

## The relational DB setup

Here I'm going to mock up a relational database for storing pwds, to serve as an example of a query needing a join

We'll have two tables
Table 1: "Pwd_Attributes"
Table 2: "Hash_Technology"

Table 1 might look like

id | SHA(pwd) | pwd_str | lang | tech_id | num_times
|--|----------|---------|------|---------|----------
1  |  ?       |  ?      | L1   |  1      | 500
2  |  ?       |  ?      | L2   |  4      | 3
3  |  ?       |  ?      | L3   |  2      | 1
4  |  ?       |  ?      | L1   |  2      | 15
5  |  ?       |  ?      | L5   |  7      | 1

Table 2 might look like

id | tech_name | memory_hard | hardware
---|-----------|-------------|-----------
1  |  T1      |  F           |      H2  |
2  |  T2      |  F           |      H2  |
3  |  T3      |  T           |      H1  |
4  |  T4      |  T           |      H3  |
5  |  T5      |  F           |      H2  |

We might want to ask how many pwds have a memory_hard tech that is F and num_times > 10?

SQL query would need an inner join
```
SELECT pa.id t.mh
FROM Pwd_Attributes pa Hash_Technology t
WHERE pa.num_times > 10
WHERE t.memory_hard == F
WHERE pa.tech_id = t.id
```

We then count the rows in the returned INNER JOIN table


## The graph database setup

One way to do this might be to have different types of nodes:

  - pwd_node: labeled with SHA-hash of pwd
  - tech_node: labeled by tech
  - lang_node: labeled with lang or n/A or LUNO, Geometric etc.

We would then have edges 
l_node --- p_node --- property -- t_node

To indicate the pwd_node p_node was used with technology t_node, and what lang the pwd was
The edge property for p to t node could be a list:
 - num_times
 - memory_hard
 - hardware

 There may be no edge property for l to p 

 To ask the same query is to aske the graph
 for the number of p_nodes
 with edges to t_nodes with edge property
 num_times > 10
 memory_hard == F


 

---
---

### References
[1 - Key Differences](https://www.techtarget.com/searchdatamanagement/feature/Graph-database-vs-relational-database-Key-differences)
[2- graph-database-use-cases](https://www.profium.com/en/blog/graph-database-use-cases/)
[3 - graph databases and knowledge graphs](https://blog.resolute.ai/graph-databases-and-knowledge-graphs)