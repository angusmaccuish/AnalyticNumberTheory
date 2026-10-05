# 8. Periodic Arithmetical Functions and Gauss Sums

## 8.1 Functions periodic modulo $k$

Let $k$ be a positive integer. An arithmetical function $f$ is said to be *periodic with period $k$* (or *periodic 
modulo $k$*) if 

$$
f(n+k) = f(n)
$$

for all integers $n$. If *k* is a period so is $mk$  for any integer $m \gt 0$. The smallest positive period of $f$ is 
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

**Theorem 8.1** *For fixed $k \ge 1$ let*

$$
g(n) = \sum_{m=0}^{k-1} e^{2 \pi i mn/k}
$$

*Then*

$$
g(n) = \begin{cases}
            0 & \text{ if } k \nmid n \\ 
            k & \text{ if } k|n 
       \end{cases}
$$

PROOF. Since $g(n)$ is the sum of terms in a geometric progression,

$$
g(n) = \sum_{m=0}^{k-1} x^m
$$

where $x = e^{2 \pi i n/k}$, we have

$$
g(n) = \begin{cases}
            \frac{x^k-1}{x-1} & \text{ if } x \ne 1 \\ 
            k                 & \text{ if } x = 1 
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

By Theorem 8.1, the sum on $m$ is $0$ unless $k|(n-r)$. But $|n-r| \le k-1$ so $k|(n-r)$ if, and only 
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
f(m) = \sum_{n \text{ mod } k} g(n) e^{2 \pi i mn/k} \tag{3}
$$

and
$$
g(n) = \frac{1}{k} \sum_{m \text{ mod } k} f(m) e^{-2 \pi i mn/k} \tag{4}
$$

In each case the summation can be extended over any complete residue system modulo $k$. The sum in (3) is called the
*finite Fourier expansion* of $f$ and the numbers $g(n)$ defined by (4) are called the *Fourier coefficients* of $f$.

## 8.3 Ramanujan's sum and generalisations

In Exercise 2.14(b) it is shown that the M&ouml;bius function $\mu(k)$ is the sum of the primitive $k$-th roots of 
unity. In this section we generalise this result. Specifically, let $n$ be a fixed positive integer and consider the 
sum of the $n$-th powers of the primitive $k$-th roots of unity. This sum is known as *Ramanujan's sum* and is denoted 
by $c_k$(n):

$$
c_k(n) = \sum_{\substack{m \text{ mod } k \\ (m,k) = 1}} e^{2 \pi i mn/k}
$$

We have already noted that this sum reduces to the M&ouml;bius function when $n=1$,

$$
\mu(k) = c_k(1)
$$

When $k|n$ the sum reduces to the Euler $\varphi$ since each term is $1$ and the number of terms is 
$\varphi(k)$. Ramanujan showed that $c_k(n)$ is always an integer and that it has interesting multiplicative 
properties. He deduced these facts from the relation

$$
c_k(n) = \sum_{d|(n,k)} d \, \mu\Big(\frac{k}{d}\Big) \tag{5}
$$

This formula shows why $c_k(n)$ reduces to both $\mu(k)$ and $\varphi(k)$. In fact, when $n=1$ there is only one term 
in the sum and we obtain $c_k(1) = \mu(k)$. And when $k|n$ we have $(n,k) = k$ and 
$c_k(n) = \sum_{d|k} d \, \mu(\frac{k}{d}) = \varphi(k)$. We shall deduce (5) as a special case of the more 
general result (Theorem 8.5).

Formula (5) for $c_k(n)$ suggests that we study general sums of the form

$$
\sum_{d|(n,k)} f(d) \, g\Big(\frac{k}{d}\Big) \tag{6}
$$

These resemble the sums for the Dirichlet convolution of $f * g$ except that we sum over a *subset* of the divisors of 
$k$, namely those $d$ which also divide $n$.

Denote the sum in (6) by $s_k(n)$. Since $n$ occurs only in the $\gcd$ $(n,k)$ we have 

