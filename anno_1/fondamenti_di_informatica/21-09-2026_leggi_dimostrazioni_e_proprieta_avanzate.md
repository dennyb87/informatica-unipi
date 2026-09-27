## Proprieta'   

| Legge | Unione | Intersezione |
|---|---|---|
| Unità | $A \cup \varnothing = A$ | $A \cap U = A$ |
|Associativa|$(A \cup B) \cup C = A \cup (B \cup C)$|$(A \cap B) \cap C = A \cap (B \cap C)$|
| Commutativa | $A \cup B = B \cup A$ | $A \cap B = B \cap A$ |
| Idempotenza | $A \cup A = A$ | $A \cap A = A$ |
| Assorbimento | $A \cup U = U$ | $A \cap \varnothing = \varnothing$ |
| Complemento | $A \cup \overline{A} = U$ | $A \cap \overline{A} = \varnothing$ |

Proprietà distributive:

$$A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$$

$$A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$$

Differenza tra insiemi:

$$A \setminus B = A \cap \overline{B}$$

## Dimostrazione 1  

Si vuole dimostrare che:  

$(A \cup B) \cup C = A \cup (C \cup B)$  

Utilizzando le leggi dimostrate in precedenza...

$$
\begin{aligned}
(A \cup B) \cup C &= A \cup (B \cup C) && \text{(associativa)}\\
&= A \cup (C \cup B) && \text{(commutativa)}
\end{aligned}
$$

Per transitività dell'uguaglianza:

$$ (A \cup B) \cup C = A \cup (C \cup B)$$

## Dimostrazione 2

Si vuole dimosrare:  

$$A \cup (\overline{A} \cap B) = A \cup B$$

Dalle leggi dimostrate in precedenza...  

$$
\begin{aligned}
A \cup (\overline{A} \cap B)
&= (A \cup \overline{A}) \cap (A \cup B) && \text{(distributiva)}\\
&= U \cap (A \cup B) && \text{(complemento)}\\
&= (A \cup B) \cap U && \text{(commutativa)}\\
&= A \cup B && \text{(unità)}
\end{aligned}
$$

## Dimostrazione 3

Si vuole dimostrare:  

$$A \cup (A \cap B) = A$$  

Dalle leggi dimostrate in precedenza...  

$$
\begin{aligned}
A \cup (A \cap B)
&= (A \cap U) \cup (A \cap B) && \text{(unità)}\\
&= A \cap (U \cup B) && \text{(distributiva)}\\
&= A \cap (B \cup U) && \text{(commutativa)}\\
&= A \cap U = A
\end{aligned}
$$

## Dimostrazione 4

Si vuole dimostrare:  

$$ (A \setminus B) \cup (B \setminus A) = (A \cup B) \setminus (A \cap B)$$  

Dalle leggi dimostrare in precedenza...  

(da dimostrare)

## Altre proprieta'  

### Doppio complemento

$$\overline{\overline{A}} = A$$

### Leggi di De Morgan  

$$\overline{A \cup B} = \overline{A} \cap \overline{B} \qquad \overline{A \cap B} = \overline{A} \cup \overline{B}$$

$$\overline{\varnothing} = U \qquad \overline{U} = \varnothing$$

Esercizio: dimostra queste leggi nei 3 modi.

## Importanza delle dimostrazioni

- Isomorfismo di Curry–Howard: dimostrare correttamente equivale a programmare correttamente.
- Non tutte le verità sono dimostrabili (Gödel, 1930).
- Non tutti i problemi hanno una soluzione algoritmica (Turing, 1936).
- Goodstein: esempio di logica controintuitiva.
- Problema della dimostrabilità centrale per gli smart contract (es. Ethereum, RSA).

## Prodotto cartesiano

Il prodotto cartesiano di due insiemi A e B e' l'insieme di tutte le coppie ordinate $(a, b)$ in cui il primo elemento $a$ appartiene ad $A$ e il secondo elemento $b$ appartiene a $B$.  

$$A \times B = \{(a,b) \mid a \in A \land b \in B\}$$

E@ importante notare che la coppia ordinata $(a,b)$ è diversa da $(b,a)$, mentre le coppie non ordinate coincidono come insiemi:  

$$(a,b) \ne (b,a) \qquad \{a,b\} = \{b,a\}$$


Esempio:

