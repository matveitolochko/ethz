<style>
.katex-flalign .katex-display {
    text-align: left !important;
}
.katex-flalign .katex-display>.katex {
    text-align: left !important;
}
</style>

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

**Powerset**: $\mathcal{P}(A) \dot{\iff} \{S | S \subseteq A\}$.
For a finite set with cardinality $k$, the power set has cardinality $2^k$ (hence the name "power set").

#### Relations

**Relation:**
$\rho \subseteq A \times B \implies (a, b) \in \rho \equiv a ~\rho~ b$

**Inverse:** $\hat{\rho}$, or somtimes $\rho^{-1}$: 
$~~\hat{\rho} \dot{\iff} \{(b, a)~|~(a, b) \in \rho\} \iff a~\rho~b \equiv b~\hat{\rho}~a$

**Composition:**
$\rho \circ \sigma \dot{\iff} \{(a, c)~|~\exists b: (a, b) \in \rho \land (b, c) \in \sigma\}$

| Property Name | Propositional | Set |
| :- | :- | :- |
| Reflexitivity | $\forall a: (a~\rho~a)$ | $\text{id}_A \subseteq \rho$ |
| Irreflexitivity | $\forall a: \lnot(a~\rho~a)$ | $\rho \cap \text{id}_A = \varnothing$ |
| Symmetry | $a~\rho~b \leftrightarrow b~\rho~a$ | $\rho = \hat{\rho}$ |
| Antisymmetry | $a~\rho~b \land b~\rho~a \to a = b$ | $\rho \cap \hat{\rho} = \text{id}_A$ |
| Transitivity | $a~\rho~b \land b~\rho~c \leftrightarrow a~\rho~c$ | $\rho^2 \subseteq \rho$ |

- Reflexivity and Irreflexitivity are **mutually exclusive**
- Symmetry and Antisymmetry are **NOT mutually exclusive** (both possible at once)

## $\N\text{umber Theory}$

<div class="katex-flalign">

$$
\begin{align*}
    &\textbf{Euclid Arithmetic:}\\
    &x = dq + r \text{~~where~~} 0 \le r \lt |d| \iff R_d(x) = r \\
    \\
    &\textbf{Prime Factorization:}\\
    &a = \prod_i p_i^{e_i} \text{~~and~~} b = \prod_i p_i^{f_i}\\
    \\
    &\textbf{Greatest Comon Divisor:}\\
    &\gcd(a, b) = \prod_i p_i^{\min(e_i, f_i)} \\
    &\gcd(a, b) \implies \exists u,v: ua + vb \\
    &\gcd(a, b) = 1 \implies a \text{~and~} b \text{~called relatively prime} \\
    &\gcd(m, n) = \gcd(m, n - qm) = \gcd(m, R_m(n)) \\
    \\
    &\textbf{Modular Arithmetic:}\\
    &a \equiv_m b \dot{\iff} m~|~(a - b) \dot{\iff} R_m(a) = R_m(b)\\
    &a = b \models a \equiv_m b \iff a \not\equiv_m b \models a \not= b\\
    &a \equiv_m R_m(a) \\
    &\gcd(a, m) = 1 \iff \exists x \in \Z_m : ax \equiv_m 1\\
    \\
    &\textbf{Group~}\Z_m^*\textbf{:}\\
    &\Z_m^* = \{a \in \Z_m ~|~ \gcd(a, m) = 1\}\\
    \\
    &\textbf{Euler function:}\\
    &\varphi: \Z^+ \to \Z^+\\
    &\varphi(m) = |Z_m^*|\\
    &\varphi(p) = p - 1 \textbf{~~where~~} p \text{~prime}\\
    &\varphi(m) = \prod_{i=1}^r (p_i - 1)p_i^{e_i - 1} \textbf{~~where~~} m = \prod_{i=1}^r p_i^{e_i} \\
    \\
    &\textbf{Euler and Fermat:}\\
    &a^{\varphi(m)} \equiv_m 1 \textbf{~~where~~} m \ge 2 \land \gcd(a, m) = 1 \\
    &a^{p - 1} \equiv_m 1 \textbf{~~where~~} p \text{~prime} \land a \text{~not divisible by~} p \\
\end{align*}
$$
</div>

## Algebras

Given set $S$ with operation $\ast$ we denote this Algebra as $\braket{S;*}$, and the operations of $\ast$ as:

- **Totality:** $\forall a,b \in S: a\ast b \in S$ (not technically required, but assumed)
- **Associativity:** $a\ast(b\ast c) = (a\ast b)\ast c$
- **Identity:** $\exists e \in S: \forall a \in S : e \ast a = a \ast e = a$
- **Divisibility:** $\forall a,b \in S: \exists d : a \ast d = b$
    - **Invertibility**: Special case where $b = e$ and $d = \hat{a}$
- **Commutativity:** $a\ast b = b\ast a$

| | Associativity | Identity | Divisibility | Commutativity |
| :- | :-: | :-: | :-: | :-: |
| Magma | | | | |
| Quasigroup | | | $\color{green}{\text{Required}}$ | |
| Unital magma | | $\color{green}{\text{Required}}$ | | |
| Loop | | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ | |
| Semigroup | $\color{green}{\text{Required}}$ | | | |
| Associative quasigroup | $\color{green}{\text{Required}}$ | | $\color{green}{\text{Required}}$ | |
| **Monoid** | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ | | |
| **Group** | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ | |
| **Abelian Group** | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ | $\color{green}{\text{Required}}$ |
