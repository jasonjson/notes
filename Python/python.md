
## Decorators
* A decorator is a tool for wrapping code around functions or classes. Decorators then explicitly apply that wrapper to functions or classes to cause them to "opt in" to the decorator's functionality. Decorators are extremely useful for addressing common prerequisite cases before a function runs or ensuring cleanup after a function runs.
* As its core, a decorator is a callable that accepts a callable and returns a callable. A decorator is simply a function that accepts the decorated function as its positional argument. The decorator takes some actions using that argument, and then either returns the original argument or some other callable.
* The decorator is assumed to take a single, positional argument, which is the method being decorated. When the @syntax is being used, decorators are applied immediately after the decorated callable is created. If you use multiple decorators using the @ syntax, they are applied in order, from bottom to top.
* Python implements a decorator called `@functools.wraps` that copies the important introspection elements of one function onto another function.
* The reusability and maintainability is part of what makes decorators valuable. Essentially, decorators are tools to avoid repeating yourself, and part of their value is in providing hooks for future maintenance.
*

## optparse and argparse

`parser = optparser.OptionParser()`

* Any argument that begins with hyphens is expected to be an option, and an exception is raised if you try to send an option that the parser dose not recognize.
* There are two common types of options. One type is called a flag or a switch, which is an option that dose not require or accept a value along with the option. Another type is one that does accept a value. The basic tradeoff between these two types is that the former is quicker to type on the CLI, whereas the latter is more explicit.
* Available values: short-form, long-form, action, dest, help, default, type.
* Availabe actions: `store_true, store_false, count, append, store`
* Any arguments that are not attached to an option will be considered by the parser to be a positional argumen
* Counter flag is to allow specifying a flag multiple times to intensify the effect. You do this through a different action value: count and a default value: 0 or anything you decide.
* You may accept multiple values for the same option, and use them as a list. You do this through an action value: append and a default value: [].


`parse = argparser.ArgumentParser()`

* In `argparser`, you need to provide both positional arguments and options through the `add_argument` method of `ArgumentParser` Objects
* You can change which characters are used for prefixes by providing the `prefix_chars` keyword argument to the `ArgumentParser` constructor.
* `ArgumentParser` adds the capability to specify that an option may only be one of an enumerated set of choices.
* You can set `nargs` keyword argument too accept an unbound number of arguments. or an exact number. However, the value will be in a list, even if you specify a `nargs` value of 1. You may also allow any number of arguments by providing `+` or `*` to `nargs`.
* The `argparse` module provides a special class `argparse.FileType` that can be sent to the `type` keyword. It's generally useful for reading configuration files.


## Asyncio

* The fundamental way that most asynchronous applications work is via an **event loop** that runs in the background. When something needs to run, it is registered to the event loop, which becomes a **task**.
* Tasks are primarily registered to the loop using `call_soon`, which operates as a FIFO queue. It's also possible to register a task called until later using `call_later` method.
* Most `asyncio` mehtods only take function objects (or other callables). The `functools.partial` method itself takes the arguments and keyword arguments that must be passed to the underlying function.
* A **coroutine** is a special kind of function designed to run within an event loop. You can make a function into a coroutine by decorating it with `@asyncio.coroutine`. Howver, the function created is a special generator consumeed by the event loop and you can no longer call it the regular way.
* You can add a callback to any `Future` object by using the object's `add_done_callback` method. Callbacks are expected to take a single argument, which is the `Future` object itself.
* It is possible to send other arguments to a callback through the use of `functools.partial`. In practice, the `Future` is appended to the end of the positional arguments list before the callback is called.
* The `asyncio` module provides a convenient way to aggregate tasks for two reasons: the first is to take some sort of action once any task in a set of tasks has completed, the second is to take some sort of action once all tasks in the set have completed.
* In the case of a task created with `asyncio.gather`, the result is always a list, which contains the results of the individual task that were gathered. The order of the list of results is guaranteed to be the same order in which the tasks were gathered (but the tasks are not guaranteed to be run in that order).
* The `asyncio.wait` coroutine takes a sequence of coroutines or tasks and returns once they are done. Additionaly, `wait` accepts a parameter to return when **any** of its tasks complete. The `wait` method always returns a two-tuple, with the first element being the `Future` objects that have completed, and the second element being those are still pending.
* It is possible to pass the `timeout` keyword argument to have the `asyncio.wait` coroutine return when a specific amount of time has passed, regardless of whether all of the tasks have completed.
* A **queue** is a collection of tasks to be processed by a task runner. Two methods `put_nowait` and `get_nowait` are designed to perform addition or removeal of the item to or from the queue immediately. Another method `get` will patiently wait for an item to be added to the queue, and then retrieve it from the queue and return it immediately. It's possible to give a **queue** object a maximum size, by setting the `maxsize` keyword argument.

## Style

* Writing a comment block explain what the code is doing is better than doing so for every few lines of code. If a somewhat complex algorithm is being used, consider including a link to an article explaining the pattern and providing other examples of its use.
* **PEP 8** designates that two blank lines should seperate "top level" classes and function definitions in a module. After the top level, class and function definitions should be seperated by one blank line each.
* Consider keeping imports grouped by the packages that they come from. Within each group, sort imports by alphabetical order.
* Ensure that comments are kept up to date. If the code changes, the comments may need to change along with it. You do not want to end up with a series of comments that actually contradict the code.


