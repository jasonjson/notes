## Basic RDD Transformations

* The `map()` transformation is the most basic of all transformations. It evaluates a named or anonymous fucntion for each element within a dataset partition. One or many `map()` functions can run asynchronously, which are shared nothing operations.
