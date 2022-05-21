• Dispatch queues can be serial or concurrent, but are always first-in first-out. (It doesn't quite mean that a task submitted later will be finished later, but rather that the tasks will be started in the order they are submitted.)
• Operations can have dependencies and priorities.
• InvocationOperation has a target and a sepector as operation.
• BlockOperation can have multiple blocks as the operation.
• A concurrent operation should override start, isConcurrent, isExecuting, isFinished methods.
• Maximum concurrent operations can be set for an operation queue.
• It is better to just add an operation to operation queue than to manually start it.
• To remove an operation from operation queue, it should be cancelled. In dispatch queue however, there is no way to cancel a submitted task.
• Dispatch queue is more efficient and is better for short tasks. However, operation queue gives lot more control.
