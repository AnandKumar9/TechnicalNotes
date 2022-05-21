##### Basic controls

Build Logs say everything. <br>
Build Phases outlines the sequence of tasks to be performed. <br>
Build Rules specify how files with various extensions should be compiled. <br>
Build Settings has plenty of options for tweaking a whole set of things during the build. <br>


##### For frameworks
```
If there is an info.plist, it gets processed.
Any .c, .m file gets compiled.
Linking happens
Then .h files (i.e. header files) gets copied
An umbrella.h file that gets created at some point during this process, also gets copied.
The modulemap file gets copied
The framework is touched (i.e. opened)
```

##### For the target actually getting built
```
Process product packaging
Run any custom shell scripts
Compile Swift (and any other too?) source files
Link the target executable to something
Compile storyboards and asset files
Link storyboards
Run any post-compile shell scripts
Copy standard OS libraries into the app
Touch the app
Sign the app
```
