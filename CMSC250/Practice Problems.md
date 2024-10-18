#### Sum of first n odd numbers
Claim: 
   Sum of the first n odd numbers: Prove that the sum of the first $n$ odd numbers is equal to $n^2$.
Proof: 
	I will induct on n. 
	 Base Case(n = 1): $1 = 1^2$ ☑
	 Inductive Hypothesis: Assume that for some $\displaystyle k \geq 1, \sum_{i=1}^{k}2(i-1)+1 = k^2$ .
	 Inductive Step: $[\text{I must show} \displaystyle \sum_{i=1}^{k+1}2(i-1)+1 = (k+1)^2]$
	 $\displaystyle \sum_{i=1}^{k+1}2(i-1)+1 = \sum_{i-1}^{k}2(i-1)+1+2k+1=$[By I.H.]
	 $\displaystyle k^2+2k+1=$
	 $\displaystyle (k+1)^2$, as desired. 