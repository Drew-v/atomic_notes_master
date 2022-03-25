#### Chapter intro
We will see that all synchronization instructions are not created equal. If one thinks of primitive synchronization instructions as objects whose exported methods are the instructions themselves (in the literature these objects are often referred to as synchronization primitives), one can show that there is an infinite hierarchy of synchronization primitives, such that no primitive at one level can be used for a wait-free or lock-free implementation of any primitives at higher levels. The basic idea is simple: each class in the hierarchy has an associated consensus number, which is the maximum number of threads for which objects of the class can solve an elementary synchronization problem called consensus. We will see that in a system of n or more concurrent threads, it is impossible to construct a wait-free or lock-free implementation of an object with consensus number n from an object with a lower consensus number.

#### Chapter definitions
- consensus: a *consensus* object provides a single method *decide*. each thread calls the decide method with input v *at most once*. the object's decide method will return a value meeting the following conditionsl:
	- consistent: all threads decide on the same value
	- valid: the common decision valie is some thread's input 
- *consensus protocall*: any class that implements *consensus* in a wait-free manner.
- deterministic sequential specification: objects in which each sequential method has a single outcome.
- *binary consensus:* 

#### 5.1 consensus numbers
this discusses objects which have a *deterministic sequential specification*, that is, objects in which each sequential method call has a single outcome. 

**Definition 5.1.1:** A class C solves n-thread consensus if there exist a consensus protocol using any number of objects of class C and any number of atomic registers. 
**Definition 5.1.2:** The consensus number of a class C is the largest n for which that class solves n-thread consensus. If no largest n exists, we say the consensus number of the class is infinite. 
**Corollary 5.1.1:** Suppose one can implement an object of class C from one or more objects of class D, together with some number of atomic registers. If class C solves n-consensus, then so does class D.

##### 5.1.1 States and Variance
