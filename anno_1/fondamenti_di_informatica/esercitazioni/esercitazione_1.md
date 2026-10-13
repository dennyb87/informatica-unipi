## Esercizio 1

Fornire un dimostrazione discorsiva o per sostituzione del seguente enunciato:

> Per tutti gli insiemi $A$, e tutte le relazion $R \in Rel(A, A)$ vale che: $R^{op} \cap Id_A = (R \cap Id_A)^{op}$

#### Svolgimento

$$
\begin{aligned}
    R^{op} \cap Id_A &= (R \cap Id_A)^{op} \qquad \{ \text{dist. di} \ ^{op}\ \text{su} \ \cap\} \\
    &= R^{op} \cap Id_A^{op} \ \ \ \qquad \{ \text{op-id}\} \\
    &= R^{op} \cap Id_A \qquad \quad \checkmark
\end{aligned}
$$

## Esercizio 2

Fornire un controesempio al seguente enunciato:

> Per tutti gli insiemi $A$ e tutte le relazioni $R \in Rel(A, A)$ vale che: $R \subseteq R;R$


#### Svolgimento

$A = \{x, y, z\}$  

$R = \{(x, y), (y, z), (z, x)\}$  

$R;R = \{(x, z), (y, x), (z, y)\}$  

$R \nsubseteq R;R \quad \checkmark$  


## Esercizio 3  

Per ognuno dei seguenti enunciati dire se e' vero: in caso affermativo fornire una dimostrazione discorsiva o per sostituzione (utilizzando le leggi viste fin'ora); in caso negativo fornire un controesempio.  

> 1. Per tutti gli insiemi $A$ e tutte le relazioni $R \in Rel(A, A)$ vale che: $R \subseteq (Id_A \cup R);R$
> 2. Per tutti gli insiemi $A$ e tutte le relazioni $R \in Rel(A, A)$ vale che: $R \subseteq (Id_A \cap R);R$


#### Svolgimento enunciato 1

$$
\begin{aligned}
    R &\subseteq (Id_A \cup R);R \ \ \ \ \qquad \{\text{dist. di}\ ; \text{su} \cup \text{(destra)}\} \\
    R &\subseteq (Id_A;R) \cup (R;R) \quad \{\text{unita'}\} \\
    R &\subseteq R \cup (R;R) \qquad \qquad \checkmark
\end{aligned}
$$

#### Svolgimento enunciato 2

Sia...  

$A = \{x, y, z\}$  

$Id_A = \{(x, x), (y, y), (z, z)\}$  

$R = \{(x, y), (y, z), (z, x)\}$  

$R$ non ha elementi in comune con l'identita', allora...  

$$
\begin{aligned}
    R &\subseteq (Id_A \cap R);R \ \ \ \ \qquad \{\text{intersezione senza elementi in comune}\} \\
    R &\subseteq \varnothing;R \qquad \qquad \qquad \ \ \{\text{assorbimento}\} \\
    R &\nsubseteq \varnothing \qquad \qquad \qquad \qquad \checkmark
\end{aligned}
$$
