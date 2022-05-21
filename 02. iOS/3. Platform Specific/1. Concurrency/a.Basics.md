
Think of dispatch queues as something you put tasks into. And then depending upon what kind of a queue it is, they are executed together or one by one. A serial queue executes tasks one by one and runs them in a separate private queue. A global queue executes them together. The main queue is the globally available serial queue (and hence executes tasks one by one) and runs the tasks on app's main thread. And once a queue is there, either of synchronous or asynchronous tasks can be added to it.

Operation queues too are things you put tasks into it but they also allow dependencies to be created between those tasks.

Now the thing to note is that an operation queue by itself probably does not have any way to start a task in a separate thread (i.e. non-main thread), etc. That piece still comes through dispatch queue API.


**************


One of the technologies for starting a task asynchronously is Grand Central Dispatch (GCD). With GCD just the tasks need to be defined and put in appropriate dispatch queues. GCD takes care of creating the required threads and scheduling them. It is a C-based api.

Dispatch queues execute tasks either serially or concurrently but always in a first-in first-out order. A serial dispatch queue runs only one task at a time, waiting until the current task is complete before dequeueing it and starting the next task. A concurrent dispatch queue whereas starts as many tasks as it can without waiting for the already started tasks to finish.

Dispatch sources are a mechanism for processing specific types of system events asynchronously. They encapsulate information about a specific system event in a block object or function and submit it to a dispatch queue when the event occurs. Timers and process-related events (?) are some of such system events.

Operation queues (NSOperationQueue) are Objective-C objects that act a lot like dispatch queues. While dispatch queues always execute tasks in first-in first-out order, operation queues take into account other factors while determining the execution order of tasks. The major such factor is dependencies a given task has on the completion of other tasks.

Although operation queues always execute operations concurrently, if needed dependencies can be configured to execute them serially.

Dispatch queues are more efficient, but provide very little control over the execution. The operations cannot even be cancelled. Hence, it is better to use dispatch queues when the tasks to be performed are very small and will require minimum memory. In other cases it is better to use operation queues. Link.


**************


Clock speed of CPU (processor). Number of processor cores per chip started increasing.

Traditional way to take advantage of multiple cores is to create multiple threads. Actually using them is not as simple because not all cores may be equally ready and number of available cores may be arbitrary. Asynchronous design approach in Apple systems provides an API to use them without directly having to interact with them by writing low-level code.
