# 9. Quadratic Residues and the Quadratic Reciprocity Law

## 9.1 Quadratic residues

As shown in Chapter 5, the problem of solving a polynomial congruence

$$
f(x) \equiv 0 \pmod{n}
$$

can be reduced to polynomial congruences with prime moduli plus a set of
linear congruences. This chapter is concerned with quadratic congruences
of the form

$$
x^2 \equiv n \pmod{p} \qquad(1)
$$

where $p$ is an odd prime and $n \not\equiv 0 \pmod{p}$. Since the modulus is prime we know that (1) has at most two 
solutions. Moreover, if $x$ is a solution so is $-x$, hence the number of solutions is either $0$ or $2$.

**Definition** If congruence (1) has a solution we say that $n$ is a quadratic residue mod $p$ and we write $nRp$. 
If (1) has no solution we say that $n$ is a quadratic nonresidue mod $p$ and we write $n\bar{R}p$.

Two basic problems dominate the theory of quadratic residues:

1. Given a prime $p$, determine which $n$ are quadratic residues mod $p$ and which are quadratic nonresidues mod $p$.
2. Given $n$, determine those primes $p$ for which $n$ is a quadratic residue mod $p$ and those for which $n$ is a 
   quadratic nonresidue mod $p$.

We begin with some methods for solving problem 1.

EXAMPLE To find the quadratic residues modulo $11$ we square the numbers $1, 2, \ldots , 10$ and reduce mod $11$. We 
obtain 

$$
1^2 \equiv 1, 2^2 \equiv 4, 3^2 \equiv 9, 4^2 \equiv 5, 5^2 \equiv 3 \pmod{11}
$$

It suffices to square only the first half of the numbers since

$$
6^2 \equiv (-5)^2 \equiv 3, 7^2 \equiv (-4)^2 \equiv 5, \ldots, 10^2 \equiv (-1)^2 \equiv 1 \pmod{11}
$$

Consequently, the quadratic residues mod $11$ are $1, 3, 4, 5, 9$, and the nonresidues are $2, 6, 7, 8, 10$.

This example illustrates the following theorem.

**Theorem 9.1** Let $p$ be an odd prime. Then every reduced residue system mod $p$ contains exactly $(p-1)/2$ quadratic 
residues and exactly $(p-1)/2$ quadratic nonresidues mod $p$. The quadratic residues belong to the residue classes 
containing the numbers

$$
1^2, 2^2, 3^2, \ldots, \left(\frac{p-1}{2}\right)^2 \qquad (2)
$$

PROOF. First we note that the numbers in (2) are distinct mod $p$. In fact, if $x^2 \equiv y^2 \pmod{p}$ with 
$1 \le x \le (p-1)/2$ and $1 \le y \le (p-1)/2$, then

$$
(x-y)(x+y) \equiv 0 \pmod{p}
$$

But $1 \lt x+y \lt p$ so $x-y \equiv 0 \pmod{p}$, hence $x=y$. Since 

$$
(p-k)^2 \equiv k^2 \pmod{p}
$$

every quadratic residue is congruent mod $p$ to exactly one of the numbers in (2). This completes the proof. $\square$

The following brief table of quadratic residues $R$ and nonresidues $\bar{R}$ was obtained with the help of Theorem 9.1. 

|           | $p=3$ | $p=5$ | $p=7$   | $p=11$       | $p=13$          |
| :-------- | :---- | :---- | :------ | :----------- | :-------------- |
| $R$       | $1$   | $1,4$ | $1,2,4$ | $1,3,4,5,9$  | $1,3,4,9,10,12$ |
| $\bar{R}$ | $2$   | $2,3$ | $3,5,6$ | $2,6,7,8,10$ | $2,5,6,7,8,11$  |

## 9.2 Legendre's symbol and its properties

**Definition** Let $p$ be an odd prime. If $n \not\equiv 0 \pmod{p}$ we define Legendre's symbol $(n|p)$ as follows:

$$
(n|p) = \begin{cases}
        +1 & \text{ if } nRp \\
        -1 & \text{ if } n\bar{R}p
        \end{cases}
$$

If $n \equiv 0 \pmod{p}$ we define $(n|p)=0$.

EXAMPLES. $(1|p)=1$, $(m^2|p)=1$, $(7|11)=-1$, $(22|11)=0$.

*Note.* Some authors write $\left(\frac{n}{p}\right)$ instead of $(n|p)$.

It is clear that $(m|p)=(n|p)$ whenever $m \equiv n \pmod{p}$, so $(n|p)$ is a periodic function of $n$ with period $p$.

The little Fermat theorem tells us that $n^{p-1} \equiv 1 \pmod{p}$ if $p \nmid n$. Since

$$
n^{p-1}-1 = (n^{(p-1)/2} - 1)(n^{(p-1)/2} + 1)
$$

it follows that $n^{(p-1)/2} \equiv \pm 1 \pmod{p}$. The next theorem tells us that we get $+1$ if $nRp$ and $-1$ if 
$n\bar{R}p$.

**Theorem 9.2** Euler's criterion. Let $p$ be an odd prime. Then for all $n$ we have

$$
(n|p) \equiv n^{(p-1)/2} \pmod{p}
$$

PROOF. If $n \equiv 0 \pmod{p}$ the result it trivial since both members are congruent to $0$ mod $p$. Now suppose 
$(n|p)=1$. Then there is an $x$  such that $x^2 \equiv n \pmod{p}$ and hence

