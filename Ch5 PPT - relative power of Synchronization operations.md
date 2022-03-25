***Wait-free synchronization*** a good idea, but how to implement it?? 
- systematically?
- correctly?
- efficiently?

two thread wait-free queue: one for enqueue() and one for dequeue()
- methods are partial, they block when object state is not defined. that is, they spin in  an empty while loop. 
- they are still considered non-blocking methods as their blocking behavior is explicitly desired
**VOCABULARY**
- ***consensus***: each thread has a private input, they communicate and agree on one thread's input. Formally, two properties of consensus:
	- *consistent*: all threads decide the same value
	- *valid*: the common decision value is some thread's input
- ***CONSENSUS NUMBER***: an object X has a *consensus number* n 
	- if it can be used to solve n-thread consensus
		- take any number if instances of X
		- together with atomic read/write registers
		- and implement n-thread consensus
	- BUT not (n+1) thread consensus

***THEOREM - wair-free implementation:*** there is no wait-free implementation of n-thread consensus from read-write registers
	***impies:*** asynchronous computability different from turing computability
**why is consensus useful for concurrent objects?**: to determine if an n-thread algorithm is possible to be built wait-free??? details page 31

***THEOREM - consensus numbers1:*** atomic read/write registers have consensus# of 1
***THEOREM - consensus numbers2***: multi-dequeuer FIFO queues have consensus number of at least 2
	**Consensus numbers measure synchronization power**
***THEOREM - consensus numbers3***: if you can implement X from Y AND X has a *consensus* number of c THEN Y has a *consensus* number at leasst c
**conversely**
	**Synchronization speed limit**
if X has consensus number c AND Y has consensus number d < c THEN there is no way to construct a wait-free implementation of X by Y
**this theorem  is very practical and has many unforseen implications!** keep it in mind
**read-modify-write objects**: method call returns objkect's proir value x, replaces x with **mumble(x)** 
- most synchronizatioun instructions are RMW methods
- those that are not can be trivially transformed into RMW methods
- why identity funciton on slide 60?
**DEFINITION - RMW method triviality:** method is trivial if there exists a value v such that v $\neq$ mumble(v). for example Identity(x) = x is trivial. getAndIcrement(X) = x+1 is non trivial. 
**THEOREM - RMW methods**: 
1. any non-trivial RMW obkect has consensus # of at least 2. 
2. no wait-free implementation of RMW registers from atomic registers
3. hardware RMW instructions not just a convienience

note: subclasses of *consensus* have 
- propose(x) method
	- which stores x into proposed\[i\]
	- is a built in method
- decide(object value) method
	- which determines winning value
	- customized class-specific method
**compareAndSet() has an $\infty$ consensus #**: 
```
public class RMWConsensus extends ConsensusProtocol {
	private AtomicInteger r = new AtomicInteger(-1);
	
	  public T decide(T value) {
		  propose(value);
		  r.compareAndSet(-1, i);     //try to swap in currThreadID
		  return proposed[r.get()];   //decide winner's preference
		  }
	  }
}
```
**the consensus hierarchy**
1. read/write registers, snapshots...
2. getAndSet, getAndIncrement...
3. ....
...
$\infty$. compareAndSet(), ...

chapter 5 done