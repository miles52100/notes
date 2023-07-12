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


To insert an image. The file path to the image is either relative or absolute from the top sourcedir
So e.g. if we have a directory `sourcedir/Images` containing a **PNG** file `logo.png`

Then we'd insert that here (we're showing some options, e.g. we want it one-qarter the size of the *PNG*)

```
.. image:: /Images/logo.png
   :class: with-shadow
   :scale: 25 %
   :align: right
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

For example

```
1  :php:`$result = $a + 23;`
2  :typoscript:`lib.hello.value = Hello World!`
3  :file:`/etc/passwd`
4  :kbd:`ctrl` +  :kbd:`s`
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

    An example
    
    ```
    .. This is a comment - an explicit markup block which is an invalid construct.
    .. 
       This is part of example_page.rst
       And a multiline comment
    
    .. _explicit-ref-label:
    Example usage is blah.

    To reference that label:
    .. We assume this is e.g. the index.rst file snippet

    Look at the :ref:`example_linl <explicit-ref-label>`

    ```

*footnotes*
  For footnotes use `[#name]_` to mark the footnote location. Add the footnote at the bottom of the document
  after a "Footnotes" rubric heading

  ```
  Here is a latin [#f1]_ word ipsum [#f2]_


  .. rubric:: Footnotes

  .. [#f1] The first footnote
  .. [#f1] A placeholder text, doesn't mean anything in Latin, Lorem Ipsum is the most common placeholder

  ```

*unicode*
The easiest way is to directly write them as Unicode characters, the default encoding is UTF-8.
To write them directly in VSCode it's easiest to install the extension "Insert Unicode", the search from the Command Palette for `insert from hex`  and enter the UTF-8 hex encoding of the Unicode character.
E.g. for ©, you enter 'a9' as the hex.


Another approach is to use substitution and the unicode directive. For example

```
Copyright |copy| 2003, |BogusCorp(TM)| |---|
all rights reserved.


.. |copy| unicode:: 0xa9 .. copyright sign
.. |BogusCorp(TM)| unicode:: BogusCorp U+2122
   .. with trademark - a comment
.. |---| unicode:: U+02014 .. em dash
  :trim:  .. equiv to ltrim and rtrim to remove whitespace
```

*warning*

.. warning::
   This is your *FINAL* warning



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