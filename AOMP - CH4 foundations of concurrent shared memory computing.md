**chapter introduction**
we learn about shared memory coputation, which consists of multiple threads, each of which is a sequential program inits own rihty. threads communicate by calling methods of objects that reside in shared memory. Threads are asynchronous, meaning they run at different speeds and any thread can halt for any amount of time. Thread interuptiopns can range from microseconds (cache misses) to miliseconds (page faults) to seconds (scheduling interupts). We learn these concepts using very easy to understand but innefficient constructs. 
### Chapter definitions and vocabulary


### 4.1 The space of registers
wealest form interthread communication is setting a flag bit. if no constraints, a write could be interupted by a read. if this happens, then any number could be read form the register. 
A single writer and multi-reader is *safe* if:
- a read that does not overlap write returns most recent written value.
- a read call overlapping a write can return any value in the registers domain, 0 - (M -1) for a m valued register 
Dont be mislead by the term *safe*, this should be considered unsafe. a safe register provides a very weak guarantee. 

as defined in chapter 3, object implementation is wait-free if each method call completes in a finite number of steps. this guarantees *independant* progress.  (independant of OS scheduler). 
So we want registers to be wait free. 

Registers can be grouped by nummber of readers and writers:
- SRSW, single reader single writer
- MRSW
- MRMW
these registers will store integers, booleans or references.
**a fundamental question:**: can any data structure implemented from the most powerful registers we define also be implementd from the weakest?

now define a level of safety in between *safe* and *atomic*, a ***regular*** register:
-  a read that does not overlap write returns most recent written value.
- 