$$
s_k(n+k) = s_k(n)
$$

so $s_k(n)$ is a periodic function of $n$ with period $k$. Hence this sum has a finite Fourier expansion. The next 
theorem tells us that its Fourier coefficients are given by a sum of the same type.

**Theorem 8.5** Let $s_k(n) = \sum_{d|(n,k)} f(d) \, g(\frac{k}{d})$. Then $s_k(n)$ has a finite Fourier 
expansion

$$
s_k(n) = \sum_{m \text{ mod } k} a_k(m) e^{2 \pi i mn/k} \tag{7}
$$

where

$$
a_k(m) = \sum_{d|(m,k)} g(d) \, f\Big(\frac{k}{d}\Big) \frac{d}{k} \tag{8}
$$

PROOF. By Theorem 8.4 the coefficients $a_k(m)$ are given by

$$
\begin{align*}
a_k(m) &= \frac{1}{k} \sum_{n \text{ mod } k} s_k(n) e^{-2 \pi i mn/k} \\
       &= \frac{1}{k} \sum_{n=1}^k \sum_{\substack{d|n \\ d|k}} f(d) \, g\Big(\frac{k}{d}\Big) e^{-2 \pi i mn/k} \\
\end{align*}
$$

Now we write $n=cd$ and note that for each fixed $d$ the index $c$ runs from $1$ to $k/d$ and we obtain

$$
a_k(m) = \frac{1}{k} \sum_{d|k} f(d) \, g\Big(\frac{k}{d}\Big) \sum_{c=1}^{k/d} e^{-2 \pi i cdm/k}
$$

Now we replace $d$ by $k/d$ in the sum on the right to get

$$
a_k(m) = \frac{1}{k} \sum_{d|k} f\Big(\frac{k}{d}\Big) \, g(d) \sum_{c=1}^{d} e^{-2 \pi i cm/d}
$$

But by Theorem 8.1 the sum on $c$ is $0$ unless $d|m$ in which case the sum has value $d$. Hence

$$
a_k(m) = \frac{1}{k} \sum_{\substack{d|k \\ d|m}} f\Big(\frac{k}{d}\Big) \,g(d) \, d
$$

which proves (8). $\square$

Now we specialise $f$ and $g$ to obtain the formula for Ramanujan's sum mentioned earlier.

**Theorem 8.6** We have

$$
c_k(n) = \sum_{d|(n,k)} d \, \mu\Big(\frac{k}{d}\Big)
$$

PROOF. Taking $f(k)=k$ and $g(k)=\mu(k)$ in Theorem 8.5 we find

$$
\sum_{d|(n,k)} d \, \mu\Big(\frac{k}{d}\Big) = \sum_{m \text{ mod } k} a_k(m) e^{2 \pi i mn/k}
$$

where

$$
a_k(m) = \sum_{d|(m,k)} \mu(d) \Big[\frac{1}{(m,k)}\Big] = 
\begin{cases}
1 & \text{ if } (m,k) = 1 \\
0 & \text{ if } (m,k) \gt 1
\end{cases}                                                          
$$

Hence

$$
\sum_{d|(n,k)} d \, \mu\Big(\frac{k}{d}\Big) 
= \sum_{\substack{m \text{ mod } k \\ (m,k)=1}} e^{2 \pi i mn/k} 
= c_k(n)
$$

## 8.4 Multiplicative properties of the sums $s_k(n)$

Out of scope

## 8.5 Gauss sums associated with Dirichlet characters

**Definition** For any Dirichlet character $\chi$ mod $k$ the sum

$$
G(n,\chi) = \sum_{m=1}^k \chi(m) e^{2 \pi i mn/k} 
$$

is called the Gauss sum associated with $\chi$.

If $\chi=\chi_1$, the principal character mod $k$, we have $\chi_1(m)=1$ if $(m,k)=1$, and $\chi_1(m)=0$ otherwise. In 
this case the Gauss sum reduces to Ramanajan's sum:

