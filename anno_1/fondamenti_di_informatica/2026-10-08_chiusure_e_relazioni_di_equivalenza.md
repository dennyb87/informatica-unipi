
# Chiusure di una Relazione

Se una relazione non possiede una proprieta', e' possibile *"chiuderla"* aggiungendo il minor numero possibile di coppie per soddisfare la proprieta' desiderata.

### Chiusura Riflessiva
La **chiusura riflessiva** di una relazione $R$ su $A$ e':
$$R \cup \text{Id}_A$$
Aggiunge tutti i cappi mancanti agli elementi di $A$.

### Chiusura Simmetrica
La **chiusura simmetrica** di una relazione $R$ e':
$$R \cup R^{\text{op}}$$
Garantisce che per ogni freccia in una direzione esista anche quella opposta.

## Chiusura Transitiva e Composizione N-aria

Dati due elementi collegati da un cammino indiretto (es. $a \to b$ e $b \to c$, ma manca $a \to c$), la chiusura transitiva aggiunge le frecce mancanti.

* **Composizione N-aria di una relazione:**
  1. Caso base: $R^0 = \text{Id}_A$
  2. Passo induttivo: $R^{n+1} = R ; R^n$ ($\forall n \in \mathbb{N}$)

* **Definizione formale della Chiusura Transitiva ($R^+$):**
  $$R^+ = \bigcup_{n \in \mathbb{N}^+} R^n = R^1 \cup R^2 \cup R^3 \cup \dots \cup R^n$$

* *Nota intuitiva:* Se il numero di composizioni supera la lunghezza dei cammini originali, le composizioni successive restituiscono l'insieme vuoto $\varnothing$, quindi non aggiungono ulteriori elementi.  

### Dimostrazione: $\text{Id}_A^+ = \text{Id}_A$

Vogliamo dimostrare che per ogni $n \in \mathbb{N}^+$ vale $\text{Id}_A^n = \text{Id}_A$, e di conseguenza la chiusura transitiva dell'identità è l'identità stessa.

Procediamo per induzione:

1. **Caso Base (CB):** Per $n = 1$
   $$\text{Id}_A^1 = \text{Id}_A \quad \checkmark$$

2. **Passo Induttivo (PI):** Assumiamo che la proprieta' valga per $n$ ($\text{Id}_A^n = \text{Id}_A$) e dimostriamola per $n+1$:
   $$\text{Id}_A^{n+1} = \{ \text{def. } R^n \} = \text{Id}_A ; \text{Id}_A^n = \{ \text{proprieta' d'unita'} \} = \text{Id}_A^n = \{ \text{ipotesi induttiva} \} = \text{Id}_A$$

---

### Esempio pratico: La relazione Successore ($\text{Succ}$)

Prendiamo la relazione successore sui numeri naturali:
* $\text{Succ} = \{ (x, y) \mid y = x + 1 \}$
* $\text{Succ}^2 = \{ (x, z) \mid z = x + 2 \}$
* $\text{Succ}^n = \{ (x, y) \mid y = x + n \}$

La chiusura transitiva $\text{Succ}^+$ rappresenta l'insieme di tutti i passi successivi possibili, che corrisponde esattamente alla relazione **minore** ($<$):
$$\text{Succ}^+ = \{ (x, y) \mid \exists n \in \mathbb{N}^+, y = x + n \} \iff <$$

### Chiusura Riflessiva e Transitiva (Stella di Kleene, $R^*$)
La chiusura riflessiva e transitiva, nota come **Stella di Kleene**, comprende sia i cammini di lunghezza $\ge 1$ che l'identità (cammini di lunghezza 0):
$$R^* = \bigcup_{n \in \mathbb{N}} R^n = R^+ \cup \text{Id}_A \quad (\text{poiche' } \text{Id}_A = R^0)$$

## Idempotenza delle chiusure

L'idempotenza vale per tutte le chiusure, ad esempio:  

$(R^*)^* = R^*$  

In altre parole...  

> Se una relazione $R$  e' gia' chiusa (per effetto di un'operazione di chiusura o perche' gia' chiusa per definizione) applicare la stessa operazione di chiusura non cambia nulla, la relazione rimane identica a se stessa!


# Relazioni di Equivalenza

Una relazione $R: A \leftrightarrow A$ si dice **relazione di equivalenza** se gode contemporaneamente di tre proprieta':
1. **Riflessiva**
2. **Simmetrica**
3. **Transitiva**

### Esempi di relazioni:
* $\text{Id}_A$ : $\checkmark$ (e' di equivalenza)
* $\varnothing$ : $\times$ (non è riflessiva, quindi no)
* $A \times A$ : $\checkmark$ (e' di equivalenza)

---

## Classi di Equivalenza

Data una relazione di equivalenza $R$ su un insieme $A$ e preso un elemento $a \in A$, la **classe di equivalenza di $a$** (indicata con $[a]_R$) e' l'insieme di tutti gli elementi in $A$ che sono in relazione con $a$:
$$[a]_R = \{ b \in A \mid (a, b) \in R \}$$

* **Nota importante:** La classe di equivalenza **non sara' mai vuota** (contiene almeno l'elemento $a$ stesso grazie alla riflessivita').

### Esempio grafico intuitivo:
* $[c]_R = \{c\}$
* $[a]_R = \{a, b\}$
* $[b]_R = \{a, b\}$ *(elementi equivalenti generano la stessa classe).*

---

## Teorema di corrispondenza (biiezione)

Esiste uno stretto legame tra le relazioni di equivalenza e le partizioni di un insieme.

1. L'insieme di tutte le classi di equivalenza di $R$ definisce una **partizione** di $A$.
2. Viceversa, ogni partizione di $A$ definisce una **relazione di equivalenza**.

Definiamo gli insiemi:
* $\text{Part}(A) = \{ P \mid P \text{ e' una partizione di } A \}$
* $\text{ERel}(A) = \{ R \mid R \text{ e' una relazione di equivalenza su } A \}$

Tra questi due insiemi esiste una corrispondenza biunivoca (isomorfismo): 
$$\text{ERel}(A) \cong \text{Part}(A)$$
Con le funzioni di passaggio tali che $i;j = Id_{\text{Part}(A)}$ e $j;i = Id_{\text{ERel}(A)}$

---

### Verifica della Partizione generata ($J(R)$)
Data $R \in \text{ERel}(A)$, la funzione che costruisce la partizione e':
$$J(R) = \{ [a]_R \mid a \in A \}$$

Per essere una valida partizione di $A$, deve soddisfare tre proprieta':
1. **Nessuna classe e' vuota:** $[a]_R \neq \varnothing \quad \checkmark$
2. **Copertura totale:** L'unione di tutte le classi ricostruisce l'intero insieme $A$:
   $$\bigcup_{a \in A} [a]_R = A \quad \checkmark$$
3. **Disjointness (Disgiunzione):** Due classi o sono identiche o sono perfettamente disgiunte (la loro intersezione e' vuota):
   $$\text{Se } [a]_R \neq [b]_R \implies [a]_R \cap [b]_R = \varnothing \quad \checkmark$$