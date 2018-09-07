## functools - high-order functions and operations on callable objects

### lrc_cache(maxsize=128, typed=False)

* Decorator to wrap a function with a memorizing callable that saves up to the *maxsize* most recent calls. It can save time when an expensive or I/O bound function is periodically called with the same arguments.
* If *maxsize* is set to `None`, the LRU feature is disabled and the cache can grow without bound. The LRU feature performs best when `maxsize` is a power-of-two.
* If `typed` is set to `True`, function arguments of different types will be cached separately.
* To help measure the effectiveness of the cache, the wrapped function is instrumented with a `cache_info()` function that returns a named tuple showing *hits, misses, maxsize, currsize*.
* Examples of efficiently computing **Fibonacci numbers** using a cache to implement a dynamic programming technique:
``` python
@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n - 1) + fib(n - 2)

[fib(n) for n in range(16)]
fib.cache_info()
fib.cache_clear()
```

### total_ordering

* Given a class defining one or more rich comparison ordering methods, this class decorator supplies the rest. This simplifies the effort involved in specifying all of the possible rich comparison operations. The class must define one of __lt__, __le__, __gt__ or __ge__, and __eq__ method.
* While this decorator makes it easy to create well behaved totally ordered types, it dose not come at the cost of slower execution and more complex stack traces for the derived comparison methods.

### partial(func, *args, **kargs)

* Return a new partial object which when called will behave like *func* called with the positional arguments and keyword arguments. If more arugments are supplied to the call, they are appended to `args`. If additional keyword arguments are supplied, they extend and overwrite `kargs`.
* The `partial()` is used for partial function application which "freezes" some portion of a function's arguments and/or keywords resulting in a new object with a simplified signature:
``` python
from functools import partial
basetwo = partial(int, base=2)
basetwo('10010')
```

### reduce(function, iterable, [, initializer])

* Apply function of two arguments cumulatively to the items of sequence, from left to right, so as to reduce the sequence to a single value. For example, `reduce(lambda x, y : x + y, [1, 2, 3, 4, 5])` calculates `((((1+2)+3)+4)+5)`. The left argument, x, is the accumulated value and the right argument, y, is the update value from the sequence.

### wraps(wrapped, assigned=WRAPPER_ASSIGNMENTS, updated=WRAPPER_UPDATES)

* Update a wrapper function to look like the wrapped function. The main intended use for this function is in decorator functions which wrap the decorated function and return the wrapper. If the wrapper function is not updated, the metadata of the returned function will reflect the wrapper definition rather than the original function definition, which is typically less than helpful.