$$
G(n,\chi_1) = \sum_{\substack{m=1 \\ (m,k)=1}}^k e^{2 \pi i mn/k}
$$

Thus, the Gauss sums $G(n,\chi)$ can be regarded as generalisations of Ramanujan's sum. We turn now to a detailed study 
of their properties.

The first result is a factorisation property which plays an important role in the subsequent development.

**Theorem 8.9** If $\chi$ is any Dirichlet character mod $k$ then

$$
G(n,\chi) = \bar\chi(n)G(1,\chi) \text{ whenever } (n,k) = 1
$$

PROOF. When $(n,k)=1$ and the numbers $nr$ run through a complete residue system mod $k$ with $r$. Also
$|\chi(n)|^2 = \chi(n) \bar\chi(n) = 1$ so

$$
\chi(r) = \bar\chi(n) \chi(n) \chi(r) = \bar\chi(n) \chi(nr)
$$

Therefore the sum defining $G(n,\chi)$ can be written as follows:

$$
\begin{align*}
G(n,\chi) 
&= \sum_{r \text{ mod } k} \chi(r) e^{2 \pi i nr/k} 
= \bar\chi(n) \sum_{r \text{ mod } k} \chi(nr) e^{2 \pi i nr/k} \\
&= \bar\chi(n) \sum_{m \text{ mod } k} \chi(m) e^{2 \pi i m/k} = \bar\chi(n) G(1,\chi)
\end{align*}
$$

This proves the theorem. $\square$

**Definition** The Gauss sum $G(n,\chi)$ is said to be separable if 

$$
G(n,\chi) = \bar\chi(n) G(1,\chi) \tag{12}
$$

Theorem 8.9 tells us that $G(n,\chi)$ is separable whenever $n$ is relatively prime to the modulus $k$. For those 
integers $n$ not relatively prime to $k$ we have the following theorem.

**Theorem 8.10** If $\chi$ is a character mod $k$ the Gauss sum $G(n,\chi)$ is separable for every $n$ if, and only if, 

$$
G(n,\chi) = 0 \text{ whenever } (n,k) > 1
$$

PROOF. Separability always hold if $(n,k)=1$. But if $(n,k) \gt 1$ we have $\bar\chi(n)=0$ so Equation (12) holds if 
and only if $G(n,\chi)=0$.

The next theorem gives an important consequence of separability.

**Theorem 8.11** if $G(n,\chi)$ is separable for every $n$ then

$$
|G(1,\chi)|^2 = k \tag{13}
$$

PROOF. We have

$$
\begin{align*}
|G(1,\chi)|^2 &= G(1,\chi)\overline{G(1,\chi)} = G(1,\chi) \sum_{m=1}^k \bar\chi(m) e^{-2 \pi i m/k}             \\
&= \sum_{m=1}^k G(m,\chi) e^{-2 \pi i m/k} = \sum_{m=1}^k \sum_{r=1}^k \chi(r) e^{2 \pi i mr/k} e^{-2 \pi i m/k} \\
&= \sum_{r=1}^k \chi(r) \sum_{m=1}^k e^{2 \pi i m(r-1)/k} = k\chi(1) = k
\end{align*}
$$

since the last sum over $m$ is a geometric sum which vanishes unless $r=1$. $\square$

## 8.6 Dirichlet characters and nonvanishing Gauss sums

For every character $\chi$ mod $k$ we have seen that $G(n,\chi)$ is separable if $(n,k)=1$, and that the separability of 
$G(n,\chi)$ is equivalent to the vanishing of $G(n,\chi)$ for $(n,k) \gt 1$. Now we describe the further properties of 
those characters such that $G(n,\chi)=0$ whenever $(n,k) \gt 1$. Actually, is it simpler to study the complementary 
set. The next theorem gives a necessary condition for $G(n,\chi)$ to be nonzero for $(n,k) \gt 1$.

