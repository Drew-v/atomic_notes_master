Transition from fully formal machine descriptions to quasi formal descriptions which focuses more on descriptions of implementations. 

reminders:
1. a turing machine can do three things: hang, accept, or reject.
2. turing recognizable language: a language in which a turing machine accepts all strings in the language
3. turing decidable language: language in whcich all strings out side the language are rejected and all strings inside the language are accepted


### Turing machine Variants

#### The enumerator 
a turing machine with a printer, instead of accepting, it generates all the strings accepted in its language. in order to produce a string, the machine is run for a finite number of steps. this is because the possibility that the machine can hang. 
NOTE: a turing machine enumerator can only recognize a language, it cannot decide it.

#### The Multitape Turing Machine
has a finite number of tapes, each with it's own read-write head. input appears one tape 1, and other tapes start out blank. transition and tape i/o occur in parallel
so with _k_ tapes we say:
$\delta : Q\times\Upgamma^k->Q\times\Upgamma^k\times\{L, R\}^k$  
this can be simulated with a single tape turing machine
- we store the k tapes by context switching the turing machine 
![[Pasted image 20220322135554.png]]

#### Non-deterministic Turing Machine
$\delta : Q \times \Upgamma -> P(Q \times \Upgamma \times \{L,R\})$ 
oh god...

NDTMs can be simulated using a deterministic turing machine, it follows that there is nothing a NDTM can do which a deterministic turiing machine cannot do. 
what cannot be simulated with a turing machine? 
FACT: nothing can be more powerful, computationally, than a turing machine

### Computability and algorithms: the church-turing thesis
descriptions of algorithms are equivalent in power to Turing Machines. 
- algorithm: any clear and unambiguous and finite set of instructions to a computerm each step which performs only a finite amount of work
- any algorithm can become a turing machine
this doesnt only hold for turing machines, it formalizes what we know about the ability to compile any computer language into any other, holding for any model of computation with:
1. unrestricted access to an arbitrary amount of memory
2. the ability to perform arithmatic in most general sense of the word
3. the ability to make decisions leading to computational branches
This thesis isnt so maych defiinition as it is theorem, it defines the entire way we think about algoriutns as computer scientists in the first place. 

NOTE: if a programming language meets those three requirements, then it is equivalent in power to a turing machine or any other programming language which meets those same requirments. 

__This speaks only to possibility of computation, not performance__
this amounts to the foundations of computability

by defining what we CAN do with a computer, we are also defining what we CANT do with a computer. 

some problems as we currently understand them, cannot be solved with a computer

GURDLES theorem??
cannot describe itself using only itself??

Three levels of formality for discussing Turing Machines:
1. full formal descriptions of states alphabets and transition function of the machine
2. quasi-formal implementation descriptiuons of the way the machine reacts to inputs
3. algorithmic high-level descriptions that describe clearly and unambiguously an algorithm to be executed 
The church-turing thesis tells us that all three of these descriptions are equivalent. This is theoryland, not a guide for implementing a new language ect. that is extremely complicated to go from pseudocode algorithm to executable binary. 

gerber's wisdom:
$O(n^2) = k \times n^2$, $n^2$ is coming from picking the right algorithm, k comes from writing good code. 

#### Encoding Data for Turing Machines 
any input which can be encoded as a string can be passed as input to a turing machine. observe that any object can be encoded as a string. We describe a graph G and write \<G\> to mean a notional encoding of that graph suitable for a turing machine. 

#### One more turing machine:
last slide of turing machinePPT, read slide and understand it. 