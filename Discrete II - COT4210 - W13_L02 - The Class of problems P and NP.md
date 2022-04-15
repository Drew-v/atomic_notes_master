**Five things I have learned this lecture**
- class of problems P are the class that can be solved in polynomial time
- class of problems NP are the class of problems which can be solved in polynomial time in a non-deterministic manner, and be verified in polynomial deterministic time. 
- i learned of hamiltons shortest path algorithm which finds the shortest path connecting all nodes in a graph
- i learned of the importance of polynomial verifiability for class P and NP problems
- im just bsing at this poinnt


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

#### Intro to computability, complexity and P and NP class problems

[![image alt text?](http://img.youtube.com/vi/YX40hbAHx3s/0.jpg)](http://www.youtube.com/watch?v=YX40hbAHx3s "# P vs. NP and the Computational Complexity")

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

#### Polynomial Verifiability
where a problem verifier can check validity of a solution in polynomial time

note: hamilton's path is not achievable in polynomial time however we can verify a solution in polynomial time

**now what if we took a verifier and stuck it at the end of a non-deterministic turing machine?**
then we can just use non-deterministic nonsense to guess sequence. so we nondeterministically choose a path to verify, going down all possible paths at once. we non deterministically choose the path to verify then verify it. 

note: this runs into problem that a non-deterministic turing machine does not and cannot exist...
**but..** if we had one, we could solve hamiltonian path in non-deterministic polynomial time. 

**TO RECAP**: if we can nondeterministically guess solution, then polynomially verify that solution, then that problem is in the class NP, class NP being non-deterministic polynomial time algorithms. 

THE TRAP: is that it takes exponential time to simulate non-determinism. 

