---
layout: post
title: "Witt vectors"
usemathjax: true
---

Today I'd like to discuss Witt vectors. Fix throughout a prime \\(p\\).

## Teichmüller lifts

Let us begin with something less fancy. Let \\(O\\) be a complete DVR with residue field \\(k\\) of characteristic \\(p\\). Then:

**Proposition 1**: There exists a unique multiplicative section \\(\omega:k \to O\\) of the natural projection. 

I'll take a slow approach to this. Note if \\(\omega\\) is any multiplicative section then \\(\omega(\lambda)= \omega(\lambda^{1/p^n})^{p^n}\\). This is actually enough to uniquely determine \\(\omega\\): any two representatives of \\(\lambda^{1/p^n}\\) differ by an element of \\(\mathfrak m\\), but once we take \\(p^n\\)th powers, this difference `shrinks'. More precisely:

**Proposition 2**: Let \\(U_n=U_n(\lambda)\\) be the set \\(\\{x^{p^n} \mid x \in q^{-1}(\lambda^{1/p^n})\\}\\). Then \\(U_n\\) has diameter \\(\le \mathfrak m^n\\). 

This follows from the elementary

**Claim 3**: Let \\(a,b\in O\\) and \\(k \ge 1\\). If \\(a \equiv b \mod \mathfrak{m}^k\\) then \\(a^p \equiv b^p \mod \mathfrak m^{k+1}\\). 

_Proof_: Note that \\(a^p-b^p = (a-b)\cdot \sum_{i=0}^{p-1} a^i b^{p-1-i}=: (a-b)c\\), so we just need to show that \\(c\in \mathfrak m\\). And \\(c \equiv \sum_{i=0}^{p-1}a^i a^{p-1-i}= pa^{p-1} \equiv 0 \mod \mathfrak m\\) since \\(p \in \mathfrak m\\). \\(\square\\).

Now \\(\omega(\lambda)\\) belongs to \\(\bigcap_{n=0}^{\infty} U_n(\lambda)\\). But this intersection is a singleton by separatedness (?) and completeness, which means that \\(\omega\\) is uniquely determined and in fact we can _define_ it by \\(\\{\omega(\lambda)\\}=\bigcap_{n=0}^{\infty}U_n(\lambda)\\).

There's an easy characterisation of the image of \\(\omega\\): it is the set \\(S\\) of elements which are \\(p^n\\)th powers for all \\(n\\). Clearly the image is contained in \\(S\\), and for the other direction, note that if \\(x = y^{p^n}\\) then \\(x \in U_n(q(x))\\), and if this holds for all \\(n\\) then \\(x \in \bigcap U_n(q(x)) = \\{\omega(q(x))\\}\\). 

Given this characterisation, it follows that \\(\omega(\lambda\mu) = \omega(\lambda).\omega(\mu)\\), since each side lies in \\(S\\) and \\(\omega\\) is injective, being a section of \\(q\\).

**Remark 4** When \\(k=\mathbf F_p\\), the Frobenius is the identity, so one sees easier formulae in that case, such as \\(\omega(x)=\lim_{n \to \infty} x^{p^n}\\).

**Example 5** Consider the case of the p-adics \\(\mathbf Z_p\\) with residue field \\(\mathbf F_p\\). Then \\(\omega\\) provides a (multiplicative) bijection between \\(\mathbf F_p^\times\\) and the \\((p-1)\\)st roots of unity in \\(\mathbf Z_p\\).

## Witt vectors

Let me now move onto a more general and related construction - the formation of _Witt vectors_. This seems a tricky topic to motivate in general.

We'll set up \\(W(A)\\). I'd like to explain the strategy of proof.

**Definition 6** Define \\(\Phi_n \in \mathbf Z[X_0,\dots,X_n]\\) by \\(\Phi_n(a_0,\dots,a_n)=\sum_{i=0}^{n}p^i X_{i}^{p^{n-i}}\\). Slightly abusively, if \\(\mathbf a = (a_0,\dots,a_n)\\) or some sequence \\((a_0,a_1,\dots)\), we will write \\(\Phi(\mathbf a)\\) for \\(Phi(a_0,\dots,a_n)\\). We can put these together to form \\(\Phi_A: W(A) \to \mathbf A^N; \mathbf a \mapsto (\Phi_i(\mathbf a))_{i=0}^{\infty}\\).

