# Rappresentazione Posizionale

In un sistema di numerazione posizionale con base $B$, il valore di una cifra dipende dalla sua posizione all'interno del numero.

* **Insieme delle cifre ammissibili:** $C = \{0, 1, \dots, B-1\}$
* **Esempio in base 10 ($B=10$):**
  $$52_{10} = 5 \cdot 10^1 + 2 \cdot 10^0 = 50 + 2 = 52$$

* **Esempio in base 2 ($B=2$):**
  $$1010_2 = 1 \cdot 2^3 + 0 \cdot 2^2 + 1 \cdot 2^1 + 0 \cdot 2^0 = 8 + 0 + 2 + 0 = 10_{10}$$

### Valore Massimo Rappresentabile
Con $n$ bit disponibili, il massimo numero naturale rappresentabile e' dato da:
$$n_{\max} = 2^n - 1 = \sum_{i=0}^{n-1} 2^i$$

**Esempio (3 bit):**  

$111_2 = 2^0+2^1+2^2 = 2^3 - 1 = 7_{10}$

## Conversione di Base

### Da Base 10 a Base 2 (Divisioni Successive)
Per convertire un numero decimale in binario, si divide ripetutamente il numero per la nuova base $B=2$, prendendo i resti in ordine inverso (dall'ultimo al primo).

**Esempio ($154_{10}$ in binario):**
* $154 / 2 = 77$, resto **0**
* $77 / 2 = 38$, resto **1**
* $38 / 2 = 19$, resto **0**
* $19 / 2 = 9$, resto **1**
* $9 / 2 = 4$, resto **1**
* $4 / 2 = 2$, resto **0**
* $2 / 2 = 1$, resto **0**
* $1 / 2 = 0$, resto **1**

$\implies 154_{10} = 10011010_2$

### Conversione Rapida: Base 2 $\leftrightarrow$ Base 8 / Base 16
Poiche' $8 = 2^3$ e $16 = 2^4$, e' possibile convertire direttamente raggruppando i bit:
* **Base 8 (Ottale):** Raggruppamento a gruppi di 3 bit.
* **Base 16 (Esadecimale):** Raggruppamento a gruppi di 4 bit.

$$\underbrace{10}_{2} \, \underbrace{011}_{3} \, \underbrace{010}_{2} \longrightarrow 232_8$$
$$\underbrace{1001}_{9} \, \underbrace{1010}_{A} \longrightarrow 9A_{16}$$

## Rappresentazione dell'informazione nel computer

* **Bit (Binary Digit):** L'unita' minima di informazione $\{0, 1\}$, corrispondente a stati fisici (es. spento/acceso, bassa/alta tensione).
* **Byte:** Unita' composta da 8 bit ($1 \text{ Byte} = 8 \text{ bit}$).

## Overflow
Si parla di **overflow** quando il risultato di un'operazione aritmetica genera un riporto sul bit piu' significativo (MSB - *Most Significant Bit*) che non puo' essere contenuto nel numero di bit prefissato per la rappresentazione.

# Rappresentazione dei Numeri Interi relativi $\mathbb{Z}$

## A. Rappresentazione con modulo e segno

Le prime rappresentazioni prevedevano di utilizzare il bit piu' significativo (MSB) per indicare il segno ($0 = +$, $1 = -$), mentre i restanti bit indicavano il modulo. Questa rappresentazione portava dei problemi tra cui:  

  1. doppia rappresentazione dello zero ($+0$ e $-0$).
  2. rischio di overflow nelle addizioni con segni uguali dove il modulo del risultato supera la capienza dei bit dedicati
  3. rischio di overflow nelle addizioni con segno misto dove i riporti interni sconfinano nel bit di segno

#### Esempio overflow in addizione con segni uguali  

Supponendo di avere 3 bit per il modulo ed 1 bit per il segno per l'operazione $5+4 = 9$:  

$$
\begin{array}{r l}
\text{Riporti:} & 0\;1\;0\;0 \\
& 0\;1\;0\;1 \quad (+5) \\
+ & 0\;1\;0\;0 \quad (+4) \\
\hline
& \mathbf{1}\;\mathbf{0}\;\mathbf{0}\;\mathbf{1} \quad (\mathbf{-1})
\end{array}
$$

In questo caso si verifica un **overflow reale**: la somma dei moduli ($5 + 4 = 9$) supera la capacità dei 3 bit dedicati al valore assoluto, facendo traboccare il riporto nel bit del segno e trasformando la somma di due numeri positivi nel valore errato **$-1$**.
#### Esempio overflow in addizione con segno misto  

Supponendo di avere 3 bit per il modulo ed 1 bit per il segno per l'operazione $2-1 = 1$:  

$$
\begin{array}{r l}
\text{Riporti:} & 0\;0\;0\;0 \\
& 0\;0\;1\;0 \quad (+2) \\
+ & 1\;0\;0\;1 \quad (-1) \\
\hline
& \mathbf{1}\;\mathbf{0}\;\mathbf{1}\;\mathbf{1} \quad (\mathbf{-3})
\end{array}
$$

Senza circuiti condizionali aggiuntivi per separare il segno dal modulo, l'hardware non puo' eseguire sottrazioni usando una semplice somma binaria.  


### B. Complemento a 1 (1's Complement)

Risolve il problema principale della rappresentazione in modulo e segno: permette di eseguire le sottrazioni usando lo stesso circuito addizionatore delle somme, trasformando $A - B$ in una semplice addizione $A + (\sim B)$.

#### Come funziona
* **Numeri positivi:** Iniziano con bit di segno `0` e mantengono il loro valore binario standard
* **Numeri negativi:** Si ottengono invertendo ogni singolo bit del corrispondente positivo con un'operazione logica `NOT` ($a \to \bar{a}$)

#### Riporto di fine giro  

La semplice inversione logica dei bit (NOT) non sottrae il numero da $8 = 2^3$ ($1000_2$, che richiederebbe 4 bit), ma dal valore massimo rappresentabile su 3 bit con tutti 1:

$$(2^3 - 1) - B = \mathbf{7 - B}$$

Mettendo a confronto i due valori:  

$$(8 - B) - (7 - B) = \mathbf{1}$$  

L'operazione logica NOT calcola un numero negativo che e' fin dall'inizio più piccolo di $1$ rispetto al salto matematico necessario per fare il giro completo, e quindi va aggiunto con il riporto. 
Per questo motivo in questa rappresentazione, quando si ha un riporto che supera $2^n-1$ si riporta sull'**LSB**.  

Ad esempio per la somma $2 -1 = 1$ si ha allora che:  

```
Riporti:  1 0 0 
          0 1 0   (+2)
+         1 1 0   (-1)
----------------
1 |       0 0 0   (riporto esterno 1)
+         0 0 1   (somma del riporto finale all'LSB)
----------------
          0 0 1   (+1)
```

Funziona perche' -1 invertito equivale al valore 6 ovvero `001` $\rightarrow$ `110`. Questo significa che se partendo da 2 (`010`) aggiungiamo 6, compieremmo 6 passi in senso orario arrivando fino a `000`. 

```text
                  +0 (000)
           -0 (111)      +1 (001)
       -1 (110)              +2 (010)
           -2 (101)      +3 (011)
                  -3 (100)
```

Il riporto sull'**LSB** ci permette di aggiungere il passo mancante, l'1 che e' stato tolto dal complemento ed arrivare correttamente a `001`.  

> Dato che il $\sim B = 2^n -1 - B$ l'operazione $A + (\sim B)$ equivale a $A + (2^n -1 - B) = (A - B) + 2^n -1$ e se $A \gt B$ il risultato della somma $(A - B) + 2^n - 1$ sara' maggiore o uguale a $2^n$ causando l'overflow rendendo necessario il riporto.

#### Limiti residui
* **Doppio Zero:** permangono due rappresentazioni dello zero, $+0$ ($\mathbf{0000}$) e $-0$ ($\mathbf{1111}$), richiedendo controlli doppi via software/hardware
* **Lentezza del circuito:** la necessita' di sommare il riporto di fine giro al LSB richiede un secondo passaggio di calcolo
* **overflow:** resta il rischio di overflow quando modulo del risultato supera la capienza dei bit dedicati


### C. Complemento a 2 (2's Complement)

E' lo standard utilizzato nei calcolatori moderni. Si ottiene invertendo tutti i bit (`NOT`) e sommando $1$. 

$$-a = \bar{a} + 1$$  

Con **3 bit** si rappresentano 8 valori (da **$-4$ a $+3$**):

| Binario | Decimale | Note |
| :---: | :---: | :--- |
| **`011`** | $+3$ | Valore massimo |
| **`010`** | $+2$ | |
| **`001`** | $+1$ | |
| **`000`** | $0$ | Zero unico |
| **`111`** | $-1$ | NOT(`001`) $+ 1$ |
| **`110`** | $-2$ | NOT(`010`) $+ 1$ |
| **`101`** | $-3$ | NOT(`011`) $+ 1$ |
| **`100`** | $-4$ | Valore minimo extra |

Con questa rappresentazione si ha quindi:  

  1. **Unico zero:** La rappresentazione di $0$ è univoca ($0000$).
  2. **Sommatori unificati:** La sottrazione si riduce a una somma $a - b = a + (-b)$.
  3. **Gestione naturale dell'overflow:** nessun riporto o circuiti dedicati 

---

## Numeri Reali (Virgola Mobile / IEEE 754)

I numeri reali si rappresentano in notazione scientifica:
$$x = \pm m \cdot B^E$$

Dove:
* $\pm$: Bit di **Segno**
* $m$: **Mantissa** (frazione)
* $E$: **Esponente**

Nello standard **IEEE 754** in base 2:
$$\pm r = \pm m \cdot 2^E$$

#### Underflow
In questa rappresentazione continua a permanere il problema dell'overflow,  e si aggiunge quello dell'overflow. Questo si verifica quando un'operazione (tipicamente una sottrazione tra numeri quasi uguali o divisioni) produce un valore troppo piccolo vicinissimo allo zero, non rappresentabile con la precisione a disposizione.

# Rappresentazione dei Numeri Reali (IEEE 754)

La rappresentazione in virgola mobile esprime i numeri reali in **notazione scientifica binaria**:

$$V = (-1)^S \times (1 + M) \times 2^{E}$$

* **Segno ($S$):** 1 bit (`0` = positivo, `1` = negativo).
* **Esponente ($E$):** Memorizza la potenza di 2
* **Mantissa ($M$):** Rappresenta la parte frazionaria

| **sign** | **exponent** | **mantissa** |
| :---: | :---: | :---: |
| `0` | `10000110` | `11010100000000000000000` |
| 1 bit | 8 bit | 23 bit |

**Totale:** 32 bit  

# Dati Testuali e Multimediali

* **Testo:** Codificato tramite standard come **ASCII** (7/8 bit) e **Unicode** (es. UTF-8, UTF-16) per la gestione di tutti i caratteri del mondo
* **Immagini e Audio:** Convertiti in digitale tramite processi di **campionamento** e **quantizzazione**

## Operatori Binari Logici e di Scorrimento (Bit Shift)

### Operatori Logici Bitwise
* **AND** Vale $1$ solo se entrambi i bit sono $1$.
* **OR** Vale $1$ se almeno un bit e' $1$.
* **XOR** Vale $1$ se i bit sono diversi.
* **NOT** Inverte il valore del bit.

### Operatori di Scorrimento (Bit Shift)

| Operatore | Tipo | Descrizione / Esempio | Effetto Aritmetico |
| :--- | :--- | :--- | :--- |
| `n << x` | Shift a Sinistra | $0101_2 \ll 1 = 1010_2$ | Moltiplica per $2^x$ |
| `n >> x` | Shift a Destra (Arithmetical) | $0101_2 \gg 1 = 0010_2$ | Divide per $2^x$ (mantiene segno) |
| `n >>> x` | Shift a Destra Logico | $0101_2 \ggg 1 = 0010_2$ | Inserisce sempre $0$ a sinistra |

