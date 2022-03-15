![[Pasted image 20220315113128.png]]
- a turing machine can write to its tape as well as read from it
- a turing machines tape can move left and right
	- generalized, it has random access memory (do not think DDR memory)
- a turing machine's tape is infinte 
	- think a turing machine has an arbitrary amount of memory
- there are special states for rejecting and accepting, that take effect immediately. 
	- a turing machine;s final states are immediately final. regardless if end of input has been reached
A turing machine is a 7-tuple: ($Q, \sum, \Upgamma, \delta, q_0, q-accept, q-reject$) with:
- note input alphabet $\sum$ is not allowed to contain the blank symbol
- the tape alphabet $\Upgamma$ MUST include the empty symbol

**Turing machine head movement** 
**note**: the turing machine cannot skip squares but must process one at a time to reach a particular place
**note**: if head tries to move from leftmost square, it stays on th leftmost square instead. 

the ***configuration*** of a turing machine is described by the current:
- state
- contents of the tape
- location of the head

slide 10 describes turing machine transitions, x is based on location of machine head, right of char being read. changes depending on if head is going left or right

transitions are defined in terms of head movement, not tape movement

ux q **a**v read the a,    ux q **b**v write the b,    ux **r** **b**v transition from q to r, u **r** xbv move the head.

this looks a lot like the von nueman cycle! the cycle is thus:
fetch-> decode-> increment-> execute

**Turing Acceptance**
**note**: think of a turing machine as an action table. 
If a turing machine reaches an accept state given an input string, we say it *accepts the string*, and likewise *reject* if it reaches reject state
***Note***: a turing machine may never get to an accept or reject state!! this is unlike a PDA, NFA or DFA. 
therefore not guaranteed to halt, infinite loop

- A Turing machine *recognizes* a language if it accepts the strings in it and no others
- A Turing machine *decides* a language if it accepts the strings in it and rejects all others
- A language is *Turing-recognizable* if some Turing machine recognizes it 
- A language is *Turing-decidable* if some Turing machine decides it
NOT ALL TURING-RECOGNIZABLE LANGUAGES ARE TURING-DECIDABLE
**note**: that it is harder to correctly reject than to correctly accept a string in a language. 
