## Massimo di un insieme
Sia $A \subset \mathbb{R}$, con $A \neq \emptyset$. Un elemento $m \in \mathbb{R}$ si dice **massimo di $A$** se:
1. $m \in A$
2. $m \ge a \quad \forall a \in A$

Si scrive $m = \max(A)$.

* **Esempio 1:** $A = [0, 1] \implies \max(A) = 1$
* **Esempio 2:** $B = [0, 1)$ **non ha massimo!**

In analogo si ha che il minimo e' $\min(A) = 0$  

#### **Dimostrazione per assurdo che $B = [0, 1)$ non ha massimo**
 Supponiamo per assurdo che $B$ abbia massimo, ovvero sia $m = \max(B)$.
1. Poiche' $m \in B = [0, 1) \implies m < 1$.
2. Poniamo $\varepsilon = 1 - m > 0$ e consideriamo il punto medio $b = m + \frac{\varepsilon}{2}$.
3. Risulta $b \in B$ e $b > m$, il che contraddice l'ipotesi che $m$ sia il massimo di $B$.
4. **Conclusione:** $m$ non e' il $\max(B)$, dunque $B$ non ammette massimo.

> **Osservazione:** Se un insieme e' *aperto a destra*, non ha massimo. In modo analogo, se e' *aperto a sinistra*, non ha minimo.

## Maggiorante e Insieme dei Maggioranti
Dato $A \subset \mathbb{R}, A \neq \emptyset$, un numero $k \in \mathbb{R}$ si dice **maggiorante di $A$** se:
$$k \ge a \quad \forall a \in A$$

L'insieme di tutti i maggioranti di $A$ si indica con $\mathcal{M}_A$.

* **Esempio 1:** Per $A = [0, 1]$, $1$ e' il massimo ed e' anche il maggiorante, mentre l'insieme dei maggioranti e' $\mathcal{M}_A = [1, +\infty)$.
* **Esempio 2:** Per $A = [0, 1)$ non ha massimo, ma 1 e' comunque il maggiorante.
* **Esempio 3:** Se $A = [2, +\infty)$, allora $\mathcal{M}_A = \emptyset$.
* **Esempio 4:** Se $A = \mathbb{N}$, allora $\mathcal{M}_A = \emptyset$.

> L'insieme dei maggioranti $\mathcal{M}_A$ o e' vuoto oppure contiene infiniti elementi.

Questa definizione vale anche per i minoranti e l'insieme dei minoranti.  

### Insieme Limitato Superiormente e Limitato  

Se $\mathcal{M}_A \neq \varnothing$, allora $A$ si dice **limitato superiormente**. L'insieme dei minoranti e' incvece $m_A$ e se $m_A \ne \varnothing$ allora A si dice **limitato inferiormente**.  

$A \subset \mathbb{R}$ si dice **limitato** se e' sia inferiormente che superiormente limitato.  

> **Osservazione:** $A \subset \mathbb{R}$ e' limitato $\iff \exists h, k \in \mathbb{R}$ tali che:
> $$h \le a \le k \quad \forall a \in A$$



## Estremo Superiore ed Estensione di $\mathbb{R}$

### **Teorema (Sull'estremo superiore)**
Sia $A \subset \mathbb{R}, A \neq \emptyset$ e superiormente limitato.
Allora l'insieme dei maggioranti di $A$ ($\mathcal{M}_A$) ha **minimo**, che si dice **estremo superiore di $A$** e si scrive $\sup(A)$:
$$\sup(A) = \min(\mathcal{M}_A)$$

* **Esempi:**
  * $A = [0, 1] \implies \mathcal{M}_A = [1, +\infty) \implies \sup(A) = 1 = \max(A) = \min(\mathcal{M}_A)$
  * $B = [0, 1) \implies \mathcal{M}_B = [1, +\infty) \implies \sup(B) = 1 = \min(\mathcal{M}_B), \quad \nexists \max(B)$

> **Osservazione:** L'insieme dei maggioranti $\mathcal{M}_A$ e' sempre chiuso a sinistra.
> Se $\exists \max(A)$, allora $\sup(A) = \max(A)$. Stessa cosa vale per $m_A$

### **Caratterizzazione dell'Estremo Superiore**
Sia $A \neq \emptyset$ e limitato superiormente. Un numero $m = \sup(A) \iff$ valgono:
1. $m$ e' un maggiorante: $a \le m \quad \forall a \in A$
2. $m$ è il piu' piccolo dei maggioranti: $\forall \varepsilon > 0 \quad \exists a \in A \quad | \quad a > m - \varepsilon$

## **Retta Reale Estesa $\overline{\mathbb{R}}$**

Definiamo la **retta reale estesa** come:
$$\overline{\mathbb{R}} = \mathbb{R} \cup \{-\infty\} \cup \{+\infty\}$$
in modo che valga $-\infty \le x \le +\infty \quad \forall x \in \overline{\mathbb{R}}$.

* Se $A$ non e' limitato superiormente, si scrive $\sup(A) = +\infty$.
* Se si scrive $\sup(A) < +\infty$, vuolsi dire che $A$ e' limitato superiormente.

#### **Operazioni in $\overline{\mathbb{R}}$**
1. Se $x \neq +\infty \implies x + (-\infty) = -\infty$
2. Se $x \neq -\infty \implies x + (+\infty) = +\infty$
3. Se $x > 0 \implies x \cdot (+\infty) = +\infty \quad \text{e} \quad x \cdot (-\infty) = -\infty$
4. Se $x < 0 \implies x \cdot (-\infty) = +\infty \quad \text{e} \quad x \cdot (+\infty) = -\infty$