$$
n^{(p-1)/2} \equiv (x^2)^{(p-1)/2} = x^{p-1} \equiv 1 = (n|p) \pmod{p}
$$

This proves the theorem if $(n|p)=1$.

Now suppose that $(n|p)=-1$ and consider the polynomial 

$$
f(x) = x^{(p-1)/2} - 1
$$

Since $f(x)$ has degree $(p-1)/2$ the congruence 

$$
f(x) \equiv 0 \pmod{p}
$$

has at most $(p-1)/2$ solutions. But the $(p-1)/2$ quadratic residues mod $p$ are solutions so the nonresidues are not. 
Hence

$$
n^{(p-1)/2} \not\equiv 1 \pmod{p} \text{ if } (n|p)=-1
$$

But $n^{(p-1)/2} \equiv \pm 1 \pmod{p}$ so $n^{(p-1)/2} \equiv -1 \equiv (n|p) \pmod{p}$. This completes the proof. 
$\square$

**Theorem 9.3** Legendre's symbol $(n|p)$ is a completely multiplicative function of $n$.

PROOF. If $p|m$ or $p|n$ then $p|mn$ so $(mn|p)=0$ and either $(m|p)=0$ or $(n|p)=0$. Therefore $(mn|p)=(m|p)(n|p)$ if 
$p|m$ or $p|n$.

If $p \nmid m$ and $p \nmid n$ then $p \nmid mn$ and we have

$$
(mn|p) \equiv (mn)^{(p-1)/2} = m^{(p-1)/2} n^{(p-1)/2} \equiv (m|p)(n|p) \pmod{p}
$$

But each of $(mn|p)$, $(m|p)$ and $(n|p)$ is $1$ or $-1$ so the difference 

$$
(mn|p) - (m|p)(n|p)
$$

is either $0$, $2$ or $-2$. Since this difference is divisible by $p$ it must be $0$.

*Note.* Since $(n|p)$ is a completely multiplicative function of $n$ which is periodic with period $p$ and vanishes 
when $p|n$, it follows that $(n|p)=\chi(n)$, where $\chi$ is one of the Dirichlet characters modulo $p$. The Legendre 
symbol is called the *quadratic character* mod $p$. 

## 9.3 Evaluation of $(-1|p)$ and $(2|p)$

**Theorem 9.4** For every odd prime $p$ we have

$$
(-1|p) = (-1)^{(p-1)/2} = \begin{cases}
                          1  & \text { if } p \equiv 1 \pmod{4} \\
                          -1 & \text { if } p \equiv 3 \pmod{4}
                          \end{cases}
$$

PROOF. By Euler's criterion we have $(-1|p) \equiv (-1)^{(p-1)/2} \pmod{p}$. Since each member of this congruence is 
$1$ or $-1$ the two members are equal. $\square$

**Theorem 9.5** For every odd prime $p$ we have 

$$
(2|p) = (-1)^{(p^2-1)/8} = \begin{cases}
                           1  & \text{ if } p \equiv \pm 1 \pmod{8} \\
                           -1 & \text{ if } p \equiv \pm 3 \pmod{8}
                           \end{cases}
$$

PROOF. Consider the following $(p-1)/2$ congruences:

$$
\begin{align*}
p-1 & \equiv 1(-1)^1 \pmod{p} \\
  2 & \equiv 2(-1)^2 \pmod{p} \\
p-3 & \equiv 3(-1)^3 \pmod{p} \\
  4 & \equiv 4(-1)^4 \pmod{p} \\
    & \vdots                  \\
  r & \equiv \frac{p-1}{2}(-1)^{(p-1)/2} \pmod{p}
\end{align*}
$$

where $r$ is either $p-(p-1)/2$ or $(p-1)/2$. Multiply these together and note that each integer on the left is even. 
We obtain

$$
2 \cdot 4 \cdot 6 \cdots (p-1) \equiv \left(\frac{p-1}{2}\right)! (-1)^{1+2+\cdots+(p-1)/2} \pmod{p}
$$

This gives us 

$$
2^{(p-1)/2} \left(\frac{p-1}{2}\right)! \equiv \left(\frac{p-1}{2}\right)! (-1)^{(p^2-1)/8} \pmod{p}
$$

Since $((p-1)/2)! \not\equiv 0 \pmod{p}$ this implies

$$
2^{(p-1)/2} \equiv (-1)^{(p^2-1)/8} \pmod{p}
$$

By Euler's criterion we have $2^{(p-1)/2} \equiv (2|p) \pmod{p}$ and since each member is $1$ or $-1$ the two members 
are equal. This completes the proof. $\square$

## 9.4 Gauss' lemma

Although Euler's criterion gives a straightforward method for computing $(n|p)$, the calculation may become prohibitive 
for large $n$ since it requires raising $n$ to the power $(p-1)/2$. Gauss found another criterion which involves a 
simpler calculation.

**Theorem 9.6** Gauss' lemma. Assume $n \not\equiv 0 \pmod{p}$ and consider the least positive residues mod $p$ of the 
following $(p-1)/2$ multiples of $n$:

$$
n,2n,3n,\ldots,\frac{p-1}{2}n \qquad(3)
$$

If $m$ denotes the number of these residues which exceed $p/2$, then

$$
(n|p) = (-1)^m
$$

PROOF. The numbers in (3) are incongruent mod $p$. We consider their least positive residues and distribute them into 
two disjoint sets $A$ and $B$, according as the residues are $\lt p/2$ or $\gt p/2$. Thus

