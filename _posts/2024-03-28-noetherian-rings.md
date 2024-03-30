---
layout: post
title: "Noetherian rings and injective modules"
usemathjax: true
---

Today I wanted to talk about some algebra through trying to overkill a concrete problem and generalise the conclusion:

_Problem:_ Show that a \\( A:= \mathbf C[x]/x^2\\)-module is injective iff it is free.

There are a few ways to do this - for example, one can view a \\(\mathbf C[x]/x^2\\)-module as a \\(\mathbf C\\)-vector space equipped with a square-zero endomorphism. But if we try to find a slightly less _ad-hoc_ approach, we can learn more about Noetherian rings and injective modules in general.

# The 'Free implies injective' direction

The first thing to check, of course, is that \\(\mathbf C[x]/x^2\\) is self-injective (that is, injective regarded as a module over itself). This isn't bad if we recall Baer's criterion, and that \\(\mathbf C[x]/x^2\\) has only one non-trivial, proper ideal, namely \\(x\mathbf C[x]/x^2\\). All we need to do, then, is show that any map \\(x \mathbf C[x]/x^2 \to \mathbf C[x]/x^2\\) extends to \\(\mathbf C[x]/x^2\\), but all such maps are just multiplication by a scalar, so this is obvious.

Let's now generalise. It follows by general nonsense that any _product_ of injective modules is injective, and thus that any finite direct sum is injective. It isn't true for arbitrary direct sums in general though. Rather than give very specific counterexamples, it seems best just to establish the following theorem:

**Theorem**: TFAE for a (not necessarily commutative) ring \\(A\\):

1) A is left-Noetherian.

2) Arbitary direct sums of injective left A-modules are injective

3) _Countable_ direct sums of injective left A-modules are injective

_Proof_: (For brevity I'll stop saying `left' everywhere)

(1) \\(\to \\) (3): Suppose \\( A \\) is Noetherian and \\((M_i)_{i \in I}\\) some collection of injective \\(A\\)-modules; let \\(M\\) be their sum. 

