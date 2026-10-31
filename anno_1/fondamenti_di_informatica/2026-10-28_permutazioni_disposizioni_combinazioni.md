# Permutazioni, Disposizioni e Combinazioni

**L'obiettivo principale del Calcolo Combinatorio:**
- Hai un totale di **$n$ oggetti** e vuoi capire in **quanti modi diversi** puoi organizzarli o sistemarli in **$k$ posti** disponibili.

---

### Da cosa dipende la formula da usare?
Tutto si riduce a rispondere a **due semplici domande**:

1. **L'ordine degli elementi conta?**
   - **Si'** $\rightarrow$ Importa la sequenza precisa (es. una password).
   - **No** $\rightarrow$ Importa solo quali elementi hai scelto (es. le carte che hai in mano).

2. **Gli elementi si possono ripetere?**
   - **No (Semplici)** $\rightarrow$ Ogni elemento viene usato una sola volta.
   - **Si' (Con ripetizione)** $\rightarrow$ Puoi riutilizzare lo stesso elemento piu' volte.


# Permutazioni

Sia $A$ un insieme finito con cardinalita' $\vert{}A\vert{} = n$. Il concetto di **permutazione** puo' essere definito in due modi equivalenti:

1. **Definizione sequenziale**: Una permutazione di $A$ e' una sequenza ordinata contenente tutti gli elementi di $A$:  

   $$a_0, a_1, \dots, a_{n-1}$$  

2. **Definizione funzionale**: Una permutazione di $A$ e' una funzione biiettiva (o biiezione):  

   $$\pi: A \to \vert{}A\vert{}$$  

   dove $\vert{}A\vert{}$ rappresenta l'insieme degli indici $\{0, 1, \dots, n-1\}$ (spesso indicato anche come l'insieme di cardinalita' $n$).

---

### Equivalenza tra le definizioni

Possiamo dimostrare formale l'equivalenza mostrando che esiste una **biiezione** tra l'insieme di tutte le permutazioni intese come sequenze, $Perm(A)$, e l'insieme delle biiezioni, $Bii(A, \vert{}A\vert{})$.

```mermaid
graph LR
    A["Perm(A) (Sequenze)"] <-->|biiezione| B["Bii(A, |A|) (Funzioni)"]
```

Per dimostrare la biiezione, definiamo le trasformazioni nei due versi:

* **Da sequenza a funzione ($bi$):**
  Data una sequenza $a_0, a_1, \dots, a_{n-1} \in \text{Perm}(A)$, associamo una funzione $f \in \text{Bii}(A, |A|)$ tale che:  

  $$f(a) = i \iff a = a_i$$  

* **Da funzione a sequenza ($perm$):**
  Data una biiezione $\pi: A \to |A|$, sfruttando la sua funzione inversa $\pi^{-1}: |A| \to A$, otteniamo la sequenza ordinata:  

  $$\pi^{-1}(0), \pi^{-1}(1), \dots, \pi^{-1}(n-1)$$  

Infine, verifichiamo che le due trasformazioni siano una l'inversa dell'altra attraverso le identita':

* $perm;bi = id_{\text{Bii}(A, |A|)}$
* $bi;perm = id_{\text{Perm}(A)}$


## Contando le permutazioni

Un esempio pratico con l'insieme $A = \{a, b, c, d\}$ mostra tutte le possibili permutazioni in $\text{Perm}(A)$:
* Sono in totale $24$, cioe' $4! = 24$.
* Lo stesso conto vale per $B = \{1, 2, 3, 4\}$ oppure per $S = \{\text{cuori, quadri, fiori, picche}\}$.

> **Nota:** Il numero di permutazioni dipende esclusivamente dal numero di elementi dell'insieme.

---

### Proprieta' formale

Formalmente, se due insiemi hanno la stessa cardinalita', lo stesso vale per i loro insiemi di permutazioni:  

$$|A| = |B| \implies |\text{Perm}(A)| = |\text{Perm}(B)|$$  


