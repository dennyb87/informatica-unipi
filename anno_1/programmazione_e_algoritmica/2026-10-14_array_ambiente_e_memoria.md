## Valori e riferimenti negli array

Con l'introduzione degli array dobbiamo espandere l'insieme dei valore gestiti dal nostro pseudo-linguaggio, in particolare abbiamo bisogno delle locazioni (o riferimenti) $\mathbb{L}$:

$$V = \mathbb{Z} \cup \mathbb{B} \cup \mathbb{L}$$

Dove:
- $\mathbb{Z}$: interi
- $\mathbb{B}$: booleani
- $\mathbb{L}$: Locazioni di memoria (o riferimenti)

## Ambiente e Memoria

La gestione delle variabili avviene separando l'**Ambiente** (che associa i nomi delle variabili alle rispettive locazioni) e la **Memoria** (che memorizza i valori effettivi o i riferimenti ad altre celle).

```c
int[] voti = [18, 30, 23];
int max = 30;
int m = max;  // dichiarazione 3
int[] v = voti; // dichiarazione 4
```

| Ambiente | Memoria |
| :--- | :--- |
| `voti` $\to L_{\text{voti}}$ | $L_{\text{voti}} \to L_b$ |
| | $L_b \to 3$ |
| | $L_b[0] \to 18$ |
| | $L_b[1] \to 30$ |
| | $L_b[2] \to 23$ |
| `max` $\to L_{\text{max}}$| $L_{\text{max}} \to 30$ |
|`m` $\to L_m$ *(dopo dichiarazione 3)*  | $L_m \to 30$ *(dopo dichiarazione 3)* |
| `v` $\to L_v$ *(dopo dichiarazione 4)* | $L_v \to L_b$ *(dopo dichiarazione 4)* |

Si nota allora che mentre `max` e `m` sono due variabili che puntanto a valori indipendenti, `voti` e `v` puntano allo stesso oggetto, in questo caso un array, in quanto nella dichiarazione 4 e' stato copiato il riferimento $L_b$ invece dell'intero array. Qualsiasi modifica effettuata tramite `v` si riflettera' anche su `voti`. Questa situazione prende il nome di **aliasing** dove `voti` e `v` vengono detti **alias**.

---

### Esercizio: Azzera la prima occorrenza di `k`
Cerca la prima occorrenza di $k$ nell'array, se trovato, lo azzera e interrompe la ricerca.

```c
int i = 0;
bool azzerato = false;

while (i < a.length && !azzerato) {
    if (a[i] == k) {
        a[i] = 0;
        azzerato = true;
    }
    i = i + 1;
}
```

---

### Esercizio: Inversione di un array (reverse)
Inverte l'ordine degli elementi dell'array scambiandoli specularmente.

```c
int i = 0;

while (i < a.length / 2) {
    int T = a[i];
    a[i] = a[a.length - 1 - i];
    a[a.length - 1 - i] = T;
    i = i + 1;
}
```
