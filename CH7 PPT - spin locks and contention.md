**chapter 7 goals**:
1. think of performance not just correctness and progress
2. understand link between algorithm implementation and hardware architecture
3. get to know a collection of locking algorithms 

**chapter 7 definitions**
1. *invalidation storm*: 
2. TAS lock:
3. TTAS lock:
4. backoff lock:

aquire lock -> fail
a - immediately repeat until success
	good if delays are short and not much competition
b - give up the processor
	good if delays are long and expect a lot of thread competition
***spin lock*** spins until lock is aquired. this introduces significant ***contention***. *contention* is when a threads waste each others time trying to aquire a lock 

**to increase performance of blocking concurrent methods** (mutual exclusion)
1. optimize bandwidth used by spinning threads
2. release/aqiure latency
3. aquire latency for idle lock

### **lock types**
**test-and-set locks, test-and-test-and-set**
- lock is free: bool flag is false
- lock is taken: bool flag is true
- aquired by calling TAS()
	- if res is false, you win
	- if res is true, you lose
- release lock by writing false

**why does TASLock perform poorly?**
- TAS invalidates cache lines
- spinning threads:
	- miss in cache
	- go to bus
- thread wants to release lock, but is delayed by spinners

**how does TTAS perform differently?**
- wait until lock 'looks' free
	- spin on local cache
	- no bus use while lock busy
- problem: when lock is released can lead to *invalidation storm*: setting lock to 
   false(available) invalidates cached copies of lock, forcing other threads to read from memory. this cycle repeats and floods the bus with traaffic, slowing things down. 

How to minimize *invalidation storm* dleays in TTAS? 
***Backoff*** lock: after failed lock attempt, wait specified or exponential time period based on # of failed attempts 
	**pros**: easy to implement, beats TTAS lock
	**cons:** must tune params carefully, not portable across platforms
how to avoid issue of platform incompatability?
introduce a thread queue for the lock!

***Anderson Queue Lock***
addresses weakness of TTAS backoff lock
- avoid useless invalidations, threads wait in line
- each thread notifies next in line, without bothering others
- implement bool linked list? of flags
	- flag\[i\] where i is thread place. only value at front is set to true (allowed to aquire lock), others must wait
- implementation details slide 51
note that false sharing causes cache invalidation (require from memory) which results in bus contention. **the solution** is to store each bit flag on its own separate cache line

**an anderson queue lock performs better than TTAS but only at higher n values of threads**. another benefit is that this lock guarantees no lockout, and lock given on first come first serve basis

***the good***:  
1. truly scalable
2. simple and easy to implement
3. back to FIFO order (like bakery)
***the bad***: 
1. space hog, one bit per cache line, one line per thread
2. bad if n threads not known beforehand
3. bad if num of actual threads contenders is small 
 **memory usage** is O(L\*N) where L = num of locks, N = num of threads

***CLH Queue Lock***
addresses weakness of anderson queue
- FIFO order
- small, constant-size overhead per thread
- uses implicit linked list to create queue. 
- memory usage is O(L+N) where L = num of locks, N = num of threads
**disadvantage?**
performs poorly on NUMA architectures

**NUMA Architectures**: Non-Uniform-Memory-Architecture
![[Pasted image 20220316204725.png]]

**The MCS Lock**
- FIFO order
- spin local mem only
- small, constant sized overhead
- maybe is specialized for NUMA? not sure. p140

**Real Time Systems needs: abortable locks**
- what if a need arises for thread to abort a lock?
	- in case of timeout
	- database transaction aborted by user
1. for *backoff* lock, aborting trivial. return from lock() call
2. for *queue* lock, aborting a lock will starve other threads, they wont be able to aquire lock. must have additional flag for abort case
This leads to the last lock reviewed, the **ToLock** or time out lock. 

chapter 7 done!! woot