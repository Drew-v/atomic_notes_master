#### Facts
1. every regular language is also a context free language
#### Theorems
1. Given PDAs recognize context free languages, and that a PDA is just an NFA with a stack, it can ignore its stack just like an NFA can ignore non-determinism 

### Formalizing our first Pushdown Automata
note the transition function has 3 inputs and produces 2 outputs:
input: 
	1. current state
	3. stack symbol
	4. next input char
output:
	1. output state
	  2. output stack symbol
at end of any transition we can either push or not push 
![[Pasted image 20220329152348.png]]
this recognizes palindromes??? what are palindromes??
push a char each time we read it. then non-deterministically, switch to popping a char each time we read it. this will only work for palindromes of even length. the switch must happen half way through the string. 
IN EFFECT: this reverses the string. {w$w^R$, W $\geq$ {0,1}$^*$} 
Important example:
![[Pasted image 20220329153552.png]]
#### CFLs and PDAs
NOTE: every PDA can become a CFG.
will be showing how to recognize any context free grammar with a PDA
**PDA tricks**:
1. use empty stack symbol
2. can push whole strings to stack, just note that for example: w= xyz, first z is pushed, then y and finally x.
 **Recognizxing CFLs with PDAs, the PLAN:**
- PDAs are equivalent in power to CFGs
- Use the non-determinism of PDAs
- we will use the stack to "walk" the string
**The general method:**
- push stack bottom symbol
- repeat forever:
	- pop stack, and switch on the result:
		- for variable A: 
			- new non-deterministic branch for each rule with A as the LHS
			- on each branch:
				- push the RHS
		- for terminal b:
			- read next input symbol
			- if next input symbol is b, continue
			- if not, reject on this branch
		- for stack bottom symbol $:
			- enter the accept state
				- accept the input if its all been read
**We build a PDA with 3 states:** 
1. set up state
2. loop state
3. accept state
![[Pasted image 20220329194039.png]]
![[Pasted image 20220329194350.png]]
S-> A
A-> a | aBC
B -> b | bC | BBb | $\varepsilon$ 
C -> c | A | cC | S 


<table>
<tr>
<th> PDA grammar </th>
<th> Stack </th>
</tr>
<tr>
<td>

S-> A  <br />
A-> a | aBC   <br />
B -> b | bC | BBb | [empy str]   <br />
C -> c | A | cC | S   <br />

</td>
<td>
<br />
Variables: <br />
empt str, S -> A <br />
empt str, A -> a <br />
empt str, A -> aBC <br />
empt str, B -> b <br />
empt str, B -> bC <br />
empt str, B -> BBb <br />
empt str, B -> empt str <br />
empt str, C -> c <br />
empt str, C -> A <br />
empt str, C -> cC <br />
empt str, C -> S <br />
<br />
Terminals:<br />
a, a -> empt str <br />
b, b -> empt str <br />
c, c -> empt str <br />

</td>
</tr>
</table>
NOTE: PDA has power to directly generate grammar of a CFG, CFG is a grammar expressed as a stack??

A PDA is just an NFA with a stack...