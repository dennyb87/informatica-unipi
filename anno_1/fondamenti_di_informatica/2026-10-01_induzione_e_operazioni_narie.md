# Fattoriale

Il fattoriale di un numero $n \in \mathbb{N}$ si definisce in modo informale come:
$$n! = 1 \cdot 2 \cdot 3 \cdot ... \cdot n$$

**Definizione induttiva formale:**
1. **Caso Base:** $0! = 1$
2. **Passo Induttivo:** $(n+1)! = (n+1) \cdot n!$

---

### Teorema

Vogliamo dimostrare per induzione che per tutti i numeri naturali positivi ($\mathbb{N}^+ = \{1, 2, 3, \dots\}$) vale la disuguaglianza:  

$$n! \ge 2^{n-1} \quad \forall n \in \mathbb{N}^+$$

**Caso Base (CB)** per $n = 1$:
  $$P(1) \equiv 1! \ge 2^{1-1} \implies 1 \ge 2^0 \implies 1 \ge 1 \quad \checkmark$$

**Passo Induttivo (PI)**:  
  * $P(n) \implies P(n+1)$
  * *Ipotesi Induttiva:* $n! \ge 2^{n-1}$
  * *Tesi:* $(n+1)! \ge 2^n$

**Dimostrazione:**
$$(n+1)! = (n+1) \cdot n!$$

Per ipotesi induttiva sappiamo che $n! \ge 2^{n-1}$ quindi moltiplicando per $(n+1)$ la disuguaglianza continua a valere ($n \in \mathbb{Z}^+$ quindi positivo) ottenendo:  
$$(n+1)! = (n+1) \cdot n! \ge (n+1) \cdot 2^{n-1}$$  

Semplificando e concentrandoci sulla disequazione...  

$$(n+1)! \ge (n+1) \cdot 2^{n-1}$$

