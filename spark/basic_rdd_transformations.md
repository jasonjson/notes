### Basic RDD Transformations

* The `map()` transformation is the most basic of all transformations. It evaluates a named or anonymous fucntion for each element within a dataset partition. One or many `map()` functions can run asynchronously, which are shared nothing operations.

* The `flatMap()` transformation is similar to the `map()` in that it runs a function against each record in the input dataset. However, it "flattens" the output, meaning it removes a level of nesting.

* The `filter()` transformation evaluates a Boolean expression, usually expressed as an anonymous function, against each element in the dataset. The boolean value returned determines whether the record is included in the resultant output RDD.