$$
A = \{ a_1, a_2, \ldots, a_k \}
$$

where each $a_i \equiv tn \pmod{p}$ for some $t \le (p-1)/2$ and $0 \lt a_i \lt p/2$; and 

$$
B = \{ b_1, b_2, \ldots, b_m \}
$$

where each $b_i \equiv sn \pmod{p}$ for some $s \le (p-1)/2$ and $p/2 \lt b_i \lt p$. Note that $m+k = (p-1)/2$ since 
$A$ and $B$ are disjoint. The number $m$ of elements in $B$ is pertinent in this theorem. Form a new set $C$ of $m$ 
elements by subtracting each $b_i$ from $p$. Thus

$$
C = \{ c_1, c_2, \ldots, c_m \} \text{ where } c_i = p - b_i
$$

Now $0 \lt c_i \lt p/2$ so the elements of $C$ lie in the same interval as the elements of $A$. We show next that the 
sets $A$ and $C$ are disjoint. 

Assume that $c_i=a_j$ for some pair $i$ and $j$. Then $p-b_i=a_j$, or $a_j+b_i \equiv 0 \pmod{p}$. Therefore 

$$
tn + sn = (t + s)n \equiv 0 \pmod{p}
$$

for some $s$ and $t$ with $1 \le t \lt p/2$, $1 \le s \lt p/2$. But this is impossible since $p \nmid n$ and 
$0 \lt s + t \lt p$. Therefore $A$ and $C$ are disjoint, so their union $A \cup C$ contains $m+k=(p-1)/2$ integers in 
the interval $[1,(p-1)/2]$. Hence

$$
A \cup C = \{ a_1, a2, \ldots a_k, c_1, c_2, \ldots, c_m \} = \left\{ 1, 2, \ldots, \frac{p-1}{2} \right\}
$$

Now form the product of all the elements in $A \cup C$ to obtain

$$
a_1 a_2 \cdots a_k c_1 c_2 \cdots c_m = \left( \frac{p-1}{2} \right)!
$$

Since $c_i=p-b_i$ this gives us

$$
\begin{align*}
\left( \frac{p-1}{2} \right)! &= a_1 a_2 \cdots a_k (p-b_1) (p-b_2) \cdots (p-c_m) \\
                              &\equiv (-1)^m a_1 a_2 \cdots c_k b_1 b_2 \cdots b_m \pmod{p} \\
                              &\equiv (-1)^m n(2n)(3n) \cdots \left( \frac{p-1}{2}n \right) \pmod{p} \\
                              &\equiv (-1)^m n^{(p-1)/2} \left( \frac{p-1}{2} \right)! \pmod{p} \\
\end{align*}
$$

Cancelling the factorial we obtain

$$
n^{(p-1)/2} \equiv (-1)^m \pmod{p}
$$

Euler's criterion shows that $(-1)^m \equiv (n|p) \pmod{p}$ hence $(-1)^m=(n|p)$ and the proof of Gauss' lemma is 
complete. $\square$

To use Gauss' lemma in practice we need not know the exact value of $m$, but only its parity, that is, whether $m$ is 
odd or even. The next theorem gives a relatively simple way to determine the parity of $m$. 

**Theorem 9.7** Let $m$ be the number defined in Gauss' lemma. Then

$$
m \equiv \sum_{t=1}^{(p-1)/2} \left[ \frac{tn}{p} \right] + (n-1) \frac{p^2-1}{8} \pmod{2}
$$

In particular, if $n$ is odd we have 

$$
m \equiv \sum_{t=1}^{(p-1)/2} \left[ \frac{tn}{p} \right] \pmod{2}
$$

PROOF. Recall that $m$ is the number of least positive residues of the numbers

$$
n, 2n, 3n \ldots, \frac{p-1}{2}n
$$

which exceed $p/2$. Take a typical number, say $tn$, divide it by $p$ and examine the size of the remainder. We have 

$$
\frac{tn}{p} = \left[ \frac{tn}{p} \right] + \left\{ \frac{tn}{p} \right\}, \text{ where } 0 \lt \left\{ \frac{tn}{p} \right\} \lt 1
$$

so

$$
tn = p \left[ \frac{tn}{p} \right] + p \left\{ \frac{tn}{p} \right\} = p \left[ \frac{tn}{p} \right] + r_t
$$

say, where $0 \lt r_i \lt p$. The number $r_t = tn -p[tn/p]$ is the least positive residue of $tn$ modulo $p$. 
Referring again to the sets $A$ and $B$ used in the proof of Gauss' lemma we have

$$
\{ r_1, r_2, \ldots, r_{(p-1)/2} \} = \{ a_1, a_2, \ldots, a_k, b_1, \ldots, b_m \}
$$

Recall also that 

$$
\left\{ 1, 2, \dots, \frac{p-1}{2} \right\} =  \{ a_1, a_2, \ldots, a_k, c_1, \ldots, c_m\}
$$

where each $c_i=p-b_i$. Now we compute the sums of the elements in these sets to obtain the two equations

$$
\sum_{t=1}^{(p-1)/2} r_t = \sum_{i=1}^k a_i + \sum_{j=1}^m b_j
$$

and 

$$
\sum_{t=1}^{(p-1)/2} t = \sum_{i=1}^k a_i + \sum_{j=1}^m c_j = \sum_{i=1}^k a_i + mp - \sum_{j=1}^m b_j
$$

In the first equation we replace $r_t$ by its definition to obtain

