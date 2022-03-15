### reminders
**mutual exclusion**: a process locks down a shared resource while performing some operation with it. introduces ***waiting***. it is a *safety property*. 
**freedom from deadlock:** if some thread attempts aquiring lock, then some thread will succeed aquiring it. if it cannot, then some thread must be executing an infinite # of critical sections. *deadlock freedom is a liveness property*. 
**freedom from starvation:** every thread that attempts too aquire the lock eventually succeeds. every call to lock() returns. the starvation freedom property is the weakest property of the three
**correctness**: if a program correctly follows sequential behavior
**safety**: guarantee that some bad thing does not happen
**liveness**: progress guarantee
**transient communication:** both parties participate at the same time. 
**persistent communication**: parties participate at different times. 
**deadlock-free:** if one threads attempts aquire lock, it eventually succeeds. if two attempt lock aquire, then eventually at least one succeeds. *liveness property*.
**starvation-free:** stronger than deadlock freedom property, all threads attempting to access a critical section eventually make progress.  *liveness property*.
**Amdahls Law:** the more processors added is dependant on proportion of work which can be paralellized. its given as: $S =\dfrac{1}{1-p+{\dfrac{p}{n}}}$,
where S is given as the maximum speedup, achieved by n processors where p is the fraction of the job which can be parallelized
***thread***: a **state machine** whose state transitions are called ***events***. 
***partial order*** & ***total order***: [[total order and partial order]]
***total method***: a method is total if it is defined for every object state, otherwise it is called a ***partial method***. 


### Chapter 3: concurency, correctness
**concurrent object behavior**: described with safety and liveness properties, referred to as correctness and progress. three correctness conditions examined: **Quiescent consistency, Sequential consistency and Linearizability.** Quiescent consistency trades weak concurrency constraints for high performance. Sequential consistency is stronger condition often useful for low level hardware systems. Linearizability is the strongest constraint which ensures a system's behavior can be mapped sequentially.

#### Chapter 3 principles:
- **3.3.1:** Method calls should appear to happen in a one-at-a-time sequential order. 
- **3.3.2:** method calls separated by a period of quiescence should appear to take effect in 
			  their real time order
- **3.4.1:** method calls should appear to take effect in program order
- **3.5.1:** each method call should appear to take effect instantaneously at some moment 
             between invocation and responce. 

#### Chapter 3 facts:
- If -> is a partial order on X, then there exists a total order "<" on X such that if x->y, then x < y. 
            
