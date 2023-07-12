# Sphinx Notes

Documentation tool, built upon default plain-text markup reStructuredTest (rst), see References.

Although mainly a documenting tool (for code?), it can be used to 
generate blogs, homepages, and even books.

### ReST
There are 

 *directives*
A ReST markup element that allows for marking a block of content with special meaning

e.g.

```
.. directivenanme:: argument ...
   :option: value

   Content of the directive
```

*domain*
A collection of markup to describe and link to objects belonging together
e.g. elements of a programming language. Default domain is 'py:' for Python


*role*
A ReST markup element that allows marking a piece of text. Like directives, roles are extensible.
Basic syntax is:

```
:rolename: `content`
```

*Literal blocks*
Introduced be ending a paragraph with the special marker `::`
The literal block must be indented e.g.

```
This is a normal text paragraph. The next is a code sample::

  It is not processed in any way, except
  that the indentation is removed

  It can span multiple lines

This is a normal text paragraph again.
```

*Hyperlinks*

Use 
```
`Link text <https://domain.invalid/>`_
```
for inline weblinks (if the link text should be the web address you don't need special markup at all - it should just work)

You can also separate the link and target definition 
```
This is a paragraph that contains `a link`_.

.. _a link: https://domain.invalid/
```

Internal links. 

To support cross-referencing to arbitrary locations in any document, the standard reST labels are used.
For this to work label names must be globally unique in the document.

Two ways to refer to labels:

  1. Place a label name directly before a section title

      ```
      .. _my-reference-label:
      Section to cross-reference
      --------------------------

      This is the text of the section.
      It refers to the section itself, see :ref:`my-reference-label`.
      ```
     The :ref: role would then generate a link to the section.

  2. Labels that aren't placed before a section title can still be referenced, but you must give the link
     an explicit title, using this syntax
     '''
     :ref:\`Link title <label-name>\`
     '''


## Installing
See the methods in the official documentation under References

## Starting a new project
Create a Python virtual environment to install all required tools

```
python -m venv .venv
source .venv/bin/activate
(.venv) $ python -m pip install sphinx
```

### Quickstart
To set up all the required document structures
`sphinx-quickstart`

This will create a sourcedir with `conf.py` and `index.rst`
and a builddir, where ultimately a processed index file 
(default is `index.html`) for viewing will be stored


To build the documentation

`sphinx-build -b html sourcedir buildir`


In reST


## References

* [Sphinx Documentation](https://www.sphinx-doc.org/en/master/index.html)

* [ReStructuredTex](https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html)