$$
\sum_{i=1}^k a_i + \sum_{j=1}^m b_j = n \sum_{t=1}^{(p-1)/2} t - p \sum_{t=1}^{(p-1)/2} \left[ \frac{tn}{p} \right]
$$

The second equation is 

$$
mp + \sum_{i=1}^k a_i - \sum_{j=1}^m b_j = \sum_{t=1}^{(p-1)/2} t
$$

Adding this to the previous equation we get 

$$
\begin{align*}
mp + 2 \sum_{i=1}^k a_i &= (n+1) \sum_{t=1}^{(p-1)/2} t - p \sum_{t=1}^{(p-1)/2} \left[ \frac{tn}{p} \right] \\
                        &= (n+1)\frac{p^2-1}{8} - p \sum_{t=1}^{(p-1)/2} \left[ \frac{tn}{p} \right]
\end{align*}
$$

Now we reduce this modulo $2$, noting that $n+1 \equiv n-1 \pmod{2}$ and $p \equiv 1 \pmod{2}$, and we obtain 

$$
m \equiv (n-1)\frac{p^2-1}{8} + \sum_{t=1}^{(p-1)/2} \left[ \frac{tn}{p} \right] \pmod{2}
$$

which completes the proof. $\square$

## 9.5 The quadratic reciprocity law

Both Euler's criterion and Gauss' lemma give straightforward though sometimes lengthy procedures for solving the first 
basic problem of the theory of quadratic residues. The second problem is much more difficult. Its solution depends on a 
remarkable theorem known as the quadratic reciprocity law, first stated in a complicated form by Euler in the period 
1744-1746, and rediscovered in 1785 by Legendre who gave a partial proof. Gauss discovered the reciprocity law 
independently at the age of eighteen and a year later in 1796 gave the first complete proof. 

The quadratic reciprocity law states that if $p$ and $q$ are distinct odd primes, then $(p|q)=(q|p)$ unless 
$p \equiv q \equiv 3 \pmod{4}$, in which case $(p|q)=-(q|p)$. The theorem is usually stated in the following symmetric 
form given by Legendre. 

**Theorem 9.8** Quadratic reciprocity law. If $p$ and $q$ are distinct odd primes, then

$$
(p|q)(q|p) = (-1)^{(p-1)(q-1)/4} \qquad(4)
$$

PROOF. By Gauss' lemma and Theorem 9.7 we have

$$
(q|p) = (-1)^m
$$

where 

$$
m = \sum_{t=1}^{(p-1)/2} \left[ \frac{tq}{p} \right] \pmod{2}
$$

Similarly, 

$$
(p|q) = (-1)^n
$$

where
$$
n = \sum_{s=1}^{(q-1)/2} \left[ \frac{sp}{q} \right] \pmod{2}
$$

Hence $(p|q)(q|p)=(-1)^{m+n}$, and (4) follows at once from the identity

$$
\sum_{t=1}^{(p-1)/2} \left[ \frac{tq}{p} \right] + \sum_{s=1}^{(q-1)/2} \left[ \frac{sp}{q} \right] = \frac{p-1}{2} \frac{q-1}{2} \qquad(5)
$$

To prove (5) consider the function

$$
f(x,y) = qx - py \quad \text{ for } |x| \lt p/2 \text{ and } |y| \lt q/2
$$

If $x$ and $y$ are nonzero integers then $f(x,y)$ is a nonzero integer. Moreover, as $x$ takes the values 
$1, 2, \ldots, (p-1)/2$ and $y$ takes the values $1, 2, \ldots, (q-1)/2$ then $f(x,y)$ takes

$$
\frac{p-1}{2} \frac{q-1}{2}
$$

values, no two of which are equal since

$$
f(x,y)- f(x',y') = f(x - x',y - y') \ne 0
$$

Now we count the number of values of $f(x,y)$ which are positive and the number which are negative.

For each fixed $x$ we have $f(x,y) \gt 0$ if and only if $y \lt qx/p$, or $y \le [qx/p]$. Hence the total number of 
positive values is

$$
\sum_{x=1}^{(p-1)/2} \left[ \frac{qx}{p} \right]
$$

Similarly, the number of negative values is

$$
\sum_{y=1}^{(q-1)/2} \left[ \frac{py}{q} \right]
$$

Since the number of positive and negative values together is

$$
\frac{p-1}{2} \frac{q-1}{2}
$$

this proves (5) and hence (4). $\square$

*Note*. The reader may find it instructive to interpret the foregoing proof of (5) geometrically, using lattice points 
in the plane.

At least 150 proofs of the quadratic reciprocity law have been published. Gauss himself supplied no less than eight, 
including a version of the one just given. A short proof of the quadratic reciprocity law is described in an article 
by M. Gerstenhaber [25]. 

## 9.9 Gauss sums and the quadratic reciprocity law

This section gives another proof of the quadratic reciprocity law with the help of the Gauss sums

$$
G(n,\chi) = \sum_{r \text{ mod } k} \chi(r) e^{2 \pi i nr/p} \qquad(16)
$$

where $\chi(r)=(r|p)$ is the quadratic character mod $p$. Since the modulus is prime, $\chi$ is a primitive character 
and we have the separability property

$$
G(n,\chi) = (n|p) G(1,\chi) \qquad(17)
$$

for every $n$. Also, Theorem 8.11 implies that $\left| G(1,\chi) \right|^2 = p$. The next theorem shows that 
$G(1,\chi)^2 = \pm p.$

