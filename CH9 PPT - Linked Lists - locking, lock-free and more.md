Concurrent objects!

### Coarse-Grained Synchronization
- each method locks the object 
	- avoid contention using queue locks
	- easy to reason about for simple cases
**problem:** sequential bottle neck
- threads stand in line (queue)
- adding more threads
	- does not improve throughput
	- struggle to prevent from getting worse

**SO some applications are inherently parallel**. now we introduce four 'patterns', methods that can be applied in many situations, for highly-concurrent objects
1. **Fine-Grained-Synchronization**
	- instead of single lock,  split object into independantly synchronized compnents
	- methods conflict when the access the same component at the same time
2. **Optimistic Synchronization**
	- search without locking
	- if found, lock and check
		- ok operation done
		- oops start again
	- evaluation is cheaper than locking but mistakes are expensive
3. **Lazy Synchronization**
	- postpone hard work
	- removing components is tricky
		- logical removal: mark component to be deleted
		- physical removal: do what needs to be done
4. **Lock-Free Synchronization**
	- no use of locks at all
		- instead use compareAndSet() and *relatives*
	- advantages: no scheduler assumptions/support
	- disadvantages: complex and sometimes high overhead

continue here tomorrow at slide 17. maybe start with video lecture, chapter 9 topics supposedly start about an hour into part 1?