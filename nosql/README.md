# Understanding: NoSQL

## Overview

NoSQL stands for a database that is not based on SQL (Structured Query Language), the language most commonly associated with **relational** databases. Essentially, NoSQL data isn't relational, their databases are usually schema-less, and they come with looser consistency models than traditional relational databases.

The term "NoSQL" arises as a response that traditional relational databases are not adequate for all solutions, particularly ones involving large volumes of data. But the term has been extended by some to also mean "Not only SQL", indicating support for potential SQL-based interfaces even if the core database isn't relational. Software developers that use NoSQL solutions don't necessarily advocate totally dismissing relational databases, but instead see value in using the right data store for the job.

## Use of NoSQL

NoSQL data stores sprang up due to key data needs that were not being met by relational databases.

### Caching solutions
A commonly seen solution to increase application response has been caching results. One example is that a website may be feeding the same answers to hundreds of thousands of users. Instead of taxing a relational database to recompute the same thing, caching solutions have often been implemented by hand. Several NoSQL data stores are aimed at providing a similar solution with the benefit of the developer no longer having to maintain their custom cache solution.

### Key-value stores
Another area that has seen much popularity has been the need to store pairs of data to allow quick lookups. Another way to view this is question/answer access. Relational databases are more oriented towards storing more complex data along with various relationships between different types of data. This has been viewed as overcomplicated when the developer is trying to put together a quick way to store Q&A data.

### Document stores
Other types of data that people work with are more document oriented, and have variations. For example, forms of data may have many optional fields. Relational databases with their rigid schemas would require all of these fields be defined for every row of stored data, but document-based NoSQL stores are more flexible and efficient in handling this.

### Faster access to bigger sets of data
Something that relational databases have often suffered is a lack of performance when searching large volumes of data. Developers have historically developed systems where writing SQL queries to find a few rows of data often involved thinning out data sets in the most efficient ways possible. The bigger the result set, though, the more expensive queries have typically taken. Large volumes of data or queries that involved aggregating large amounts of data have sometimes been referred to as **data warehousing**.

NoSQL data stores are undergoing a huge adoption and being tested in many situations. This often involves large volumes of data as well as large rates of data growth in many consumer systems based on lack of adequacy from existing relational databases. They are also being investigated given that certain consistency requirements that are inherently part of relational databases are very different in modern enterprises.

## Side effect of NoSQL
Because each NoSQL data store has unique aspects different from others, there has yet to emerge any single API that manages them all. SQL has been a powerful standard in use for the past 40 years, but it isn't adequate for NoSQL access. While switching from one relational database to another isn't 100% transparent, it is much easier than switching from between two different NoSQL data stores.

## NoSQL Database Examples

While there are literally dozens of NoSQL data stores in existence, here is a list of some of the most popular:

- [MongoDB](http://www.mongodb.org/) - an open-source document database
- [CouchDB](http://couchdb.apache.org/) - a database that uses JSON for documents, JavaScript for MapReduce queries, and regular HTTP for an API
- [GemFire](http://www.springsource.org/spring-gemfire) - distributed data management platform providing dynamic scalability, high performance, and database-like persistence
- [Redis](http://redis.io/) - a data structure server where keys can contain strings, hashes, lists, sets and sorted sets
- [Cassandra](http://cassandra.apache.org/) - a database that provides scalability and high availability without compromising performance
- [memcached](http://memcached.org/) - open source, high-performance, distributed memory object caching system
- [Hazelcast](http://www.hazelcast.com/) - open source highly scalable data distribution platform
- [HBase](http://hbase.apache.org/) - the Hadoop database, a distributed, scalable, big data store
- [Mnesia](http://www.erlang.org/doc/man/mnesia.html) - a distributed DataBase Management System that exhibits soft real-time properties
- [Neo4j](http://www.neo4j.org/) - an open-source, high-performance, enterprise-grade graph database.

This list is by no means exhaustive.