**Theorem 9.13** If $p$ is an odd prime and $\chi(r)=(r|p)$ we have 

$$
G(1,\chi)^2 = (-1|p) p \qquad(18)
$$

PROOF. We have

$$
G(1,\chi)^2 = \sum_{r=1}^{p-1} \sum_{s=1}^{p-1} (r|p) (s|p) e^{2 \pi i(r+s)/p}
$$

For each pair $r,s$ there is a unique $t$ mod $p$ such that $s \equiv tr \pmod{p}$, and 
$(r|p)(s|p) = (r|p)(tr|p) = (r^2|p)(t|p) = (t|p)$. Hence

$$
G(1,\chi)^2 = \sum_{t=1}^{p-1} \sum_{r=1}^{p-1} (t|p) e^{2 \pi ir(1+t)/p} 
            = \sum_{t=1}^{p-1} (t|p) \sum_{r=1}^{p-1} e^{2 \pi ir(1+t)/p} 
$$

The last sum on $r$ is a geometric sum given by

$$
\sum_{r=1}^{p-1} e^{2 \pi ir(1+t)/p} = \begin{cases}
                                        -1 & \text{ if } p \nmid (1+t) \\
                                       p-1 & \text{ if } p | (1+t)
                                       \end{cases}
$$

Therefore

$$
\begin{align*}
G(1,\chi)^2 &= -\sum_{t=1}^{p-2} (t|p) + (p-1)(p-1|p)
             = -\sum_{t=1}^{p-1} (t|p) + p(-1|p)       \\
            &= (-1|p) p
\end{align*}
$$

since $\sum_{t=1}^{p-1} (t|p) = 0$. This proves (18). $\square$

Equation (18) shows that $G(1,\chi)^2$ is an integer, so $G(1,\chi)^{q-1}$ is also an integer for every odd $q$. The 
next theorem shows that the quadratic reciprocity law is connected to the value of this integer modulo $q$.

**Theorem 9.14** Let $p$ and $q$ be distinct odd primes and let $\chi$ be the quadratic character mod $p$. Then the 
quadratic reciprocity law

$$
(q|p) = (-1)^{(p-1)(q-1)/4} (p|q) \qquad(19)
$$

is equivalent to the congruence

$$
G(1,\chi)^{q-1} \equiv (q|p) \pmod{q} \qquad(20)
$$

PROOF. From (18) we have

$$
G(1,\chi)^{q-1} = (-1|p)^{(q-1)/2} p^{(q-1)/2} = (-1)^{(p-1)(q-1)/4} p^{(q-1)/2} \qquad(21)
$$

By Euler's criterion we have $p^{(q-1)/2} \equiv (p|q) \pmod{q}$ so (21) implies

$$
G(1,\chi)^{q-1} \equiv (-1)^{(p-1)(q-1)/4} (p|q) \pmod{q} \qquad(22)
$$

If (20) holds we obtain

$$
(q|p) \equiv (-1)^{(p-1)(q-1)/4} (p|q) \pmod{q}
$$

which implies (19) since both members are $\pm 1$. Conversely, if (19) holds then (22) implies (20).

The next theorem gives an identity which we will use to deduce (20).

**Theorem 9.15** If $p$ and $q$ are distinct odd primes and if $\chi$ is the quadratic character mod $p$ we have

$$
G(1,\chi)^{q-1} = (q|p) \sum_{\substack{r_1 \text{ mod } p \\ r_1 + \cdots + r_q \equiv q \pmod{p} }} \cdots \sum_{\substack{r_q \text{ mod } p \\ r_1 + \cdots + r_q \equiv q \pmod{p} }} (r_1 \cdots r_q|p) \qquad(23)
$$

PROOF. The Gauss sum $G(n,\chi)$ is a periodic function of $n$ with period $p$. The same is true of $G(n,\chi)^q$ so we 
have a finite Fourier expansion

$$
G(n,\chi)^q = \sum_{m \text{ mod } p} a_q(m) e^{2 \pi i  mn/p}
$$

where the coefficients are given by

$$
a_q(m) = \frac{1}{p} \sum_{n \text{ mod }p} G(n,\chi) e^{-2 \pi i mn/p} \qquad(24)
$$

From the definition of $G(n,\chi)$ we have

$$
\begin{align*}
G(n,\chi)^q &= \sum_{r_1 \text{ mod } p} (r_1|p) e^{2 \pi i nr_1/p} \cdots \sum_{r_q \text{ mod } p} (r_q|p) e^{2 \pi i nr_q/p} \\
            &= \sum_{r_1 \text{ mod } p} \cdots \sum_{r_q \text{ mod } p} (r_1 \cdots r_q|p) e^{2 \pi i n(r_1 + \cdots + r_q)/p}
\end{align*}
$$

so (24) becomes

$$
a_q(m) = \frac{1}{p} \sum_{r_1 \text{ mod } p} \cdots \sum_{r_q \text{ mod } p} (r_1 \cdots r_q|p) \sum_{n \text{ mod }p} e^{2 \pi i n(r_1 + \cdots + r_q - m)/p}
$$

The sum on $n$ is a geometric sum which vanishes unless $r_1+\cdots+r_q \equiv m \pmod{p}$, in which case the sum is 
equal to $p$. Hence

$$
a_q(m) = \sum_{\substack{r_1 \text{ mod } p \\ r_1 + \cdots + r_q \equiv q \pmod{p} }} \cdots \sum_{\substack{r_q \text{ mod } p \\ r_1 + \cdots + r_q \equiv q \pmod{p} }} (r_1 \cdots r_q|p) \qquad(25)
$$

