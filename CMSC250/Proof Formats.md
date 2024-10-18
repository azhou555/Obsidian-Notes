## Induction
Claim: For all $n\geq a$, $f(n)=g(n)$
Proof: I will induct on n. 
Base Case(n=a): $f(a)=g(a)$
Inductive Hypothesis: For some $k\geq a$, assume that $f(k)=g(k)$. 
Inductive Step: \[I must show $f(k+1)=g(k+1)$]
$f(k+1)=$
...
...
$g(k+1)$, 
as desired. ⬛
## Strong Induction
Claim: For all $n\geq a$, $f(n)=g(n)$
Proof: I will apply strong induction on $n$. 
Base Case($n=a,b,c\dots$): $f(a,b,c\dots)=g(a,b,c\dots)$
Inductive Hypothesis: For some $k\geq a$, assume that for all $a\leq i\leq k$, $f(i)=g(i)$. 
Inductive Step: \[I must show $f(k+1)=g(k+1)$]
$f(k+1)=$
...
...
$g(k+1)$, 
as desired. ⬛
## Universal Generalization
Claim: For all $n\in\mathbb{N}$, statement about $n$. 
Proof: Let $x\in\mathbb{N}$, selected arbitrarily. 
Prove that statement about $x$. 
Since $x$ was chosen arbitrarily, the proposition holds for all $n\in\mathbb{N}$. 
⬛
## Proving one to one(injective)
Claim: For some function $f(n)$ over $\mathbb{D}_{1}\to\mathbb{D}_{2}$, $f(n)$ is injective. 
Proof: Let $a, b\in\mathbb{D}_{1}$ such that $f(a)=f(b)$. \[I must show that $a=b$]
$f(a)=f(b)$
...
...
$a=b$, as desired. ⬛
## Proving onto(subjective)
Claim: For some function $f(n)$ over  $\mathbb{D}_{1}\to\mathbb{D}_{2}$, $f(n)$ is onto.
Proof: Let $y\in\mathbb{D}_{2}$, selected arbitrarily. \[I must show there exists $x\in\mathbb{D}_{1}$ such that $f(x)=y$]
Let $x=g(y)$. \[I must show $f(x)=y$]. 
$f(x)=$
...
...
$=y$, as desired. ⬛
## Proof by contradiction
Claim: Statement $p$ 
Proof: Suppose (BWOC) that $\neg p$
...
...
Some contradiction ☠. 
⬛
## Proof of implication
Claim: $p\to q$
Proof: Assume $p$. \[I must show $q$]
$p$
...
...
$q$, as desired. ⬛
Countability:
Anything of size $\aleph_{o}$ is countably infinite. This includes things like $\mathbb{N}$ and $\mathbb{Z}$, but not $\mathbb{R}$ which is of size $2^{\aleph_{o}}$. Generally we view $\mathbb{R}$ as the first uncountably infinite set. Continuum Hypothesis, but don't worry too much about it. 

# Binary Relations
## Equivalence
1. Reflexive
2. Symmetric
3. Transitive
## Partial
1. Reflexive
2. Antisymmetric
3. Transitive
## Total
1. Total
2. Antisymmetric
3. Transitive
## Well Ordering?
Any set such that for any subset of the set, there exists a $x$ in the set and every other element in the subset is greater than or equal to it. For example, the natural numbers. 