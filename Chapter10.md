# 10. Primitive Roots

## 10.1 The exponent of a number mod $m$. Primitive roots

Let $a$ and $m$ be relatively prime integers, with $m \ge 1$, and consider all the positive powers of $a$:

$$
a, a^2, a^3, \ldots
$$

We know, from the Euler-Fermat theorem, that $a^{\varphi(m)} \equiv 1 \pmod{m}$. However, there may be an earlier power 
$a^f$ such that $a^f \equiv 1 \pmod{m}$. We are interested in the smallest positive $f$ with this property.

**Definition** The smallest positive integer f such that

$$
a^f \equiv 1 \pmod{m}
$$

is called the exponent of $a$ modulo $m$, and is denoted by writing 

$$
f = \exp_m(a)
$$

If $\exp_m(a) = \varphi(m)$, then $a$ is called a primitive root mod $m$.

The Euler-Fermat theorem tells us that $\exp_m(a) \le \varphi(m)$. The next theorem shows that $\exp_m(a)$ divides 
$\varphi(m)$.

**Theorem 10.1** Given $m \ge 1$, $(a,m)=1$, let $f=\exp_m(a)$. Then we have:

(a) $a^k \equiv a^h \pmod{m}$ if, and only if, $k \equiv h \pmod{f}$.  
(b) $a^k \equiv 1 \pmod{m}$ if, and only if, $k \equiv 0 \pmod{f}$. In particular, $f|\varphi(m)$.  
(c) The numbers $1, a, a^2, \ldots, a^{f-1}$ are incongruent mod $m$.

**PROOF.** Parts (b) and (c) follow at once from (a), so we need only prove (a).  
If $a^k \equiv a^h \pmod{m}$ then $a^{k-h} \equiv 1 \pmod{m}$. Write

$$
k - h = qf + r, \text{ where } 0 \le r \lt f
$$

Then $1 \equiv a^{k-h} = a^{qf+r} \equiv a^r \pmod{m}$, so $r=0$ and $k \equiv h \pmod{f}$.

Conversely, if $k \equiv h \pmod{m}$ then $k-h=qf$ so $a^{k-h} \equiv 1 \pmod{m}$ and hence $a^k \equiv a^h \pmod{m}$.

## 10.2 Primitive roots and reduced residue systems

## 10.3 The nonexistence of primitive roots mod $2^\alpha$ for $\alpha \ge 3$

## 10.4 The existence of primitive roots mod $p$ for odd primes $p$

## 10.5 Primitive roots and quadratic residues

## 10.6 The existence of primitive roots mod $p^\alpha$

## 10.7 The existence of primitive roots mod $2p^\alpha$

## 10.8 The nonexistence of primitive roots in the remaining cases

## 10.9 The number of primitive roots mod $m$

## 10.10 The index calculus

## 10.11 Primitive roots and Dirichlet characters

## 10.12 Real-valued Dirichlet characters mod $p^\alpha$

## 10.13 Primitive Dirichlet characters mod $p^\alpha$
