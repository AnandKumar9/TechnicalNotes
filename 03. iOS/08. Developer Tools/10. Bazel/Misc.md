`BAZEL_INTEGRATION_DIR` - 'TestSomething/TestSomething.xcodeproj/rules_xcodeproj/bazel'

##### bazelrc file ([reference](https://bazel.build/run/bazelrc))

Configuration file which can be used to specify bazel options that need to remain same across builds. Usually placed in workspace folder, but can be placed in other places too.

Lines that start with import or try-import are special and are used to load other `rc` files. To specify a path that is relative to the workspace root, write 'import %workspace%/path/to/bazelrc'.

The first word on each line specifies when these defaults are applied with the possible values being - `startup`, `common`, `always`, `command`.

`````
build --test_tmpdir=/tmp/foo --verbose_failures
`````

In addition to setting option defaults, the rc file can be used to group options and provide a shorthand for common groupings. This is done by adding a `:name` suffix to the command. These options are ignored by default, but will be included when the option --config=name is present, either on the command line or in a .bazelrc file, recursively.

`````
# Definition of --config=memcheck
build:memcheck --strip=never --test_timeout=3600
`````

Bazel looks for a `bazelrc` file in multiple places, not just the workspace file but also in certain folders in home directory, etc.

##### bazelignore file

Used to specify directories within the workspace that you want Bazel to ignore, such as related projects that use other build systems.

##### glob function ([reference](https://bazel.build/reference/be/functions#glob))

`glob` is a helper function that finds all files that match certain path patterns, and returns a new, mutable, sorted list of their paths. Glob only searches files in its own package, and looks only for source files (not generated files nor other targets).

`````python
glob(include, exclude=[], exclude_directories=1, allow_empty=True)

data = glob(
    ["testdata/*.txt"],
    exclude = ["testdata/experimental.txt"],
),
`````

##### bazel directories ([documentation](https://bazel.build/remote/output-directories))

When a build is done, four different directories are generated -

 `bazel-bin` (refers to bin directory?) <br> `bazel-<RootFolderName>` (the working directory for all actions that take place in the build) <br> `bazel-out` (where outputs are stored?) <br>`bazel-testlogs`  (results of unit tests)

##### alias rule ([reference](https://bazel.build/reference/be/general#alias))

`alias` is a native rule that creates another name a rule can be referred to as. It only works for "regular" targets. In particular, package_group and test_suite cannot be aliased.

----

