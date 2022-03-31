#### Facts
#### Theorems

### what is Chomsky Normal Form?
- a simplified form for context-free grammars
- useful for forking with CFGs using algorithms
A CFG is in Chomsky Normal form if:
- every rule is of the following forms:
	- A->BC
	- A->a
	- S-> $\varepsilon$ 
#### Converting to CNF from CFG example
Converting to CNF: 4steps
![[Pasted image 20220329132815.png]]
given example grammar, convert to CNF:
S->A
A->a|aBC
B->b|bC|BBb|$\varepsilon$ 
C->c|A|cC|S

 ---
1.  $s_0$ -> S
	- this is because we cant rewrite to old start variable
$s_0$ -> S
S->A
A->a|aBC
B->b|bC|BBb|$\varepsilon$ 
C->c|A|cC|S
2. only B leads to empty string, so replace B w/$\varepsilon$ 
	- B->b|bC|BBb|$\varepsilon$ , BBb := $\varepsilon$Bb | B$\varepsilon$b | $\varepsilon$$\varepsilon$b, := b|bC|BBb|$\varepsilon$ | Bb
$S_0$ -> S
S->A
A->a|aBC| aC
B->b|bC|BBb|$\varepsilon$ | <mark>Bb</mark>
C->c|A|cC|S
3. get rid of unit rules: C->A|B ect... then replace with their respective transformations
$S_0$-> <del>S</del> | **a | aBC | aC**
S-> <del>A</del> | **a | aBC | aC**
A-> a | aBC | aC
B-> b | bC | BBb | $\varepsilon$ | Bb
C-> c | <del>A</del> | cC | <del>S</del> | **a | aBC | aC**
4. convert all the remaining rules, **BUT**: note some vars cannot be generated anymore. cross these out
$S_0$-> a | aBC | aC
<del> S-> **a | aBC | aC** </del>
<del> A-> a | aBC | aC </del>
B-> b | bC | BBb | $\varepsilon$ | Bb
C-> c | cC | a | aBC | aC
	4. a) take care of mixed and multiple terminals
		- everywhere there is a terminal that isnt alone, replace w/new 
		  vars
		- can have exactly one terminal OR 2 or more variables
		$A_0$ -> a
		$B_0$ -> b
		$C_0$ -> c
		$S_0$-> a | $A_0$BC | $A_0$C
		B-> b | $B_0$C | BB$B_0$ | $\varepsilon$ | B$B_0$
		C-> c | $C_0$C | a | $A_0$BC | $A_0$C
	4. b) eliminate long rewrites: long rewite if var is being rewritten to more than 2 elements
		$S_0$-> a | **$A_0$BC** | $A_0$C
	B-> b | $B_0$C | **BB$B_0$** | $\varepsilon$ | B$B_0$
	C-> c | $C_0$C | a | **$A_0$BC** | $A_0$C
		$A_1$ -> $A_0$B
		$B_1$ -> BB
		$S_0$-> a | **$A_1$C** | $A_0$C
	B-> b | $B_0$C | **$B_1$$B_0$** | $\varepsilon$ | B$B_0$
	C-> c | $C_0$C | a | **$A_1$C** | $A_0$C
**This is the final result, from CFG to Chomsky Normal Form!:**
$S_0$-> a | **$A_1$C** | $A_0$C
B-> b | $B_0$C | **$B_1$$B_0$** | $\varepsilon$ | B$B_0$
C-> c | $C_0$C | a | **$A_1$C** | $A_0$C

So why do we want to translate to CNF? Because we always know we will grow the string exactly n-1 times, and it will not string. This is because each variable can only turn into a final variable of the same length. 
We also know the process will take exactly 2n-1 steps to derive any string in the Chomsky Normal Form grammar. It is much more predictable than normal CFGs. This becomes useful later to prove properties of context free grammars. 

---
### A new kind of Automaton: Pushdown Automata
a pushdown automata is an NFA with a stack. at any transition, it can push data onto the stack. 
![[Pasted image 20220329144741.png]]
left side of 'a, $\varepsilon$ ->a', 'a' is the transition function. the right side, '$\varepsilon$ ->a', shows what is popped and pushed. left side of that is what is popped, right side is what is pushed. 
![[Pasted image 20220329145318.png]]
note that in this context, $ represents the bottom of the stack. we cant accept until we pop the stack bottom symbol. it recognizes string w if and only if it has the form $0^n1^n$. 
NOTE: this is an enhanced NFA not an enhanced DFA. in this case if a 2 is read, then you enter the abyss (stops). 

---
#### Proper definition of the Pushdown Automaton
A pushdown automaton: is a 6-tuple, M = (Q, $\Upgamma$ , $\delta$, $q_0$, q0 , F) with:
- Q as the set of states.
- $\sum$ as the input alphabet
- $\Upgamma$ as the stack alphabet
- $\delta: Q\times\sum_{\varepsilon}\times\Upgamma_{\varepsilon}$ -> P(Q$\times\Upgamma_{\varepsilon}$) as the transition funciton
- $q_0 \in$ Q as the start state, and
- F $\subseteq Q$ as the accept states