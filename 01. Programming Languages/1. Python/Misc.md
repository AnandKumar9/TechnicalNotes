##### Run a function from command line and pass arguments

In the file add a snippet such as this

```swift
if __name__ == "__main__":
    import sys
    arg1 = sys.argv[1]
		thatParticularFunction(arg1)
```

And then it can be run like this from command line

```swift
python3 FileName.py customArgumentXYZ
```

Basically if a python file is run, `__name__ ` becomes `__main__` and the arguments get passed in `sys.argv` array.

##### Standard Library Modules

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

##### Printing

Printing arrray elements in different lines.

```python
print(*array1, sep = "\n")
```

String interpolation.

```python
print(f"TEXT - {variableName}")
```