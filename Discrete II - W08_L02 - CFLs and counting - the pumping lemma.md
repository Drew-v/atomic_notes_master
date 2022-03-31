### Pumping Lemma for Context free languages
If A is a CFL there is a pumping length p where 
if s $\in$ A and | s | $\geq$ p, s= uvxyz so that:
1. $u\,v^i\,x\,y^i\,z\in\:A$  for all non-neg ints i
   u is prefix string, z is suffix string, x is central string. v is the cycle prefix and y is the cycle suffix, which have to work for any i. 
2.  | VY | > 0
3. | vxy | $\leq$ p
--- 
- NOTE: pumping a parse tree works up and down. pumping down reduces complexity
- NOTE: we are assuming chomsky normal form for these pumping lemma CFL problems. 
- NOTE: pumping lemma for CFLs is symmetric, because it has a left branch and a right branch for the parse tree. which is why it has two expanding chars?? unlike the pumping lemma for regular languages. 

#### example 1:
Consider the alphabet $\sum = {a,b,c}$ and the language L = {$a^nb^nc^n\,|\,n\geq\,0$}. **Show that L is not a context-free-language**

we will show that CFLs can only count once. 

Assume BWOC that L is context free. THen it has a pumping length which we will call p. Consider the string $a^pb^pc^p$, clearly s $\in$ L; equally clearly |s| $\geq$ p. So:
> s = uvxyz so that:
> PL1:    $u\,v^i\,x\,y^i\,z \in L$ for all non-neg ints i       repition
> PL2:   |vy| > 0                                                 nontriviality 
>	     - *constructive dilemma: either v or y is empty*
> PL3: |vxy| $\leq$ p                                                 repition cycle isnt long

<mark> Now as before well take apart the string. y is always the important part for regular languages; v and or y will always be the important part for context free languages. </mark> 
- to make things less complicated we **start by using PL3**, |vxy| $\leq$ p , so by counting, |v| $\leq$ p and |y| $\leq$ p. 
- Now note that there are p b's in the middle of the string.
- By counting, neither v nor y can over-span the b's- they cannot reach both to the left of them and to the right of them at once. 
- so v and y can have at most 2 kinds of symbols each. they can each have a;b; c; a and b; or b and c; but they cannot have a b and c at same time! this is due to assuming chomsky normal form??
- now we can break this down into 3 cases:
	- v has two kinds of symbols. then v has the form of either $a^i\,b^k$ or $b^i\,c^k$ and it doesnt matter which, or what j and k are: vv, and therefore uvvxyyz has letters out of order
	- y has two kinds of symbols similar to v having two
	- v and y each have one kind of symbol. but there are three kinds of symbols so there is at least one that neither v nor y have. by counting, uvvxyyz doesn't have enough of that one. 
So for all possible constructions of v and y, uvvxyyz $\notin$ L. -><- and our assumption must be false. L is not context free. 