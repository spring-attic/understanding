### Related Resources

There's more to NoSQL than what is presented here. You may want to continue your exploration of NoSQL using Spring with the following

### Getting Started Guides

* [Accessing Relational Data][gs-relational-data-access]
* [Accessing Data with JPA][gs-accessing-data-jpa]
* [Accessing Data with GemFire][gs-accessing-data-gemfire]
* [Accessing Data with Neo4j][gs-accessing-data-neo4j]
* [Accessing Data with MongoDB][gs-accessing-data-mongo]

[gs-relational-data-access]: /guides/gs/relational-data-access/content
[gs-accessing-data-jpa]: /guides/gs/accessing-data-jpa/content
[gs-accessing-data-gemfire]: /guides/gs/accessing-data-gemfire/content
[gs-accessing-data-neo4j]: /guides/gs/accessing-data-neo4j/content
[gs-accessing-data-mongo]: /guides/gs/accessing-data-mongo/content


### Spring Data and NoSQL support

Here are links to Spring's NoSQL projects:

- [Spring Data JDBC Extensions](http://www.springsource.org/spring-data/jdbc-extensions)
- [Spring for Apache Hadoop](http://www.springsource.org/spring-data/hadoop)
- [Spring Data GemFire](http://www.springsource.org/spring-gemfire)
- [Spring Data Redis](http://www.springsource.org/spring-data/redis)
- [Spring Data MongoDB](http://www.springsource.org/spring-data/mongodb)
- [Spring Data Neo4j](http://www.springsource.org/spring-data/neo4j)
- [Spring Data Solr](https://github.com/SpringSource/spring-data-solr)
- [Spring Data Elasticsearch](https://github.com/BioMedCentralLtd/spring-data-elasticsearch)
- [Spring Data Couchbase](https://github.com/couchbaselabs/spring-data-couchbase)
- [Spring Data FuzzyDB](https://github.com/whirlwind-match/fuzzydb-spring/)

Each of these projects provides a simplified API to interact with their relevant data stores. They also employ a commonly shared [Spring Data Commons](http://www.springsource.org/spring-data/commons) to make it possible to write basic **save()**, **delete()**, **update()**, and **findXxxYyyZzz()** methods which automatically generate queries. This can provide a developer with a lot of data needs.

When a more customized query is needed, `@Query("<query string>")` can be used to annotate the method, allowing the developer to write a query in the data store's query language.