**Theorem 8.12** Let $\chi$ be a Dirichlet character mod $k$ and assume that $G(n,\chi) \ne 0$ for some $n$ satisfying
$(n,k) \gt 1$. Then there exists a divisor $d$ of $k$, $d \lt k$, such that

$$
\chi(a) = 1 \text{ whenever } (a,k) = 1 \text{ and } a \equiv 1 \pmod{d} \tag{14}
$$

PROOF. For the given $n$, let $q=(n,k)$ and let $d=k/q$. Then $d|k$ and, since $q \gt 1$, we have $d \lt k$. Choose any 
$a$ satisfying $(a,k)=1$ and let $a \equiv 1 \pmod{d}$. We will prove that $\chi(a)=1$.

Since $(a,k)=1$, in the sum defining $G(n,\chi)$ we can replace the index of summation $m$ by $am$ and we find

$$
\begin{align*}
G(n,\chi) &= \sum_{m \text{ mod } k} \chi(m) e^{2 \pi i nm/k} = \sum_{m \text{ mod } k} \chi(am) e^{2 \pi i nam/k}\\
          &= \chi(a) \sum_{m \text{ mod } k} \chi(m) e^{2 \pi i nam/k}
\end{align*}
$$

Since $a \equiv 1 \pmod{d}$ and $d=k/q$ we can write $a=1+(bk/q)$ for some integer $b$, and we have

$$
\frac{anm}{k} = \frac{nm}{k} + \frac{bknm}{qk} = \frac{nm}{k} + \frac{bnm}{q} \equiv \frac{nm}{k} \pmod{1}
$$

since $q|n$. Hence $e^{2 \pi i nam/k}=e^{2 \pi i nm/k}$ and the sum for $G(n,\chi)$ becomes

$$
G(n,\chi) = \chi(a) \sum_{m \text{ mod } k} \chi(m) e^{2 \pi i nm/k} = \chi(a) G(n,\chi)
$$

Since $G(n,\chi) \ne 0$ this implies $\chi(a)=1$, as asserted. $\square$

The foregoing theorem leads us to consider those characters $\chi$ mod $k$ for which there is a divisor $d \lt k$ 
satisfying (14). These are treated next.

## 8.7 Induced moduli and primitive characters

**Definition of induced modulus** Let $\chi$ be a Dirichlet character mod $k$ and let $d$ be any positive divisor of 
$k$. The number $d$ is called an induced modulus for $\chi$ if we have

$$
\chi(a) = 1 \text{ whenever } (a,k) = 1 \text{ and } a \equiv 1 \pmod{d} \tag{15}
$$

In other words, $d$ is an induced modulus if the character $\chi$ mod $k$ acts like a character mod $d$ on the 
representatives of the residue class $\hat{1}$ mod $d$ which are relatively prime to $k$. Note that $k$ itself is 
always an induced modulus for $\chi$.

**Theorem 8.13** Let $\chi$ be a Dirichlet character mod $k$. Then $1$ is an induced modulus for $\chi$ if, and only 
if, $\chi=\chi_1$.

PROOF. If $\chi=\chi_1$ then $\chi(a)=1$ for all $a$ relatively prime to $k$. But since every $a$ satisfies 
$a \equiv 1 \pmod{1}$ the number $1$ is an induced modulus.

Conversely, if $1$ is an induced modulus, then $\chi(a)=1$ whenever $(a,k)=1$, so $\chi=\chi_1$ since $\chi$ vanishes 
on the numbers not prime to $k$. $\square$

For any Dirichlet character mod $k$ the modulus $k$ itself is an induced modulus. If there are no others we call the 
character *primitive*. That is, we have

**Definition of primitive characters** A Dirichlet character $\chi$ mod $k$ is said to be primitive mod $k$ if it has 
no induced modulus $d \lt k$. In other words, $\chi$ is primitive mod $k$ if, and only if, for every divisor $d$ of 
$k$, $0 \lt d \lt k$, there exists an integer $a \equiv 1 \pmod{d}$, $(a,k)=1$, such that $\chi(a) \ne 1$.

