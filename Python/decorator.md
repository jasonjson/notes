## Decorators

* A decorator is a tool for wrapping code around functions or classes. Decorators then explicitly apply that wrapper to functions or classes to cause them to "opt in" to the decorator's functionality. Decorators are extremely useful for addressing common prerequisite cases before a function runs or ensuring cleanup after a function runs.
* As its core, a decorator is a callable that accepts a callable and returns a callable. A decorator is simply a function that accepts the decorated function as its positional argument. The decorator takes some actions using that argument, and then either returns the original argument or some other callable.
* The decorator is assumed to take a single, positional argument, which is the method being decorated. When the @syntax is being used, decorators are applied immediately after the decorated callable is created. If you use multiple decorators using the @ syntax, they are applied in order, from bottom to top.
* Python implements a decorator called `@functools.wraps` that copies the important introspection elements of one function onto another function.
* The reusability and maintainability is part of what makes decorators valuable. Essentially, decorators are tools to avoid repeating yourself, and part of their value is in providing hooks for future maintenance.
