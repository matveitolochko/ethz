<style>
.katex-flalign .katex-display {
    text-align: left !important;
}
.katex-flalign .katex-display>.katex {
    text-align: left !important;
}
</style>

$$
\global\def\sub#1{ _#1 }
\global\def\space{ ~ }
\global\def\rel#1{\space #1 \space}
$$

# DiskMat CheatSheet

## Logic

<div class="katex-flalign">

$$
\begin{align*}
    \lnot \lnot A &\equiv A &\textit{(Double Negation)} \\
    A \land A &\equiv A &\textit{(Idempotence)} \\
    A \lor  A &\equiv A\\
    A \land B &\equiv B \land A &\textit{(Commutativity)} \\
    A \lor  B &\equiv B \lor  A\\
    (A \land B) \land C &\equiv A \land (B \land C) &\textit{(Associativity)}\\
    (A \lor  B) \lor  C &\equiv A \lor  (B \lor  C)\\
    A \land (A \lor  B) &\equiv A &\textit{(Absorption)}\\
    A \lor  (A \land B) &\equiv A\\
    A \land (B \lor  C) &\equiv (A \land B) \lor  (A \land C) &\textit{(First distributive law)}\\
    A \lor  (B \land C) &\equiv (A \lor  B) \land (A \lor  C) &\textit{(Second distributive law)}\\
    \lnot (A \land B) &\equiv \lnot A \lor  \lnot B &\textit{(De-Morgan's law)}\\
    \lnot (A \lor  B) &\equiv \lnot A \land \lnot B \\
\end{align*}
$$
</div>

**Quantifier Logic Rules**:

<div class="katex-flalign">

$$
\begin{align*}
\lnot (\forall x: P) &\equiv \exists x: (\lnot P) \\
\lnot (\exists x: P) &\equiv \forall x: (\lnot P) \\
\forall x:(P \land Q) &\equiv (\forall x:P) \land (\forall x:Q) \\
{\color{teal} \exists x:(P \land Q)}  &\models {\color{violet} (\exists x:P) \land (\exists x:Q)} \\
{\color{violet} (\exists x:P) \land (\exists x:Q)} &\not\models {\color{teal} \exists x:(P \land Q)} \\
{\color{green} \exists y: (\forall x: P(x, y))} &\models {\color{orange} \forall x: (\exists y: P(x, y))} \\
{\color{orange} \forall x: (\exists y: P(x, y))} &\not\models {\color{green} \exists y: (\forall x: P(x, y))}
\end{align*}
$$
</div>

|     | Input | Output | Meaning |
| :-: | :---: | :----: | :-----: |
| $A \to B$ | Formulas | Formula | $A$ implies $B$ |
| $A \gets B$ | Formulas | Formula | $B$ implies $A$ |
| $A \leftrightarrow B$ | Formulas | Formula | $A$ implies $B$ and $B$ implies $A$ |
| | | |
| $A \implies B$ | Expressions | Expression | $A$ implies $B$ |
| $A \impliedby B$ | Expressions | Expression | $B$ implies $A$ |
| $A \iff B$ | Expressions | Expression | $A$ implies $B$ and $B$ implies $A$ |
| | | |
| $A \models B$ | Formulas | Expression | $B$ is a logically consequence of $A$ |
| $A \equiv B$ | Formulas | Expression | $A$ is logically equivalent to $B$ |

### $\mathcal{S}\text{ets}$

<div class="katex-flalign">

$$
\begin{align*}
    A \cap A &= A &\textit{(Idempotence)} \\
    A \cup A &= A \\
    A \cap B &= B \cap A &\textit{(Commutativity)} \\
    A \cup B &= B \cup A \\
    A \cap (B \cap C) &= (A \cap B) \cap C &\textit{(Associativity)}\\
    A \cup (B \cup C) &= (A \cup B) \cup C \\
    A \cap (A \cup B) &= A &\textit{(Absorption)}\\
    A \cup (A \cap B) &= A \\
    A \cap (B \cup C) &= (A \cap B) \cup (A \cap C) &\textit{(Distributivity)}\\
    A \cup (B \cap C) &= (A \cup B) \cap (A \cup C) \\
    A \subseteq B \iff A \cap B &= A \iff A \cup B = B &\textit{(Consistency)}\\
\end{align*}
$$
</div>

**Cartesian Product:** $A \times B \dot{\iff} \Set{(a, b) | a \in A \land b \in B}$ \
$\implies |A \times B| = |A| \cdot |B|$ \
$\implies \text{X}\sub{{i=1}}^k A\sub{i}=\Set{(a\sub{1}, ..., a\sub{k}) | a\sub{i} \in A\sub{i} ~\forall i \in [1,...,k]}$ \
**Powerset:** $\mathcal{P}(A) \dot{\iff} \Set{S | S \subseteq A}$. \
$\implies$ If $A$ finite with cardinality $k$, $\mathcal{P}(A)$  has cardinality $2^k$ \
**Partition:** $\bigcup\sub{{i \in \mathcal{I}}} S\sub{i} = A$ where $S\sub{i} \cap S\sub{j} = \varnothing \space\forall i \neq j$

#### Relations

**Relation:**
$\rho \subseteq A \times B \implies (a, b) \in \rho \equiv a \rel{\rho}  b$ \
**Inverse:** $\hat{\rho}$, or somtimes $\rho^{-1}$: 
$\space\space\hat{\rho} \dot{\iff} \Set{(b, a) | (a, b) \in \rho} \iff a \rel{\rho} b \equiv b \rel{\hat{\rho}} a$ \
**Composition:**
$\rho \circ \sigma \dot{\iff} \Set{(a, c) | \exists b: (a, b) \in \rho \land (b, c) \in \sigma}$

| Property Name | Propositional | Set |
| :- | :- | :- |
| Reflexitivity | $\forall a: (a \rel{\rho} a)$ | $\text{id}_A \subseteq \rho$ |
| Irreflexitivity | $\forall a: \lnot(a \rel{\rho} a)$ | $\rho \cap \text{id}_A = \varnothing$ |
| Symmetry | $a \rel{\rho} b \leftrightarrow b \rel{\rho} a$ | $\rho = \hat{\rho}$ |
| Antisymmetry | $a \rel{\rho} b \land b \rel{\rho} a \to a = b$ | $\rho \cap \hat{\rho} = \text{id}_A$ |
| Transitivity | $a \rel{\rho} b \land b \rel{\rho} c \leftrightarrow a \rel{\rho} c$ | $\rho^2 \subseteq \rho$ |

$\implies$ Reflexivity and Irreflexitivity are **mutually exclusive** \
$\implies$ Symmetry and Antisymmetry are **NOT mutually exclusive** (both possible at once) \
**Transitive closure**: $\rho^\ast = \displaystyle\bigcup_{n \in \N_{1+}}{\rho^n}$ \
**Equivalence Relation:** $\theta \in$ reflexive, transitive, symmetric \
$\implies$ **Equivalence Class:** $[a]_\theta \dot{\iff} \Set{b \in A | b \rel{\theta} a}$\
$\implies$ **Quotient Set:** $A / \theta \dot{\iff} \Set{[a]_\theta | a \in A}$ (Partition of $A$) \
**Order Relation:** $(\preccurlyeq) \in$ reflexive, transitive, **anti**-symmetric \
$\implies a \prec b \dot{\iff} a \preccurlyeq b \land a \neq b$ \
$\implies (A; \preccurlyeq)$ is called a **Poset** \
$\quad\implies$ If all elements in Poset comparable $\iff$ **Totally Ordered Set**

**Functions:** $f: A \to B$ from **domain** $A$ to **codomain** $B$ **maps** $f: a \in A \mapsto b \in B$ \
$\quad1. \forall a \in A: \exists b \in B: a \rel{f} b~~$ _(Totality)_ \
$\quad2. \forall a \in A: \forall b, b' \in B: (a \rel{f} b \land a \rel{f} b' \to b = b')~~$ _(well-defined)_ \
$\implies$ **injective:** $\forall a \neq a':f(a) \neq f(a')$ \
$\implies$ **surjektive:** $\forall b \in B \exists a \in A: b=f(a)$ where $f(A) = B$ \
$\implies$ **bijektive:** injektiv + surjektiv

## $\N\text{umber Theory}$

**Euclid Arithmetic:** \
$x = mq + r$ where $0 \le r \lt |m| \iff R_m(x) = r$ \
$y(x) = m(x)q(x) + r(x)$ where $\deg(r(x)) \lt \deg(m(x)) \iff R_{m(x)}(y(x)) = r(x)$

**Prime Factorization:** \
$a = \displaystyle\prod_i p_i^{e_i}$ and $b = \displaystyle\prod_i p_i^{f_i}$

**Polynomials:** \
$a(x)=a_{d}x^{d}+a_{d-1}x^{d-1}+...+a_1x+a_0=\displaystyle\sum_{i=0}^d a_i x^i$ \
$\deg(a(x)) = $ greatest $i$ for which $a_i \neq 0$ \
Special polynomial $0$ has $deg(0) = -\infin$

**Greatest Comon Divisor:** \
$\displaystyle \gcd(a, b) = \prod_i p_i^{\min(e_i, f_i)}$ \
$\gcd(a, b) \implies \exists u,v: ua + vb$ \
$\gcd(a, b) = 1 \implies a$ and $b$ called relatively prime \
$\gcd(m, n) = \gcd(m, n - qm) = \gcd(m, R_m(n))$

**Modular Arithmetic:** \
$a \equiv_m b \dot{\iff} m \mid (a - b) \dot{\iff} R_m(a) = R_m(b)$ \
$a = b \models a \equiv_m b \iff a \not\equiv_m b \models a \not= b$ \
$a \equiv_m R_m(a)$ \
$\gcd(a, m) = 1 \iff \exists x \in \Z_m : ax \equiv_m 1$

**Groups:** \
$\Z_m^\ast = \Set{a \in \Z_m | \gcd(a, m) = 1}$ \
$\forall a \in G: a^{|G|} = e$ where $G$ finite Group \
Lagrange:\
$\to \forall H \subseteq G: \text{ord}(H) \mid \text{ord}(G)$ where $H$ subgroup of $G$ \
$\to \forall a \in G: \text{ord}(a) \mid \text{ord}(G)$ \
**$e$-th root of Group $G$:** $\exists e \in \Z: \gcd(e, |G|) = 1 \implies x \mapsto x^e$ bijektiv \
$\implies e$-th root $y = x^e \implies \exists d: x = y^d \implies ed \equiv_{\text{ord}(G)} 1$

**Euler function:** \
$\varphi: \Z^+ \to \Z^+$ \
$\varphi(m) = |Z_m^\ast|$ \
$\varphi(p) = p - 1$ where $p$ prime \
$\varphi(m) = \displaystyle\prod_{i=1}^r (p_i - 1)p_i^{e_i - 1}$ where $m = \displaystyle\prod_{i=1}^r p_i^{e_i}$

**Euler and Fermat:** \
$a^{\varphi(m)} \equiv_m 1$ where $m \ge 2 \land \gcd(a, m) = 1$ \
$a^{p - 1} \equiv_m 1$ where $p$ prime and $a$  is not divisible by $p$

## Algebras

Given set $S$ with operation $\ast$ we denote this Algebra as $\braket{S;\ast}$, and the properties of $\ast$ as: \
$\implies$ **Totality:** $\forall a,b \in S: a\ast b \in S$ (not technically required, but usually assumed) \
$\implies$ **Associativity:** $a\ast(b\ast c) = (a\ast b)\ast c$ \
$\implies$ **Identity:** $\exists e \in S: \forall a \in S : e \ast a = a \ast e = a$ \
$\implies$ **Divisibility:** $\forall a,b \in S: \exists d : a \ast d = b$ \
$\quad\implies$ **Invertibility**: Special case where $b = e$ and $d = \hat{a}$ \
$\implies$ **Commutativity:** $a\ast b = b\ast a$

| | Associativity | Identity | Divisibility | Commutativity |
| :- | :-: | :-: | :-: | :-: |
| Magma | | | | |
| Quasigroup | | | Required | |
| Unital magma | | Required | | |
| Loop | | Required | Required | |
| Semigroup | Required | | | |
| Associative quasigroup | Required | | Required | |
| **Monoid** | Required | Required | | |
| **Group** | Required | Required | Required | |
| **Abelian Group** | Required | Required | Required | Required |

**Homomorphisms** Given $\braket{G;\ast;\hat{~}~;e}$ and $\braket{H;\star;\tilde{~}~;e'}$, $\varPsi~$ Is a group Homomorphism iff:\
$\quad1.~ \forall a, b: \varPsi(a \ast b) = \varPsi(a) \star \varPsi(b)$ \
$\quad2.~ \forall a: \varPsi(\hat{a}) = \widetilde{\varPsi(a)}$ \
$\quad3.~ \varPsi(e) = e'$ \
$\implies \varPsi~$ bijektiv $\implies G \simeq H$ (**Isomorphism**)

**Subgroups:** $G'$ is subgroup of $G$ if all operations are closed under $G'$

**Order:** Given element $a \in$ Group $G: \text{ord}(a) = \min\set{m \ge1 | a^m = e}$ else $\text{ord} = \infin$ \
$\implies$ For groups: $\text{ord}(G) \dot{\iff} |G|$ \
$\implies \forall m \in \Z: a^m = a^{R_{\text{ord}(a)}(m)}$ \
$\implies \text{ord}(e) = 1$

**Cyclic Groups:** $G = \braket{g}$ where _generator_: $\braket{g} \dot{\iff} \set{e, g, g^2, ..., g^{\text{ord}(g) - 1}}$ \
$\implies \braket{g} = G \simeq \braket{\Z_{\text{ord}(G)}; \oplus} \implies$ **abelian**

**Ring:** $\braket{R;+;-;0;\cdot~;1}$ where $(-)$ is negation, not subtraction. Satisfies: \
$\quad1. \braket{R;+;-;0}$ Commutative/Abelian Group \
$\quad2. \braket{R;\cdot~;1}$ monoid. Iff commutative $\implies$ **Commutative Ring** \
$\quad3.~ \forall a,b,c: a(b + c) = ab + ac \land (b + c)a = ba + ca$ _(distributivity laws)_ \
$\implies$ Given $u \in R~$ iff multiplicative inverse exists then $u$ is called _unit_. \
$\implies$ Set of units of $R$ is denoted as $R^\ast = \set{u \in R | \exists u^{-1}: uu^{-1} = u^{-1}u = 1 }$ \
$\implies$ For any Commutative Ring $R$, $R[x]$ is also commutative ring.

**Zero Divisor:** $a \neq 0 \in R$ if $\exists b \neq 0 \in R: ab = 0$ \
**Integral Domain:** nontrivial commutative ring without zerodivisors \
$\implies \forall a, b: (ab = 0 \to a = 0 \lor b = 0)$

**Field:** nontrivial commutative ring $F$ in which every
nonzero element is a _unit_ ($F^\ast = F \setminus\{0\}$). \
$\implies p$ prime $\iff \Z_p$ field.
