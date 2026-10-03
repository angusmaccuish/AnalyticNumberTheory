# 8. Periodic Arithmetical Functions and Gauss Sums

## 8.1 Functions periodic modulo $k$

Let $k$ be a positive integer. An arithmetical function $f$ is said to be *periodic with period $k$* (or *periodic 
modulo $k$*) if 

$$
f(n+k) = f(n)
$$

for all integers $n$. If *k* is a period so is $mk$  for any integer $m > 0$. The smallest positive period of $f$ is 
called the *fundamental period*.

Periodic functions have already been encountered in the earlier chapters. For example, the Dirichlet characters mod $k$ 
are periodic mod $k$. A simpler example is the greatest common divisor $(n, k)$ regarded as a function of $n$. 
Periodicity enters through the relation

$$
(n+k, k) = (n,k)
$$

Another example is the exponential function

$$
f(n) = e^{2 \pi i mn/k}
$$

where $m$ and $k$ are fixed integers. The number $e^{2 \pi m/k}$ is a $k$-th root of unity and $f(n)$ is its $n$th 
power. Any finite linear combination of such functions, say

$$
\sum_m c(m) e^{2 \pi  i mn/k}
$$

is also periodic mod $k$ for every choice of the coefficients $c(m)$. Our first goal is to show that every arithmetical 
function which is periodic mod $k$ can be expressed as a linear combination of this type. These sums are called *finite 
Fourier series*. We begin the discussion with a simple but important example known as the *geometric sum*.

**Theorem 8.1** *For fixed $k >= 1$ let*

$$
g(n) = \sum_{m=0}^{k-1} e^{2 \pi i mn/k}
$$

*Then*

$$
g(n) = \begin{cases}
            0 & k \nmid n \\ 
            k & k \: | \: n 
       \end{cases}
$$

PROOF. Since $g(n)$ is the sum of terms in a geometric progression,

$$
g(n) = \sum_{m=0}^{k-1} x^m
$$

where $x = e^{2 \pi i n/k}$, we have

$$
g(n) = \begin{cases}
            \frac{x^k-1}{x-1} & x \ne 1 \\ 
            k                 & x=1 
       \end{cases}
$$

But $x^k=1$, and $x=1$ if and only if $k|n$, so the theorem is proved. $\square$

## 8.2 Existence of finite Fourier series for periodic arithmetical functions

We shall use Lagrange's polynomial interpolation formula to show that every periodic arithmetical function has a finite 
Fourier expansion.

**Theorem 8.2** Lagrange's interpolation theorem. Let $z_0, z_1, \ldots, z_{k-1}$ be $k$ distinct complex numbers and 
let $w_0, w_1, \ldots, w_{k-1}$ be $k$ complex numbers which need not be distinct. Then there is a unique polynomial 
$P(z)$ of degree $\le k-1$ such that

$$
P(z_m) = w_m, \text{for } m = 0, 1, 2, \ldots, k-1
$$

PROOF. The required polynomial $P(z)$, called the Lagrange interpolation polynomial, can be constructed explicitly as 
follows. Let

$$
A(z) = (z-z_0)(z-z_1) \ldots (z-z_{k-1})
$$

and let

$$
A_m(z) = \frac{A(z)}{z-z_m}
$$

Then $A_m(z)$ is a polynomial of degree $k-1$ with the following properties:

$$
A_m(z_m) \ne 0, \quad A_m(z_j) = 0 \text{ if } j \ne m
$$

Hence $A_m(z)/A_m(z_m)$ is a polynomial of degree $k-1$ which vanishes at each $z_j$ for $j \ne m$, and has the value 
$1$ at $z_m$. Therefore, the linear combination

$$
P(z) = \sum_{m=0}^{k-1} w_m \frac{A_m(z)}{A_m(z_m)}
$$

is a polynomial of degree $\le k-1$ with $P(z_j) = w_j$ for each $j$. If there were another such polynomial, say 
$Q(z)$, the difference $P(z)-Q(z)$ would vanish at $k$ distinct points, hence $P(z) = Q(z)$ since both polynomials have 
degree $\le k-1$. $\square$

