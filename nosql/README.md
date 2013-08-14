# Understanding NoSQL

_NoSQL_ refers to a database that is not based on SQL (Structured Query Language), which is the language most commonly associated with **relational** databases. Essentially, NoSQL data isn't relational, NoSQL databases usually do not have schema, and they come with looser consistency models than traditional relational databases do.

The term "NoSQL" refers to the fact that traditional relational databases are not adequate for all solutions, particularly ones involving large volumes of data. But the term has been extended to also mean "Not only SQL", indicating support for potential SQL-based interfaces even if the core database isn't relational. Software developers that use NoSQL solutions don't necessarily advocate dismissing relational databases, but instead see value in using the right data store for the job.

## Use of NoSQL

NoSQL data stores respond to key data needs that are not met by relational databases.

### Caching solutions
Caching results is a common solution to improving application response. For example, a website may be feeding the same answers to hundreds of thousands of users. Instead of taxing a relational database to recompute the same thing, custom caching solutions can be implemented manually. Several NoSQL data stores provide a similar solution, but the developer does not have to maintain a custom cache.

### Key-value stores
Some NoSQL databases store key-value pairs to allow quick lookups, for example, in the case of question/answer access. Relational databases are more oriented towards storing complex data and various relationships between different types of data. This methodology is overcomplicated when a developer wants to implement a quick way to store and access Q&A data.

### Document stores
Other types of data are more document oriented and have variations. For example, forms of data can have many optional fields. Relational databases with their rigid schemas require all othese fields to be defined for every row of stored data. Document-based NoSQL stores are more flexible and efficient in handling this.

### Faster access to bigger sets of data
Relational databases sacrifice performance when searching large volumes of data. Historically, developers have built systems in which writing SQL queries to find a few rows of data involved thinning out data sets in the most efficient way. The bigger the result set, though, the more expensive the queries become. Large volumes of data or queries that involve aggregating large amounts of data are referred to as "data warehousing."

NoSQL data stores are becoming widely adopted and are being tested in many situations. These situations involve large volumes of data as well as large rates of data growth in many consumer systems.

### Less rigid consistency requirements 

NoSQL is also considered an alternative to traditional relational databases because certain consistency requirements that are inherently part of relational databases are very different in modern enterprises.

Developers are discovering that certain data requirements don't demand the rigid [ACID model](https://en.wikipedia.org/wiki/ACID) of relational databases that usually comes with worse performance. Instead they can meet their needs using [eventual consistency][eventual-consistency] that tends to come with better performance. Some NoSQL data stores even allow the developer to pick how loose or rigid the consistency must be.

## Limitations of NoSQL
SQL is a powerful, 40-year-old standard that has been possible because all relational databases have the same concept of storing data in tables and relating data through foreign keys. Although switching from one relational database to another isn't 100% transparent, it is much easier than switching between two different NoSQL data stores. Developers that have learned SQL have little challenge switching between vendors. 

Because each NoSQL data store has unique aspects in both how its data is stored as well as how different bits of data relate to each other, no single API manages them all. When embracing a new NoSQL data store, the developer must invest time and effort to learn the new query language as well as the [consistency semantics][eventual-consistency].

## NoSQL database examples

Dozens of NoSQL data stores are available; the following are among the most popular:

- [MongoDB](http://www.mongodb.org/). Open-source document database.
- [CouchDB](http://couchdb.apache.org/). Database that uses JSON for documents, JavaScript for MapReduce queries, and regular HTTP for an API.
- [GemFire](http://www.springsource.org/spring-gemfire). Distributed data management platform providing dynamic scalability, high performance, and database-like persistence.
- [Redis](http://redis.io/). Data structure server wherein keys can contain strings, hashes, lists, sets, and sorted sets.
- [Cassandra](http://cassandra.apache.org/). Database that provides scalability and high availability without compromising performance.
- [memcached](http://memcached.org/). Open source high-performance, distributed-memory, and object-caching system.
- [Hazelcast](http://www.hazelcast.com/). Open source highly scalable data distribution platform.
- [HBase](http://hbase.apache.org/). Hadoop database, a distributed and scalable big data store.
- [Mnesia](http://www.erlang.org/doc/man/mnesia.html). Distributed database management system that exhibits soft real-time properties.
- [Neo4j](http://www.neo4j.org/). Open source high-performance, enterprise-grade graph database.


[eventual-consistency]: https://en.wikipedia.org/wiki/Eventual_consistency