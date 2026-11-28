## Assegnamenti destrutturanti

La **destrutturazione** permette di "spacchettare" un dato strutturato (array o oggetto) per estrarne i valori interni. A sinistra del simbolo `=` si scrive un pattern con i nomi delle variabili che riceveranno i valori corrispondenti. I pattern possono essere annidati ricorsivamente.

### Esempi su array

```typescript
let A: number[] = [4, 7, 1];
let a: number, b: number, c: number, d: number, r: number[];

[a, b] = A;             // a = 4, b = 7
[a, b, c, d] = A;       // a = 4, b = 7, c = 1, d = undefined
[a, b, c = 3, d = 8] = A; // a = 4, b = 7, c = 1, d = 8 (valori di default)
[, , c] = A;            // c = 1 (salta le posizioni vuote)
[a, ...r] = A;          // a = 4, r = [7, 1]

// Scambio di variabili
let x = 1, y = 2;
[y, x] = [x, y];        // x = 2, y = 1

// Valori di ritorno da funzioni
function f(): [number, number] { return [10, 20]; }
[a, b] = f();
```

### Annidamento e tuple

```typescript
let M: number[][] = [[1, 2], [3]];
let p: number, q: number, z: number;
[[p, q], [z]] = M; // Destrutturazione annidata: p = 1, q = 2, z = 3

let T: [number, string] = [1, "x"];
let n: number, s: string;
[n, s] = T; // OK
// [s, n] = T; // ERRORE: tipi incompatibili per posizione
```

### Esempi su oggetti

Negli oggetti si estraggono i valori in base al nome delle proprieta'. Se non si usa `let`/`const`, e' necessario racchiudere l'assegnamento tra parentesi tonde `()` per evitare che `{` venga interpretato come l'inizio di un blocco di codice.

```typescript
let O = { n: "Pippo", a: 35, c: true };
let a: number, c: boolean, r: { n: string, c: boolean };
let eta: number, nome: string;

({ a, c } = O);              // a = 35, c = true
({ a, ...r } = O);           // a = 35, r = { n: "Pippo", c: true }
({ a: eta, n: nome } = O);   // eta = 35, nome = "Pippo"

// Estrarre solo alcuni campi dal ritorno di una funzione
function getObj(): { x: string, y: number, z: boolean } {
    return { x: "a", y: 3, z: true };
}
let y: number, z: boolean;
({ y, z } = getObj());
```

## Valori di default

I valori di default si usano nei parametri delle funzioni o negli assegnamenti destrutturanti per sostituire gli elementi assenti.

* **Regola generale**: il valore di default viene assegnato **solo** quando la variabile riceverebbe `undefined` (non si attiva con `0`, `null` o `""`).

## Spread e rest

Gli operatori di **spread** e **rest** usano la sintassi `...` per trasformare un dato strutturato in una sequenza di elementi singoli (spread) o viceversa (rest).

```typescript
let A = [3, 4, 5];
let B = [1, 2, ...A, 6]; // [1, 2, 3, 4, 5, 6]
let C = [...A, ...B];    // Concatenazione di A e B

let [testa, ...resto] = A; // testa = 3, resto = [4, 5] (rest)
let D = [testa, ...resto]; // [3, 4, 5] (spread)

// Sugli oggetti (in caso di chiavi uguali, vince l'ultima specificata)
let q = { a: 1, b: 2 };
let p = { x: 5, y: 6 };

let p1 = { ...q, c: 3 }; // Copia di q con c = 3
let p2 = { c: 3, ...q }; // Copia di q, c = 3 solo se assente in q

R = {...p,...q} // unione degli oggetti p e q, se hanno chiavi in comune resta quella dell'ultimo specificato (q)
```

### Funzioni con numero variabile di parametri

Il parametro **rest** deve essere sempre l'ultimo nella firma della funzione e raccoglie gli argomenti extra in un array (vuoto `[]` se non ce ne sono).

```typescript
function f(p1: number, p2: number, ...args: number[]): void {
    // args contiene tutti i parametri dal terzo in poi
}
```
> **Nota:** Nello scope di ogni funzione esiste l'oggetto predefinito `arguments` (es. per `f(9, 2, 5)` vale `{"0": 9, "1": 2, "2": 5}`).


## Array come tuple

Le tuple sono array a lunghezza fissa e tipi predeterminati per ciascuna posizione (es. `t: [number, number] = [4, 1]`). Oltre ad acceddere agli elementi e' possibile usarle per passare argomenti a funzioni o restituire piu' valori contemporaneamente da una funzione.

```typescript
function product(a: number, b: number): number {
    return a * b;
}

let args: [number, number] = [4, 2];

product(...args);
```

## Array come liste

Metodi principali per manipolare un array $A = [1, 2, 3, 4]$ in testa o in coda:

| Operazione | Risultato | Nuovo stato di $A$ | Descrizione |
| :--- | :--- | :--- | :--- |
| `A.push(10)` | $5$ | $[1, 2, 3, 4, 10]$ | Aggiunge in coda, ritorna nuova lunghezza |
| `A.pop()` | $4$ | $[1, 2, 3]$ | Estrae e ritorna l'ultimo elemento (coda) |
| `A.shift()` | $1$ | $[2, 3, 4]$ | Estrae e ritorna il primo elemento (testa) |
| `A.unshift(10)` | $5$ | $[10, 1, 2, 3, 4]$ | Aggiunge in testa, ritorna nuova lunghezza |

### Pile e code

* **Pila - LIFO (Last In, First Out)**: l'ultimo elemento inserito e' il primo ad uscire. Si usa `push` per inserire e `pop` per estrarre.
* **Coda - FIFO (First In, First Out)**: il primo elemento inserito e' il primo ad uscire. Si usa `push` per inserire in coda e `shift` per estrarre dalla testa.

* **Nota di complessita'**: `push` e `pop` sono operazioni istantanee, mentre `shift` e `unshift` sono piu' lente perche' devono spostare tutti gli elementi in memoria.

### Ricorsione con destrutturazione

Destrutturare `[testa, ...resto]` permette di scrivere algoritmi ricorsivi sulle liste in modo molto naturale:

```typescript
function len(a: number[]): number {
    if (a.length === 0) return 0;
    let [, ...r] = a;
    return 1 + len(r);
}

function sum(a: number[]): number {
    if (a.length === 0) return 0;
    let [t, ...r] = a;
    return t + sum(r);
}

function max(a: number[]): number {
    if (a.length === 0) return -Infinity;
    let [t, ...r] = a;
    return Math.max(t, max(r));
}
```
