Language processing vocab review:
- acceptance: whether a turing machine ends in accept state and reports it accepts a ***string***
- decidable: whether a turing machine can reliably compute both acceptance and rejection of a ***language***
- recognizeable is whether a turing machine can compute acceptance of a ***language***
![[Pasted image 20220409191515.png]]
![[Pasted image 20220409192215.png]]
then consider a new machine, the devils advocate, it takes H and runs it on the encoding of the origonal machine and  outputs the opposite result. that is, 
>
$D(<M>)\;accepts\; if\;H(<M,\;<M>>)$ rejects, and rejects if it accepts. 

So D asks 'is this machine in its own language'??? then it does opposite, accept if its not in its own language (rejects itself), rejects if it doesn't(accepts itself).

now we try running D on itself:
> D(< D >) accepts if D rejects, and D(< D >) rejects if D accepts

This is as basic a contradiction as you can get, therefore $A_{TM}$ is undecidable

We cannot answer this quesiton reliably: we cannot make a TM to simulate whethor or not a TM will accept a given string

NOTE: we can recognize the turing machine acceptance problem, but not the decidability problem, therefore we must not be able to  recognize the turing machine rejection problem

Therefore acceptance is recognizable, but not corecognizable, its complement is not recognizable. 

#### Reduction
You cant do a thing if doing it means you can do another thing that you cant do. ERGO if a theorem is true and results in a contradiction in another proven theorem, then it is false...

	anything that we could use to prove the turing acceptance 
	problem must itself be undecidable...

Formally,
![[Pasted image 20220409201540.png]]
in laymens, take a problem with known decidablility, and turn it into something useful to solve the decidability of the problem in question. 

This leads to the Halting problem for Turing Machines
![[Pasted image 20220409202141.png]]
Halting problem is unsolvable for turing machines, and therefore for all computer programs. 

what about the ***emptyness of turing machines***?
this is also undecidable
![[Pasted image 20220409213619.png]]
in our turing machine, we will build another turing machine.
![[Pasted image 20220409213656.png]]
To say another way, remember that the deginition of an algorithm is any set of clear unambiguous isntructions and finite set of instructions. Each of which does a finite amount of work. This is why properties of turing machines are undecidable by other turing machiens, because if a turing machine halts, there is no way to prove that a finite amount of work is being done. 