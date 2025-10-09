`.idea` folder contains metadata about the project
`src` folder is where the source code is put.

The linked JDK version is present in `External libraries` section.

`File Project Structure` - This too has a `Project SDK` specified there.

> Strangely when the Project SDK there was specified as 11 (java version 11.0.4), code was even giving warnings such as String symbol could not be found. It went away when I selected 1.8 there. Also how can there be such discrepancy in the java version specified there.

`Edit configurations` has an option for Main class. This is what is run if you run the code.

`JRE (Java Runtime Environment)` - This is what is needed to run a Java program.

`JDK` too needs to be installed (I think I installed it using Homebrew). It includes JRE, compiler and many other things that are needed by Java to run.
Or search for JDK. An Oracle result called Java SE comes up, use that.

While creating a project, a `SDK version` (11.0.4, 1.8, etc.) needs to be selected.

For running in `Debug mode` use bug button.
