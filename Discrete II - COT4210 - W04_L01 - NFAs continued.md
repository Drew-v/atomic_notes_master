**Reminder to self: a powerset of a set S is the set of all  subsets of S**

**DFA & DFA equivalence**: the capabilities of NFAs are a strict superset of DFAs. no proof needed. whats more complicated to show is that every NFA can berepresented as a DFA. 

### Simulating NFAs with DFAs (slide 46 automata)
[FSM builder](https://madebyevan.com/fsm/)

**NFA can do three things that DFAs cannot do:**
- have multiple transitions on the same symbol
- empty strinng transitions
- no transitions on some symbols

note **relationship between power set and NFA:** when nfa transitions state, it is transitioning from one element of the powerset to the next, based only on the the next input symbol. 

so how many possible states in a DFA? imageine each state as an element of a truth table. if three possible states, then cardinality of the power set (set of all possible set combinations) is 2^(num states). for DFA w/3 states, that number is 8.

when choosing start, state, realize that if there is an empty set transition from starting node, that too is in the starting node set

accept any set containg state 1

note when transitioning to a state with an empty state transition also transitions to any empty set transitions attached. if transitioning to a state with an empty set transition, must always follow that transition**

PHI represents failure state

once all states have been simulated, finish by eliminating state sets which are not possible. 

IF NFA and DFA are equivalent, they can both recognize the same language. 

ALSO: language is only regular if and only if it can be recognized by an NFA