Ora vogliamo dimostrare che $(n+1) \cdot 2^{n-1} \ge 2^n$ e sapendo con certezza che $(n+1) \ge 2$ essendo $n \in \mathbb{N}$ possiamo sostituire il solo blocco $(n+1)$ con il numero $2$ (che e' il minimo possibile) al termine destro, lasciando il fattore $2^{n-1}$ intatto:  

$$(n+1) \cdot 2^{n-1} \ge 2 \cdot 2^{n-1} = 2^n$$  

Di conseguenza:
$$(n+1)! \ge 2^n \quad \checkmark$$

---

## 2. Operatori $n$-ari, Associatività ed Elementi Neutri

Sia $\otimes$ una generica operazione binaria definita su un insieme $S \times S \to S$:

* **Associatività:** $x \otimes (y \otimes z) = (x \otimes y) \otimes z$
* **Elemento Neutro (Unità) $e$:** $x \otimes e = x \quad \text{e} \quad e \otimes x = x$

### Tabella degli Elementi Neutri

| Dominio / Insieme | Operazione ($\otimes$) | Elemento Neutro ($e$) |
| :--- | :---: | :---: |
| $\mathbb{N} \times \mathbb{N} \to \mathbb{N}$ | $+$ (Somma) | $0$ |
| $\mathbb{N} \times \mathbb{N} \to \mathbb{N}$ | $\cdot$ (Prodotto) | $1$ |
| $\text{Sets} \times \text{Sets}$ | $\cup$ (Unione) | $\emptyset$ |
| $\text{Sets} \times \text{Sets}$ | $\cap$ (Intersezione) | $U$ (Insieme Universo) |
| $\text{Bool} \times \text{Bool}$ | $\land$ (AND) | $\text{True}$ |
| $\text{Bool} \times \text{Bool}$ | $\lor$ (OR) | $\text{False}$ |

---

## Sommatoria, Produttoria e Operazioni Generiche

### Definizione di Sommatoria $\sum$
Sia $a : \mathbb{N}^+ \to \mathbb{N}$ una successione $a_1, a_2, \dots, a_n$.

* **Definizione Informale:** $\sum_{i=1}^n a_i = a_1 + a_2 + \dots + a_n$ *(non sufficiente per dimostrazioni formali)*
* **Definizione Induttiva:**
  * **CB:** $\sum_{i=1}^0 a_i = 0$ *(elemento neutro della somma)*
  * **CI:** $\sum_{i=1}^{n+1} a_i = \left( \sum_{i=1}^n a_i \right) + a_{n+1}$

> **Verifica di consistenza:**
> $$\sum_{i=1}^2 a_i = \left( \sum_{i=1}^1 a_i \right) + a_2 = \left( \sum_{i=1}^0 a_i + a_1 \right) + a_2 = 0 + a_1 + a_2 = a_1 + a_2 \quad \checkmark$$

---

### Numeri Triangolari e somma dei dispari

I **Numeri Triangolari** rappresentano la somma dei primi $n$ interi:
$$T_n = 1 + 2 + \dots + n = \sum_{i=1}^n i$$

#### Esempio: Dimostrazione per la somma dei primi $n$ numeri dispari
Vogliamo dimostrare che:
$$\sum_{i=1}^n (2i - 1) = n^2$$

1. **Caso Base ($n=0$):**
   $$\sum_{i=1}^0 (2i - 1) = 0 = 0^2 \quad \checkmark \quad (\text{per definizione induttiva CB})$$

2. **Passo Induttivo ($n \implies n+1$):**
   * *Ipotesi Induttiva:* $\sum_{i=1}^n (2i - 1) = n^2$
   * *Tesi:* $\sum_{i=1}^{n+1} (2i - 1) = (n+1)^2$

   **Svolgimento:**
   $$\sum_{i=1}^{n+1} (2i - 1) = \left( \sum_{i=1}^n (2i - 1) \right) + (2(n+1) - 1)$$

   Sostituiamo $n^2$ alla sommatoria (ipotesi induttiva):
   $$= n^2 + (2(n+1) - 1)$$
   $$ = n^2 + 2n + 2 - 1$$  
   $$= n^2 + 2n + 1$$  
   $$= (n+1)^2 \quad \checkmark$$

---

### Estensione ad altre operazioni $n$-arie

Tutte le operazioni binarie associative dotate di elemento neutro possono essere estese a versione $n$-aria:

* **Produttoria:** 
  $$\prod_{i=1}^n i = 1 \cdot 2 \cdot 3 \cdots n = n!$$
  * Caso Base: $\prod_{i=1}^0 a_i = 1$ (elemento neutro della moltiplicazione)
* **Unione $n$-aria:** 
  $$\bigcup_{i=k}^n A_i = A_k \cup A_{k+1} \cup \dots \cup A_n$$
  * Caso Base: $\bigcup_{i=1}^0 A_i = \emptyset$
* **Intersezione $n$-aria:** 
  $$\bigcap_{i=k}^n A_i = A_k \cap A_{k+1} \cap \dots \cap A_n$$
  * Caso Base: $\bigcap_{i=1}^0 A_i = U$

---

## Leggi di De Morgan $n$-arie

La legge di De Morgan standard per due insiemi afferma che $\overline{A \cup B} = \bar{A} \cap \bar{B}$.  
Vogliamo verificare se vale per un generico $n$ di insiemi:

$$\overline{\bigcup_{i=1}^n A_i} = \bigcap_{i=1}^n \bar{A}_i$$

### Dimostrazione per Induzione

* **Caso Base ($n=0$):**
  $$\overline{\bigcup_{i=1}^0 A_i} = \bar{\emptyset} = U$$
  $$\bigcap_{i=1}^0 \bar{A}_i = U$$
  Quindi $U = U$ $\checkmark$.

* **Passo Induttivo ($n \implies n+1$):**
  * *Ipotesi Induttiva:* $\overline{\bigcup_{i=1}^n A_i} = \bigcap_{i=1}^n \bar{A}_i$
  * *Tesi:* $\overline{\bigcup_{i=1}^{n+1} A_i} = \bigcap_{i=1}^{n+1} \bar{A}_i$

  **Svolgimento:**
  $$\overline{\bigcup_{i=1}^{n+1} A_i} = \overline{\left( \bigcup_{i=1}^n A_i \right) \cup A_{n+1}}$$

  Applicando la legge di De Morgan per due insiemi:
  $$= \overline{\left( \bigcup_{i=1}^n A_i \right)} \cap \bar{A}_{n+1}$$

  Applicando l'ipotesi induttiva:
  $$= \left( \bigcap_{i=1}^n \bar{A}_i \right) \cap \bar{A}_{n+1}$$

  Per definizione induttiva dell'intersezione $n$-aria:
  $$= \bigcap_{i=1}^{n+1} \bar{A}_i \quad \checkmark$$

---

## 5. Sequenza di Fibonacci e Induzione Forte

### 5.1 Proprietà di Fibonacci
Data la sequenza di Fibonacci $f_n$, si può dimostrare per induzione la seguente proprietà per $\forall n \in \mathbb{N}^+$:

$$\sum_{i=1}^n f_i^2 = f_n \cdot f_{n+1}$$

---

### 5.2 Principio di Induzione Forte sui Naturali

Mentre nell'induzione classica si assume vera la proprietà solo per $n$ per dimostrare $n+1$, nell'**Induzione Forte** si assume la proprietà vera per **tutti gli elementi minori di $n$**.

**Regola d'Inferenza:**

$$\frac{\forall n . \left( (\forall i < n . P(i)) \implies P(n) \right)}{\forall n . P(n)}$$

```mermaid
graph LR
    A["Assunzione: P(i) è vera per OGNI i < n"] --> B["Dimostrazione: P(n) è vera"]
    B --> C["Conclusione: P(n) è vera per OGNI n in N"]
```

---

### 5.3 Applicazione: Teorema Fondamentale dell'Aritmetica

Un classico esempio di applicazione dell'induzione forte è la dimostrazione del **Teorema Fondamentale dell'Aritmetica**:

> Ogni numero naturale $n \in \mathbb{N}^+$ con $n > 1$ è un numero primo oppure può essere espresso come prodotto di numeri primi.