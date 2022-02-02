linearizable if at least one possible outcome of concurrent operations could be considered as correct behavior 
![[Pasted image 20220201185819.png]]
a is thread, q is object, void is responce 
a history is a list of operations and responces

if no responce is recorded its status should be considered pending, OR append the correct responce at the end of the history. either consider it incomplete OR complete and alter history record to reflect

in a history with a single thread, it is not possible for operations to happen out of order. this is the coinsideration in well formed vs not well formed histories