Now we return to (24) and obtain an alternate expression for $a_q(m)$. Using the separability of $G(n,\chi)$ and the 
relation $(n|p)^q=(n|p)$ for odd $q$ we find

$$
\begin{align*}
a_q(m) &= \frac{1}{p} G(1,\chi)^q \sum_{n \text{ mod } p} (n|p) e^{-2 \pi i mn/p} = \frac{1}{p} G(1,\chi)^q G(-m,\chi) \\
       &= \frac{1}{p} G(1,\chi)^q (m|p) G(-1,\chi) = (m|p) G(1, \chi)^{q-1}
\end{align*}
$$

since

$$
G(1,\chi) G(-1,\chi) = G(1,\chi)\overline{G(1,\chi)} = \left| G(1,\chi) \right|^2 = p
$$

In other words, $G(1,\chi)^{q-1} = (m|p) a_q(m)$. Taking $m=q$ and using (25) we obtain (23). $\square$

PROOF OF THE RECIPROCITY LAW. To deduce the quadratic reciprocity law from (23) it suffices to show that

$$
\sum_{r_1 \text{ mod } p} \cdots \sum_{r_q \text{ mod } p} (r_1 \cdots r_q|p) \equiv 1 \pmod{q} \qquad(26)
$$

where the summation indices $r_1, \ldots, r_q$ are subject to the restriction 

$$
r_1 + \cdots + r_q \equiv q \pmod{p} \qquad(27)
$$

If all the indices $r_1, \ldots, r_q$ are congruent to each other mod $p$, then their sum is congruent to $qr_j$ for 
each $j=1,2,\ldots,q$, so (27) holds if, and only if, 

$$
q r_j \equiv q \pmod{p}
$$

that is, if, and only if $r_j \equiv 1 \pmod{p}$ for each $j$. In this case the corresponding summand in (26) is 
$(1|p)=1$. For all other choices of indices satisfying (27) there must be at least two incongruent indices among 
$r_1,\ldots,r_q$. Therefore every cyclic permutation of $r_1,\ldots,r_q$ gives a new solution of (27) which 
contributes the same summand, $(r_1 \cdots r_q|p)$. Therefore each such summand appears $q$ times and contributes $0$ 
modulo $q$ to the sum. Hence the only contribution to the sum in (26) which is nonzero modulo $q$ is $(1|p)=1$. This 
completes the proof. $\square$

## 9.10 The reciprocity law for quadratic Gauss sums

This section describes another proof of the quadratic reciprocity law based on the quadratic Gauss sums

$$
G(n;m) = \sum_{r=1}^m e^{2 \pi i nr^2/m} \qquad(28)
$$

If $p$ is an odd prime and $p \nmid n$ we have the formula

$$
G(n;m) = (n|p) G(1;p) \qquad(29)
$$

which reduces the study of the sums $G(n;m)$ to the case $n=1$. Equation (29) follows easily from (28) or by noting 
that $G(n;p)=G(n,\chi)$, where $\chi(n)=(n|p)$, and observing that $G(n,\chi)$ is separable.

Although each term of the sum $G(1;p)$ has absolute value $1$, the sum itself has absolute value 
$0, \sqrt{p} \text{ or } \sqrt{2p}$. In fact, Gauss proved the remarkable formula

$$
(30) \quad G(1;m) = \frac{1}{2} \sqrt{m} (1+i)(1 + e^{-\pi im/2}) = 
     \begin{cases}
         \sqrt{m}      & \text{ if } m \equiv 1 \pmod{4} \\
         0             & \text{ if } m \equiv 2 \pmod{4} \\
         i\sqrt{m}     & \text{ if } m \equiv 3 \pmod{4} \\
         (1+i)\sqrt{m} & \text{ if } m \equiv 0 \pmod{4} \\
     \end{cases}                   
$$

for every $m \ge 1$. A number of different proofs of (30) are known. We will deduce (30) by treating a related sum

$$
S(a,m) = \sum_{r=0}^{m-1} e^{\pi iar^2/m}
$$

where $a$ and $m$ are positive integers. If $a=2$, then $S(2,m) = G(1;m)$.

The sums $S(a,m)$ enjoy a reciprocity law (stated below in Theorem 9.16) which implies Gauss' formula (30) and also 
leads to another proof of the quadratic reciprocity law. 

**Theorem 9.16** If the product $ma$ is even, we have 

$$
S(a,m) = \sqrt{\frac{m}{a}} \left( \frac{1+i}{\sqrt{2}} \right) \overline{S(m,a)} \qquad(31)
$$

where the bar denotes the complex conjugate.

*Note*. To deduce Gauss' formula (30) we take $a=2$ in (31) and observe that $\overline{S(m,2)}=1+e^{-\pi im/2}$.

PROOF. This proof is based on residue calculus. Let $g$ be the function defined by the equation 

$$
g(z) = \sum_{r=0}^{m-1} e^{\pi ia(z+r)^2/m} \qquad(32)
$$

Then $g$ is analytic everywhere, and $g(0)=S(a,m)$. Since $ma$ is even we find

$$
g(z+1) - g(z) = e^{\pi iaz^2/m} (e^{2 \pi iaz} - 1) 
              = e^{\pi iaz^2/m} (e^{2 \pi iz} - 1) \sum_{n=0}^{a-1} e^{2 \pi inz}
$$

Now define $f$ by the equation

