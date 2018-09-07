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
