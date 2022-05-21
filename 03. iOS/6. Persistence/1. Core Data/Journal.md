What are configurations with regards to a managed object model?
Document NSPersistentStoreCoordinator method addPersistentStoreWithType:configuration:options:error:. Understand the dictionary keys in options.
What are configurations?
Understand how transient properties can be useful.
How to use a fetch request template?
Can't there be conflicts while merging models?
How is it possible to have multiple stores for a given entity?

----

A persistent store coordinator can be associated with only one managed object model.
A single persistent object store is associated with a single file or other external data store. 
If different entities need to be put in different stores for any reason, the the managed object model must be partitioned by defining configurations. (So is it the case that the coordinator will have to be tied to multiple persistent stores if there are more than one configurations in the managed object model? Kind of yes. While linking a coordinator to a persistent store, the names of the configurations in the model are also specified. So for every configuration, a separate store needs to be added to the coordinator.)
There cannot be any relationships across configurations (strictly speaking, stores).

----

Try running an app for the first time and adding store with both the dictionary options used for lightweight migration.
Try some scenarios where a device/simulator is having version1  of model and the latest version is version 3 and there is no direct mapping model specified for version 1 to version 3.
What is custom version skew detection, migration bootstrapping.
Check the old store being saved with ~prefix before extension.
Performing migration from a very early model version when its corresponding mapping model is also present.

------

When a relationship property of a managed object is set, it throws an exception if the assigned object's context is nil for any reason. However, the error message it shows is 'Illegal attempt to establish a relationship between objects in different contexts'. Hence, before setting a relationship it is always better to check if the context is not nil.
if ([contentDetails managedObjectContext]) {
     downloadLocation.contentDetails = contentDetails;
}

Here, contentDetails is a managed object of one type (DownloadedContent) and downloadLocation is a managed object of yet another type (DownloadLocation). contentDetails's managedObjectContext may become nil for any no. of reasons. For example, a rollback has happened in a different thread and suddenly contentDetails' managedObjectContext is nil. However, printing contentDetails still gives values (though thankfully there is no value shown for any property of contentDetails).

------

When the managed objects are generated from the data model editor by doing a ‘Create a NSManagedObject subclass’, the newly generated subclass is also automatically specified by Xcode as the relevant class for that entity in the Utilities. However if the managed object class is created from the scratch, the class in Utilities stays as NSManagedObject and this can sometimes create a problem. So always check that the correct class is specified in Utilities.

------