According to Baer's criterion, it's enough to check that for any ideal \\(J\\) of \\(A\\) and any map \\(f: J \to M\\), we can find some extension \\(\bar{f}: A \to M\\). Fix any \\(J\\) and \\(f\\). Since \\(J\\) is finitely generated, any map \\(f: J \to M\\) will factor as \\( J \to \bigoplus_{i \in I'} M_i \subset \bigoplus_{i \in I} M_i\\) where \\(I'\\) is _finite_. Then we can extend the first map to \\(A\\) and we're done.

(2) \\(\to\\) (3) is trivial, so let's show that (3) \\(\to \\) (1). Suppose \\(J_0 \subset J_1 \subset \dots\\) is some ascending chain of ideals with union \\(J\\). We need to show that \\(J = J_n\\) for some \\(n\\). We can rephrase this as saying that \\(\bigoplus_{n \in \mathbf N}J/J_n\\) is a finite \\(A\\)-module.

Now there's a map \\(\phi: J \to \bigoplus_{n} J/J_n\\) given by \\(j \mapsto {(j + J_n)} \\); note this is well-defined since \\(j \in J_n\\) for \\(n \gg 0\\). We can include each \\(J/J_n\\) in some _injective_ \\(A\\)-module \\(V_n\\), and then, by our hypotheses, \\(\bigoplus_{n} J/J_n\\) embeds in the _injective_ module \\(\bigoplus_n V_n \\). 

We can then extend \\( J \to \bigoplus_n V_n\\) to \\(A\\). But \\(1\\) - and hence all of \\(A\\) - must map into \\(\bigoplus_{n=1}^{N} V_n\\) for some \\(N\\), and so \\(\phi\\) has image contained in \\(\bigoplus_{n \le N}\\). That is, \\(J_N = J\\). \\(\blacksquare\\)

In particular, (1) \\(\to\\) (3) finishes off one direction of our original statement.

# 'Injective implies free'

There are actually a couple of ways to go about this bit which connect to more general theory.

Let's do a first approach, which feels more like doing the obvious thing.

A good place to start is this. Suppose \\(M\\) is an injective \\(A\\)-module (\\(A\\) any ring). We can find a maximal linearly independent subset of \\(M\\), spanning a maximal free submodule \\(F \subset M\\). \\(F\\) is what is called an essential submodule:

**Definition**: An inclusion \\(V \subset W\\) of submodules is called an _essential_ extension if every non-zero submodule \\(W' \subset W\\) intersects \\(V\\) non-trivial.

Analogously one defines essential submodules, monomorphisms, etc.

_Example_: For any domain \\(A\\), \\(A\\) is an essential \\(A\\)-submodule of \\(\mathrm{Frac}(A)\\). Other the other hand, \\(\mathbf Q\\) is not an essential \\(\mathbf Q\\)-submodule of \\(\mathbf Q(\sqrt{2}\\). 

Why is \\(F\\) an essential submodule of \\(M\\)? Well suppose \\( \\mathscr B = \\{\omega_i\\}\\) is a basis of \\(F\\) and \\(m \in M \setminus \\{0\\}\\). By definition of \\(F\\), \\( \mathscr B \cup \\{m\\}\\) is linearly dependent. So there's \\(a \in A\\) such that \\(am\\) is a non-trivial linear combination of elements of \\(\mathscr B\\), and thus a non-zero element of \\(A.m \cap F\\).

Essential extensions link to injective modules via the following simple proposition:

**Proposition**: Suppose \\( M \subset N\\) is an essential extension of \\(A\\)-modules and that \\(M\\) is injective. Then \\(M=N\\).

_Proof_: Injectivity implies \\(M\\) is actually a direct summand of \\(N\\). If the complement is non-trivial, then we contradict essentiality. \\(\blacksquare\\)

Hence if we combine the previous two bits, we see any injective \\(\mathbf C[x]/x^2\\)-module is an essential extension of an injective module, and hence injective itself. Voilá. 

In fact, more generally, we have seen that every injective \\(A\\)-module is free if \\(A\\) is self-injective and Noetherian. Conversely, if every injective \\(A\\)-module is free, then \\(A\\) is self-injective, being a summand of an injective module. 

# A classification theorem
We can now try an alternative approach, which generalises slightly further. A nice reference for this is Stacks project (3.47.5), though my proofs are a little different.

The theorem I want to show is this:

**Theorem**: Let \\(A\\) be a commutative Noetherian ring.

(1) Any injective module over \\(A\\) is a direct sum of _indecomposable_ injective modules.

(2) Any indecomposable injective \\(A\\)-module is the injective hull of the residue field \\(\kappa(\mathfrak p)\\) of some prime \\(\mathfrak p \subset A\\).

We first need to define one of the terms used above:

**Definition**: Let \\(A\\) be a ring and \\(M\\) an \\(A\\)-module. Then an _injective hull_ of \\(M\\) is an injective \\(A\\)-module \\(N\\) equipped with a essential mono \\(M \hookrightarrow N\\).

**Proposition:** Fix a ring \\(A\\). 

(1) Every left \\(A\\)-module \\(M\\) has an injective hull.

(2) Any two injective hulls of \\(M\\) are isomorphic.

_Proof_

(1). Given \\(M\\) a module, pick an embedding \\(M \subset I\\) into an injective module. Consider the poset of modules \\(M'\\) with \\(M \subset M' \subset I\\) such that \\(M \to M'\\) is essential. A standard Zorn's argument shows that this poset has a maximal element \\(E\\). 

We want to show this is injective and will use the observation that \\(E\\) has no proper essential extensions. Any such module is injective. Indeed embed \\(E\\) into an injective module \\(E'\\) and suppose \\(E \to E'\\) is not an iso. Then \\(E \subset E'\\) is not essential, so there's \\(N \subset E'\\) such that \\(N \cap E = 0\\). By another Zorn's argument, assume \\(N\\) is maximal with respect to this property. This is equivalent to saying \\(E \hookrightarrow E'/N\\) is essential and hence an isomorphism. This means \\(E' = E \oplus N\\) and thus \\(E\\) is a direct summand of an injective module - and so injective in its own right.

(2) Suppose we pick _two_ injective hulls \\(M \hookrightarrow E\\) and \\(M \hookrightarrow E'\\). Injectivity of \\(E,E'\\) gives us a map \\(\varphi: E \to E'\\) compatible with the embeddings of \\(M\\). But, being an extension of \\(M \hookrightarrow E'\\), we know \\(\ker \varphi \cap M = 0\\) and thus \\(\ker \varphi = 0 \\) since \\(M \hookrightarrow E\\) is essential. So we may view the situation as \\(M \subset E \subset E'\\). Now \\(E\\) is a direct summand of \\(E'\\), which contradicts the fact \\(M \to E'\\) is essential unless \\(E = E'\\) \\(\blacksquare\\).

Now suppose \\(M\\) is an indecomposable, injective \\(A\\)-module.

Let \\(B\\) be the endomorphism ring of \\(M\\), and \\(I \subset B\\) the set of non-injective endomorphisms. It's not hard to see that \\(I\\) is two-sided, and that every element of \\(B \setminus I\\) is invertible. So* its preimage \\(\mathfrak p\\) under the canonical map \\(A \to B\\) is prime, and the canonical map \\(A \to B\\) extends to \\(A_\mathfrak p \to B\\) so that \\(M\\) is canonically an \\(A_\mathfrak p\\)-module.

Now \\(\mathfrak p\\) is f.g. by hypothesis; say it's generated by \\(\omega_1,\dots,\omega_n\\). Then \\(\bigcap_i \ker(\omega_i: A \to A\) \ne 0\\) and so we can find some \\(y\\) killing \\(\mathfrak p\\). Then \\(x. A_\mathfrak p \subset M\\) is a \\(A_\mathfrak p\\)-submodule isomorphic to \\(\kappa(\mathfrak p)\\), and \\(M\\) is the injective hull of \\(\kappa(\mathfrak p)\\).

We now want to prove that the promised decomposition into injective indecomposables exists. This will be a pretty standard argument Zorn's lemma argument, but to get it off the ground we need the following:

_Lemma_: Every non-zero injective module \\(M\\) over a Noetherian ring \\(A\\) has a non-zero injective indecomposable submodule \\(M'\\), which is the injective hull of \\(\kappa(\mathfrak p)\\) for some prime \\(\mathfrak p \\).

_Proof_: Let \\(A,M\\) be as given. As \\(M \ne 0 \\), it has an associated prime \\(\mathfrak p \\) (that is, there is \\(m \in M\\) such that \\(\mathfrak p := \mathrm{Ann}(m)\\) is prime). Then \\(A/\mathfrak p \simeq mA \subset M\\). 

Now let \\(M'\\) be the injective hull of \\(A/\mathfrak p\\), which we know embeds in \\(M\\) since \\(M\\) is injective. \\(A/\mathfrak p \subset \kappa(\mathfrak p )\\) is essential by an earlier example, so in fact \\(M'\\) is the injective hull of \\(\kappa(\mathfrak p)\\) too. 

We're now reduced to showing the following: for any prime \\(\mathfrak p \subset A\\), the injective hull \\(E (= M' \\) in the above) of \\(A/\mathfrak p \\) is indecomposable.

This isn't toobad though. Suppose for contradiction that \\(E = E' \oplus E''\\) where \\(E' \ne 0 \ne E''\\). Then on one hand, \\(0 = (A/\mathfrak p \cap E') \cap (A/\mathfrak p \cap E'')\\). On the other hand, \\(A/\mathfrak p \subset E\\) is essential so \\(A/\mathfrak p \cap E'\\) and \\(A/\mathfrak p \cap E''\\) are both non-zero. Submodules of \\(A/\mathfrak p\\) correspond to ideals of \\(A\\) containing \\(\mathfrak p\\), and our situation translates to \\(\mathfrak p\\) being an intersection of two strictly larger ideals, a contradiction.  \\(\blacksquare\\)

_Finishing off_: 

Finally,let \\(S\\) be set of all submodules of \\(I\\) which are direct sums of indecomposable injective modules. By the lemma, \\(S \ne \emptyset\\).

One checks, using injectivity and indecomposability, that the union of any well-ordered subset of \\(S\\) is still in \\(S\\), so that by Zorn's, there's a maximal element \\(I'\in S\\).

Suppose \\(I'\\) is properly contained in \\(I\\). \\(I'\\) is injective by earlier work, so \\(I = I' \oplus I''\\) for some \\(I'\'\ne 0\\). Then, applying the lemma again, \\(I''\\) has a on-zero indecomposable injective submodule \\(I'''\\) and \\(I \oplus I''' \in S\\) is strictly larger than \\(I\\), a contradiction. \\(\blacksquare\\).

_Applying to the original problem_

Okay, now we have this classification, we can sledgehammer our original problem. Note \\(A:=\mathbf C[x]/x^2\\) has exactly one prime ideal, namely \\(Ax\\), and the residue field is \\(A/(x) \simeq Ax\\). The injective hull is \\(A\\), and our classification theorem then tells us every injective \\(A\\)-module is free. 

