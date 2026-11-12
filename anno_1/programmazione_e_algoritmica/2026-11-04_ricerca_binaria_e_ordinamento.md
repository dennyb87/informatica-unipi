# Ricerca binaria

La ricerca binaria e' un algoritmo efficiente per trovare la posizione di un elemento (chiave $v$) all'interno di un array $a$ di dimensione $n$, presupponendo che l'array sia gia' **ordinato**.

### Idea fondamentale
Ad ogni passo si confronta la chiave $v$ con l'elemento centrale dell'array $a[cx]$:
* Se $a[cx] == v$, l'elemento e' stato trovato in posizione $cx$.
* Se $a[cx] < v$, la chiave si puo' trovare solo nella meta' destra, quindi si aggiorna l'indice sinistro: $sx = cx + 1$.
* Se $a[cx] > v$, la chiave si puo' trovare solo nella meta' sinistra, quindi si aggiorna l'indice destro: $dx = cx - 1$.

### Versione iterativa

```c
int ricercaBinaria(int[] a, int v) {
    // a deve essere gia' ordinato
    int sx = 0;
    int dx = a.length - 1;
    int pos = -1;
    int cx;

    while (sx <= dx && pos == -1) {
        cx = (sx + dx) / 2;
        if (a[cx] == v) {
            pos = cx;
        } else if (a[cx] < v) {
            sx = cx + 1;
        } else { // v < a[cx]
            dx = cx - 1;
        }
    }
    return pos;
}
```

### Analisi del numero di confronti (caso peggiore)

Dopo ogni confronto senza successo, la dimensione dello spazio di ricerca viene dimezzata:

1. Inizio: $n$
2. Dopo 1 confronto: $\frac{n}{2}$
3. Dopo 2 confronti: $\frac{n}{2^2}$
4. Dopo $i$ confronti: $\frac{n}{2^i}$

La ricerca termina al massimo quando la porzione di array si riduce a dimensione $1$:  

$$\frac{n}{2^i} \approx 1 \implies 2^i \approx n \implies i \approx \log_2 n$$  

* **Numero di confronti al caso pessimo**: $C(n) \approx \log_2 n$
* **Tempo di esecuzione**: $T(n)$ cresce come $C(n)$ quindi $T(n) \le \text{cost} + \log_2 n$

### Versione ricorsiva

La prima chiamata per avviare la ricerca sara': `ricercaBinariaRic(a, v, 0, a.length - 1)`.

```c
int ricercaBinariaRic(int[] a, int v, int sx, int dx) {
    if (sx > dx) {
        return -1;
    }
    
    int cx = (sx + dx) / 2;

    if (a[cx] == v) {
        return cx;
    } else if (a[cx] < v) {
        return ricercaBinariaRic(a, v, cx + 1, dx);
    } else { // v < a[cx]
        return ricercaBinariaRic(a, v, sx, cx - 1);
    }
}
```

Per la versione ricorsiva vale la relazione di ricorrenza:  

$$C(n) \le 1 + C\left(\frac{n}{2}\right)$$  

> Il `+1` rappresenta il singolo confronto eseguito nel passo corrente prima di effettuare la chiamata ricorsiva.  

$$T(n) \le \text{cost} \cdot \log_2 n$$  
$$T(n) \sim \log_2 n$$  

> Il numero di passaggi raddoppia a ogni livello di scomposizione, applicando la ricorrenza a $T\left(\frac{n}{2}\right)$ si dimezza l'argomento ad ogni passo, quindi $\frac{n}{2}$ diventa $\frac{n}{4}$, fino a $\frac{n}{2^i}$). Per risalire da un problema di dimensione uno fino a $n$ occorre esattamente un numero di passaggi pari a $\log_2 n$.

---

# Problema dell'ordinamento (Insertion Sort)

Gli algoritmi basati unicamente su confronti prendono in input un array disordinato e producono in output lo stesso array ordinato in modo debolmente decrescente (o *non descrescente* per chi lo preferisce, non io ;).

* **Input**: array $a$ di interi di lunghezza $n = a.\text{length}$
* **Output**: array $a$ ordinato tali che $a[0] \le a[1] \le a[2] \le \dots \le a[n-1]$

### Algoritmo Insertion Sort

Insertion Sort e' un algoritmo **incrementale**. Ad ogni passo $j$ (con $j = 1, \dots, n-1$), l'elemento $a[j]$ viene inserito nella sua corretta posizione all'interno del sotto-array gia' ordinato $a[0 \dots j-1]$.

