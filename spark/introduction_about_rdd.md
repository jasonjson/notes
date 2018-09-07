## Introduction abour RDD

* A Resilient Distributed Dataset (RDD) is the most fundamental data object used in Spark programming. RDDs are datasets within a Spark application, including the initial dataset(s) loaded, any intermediate dataset(s), and the final resultant dataset(s). Most Spark applications load an RDD with external data and then create new RDDs by performing operations on the existing RDDs; these operations are **transformations**. This process is repeated until an output operation is ultimately required—for instance, to write the results of an application to a filesystem; these types of operations are actions.

* An key property of RDDs is their immutability, which means that after they are instantiated and populated with data, they cannot be updated. Instead, new RDDs are created by performing transformations such as *map* or *filter* functions.

* The initial RDD can be created in several ways, including
    1. loading data from a file or files using `textFile()` or `wholeTextFiles()`
    2. loading data from a data source, such as a SQL or NoSQL datastore using `read.jdbc()`
    3. loading data form JSON files using `read.json()`
    4. loading data programmatically using `parallelize()` or `range()`
    5. loading data from a stream.

* If you are creating a RDD from a file on your local filesystem - you needdc to ensure that the file you are loading is available in the same relative path on all worker nodes in the cluster. For this reason, it's preferrable to use a distributed filesystem such as HDFS or S3 as a file-based source.

* Java Database Connectivity (JDBC) is a popular Java API for accessing differenet database management systems, managing functions such as connecting and disconnecting from a DBMS and runing quries. Database vendors typically provide drivers or connectors to provide access to their database platforms via JDBC.

* Operations performed against RDDs are considered to be coarse grained as they apply a function again every element in the dataset, and they return a new dataset with the transformations applied. In contrast to **corse-grained transformation**, **fine-grained transformations** can manipulate a single record or data cell, such as single-row updates in a relational database.

* Spark use lazy evaluation, also called lazy execution, in processing spark programs. Lazy evaluation defers processing until an action is called. Each transformation method is parsed for syntax and object references only. After requesting an action, a DAG is created along with logical and physical execution plans. The **Driver** then orchestrates and manages these plans across **Executors**.

* By default, RDDs are transient objects that exist only while they are required. After they transform into new RDDs and aren't needed for any other operations, they are removed permanently. An option to address this is to cache or persist the RDD by using the `persist()` method. You can see the persisted RDD in Spark application UI in the Storage tab.

* Narrow operations are categorized by: operations can collapse into a single stage, only one child RDD depends on the parent RDD, no shuffling of data between nodes is required. Wide operations are defined as: operations define new stages and often require shuffling, RDDs have multiple dependencies. Wide operations are unvoidable when grouping, reducing or joining datasets, but be aware of the impacts and overhead involved with these operations.

* There ares some speific RDD implementations that enable additional operators and functions:
    1. PairRDD: key/value pairs
    2. DoubleRDD: a collection of double values only
    3. DataFrame: a distributed collection of data organized into name and typed columns.
    4. SequenceFileRDD: created from a SequenceFile, either compressed or uncompressed.
    5. HadoopRDD: provides core functionality for reading data stored in HDFS.
    6. ShuffledRDD: resulting RDD from a shuffle, such as repartitioning of data
    7. UnionRDD: resulting from a `union()` operation again two or more RDDs
