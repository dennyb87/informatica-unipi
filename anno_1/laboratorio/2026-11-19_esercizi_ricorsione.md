## Pari e dispari

Un numero naturale $n \ge 0$ puo' essere definito pari o dispari sfruttando una definizione ricorsiva incrociata (ricorsione mutua):
* Un numero $n$ e' pari se $n = 0$, oppure se $n - 1$ e' dispari.
* Un numero $n$ e' dispari se $n \neq 0$ e $n - 1$ e' pari.

```typescript
function pari(n: number): boolean {
    if (n === 0) return true;
    return dispari(n - 1);
}

function dispari(n: number): boolean {
    if (n === 0) return false;
    return pari(n - 1);
}
```

## Massimo comune divisore

Il Massimo Comune Divisore (MCD) di due numeri interi $a$ e $b$ puo' essere calcolato in modo ricorsivo tramite l'algoritmo di Euclide.  

$$\text{MCD}(a, b) = \text{MCD}(b, a \bmod b)$$  

Il procedimento viene ripetuto sostituendo ad $a$ il valore di $b$, e a $b$ il resto della divisione intera $a \bmod b$, finche' il secondo numero non diventa $0$. A quel punto, il valore di $a$ rappresenta il massimo comune divisore cercato.

```typescript
function mcd(a: number, b: number): number {
    if (b === 0) {
        return a;
    }
    return mcd(b, a % b);
}
```

## Operazioni sulle stringhe

Per operare ricorsivamente sulle stringhe e' utile estrarre sottostringhe. In TypeScript / JavaScript si utilizza il metodo `slice`.

```typescript
// s e' una stringa
s.slice(inizio, fine)
```
Produce la sottostringa compresa tra l'indice `inizio` (incluso) e l'indice `fine` (escluso). Se `fine` e' negativo, indica la posizione contata a partire dal fondo della stringa.

### Esempio di utilizzo

```typescript
let testo: string = "Ciao mondo";
let out1: string = testo.slice(1, 4);   // Output: "iao"
let out2: string = testo.slice(1, -1);  // Output: "iao mond"
```

## Stringa palindroma

Una stringa e' detta palindroma se puo' essere letta allo stesso modo da sinistra a destra e da destra a sinistra.

### Logica ricorsiva

1. **Caso base**: Una stringa vuota o di lunghezza 1 (con $s.length \le 1$) e' sempre palindroma.
2. **Passo ricorsivo**: Se il primo e l'ultimo carattere coincidono ($s[0] === s[s.length - 1]$), la stringa e' palindroma se e solo se e' palindroma la sottostringa interna (ottenuta rimuovendo il primo e l'ultimo carattere con `s.slice(1, -1)`).

```typescript
function palindroma(s: string): boolean {
    if (s.length > 1) {
        if (s[0] === s[s.length - 1]) {
            return palindroma(s.slice(1, -1));
        } else {
            return false
        }
    }
    return true;
}
```

## Grammatica e bilanciamento parentesi

Data una grammatica con la seguente regola di produzione:
$$S \rightarrow (S) \mid SS \mid \varepsilon$$
dove $\varepsilon$ rappresenta la stringa vuota, si vuole scrivere una funzione ricorsiva per verificare se una stringa appartiene al linguaggio generato.

### Regole di validita'

* **Regola $\varepsilon$**: La stringa vuota `""` e' sempre valida.
* **Regola $(S)$**: Se la stringa inizia con `(` e finisce con `)`, ed e' del tipo `(sub)`, occorre verificare se la sottostringa interna `sub` soddisfa la grammatica $S$.
* **Regola $SS$**: La stringa puo' essere vista come concatenazione di due stringhe valide $S_1$ e $S_2$. Se esiste un punto di divisione (split) all'indice $i$ tale per cui sia la parte sinistra che quella destra soddisfano $S$, allora la stringa e' valida.

### Esempi di esecuzione

```typescript
console.log(matchesGrammar(""));       // true (regola \epsilon)
console.log(matchesGrammar("(())"));   // true (regola (S))
console.log(matchesGrammar("()"));     // true (regola SS con split a indice 2)
console.log(matchesGrammar("()()"));   // true (regola SS con split a indice 2)
console.log(matchesGrammar("())()"));  // false
console.log(matchesGrammar(")("));     // false
```

### Implementazione ricorsiva

```typescript
function matchesGrammar(s: string): boolean {
    // Regola epsilon: stringa vuota e' valida
    if (s.length === 0) return true;

    // Regola (S): Se inizia con '(' e finisce con ')', controlliamo l'interno
    if (s[0] === '(' && s[s.length - 1] === ')') {
        // Verifica se rimuovendo gli estremi otteniamo una stringa valida 
        if (matchesGrammar(s.slice(1, -1))) {
            return true;
        }
    }

    // Regola SS: suddivisione in due sottostringhe entrambe valide
    for (let i = 1; i < s.length; i++) {
        let sinistra = s.slice(0, i);
        let destra = s.slice(i);
        if (matchesGrammar(sinistra) && matchesGrammar(destra)) {
            return true;
        }
    }

    return false;
}
```

## Teorema degli zeri di Bolzano

Il Teorema di Bolzano (o teorema degli zeri) stabilisce le condizioni per l'esistenza di una radice per una funzione continua.

### Enunciato

Sia $f : [a, b] \rightarrow \mathbb{R}$ una funzione continua nell'intervallo $[a, b]$. Supponiamo che $f(a)$ e $f(b)$ abbiano segno opposto, ossia:
$$f(a) < 0 < f(b) \quad \text{oppure} \quad f(b) < 0 < f(a)$$

Allora esiste almeno un punto $x_0 \in (a, b)$ tale che:
$$f(x_0) = 0$$

## Ricerca ricorsiva degli zeri

Si vuole quindi dividere l'intervallo trovando il punto medio con:  
   $$m = \frac{a + b}{2}$$  

Se la lunghezza dell'intervallo $(b - a)$ e' inferiore alla tolleranza minima di $10^{-6}$, la ricerca termina e viene restituito $m$. Altrimenti, si valuta il segno del prodotto $f(a) \cdot f(m)$:
   * Se sono discordi allora $f(a) \cdot f(m) \le 0$ e per il teorema lo zero si trova prioprio nell'intervallo $[a, m]$
   * Altrimenti lo zero si trova nell'intervallo di destra $[m, b]$

Si procede infine con la chiamata ricorsiva sul nuovo intervallo ridotto.

Di seguito la ricerca dello zero per la funzione $f(x) = x^3 - 1$ nell'intervallo $[a, b]$:

```typescript
function f(x: number): number {
    return x ** 3 - 1;
}

function trovaZero(a: number, b: number): number {
    let m = (a + b) / 2;
    let tolleranza = 1e-6;

    if (b - a < tolleranza) {
        return m;
    }

    if (f(a) * f(m) <= 0) {
        return trovaZero(a, m);  // Lo zero e' nella prima meta'
    } else {
        return trovaZero(m, b);  // Lo zero e' nella seconda meta'
    }
}
```