If $k \gt 1$ the principal character $\chi_1$ is not primitive since it has $1$ as an induced modulus. Next we show 
that if the modulus is *prime* every nonprincipal character is primitive.

**Theorem 8.14** Every nonprincipal character $\chi$ modulo a prime $p$ is a primitive character mod $p$.

PROOF. The only divisors of $p$ are $1$ and $p$ so these are the only candidates for induced moduli. But if 
$\chi \ne \chi_1$ the divisor $1$ is not an induced modulus so $\chi$ has no induced modulus $\lt p$. Hence $\chi$ is 
primitive.

Now we can restate the results of Theorems 8.10 through 8.12 in the terminology of primitive characters.

**Theorem 8.15** Let $\chi$ be a primitive Dirichlet character mod $k$. Then we have:
- (a) $G(n,\chi)=0$ for every $n$ with $(n,k) \gt 1$.
- (b) $G(n,\chi)$ is separable for every $n$.
- (c) $|G(1,\chi)|^2 =k$.

PROOF. If $G(n,\chi) \ne 0$ for some $n$ with $(n,k) \gt 1$ then Theorem 8.12 shows that $\chi$ has an induced modulus 
$d \lt k$, so $\chi$ cannot be primitive. This proves (a).

Part (b) follows from (a) and Theorem 8.10. Part (c) follows from part (b) and Theorem 8.11.

*Note.* Theorem 8.15(b) shows that the Gauss sum $G(n,\chi)$ is separable if $\chi$ is primitive. In a later section 
we prove the converse. That is, if $G(n,\chi)$ is separable for every $n$ then $\chi$ is primitive. (See Theorem 8.19.)

## 8.8 Further properties of induced moduli

The next theorem refers to the action of $\chi$ on numbers which are congruent modulo an induced modulus.

**Theorem 8.16** Let $\chi$ be a Dirichlet character mod $k$ and assume $d|k$, $d \gt 0$. Then $d$ is an induced 
modulus for $\chi$ if, and only if,

$$
\chi(a) = \chi(b) \text{ whenever } (a,k) = (b,k) = 1 \text{ and } a \equiv b \pmod{d} \tag{16}
$$

PROOF. If (16) holds then $d$ is an induced modulus since we may choose $b=1$ and refer to Equation (15). Now we prove 
the converse.

Choose $a$ and $b$ so that $(a,k)=(b,k)=1$ and $a \equiv b \pmod{d}$. We will show that $\chi(a)=\chi(b)$. Let $a'$ be 
the reciprocal of $a$ mod $k$, $aa' \equiv 1 \pmod{k}$. The reciprocal exists because $(a,k)=1$. Now 
$aa' \equiv 1 \pmod{d}$ since $d|k$. Hence $\chi(aa')=1$ since $d$ is an induced modulus. But 
$aa' \equiv ba' \equiv 1 \pmod{d}$ because $a \equiv b \pmod{d}$, hence $\chi(aa')=\chi(ba')$, so

$$
\chi(a)\chi(a') = \chi(b)\chi(a')
$$