Sia $A$ un insieme con $|A| = n$. Una permutazione e' una sequenza ordinata di tutti gli $n$ elementi:  

$$(a_0, a_1, \dots, a_{n-1})$$  

Per costruire una generica permutazione, dobbiamo scegliere un elemento per ogni posizione, una alla volta:

* **Prima posizione ($a_0$):** abbiamo $n$ possibili elementi da scegliere tra quelli di $A$.
* **Seconda posizione ($a_1$):** avendo gia' usato un elemento, ci rimangono $(n - 1)$ scelte possibili.
* **Terza posizione ($a_2$):** ci rimangono $(n - 2)$ scelte possibili.
* $\dots$
* **Ultima posizione ($a_{n-1}$):** ci rimane solo $1$ solo elemento.

Allora il numero totale di sequenze distinte che si possono formare e' dato dal prodotto di tutte le scelte possibili:  

$$|\text{Perm}(A)| = n \cdot (n - 1) \cdot (n - 2) \cdot \dots \cdot 2 \cdot 1 = n! = |A|!$$  

Dato che $|A| = |B|$ allora $|\text{Perm}(A)| = |\text{Perm}(B)|$.

### Definizione induttiva  

Definiamo $P(n)$ come il numero di permutazioni di un insieme di $n$ elementi:  

* **CB:**
  * $P(0) = 1$
    * L'insieme con zero elementi puo' essere ordinato in un solo modo, la sequenza vuota.
  * $P(1) = 1$
    * L'insieme con 1 solo elemento puo' essere ordinato in un solo modo, la sequenza con l'unico elemento esistente.
* **CI:**
  * $P(n+1) = (n+1) \cdot P(n)$

La definizione induttiva risulta quindi identica a quella classica del fattoriale.

# Cardinalita' delle biiezioni tra due insiemi

La cardinalita' dell'insieme delle biiezioni tra due insiemi $A$ e $B$ e' definita come:  

$$|Bii(A, B)| = \begin{cases} 0 & \text{se } |A| \neq |B| \\ |A|! & \text{se } |A| = |B| \end{cases}$$  

Possiamo determinare questo risultato in due modi:

* **Contarle discorsivamente**:
  Se $|A| = |B| = n$, consideriamo il primo elemento di $A$, $a_1$: esso ha $n$ possibili immagini in $B$ ($b_1, b_2, \dots, b_n$). Il secondo elemento $a_2$ potra' essere associato a uno dei soli $(n-1)$ elementi rimasti in $B$, e cosi' via.
  Moltiplicando le opzioni disponibili per ogni elemento otteniamo:  

  $$n \cdot (n - 1) \cdot (n - 2) \cdots 1 = n!$$  

* **Ricordare che ogni permutazione e' una biiezione** $\pi: A \to |A|$.


# Anagrammi e permutazioni con ripetizioni

* Esempio: **CERTOSA** e' un anagramma valido di **COSTARE**.
* Quante combinazioni di anagrammi possiede la parola **CERTOSA**? $7! = 5040$.
* E quanti ne possiede invece **ANNA**? $6 \neq 4! = 24$.  

  $$\text{AANN} \quad \text{ANAN} \quad \text{ANNA} \quad \text{NAAN} \quad \text{NANA} \quad \text{NNAA}$$  

> **Nota:** Una parola non e' un insieme ma una sequenza ordinata di caratteri che ammette ripetizioni.

---

## Permutazioni con ripetizioni di una sequenza

* Sia $S = s_1, s_2, \dots, s_k$ una sequenza di elementi di $A = \{a_1, \dots, a_n\}$, con cardinalita' $|A| = n$.
* Per ciascun indice $i \in n+1$, definiamo $c_i$ come il numero di volte in cui l'elemento $a_i$ compare all'interno di $S$.
* Di conseguenza, il calcolo delle **permutazioni con ripetizioni** per la sequenza $S$ e' dato da:  

$$\frac{n!}{c_1! \cdot c_2! \cdots c_n!}$$  

#### Esempio

