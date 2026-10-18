### Punto isolato
Un punto $x_0 \in A$ si dice **punto isolato** se esiste un intorno $U$ di $x_0$ tale che l'intersezione con l'insieme $A$ contiene solo il punto stesso:  

$$U \cap A = \{x_0\}$$  

### Punto interno e insieme dei punti interni
Un punto $x_0 \in A$ si dice **punto interno** di $A$ se esiste un intorno $U$ di $x_0$ interamente contenuto in $A$:  

$$U \subseteq A$$  

L'insieme di tutti i punti interni si indica con $\mathring{A}$ oppure $\text{int}(A)$.  

*Esempio:* Sia l'intervallo $B = (2, 5)$, allora $\mathring{B} = (2, 5)$ perche' ogni punto dell'intervallo ammette un intorno completamente incluso in $B$.

---

## Punto di minimo locale (o relativo)

Sia $A \subseteq \mathbb{R}$ e $f: A \to \mathbb{R}$  

Un punto $x_0 \in A$ si dice **punto di minimo locale** (o relativo) se esiste un intorno $U$ di $x_0$ tale che:  

$$\forall x \in A \cap U \implies f(x) \ge f(x_0)$$  

Si dice invece **punto di minimo locale stretto** se la disuguaglianza e' stretta per ogni $x$ diverso da $x_0$:  

$$\forall x \in A \cap U \setminus \{x_0\} \implies f(x) \gt f(x_0)$$  

> **Osservazione:** Se un punto $x_0$ e' punto di minimo assoluto per la funzione, allora e' anche automaticamente un punto di minimo locale.

## Punto di massimo locale (o relativo)

Analogamente un punto $x_0 \in A$ si dice **punto di massimo locale** (o relativo) se esiste un intorno $U$ di $x_0$ tale che:  

$$\forall x \in A \cap U \implies f(x) \le f(x_0)$$  

Si dice invece **punto di massimo locale stretto** se la disuguaglianza e' stretta per ogni $x$ diverso da $x_0$:  

$$\forall x \in A \cap U \setminus \{x_0\} \implies f(x) \lt f(x_0)$$  

> **Osservazione:** Se un punto $x_0$ e' punto di massimo assoluto per la funzione, allora e' anche automaticamente un punto di massimo locale.

---

## Limiti di una Funzione

Il concetto di limite descrive il comportamento di una funzione quando la variabile indipendente si avvicina a un determinato punto $x_0$.

### Definizione Generale di Limite
Sia $A \subseteq \mathbb{R}$, $f: A \to \mathbb{R}$ e $x_0$ un punto di accumulazione per $A$. Si dice che $l \in \overline{\mathbb{R}}$ e' il **limite** di $f$ per $x$ che tende a $x_0$, e si scrive:  

$$\lim_{x \to x_0} f(x) = l$$  

se per ogni intorno $V$ di $l$ esiste un intorno $U$ di $x_0$ tale che:  

$$\forall x \in U \cap A \setminus \{x_0\} \implies f(x) \in V$$  

### Interpretazione con delta ed epsilon (caso finito)
Nel caso in cui $x_0 \in \mathbb{R}$ e $l \in \mathbb{R}$ siano numeri reali finiti, gli intorni si esprimono come intervalli:
- $U = (x_0 - \delta, x_0 + \delta)$ con $\delta > 0$
- $V = (l - \varepsilon, l + \varepsilon)$ con $\varepsilon > 0$

La definizione diventa:
$$\forall \varepsilon > 0, \quad \exists \delta > 0 \quad \text{t.c.} \quad \forall x \in A, \quad 0 < |x - x_0| < \delta,\quad x \neq x_0 \implies |f(x) - l| < \varepsilon$$

Questa struttura formale e' molto simile alla definizione di continuita', con la fondamentale differenza che nel limite il punto $x_0$ puo' non appartenere al dominio della funzione.

> **Osservazione:** Se $x_0$ e' punto di accumulazione per $A$ allora $f$ e' continua in $x_0$ se e solo se:   
> $$\lim_{x \to x_0} f(x) = f(x_0)$$


## Limiti infiniti
Se consideriamo il caso in cui il limite tende a infinito ($l = +\infty$) con $x_0 \in \mathbb{R}$, l'intorno di $l$ diventa del tipo $(m, +\infty)$. La definizione formale e':
$$\lim_{x \to x_0} f(x) = +\infty \iff \forall m \in \mathbb{R}, \quad \exists \delta > 0 \quad \text{t.c.} \quad 0 < |x - x_0| < \delta \text{ e } x \in A \implies f(x) > m$$
*Esempio:* $\lim_{x \to 0} \frac{1}{x^2} = +\infty$, dove scegliendo $\delta = \frac{1}{\sqrt{m}}$ si soddisfa la condizione.

