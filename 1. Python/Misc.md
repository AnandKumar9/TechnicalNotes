#### Standard Library Modules

`os` - Interacts with OS. That is file system, system resources, etc. <br>
`shutil` - A higher level interface for working with file system. <br>
`glob` - Provides a function for making file lists from directory wildcard searches. <br>
`sys` - For working with command line arguments. <br>
`re` - For working with regular expressions. <br>
`math` - For floating point math. <br>
`random` - For making random selections. <br>
`statistics` - For making statistical calculations. <br>
`random` - For making random selections. <br>
`urllib.request` - For working with URLs, i.e. web servies. <br>
`smtplib` - For sending emails. <br>
`datetime` - For working with date and time. <br>
`zlib`, `gzip`, etc. - For data archiving and compression. <br>
`timeit` - For performance instrumentation. <br>
`doctest` - For unit testing. <br>

`json` - For working with json data. <br>
`sqlite3` - For persistent database needs. <br>

`reprlib` - For customized abbreviated displays of large or deeply nested data. <br>
`threading` - For concurrency. <br>
`logging` - A full featured and flexible logging system. <br>
`weakref` - For tracking objects without creating a reference. Memory management related. <br>
`Decimal` - For more precise decimal floating point arithmetic <br>

#### Virtual Environments and Packages

A `virtual environment` is a self-contained directory tree that contains a Python installation for a particular version of Python, plus a number of additional packages (with their own precise versions). Each Python project can have its own virtual environment, thereby allowing allowing all the projects to exist and function from the same system. It can be created using `venv` module.

To create a virtual environment, decide upon a directory where you want to place it, and run the venv module as a script with the directory path. This will create the tutorial-env directory if it doesn’t exist, and also create directories inside it containing a copy of the Python interpreter and various supporting files.
```
python3 -m venv tutorial-env
```

A common directory location for a virtual environment is `.venv`.

Once you’ve created a virtual environment, you may activate it. (On Linux/macOS a command like below is needed.)
```
source tutorial-env/bin/activate
```
Activating the virtual environment will change your shell’s prompt to show what virtual environment you’re using, and modify the environment so that running python will get you that particular version and installation of Python. F

([Link](https://docs.python.org/3/tutorial/venv.html#creating-virtual-environments))

#### Managing Packages with pip

`pip` is used to install, upgrade, and remove packages (is it like a dependency management system?). By default, it install packages from the Python Package Index (https://pypi.org).

Installing the latest version of a package by specifying a package’s name.
```
python -m pip install novas
```

Install a specific version of a package.
```
python -m pip install requests==2.6.0
```

Upgrading a package to the latest version.
```
python -m pip install --upgrade requests
```

`pip uninstall` followed by one or more package names will remove the packages from the virtual environment.

`pip show` displays information about a particular package.

`pip list` displays all of the packages installed in the virtual environment.

`pip freeze` produce a similar list of the installed packages, but the output uses the format that pip install expects. A common convention is to put this list in a requirements.txt file. (Check more)

Installing Python Modules ([Link](https://docs.python.org/3/installing/index.html#installing-index)) <br>
Distributing Python Modules ([Link](https://docs.python.org/3/distributing/index.html#distributing-index))

#### Misc.

[Python language reference](https://docs.python.org/3/reference/index.html#reference-index) <br>
Understand global and nonlocal ([Link](https://docs.python.org/3/reference/simple_stmts.html#global)) <br>
Understand Coroutines