Now we choose the numbers $z_0, z_1, \ldots, z_{k-1}$ to be the $k$-th roots of unity and we obtain:

**Theorem 8.3** Given $k$ complex numbers $w_0, w_1, \ldots, w_{k-1}$, there exist k uniquely determined complex 
numbers  $a_0, a_1, \ldots, a_{k-1}$ such that

$$
w_m = \sum_{n=0}^{k-1} a_n e^{2 \pi i mn/k} \tag{1}
$$

for $m = 0, 1, \ldots, k-1$. Moreover, the coefficients $a_n$ are given by the formula

$$
a_n = \frac{1}{k} \sum_{m=0}^{k-1} w_m e^{-2 \pi i mn/k} \tag{2}
$$

PROOF. Let $z_m = e^{2 \pi i m/k}$. The numbers $z_0, z_1, \ldots, z_{k-1}$ are distinct so there is a unique Lagrange 
polynomial

$$
P(z) = \sum_{n=0}^{k-1} a_n z^n
$$

such that $P(z_m) = w_m$ for each $m = 0, 1, \ldots, k-1$. This shows that there are uniquely determined numbers $a_n$ 
satisfying (1). To deduce the formula (2) for $a_n$ we multiple both sides of (1) by $e^{-2 \pi i mr/k}$, where $m$ and 
$r$ are non-negative integers less than $k$, and sum on $m$ to get

$$
\sum_{m=0}^{k-1} w_m e^{-2 \pi i mr/k} = \sum_{n=0}^{k-1} a_n \sum_{m=0}^{k-1} e^{2 \pi i (n-r)m/k}
$$

By Theorem 8.1, the sum on $m$ is $0$ unless $k \: | \: (n-r)$. But $|n-r| \le k-1$ so $k \: | \: (n-r)$ if, and only 
if, $n=r$. Therefore the only nonvanishing term on the right occurs when $n=r$ and we find

$$
\sum_{m=0}^{k-1} w_m e^{-2 \pi i mr/k} = k a_r
$$

This equation gives us (2). $\square$

**Theorem 8.4** Let $f$ be an arithmetical function which is periodic mod $k$. Then there is a uniquely determined 
arithmetical function $g$, also periodic mod $k$, such that

$$
f(n) = \sum_{n=0}^{k-1} g(n) e^{2 \pi i mn/k}
$$

In fact, $g$ is given by the formula

$$
g(n) = \frac{1}{k} \sum_{m=0}^{k-1} f(m) e^{-2 \pi i mn/k}
$$

PROOF. Let $w_m = f(m)$ for $m = 0, 1, \ldots, k-1$ and apply Theorem 8.3 to determine the numbers $a_0, a_1, \ldots, 
a_{k-1}$. Define the function $g$ by the relations $g(m) = a_m$ for $m = 0, 1, \ldots, k-1$ and extend the definition
of $g(m)$ to all integers $m$ by periodicity mod $k$. Then $f$ is related to $g$ by the equations in the theorem.
$\square$

*Note.* Since both $f$ and $g$ are periodic mod $k$, we can rewrite the sums in Theorem 8.4 as follows:

$$
f(m) = \sum_{n \: \text{mod} \; k} g(n) e^{2 \pi i mn/k} \tag{3}
$$

and
$$
g(n) = \frac{1}{k} \sum_{m \: \text{mod} \; k} f(m) e^{-2 \pi i mn/k} \tag{4}
$$

In each case the summation can be extended over any complete residue system modulo $k$. The sum in (3) is called the
*finite Fourier expansion* of $f$ and the numbers $g(n)$ defined by (4) are called the *Fourier coefficients* of $f$.

## 8.3 Ramanujan's sum and generalisations

## 8.4 Multiplicative properties of the sums $s_k(n)$

Out of scope

## 8.5 Gauss sums associated with Dirichlet characters

## 8.6 Dirichlet characters and nonvanishing Gauss sums

## 8.7 Induced moduli and primitive characters

## 8.8 Further properties of induced moduli

## 8.9 The conductor of a character

## 8.10 Primitive characters and separable Gauss sums

## 8.11 The finite Fourier series of the Dirichlet characters

## 8.12 Polya's inequality for the partial sums of primitive characters
