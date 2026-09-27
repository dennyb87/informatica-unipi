# Famiglie di insiemi

Una famiglia di insiemi $F$ indicizzata da $I$ e' una collezione di insiemi $A_i$, in cui ogni insieme è contrassegnato da un *indice* $i$ appartenente a un insieme di indici $I$.  

$$F = \{A_i \mid i \in I\} = \{A_i\}_{i \in I}$$

L'unione $\bigcup F$ e' l'insieme di tutti gli elementi presenti in **almeno un** insieme della famiglia:
  

$$\bigcup F = \bigcup_{i \in I} A_i$$

L'intersezione $\bigcap F$ e' l'insieme degli elementi presenti contemporaneamente in **tutti** gli insiemi della famiglia:
  

$$\bigcap F = \bigcap_{i \in I} A_i$$

### Esempio  

* Studenti del primo anno: $S1 = \{\text{Anna}, \text{Bob}\}$

* Insieme dei corsi: $C = \{\text{FDI}, \text{PA}\}$

* Insieme dei mesi: $M = \{\text{gennaio}, \text{febbraio}\}$

*(Supponiamo che Anna segua FDI e PA e sia nata a gennaio, mentre Bob segue solo FDI ed è nato a febbraio).*

### Caso A: Famiglia indicizzata per corso ($\mathcal{F} = \{S1_c \mid c \in C\}$)

* **Insiemi della famiglia:**

  * $S1_{\text{FDI}} = \{\text{Anna}, \text{Bob}\}$

  * $S1_{\text{PA}} = \{\text{Anna}\}$

  * Famiglia completa: $\mathcal{F} = \{S1_{\text{FDI}}, S1_{\text{PA}}\}$

* **Operazioni:**

  * $\bigcup \mathcal{F}$ **(Unione):** $\{\text{Anna}, \text{Bob}\}$ $\rightarrow$ studenti che seguono **almeno un** corso.

  * $\bigcap \mathcal{F}$ **(Intersezione):** $\{\text{Anna}\}$ $\rightarrow$ studenti che seguono **tutti** i corsi.

### Caso B: Famiglia indicizzata per mese di nascita ($\mathcal{H} = \{S1_m \mid m \in M\}$)

* **Insiemi della famiglia:**

  * $S1_{\text{gennaio}} = \{\text{Anna}\}$

  * $S1_{\text{febbraio}} = \{\text{Bob}\}$

  * Famiglia completa: $\mathcal{H} = \{S1_{\text{gennaio}}, S1_{\text{febbraio}}\}$

* **Operazioni:**

  * $\bigcup \mathcal{H}$ **(Unione):** $\{\text{Anna}, \text{Bob}\} = S1$ $\rightarrow$ unendo tutti i mesi si ricostruisce l'intera classe.

  * $\bigcap \mathcal{H}$ **(Intersezione):** $\emptyset$ (insieme vuoto) $\rightarrow$ è impossibile essere nati in più mesi contemporaneamente.

# Partizioni

Una **partizione** su un insieme $A$ è una famiglia $\boldsymbol{P} = \{A_i\}_{i \in I}$ di **sottoinsiemi** di $A$ che soddisfa le seguenti condizioni:

1. ogni insieme $A_i$ è diverso da $\emptyset$ *(insiemi non vuoti)*
2. l'unione della famiglia e' uguale ad $A$ ovvero $\bigcup \boldsymbol{P} = \bigcup_{i \in I} A_i = A$ *(copertura di $A$)*
3. dati due indici qualunque $i$ e $j$ con $i \neq j$ si ha $A_i \cap A_j = \emptyset$ *(insiemi disgiunti)*


```mermaid
block
  block:A["A"]
    columns 3
    A1["A₁"]:1
    A2["A₂"]:1
    block:destra:1
      columns 1
      A3["A₃"]
      A4["A₄"]
    end
  end
```

Esempio:  

$A = \{1, 2, 3, 4, 5, 6\}$

$$A_1 = \{1, 3, 5\} \quad \text{(numeri dispari)}$$  
$$A_2 = \{2, 4, 6\} \quad \text{(numeri pari)}$$  

La famiglia $\boldsymbol{P} = \{A_1, A_2\} = \{\{1, 3, 5\}, \{2, 4, 6\}\}$ e' una partizione di $A$ poiche' rispetta le 3 proprieta'. 

$A_1 \neq \emptyset \land A_2 \neq \emptyset$  
$A_1 \cup A_2 = \{1, 3, 5\} \cup \{2, 4, 6\} = \{1, 2, 3, 4, 5, 6\} = A$  
$A_1 \cap A_2 = \emptyset$

# Relazioni   

Una **relazione $R$ tra $A$ e $B$** e' un sottoinsieme di $A \times B$ (il prodotto cartesiano).
$$A \times B = \{(a, b) \mid a \in A \land b \in B\}$$

* $R \subseteq A \times B$ (per definizione)
* $R \in Rel(A, B)$, dove $Rel(A, B)$ indica l'insieme di tutte le relazioni tra $A$ e $B$.
* $R: A \leftrightarrow B$ (simile alla tipica notazione per le funzioni)

### Esempio  

Per $R \in Rel(A, B)$ chiamiamo:
* $A$: "insieme di partenza"
* $B$: "insieme di arrivo"

Siano $A = \{x, y\}$ e $B = \{a, b, c\}$. Esempi di relazioni tra $A$ e $B$:
* $R = \{(x, a), (x, c)\} \subseteq A \times B$
* $\varnothing \subseteq A \times B$ è la **relazione vuota**, $\varnothing \in Rel(A, B)$
* $A \times B = \{(x, a), (x, b), (x, c), (y, a), (y, b), (y, c)\}$ e' la **relazione completa**

## Rappresentazione grafica di relazioni

Siano $A = \{x, y\}$ e $B = \{a, b, c\}$

```mermaid
flowchart LR
    subgraph A
        x
        y
    end
    subgraph B
        a
        b
        c
    end
    x --> a
    x --> c
```
$R = \{(x, a), (x, c)\}$ 

```mermaid
flowchart TD
    subgraph A
        x
        y
    end
    subgraph B
        a
        b
        c
    end
```

$\emptyset: A \leftrightarrow B$

```mermaid
flowchart LR
    subgraph A
        x
        y
    end
    subgraph B
        a
        b
        c
    end
    x --> a
    x --> b
    x --> c
    y --> a
    y --> b
    y --> c
```

$A \times B \in Rel(A, B)$

# Relazioni su un insieme

Se insieme di partenza e insieme di arrivo coincidono, allora chiamiamo le relazioni in $Rel(A, A)$ **relazioni su A**, ad esempio:  

$Succ = \{ (x, y) \in \mathbb{N} \times \mathbb{N} \mid y = x + 1 \}$  
$Succ \in Rel(\mathbb{N}, \mathbb{N})$
