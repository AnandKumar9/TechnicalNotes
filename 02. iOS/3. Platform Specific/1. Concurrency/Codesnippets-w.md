Getting a global concurrent dispatch queue - 
dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);

Creating a serial dispatch queue -
dispatch_queue_t queue = dispatch_queue_create("com.example.MyQueue", NULL);

Putting a task asynchronously in a dispatch queue -
dispatch_async(queue, ^{//block});

Working with context information in dispatch queue -

dispatch_queue_t globalQueue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
static void *globalQueueKey = @"Global Queue key";
dispatch_queue_set_specific(globalQueue, globalQueueKey, (void *)globalQueueKey, NULL);
if (dispatch_get_specific(globalQueueKey)) { // .. In the task block

Working with dispatch_apply as a replacement for for loop -

dispatch_queue_t queue = dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0);
dispatch_apply(count, queue, ^(size_t i) {
    printf("%u\n",i);
});


******************

NSInvocationOperation -

An operation is added into the operation queue and inside the operation's selector, there is finally a statement in the end when it has done its job to return to the main thread.
- (void)viewWillAppear:(BOOL)animated {
    [super viewWillAppear:animated];
    self.remoteData = [[NSMutableArray alloc] init];

    NSOperationQueue *operationQueue = [[NSOperationQueue alloc] init];
    NSInvocationOperation *operation = [[NSInvocationOperation alloc] initWithTarget:self selector:@selector(fetchData) object:nil];
    [operationQueue addOperation:operation];
}

- (void)fetchData {
    NSURL *remoteURL = [NSURL URLWithString:@"http://icodeblog.com/samples/nsoperation/data.plist"];
    NSMutableArray *remoteDataArray = [NSMutableArray arrayWithContentsOfURL:remoteURL];
    for (NSString *data in remoteDataArray) {
        [self.remoteData addObject:data];
    }
    [self.tableView performSelectorOnMainThread:@selector(reloadData) withObject:nil waitUntilDone:YES];
}

NSBlockOperation - 

Similar to above.

- (void)viewWillAppear:(BOOL)animated {

    [super viewWillAppear:animated];

     self.remoteData = [[NSMutableArray alloc] init];
     NSOperationQueue *operationQueue = [[NSOperationQueue alloc] init];

     NSBlockOperation *operation = [NSBlockOperation blockOperationWithBlock:^(){

        NSURL *remoteURL = [NSURL URLWithString:@"http://icodeblog.com/samples/nsoperation/data.plist"];
        NSMutableArray *remoteDataArray = [NSMutableArray arrayWithContentsOfURL:remoteURL];

        for (NSString *data in remoteDataArray) {
            [self.remoteData addObject:data];
        }
        [self.tableView performSelectorOnMainThread:@selector(reloadData) withObject:nil waitUntilDone:YES];
    }];

    [operationQueue addOperation:operation];

}

Custom NSOperation - 

The below code snippet is for the place where a custom NSOperation is initiated and the main method of the custom NSOperation.

FileLoadOperation *_operation = [[FileLoadOperation alloc] initWithURL:url];
__weak FileLoadOperation *operation = _operation;
operation.completionBlock = ^() {
        self.remoteData = operation.remoteData;
        [self.tableView reloadData];
};

- (void)main {
    NSURL *remoteURL = [NSURL URLWithString:@"http://icodeblog.com/samples/nsoperation/data.plist"];
    self.remoteData = [[NSMutableArray alloc] init];
    NSMutableArray *remoteDataArray = [NSMutableArray arrayWithContentsOfURL:remoteURL];
    for (NSString *data in remoteDataArray) {
        [self.remoteData addObject:data];
    }
}
