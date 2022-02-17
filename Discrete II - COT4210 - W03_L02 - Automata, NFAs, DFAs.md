what is a **regular language**: a language that can be expressed with a regular expression or a deterministic or a non-deterministic fintite automata or state machine. A **language** is a set of strings
picking up at regular operations

Remember: a language is a set of strings

applying union operation to regular language preserves the regular property. and this is true for all regular operations

we know that somethjing is a regular language if a DFA can recognize it

when you have a regular language C consisting of A u B regular languages, C finite automata is literally running A and B machines at the same time, processing A and B ordered pairs over the cartesian product of AxB

C(A, B) is in accept state if A or B is in accept state

### Non-Deterministic Finite Automata
like DFA, but input can follow multiple paths. If at least one path leads to accept state, then it is in accept state. 

think of this process as a threaded instance, where NFA calculates each possible outcome and accepts if at least one ends in accept state. think of this process as a breadth first search.

a problem represented by a DFA can always be represented by an NFA and vice versa. However NFAs can simplify very complex problems.

