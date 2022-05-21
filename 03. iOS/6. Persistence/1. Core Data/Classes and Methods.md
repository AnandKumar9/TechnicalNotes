NSManagedObjectContext
NSPersistentStoreCoordinator
NSManagedObjectModel
NSPersistentStore
NSManagedObject
NSManagedObjectID
NSEntityDescription
NSAttributeDescription
NSRelationshipDescription
NSFetchedPropertyDescription

NSFetchRequest
NSPredicate
NSSortDescriptor
NSExpression
NSExpresssionDescription
NSMappingModel
NSEntityMapping
NSPropertyMapping

NSMigrationManager
NSEntityMigrationPolicy
NSInferMappingModelAutomaticallyOption
NSMigratePersistentStoresAutomaticallyOption

NSEntityMappingType
NSManagedObjectContextConcurrencyType
NSMainQueueConcurrencyType

NSManagedObjectContextDidSaveNotification
NSManagedObjectContextObjectsDidChangeNotification

NSFetchedResultsController 
NSFetchedResultsControllerDelegate 
NSFetchedResultsChangeType

**********************************

Some important methods used for setting up a usual Core Data stack - 

NSManagedObjectModel -> -initWithContentsOfURL:  (For creating the managed object model) 
NSPersistentStoreCoordinator -> -initWithManagedObjectModel: (For adding a managed object model to a persistent store coordinator)
NSPersistentStoreCoordinator -> -addPersistentStoreWithType:configuration:URL:options:error: (For adding a persistent store to the persistent store coordinator)
NSManagedObjectContext -> -setPersistentStoreCoordinator: (For linking a persistent store coordinator to the managed object context)
NSManagedObjectContext -> -save: (For saving the latest changes in the context to the persistent store)


Some important methods to work with a Core Data stack - 

NSEntityDescription -> +insertNewObjectForEntityForName:inManagedObjectContext: (For creating a new record in an entity in the specified context).
NSManagedObjectContext -> -executeFetchRequest:error: (For executing a fetch request through a context)
NSManagedObjectContext -> -deleteObject: (For deleting an object from a persistent store in a context)

A fetch request has 3 parts - Entity to be queried, predicate to be applied, sort descriptor to be used.

Some methods to load a model -

NSManagedObjectModel -> +mergedModelFromBundles: (For creating a model by merging the models found in all the specified bundles)
NSManagedObjectModel -> +modelByMergingModels: (For creating a model by merging the specified models)
NSManagedObjectModel -> -initWithContentsOfURL: (For creating a model using the model file at specified URL)


Some methods to access the model -

