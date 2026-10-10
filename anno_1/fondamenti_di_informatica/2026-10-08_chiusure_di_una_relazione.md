
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

# Idempotenza delle chiusure

L'idempotenza vale per tutte le chiusure, ad esempio:  

$(R^*)^* = R^*$  

In altre parole...  

> Se una relazione $R$  e' gia' chiusa (per effetto di un'operazione di chiusura o perche' gia' chiusa per definizione) applicare la stessa operazione di chiusura non cambia nulla, la relazione rimane identica a se stessa!