But $\chi(a') \ne 0$ since $\chi(a)\chi(a')=1$. Cancelling $\chi(a')$ we find $\chi(a)=\chi(b)$, and this completes the 
proof. $\square$

Equation (16) tells us that $\chi$ is periodic mod $d$ on those integers relatively prime to $k$. Thus $\chi$ acts very 
much like a character mod $d$. To further explore this relation it is worthwhile to consider a few examples.

EXAMPLE 1 The following table describes one of the characters $\chi$ mod $9$.

| n         | 1 | 2  | 3 | 4 | 5  | 6 | 7 | 8  | 9 |
| --------- | - | -- | - | - | -- | - | - | -- | - |
| $\chi(n)$ | 1 | -1 | 0 | 1 | -1 | 0 | 1 | -1 | 0 | 

We note that this table is periodic modulo $3$ so $3$ is an induced modulus for $\chi$. In fact, $\chi$ acts like the 
following character $\psi$ modulo $3$:

| n         | 1 | 2  | 3 |
| --------- | - | -- | - |
| $\psi(n)$ | 1 | -1 | 0 |

Since $\chi(n)=\psi(n)$ for all $n$ we call $\chi$ an *extension* of $\psi$. It is clear that whenever $\chi$ is an 
extension of a character $\psi$ modulo $d$ then $d$ will be an induced modulus for $\chi$.

EXAMPLE 2 Now we examine one of the characters $\chi$ modulo $6$:

| n         | 1 | 2 | 3 | 4 | 5  | 6 |
| --------- | - | - | - | - | -- | - |
| $\chi(n)$ | 1 | 0 | 0 | 0 | -1 | 0 | 

In this case the number $3$ is an induced modulus because $\chi(n)=1$ for all $n \equiv 1 \pmod{3}$ with $(n,6)=1$.
(There is only one such $n$, namely, $n=1$.)

However, $\chi$ is *not* an extension of any character $\psi$ modulo $3$, because the only characters modulo $3$ are 
the principal character $\psi_1$, given by the table:

| n           | 1 | 2 | 3 |
| ----------- | - | - | - |
| $\psi_1(n)$ | 1 | 1 | 0 |

and the character $\psi$ shown in Example 1. Since $\chi(2)=0$ it cannot be an extension of either $\psi$ or $\psi_1$.

These examples shed light on the next theorem.

**Theorem 8.17** Let $\chi$ be a Dirichlet character modulo $k$ and assume $d|k$, $d \gt 0$. Then the following two 
statements are equivalent:
- (a) $d$ is an induced modulus for $\chi$.
- (b) There is a character $\psi$ modulo $d$ such that $$\chi(n) = \psi(n)\chi_1(n) \text{ for all } n \tag{17}$$ 
      where $\chi_1$ is the principal character modulo $k$.

PROOF. Assume (b) holds. Choose $n$ satisfying $(n,k)=1$, $n \equiv 1 \pmod{d}$. Then $\chi_1(n)=\psi(n)=1$ so 
$\chi(n)=1$ and hence $d$ is an induced modulus. Thus, (b) implies (a).

Now assume (a) holds. We will exhibit a character $\psi$ modulo $d$ for which (17) holds. We define $\psi(n)$ as 
follows: if $(n,d) \gt 1$, let $\psi(n)=0$. In this case we also have $(n,k) \gt 1$ so (17) holds because both members 
are zero.

Now suppose $(n,d)=1$. Then there exists an integer $m$ such that $m \equiv n \pmod{d}$, $(m,k)=1$. This can be proved 
immediately with Dirichlet's theorem. The arithmetic progression $xd+n$ contains infinitely many primes. We choose one 
that does not divide $k$ and call this $m$. However, the result is not that deep; the existence of such an $m$ can be 
easily established without using Dirichlet's theorem. (See Exercise 8.4 for an alternative proof.) Having chosen $m$, 
which is unique modulo $d$, we define 

$$
\psi(n) = \chi(m)
$$

The number $\psi(n)$  is well-defined because $\chi$ takes equal values at numbers which are congruent modulo $d$ and 
relatively prime to $k$.

The reader can easily verify that $\psi$ is, indeed, a character mod $d$. We shall verify that Equation (17) holds for 
all $n$.

If $(n,k)=1$ then $(n,d)=1$ so $\psi(n)=\chi(m)$ for some $m \equiv n \pmod{d}$. Hence, by Theorem 8.16, 

$$
\chi(n) = \chi(m) = \psi(n) = \psi(n)\chi_1(n)
$$

since $\chi_1(n)=1$.

If $(n,k) \gt 1$, then $\chi(n)=\chi_1(n)=0$ and both members of (17)  are $0$. Thus, (17) holds for all $n$.

## 8.9 The conductor of a character

**Definition** Let $\chi$ be a Dirichlet character mod $k$. The smallest induced modulus $d$ for $\chi$ is called the 
conductor of $\chi$.

**Theorem 8.18** Every Dirichlet character $\chi$ mod $k$ can be expressed as a product,

$$
\chi(n) = \psi(n)\chi_1(n) \text{ for all } n \tag{18}
$$

where $\chi_1$ is the principal character mod $k$ and $\psi$ is a primitive character modulo the conductor of $\chi$.

PROOF. Let $d$ be the conductor of $\chi$. From Theorem 8.17 we know that $\chi$ can be expressed as a product of the 
form (18), where $\psi$ is a character mod $d$. Now we shall prove that $\psi$ is primitive mod $d$.

We assume that $\psi$ is not primitive mod $d$ and arrive at a contradiction. If $\psi$ is not primitive mod $d$ there 
is a divisor $q$ of $d$, $q \lt d$, which is an induced modulus for $\psi$. We shall prove that this $q$, which divides 
$k$, is also an induced modulus for $\chi$, contradicting the fact that $d$ is the smallest induced modulus for $\chi$.

Choose $n \equiv 1 \pmod{q}$, $(n,k)=1$. Then 

$$
\chi(n) = \psi(n)\chi_1(n) = \psi(n) = 1
$$

because $q$ is an induced modulus for $\psi$. Hence $q$ is also an induced modulus for $\chi$  and this is a 
contradiction. $\square$

## 8.10 Primitive characters and separable Gauss sums

As an application of the foregoing theorems we give the following alternate description of primitive characters.

**Theorem 8.19** Let $\chi$ be a character mod $k$. Then $\chi$ is primitive mod $k$ if, and only if, the Gauss sum

$$
G(n,\chi) = \sum_{m \text{ mod } k} \chi(m) e^{2 \pi i mn/k}
$$

is separable for every $n$.

PROOF. If $\chi$ is primitive, then $G(n,\chi)$ is separable by Theorem 8.15(b). Now we prove the converse.

Because of Theorems 8.9 and 8.10 it suffices to prove that if $\chi$ is not primitive mod $k$ then for some $r$ 
satisfying $(r,k) \gt 1$ we have $G(r,\chi) \ne 0$. Suppose, then, that $\chi$ is not primitive mod $k$. This implies 
$k \gt 1$. Then $\chi$ has a conductor $d \lt k$. Let $r=k/d$. Then $(r,k) \gt 1$ and we shall prove that 
$G(r,\chi) \ne 0$ for this $r$. By Theorem 8.18 there exists a primitive character $\psi$ mod $d$ such that 
$\chi(n)=\psi(n)\chi_1(n)$ for all $n$. Hence we can write

$$
\begin{align*}
G(r,\chi) &= \sum_{m \text{ mod } k} \psi(m) \chi_1(m) e^{2 \pi i rm/k}
           = \sum_{\substack{m \text{ mod } k \\ (m,k)=1}} \psi(m) e^{2 \pi i rm/k} \\
          &= \sum_{\substack{m \text{ mod } k \\ (m,k)=1}} \psi(m) e^{2 \pi i m/d}
           = \frac{\varphi(k)}{\varphi(d)} \sum_{\substack{m \text{ mod } d \\ (m,d)=1}} \psi(m) e^{2 \pi i m/d}
\end{align*}
$$

where in the last step we used Theorem 5.33(a). Therefore we have

$$
G(r,\chi) = \frac{\varphi(k)}{\varphi(d)} G(1,\psi)
$$

But $|G(1,\psi)|^2=d$ by Theorem 8.15 (since $\psi$ is primitive mod $d$) and hence $G(r,\chi) \ne 0$. This completes 
the proof. $\square$

## 8.11 The finite Fourier series of the Dirichlet characters

## 8.12 Polya's inequality for the partial sums of primitive characters