NSPersistentStoreCoordinator -> -managedObjectModel
NSEntityDescription -> -managedObjectModel (the entity can in turn be accessed using a managed object)
NSPersistentDocument -> -managedObjectModel (For directly accessing the managed object model tied to the persistent document's coordinator)

Some more methods - 

NSManagedObjectModel -> -setFetchRequestTemplate:forName: (For adding a fetch request template to a model)
NSManagedObjectModel -> -fetchRequestFromTemplateWithName:substitutionVariables: (For retrieving a fetch request from one of the templates and setting it up with the arguments to be used)
NSManagedObjectModel -> -entitiesByName (For getting the entities in the model as a dictionary with the keys being entity name)
NSManagedObjectContext -> -assignObject:toPersistentStore: (For specifying the persistent store to which the managed object should be saved)
NSManagedObjectContext -> -initWithConcurrencyType: (For initializing a context with a specified concurrency type, used especially while creating a child context)
NSManagedObjectContext -> -setParentContext: (For setting the parent context of the receiver context)

Some NSManagedObject methods -

NSManagedObject -> -entity (For accessing the entity to which the managed object belongs)
NSManagedObject -> -managedObjectContext (For accessing the context with which the managed object is registered)
NSManagedObject -> -awakeFromInsert (Invoked automatically when the managed object in inserted into a context, hence invoked just once)
NSManagedObject -> -awakeFromFetch (Invoked automatically when the managed object is fetched from the store)
NSManagedObject -> -validateValue:forKey:error: (For programmatically checking if a value can satisfy a specific attribute's validation constraints)
NSManagedObject -> -isDeleted (For checking if the managed object is marked for deletion in next save operation)
NSManagedObject -> -objectID (To get the managed object ID of the managed object) 
NSManagedObject -> -isFault (To check if the object is a fault)
NSManagedObject -> -didTurnIntoFault (Invoked automatically when the managed object turns into a fault) 

Some NSFetchRequest methods -

NSFetchRequest -> +fetchRequestWithEntityName: (For creating a fetch request for the specified entity)
NSFetchRequest -> -setResultType: (For setting the result type. It can correspond to managed objects, managed object IDs, dictionary, and a count)
NSFetchRequest -> -setPropertiesToFetch: (For specifying the properties to be returned by the fetch. Attributes, relationships and expressions can be specified.)
NSFetchRequest -> -setIncludesSubentities: (For specifying if the fetch request should also return managed objects which were created through the child entity of the entity being queried in this fetch request.)
NSFetchRequest -> -setFetchLimit: (For specifying no. of qualifying results that should be fetched. Better than fetching all qualifying results, but still not a very efficient way and expressions can instead be used.)
NSFetchRequest -> -setFetchOffset: (For specifying the offset to be applied, i.e. no. of qualifying results that should be skipped before sending the results.)
NSFetchRequest -> -setFetchBatchSize: (For specifying the no. of results to be included in one batch.)
NSFetchRequest -> -setReturnsObjectsAsFaults: (For specifying if the objects should be returned as faults. The default value is YES.)

NSManagedObjectID -> -isTemporaryID (To check if an object ID is temporary or permanent)
NSManagedObjectContext -> -objectWithID: (For getting the managed object from the object ID, but will this not work if managed object is present only in context?)


Some undo management related NSManagedObjectContext methods -

NSManagedObjectContext -> -rollback (Rolls back all unsaved changes in context and clears the context's undo manager stack)
NSManagedObjectContext -> -reset (Wipes out all the managed objects from context, does not delete them from store. Just does a reset on context.)
NSManagedObjectContext -> -processPendingChanges (For forcing to process, i.e. commit all pending changes to the object graph (NOT data store). Calling save automatically calls this method; rarely needs to be used.)
NSUndoManager -> -disableUndoRegistration (Subsequent changes to objects in context are not recorded in the context's undo manager)
NSUndoManager -> -enableUndoRegistration (Subsequent changes to objects in context are recorded in the context's undo manager)

NSManagedObjectContext -> -mergeChangesFromContextDidSaveNotification: (For merging all the changes made by a save in another context)

Some persistent store related methods -

NSPersistentStoreCoordinator -> -persistentStoreForURL: (For getting the persistent store of a context for a particular URL)
NSFetchRequest -> -setAffectedStores: (For restricting the fetch request to specified persistent stores)
NSPersistentStore -> -migratePersistentStore:toURL:options:withType:error: (For migrating a store from one location to another and also having it as a different type, i.e. SQLite, XML store, etc. in the process)
NSPersistentStoreCoordinator -> +registeredStoreTypes (For getting the registered store types. Classes for SQLite, Binary and In-memory are always there. Mac OS X also has XML.)


**********************************

Sequence of methods called while doing custom migration -

NSPersistentStoreCoordinator -> +metadataForPersistentStoreOfType:URL:error: (For getting the store metadata)
NSPersistentStoreCoordinator -> -managedObjectModel (For getting the managed object model)
NSManagedObjectModel -> -isConfiguration:compatibleWithStoreMetadata: (For checking if managed object model and store data are compatible)

NSManagedObjectModel -> +mergedModelFromBundles:forStoreMetadata: (For getting a model version from the bundle which corresponds to the store data)
NSMappingModel -> +mappingModelFromBundles:forSourceModel:destinationModel: (For getting a mapping model which corresponds to the a pair of object models)
NSMigrationManager -> -initWithSourceModel:destinationModel: (For initiating a migration manager)
NSMigrationManager -> -migrateStoreFromURL:type:options:withMappingModel:toDestinationURL:destinationType:destinationOptions:error: (For migrating the store at the specified source URL to the specified destination URL using the specified mapping model)

**********************************


Some data migration methods - 

NSPersistentStore -> +migrationManagerClass (Returns the NSMigrationManager class for the store class.)
NSMigrationManager -> -initWithSourceModel:destinationModel: (Initialises a migration manager with the specified source and destination models)
NSMigrationManager -> 
-migrateStoreFromURL:type:options:withMappingModel:toDestinationURL:destinationType:destinationOptions:error: (For migrating the store at the specified source URL to the specified destination URL using the specified mapping model)
NSMappingModel -> +inferredMappingModelForSourceModel:destinationModel:error: (For creating a mapping model for the specified source model and destination model)
NSMappingModel - +mappingModelFromBundles:forSourceModel:destinationModel: (For getting the mapping model for the specified source and destination models)

NSEntityMigrationPolicy -> -beginEntityMapping:manager:error: (Invoked automatically be the migration manager at start of a given entity mapping.)
NSEntityMigrationPolicy -> -createDestinationInstancesForSourceInstance:entityMapping:manager:error: (Invoked automatically by the migration manager on each source instance to create the corresponding destination instance(s)).
NSEntityMigrationPolicy -> -endEntityMapping:manager:error: (Invoked automatically be the migration manager at end of a given entity mapping.)


NSManagedObjectModel ->  -isConfiguration:compatibleWithStoreMetadata: (For checking if the specified configuration in the receiver is compatible with the version or metadata in the persistent store.)
NSManagedObjectModel -> +mergedModelFromBundles:forStoreMetadata: (For finding the model for the version information contained in the specified store metadata.)

NSPersistentStoreCoordinator -> +metadataForPersistentStoreOfType:URL:error: (For getting a dictionary with the details of the persistent store's metadata.)

**********************************

Some fetched results controller methods -

NSFetchedResultsController -> -initWithFetchRequest:managedObjectContext:sectionNameKeyPath:cacheName: (For initializing a fetched results controller. Specifying nil in last argument indicates no caching).
NSFetchedResultsController -> -performFetch: (For performing an initial fetch)

NSFetchedResultsController -> - objectAtIndexPath:
NSFetchedResultsController -> - sectionForSectionIndexTitle:atIndex:
NSFetchedResultsController -> - sectionIndexTitleForSectionName:

NSFetchedResultsControllerDelegate -> -controllerWillChangeContent:
NSFetchedResultsControllerDelegate -> -controller:didChangeObject:atIndexPath:forChangeType:newIndexPath:
NSFetchedResultsControllerDelegate -> -controller:didChangeSection:atIndex:forChangeType:
NSFetchedResultsControllerDelegate -> -controllerDidChangeContent:
