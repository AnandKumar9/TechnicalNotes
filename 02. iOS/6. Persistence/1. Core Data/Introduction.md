Object Graph is a view of an object system at a particular point of time. Data model diagrams such as UML class diagram describe the relationship between the classes, whereas object graph relates their instances.

Core Data is a database API that persists data to disk, and also serves as the model layer, i.e. it also generates the data objects.

Core Data APIs introduced with iOS5 do not work reliably in iOS5, but do work well in iOS6. For iOS5, it is better to stick with the Core Data APIs that were there in iOS4 as well.

Macros in pch file -

DLog - Log if debug compiler flag is set, do not log otherwise.
ALog - Log and raise an assertion if debug compiler flag is set, only log otherwise.
ZAssert - Execute the passed condition and raise an assertion if debug compiler flag is set, only execute otherwise.
Read 'Concurrency with CoreData section'.
