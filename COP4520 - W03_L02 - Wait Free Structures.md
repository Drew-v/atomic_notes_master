Wait free queue
how to map concurrent execution to sequential?
identify where in code an operation becomes visible to other threads. 
everything before then should be considered a blackbox to threads. as if operation has not yet taken place. 
![[Pasted image 20220127182617.png]]
in this example the visibilkity point is tail++ or head++. these are called linearization points

if operation breaks early, ie if queue is full, linearization point is at the tail-head if statement, when exception is thrown

the 'correctness' of a concurrent algorithm refers to if its behavior matches a sequential counterpart, basically, to always give the same and correct answers as sequential counterpart. 

linearization points dertermine order of operations

safety is similar or same concept to correctness.

cannot achieve wait free structure using locks or mutual exlusion, only using atomic operations

wait free isnt a statement that no locks are used (although it does also mean this) BUT RATHER IS A PROGRESS GUARANTEE

when designing a new program, must start with ensuring safety/correctness, and liveness

linearizability: page 46 in chpt3 ppt. important concept to building a concurrent program

