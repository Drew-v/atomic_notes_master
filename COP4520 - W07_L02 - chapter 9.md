## synchronized linked list, algorithms for multthreaded operations over linked list

### Vlidation: hand over hand vs optimistic synchronization, missed lectures information, chapter 9. pop quiz for extra credit coming up

fine grain synchronization?

hand over hand locking? terribly expensive aand causes bottlenecks

solution? optimistic synchronization
- ony aquire locks when target elements of predesessor?
- find element first in a remove operation, then aquire lock on element and its predecessor 
- if conflict is encountered, operation must be restarted (ex. predessesor diapears while aquiring lock, must search for it in list and find it to continue, else abort)
- **if we do not aquire locks, do analysis of how another thread could possibly be overlapping** , for example, if C is inserted, but then is attempted to be removed, but falsely returns C not found 

## Validation pseudocode analysis
if optimistic assumption doesnt pay off (lots of conflicts, resulting in slow execution) then its time to write another type of algorithm 

### optimistic list
- missed slide

- much less aquisition/release
	- performance, concurrency
- problems
	- need to traverse list at least twice 
	- contains() method aquires locks
		- cotains() is not wait free

optimistic is effective if
	- cost of scanning twice without locks is less than 
    - cost of scanning once with locks
improvement if can implement contains without locks


### next version in the set: Lazy list
- like optimistic except:
	- scan once
	- contains(X) never needs to lock
- key insight:
	- removing nodes causes trouble
	- do it "lazily"

remove()
- scans list (as before)
- locks predecessor, and current (as before)
logical delete
- marks current node as removed(new)
-physical delete
- redirects predecessor's next(as before)

marking is done for the benefit of other threads to be abe to examine node contents without needing a lock, specificaly contains() method and others

marking is done before a remove operation is executed, with the same lock

linearization point is when mark is set to true

reminder: wait free means locks are not used

IN SUMMARY, Lazy List has
- lazy add() and remove() plus wait-free contains()
wait free progress guarantee, at least one thread will complete in a certain number of steps. these cannot be applied to algrotithms with multiple locks. 

the good: contains is wait free, bad: add and remove lock and are not wait free

bit stealing from pointer to use as flag in add(), stealing because of word alignment in memory! allows two atomic operations to be combined into one! very clever