$$
f(z) = \frac{g(z)}{e^{2 \pi iz} - 1}
$$

Then $f$ is analytic everywhere except for a first-order pole at each integer, and $f$ satisfies the equation

$$
f(z+1) = f(z) + \varphi(z) \qquad(33)
$$

where

$$
\varphi(z) = e^{\pi iaz^2/m} \sum_{n=0}^{a-1} e^{2 \pi inz} \qquad(34)
$$

The function $\varphi(z)$ is analytic everywhere.

At $z=0$ the residue of $f$ is $g(0)/(2\pi i)$ and hence

$$
S(a,m) = g(0) = 2 \pi i \operatorname{Res}_{z=0} = \int_\gamma f(z) dz
$$

where $\gamma$ is any positively oriented simple closed path whose graph contains only the pole $z=0$ in its interior 
region. We will choose $\gamma$ so that it describes a parallelogram with vertices $A$, $A+1$, $B+1$, $B$ where

$$
A = -\frac{1}{2} - R e^{\pi i/4} \text{ and } B = -\frac{1}{2} + R e^{\pi i/4}
$$

as shown in Figure 9.1. Integrating $f$ along $\gamma$ we have

$$
\int_\gamma f = \int_A^{A+1} f + \int_{A+1}^{B+1} f + \int_{B+1}^B f + \int_B^A f
$$

![Figure 9.1](images/9.1.png)

In the integral $\int_{A+1}^{B+1} f$ we make the change of variable $w=z+1$ and then use (33) to get

$$
\int_{A+1}^{B+1} f(w) dw = \int_A^B f(z+1) dz = \int_A^B f(z) dz + \int_A^B \varphi(z) dz 
$$

Therefore (35) becomes

$$
S(a,m) = \int_A^B \varphi(z) dz + \int_A^{A+1} f(z) dz - \int_B^{B+1} f(z) dz \qquad(36)
$$

Now we show that the integrals along the horizontal segments from $A$ to $A+1$ and from $B$ to $B+1$ tend to $0$ as 
$R \to \infty$. To do this we estimate the integrand on these segments. We write

$$
\left| f(z) \right| = \frac{\left| g(z) \right|}{\left| e^{2 \pi iz} - 1\right|} \qquad(37)
$$

and estimate the numerator and denominator separately.

On the segment joining $B$ to $B+1$ we let

$$
\gamma(t) = t + R e^{\pi i/4}, \text{ where } -\frac{1}{2} \le t \le \frac{1}{2}
$$

From (32) we find

$$
\left| g[\gamma(t)] \right| \le \sum_{r=0}^{m-1} \left| \mathrm{exp}\left\{ \frac{\pi ia(t + R e^{\pi i/4} + r)^2}{m} \right\} \right| \qquad(38)
$$

where $\mathrm{exp} z = e^z$. The expression in braces has real part

$$
\frac{-\pi a(\sqrt{2}tR + R^2 + \sqrt{2}rR)}{m}
$$

Since $\left| e^{x+iy} \right|=e^x$ and $\mathrm{exp}\left\{ -\pi a \sqrt{2}rR/m \right\} \le 1$, each term in (38) has 
absolute value not exceeding $\mathrm{exp}\left\{ -\pi aR^2/m \right\} \mathrm{exp} \left\{ -\sqrt{2} \pi atR/m \right\}$. 
But $-1/2 \le t \lt 1/2$, so we obtain the estimate

$$
\left| g[\gamma(t)] \right| \le m e^{\pi \sqrt{2} aR/(2m)} e^{-\pi aR^2/m}
$$

For the denominator in (37) we use the triangle inequality in the form 

$$
\left| e^{2 \pi iz} - 1 \right| \ge \left| \left| e^{2 \pi iz} \right| -1 \right|
$$

Since $\mathrm{exp}\left\{ 2 \pi i \gamma(t) \right\} = \mathrm{exp}\left\{ -2 \pi R \sin{\pi/4} \right\} =  \mathrm{exp}\left\{ -\sqrt{2} \pi R \right\}$, 
we find

$$
\left| e^{2 \pi i \gamma(t)} - 1 \right| \ge 1 - e^{-\sqrt{2} \pi R}
$$

Therefore on the line segment joining $B$ to $B+1$ we have the estimate

$$
\left| f(z) \right| \le \frac{m e^{\pi \sqrt{2} aR/(2m)} e^{-\pi a R^2/m}}{1 - e^{-\sqrt{2} \pi R}} 
                    = o(1) \text{ as } R \to +\infty
$$

A similar argument shows that the integrand tends to $0$ on the segment joining $A$ to $A+1$ as $R \to +\infty$. Since 
the length of the path of integration is $1$ in each case, this shows that the second and third integrals on the right 
of (36) tend to $0$ as $R \to +\infty$. Therefore we can write (36) in the form

$$
S(a,m) = \int_A^B \varphi(z) dz + o(1) \text{ as } R \to +\infty \qquad(39)
$$

To deal with the integral $\int_A^B \varphi$ we apply Cauchy's theorem, integrating $\varphi$ around the parallelogram 
with vertices $A, B, \alpha, -\alpha$, where $\alpha = B+\frac{1}{2} = R e^{\pi i/4}$. (See Figure 9.2.) Since 
$\varphi$ is analytic everywhere, its integral around this parallelogram is $0$, so

$$
\int_A^B \varphi + \int_B^\alpha \varphi + \int_\alpha^{-\alpha} \varphi + \int_{-\alpha}^A \varphi = 0 \qquad(40) 
$$

