# A&D CheatSheet

## Graphen

**Graph:** $~G = (V, E)$ \
**Knoten:** $~V =\{v_1, ..., v_n\}~$ (vertices, nodes) \
**Kanten:** $~E = \{e_1, ..., e_m\}~$ (edges, links) \
$\to$ **Ungerichtete Graphen:** $e$ ist Menge, $~E =\{e_1 = \{v_i, v_j\}, ...\}~$ \
$\to$ **Gerichtete Graphen:** $e$ ist Geordnetes Paar, $~E =\{e_1 = (v_i, v_j), ...\}~$ \
**Grad:** $~\deg(v)~$ Anzahl anliegenden Kanten (degree) \
$\to$ **Handschlaglemma:** $\sum_{v \in V}\deg(v) = 2m = 2|E|$ \
$\to$ Für Gerichtete Graphen: \
$\quad\to$ $\deg_{in}(v) =~$ Eingangsgrad. **Quelle** (source) falls 0 \
$\quad\to$ $\deg_{out}(v) =~$ Ausgangsgrad. **Senke** (sink) falls 0 \
$\quad\to$ $\deg(v) = \deg_{in}(v) + \deg_{out}(v)$ \
**Einfache Graphen (Default):** \
$\to$ Jede Kante kommt höchstens einmal vor \
$\to$ keine **Schleifen**: Kanten von $v$ zu sich selbst \
**Multigraph (<span style="color:red">nur, falls explizit erwähnt</span>):** \
$\to$ Kanten dürfen mehrfach vorkommen \
$\to$ Schleifen erlaubt, wo Schleife $(v, v)$ zählt doppelt für $\deg(v)$

$\xi = v_i$ erreicht $v_j = \exists$ Weg von $v_i$ nach $v_j$ \
$\to \xi$ [Äquivalenzrelation](./diskmat.md) (symmetrisch, reflexiv, transitiv) \
$\to$ **Zusammenhangskomponente (ZHK):** [Äquivalenzklassen](./diskmat.md) der $\xi$ relation. \
$\to$ **Zusammenhängend (zhgd):** Genau eine ZHK $\equiv$ "Jeder Knoten erreicht jeden anderen"

$$
\begin{CD}
\text{Weg} @>\text{Keine Wiederholten Knoten}>> \text{Pfad} @>>>\\
@VV\text{$v_0 = v_l$}V \\
\text{Geschlosener Weg} @>\text{Keine Wiederholten Kanten}>\text{und $l \ge 1$}> \text{Zyklus} @>\text{Keine Wiederholten Knoten}>\text{(Ausser $v_0 = v_l$) und $l \ge 1$}> \text{Kreis}
\end{CD}
$$

### Laufzeiten typischer Graphoperationen

| | Adjazenzmatrix | Adjazenzlisten |
| :- | :-: | :-: |
| Ist Kante $e \in E~$? | $\mathcal{O}(1)$ | $\mathcal{O}(\deg(v_i))$ <br><span style="color:orange">Formal Korrekt: $\mathcal{O}(1 + \deg(v_i))$ </span>|
| Finde einen Nachbarn von $v$ | $\mathcal{O}(n)$ | $\mathcal{O}(1)$ |
| Finde alle Nachbarn von $v$ | $\mathcal{O}(n)$ | $\mathcal{O}(\deg(v))$ |
| Finde $\deg(v)$ | $\mathcal{O}(n)$ | $\mathcal{O}(\deg(v))$ <br><span style="color:teal">Oder $\mathcal{O}(1)$ mit Erweiterungen</span> |
| Lösche Kante $e$ | $\mathcal{O}(1)$ | $\mathcal{O}(\deg(v_i))$ <br><span style="color:teal">Oder $\mathcal{O}(1)$ falls Zeiger auf $e$ gegeben</span> |
| Füge Kante $e$ ein | $\mathcal{O}(1)$ | $\mathcal{O}(\deg(v_i))$ <br><span style="color:red">Müssen prüfen ob $e$ schon existiert!</span><br><span style="color:teal">Falls bekannt dass $e$ neu ist: $\mathcal{O}(1)$</span> |
| Lösche / Füge Knoten $v$ ein <br><span style="color:red">(mitsamt inzidenten Kanten)</span> | $\mathcal{O}(n^2)$ | $\mathcal{O}(n)$ <br><span style="color:teal">Kann verbessert werden</span> |