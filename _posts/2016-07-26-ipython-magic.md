---
title: IPython's magic functions
layout: post
---

I love IDEs. And I use Python quite often. And since my Macbook Air goes mad when I open JetBrains's PyCharm, there are not so many decent options for me – Spyder, Rodeo, Sublime Text (which is totally awesome, but it's not an IDE), – and IPython, my favorite tool for writing and running all that stuff I write in Python.

**Magic functions** are one of the IPython's cool features. The magic function system provides a series of functions which allow you to
control the behavior of IPython itself, plus a lot of system-type
features. 

There are two kinds of magics, **line-oriented** and **cell-oriented**.

## Line magics

Line magics are prefixed with the `%` character and work much like OS
command-line calls: they get as an argument the rest of the line, where
arguments are passed without parentheses or quotes.

For example, this will time the given statement:

```
%timeit range(1000)
```

Full list of available line magic functions (from `%lsmagic`):

```
%alias  %alias_magic  %autocall  %automagic  %autosave  %bookmark  %cat  %cd  %clear  %colors  %config  %connect_info  %cp  %debug  %dhist  %dirs  %doctest_mode  %ed  %edit  %env  %gui  %hist  %history  %install_default_config  %install_ext  %install_profiles  %killbgscripts  %ldir  %less  %lf  %lk  %ll  %load  %load_ext  %loadpy  %logoff  %logon  %logstart  %logstate  %logstop  %ls  %lsmagic  %lx  %macro  %magic  %man  %matplotlib  %mkdir  %more  %mv  %notebook  %page  %pastebin  %pdb  %pdef  %pdoc  %pfile  %pinfo  %pinfo2  %popd  %pprint  %precision  %profile  %prun  %psearch  %psource  %pushd  %pwd  %pycat  %pylab  %qtconsole  %quickref  %recall  %rehashx  %reload_ext  %rep  %rerun  %reset  %reset_selective  %rm  %rmdir  %run  %save  %sc  %set_env  %store  %sx  %system  %tb  %time  %timeit  %unalias  %unload_ext  %who  %who_ls  %whos  %xdel  %xmode
```


## Cell magics

Cell magics are prefixed with a double `%%`, and they are functions that get as an argument not only the rest of the line, but also the lines below it in a
separate argument.  These magics are called with two arguments: the rest of the
call line and the body of the cell, consisting of the lines below the first.

For example:
        
```python
%%timeit x = numpy.random.randn((100, 100))
numpy.linalg.svd(x)
```

will time the execution of the numpy `svd` routine, running the assignment of `x` as part of the setup phase, which is not timed.

Available cell magics:
```
%%!  %%HTML  %%SVG  %%bash  %%capture  %%debug  %%file  %%html  %%javascript  %%latex  %%perl  %%prun  %%pypy  %%python  %%python2  %%python3  %%ruby  %%script  %%sh  %%svg  %%sx  %%system  %%time  %%timeit  %%writefile
```

In a line-oriented client (the terminal or Qt console IPython), starting a new
input with `%%` will automatically enter cell mode, and IPython will continue
reading input until a blank line is given.  In the notebook, simply type the
whole cell as one entity, but keep in mind that the `%%` escape can only be at
the very start of the cell.

## How-to & some really cool magics

If you have 'automagic' enabled (via the command line option or with the `%automagic` function), you don't need to type in the `%` explicitly for line magics; cell magics always require an explicit `%%` escape.  By default,
IPython ships with automagic on, so you should only rarely need the `%` escape. For example, typing `%cd mydir` changes your working directory
to 'mydir', if it exists.

For a list of the available magic functions, use `%lsmagic`.

For a description of any of them, type `%magic_name?`, e.g. `%cd?`.

### `%edit`

Brings up an external text editor and executes the resulting code. You will need to set the command for
this editor via the ``TerminalInteractiveShell.editor`` option in your
configuration file before it will work.

```
%edit [options] [args]
```

### `%%writefile`

Writes the contents of the cell to a file. `-a`, `--append`: Append contents of the cell to an existing file. The file will be created if it does not exist.

```
%writefile [-a] filename
```

## `%pastebin`

This magic uploads code to Github's Gist paste bin and returns the URL. The argument can be an input history range, a filename, or the name of a string or macro.

```
%pastebin [-d "Custom description"] 1-7
```
    
## `%matplotlib`

This magic is an absolute must-have! Its basic structure is `%matplotlib [-l] [gui]` and this magics sets up `matplotlib`. For example, 

```
In [1]: %matplotlib inline
```

enables the inline backend for usage with the IPython Notebook, which is much more convenient.

*to be continued...*