$$A = \{a,b,c\} \qquad B = \{1,2\} \qquad C = \{a\}$$

$$A \times B = \{(a,1),(a,2),(b,1),(b,2),(c,1),(c,2)\}$$

$$A \times C = \{(a,a),(b,a),(c,a)\}$$

Se il prodotto cartesiano contiene tutte e sole le coppie $(a,b)$ tali che $a \in A$ e $b \in B$...  

$$\mathbb{R} \times \mathbb{R} = \{(x,y) \mid x \in \mathbb{R} \land y \in \mathbb{R}\},$$

...allora questo e' il piano cartesiano.

Il prodotto cartesiano non è associativo: $(A \times B) \times C$ e $A \times (B \times C)$ contengono elementi diversi!

$(A \times B) \times C) = \{((a,1),a), ...\}$  
$A \times (B \times C) = \{(a,(1,a)),...\}$  

## Insieme di insiemi  

Un insieme di insiemi (anche famiglia di insiemi o collezione di insiemi) e' un insieme i cui elementi sono a loro volta degli insiemi.  

$$X = \{a,\{a\},\{a,b,c\},\{b\}\}$$  

Si noti che:  

$$a \in X, \quad b \notin X, \quad \{a\} \subseteq X, \quad \{a,b,c\} \not\subseteq X, \quad \{\{a,b,c\}\} \subseteq X$$

## Insieme delle parti  


L'insieme delle parti di $A$ e' l'insieme che ha come elementi tutti e soli i sottoinsiemi di $A$.  

$$\mathcal{P}(A) = \{X \mid X \subseteq A\}$$  

Per $A = \{a,b,c\}$:

$$\mathcal{P}(A)=\{\{a,b,c\},\{a,b\},\{a,c\},\{b,c\},\{a\},\{b\},\{c\},\varnothing\}.$$

Il numero di elementi di $A$ si determina con:  

$$|\mathcal{P}(A)| = 2^{|A|}$$  


$$\mathcal{P}(\varnothing)=\{\varnothing\} \implies |\mathcal{P}(\varnothing)| = 2^0=1$$

Per ogni insieme $A$ vale $A \in \mathcal{P}(A)$ e $\varnothing \in \mathcal{P}(A)$.

## Cardinalità

Sia $A$ un insieme costituito da esattamente $n$ elementi distinti tra loro, si scrive cardinalita' di $A$:  

$$|A| = n$$  

## $k$-insiemi

Sia $A = \{x,y,z\}$ allora $\mathcal{P}_k(A)$ contiene i sottoinsiemi di $A$ con esattamente $k$ elementi.

$$
\begin{aligned}
    \mathcal{P}_4(A) &= \varnothing \\
    \mathcal{P}_3(A) &= \{\{x,y,z\}\} \\
    \mathcal{P}_2(A) &= \{\{x,y\},\{x,z\},\{y,z\}\} \\
    \mathcal{P}_1(A) &= \{\{x\},\{y\},\{z\}\} \\
    \mathcal{P}_0(A) &= \{\varnothing\}
\end{aligned}
$$

## Paradosso di Russell

Non e' sempre possibile definire un insieme utilizzando proprieta' arbitrarie...  

$NS = \{x \mid x \notin \varnothing\}$  

Questo e' *l'insieme degli insiemi che non appartengono all'insieme vuoto*. Dato che nessun insieme appartiene a $\varnothing$, allora $NS$ contiene tutti gli insiemi esistenti. Essendo $NS$ un insieme allora appartiene a se stesso $NS \in NS$.

$AS = \{x \mid x \in x\}$  

Questo e' *l'insieme degli insiemi che appartengono a se stessi*, percio' $NS \in AS$. Ma $AS \in AS$ ?
* se $AS$ appartiene a se stesso, soddisfa il requisito per entrare in $AS$. Nessuna contraddizione.
* Se $AS$ non appartiene a se stesso, allora non soddisfa il requisito per entrare in $AS$. Nessuna contraddizione.  


$NAS = \{x \mid x \notin x\}$


Questo e' *l'insieme degli insiemi che non appartengono a se stessi*. La domanda e': $NAS \in NAS$?

* se $NAS \in NAS$, allora per definizione $NAS \notin NAS$
* $NAS \notin NAS$, allora per definizione $NAS \in NAS$


Si ottiene quindi una contraddizione: il paradosso di Russell.
