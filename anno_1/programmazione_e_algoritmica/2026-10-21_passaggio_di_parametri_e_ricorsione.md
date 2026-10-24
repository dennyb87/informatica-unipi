# Passaggio di parametri

Quando viene definita e invocata una funzione, si distingue tra due tipi di parametri:

* **Parametri Formali**: Definiti nella firma (*signature*) della funzione (es. `int max(int a, int b)` dove `a` e `b` sono parametri formali).
* **Parametri Attuali**: I valori o le variabili reali passati al momento della chiamata (es. `max(12, 18)` dove `12` e `18` sono parametri attuali).

### Passaggio per Valore
Nel passaggio per valore, i parametri attuali **non vengono modificati**. La funzione lavora su una copia locale dei dati.

### Passaggio per Riferimento
Nel passaggio per riferimento, la funzione opera **direttamente sui parametri attuali** (fenomeno noto come *aliasing*), con il potenziale **side effect** della modifica dei valori originali dei parametri attuali.

**Esempio di Aliasing ed effetto collaterale:**

| Ambiente | Memoria |
| :--- | :--- |
| `c` $\to l_1$ | $l_1 \to 3$ |
| `a` $\to l_1$ | |


In questo caso, sia la variabile `c` che il parametro `a` puntano alla stessa locazione di memoria $l_2$, quindi modificare `a` modifica direttamente il valore associato a `c`.


In **MAO**:
* I **tipi base** (come `int`) vengono passati **per valore**
* Il tipo **Array** viene passato **per riferimento**

### Esempio: Estrazione da Array

Consideriamo la seguente funzione che estrae un valore da un array e lo azzera:

```c
int estrai(int[] a, int i) {
    int v = a[i];
    a[i] = 0;
    return v;
}
```

Esecuzione del codice:
```c
int b = [10, 2];
estrai(b, 0);
```

#### Stato dell'Ambiente e della Memoria

| Ambiente | Memoria |
| :--- | :--- |
| `b` $\to l_1$ | $l_1 \to l_b$ |
| | $l_b \to 2$ |
| | $l_b[0] \to 10 \ (\to 0)$ |
| | $l_b[1] \to 2$ |
| `a` $\to l_2$ | $l_2 \to l_b$ |
| `i` $\to l_3$ | $l_3 \to 0$ |
| `v` $\to l_4$ | $l_4 \to 10$ |

> **Nota sull'uscita dalla funzione:**  
> All'uscita della funzione, le variabili locali e parametri `a`, `i`, `v` vengono eliminati dall'**ambiente**, ma la modifica all'array rimane salvata nella **memoria**!

---

## Sintassi delle funzioni

La sintassi astratta per la dichiarazione di una funzione e' espressa come:

$$C ::= \dots \mid T \text{ Id}(D_s) \, E$$

Dove:
* $T$: e' il **tipo di ritorno** della funzione.
* $\text{Id}$: e' il **nome della funzione**.
* $D_s$: e' la **lista dei parametri formali** ($D_s = T_1 \text{Id}_1, T_2 \text{Id}_2, \dots$).
* $E$: e' il **blocco di codice/espressione** ritornato, tipicamente nella forma $\{ C; \text{return } E; \}$.

## Esempio: Clonazione di un Array

La variabile del clone creato viene rimosso dall'ambiente locale al termine della funzione, la funzione ritorna il "puntatore" (o l'indirizzo base) del nuovo array/vettore.  

```c
int[] clone(int[] v) {
    int[] a, int i = new int[v.length], 0;
    while (i < v.length) {
        a[i] := v[i];
        i := i+1;
    }
    return a;   // ritorna l'indirizzo base dell'array creato
}               // mentre la variabile a viene tolta dall'ambiente
```
## Stintassi chiamata di funzione

```c
E ::= ... | Id(Es)
```
La chiamata (o invocazione) di una funzione e' un'espressione che, dopo avere instanziato i parametri formali della funzione con i valori dei parametri attuali restituisce il valore ottenuto valutando il corpo della funzione.

## Valutazione di funzione  

Sia la funzione:

```c
T Id(Ds) {
    C
    return E;
}
---

Per valutarla occorre `Id(Es)` che corrisponde a:  

```c
{
    Ds = Es;
    C
    return E;
}
```

In termini di codice e' equivalente ad avere ad esempio una funzione `max`:  

```c
int max(int a, int b) {
    if (b > a) { return b }
    return a;
}
```

la cui invocazione sara' `max(3, 5)` che corrisponde a valutare:  

```c
{
    int a, int b = 3, 5;
    if (b > a) { return b }
    return a;
}
```

## Ricorsione

La ricorsione si verifica quando abbiamo **funzioni che chiamano se stesse**. Una chiamata ricorsiva puo' essere:  

* **Diretta**: La funzione $f$ chiama direttamente se stessa ($f \to f$).
* **Indiretta**: La funzione $f$ chiama una funzione $g$, la quale a sua volta chiama $f$ ($f \to g \to f$).

```c
int fattoriale(int n) {
    // Caso base: se n e' 0 o 1, il fattoriale e' 1
    if (n <= 1) {
        return 1;
    }
    // Passo ricorsivo: chiama se stesso con n - 1
    return n * fattoriale(n - 1);
}
```

`fattoriale(3)` restituisce $3 \times \text{fattoriale}(2)$  

`fattoriale(2)` restituisce $2 \times \text{fattoriale}(1)$  

`fattoriale(1)` incontra il caso base e restituisce $1$  

Risalendo le chiamate si ottiene: $3 \times 2 \times 1 = 6$  
