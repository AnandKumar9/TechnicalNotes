Every thread in a running program has one stack which it uses to stire state for function calls.

When the thread executes a function call, a new frame is pushed onto its stack. This newly created stack frame can be used by the function to store local variables, the return address, and any other information that is needed. Once the function finishes executing and returns, its stack frame is popped. 
