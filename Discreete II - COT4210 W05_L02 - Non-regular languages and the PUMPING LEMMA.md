example, is B regular?
	$B=\{0^n\:1^n\;|\;n\geq0\}$ 
no, this would require an unbounded number of states as n goes to infinity, it cannot be accepted by a DFA, but can be by other types. 

gerber's bird hotel...
10 pigeons in 9 cubbies, unknown is # of pigeons in each cubby. All is known is that at least one cubby has 2 pigeons. This is known as the ***pigeonhole*** principle.

**Pigeonholes and DFAs**
DFAs start in state 1 for input char 1, therefore in DFA with n states and string w with length m, then one state is repeated at least once. therefore this requires at least one cycle be present in the graph
![[Pasted image 20220322202743.png]]
therefore the cycle can be taken as many times as desired, and allows repitition as many times as desired. THIS LEADS TO THE *PUMPING LEMMA*. A LEMMA IS A THEOREM ONLY GOOD FOR PROVING OTHER THEOREMS. The pumping lemma is only useful for looking at a language and proving that it is not regular. This is proved by way of contradiction. BWOC!
![[Pasted image 20220322213654.png]]
pumping lemma cycle string *cannot be empty*. which violates the requirement that cycle must happen at least once. note y may be skipped in an implementation (example y*), however y itself cannot be empty.

***long string***: a string with length $\geq$ Q, number of states in the language's DFA
now consider a long string in a regular language:
	show that w conforms to the prefix cycle suffix pattern, _xyz_
### How to use the pumping lemma:
**1. assume lanugage is regular**
	1. observe by the pumping lemma, there is a p so that any string s in A of length p or greater, can be cut into *xyz* and **pumped**
		1. p length is arbitray and it value is not needed
**2. break the pump**
	1. find string s in it, of length p or greater, that can't be pumped
	2. demonstrate no matter how it is cut into *xyz*, it still cant be pumped
**3. clean up the mess**
	1. observe from step 2 that since s in A of length p or greater cant be pumped, and A is regular, we have a contradiction with the pumping lemma
	2. conclude that A is not regular!