I find these formulae a little hard to motivate. One thing to note, though, is that if \\(p=0\\) in \\(A\\), then the above map is simply \\((a_i)_{i=0}^{\infty} \mapsto (a_0,a_0^p,a_0^{p^2},\dots).\\). So \\(\Phi_A\\) should roughly turn pth powers into shifts. We'll actually find a lift of Frobenius \\(F\\) on \\(W(A)\\) such that \\(\Phi_A F = f_A \Phi_A\\) where \\(f_A\\) is a left shift.

It'll be important to work out \\(\Phi's\\) image. By going inductively, we're basically interested in seeing what conditions we need to find \\(a_n\\) with \\(\Phi_{n}(a_0,\dots,a_n)=u_n\\).

Note that \\(\Phi_n(a_0,\dots,a_{n-1},X_n) =\Phi_{n-1}(a_0^p,\dots,a_{n-1}^{p})) + p^n X_n\\) (*)

**Proposition 7** \\(\Phi_A\\) is injective if \\(p\\) is not a zero divisor in \\(A\\).

_Proof_ From (*) we see that if \\((u_k)_{k=0}^{\infty}=\Phi_A(a)\\) then each \\(a_n\\) is uniquely determined by \\(a_1,\dots,a_{k-1}\\). \\(\square\\).

**Proposition 8** Suppose \\(A,\sigma\\) is a ring with a lift of Frobenius and put \\(u_{n-1}=\Phi_{n-1}(a_0,\dots,a_{n-1})\\). TFAE:

1) There is \\(a_n\\) with \\(u_n=\Phi_{n}(a_0,\dots,a_n)\\)

2) \\(u_n \equiv \sigma(u_{n-1}) \mod p^n\\)

Hence \\(\Phi\\)'s image is the set of sequences \\((u_n)_{n \in \mathbf N}\\) where \\(\sigma(u_n) \equiv u_{n+1} \mod p^{n+1}\\).

_Proof_ Let's use the above observation. Existence of \\(a_n\\) is therefore equivalent to \\(u_n \equiv \Phi_{n-1}(a_0^p,\dots,a_{n-1}^{p}) \mod p^n\\). However, since each \\(a_i^p \equiv \sigma(a_i) \mod p \\) (by definition), \\(\Phi_{n-1}(a_0^p,\dots,a_{n-1^{p}}) \equiv \Phi_{n-1}(\sigma(a_0),\dots,\sigma(a_{n-1}))=\sigma_{n-1}(u_{n-1}) \mod p^n\\). So existence of \\(a_n\\) is equivalent to \\(u_n\equiv \sigma(u_{n-1}) \mod p^n \\), as claimed. \\(\square\\)

Now the above is very useful. Take \\(A = \mathbf Z[\mathbf X,\mathbf Y]=\mathbf Z[X_i,Y_i \mid i \in \mathbf N]\\), which has a lift of Frobenius determined by \\(X_i \mapsto X_i^p, Y_i \mapsto Y_i^p\\). The elements \\(\Phi_A(\mathbf X)+\Phi_A(\mathbf Y), \Phi_A(\mathbf X)\Phi_A(Y)\\) lie in \\(\Phi_A(A)\\) and so we find (unique!) polynomials \\((S_n),(P_n)\\) with \\(\Phi_A(S)=\Phi_A(\mathbf X) + \Phi_A(\mathbf Y)\\) and \\(\Phi_A(P)=\Phi_A(\mathbf X)\Phi_A(\mathbf Y)\\). Arguing similarly for \\(A=\mathbf Z[\mathbf X]\\) we find \\(I=(I_n)\\) with \\(\Phi_A(\mathbf I)=-\Phi_A(\mathbf X)\\).

We can use this `universal' case to define addition, multiplication and taking inverses on \\(W(A)\\) for _arbitrary_ \\(A\\): put \\(a{+}_{W(A)}b= S(\mathbf a,\mathbf b)\\) and \\(a \cdot_{W(A)}b= P(\mathbf a, \mathbf b)\\). [...]

**Theorem 9** The binary operations defined above provide \\(W(A)\\) with a ring structure such that \\(\Phi_A: W(A) \to A^\mathbf N\\) is a homomorphism.

_Proof_: This is a clever use of functoriality and `universal cases'. Let \\(B:=\mathbf Z[(X_a)_{a \in A}]\\). As usual, this has a lift of Frobenius \\(\sigma\\) and \\(p\\) is not a zero divisor, but there is also a natural surjection \\(\varphi:B \to A\\).

