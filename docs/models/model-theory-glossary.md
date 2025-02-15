## Model Theory Reference
$\def\bfall{\boldsymbol{\forall}}\def\bfex{\boldsymbol{\exists}}$
This is essentially a glossary of the most basic and important model theory concepts along with some elementary facts about them.

---

### Signatures, Languages, Terms, Formulas, Sentences

#### Signatures
+ A **signature** $\sigma = (\mathbf{C}, \mathbf{F}, \mathbf{R}, \sigma')$ consists of
  three (possibly empty) sets $\mathbf{C}$, $\mathbf{F}$, and $\mathbf{R}$ of *constant*, *function*, and *relation* symbols (resp.), along with a function 
  $\sigma': \mathbf{C} + \mathbf {F} + \mathbf{R} \to \mathbb N$ that assigns an *arity* to each symbol.

---

#### Languages
+ The **language** $L = L(\sigma)$ of signature $\sigma$ is a certain collection of strings of symbols from the following **alphabet** of symbols:
  - **logical symbols** 
    + *logical connectives*: $\neg$ ,  $\wedge$ , $\vee$ (resp. "negation," "conjunction," "disjunction), 
    + *existential quantifier:* $\exists$
    + *equality*: $=$ 
  - **variables** (countably many)
  - **non-logical symbols** from $\sigma$ (the constant, function, and relation symbols)
  - **parentheses** ( and )  

  To specify which strings of symbols belong to $L$, we need to define the *terms* and *formulas* of $\sigma$. Eventually, we will define $L$ to be *the set of all $\sigma$-formulas.*

---
  
#### Terms
The **terms** of signature $\sigma$ (aka $\sigma$-**terms**) are defined recursively as follows:
- All variables are terms.
- All constant symbols are terms.
- If $t_0, \dots, t_{n-1}$ are terms and $f\in \mathbf F$ with $\sigma'(f) = n$,
  then $f(t_0,\dots, t_{n-1})$ is a term.
- $t$ is a terms if it can be obtained in finitely many steps from some combination of the three items above.

---

#### Formulas
The **formulas** of $\sigma$ (aka $\sigma$-formulas) are defined recursively as follows:
- If $t_1$ and $t_2$ are $\sigma$-terms, then $t_1 = t_2$ is a $\sigma$-formula.
- If $t_0,\dots, t_{n-1}$ are $\sigma$-terms and $R \in \mathbf R$ with $\sigma'(R)=n$, then $R(t_0,\dots, t_{n-1})$ is a $\sigma$-formula.
- If $\varphi$ and $\psi$ are $\sigma$-formulas and $x$ is a variable, then
  $\neg \varphi$, $\varphi \wedge \psi$, and $\exists x \varphi$ are formulas too.
- $\varphi$ is a fornıula if it can be obtained in finitely many steps from some combination of the three items above.

Finally, we can define 
+ The **language** $L = L(\sigma)$ is the set of all $\sigma$-formulas.

---

#### Sentences
+ A term $t$ is said to be **constant** (or **closed**) if it contains no variables.
+ A formula $\varphi$ is called a **sentence** (or **closed formula**) if it contains *no __free__ variables*; that is, all variables appearing in $\varphi$ are bound;
+ $L_0 :=$ all sentences in the language $L$ (aka "$L$-sentences");
+ An **atomic** $L$-formula has one of the following two forms:
  - $s = t$, where $s$ and $t$ are $L$-terms;
  - $R(t_0, \dots, t_{n-1})$, where $R$ is an relation symbol in $L$ and $t_i$ are $L$-terms;
+ $\mathbf{at}_L$ (or just $\mathbf{at}$ when the context makes $L$ clear) is the class of all atomic $L$-formulas.
+ An **atomic** $L$-sentence is either an equation of constant terms or a relational sentence, $R(t_0, \dots, t_{n-1})$, where all $t_i$ are closed terms;
+ A **literal** $L$-formula (or, $L$-**literal**) is an atomic or negated atomic $L$-formula; 
+ $\mathbf{lt}_L:=$ the set of all $L$-**literals**; that is, $\mathbf{at}_L \cup \{\neg \varphi : \varphi \in \mathbf{at}_L\}$;
+ $\mathbf{cl}_L:=$ the set of all **closed** $L$-**literals** (literal $L$-sentences; that is, literals without free variables).


**Remarks.**
+ Every constant symbol is a constant term.
+ An atomic sentence contains no variables at all.
+ *Languages without constant symbols have no atomic sentences.*
+ Every language comes equipped with a countable supply of variables, so the cardinality of $L$ is $|L| = \max \{\aleph_0, |\mathbf C \cup \mathbf F \cup \mathbf R|\}$.

---
#### Boolean comibinations and quantifier-free formulas
Let $\Sigma$ be a set of formulas. 

+ A **boolean combination** of formulas from $\Sigma$ is obtained by connecting formulas from $\Sigma$ using only the logical connectives; i.e., only $\vee$, $\wedge$, $\neg$.

+ A **positive boolean combination** of formulas from $\Sigma$ is obtained by connecting formulas from $\Sigma$ with only $\wedge$ and $\vee$. 

+ The **boolean closure** of $\Sigma$ is the set $\tilde{\Sigma}$ of all boolean combinations of formulas from $\Sigma$.

+ A **positive** formula is obtained from atomic formulas using
only $\wedge$, $\vee$, $\exists$, $\forall$.   
The class of all positive formulas (of all possible languages) is denoted by $\boldsymbol{+}$.

+ A **negative** formula is a negated positive formula. The class of all such
is denoted by $\boldsymbol{-}$.

+ A **quantifier-free** formula is one that contains no quantifiers; we 
  assume $\top$ and $\perp$ are quantifier-free.  
  The class of all quantilier-free formulas (of arbitrary signature) is denoted by $\mathbf{qf}$.

**Remarks.** 
+ In the definition of boolean combinations, we could allow $\to$ and $\leftrightarrow$; we could do without $\vee$.
+ $\mathbf{qf}$ is the class of all boolean combinations of atomic formulas.


---

#### Expansion by Constants, Validity, Truth

Fix a signature $\sigma = (\mathbf{C}, \mathbf{F}, \mathbf{R}, \sigma')$ and a language $L = L(\sigma)$ (i.e., $L$ is a language of signature $\sigma$). Let $\mathcal M = \langle M, \dots\rangle$ and $\mathcal N = \langle N, \dots\rangle$ be $L$-structures, let $\mathbf x = (x_0, x_{1}, \dots)$ be a tuple of variables, and let $\varphi = \varphi(\mathbf x)$ be an $L$-formula.

##### Expansion by Constants
+ A **new constant** (**symbol**) for $L$ is any symbol not occuring in the alphabet of $L$.
+ $L(C)$ is the **expansion** of $L$ by new constant symbols $C$, and is defined to be the (uniquely determined) language of signature $(\mathbf C \cup C, \mathbf F, \mathbf R, \sigma')$.
+ $\Delta(C)$ is the **expansion** of $\Delta$ by new constants symbols $C$ (not occuring in $\Delta$) and is defined to be the class of all the formulas obtained from formulas $\varphi \in \Delta$ upon substituting (at will) elements from $C$ for variables in $\varphi$. ("At will" indicates that $\Delta\subseteq \Delta(C)$.)
+ $\mathbf{lt}_{L(M)}:=$ the set of all atomic and negated atomic $L(M)$-formulas.
+ $\mathbf{cl}_{L(M)}:=$ the set of all atomic and negated atomic $L(M)$-setnences.

##### Validity and Truth

+ $\mathcal M \vDash \varphi$ means that $\varphi$ is **valid** in $\mathcal M$ which means that for every tuple $\mathbf a  = (a_0, a_1, \dots )$ from $M$ (that is at least as long as $\mathbf x$) the $L$-sentence $\varphi(\mathbf a)$ is *true in $\mathcal M$*. 

*What exactly do we mean by "$\varphi(\mathbf a)$ is true in $\mathcal M$?"*

Intuitively, for each $i$ we subsitute the element $a_i$ for the variable $x_i$ in the formula $\varphi(\mathbf x)$, which yields a sentence $\varphi(\mathbf a)$ that is "decidable" in $\mathcal M$. That is, there is a finite procedure by which we can determine whether or not $\varphi(\mathbf a)$ holds (or is "true") in $\mathcal M$.

Formally, however, we may follow a more careful procedure for judging the truth of a given formula $\varphi$ in a given structure $\mathcal M = \langle M, \dots\rangle$.  This is the simple matter of how syntactically to denote interpretation of variables.  But as Hodges puts it, this is "one of the more irksome parts of model theory." 

The issue is explained clearly in Section 1.4 of Hodges, "Model Theory," so we defer to that presentation:

+ The conventions for interpreting variables are one of the more irksome parts
  of model theory. We can avoid them, at a price. Instead of interpreting a
  variable as a name of the element $b$, we can add a new constant for $b$ to 
  the signature. The price we pay is that the language changes every time another
  element is named. When constants are added to a signature, the new
  constants and the elements they name are called parameters. 

  Suppose for example that $\mathcal A$ is an $L$-structure, $\mathbf a$ is a sequence of elements of $\mathcal A$, and we want to name the elements in $\mathbf a$. Then we choose a sequence $\mathbf c$ of distinct new constant symbols, of the same length as $\mathbf a$, and we form the signature $L(\mathbf c)$ by adding the constants $\mathbf c$ to $L$. Then $(\mathcal A, \mathbf a)$ is an $L(\mathbf c)$-structure, and each element $a_i$ is $c_i^{(\mathcal A, \mathbf a)}$.
  
  Likewise if $\mathcal B$ is another $L$-structure and $\mathbf b$ a sequence of elements of $\mathcal B$ of the same length as $\mathbf c$, then there is an $L(\mathbf c)$-structure $(\mathcal B, \mathbf b)$ in which these same constants $c_i$ name the elements of $\mathbf b$. The next lemma is about this situation. It comes straight out of the definitions, and it is often used silently.

  **Lemma** [1.4.1. Hodges] Let $\mathcal A$, $\mathcal B$ be $L$-structures and suppose $(\mathcal A, \mathbf a)$, $(\mathcal B, \mathbf b)$ are $L(\mathbf c)$-structures. Then a homomorphism $f \colon (\mathcal A, \mathbf a) \to (\mathcal B, \mathbf b)$ is the same thing as a homomorphism $f \colon \mathcal A \to \mathcal B$ such that $f[\mathbf a] = \mathbf b$.
  
In the situation above, if $t(\mathbf x)$ is a term of $L$, then $t^{\mathcal A}(\mathbf a)$ and $t(\mathbf c)^{(\mathcal A, \mathbf a)}$ are
the same element; and if $\varphi(\mathbf x)$ is an atomic formula then 
$\mathcal A \vDash \varphi_{\mathbf x}(\mathbf a) \; \Leftrightarrow \;
(\mathcal A, \mathbf c) \vDash \varphi_{\mathbf x}(\mathbf c)$.

**Notation** (used above) $f[\mathbf a]$ is shorthand for $(f(a_0), f(a_1), \dots)$ and $\varphi_{\mathbf x}(\mathbf a)$ is shorthand for $[a_0/x_0, a_1/x_1, \dots]\varphi(x_0, x_1, \dots)$, the sentence obtained from $\varphi$ upon substituting $a_i$ for $x_i$, for each $i$.

---
### Models, Theories, Diagrams
Let $\varphi \in L_0$, $\Sigma\subseteq L_0$, and let $\mathcal M = \langle M, \dots\rangle$ and $\mathcal N = \langle N, \dots\rangle$ be $L$-structures. Let $\Delta$ be an arbitrary class of formulas (not necessarily from $L$).


#### Models

+ If $M\neq \emptyset$ and $\mathcal M \vDash \Sigma$, then $\mathcal M$ is a **model** of $\Sigma$; we also say "$\mathcal M$ *models* $\Sigma$."
+ $\operatorname{Mod}_L \Sigma :=$ the class of $L$-structures that model $\Sigma$.
+ $\operatorname{Mod}_L \emptyset :=$ the class of all nonempty $L$-structures.
+ $\Sigma$ **entails** $\varphi$, denoted $\Sigma \vdash \varphi$, if every model of $\Sigma$ also models $\varphi$.
+ $\varphi$ is a **logical consequence** of $\Sigma$ means $\Sigma$ entails $\varphi$.
+ The **deductive closure** of $\Sigma$ is the set $\Sigma^{\vdash} = \{\varphi \in L_0 : \Sigma \vdash \varphi\}$ of logical consequences of $\Sigma$.
+ $\Sigma$ **deductively closed** if $\Sigma^\vdash \subseteq \Sigma$.
+ $\Sigma_0, \Sigma_1 \subseteq L_0$ are $\Sigma$-**equivalent** if $(\Sigma \cup \Sigma_0)^\vdash = (\Sigma \cup \Sigma_1)^\vdash$.
+ **logically equivalent** means $\emptyset$-equivalent.
+ A **contradiction** is an $L$-sentence of the form $\varphi \wedge \neg \varphi$.
+ $\Sigma$ is **consistent** if $\Sigma^\vdash$ contains no contradictions; otherwise, $\Sigma$ is **inconsistent**.  
  **Remark.** No model satisfies a contradiction, so the deductive closure of a contradiction is the set $L_0$ of all $L$-sentences, and $L_0$ is the only deductively closed inconsistent set of $L$-sentences.

---
#### Theories
+ An $L$-**theory** is a *consistent* and *deductively closed* set of $L$-sentences.
+ The **cardinality** or **power** of an $L$-theory $T$ is denoted $|T|$ and defined to be the cardinality of $L$.
+ $T_\Delta = (T \cap \Delta)^\vdash$ is the $\Delta$-**part** of the $L$-theory $T$ (here $\Delta$ is an arbibtrary class of formulas).
+ $\bfall$ is the class of formulas in which $\exists$ does not appear; $T_{\bfall} = (T \cap \bfall)^\vdash$ is the *universal part* of $T$.

+ $\operatorname{Th}_\Delta \mathcal M := \{\varphi \in L_0 : \varphi \in \Delta,\; \mathcal M \vDash \varphi\}=$ all $L$-sentences in $\Delta$ that are true in $\mathcal M$.
+ $\operatorname{Th} \mathcal M := \operatorname{Th}_{L_0} \mathcal M =$ all $L$-sentences that are true in $\mathcal M$.
+ An $L$-theory $T$ is **complete** if for all $\varphi\in L_0$, either $\varphi \in T$ or $\neg\varphi\in T$.  
**Lemma 3.5.1.** If $T$ is an $L$-theory, the following are equivalent:
  1. $T$ is complete.
  2. $T$ is a maximal $L$-theory.
  3. $T$ is a maximal consistent set of $L$-sentences.
  4. $T= \operatorname{Th}\mathcal M$ for all $\mathcal M \vDash T$.
  5. $T= \operatorname{Th}\mathcal M$ for some $\mathcal M \vDash T$.
+ **Examples.**
  - $T^\infty$ is the theory of the class of all infinite models of $T$.
  - $T_=$ is the **theory of pure identity**, which is the $L_=$-theory of all sets (regarded as $L_=$-structures).

---
#### Diagrams
+ The **diagram** of $\mathcal M$ is the set $D(\mathcal M) := \mathbf{cl}_{L(M)}$ of all atomic and negated atomic $L(M)$-sentences; 
+ $\mathcal M \Rrightarrow_{\Delta} \mathcal N$ means $\mathcal M \vDash \varphi$ implies $\mathcal N \vDash \varphi$ for all $\varphi \in \Delta \cap L_0$.
+ $\mathcal M \Rrightarrow \mathcal N$ means $\mathcal M \Rrightarrow_{L} \mathcal N$.
+ $\mathcal M \equiv \mathcal N$ means $\mathcal M \Rrightarrow \mathcal N$ and $\mathcal M \Lleftarrow \mathcal N$ hold, and this is equivalent to $\operatorname{Th} \mathcal M = \operatorname{Th} \mathcal N$.   
We call $\mathcal M$ and $\mathcal N$ **elementarily equivalent** in this case.
+ $f \colon \mathcal M \hookrightarrow \mathcal N$ means 
$f$ is an $L$-structure-monomorphism from $\mathcal M$ to $\mathcal N$.
+ $f \colon \mathcal M \stackrel{\Delta}{\longrightarrow} \mathcal N$ means all $L$-formulas in $\Delta$ are preserved by $f$.  That is,   
$\mathcal M \vDash \varphi(\mathbf a)$ implies  $\mathcal N \vDash \varphi(f[\mathbf a])$, for all $\varphi \in \Delta\cap L$ and all tuples $\mathbf a$ from $M$. 
+ $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$ means 
$f \colon \mathcal M \stackrel{L}{\longrightarrow} \mathcal N$.  

---

**Facts.** Let $\mathcal M$ and $\mathcal N$ be $L$-structures and let $\Delta$ be a set of $L$-formulas.
1. $f \colon \mathcal M \stackrel{\mathbf{at}}{\longrightarrow} \mathcal N$iff $f \colon \mathcal M \rightarrow \mathcal N$ 
2.  $f \colon \mathcal M \stackrel{\Delta}{\longrightarrow} \mathcal N$ iff $(\mathcal M, M) \Rrightarrow_{\Delta(M)} (\mathcal N, f[M])$.
3. If $f \colon \mathcal M \stackrel{\Delta}{\longrightarrow} \mathcal N$ and $\Delta$ contains $\mathbf{at}$ and all negations of
   unnested relational atomic formulas, then
   $f$ is a strong homomorphism. (The converse is not true.)
4. If 
   $f \colon \mathcal M \stackrel{\Delta}{\longrightarrow} \mathcal N$ 
   and $\Delta$ is closed under negation, then $\mathcal M \vDash \varphi(\mathbf a)$ implies $\mathcal N \vDash \varphi(f[\mathbf a])$, for all $\varphi \in \Delta$ and tuples $\mathbf a$ from $M$.
5. $f \colon M \to N$ is injective iff 
   $f \colon \mathcal M \stackrel{\Delta}{\longrightarrow} \mathcal N$ for the set $\Delta = \{x \neq y\}$.
6. If $\Delta \subseteq L_0$, then
   $f \colon \mathcal M \stackrel{\Delta}{\longrightarrow} \mathcal N$ iff $\mathcal M \Rrightarrow_{\Delta} \mathcal N$ and $f \colon M \to N$.
7. If $\Delta \subseteq L_0$  and $\Delta$ is closed under negation, then $\mathcal M \Rrightarrow_\Delta \mathcal N$ implies $\mathcal M \equiv_\Delta \mathcal N$.

---

#### The Lemma on Constants

Above we remarked that if $(\mathcal A, \mathbf a)$ is an $L(\mathbf c)$-structure with $\mathcal A$ an $L$-structure, then for every atomic formula $\varphi$ of $L$, $\mathcal A \vDash \varphi(\mathbf a)$ if and only if $(\mathcal A, \mathbf a) \vDash \varphi(\mathbf c)$.

**Lemma** [2.3.2. Hodges] Let $L$ be a language, $T$ a theory in $L$ and $\varphi(\mathbf x)$ a formula in $L$. Let $\mathbf c$ be a sequence of distinct constants that are not in $L$. Then $T \vdash \varphi(\mathbf c)$ if and only if $T \vdash \forall \mathbf x\, \varphi$.

---

#### The Diagram Lemma

**Lemma** [6.1.2. Rothmaler] Let $\mathcal M$ and $\mathcal N$ be $L$-structures.
1. $f \colon \mathcal M \hookrightarrow \mathcal N$ $\; \Leftrightarrow \;$ 
   $f \colon \mathcal M \stackrel{\mathbf{qf}}{\longrightarrow} \mathcal N$
   $\; \Leftrightarrow \;$ $(\mathcal N, f[M]) \vDash D(\mathcal M)$.  
   In particular, $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N \; \Rightarrow \; f \colon \mathcal M \hookrightarrow \mathcal N$.

2. $\mathcal M \hookrightarrow \mathcal N$ $\; \Leftrightarrow \;$ $\mathcal N$ has an $L(M)$-expansion that models $D(\mathcal M)$.

---

#### The Diagram Lemma (ver. 2)

Let's consider an alternative version of the Diagram Lemma that makes the role played by new constants more explicit. For this version, we will use the following additional notation:

+ $\mathbf c = (c_0, \dots, c_{n-1})=$ an arbitrary tuple of distinct symbols not appearing in $L$; 
+ $\mathbf a = (a_0, \dots, a_{n-1}) \in M^n$, $\mathbf b = (b_0, \dots, b_{n-1}) \in N^n$; 
+ $(\mathcal M, \mathbf c)$ and $(\mathcal N, \mathbf c)$ are $L(\mathbf c)$-structures, where $c_i^{\mathcal M} = a_i$ and $c_i^{\mathcal N} = b_i$ are the interpretations in $\mathcal M$ and $\mathcal N$ of the new constant symbols;
+ $\langle \mathbf a \rangle$ is the substructure of $\mathcal M$ generated by the elements of the tuple $\mathbf a$;
+ $f[\mathbf a]:=(f(a_0), \dots, f(a_{n-1}))$.


**Lemma** [1.4.2. Hodges] The following are equivalent:  
1. For every atomic sentence $\varphi(\mathbf c)$ of $L(\mathbf c)$, if 
   $(\mathcal M, \mathbf c) \vDash \varphi(\mathbf c)$ then $(\mathcal N, \mathbf c) \vDash \varphi(\mathbf c)$.
2. There is a homomorphism $f \colon \langle \mathbf a \rangle \to \mathcal N$ such that $f[\mathbf a] = \mathbf b$.  
3. The homomorphism in 2 is unique, if it exists, and it is an embedding if and only if:  
   for every atomic sentence $\varphi$ of $L(\mathbf c)$, we have 
   $(\mathcal M, \mathbf c) \vDash \varphi \; \Leftrightarrow \; (\mathcal N, \mathbf c) \vDash \varphi$.

---

### Elementary equivalence

#### Isomorphic structures are elementarily equivalent

**Proposition** [6.1.3. Rothmaler]
If $f \colon \mathcal M \cong \mathcal N$, then $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$, hence also $\mathcal M \equiv \mathcal N$.

Proof of the first implication is on page 70 of the text. 

The second implication is $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$ implies $\mathcal M \equiv \mathcal N$.  That's true because, if $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$, then we have not only $\varphi \in \operatorname{Th} \mathcal M$ implies $\varphi \in \operatorname{Th}\mathcal N$, 
but also $\neg \varphi \in \operatorname{Th} \mathcal M$ implies $\neg \varphi \in \operatorname{Th}\mathcal N$.
From the former, $\mathcal M \Rrightarrow \mathcal N$.  From the latter,
$\mathcal M \Lleftarrow \mathcal N$.  Thus, $\mathcal M \equiv \mathcal N$.

---

The converse of 6.1.3 holds if and only if the structures involved are finite, as the next proposition shows.

**Proposition** [8.1.1. Rothmaler] Let $\mathcal M$ be an $L$-structure. The following are equivalent:
1. $\mathcal N \equiv \mathcal M$ implies $\mathcal N \cong \mathcal M$ for any $L$-structure $\mathcal N$.
2. $\mathcal M$ is finite.

---

#### All models of a complete theory are elementarily equivalent

**Proposition** [8.1.2. Rothmaler] A theory is complete iff its models are elementarily equivalent.

**Corollary** [8.1.3. Rothmaler] A complete theory has a finite model iff it has only one model (up to isomorphism).

---

### Elementary maps
Let $\mathcal M$ and $\mathcal N$ be $L$-structures. A map $f \colon M \to N$ is called **elementary** if $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$.  The structure $\mathcal M$ is **elementarily embeddable** in $\mathcal N$, in symbols $\mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$, if there is an elementary map $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$.

**Remarks.**  
1. If $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$, then $\mathcal M \equiv \mathcal N$.
2. While elementary equivalence is weaker than isomorphism, every elementary map is automatically an isomorphic embedding (by Lemma 6.1.2(1)). Therefore elementary maps are also called **elementary embeddings**, and the notation $f \colon \mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$ is justified.
3. The converse is not true in general, unless the embedding is surjective
(i.e., an isomorphism), since
4. Proposition 6.1.3 says that every isomorphism $f \colon \mathcal M \cong \mathcal N$ is an elementary map.

---

#### Elementary Diagram Lemma
The **elementary diagram** of an $L$-structure $\mathcal M$ is the complete $L(M)$-theory $\operatorname{Th}(\mathcal M, M)$.

**Lemma** [8.2.1. Rothmaler] Let $\mathcal M$ and $\mathcal N$ be $L$-structures and $f \colon M \rightarrow N$.
1. $f$ is elementary $\; \Leftrightarrow \;$  $(\mathcal M, M) \equiv (\mathcal N, f[M])$ $\; \Leftrightarrow \;$ 
$(\mathcal N, f[M]) \vDash Th(\mathcal M, M)$.
2. $\mathcal M \stackrel{\equiv}{\hookrightarrow} \mathcal N$ 
   $\; \Leftrightarrow \;$ iff 
   $\mathcal N$ has an expansion that is a model of $\operatorname{Th}(\mathcal M, M)$.