#### **Forme Indeterminate:**
$$0 \cdot (-\infty), \quad 0 \cdot (+\infty), \quad +\infty + (-\infty), \quad -\infty + (+\infty)$$

# Parte Intera e proprieta' in $\mathbb{Z}$

> **Osservazione:** Dato $A \subset \mathbb{Z}, A \neq \emptyset$:
> * Se $A$ e' limitato superiormente, allora **ha massimo**.
> * Se $A$ e' limitato inferiormente, allora **ha minimo**.
> *(Valido poiche' $\mathbb{Z}$ e' un insieme discreto).*

## Parte Intera
Dato $x \in \mathbb{R}$, si dice **parte intera di $x$** (e si indica con $[x]$) il numero massimo:
$$[x] = \max\{m \in \mathbb{Z} : m \le x\}$$

* **Esempi:**
  * $[3] = 3$
  * $\left[\frac{25}{10}\right] = [2.5] = 2$
  * $\left[-\frac{25}{10}\right] = [-2.5] = -3$

## Estremi e Massimo di Funzioni

Siano $A \subset \mathbb{R}$ e $f: A \to \mathbb{R}$.

* $f$ si dice **limitata superiormente (o inferiormente)** se lo e' l'insieme immagine $f(A)$
* $f$ ha **massimo** se $f(A)$ ha massimo. Si dice che $M = \max(f) = \max(f(A))$. *(Stessa cosa per $\min(f)$).*
* $\sup(f) = \sup(f(A))$. Se $f$ non e' limitata superiormente, si scrive $\sup(f) = +\infty$
* Se $f$ ha massimo, ogni $x_0 \in A$ tale che $f(x_0) = \max(f)$ si dice **punto di massimo** per $f$. *(Stesso per i punti di minimo).*

> **Osservazione:**
> * Il massimo di $f$ (se esiste) e' **unico**.
> * I **punti di massimo** possono essere molti.
>
> *Esempio:* $f(x) = \sin(x) \implies \max(f) = 1$, mentre i punti di massimo sono $x = \frac{\pi}{2} + 2k\pi \quad \forall k \in \mathbb{Z}$.

* **Esempio pratico:** $f: (0, +\infty) \to \mathbb{R}$, con $f(x) = \frac{1}{x}$
  * $\sup(f) = +\infty \implies \nexists \max(f)$
  * $\inf(f) = 0$, ma $\nexists \min(f)$

---

### **Osservazione sulle Funzioni Crescenti**
Dati $A \subset \mathbb{R}$ e $f: A \to \mathbb{R}$:
1. Se $A$ ha massimo e $f$ e' debolmente/strettamente crescente $\implies f$ ha massimo e $\max(f) = f(\max(A))$.
2. Se $A$ ha minimo e $f$ è debolmente/strettamente crescente $\implies f$ ha minimo e $\min(f) = f(\min(A))$.

---

# Valore Assoluto

Si dice **valore assoluto** di $x \in \mathbb{R}$ il numero:
$$|x| = \max\{-x, x\}$$

---

### **Proprietà del Valore Assoluto**
1. $x \le |x|$
2. $|x| = x \text{ se } x \ge 0, \quad |x| = -x \text{ se } x \le 0$
3. $|x| \ge 0$
4. $|x| = 0 \iff x = 0$
5. $|-x| = |x|$
6. $-|x| \le x \le |x|$
7. Se $M \ge 0$, allora $|x| \le M \iff -M \le x \le M$
8. $|x| \ge M \iff x \ge M \text{ oppure } x \le -M$

> **Nota:** Un'equazione del tipo $|x| \le -2$ **non ha soluzione!**

### **Disuguaglianza Triangolare**
Dati $a, b \in \mathbb{R}$, si ha che:
1. $|a + b| \le |a| + |b|$
2. $\left| |a| - |b| \right| \le |a - b|$

> Se ti muovi di due passi nella stessa direzione, le distanze si sommano esattamente ($\vert{}a + b\vert{} = \vert{}a\vert{} + \vert{}b\vert{}$). Se invece muovi un passo a destra e uno a sinistra (cambi direzione, formando un "angolo" o un'inversione), la distanza netta dal punto di partenza sara' strettamente inferiore alla somma dei due passi singoli ($\vert{}a + b\vert{} < \vert{}a\vert{} + \vert{}b\vert{}$).In sintesi: il nome deriva dal fatto che il percorso diretto non e' mai piu' lungo di un percorso con una deviazione intermedia (che forma i tre lati di un triangolo).

#### **Dimostrazione Disuguaglianza Triangolare (Punto 1)**
Dalla proprieta' 6 del valore assoluto sappiamo che:
$$-|a| \le a \le |a|$$
$$-|b| \le b \le |b|$$

Sommando membro a membro le due disuguaglianze:
$$-(|a| + |b|) \le a + b \le |a| + |b|$$


Applicando la proprieta' 7 con $x = a + b$ e $M = |a| + |b|$, otteniamo direttamente:
$$|a + b| \le |a| + |b|$$

La proprieta' 7 richiede che $M \ge 0$. Poiche' il valore assoluto e' sempre non negativo ($\vert{}a\vert{} \ge 0$ e $\vert{}b\vert{} \ge 0$), la loro somma $M = \vert{}a\vert{} + \vert{}b\vert{}$ e' sicuramente $\ge 0$. La regola e' quindi valida ed eseguibile.

> **Osservazione (estensione):**
> $$|a + b + c| \le |a| + |b| + |c|$$