![Figure 9.2](images/9.2.png)

Because of the exponential factor $e^{\pi iaz^2/m}$ in (34), an argument similar to that given above shows that the 
integral of $\varphi$ along each horizontal segment $\to 0$ as $R \to +\infty$. Therefore (40) gives us

$$
\int_A^B \varphi = \int_{-\alpha}^\alpha \varphi + o(1) \text{ as } R \to +\infty
$$

and (39) becomes

$$
S(a,m) =  \int_{-\alpha}^\alpha \varphi(z) dz + o(1) \text{ as } R \to +\infty \qquad(41)
$$

where $\alpha = R e^{\pi i/4}$. Using (34) we find

$$
\int_{-\alpha}^\alpha \varphi(z) dz = \sum_{n=0}^{a-1} \int_{-\alpha}^\alpha e^{{\pi}iaz^2/m} e^{2{\pi}inz} dz
                                    = \sum_{n=0}^{a-1} e^{-{\pi}imn^2/a} I(a,m,n,R)
$$

where

$$
I(a,m,n,R) = \int_{-\alpha}^\alpha \mathrm{exp}\left\{ \frac{{\pi}ia}{m} \left( z+\frac{nm}{a} \right)^2 \right\} dz
$$

Applying Cauchy's theorem again to the parallelogram with vertices $-\alpha$, $\alpha$, $\alpha-(nm/a)$, and 
$-\alpha-(nm/a)$, we find as before that the integrals along the horizontal segments $\to 0$ as $R \to +\infty$, so

$$
I(a,m,n,R) = \int_{-\alpha-nm/a}^{\alpha-nm/a} \mathrm{exp}\left\{ \frac{{\pi}ia}{m} \left( z+\frac{nm}{a} \right)^2 \right\} dz + o(1) \text{ as } R \to +\infty
$$

The change of variable $w=\sqrt{a/m}(z+(nm/a))$ puts this into the form

$$
I(a,m,n,R) = \sqrt{\frac{m}{a}} \int_{-\alpha \sqrt{a/m}}^{\alpha \sqrt{a/m}} e^{{\pi}iw^2} dw + o(1) \text{ as } R \to +\infty
$$

Letting $R \to +\infty$ in (41), we find

$$
S(a,m) = \sum_{n=0}^{a-1} e^{-{\pi}imn^2/a} \sqrt{\frac{m}{a}} \lim_{R \to \infty} \int_{-R\sqrt{a/m}e^{{\pi}i/4}}^{R\sqrt{a/m}e^{{\pi}i/4}} e^{{\pi}iw^2} dw \qquad(42)
$$

By writing $T = \sqrt{a/m}R$,  we see that the last limit is equal to

$$
\lim_{T \to +\infty} \int_{-Te^{{\pi}i/4}}^{Te^{{\pi}i/4}} e^{{\pi}iw^2} dw = I
$$

say, where $I$ is a number independent of $a$ and $m$. Therefore (42) gives us 

$$
S(a,m) = \sqrt{\frac{m}{a}} I \overline{S(m,a)} \qquad(43)
$$

To evaluate $I$ we take $a=1$ and $m=2$ in (43). Then $S(1,2)=1+i$ and $S(2,1)=1$, so (43) implies $I=(1 + i)/\sqrt{2}$, 
and (43) reduces to (31). $\square$

Theorem 9.16 implies a reciprocity law for quadratic Gauss sums.

**Theorem 9.17** If $h \gt 0$, $k \gt 0$, $h$ odd, then

$$
G(h;k) = \sqrt{\frac{k}{h}} \frac{1+i}{2} (1+e^{-{\pi}ihk/2}) \overline{G(k;h)} \qquad(44)
$$

PROOF. Take $a=2h$, $m=k$ in Theorem 9.16 to obtain

$$
G(h;k) = S(2h,k) = \sqrt{\frac{k}{2h}} \frac{1+i}{\sqrt{2}} \overline{S(k,2h)}
                 = \sqrt{\frac{k}{h}} \frac{1+i}{2} \sum_{r=0}^{2h-1} e^{{\pi}ikr^2/(2h)} \qquad(45)
$$

We split the sum on $r$ into two parts corresponding to even and odd $r$. For even $r$ we write $r=2s$ where 
$s=0,1,2,\ldots,h-1$. For odd $r$ we note that $(r+2h)^2 \equiv r^2 \pmod{4h}$ so the sum can be extended over 
the odd numbers in any complete residue system mod $2h$. We sum over the odd numbers in the interval 
$h \le r \lt 3h$, writing $r=2s+h$, where $s=0,1,2,\ldots,h-1$. (The numbers $2s+h$ are odd and distinct mod $2h$.) 
This gives us

$$
\begin{align*}
\sum_{r=0}^{2h-1} e^{-{\pi}ikr^2/(2h)} &= \sum_{s=0}^{h-1} e^{-{\pi}ik(2s)^2/(2h)} + \sum_{s=0}^{h-1} e^{-{\pi}ik(2s+h)^2/(2h)} \\
                                       &= \sum_{s=0}^{h-1} e^{-2{\pi}iks^2/h} (1 + e^{-{\pi}ihk/2}) \\
                                       &= (1 + e^{-{\pi}ihk/2}) \overline{G(k;h)}
\end{align*}
$$

Using this in (45) we obtain (44). $\square$

## 9.11 Another proof of the quadratic reciprocity law
