While using an ordered relationship if one of the core Data generated accessors is used for inserting an object in the relationship, it throws an exception. This is a known bug in Core Data ([link](http://stackoverflow.com/questions/7385439/exception-thrown-in-nsorderedset-generated-accessors)). Instead, an NSOrderedSet can be created and objects inserted to it and then finally that NSOrderedSet assigned to the ordered relationship.

```
NSMutableOrderedSet *templateFields = [NSMutableOrderedSet new]; 
for (id formField in [form valueForKey:@"fieldDetails"]) {
     ELogTemplateField *templateField = ....
     [templateFields addObject:templateField]; 
}
template.templateFields = [NSOrderedSet orderedSetWithOrderedSet:templateFields];
```
----

If for any reason the context in which a managed object was created is not valid anymore, all the properties of the managed objects return nil. Sometimes the context can be released in unpredictable situations. For example when I created a managed object in a child context in a method and returned it, the context was active when it was returned but when a property of the managed object was accessed the context was released. So I had the child context as an app delegate property and then it worked. ([http://stackoverflow.com/questions/24700981/managed-object-created-in-child-context-not-reflected-in-main-thread]) ([Link2](http://stackoverflow.com/a/16854696/1135417))

----

NSFetchedResultsController allows to efficiently provide data for table views that have their data in a Core Data persistent store. In addition it also allows automatic change tracking so that whenever any object is changed in the context, the NSFetchedResultsController object is also notified of the change so that it can then update the table view too. Further, it can maintain a cache too so that when the same data has to be redisplayed it is a lot faster.
It is just a subclass of NSObject (and not UITableViewController).
initWithFetchRequest:managedObjectContext:sectionNameKeyPath:cacheName: method is used to create a fetched results controller. Passing nil to the last argument indicates that cache would not be maintained.

For getting automatic notifications a delegate must be specified. The delegate has to conform to NSFetchedResultsControllerDelegate protocol. The delegate must implement at least one of the delete methods for tracking to be enabled. Even an empty implementation of controllerDidChangeContent: is enough. 
The initial fetch is done by calling performFetch: method. Also the fetch request of a NSFetchedResultsController object must not be simply changed after initialization. If at all needed, first the cache should be deleted, then the fetch request changed and then a performFetch: done again.
There are methods that basically perform the basis for implementation of table view data source methods. These include objectAtIndexPath:, sectionForSectionIndexTitle:atIndex:, sectionIndexTitleForSectionName:.

----

It is possible to have multiple managed object models. However, the thing to note is that a persistent store coordinator can be tied to only one model at a time and every coordinator usually has its own set of persistent stores or files (every file corresponds to a model or a configuration in a model). Hence if multiple models are used they would essentially mean at least as many coordinators and persistent stores. 
So if multiple managed object models are used they need to have totally separate stacks. ([Link1](http://stackoverflow.com/a/16146335/1135417)) ([Link2](http://stackoverflow.com/a/13128484/1135417))

----

When a persistent store is added it can also be specified whether it should be readonly. This can be done using the options parameter of addPersistentStoreWithType:configuration:URL:options:error method.

----

Configurations allow entities in a single managed object model to be stored in different persistent stores. This is done by first creating the configurations in data model editor and associating entities to them and then by specifying the configuration to be used by a persistent store while creating it. A persistent store corresponds to a configuration in a model. If no configuration is specified, the default configuration that is always there and includes all the entities in the model is used.

There can be several reasons for needing to segregate entities of a model into various configurations. There may be a need to have some entities strictly as readonly or for objects of some entities to be deleted together. The one restriction with having configurations is that there cannot be any relationships crated between entities belonging to different configurations.
([Link](http://commandshift.co.uk/blog/2013/06/06/multiple-persistent-stores-in-core-data/) on how to add and use configurations)

----

Transformable attributes allow non-standard data types (i.e. UIImage, NSArray, NSDictionary, etc.) to be stored as attributes. The only requirement is that the data type should adopt NSCoding protocol (though this is not officially stated, it seems to be the case). To put it very simply, if there is a data type which you would want to convert to NSData and save in CoreData, you can just mark that attribute as of type transformable. You would then not need to do the conversion yourself and CoreData will handle it automatically.
In the default case, transformable attributes are automatically converted to NSData. This actually uses the reverse transformer of NSKeyedUnarchiveFromDataTransformerName behind the scenes. If a different built-in transformer is needed, it can also be used by specifying its reverse transformer’s name.
If needed, a custom transformer (i.e. a NSValueTransformer subclass) can also be used. The custom transformer should implement all the required NSValueTransformer methods and should be specified in the data model inspector in the data model utilities.
In some places it is written that the downside is that transformable attributes are stored in the SQLite backend as binary plists inside blobs, and you can't query those fields directly from an NSPredicate. (Need to check.)

----

([Link](http://stackoverflow.com/questions/9157436/distinct-count-via-core-data-nsexpression-into-nsfetchedresultscontroller) showing how to use expressions to efficiently perform complicated fetch requests. The result type is NSDictionaryResultType and the expression description is set as one of the properties to fetch.)

----

Adding seed data to the app. ([link1](http://blog.atwam.com/blog/2012/05/11/multiple-persistent-stores-and-seed-data-with-core-data/)) ([link2](http://www.objc.io/issue-4/importing-large-data-sets-into-core-data.html))

----

The SQL commands actually being sent to Core Data as well as the time taken to execute the various fetch commands can actually be seen in the debug console using the below launch argument.
-com.apple.CoreData.SQLDebug 1
2015-05-27 12:30:48.054 TestVarious[5733:6143210] CoreData: sql: SELECT TBL_NAME FROM SQLITE_MASTER WHERE TBL_NAME = 'Z_METADATA'
2015-05-27 12:30:48.061 TestVarious[5733:6143210] CoreData: sql: SELECT t0.ZNAME,  t1.ZNAME FROM ZCITY t0 LEFT OUTER JOIN ZSTATE t1 ON t0.ZSTATE = t1.Z_PK ORDER BY t0.ZNAME DESC
2015-05-27 12:30:48.061 TestVarious[5733:6143210] CoreData: annotation: sql connection fetch time: 0.0002s
2015-05-27 12:30:48.061 TestVarious[5733:6143210] CoreData: annotation: total fetch execution time: 0.0003s for 5 rows.
([Link](http://www.objc.io/issue-4/core-data-fetch-requests.html) discussing the various aspects involved in the efficiency of fetch requests.)

----

There is a library called Groot (explained in another note) which can be used to easily convert managed objects into JSON objects (i.e. dictionary and array) and even vice-versa. What it means is that in one of the cases there is no need to manually traverse through all the managed objects and create the JSON object.

----
