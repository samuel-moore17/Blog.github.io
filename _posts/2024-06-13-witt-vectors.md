---
layout: post
title: "Witt vectors"
usemathjax: true
---

Today I'd like to discuss Witt vectors. Fix throughout a prime \\(p\\).

## Teichmüller lifts

Well we can begin with a study of (\O\\) in mixed characteristic [strict p-ring?]. Say \\(O\\) with residue field \\(k\\) of characteristic \\(p\\). Then get following:

**Proposition 1**: There exists a unique multiplicative section \\(\omega:k \to O\\) of the natural projection. 

I'll take a slow approach to this. Note if \\(\omega\\) is any multiplicative section then \\(\omega(\lambda)= \omega(\lambda^{1/p^n})^{p^n}\\). This is actually enough to uniquely determine \\(\omega\\): any two representatives of \\(\lambda^{1/p^n}\\) differ by an element of \\(\mathfrak m\\), but once we take \\(p^n\\)th powers, this difference `shrinks'. More precisely:

**Proposition 2**: Let \\(U_n=U_n(\lambda)\\) be the set \\(\\{x^{p^n} \mid x \in q^{-1}(\lambda^{1/p^n})\\}\\). Then \\(U_n\\) has diameter \\(\le \mathfrak m^n\\). 

This follows from the elementary

**Claim**: Let \\(a,b\in O\\) and \\(k \ge 1\\). If \\(a \equiv b \mod \mathfrak{m}^k\\) then \\(a^p \equiv b^p \mod \mathfrak m^{k+1}\\). 

_Proof_: Note that \\(a^p-b^p = (a-b)\cdot \sum_{i=0}^{p-1} a^i b^{p-1-i}=: (a-b)c\\), so we just need to show that \\(c\in \mathfrak m\\). And \\(c \equiv \sum_{i=0}^{p-1}a^i a^{p-1-i}= pa^{p-1} \equiv 0 \mod \mathfrak m\\) since \\(p \in \mathfrak m\\). \\(\square\\).

Now \\(\omega(\lambda)\\) belongs to \\(\bigcap_{n=0}^{\infty} U_n(\lambda)\\). But this intersection is a singleton by separatedness (?) and completeness, which means that \\(\omega\\) is uniquely determined and in fact we can _define_ it by \\(\\{\omega(\lambda)\}=\bigcap_{n=0}^{\infty}U_n(\lambda)\\).

There's an easy characterisation of the image of \\(\omega\\): it is the set \\(S\\) of elements which are \\(p^n\\)th powers for all \\(n\\). Clearly the image is contained in \\(S\\), and for the other direction, note that if \\(x = y^{p^n}\\) then \\(x \in U_n(q(x))\\), and if this holds for all \\(n\\) then \\(x \in \bigcap U_n(q(x)) = \{\omega(q(x))\}\\). 

Given this characterisation, it follows that \\(\omega(\lambda\mu) = \omega(\lambda).\omega(\mu)\\), since each side lies in \\(S\\) and \\(\omega\\) is injective, being a section of \\(q\\).

**Remark** When \\(k=\mathbf F_p\\), the Frobenius is the identity, so one sees easier formulae in that case, such as \\(\omega(x)=\lim_{n \to \infty} x^{p^n}\\).

