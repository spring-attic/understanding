# Understanding Hadoop

## Overview

[Apache™ Hadoop®](http://hadoop.apache.org/) is an open-source project that provides reliable, scalable, distributed computing.

The Apache Hadoop software library is a framework that allows for the distributed processing of large data sets across clusters of computers using simple programming models. It is designed to scale up from single servers to thousands of machines, each offering local computation and storage. Rather than rely on hardware to deliver high-availability, the library itself is designed to detect and handle failures at the application layer, so delivering a highly-available service on top of a cluster of computers, each of which may be prone to failures.

Hadoop supports multiple programming models including:
- Map/Reduce - a way to split up a big task in small tasks (map) and then aggregate the results back together (reduce)
- HDFS (Hadoop Distributed File System) - a way to collect raw data files from multiple locations in preparation for other processing
- Batch jobs - a way to run scheduled tasks against chunks of data

### Hive

[Hive is a data warehouse system](http://hive.apache.org/) that provides the means to query Hadoop file systems with a SQL-like language called HiveQL.

### Pig

[Apache Pig](http://pig.apache.org/) is a platform for analyzing large sets of data using map-reduce programs. The name is based on its query/map-reduce language, Pig Latin.

There are many other systems being built on top of Hadoop. It is being used as a distributed, fault tolerant infrastructure. Examples include [Cassandra NoSQL database](http://cassandra.apache.org/), and [HBase](http://hbase.apache.org/).

## Challenges

Hadoop is used to solve complex problems. Different problems require different solutions. For example, some problems require real time response based on current incoming data. Other solutions are based on running an analysis on months of historical data. In many circumstances, companies may need to do multiple forms of analysis. 

For example, the company may need to digest current incoming data and detect trending topics based on the past 24 hours. But the company may also need to analyze traffic flow for the past 12 months to generate a histogram so they can plan expansion of their data center. Companies that serve [CDN-based assets](https://en.wikipedia.org/wiki/Content_delivery_network), like movies or videos, may need to analyze traffic patterns to best predict viewing trends.

All of these variants of data consumption and analysis can require a mixture of map-reduce, batch jobs, and collecting long term data in a Hadoop cluster. A Hadoop system can be used to collate data based on network traffic while also gathering actual system log files from servers. This can result in a collection of Big Data. Companies are prone to hold this data forever to preserve the ability to run an analysis sometime in the future.

All of these various approaches for tackling large volumes of data is inherently complex. Hence, it's hard if not impossible to fit into a single tool or language. This also makes it hard to just "pick up" Hadoop and start using it quickly.


## Summary

Hadoop by itself offers a powerful system, but many aspects of it can be complex to embrace. This has generated the various libraries and tools. In the past, this might have caused such a project to fall by the wayside. But due to the increase of network traffic driven by social media and web services (Facebook, Twitter, Netflix, etc.), there is an increasing need to manage such large volumes of data.

