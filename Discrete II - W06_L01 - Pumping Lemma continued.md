**consider the language** $L = \{s|s=\:0^n1^n\: for\:n \in \mathbb{N} \}$, htat is lang comprised of strings that some num of zeroews followed by same num of 1s. **Show that L is not a regular language.** 


assume BWOC🐔 that L is a regular language. then we can find string xyz, and it has a pumping length p. 

now consider string s = $0^p1^p$ , clearly |s| > p-s is longer than pumping length, and equally clearly pumping lemma must apply to s. 

Therefore s = xyz with x cycling prefix, y the cycling string and z the suffix 


>PL1: x$y^i$ z $\in$ L for all i $\in \mathbb{N}$ pumping cycle
PL2: |y| > 0  cant be degenerate
PL3: |xy| $\leq$ p  cycle has to finish early

note: $|y^i|\: =\: |y| * i$
y must be a substring of s, therefore it can only be three possibilities:
1. *y composed entirely of zeroes, then xyyz only adds zeroes, then xyyz has more 0s than 1s*
	- s is not in the language by definition of the language
2. *y composed entirely of ones, then xyyz has more 1s than 0s*
	- s is not in the language by definition of the language
3. *y composed entirely of zeroes followed by ones*
	- xyyz would not be inside the language as there would be mixed zeroes and ones, which is not allowed.
$\therefore$ in all possible cases, xyz $\notin$ the language, set i = 2 and therefor --><-- (contradiction) with PL1. 

BWWWWOOOOCCCCC! THE CHICKEN LIED! CONTRADICITONNNNNNN
🔪-->🐔-->🍗-->🍷

---
let $L \subset\:\{0,1\}^* \: where \:L = \{s|s\:has\:as\:equal\:number\:of\:0's\:and\:1's\}$, **show that L is not regular.** 
assume by way of contradiction that L is regular. then by the pumping lemma, it has pumping length p. 
>PL1: x$y^i$ z $\in$ L for all i $\in \mathbb{N}$ pumping cycle
PL2: |y| > 0  cant be degenerate
PL3: |xy| $\leq$ p  cycle has to finish early

By PL3, |xy| $\leq$ p, so by our definiton, s starts with p zeroes. so y is composed entirely of zeroes. so y is composed entirely of zeroes (and by PL2 must have at least some zeroes)
- xyyz has more zeroes than xyz
- by the definiton of L, if xyz $\in$ L, xyz has equal zeroes and ones
- so xyyz has more zeroes than ones
set i = 2 and x$y^i$z $\notin$ L, --><-- PL1. Our assumption must be false, L is *not* regular
NOTE: *if a language is regular, ANY long string can be pumped.*
**NOTE: PUMPING LEMMA IS A *STRONG ASSERTION* MEANING IF THERE IS ANY STRING WHICH CAN BE PROVEN TO BE NOT REGULAR, ITS LANGUAGE IS SHOWN TO NOT BE REGULAR** 

---

**consider the language** $L = \{s|s=\:0^i1^j\: with\:i>j;i,j \in \mathbb{N} \}$, that is, language comprised of strings that a number i of zeroes are followed by a fewer number of 1s, j. **Show that L is not a regular language.** 

consider the string s = $0^p1^{p-1}$ ,  clearly |s| > p-s is longer than pumping length, and equally clearly pumping lemma must apply to s. 
>PL1: x$y^i$ z $\in$ L for all i $\in \mathbb{N}$ pumping cycle
PL2: |y| > 0  cant be degenerate
PL3: |xy| $\leq$ p  cycle has to finish early

By PL3, |xy| $\leq$ p, so by our definiton, s starts with p zeroes. so y is composed entirely of zeroes (and by PL2 must have at least some zeroes)
- xyz has exactly one more zero than it has ones, by choice of s
- y has at least one zero (and nothing else) by PL2
- xz has fewer zeroes than xyz
- then xz has at most as many zeroes as it does 1s by counting.
-  by the definition of L , xz $\notin$ L
Set i = 0 and x$y^i$z $\notin$ L, --><-- PL1. Our asumption must be false; L is not regular
---

thus we have given three key examples, pumping up, pumpijng up w/ restricted xy, and pumpiing down(examples in order???)