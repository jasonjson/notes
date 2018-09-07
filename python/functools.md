## functools - high-order functions and operations on callable objects

### `lrc_cache(maxsize=128, typed=False)`

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

* `total_ordering` - Given a class defining one or more rich comparison ordering methods, this class decorator supplies the rest. This simplifies the effort involved in specifying all of the possible rich comparison operations. The class must define one of __lt__, __le__, __gt__ or __ge__, and __eq__ method.
