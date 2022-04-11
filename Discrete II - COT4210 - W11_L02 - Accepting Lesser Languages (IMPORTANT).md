#### Acceptance of Regular Languages
![[Pasted image 20220405165003.png]]
the definition of a regular language is that it can be recognized by a DFA
	- this only happens if its possible to get from start state to accept state
therefore: therefore all regular languages are turing decidable

#### Emptiness of Regular Languges
![[Pasted image 20220405173029.png]]
#### Equivalence of Regular Languages
can we find out if two regular languages are equivalent? it turns out that this is decidable as well. we are asking if two DFAs are equivalent. 
>
Remember the symmetric difference between two sets, everything thats in B that isnt in A and everything in A that isnt in B
We already know that the basic set operations preserve regularity. (union complement and intersect). difference is derived from intersect with complement. difference and union become symmetric difference, so that also preserves regularity. thus symmetric difference of languages preserves regularity. 
NOTE ANY PROOF BY CONTRRUCTION IS AN ALGORITHM. THEREFORE WE KNOW A TURING MACHINE CAN COMPUTE THESE SET OPERATIONS. 


AND NOTE THAT any2  languages which are equivalent have no symmetric difference. Therefore they are decidable. 
![[Pasted image 20220405173553.png]]

NOTICE:  set theory is very important topic and relevant for programming algorithms. especially database systems.
#### Decidablility of Context Free languages
![[Pasted image 20220409144928.png]]
NOTE: the equivalence of CFLs is not decidable 
![[Pasted image 20220409150016.png]]
this works because if we cant generate all terminals from the start symbol then the language must be empty.pathfinding backward through the grammer to get to the start symbol. if start symbol is still marked at end of algorithm, it means it is unreachable from all terminal symbols. therefore the language must be empty. 

Before we discuss what we cannot do with turing machines, we must discuss infinity.
#### Brief Digression INTO INFINITY!
![[Pasted image 20220409151212.png]]
one of these sets is bigger than the rest. but which?

**We must define the size of infinity**
![[Pasted image 20220409151344.png]]
![[Pasted image 20220409151634.png]]
![[Pasted image 20220409151850.png]]
So we now define a *countably infinite set*: a set that is the same size as the natural numbers, that is, any set which can have an order imposed, where we can define the next item in the domain based on the previous item. 
![[Pasted image 20220409152221.png]]
prime numbers is a great example of this, we dont know the next prime from the previous. 

The impossible one: The set of all Real numbers: 
![[Pasted image 20220409153703.png]]
therefore its shown that the set of real numbers is uncountably infinite, a higher infinity than say the infinite set of integers.
we cannot say, what the next real number after say 1.12. If we say 1.13, then we notice that there is an infinite amount of real numbers between 1.12 and 1.13

also note that the real number set is continuous, whereas integers are discrete

From the above observations, we regocnize that the set of all strings over a given alphabet is countable.
any turing machine M can be encoded into a string W
therefore, the set of all turing machines on  a given alphabet is countable.

**This is known as the church-turing thesis**. A turing machine can be represented as a number. 

Discuss an infinite binary sequence, a set of infinite 0s and 1s
this set is uncountable like the set of real numbers. 

we have an *mapping bjection* (meaning of binary ) between a set of infinite binary sequences and the set of languages over any alphabet. this means they are uncountable. 
![[Pasted image 20220409161116.png]]
there are turing-unrecognizable languages
gerb says: there are not enough turing machines to recognize every language, because the set of languages is uncountably infinite, whereas set of turing machines is countably infinite. 
THIS IS WHY DISCRETE MATHEMATICS IS SO IMPORTANT TO COMPUTING! WE SHOW THAT NOT EVERY PROBLEM IS ABLE TO BE SOLVED BY A COMPUTER!!]]C