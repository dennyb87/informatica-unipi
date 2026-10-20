## Tipi base aggiuntivi: `char` e Stringhe (`char[]`)

### Caratteri
Il tipo base `char` permette di rappresentare caratteri singoli codificati secondo standard come ASCII o Unicode.

* **Sintassi**:
  * I singoli caratteri sono racchiusi tra apici singoli, e.g., `'c'`.
  * I caratteri speciali o non stampabili sono rappresentati tramite **sequenze di escape**, come ad esempio:
    * `\t` (tabulazione)
    * `\n` (nuova linea)
* **Valore di Default**: Il valore di default per il tipo `char` e' il carattere nullo `'\0'`.

#### Estensione della Sintassi  

```c
T_b ::= ... // i tipi gia' conosciuti e.g. INT, BOOL
        | CHAR
V ::= ...
        | c  // dove c e' un carattere da tastiera tra apici o una sequenza di escape
```

#### Confronto tra Caratteri
Le operazioni di confronto ($<, \le, >, \ge$) si estendono ai caratteri in base al loro valore numerico nella codifica (ASCII/Unicode).
I caratteri maiuscoli e minuscoli sono codificati in modo sequenziale e indipendente. Di conseguenza, e' possibile verificare se un carattere $c$ e' minuscolo con l'espressione:

$$'a'\ \le\ c\ \le\ 'z'$$

In sintassi logica/di programmazione Mao:

```c
('a' <= c) && (c <= 'z')
```

---

## Stringhe
Le stringhe sono definite come **array (o sequenze) di caratteri**.

* `'b'` $\rightarrow$ indica il singolo **carattere** $b$.
* `"b"` $\rightarrow$ indica una **stringa** composta dal solo carattere $b$.
* `"ciao"` e' equivalente all'array di caratteri: `['c', 'i', 'a', 'o']`.

---

## Assegnamenti Multipli

L'assegnamento multiplo permette di **inizializzare o aggiornare piu' variabili contemporaneamente**.

* **Esempio (JavaScript)**:
  ```javascript
  let x, y, z = 6, 7, 42;
  ```

#### Nota sullo scambio di valori (swap)
Con l'assegnamento multiplo e' possibile scambiare i valori di due variabili senza usare una variabile d'appoggio temporanea:
```text
x, y := y, x;
```
Questo scambia i valori di `x` ed `y` correttamente.

### Differenza tra assegnamento multiplo e sequenziale
L'assegnamento multiplo valuta tutte le espressioni di destra prima di effettuare l'assegnamento a sinistra, a differenza dell'assegnamento sequenziale.

#### Sintassi
$$Ids ::= Id \mid Id, Ids$$

#### Confronto di esecuzione

Dati i valori iniziali nell'Ambiente/Memoria:
* $x \mapsto l_x$, con contenuto di $l_x = 5$
* $y \mapsto l_y$, con contenuto di $l_y = 8$

1. **Assegnamento Multiplo**: `x, y = x + 10, x;`
   * Valutazione parallela: $x+10 = 15$ e $x = 5$.
   * Risultato finale: $x = 15$, $y = 5$.

2. **Assegnamento Sequenziale**:
   ```text
   x := x + 10;
   y := x;
   ```
   * Passaggio 1: $x$ diventa $15$.
   * Passaggio 2: $y$ prende il *nuovo* valore di $x$, quindi anche $y$ diventa $15$.


### Assegnamento multiplo con stringhe
Se `s` ed `t` sono stringhe (`char[]`), l'assegnamento multiplo continua a funzionare in quanto vengono scambiati i **riferimenti** (puntatori) agli array in memoria.

```c
char[] s = "foo";
char[] t = "bar"; 
```

| Ambiente | Memoria |
| :--- | :--- |
| `s` $\to L_s$ | $L_s \to L_a$ |
| | $L_a \to 3$ |
| | $L_a[0] \to \text{'f'}$ |
| | $L_a[1] \to \text{'o'}$ |
| | $L_a[2] \to \text{'o'}$ |
| `t` $\to L_t$ | $L_t \to L_b$ |
| | $L_b \to 3$ |
| | $L_b[0] \to \text{'b'}$ |
| | $L_b[1] \to \text{'a'}$ |
| | $L_b[2] \to \text{'r'}$ |

```c
s, t := t, s;
```

| Ambiente | Memoria |
| :--- | :--- |
| `s` $\to L_s$ | $L_s \to L_b$ (ora s punta al blocco $L_b$) |
| `t` $\to L_t$ | $L_t \to L_a$ (ora t punta al blocco $L_a$) |
| |...|
---

## Direttiva `return`

La direttiva `return` restituisce il risultato di un'espressione, determinando quindi un valore di uscita da un blocco/funzione.

```c
E ::= ... // tutte le espressioni gia' viste
    | C RETURN E;
```

### Esempio: massimo tra due variabili

```c
{
    int max = a;
    if (b > max) {
        max = b;
    }
    return max;
}
```

L'uso della direttiva `return` ci permette di ritornare un valore direttamente dalle funzioni...  

---

# Funzioni

Le funzioni permettono di riutilizzare blocchi di codice passandovi dei parametri.

### Struttura di una Funzione
```c
int max(int a, int b) {
    if (b > a) {
        return b;
    } else {
        return a;
    }
}
```

* **Tipo di Ritorno**: `int` (indica il tipo di dato restituito dalla funzione).
* **Parametri Formali**: `(int a, int b)`.

### Invocazioni di funzione
Esempi di chiamata/invocazione della funzione `max`:

```c
max(12, 18) // returns 18
max(x, 18) // the output depends on x
```