# Invariante di Ciclo (*Loop Invariant*)

Nel contesto dei cicli software (come il ciclo `while`), un **invariante** e' una condizione o proprieta' logica che rimane **sempre vera** in tre momenti chiave:
1. **Prima** dell'inizio del ciclo (inizializzazione).
2. **Prima e dopo** ogni singola iterazione (conservazione).
3. **Al termine** del ciclo (terminazione).

Serve a garantire e dimostrare matematicamente la correttezza di un algoritmo e aiuta il programmatore a capire come inizializzare le variabili e come aggiornarle correttamente dentro il ciclo.  

### Esempio: Divisione Intera ($x = q \cdot y + r$)

Calcoliamo il quoziente $q$ e il resto $r$ della divisione tra $x$ e $y$ mediante sottrazioni successive sapendo che $r$ e' sempre $\ge 0$  


```c
// 1. INIZIALIZZAZIONE
int r = x
int q = 0
// Verifica: x == (0 * y) + x (VERO)

while (r >= y) {
    r := r - y
    q := q + 1
    // Dopo l'aggiornamento:
    // x = (q + 1)*y + (r - y) = q*y + r (VERO)
}
```

L'equazione $x = q \cdot y + r$ continua a valere dopo ogni iterazione dimostrando la correttezza dell'algoritmo.  

# Terminazione e divergenza  

Introducendo i cicli nei programmi, e' possibile che l'esecuzione **diverga** (ovvero non produca mai un risultato finale).


* **Divergenza:** Il ciclo entra in un *loop infinito* e non termina mai
* **Terminazione:** Il programma completa l'esecuzione e produce il risultato finale in un **tempo finito**

> Il corpo del ciclo deve contenere almeno un'istruzione che porti la **guardia** (la condizione del `while`) a diventare **falsa**

### Condizioni Necessarie per la Terminazione

Affinche' un ciclo possa terminare, devono essere soddisfatte le seguenti due condizioni strutturali:

1. **Variabile nella guardia:** La guardia deve contenere almeno una variabile di stato.
2. **Aggiornamento della variabile:** Il corpo del ciclo deve contenere un aggiornamento (riassegnamento) per quella specifica variabile

> ⚠️ **Nota:** Queste condizioni sono **necessarie ma non sufficienti**!
> *Esempio:* In `while x > 0: x = x + 1`, la variabile `x` e' sia nella guardia sia aggiornata nel corpo, ma il ciclo diverge comunque perche' `x` cresce anziche' decrescere verso la condizione di uscita.


Esempio 1: Assenza di aggiornamento della variabile della guardia
```c
while (x > 0) {
    y := y + 1;
}
```

Esempio 2: Aggiornamento nella direzione sbagliata
```c
while (x > 0) {
    x := x + 1;
}
```

Esempio 3: Ciclo corretto (Terminazione Garantita)
```c
while (x > 0) {
    x := x - 1;
}
```
