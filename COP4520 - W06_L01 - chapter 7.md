### TTAS locks and backoff continued, lockout algorithms continued, how algorithms overcome issue of shared resource contention 

whats faster than a backoff lock system? the **Anderson Queue Lock**

uses a lot of memory, however performance is almost flat, and very scalable

when number of threads n is low, TTAS actually outperforms queue. 

false sharing???

also must know number of threads beforehand(compiletime??), this is very impractical

### **the CLH lock**
small, constant size overhead per thread, an implicit linked list

makes good use of memory, cahce memory, a degree of fairness as threads wait in FIFO. not limited by thread # like anderson is, implicit linked list can be dynamically allocated
good: lock release affects predecessor only, small, constant sized space

conc: doesnt work for uncached NUMA architectures

## The MCS lock
- FIFO order
- spin on local memory only
- small, constant sized overhead
- each thread performs busy waiit on its own cache vs prev thread's cache
	- this is much better for numa architectures than the CLH lock for this reason
- 