* **ANNA:**  
  
  $$\frac{4!}{2! \cdot 2!} = \frac{24}{4} = 6$$  

  * dove la lettera $A$ compare $2$ volte ($c_A = 2$) e la $N$ compare $2$ volte ($c_N = 2$)

* **NONNO:**  
  $$\frac{5!}{3! \cdot 2!} = \frac{5 \cdot 4 \cdot 3!}{3! \cdot 2} = \frac{20}{2} = 10$$  

# Disposizioni

Sia $A$ un insieme con $|A| = n$. Una **disposizione** degli elementi di $A$ in $k$ posti e' una sequenza ordinata di $k$ elementi distinti scelti tra quelli di $A$:  

$$a_0, a_1, \dots, a_{k-1}$$  

* **Esempio:** Le disposizioni possibili di $A = \{a, b, c, d, e\}$ disposte in $2$ posti sono in totale $20$.
* Il numero delle disposizioni dipende unicamente dalla cardinalita' dell'insieme di partenza e dal numero $k$ di posti considerati.

---

## Calcolo delle disposizioni

Definiamo $D(n, k)$ come il numero complessivo di disposizioni ricavabili da $n$ elementi distinti sistemati in $k$ posizioni:  

$$D(n, k) = \frac{n!}{(n - k)!}$$  

* **Esempio numerico:** Per un insieme di $5$ elementi disposti in $2$ posti, la formula restituisce:  

  $$D(5, 2) = \frac{5!}{(5 - 2)!} = \frac{5!}{3!} = \frac{5 \cdot 4 \cdot 3!}{3!} = 5 \cdot 4 = 20$$  

---

## Relazione con le permutazioni e induzione

Possiamo ricavare le disposizioni anche partendo dalle permutazioni:  

$$D(n, k) = \frac{P(n)}{P(n - k)}$$  

In alternativa, possiamo definirle per induzione (fissato $n$ e per $0 \le k \le n$):
* $D(n, 0) = 1$
* $D(n, k + 1) = D(n, k) \cdot (n - k)$

--- 

# Combinazioni

Sia $A$ un insieme con $|A| = n$. Una **combinazione di $k$ elementi** di $A$ e' un qualsiasi sottoinsieme di $A$ avente cardinalita' $k$.
L'insieme di tutte queste combinazioni si indica con $P_k(A)$, ovvero l'insieme dei $k$-sottoinsiemi di $A$.

* **Esempio pratico:** Se consideriamo $A = \{a, b, c, d, e\}$ e vogliamo formare i gruppi di $3$ elementi, le combinazioni possibili sono in totale $10$:  

  $$\{a,b,c\}, \{a,b,d\}, \{a,b,e\}, \{a,c,d\}, \{a,c,e\}, \{a,d,e\}, \{b,c,d\}, \{b,c,e\}, \{b,d,e\}, \{c,d,e\}$$  

* Il totale delle combinazioni dipende esclusivamente dalla dimensione dell'insieme di partenza ($n$) e dal numero di elementi da scegliere ($k$).

---

## Calcolo delle combinazioni

Il numero di combinazioni di $k$ elementi scelti da un insieme di $n$ elementi prende il nome di **coefficiente binomiale**:  

$$\binom{n}{k} = \frac{n!}{k! \cdot (n - k)!}$$  

* **Applicazione sull'esempio precedente:** Scegliere $3$ elementi da un gruppo di $5$ ($n = 5$, $k = 3$):  

  $$\binom{5}{3} = \frac{5!}{3! \cdot (5 - 3)!} = \frac{5!}{3! \cdot 2!} = \frac{5 \cdot 4 \cdot 3!}{3! \cdot 2} = \frac{20}{2} = 10$$  

---

## Relazione tra combinazioni e disposizioni

Una combinazione equivale a una disposizione in cui l'ordine degli elementi non ha alcuna importanza. 

Poiche' per ogni gruppo di $k$ elementi ci sono $P(k) = k!$ modi diversi di ordinarli, basta dividere le disposizioni per il loro fattoriale:  