#### Vocabulary
- *program oder*: order in which a single thread issues method calls. 
- *well formed* history: a history is well formed if each thread subhistory is sequential. 
- history *extension*:  is a history of history H which includes all pending invocations which have no matching responces. 
- *complete* history: is a history H where for every invocation there is a matching responce. 
- *sequential specification*: is a set of sequential histories for an object
- *linearizable*: a history is linearizable if it has an extension H' and there is a legal sequential history S such that 
	- L1 complete (H') is equivalent to S, and
	- L2 if method call $m_0$ precedes method call $m_1$, in H, then the same is true in S
- *linearization*: a specific *legal* and *complete* history of H, which there can be many linearizations of a specific history H. The above history S is a linearization of H.
- *wait-free* a method is wait free if it guarantees that every call finsihes its execution in a finite number of steps. 
- *bounded wait free* a method is bounded wait-free if there is a bound on the number of steps a method can take.
- population-oblivious is a wait-free method whose performance does not depend on the number of threads making method calls. 
-  *lock-free method* guarantees that infinitely often *some* method call finishes in a finite number of steps. any wait-free method is also lock-free, but not vice versa.
- *dependant progress conditions*, are progress conditions which rely on the operating system to provide certain guarantees.
- 
#### Chapter notes:
sequential consistency is useful to describe hardware systems where composition is not important. For most algorithms in this textbook are linearizable, which is more useful in programs, because programs tend to benefit from compositionality. 

#### 3.3 Quiescent Consistency
**Quiescent consistency**, a correctness property, is defined by 2 principles:
 - method calls should appear to happen one at a time in sequential order. 
 - method calls separated by periods of quiescence (no active method calls) should appear to take effect in their real time order
 To summarize informally: any time an object becomes quiescent then the execution so far is equivalent to some sequential execution of the completed calls. 
 
 As a useful example: consider a counter, which is incremented in a while loop. If the order of execution does not matter, a quiescent counter could be used, only guaranteing that each value of counter will be executed, but not each value of counter will be issued in sequential order. 
It is stated that Quiescent consistency is a *non-blocking* correctness condition. (total vs partial methods, p51)
The Quiescent consistency property is considered ***compositional***, because if objects of a system are quiescently consistent, then the property holds for the system as a whole. 

#### 3.4 Sequential Consistency
principels 3.3.1 and 3.4.1 together define a *correctness property* called ***sequential consistency***, which is widely used in literature on multiprocessor synchronization. In any concurrent execution, there is a way to order the method calls such that they are (1) consistent with program order and (2) meet object's sequential specification. **it should be stated there can be more than one order satisfying this condition. 

**Note:** sequential and quiescent consistency are *incomparable*, there exists sequentially consistent executions which are not quiescently consistent and vice versa. Quiescent consistnecy does not nesisarily follow program order, and 

**Important**: in most modern computer architectures, read and writes are not sequentially consistent, because the vast majoprity of read-writes do not need synchronization.  A program must specify when sequential consistency is needed. special instructions tell the processor to propagate updates to and form memory as needed, to ensure that reads and writes interact  correctly. these special instructions are usually memory barriers or memory fences. 
**sequential consistency and *composition***: is it compositional? no. a system of sequentially consistent objects is not nesisarily sequentially consistent itself. 

#### 3.5 Linearizability
We see sequential consistency is not compositional, so propose a new stronger restriction: each method call should appear to take effect instantaneously at some moment between invocation and responce. 

This principal principle states real time behavior of method calls must be preserved. This is called ***linearizability***. Every linearizable execution is sequentially consistent, but not every sequentially consistent execution is linearizable. 

The linearization point is what is used to identify if an object implementation is linearizable. For a lock based system, this is the critical section. For non lock-based systems, the linearization point can be a single atomic step where effects of the method call become visible to other threads. 

#### 3.6 Formal Definitions, concurrent system history
Reminder: a concurrent object is linearizable if each method call's effects appear to happen instantaneously at some moment between its invocation and return. 

the execution of a concurrent system is modeled by its ***history***, which is a finite sequence of method invocations and responce events. 
formalizing the format of a concurrent system's **history**:
- method invocation: {X.m(a*) A} where x is an object, m is a method name, a* a seqience of arguements, and A a thread. 
- method responce: {x:t(r*) A}, where t is either OK or an exception name, and r* is a sequence of result values. sometimes an event with a thread labeled A is referred to as a step of A.
In some histories, method calls do not overlap. History H is sequential if each method invocation (except possibly the last) is immediatly followed by its responce. 
A method invocation is considered pending if it has no matching responce. As such, calls which have not returned must be distinguished from those that have not. An **extension** of a history is a history H which includes all pending method invocations. a **complete** history H is a history which for every invocation there is a matching responce. 
An object is sequential if it has a legal ***sequential specification***. a *sequential specification* is a set of sequential histories for an object. a sequential history of an object is ***legal*** if each object subhistory is legal for that object. 

a history is **well formed** if each thread history is sequential. Note: thread subhistories of a well formed history must be sequential, but the object subhistories need not be. 

a *partial order* on a set X is a relation that is [[reflexive irreflexive and transitive| irreflexive and transitive]]. That is it is never true that x -> x and whenever x -> y and y -> z, then x -> z. *Note* that it is possible that there are distinct x and y such that neither x -> y nor y->x. A *total order* < on X is a partial order such that for all distinct x and y in X, either x < y or y< x. any partial order can be extended to a total order: If -> is a partial order on X, then there exists a total order "<" on X such that if x->y, then x < y. 

shorthand for (H at A): read history of thread A, also subhistory of thread A, shortened to H | A.
introducing shorthand notation to state a relation: method call $m_0$ precedes method call $m_1$ in history H if $m_0$'s responce event occurs before $m_1$'s invocation. So we say that 
$m_0->_H m_1$ if $m_0$ precedes $m_1$ in H. Notice that  $->_H$ **is a *partial order***. Also notice that if H is sequential, then $->_H$ **is a *total order*.** Finally, given history H and an object x, such that H | x is the subhistory of x, and contains method calls $m_0$ and $m_1$, we say that 
$m_0 ->_x m_1$ if $m_0$ precedes $m_1$ in H | x. 

#### 3.6 Linearizability
Basic idea: every concurrent history is equivalent to some sequential history. WHen one method call preceds another, then earlier call must have taken effect before the later call. If method calls overlap, then precedence is ambigious, and we are free to order them as we see fit. 

**Linearizablilty is compositional:**
***Theorem 3.6.1***: H is linearizable if and only if for each object x, H | x is linearizablr. 
**Linearizability** is a ***non blocking property*** 
a pending invocation of a total method is never required to wait for another pending invocation to complete. 
inv(m) is an invocation of a total method. if {x inv P} is a pendin ginvocation in a linearizable history, then thre exists a respionce {x res P} such that H*{x res P} is linearizable. 
*therefore* linearizability by itself never forces a thread with a pending invocation of a total method to block. 
For systems which concurrency and real-time responce are important, linearizability is an appropriate correctness condition. 
**the nonblocking property does not rule out blocking where it is explicitly desired:** it is sensible for a thread attempting to deque from an empty queue to block, waiting until another thread enques an item. **This behavior could be made through making the dequeue()  a partial method**, where it is undefined for an empty queue. 
??naturally?? concurrent interpritation of a partial sequential specification is to wait until the object reaches a state where the method is defined. 

#### 3.7 Progress conditions
linearizability's *nonblocking* property states any pendin ginvocation has a correct responce. This says nothing about how a responce is comupted. THere are two relevant implementations, *blocking* and *nonblocking*. In a *blocking* implementation, if a thread halts in a critical section it prevents other threads from accessing that resource. In a *nonblocking* implementation, that thread does not rely on a lock, and as such does not prevent other threads from accessing that shared resource if it is halted. 
a method is ***wait-free*** if it guarantees that every call finsihes its execution in a finite number of steps. it is ***bounded wait free*** if there is a bound on the number of steps a method can take. 
**wait-free systems are compositional.** *wait-free* is *nonblocking*
a method is ***lock-free*** if it guarantees that infinitely often *some* method call finishes in a finite number of steps. any wait-free method is also lock-free, but not vice versa.

#### 3.7.1 Dependent progress conditions
*wait-free* and *lock-free* nonbloocking progress conditions **guarantee that the computation as a whole makes progress**, independantly of how the system schedules threads. 
the lliveness properties deadlock-free and starvation-free are ***dependant progress conditions***, meaning they rely on the operating system providing certain guarantees. These properties are useful when the OS guarantees that every thread leaves a critical section in a timely manner. 
therefore, **note** that classes whose methods rely on lock-based synchronization can guarantee at best, dependant progress properties. therefore the rate of occurance of things like premption should be taken into account when designing a  system.  

two kinds of locks: implicit and explicit. both have same implications for memory behavior. 
#### 3.8.2 Volatile fields
volatile fields are linearizable. volatile fields ensure that a certain expected memory state is true across different threads. A common usecase here is when only one thread writes to a field, and the rest read from it. 
#### 3.8.3 Final fields
static fields do not require synchronization. if a object constructor is initialized incorrectly however, then final fields may be observed to change value and as a result will not be synchronized. simply put, a constructor's **this** reference must not be released before the constructor returns. 
**in summary:** reads-writes to fields are linearizable if either the field is volatile, or the field is protected by a unique lock which is aquired by all readers and writers.
#### 3.9 Remarks
progress guarantees should be chosen depending on the needs of a program. The same goes for correctness conditions...