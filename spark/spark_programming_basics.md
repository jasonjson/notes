
## Spark Programming Bascis

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

* Operations