$$\binom{n}{k} = \frac{D(n, k)}{P(k)}$$  

## Combinazioni, ricorsivamente

Dato un qualsiasi insieme finito $A$ con cardinalita' $|A| = n$, valgano le seguenti osservazioni:
* L'insieme delle parti e' in biiezione con le sequenze binarie di lunghezza $n$: $\mathcal{P}(A) \cong 2^n$.
* L'insieme dei $k$-sottoinsiemi corrisponde alle sequenze binarie contenenti esattamente $k$ uni:  

  $$P_k(A) \cong \{s \in 2^n \mid s \text{ ha esattamente } k \text{ uni}\}$$  


### Esempio pratico  

Immagina di avere un insieme di oggetti molto ridotto, ad esempio $A = \{a, b, c\}$ (quindi con cardinalita' $n = 3$). Vogliamo trovare i sottoinsiemi che contengono esattamente $k = 2$ elementi (i nostri $2$-sottoinsiemi).  

Se scriviamo tutte le possibili sequenze di lunghezza 
3 ($2^3=8$ combinazioni) e selezioniamo solo quelle che contengono esattamente due 1 (cioe' $k=2$), otteniamo:   

* $(1, 1, 0) \implies \text{include } a \text{ e } b \implies \text{sottoinsieme } \{a, b\}$
* $(1, 0, 1) \implies \text{include } a \text{ e } c \implies \text{sottoinsieme } \{a, c\}$
* $(0, 1, 1) \implies \text{include } b \text{ e } c \implies \text{sottoinsieme } \{b, c\}$

> **Nota:** Contare quanti sottoinsiemi di $k$ elementi si possono formare equivale esattamente a contare quante sequenze di $n$ bit contengono esattamente $k$ volte il numero $1$


## Definizione induttiva del coefficiente binomiale
Definiamo quindi la cardinalita' del coefficiente binomiale come $\binom{n}{k} = |\{s \in 2^n \mid s \text{ ha esattamente } k \text{ uni}\}|$:  

* **Clausola base:**  

  $$\binom{n}{0} = \binom{n}{n} = 1$$  

* **Clausola induttiva:**  

  $$\binom{n}{k} = \binom{n - 1}{k} + \binom{n - 1}{k - 1}$$  

---

# Cardinalita' sfruttando regola di biiezione

I seguenti due problemi sono del tutto equivalenti:

* In quanti modi si possono distribuire $z$ magliette all'interno di $g$ cassetti?
* In quanti modi si possono scegliere $z$ ciambelle tra $g$ gusti differenti (problema di Homer :))?

---

## Rappresentazione come sequenza binaria

Possiamo codificare ogni configurazione come una sequenza binaria dove:
* Gli **$0$** rappresentano gli oggetti (le $z$ magliette o le $z$ ciambelle).
* Gli **$1$** rappresentano i separatori tra i vari contenitori/gusti (i $g - 1$ separatori per distinguere $g$ gruppi).

Un esempio pratico con $g = 5$ gusti ($G_1, G_2, G_3, G_4, G_5$) e una determinata scelta di ciambelle:  

$$\underbrace{00000}_{G_1} \, 1 \, \underbrace{0}_{G_2} \, 1 \, \underbrace{000000}_{G_3} \, 1 \, \underbrace{0}_{G_4} \, 1 \, \underbrace{0000}_{G_5}$$  

La lunghezza totale della stringa binaria e' pari a $z + g - 1$, contenente esattamente $g - 1$ uni.

---

## Calcolo del numero di soluzioni

L'insieme delle soluzioni dei problemi citati e' in biiezione con l'insieme delle sequenze binarie di lunghezza $z + g - 1$ aventi $g - 1$ uni.

* Ricordiamo che il totale delle sequenze binarie di lunghezza $n$ contenenti $k$ uni e' dato dal coefficiente binomiale $\binom{n}{k}$.
* Applicando la regola di biiezione, il numero totale di soluzioni possibili e':  

$$\binom{z + g - 1}{g - 1}$$  