Now \\(\Phi_B:W(B) \to B^\mathbf N\\) is injective and its image is a subring of \\(B^\mathbf N\\). Corestricting \\(\Phi_B\\) to its image, we see that \\(W(B)\\) actually has the operations and identities transferred from \\(B^\mathbf N\\) along \\(\Phi_B\\), and so forms a ring itself.As for \\(A\\) itself, all relevant identities follow from those in \\(W(B)\\) via \\(W(\varphi))\\). \\(\square\\).


### Frobenius and Verschiebung

Thus far we've mostly neglected two pieces of extra structure. 

We first want to endow \\(W(A)\\) with a lift of Frobenius \\(F\\). We have \\(f_A:A^\mathbf N \to A^\mathbf N\\) which is a left shift. Again this gives \\(F\\) with \\(\Phi_A F_A = f_A \Phi_A\\).

**Proposition 10** \\(F_A\\) is a lift of Frobenius.

We omit the proof as it is similar to previous arguments: reduce to polynomial rings and check that \\(f_A\\) is a l.o.F. on \\(\Phi_A(A)\\).

So the Frobenius corresponds to a left shift in \\(\Phi_A(A)\\), but there is also a group endomorphism \\(W(A)\\) sending \\((a_i)_{i=0}^{\infty}\\) to \\((0,a_0,a_1,\dots)\\). Of course this is not a ring endomorphism (e.g. it doesn't preserve the identity); to see it is a group endomorphism, note that [...]

We can also see that \\(\Phi(F(\mathbf a))=(\Phi_n(0,a_0,\dots,a_{n-1}))_{n\in \mathbf N} = (p\Phi_{n-1}(a_0,\dots,a_{n-1}))_{n\in \mathbf N}= v_A(\Phi(\mathbf a)\\), where \\(v_A(\mathbf a)=(0,pa_0,pa_1,\dots)\\).

### A filtration and finite length vectors.

The Witt vectors have a natural filtration: let \\(V_n\\) be the set of sequences of the form \\((0,\dots,0,a_n, a_{n+1},\dots)\\). Then \\((V_n)_{n \in \mathbf N}\) is a descending filtration by ideals with \\(\bigcap_{n=0}^{\infty} V_n=0\\) and \\(V_0=W(A)\\).

Note that \\(V_n=V^n(A)\\) where \\(V\\) is the Verschiebung.

**Proposition 11** (Teichmüller lifts, take II)

Let \\(\tau:A \to W(A)\\) be the map sending \\(a \mapsto (a,0,0,\dots)\\). This map is multiplicative and \\(\sum_{n=0}^{\infty} V^n(\tau(x_n)) = x\\).

_Proof_ [...]

After one checks that \\(a_0,\dots,a_{n-1},0,\dots) + (0,\dots,0,a_n,a_{n+1},\dots)=(a_0,\dots,a_n,a_{n+1},\dots)\\), it follows that \\(W_n(A):=W(A)/V_n\\) is canonically in bijection with the set of sequences \\([a_0,\dots,a_{n-1}]\\) in \\(A^\mathbf N\\).

[...]

### Characteristic \\(p\\)

If \\(p=0\\) in \\(A\\), everything simplifies a lot. 

**Proposition** Let \\(A\\) be a ring wherein \\(p=0\\). Then \\(F(\mathbf a) = (a_i^{p^i})_{i=0}^{\infty})\\) and \\(VF=FV=[p]\\)

_Proof_ The first part is equivalent to saying \\(F_n \equiv X_n^p \mod p\\), which [...] Using this, second part is easy to see. \\(\square\\)

Let's now do important stuff...

**Proposition** Let \\(A\\) be a ring with \\(p=0\\).

1) \\(V_1(A)^k=p^{k-1}V_1(A)\\)

2) The \\(V_1(A)\\)-adic and \\(p\\)-adic topologies coincide, and \\(W(A)\\) is coomplete and separated.

_Proof_: 1) This foollowsf fromo \\(V_1(A)^2=p.V_1(A)\\).

2) Note \\(p.W(A)=VF(W(A)) \subseteq V(W(A))=V_1(A)\\), so \\(p^k.W(A)\subseteq p^{k-1}.V_1(A)}=(V_1)^k\\), whilst conversely [...] 

[...]







### `Universal' property

One thing is: fix \\(A\\). Suppoose we have a ring map \\(\varphi:B \to A\\) where \\(B\\) has a lift of Frobenius. If \\(B\\) is torsion-free, then there is a unique lift of \\(\varphi\\) along the projection \\(W(A)\to A\\) which commutes with the Frobenius lifts.






