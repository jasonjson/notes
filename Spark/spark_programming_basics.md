
## Spark Programming Bascis

* A Resilient Distributed Dataset (RDD) is the most fundamental data object used in Spark programming. RDDs are datasets within a Spark application, including the initial dataset(s) loaded, any intermediate dataset(s), and the final resultant dataset(s). Most Spark applications load an RDD with external data and then create new RDDs by performing operations on the existing RDDs; these operations are transformations. This process is repeated until an output operation is ultimately required—for instance, to write the results of an application to a filesystem; these types of operations are actions.
* An key property of RDDs is their immutability, which means that after they are instantiated and populated with data, they cannot be updated. Instead, new RDDs are created by performing transformations such as *map* or *filter* functions.
* The initial RDD can be created in several ways, including loading data from a file or files, loading data from a data source, such as a SQL or NoSQL datastore, loading data programmatically, loading data from a stream.