#### Esempio figurato
1. `[7, 2, 4, 5, 3, 1]` $\rightarrow$ si inserisce 2 al posto giusto $\rightarrow$ `[2, 7, 4, 5, 3, 1]`
2. `[2, 7, 4, 5, 3, 1]` $\rightarrow$ si inserisce 4 $\rightarrow$ `[2, 4, 7, 5, 3, 1]`
3. `[2, 4, 7, 5, 3, 1]` $\rightarrow$ si inserisce 5 $\rightarrow$ `[2, 4, 5, 7, 3, 1]`
4. E cosi' via fino ad ottenere `[1, 2, 3, 4, 5, 7]`.

### Implementazione

```c
void insertionSort(int[] a) {
    int n = a.length;
    int i, j, key;

    for (j = 1; j < n; j++) {
        // Tengo traccia del valore corrente key
        key = a[j];
        i = j - 1;

        // Sposto gli elementi maggiori di key di una posizione a destra
        while (i >= 0 && key < a[i]) {
            a[i + 1] = a[i];
            i = i - 1;
        }
        
        // Posiziono key nel punto corretto liberato
        a[i + 1] = key;
    }
}
```

---

## Dimostrazione di correttezza tramite invariante di ciclo

L'**invariante di ciclo** e' una proprieta' che rimane vera ad ogni iterazione del ciclo `for`.

> **Invariante**: All'inizio di ogni iterazione del ciclo `for` (con indice $j$), il sotto-array $a[0 \dots j-1]$ e' **ordinato** e contiene gli stessi elementi originariamente presenti nelle prime $j$ posizioni dell'array.

La correttezza e' dimostrata in 3 passaggi:

1. **Inizializzazione**:
   * Prima della prima iterazione ($j = 1$), il sotto-array e' composto dal solo elemento $a[0]$.
   * Un sotto-array di un solo elemento e' banalmente ordinato e contiene l'elemento originale. L'invariante e' valida.

2. **Conservazione**:
   * Assumiamo che $a[0 \dots j-1]$ sia ordinato prima dell'iterazione $j$.
   * Il corpo del ciclo sposta verso destra tutti gli elementi di $a[0 \dots j-1]$ maggiori di $key = a[j]$ e inserisce $key$ nella posizione opportuna.
   * Al termine del passo $j$, il sotto-array $a[0 \dots j]$ e' ordinato e contiene gli elementi originali di $a[0 \dots j]$. Incrementando $j$ per il prossimo ciclo, la proprieta' rimane valida.

3. **Conclusione**:
   * Il ciclo termina quando $j = n$.
   * Sostituendo $j = n$ nell'invariante, otteniamo che il sotto-array $a[0 \dots n-1]$ e' ordinato e contiene gli stessi elementi originari.
   * Siccome $a[0 \dots n-1]$ rappresenta l'intero array $a$, l'array e' completamente **ordinato**.

---

## Analisi della complessita' di Insertion Sort

Il tempo di esecuzione dipende dal numero di confronti effettuati dalla guardia del ciclo `while` (`i >= 0 && key < a[i]`).

### 1. Caso ottimo
Il caso ottimo si verifica quando l'array e' **gia' ordinato**.
* Ad ogni passo $j$, il test `key < a[i]` risulta subito `false`
* Viene effettuato solo **1 confronto** per ciascun passo $j$.  

$$C_{\text{ottimo}}(n) = \sum_{j=1}^{n-1} 1 = n - 1$$  

Il tempo $T_{\text{ottimo}}(n)$ cresce come $C_{\text{ottimo}}(n)$ quindi e' lineare.

---

### 2. Caso pessimo
Il caso pessimo si verifica quando l'array e' ordinato in **ordine inverso**.
* Ad ogni passo $j$, l'elemento $key$ e' piu' piccolo di tutti quelli che lo precedono.
* La guardia del ciclo `while` e' sempre vera finche' $i$ non diventa $< 0$.
* Per ogni passo $j$ si eseguono esattamente $j$ confronti.  

$$C_{\text{pessimo}}(n) = \sum_{j=1}^{n-1} j = \frac{(n-1) \cdot n}{2} = \frac{n^2 - n}{2}$$  

Notare che $\frac{n(n-1)}{2} = \binom{n}{2}$, ossia il numero di coppie non ordinate presenti in un array di $n$ elementi.

Il tempo cresce in modo **quadratico**: $T_{\text{pessimo}}(n) = n^2$.

---

### 3. Caso medio
Nel caso medio, per ciascun elemento $a[j]$, ci si aspetta che esso sia piu' piccolo di circa la meta' degli elementi che lo precedono.

* Ad ogni passo $j$ si effettuano circa $\frac{j}{2}$ iterazioni e confronti.  

$$C_{\text{medio}}(n) = \sum_{j=1}^{n-1} \frac{j}{2} = \frac{1}{2} \sum_{j=1}^{n-1} j = \frac{1}{2} \binom{n}{2} = \frac{n^2 - n}{4}$$  

Il tempo di esecuzione rimane quindi nell'ordine di complessita' **quadratica**: $T_{\text{medio}}(n) = n^2$.