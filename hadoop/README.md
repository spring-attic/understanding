# Understanding Hadoop

[Apache™ Hadoop®](https://hadoop.apache.org/) is an open-source project that provides reliable, scalable, distributed computing.

The Apache Hadoop software library is a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It can scale up from single servers to thousands of machines, each offering local computation and storage. Rather than relying on hardware to deliver high-availability, the library itself detects and handles failures at the application layer. It delivers a highly-available service on top of a cluster of computers, each of which may be prone to failure.

Hadoop supports multiple programming models including:
- Map/Reduce. Divides a big task into small tasks (map) and then aggregates the results back together (reduce).
- HDFS (Hadoop Distributed File System). Collects raw data files from multiple locations in preparation for other processing.
- Batch jobs. Run scheduled tasks against chunks of data.

### Hive, Pig, and other Hadoop-based systems

[Hive is a data warehouse system](https://hive.apache.org/) that provides the means to query Hadoop file systems with a SQL-like language called HiveQL.

[Apache Pig](https://pig.apache.org/) is a platform for analyzing large sets of data using map-reduce programs. The name is based on its query/map-reduce language, Pig Latin.

Many other systems are being built on top of Hadoop. It is being used as a distributed, fault tolerant infrastructure. Examples include [Cassandra NoSQL database](https://cassandra.apache.org/), and [HBase](https://hbase.apache.org/).

## Challenges

Hadoop is used to solve complex problems. Some problems require real-time response based on current incoming data. Other solutions are based on analyzing months of historical data. In many circumstances, companies must do multiple forms of analysis. 

For example, a company may need to digest current incoming data and detect trending topics based on the past 24 hours. But the company may also need to analyze traffic flow for the past 12 months to generate a histogram that helps them plan an expansion of their data center. Companies that serve [CDN-based assets](https://en.wikipedia.org/wiki/Content_delivery_network), like movies or videos, need to analyze traffic patterns to predict viewing trends.

These variants of data consumption and analysis can require a mixture of map-reduce, batch jobs, and collecting long term data in a Hadoop cluster. A Hadoop system can be used to collate data based on network traffic while also gathering actual system log files from servers. Companies are prone to hold this Big Data forever to preserve the ability to run an analysis sometime in the future.

These approaches are inherently complex. It's difficult if not impossible to handle large volumes of data with a single tool or language, which in turn makes it challenging to just "pick up" Hadoop and start using it quickly.


## Summary

Hadoop by itself offers a powerful system, with many complexities that have generated various libraries and tools. In the past, this complexity might have caused such a project to fall by the wayside. But network traffic driven by social media and web services (Facebook, Twitter, Netflix, and so on) demands a means to manage large volumes of data.

