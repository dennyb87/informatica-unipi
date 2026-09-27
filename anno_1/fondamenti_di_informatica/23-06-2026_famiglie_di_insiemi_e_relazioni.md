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