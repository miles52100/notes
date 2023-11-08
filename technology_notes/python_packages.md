# Python Packages 
A short note on some python packages and what they do.


## Misc.

  * pyenv - simply version management tool, see [here](https://github.com/pyenv/pyenv#installation)

  * Django - high level Python web framework encourages rapid development and clean and pragmatic design. See [DJ4E](https://www.dj4e.com/lessons)


## Standard Library

  * pickle module - implements binary protocols for serializing and de-serializing an Python object structure, see [here](https://docs.python.org/3/library/pickle.html?highlight=pickle#module-pickle)
  
  * inspect module - useful functions to get info about live objects such as modules, classes, methods,..,e.g., it can help you examine the contents of a class, retrieve the source code of a method, extract and format the argument list for a function. See [here](https://docs.python.org/3/library/inspect.html#fetching-attributes-statically)


  * itertools module - implements a number of iterator building building blocks. 
    See [here](https://docs.python.org/3/library/itertools.html)

  * haslib module - common interface to many secure hashes and message digests.
    See [here](https://docs.python.org/3/library/hashlib.html#tree-mode)

  * unittest.mock - library for mocking objects for testing
  See [here](https://docs.python.org/3/library/unittest.mock.html#module-unittest.mock)

  * __future__ - module that serves 3 purposes. Avoid confusing import tools that expect to find modules they're importing, ensure 'future statements' run under releases < 2.1 at least yield runtime exceptions, and document when incompatible changes were introduced.

  For an explanation of how to use __future__ see [here](https://stackoverflow.com/questions/7075082/what-is-future-in-python-used-for-and-how-when-to-use-it-and-how-it-works).
  Basically I think it's about breaking changes that will become standard in future releases but are available using your current version so that you can become use to them.
  E.g. print in versions < 3.x  was a keyword, before becoming a function in >= 3.x
  If you were using version 2.x you could do something like:

    >>>print

    >>>from __future__ import print print_function
    >>>print
    <built-in function print>



* filter - use custom function to filter a list, e.g.,

    def fun(letter):
      if letter in list("aeiou"):
        return True
      return False
    
    seq=list("djfhsirhdjdvaebion")

    filtered = filter(fun,seq)

    print(list(filtered)) # should be  vowels in seq only
  
  See [here](https://www.geeksforgeeks.org/filter-in-python/#:~:text=The%20filter%20%28%29%20method%20in%20Python%20has%20the,iterators.%20Returns%3A%20an%20iterator%20that%20is%20already%20filtered.)

* random module
  implements pseudo-random number generators for various distributions
  See [here](https://docs.python.org/3/library/random.html#random.shuffle)

* collections module
  implements specialized container datatypes providing alternatives to Pythons general
  purpose built-in containers.

* Builtin functions
  See [here](https://docs.python.org/3/library/functions.html#slice)

* typing module
Runtime support typehints. See [here](https://docs.python.org/3/library/typing.html#building-generic-types)


## Other

  * dataclasses - see [here](https://www.geeksforgeeks.org/understanding-python-dataclasses/)

  * Python reference the right way - useful guide, [here](https://python-reference.readthedocs.io/en/latest/index.html)

  * Introduction to Python bytecode, 
    See [here](https://opensource.com/article/18/4/introduction-python-bytecode)

  * Lumache, a Python library for cooks and food lovers, creates recipes from mixing random ingredients (name from shell shaped pasta) 
  
  See [lumache](file:///Users/miles52100/Documents/Code/TmpCode/sphinx_example/docs/build/html/usage.html)




## ML packages

  * DeepSpeed: open source DL optimization library for PyTorch
