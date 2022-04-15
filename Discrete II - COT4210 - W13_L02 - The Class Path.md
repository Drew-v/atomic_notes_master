**Five things I have learned this lecture**
- 


note that Multi-tape-turing machines take polynomial time longer than standard deterministic turing machines

note that non-deterministic turing machines take exponentially longer than standard DTMs. 
### The path problem
given a directed graph G and nodes s and t:
observe by counting that a path can nver be longer than the number of nodes in G

#### Polynomial Equivalence 
theorem: all reasonable deterministic computational models are polynomially equivalent. 
	- meaning all can simulate eachother with only a polynomial increase in runnning time. 
We now focus on time complexity unaffected by polynomial equivalence, that is, between $n^2$ and $2^n$ but not $n^2\;and\;n^3$ 
*we venture further into the dimension of theory land...* 

### The complexity class P
the class of  problems we can solve in polynomial time, using real computers, in the real world and a realistic amount of time. Problems within the set class P are problems that computers can actually do

class P decidability 
- set containing all pilynomially decidable problems. 
- if can decided? it polynomial, then its in the class P
- 

#### Greatest Common Divisor 
![[Pasted image 20220414221048.png]]
every execution cuts number in half
exchange every step
so max repetitions is 2logn
so it is of order n on the length (digits) of input numbers

#### Relative Prime Numbers
![[Pasted image 20220414221416.png]]
given two integers x and y, they are relatively prime if 1 is the largest integer that evenly divides both of them

If problem A is polynomial and problem B can be reduced to problem A, then B must be polynomial. We use GCD to prove relative prime as polynomial complexity. 

#### Hamiltonian Path
![[Pasted image 20220414221547.png]]
hamiltonian path: a perfect path which goes throuhg each node exactly once. the idea is that it is a perfectly efficient tool. 

pick up april 7th lecture, 45 minutes...