> In altre parole, per quanto tu possa scegliere una quota $m$ gigantesca e arbitraria, ci sara' sempre un intorno di $x_0$ in cui la funzione $f(x)$ supera $m$.

---

# Teorema di unicita' del limite
> Se il limite di una funzione per $x \to x_0$ esiste, allora esso e' **unico**.

### Limite destro e limite sinistro
E' possibile studiare il comportamento di una funzione avvicinandosi a $x_0$ da una sola direzione:
- **Limite destro:** $\lim_{x \to x_0^+} f(x) = l$
- **Limite sinistro:** $\lim_{x \to x_0^-} f(x) = l$

Un teorema fondamentale stabilisce che il limite globale esiste se e solo se esistono sia il limite destro che quello sinistro e sono uguali fra loro:  

$$\lim_{x \to x_0} f(x) = l \iff \lim_{x \to x_0^+} f(x) = \lim_{x \to x_0^-} f(x) = l$$  

### Dimostrazione della non esistenza del limite
Dimostriamo per assurdo che non esiste il limite:  

$$\lim_{x \to +\infty} \sin x$$  

* Supponiamo che esista un limite finito $l \in \mathbb{R}$ per $x \to +\infty$
* Scegliamo $\varepsilon = \frac{1}{2}$ nella definizione di limite.
* Dalla definizione di limite, dovrebbe esistere un intorno di $+\infty$ in cui:  

   $$|\sin x - l| < \frac{1}{2} \implies l - \frac{1}{2} < \sin x < l + \frac{1}{2}$$  

* Questo implica che per valori di $x$ sufficientemente grandi la funzione $\sin x$ dovrebbe rimanere confinata all'interno di un intervallo di ampiezza pari a $1$.
* Tuttavia, la funzione $\sin x$ oscilla periodicamente tra $-1$ e $1$, coprendo un'ampiezza totale pari a $2$.
* Risulta quindi impossibile contenere tutte le oscillazioni di ampiezza $2$ in una striscia di ampiezza $1$.
* Si giunge a una **contraddizione** (assurdo), pertanto il limite **non existe**.

## Teorema della permanenza del segno
Sia $A \subseteq \mathbb{R}, f: A \to \mathbb{R}$ e $x_0 \in \text{Acc}(A)$. Se esiste il limite $\lim_{x \to x_0} f(x) = l \in \overline{\mathbb{R}}$ con $l \neq 0$, allora esiste un intorno $U$ di $x_0$ tale che per ogni $x \in U \cap A \setminus \{x_0\}$, la funzione $f(x)$ ha lo stesso segno di $l$.

## Teorema di confronto
Siano $f, g: A \to \mathbb{R}$ tali che $f(x) \le g(x)$ in un intorno di $x_0$ (escluso). Se esistono i rispettivi limiti:  

$$\lim_{x \to x_0} f(x) = l_1, \quad \lim_{x \to x_0} g(x) = l_2$$  

allora si ha:  

$$l_1 \le l_2$$  

> **Nota bene:** Il teorema non si estende alle disuguaglianze strette. Anche se $f(x) < g(x)$ rigorosamente (come $f(x) = -\frac{1}{x}$ e $g(x) = \frac{1}{x}$), al limite si puo' avere comunque l'uguaglianza ($l_1 \le l_2$) ovvero, il limite indebolisce la disuguaglianza stretta!

---

## Continuita'

Una funzione $f$ si dice **continua** in un punto $x_0$ se il valore del limite coincide con il valore della funzione nel punto:  

$$\lim_{x \to x_0} f(x) = f(x_0)$$  

Dal momento che cio' richiede che $x_0$ appartenga al dominio, la continuita' puo' essere vista anche come continuita' a destra e a sinistra: $f$ e' continua in $x_0$ se e solo se e' continua sia a destra che a sinistra in tale punto. Consideriamo la funzione a tratti $f: \mathbb{R} \to \mathbb{R}$:  

$$f(x) = \begin{cases} 1 & \text{se } x \ge 0 \\ -1 & \text{se } x < 0 \end{cases}$$  

Da destra di $0$:  

$$\lim_{x \to 0^+} f(x) = 1 = f(0)$$  

La funzione e' **continua da destra** in $x_0 = 0$.

Da sinistra di $0$:  

$$\lim_{x \to 0^-} f(x) = -1 \neq f(0)$$  

La funzione **non e' continua da sinistra** in $x_0 = 0$, ne' e' continua globalmente in $0$.

*Osservazione generale sulla continuita':* Una funzione e' continua in $x_0$ se e solo se e' sia continua da destra che da sinistra in $x_0$, ossia:  

$$\lim_{x \to x_0} f(x) = f(x_0) \iff \lim_{x \to x_0^+} f(x) = \lim_{x \to x_0^-} f(x) = f(x_0)$$