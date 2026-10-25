## Limiti notevoli e forme indeterminate

### Limiti logaritmici notevoli

Analizziamo la forma indeterminata $0 \cdot (-\infty)$:  

$$\lim_{x \to 0^+} x \log x = 0 \cdot (-\infty) \quad \text{?}$$  

Per risolverla, applichiamo un **cambio di variabile**:  

Sia $y = \log x \implies x = e^y$.  

Se $x \to 0^+$, allora $y \to -\infty$.  

$$\lim_{y \to -\infty} e^y \cdot y = e^{-\infty} \cdot (-\infty) = 0 \cdot (-\infty) \quad \text{?}$$  

Siamo di nuovo nella stessa forma indeterminata, allora facciamo un'ulteriore **sostituzione**:  

$z = -y$. Se $y \to -\infty$, allora $z \to +\infty$:  

$$\lim_{z \to +\infty} e^{-z} \cdot (-z) = \lim_{z \to +\infty} \frac{-z}{e^z} = 0$$  

*Intuizione:* L'esponenziale al denominatore cresce piu' velocemente di qualsiasi potenza di $z$, guidando il limite a $0$.

---

### Generalizzazione con $\alpha > 0$

Calcoliamo:  

$$\lim_{x \to 0^+} x^\alpha \log x \quad \text{con } \alpha > 0$$  

Sostituzione:
Sia $y = x^\alpha$ (poiche' $x \to 0^+ \implies y \to 0^+$), elevando entrambe i membri all'esponente reciproco, si ha $x = y^{\frac{1}{\alpha}}$.  

$$\lim_{y \to 0^+} y \log\left(y^{\frac{1}{\alpha}}\right) = \lim_{y \to 0^+} y \cdot \frac{1}{\alpha} \log y = 0$$  

> **Nota**: $y \cdot \frac{1}{\alpha} \log y$ e' esattamente nella forma del limite notevole dimostrato in precedenza moltiplicato per una costante $\frac{1}{\alpha}$ e una costante moltiplicata per zero fa zero!

---

### Limite notevole dell'esponenziale

Consideriamo la forma indeterminata $1^{+\infty}$:  

$$\lim_{x \to 0^+} (1+x)^{\frac{1}{x}} = (1+0^+)^{\frac{1}{0^+}} = 1^{+\infty} \quad \text{(Forma Indeterminata)}$$  

Usiamo l'identita' $a^b = e^{b \log a}$:  

$$\lim_{x \to 0^+} e^{\log\left[(1+x)^{\frac{1}{x}}\right]} = e^{\lim_{x \to 0^+} \frac{1}{x} \log(1+x)}$$  

Poiche' il limite notevole al limite dell'esponente vale:  

$$\lim_{x \to 0^+} \frac{\log(1+x)}{x} = 1$$  

Otteniamo:  

$$e^1 = e$$  

---

### Gestione di $f(x)^{g(x)}$ e forme indeterminate

Quando si presenta un limite della forma $\lim f(x)^{g(x)}$, lo riscriviamo sempre sfruttando l'esponenziale e il logaritmo:

$$f(x)^{g(x)} = e^{\log\left(f(x)^{g(x)}\right)} = e^{g(x) \cdot \log f(x)}$$

In questo modo trasformiamo una potenza in un **prodotto** all'esponente, che sappiamo gestire piu' facilmente.

#### Casi di indeterminazione per $g(x) \cdot \log f(x)$:
1. **Se $g \to 0$ e $f \to +\infty$**:
   $$\log f \to +\infty \implies 0 \cdot (+\infty) \implies \text{Forma } (+\infty)^0$$
2. **Se $g \to 0$ e $f \to 0^+$**:
   $$\log f \to -\infty \implies 0 \cdot (-\infty) \implies \text{Forma } (0^+)^0$$
3. **Se $g \to \pm\infty$ e $f \to 1$**:
   $$\log f \to 0 \implies (\pm\infty) \cdot 0 \implies \text{Forma } 1^{\pm\infty}$$

*Esempio:*  

Calcolare $\lim_{x \to 0^+} x^x = 0^0 \text{?}$  

Riscriviamo:  

$$\lim_{x \to 0^+} e^{x \log x} = e^0 = 1$$  

---

## Teorema di Weierstrass generalizzato

### Enunciato
Siano $a, b \in \overline{\mathbb{R}}$ e $f: (a,b) \to \mathbb{R}$ una funzione **continua** tale che esistano i limiti agli estremi:
$$\exists \lim_{x \to a^+} f(x) = l_1 \quad \text{e} \quad \lim_{x \to b^-} f(x) = l_2$$

Allora valgono i seguenti risultati:
* $f$ e' **limitata inferiormente** $\iff l_1 \neq -\infty \text{ e } l_2 \neq -\infty$
* $f$ e' **limitata superiormente** $\iff l_1 \neq +\infty \text{ e } l_2 \neq +\infty$
* $f$ e' **limitata** $\iff l_1 \in \mathbb{R} \text{ e } l_2 \in \mathbb{R}$
* $f$ **ha minimo** $\iff \exists x_0 \in (a,b) \text{ t.c. } f(x_0) \le \min\{l_1, l_2\}$
* $f$ **ha massimo** $\iff \exists x_1 \in (a,b) \text{ t.c. } f(x_1) \ge \max\{l_1, l_2\}$

*Osservazione:* I risultati valgono anche nel caso di intervalli semiaperti con $a \in \mathbb{R}, f:[a,b) \to \mathbb{R}$ oppure $b \in \mathbb{R}, f:(a,b] \to \mathbb{R}$.

---

### Esempio Applicativo

Sia $f: \mathbb{R} \to \mathbb{R}$ definita da:
$$f(x) = \frac{x^2 + |x| + x}{1 + x^2}$$

Esplicitiamo il valore assoluto:
$$f(x) = \begin{cases} \frac{2x^2 + x}{1 + x^2} & \text{se } x \ge 0 \\ \frac{x}{1 + x^2} & \text{se } x < 0 \end{cases}$$

Calcoliamo i limiti agli estremi ($a = -\infty, b = +\infty$):
- $l_1 = \lim_{x \to -\infty} \frac{x}{1+x^2} = 0$
- $l_2 = \lim_{x \to +\infty} \frac{2x^2 + x}{1+x^2} = 2$

#### Verifica Minimo e Massimo:
1. **Esiste il minimo?** Dobbiamo verificare se $\exists x_0 \text{ t.c. } f(x_0) \le \min\{0, 2\} = 0$.
   Proviamo con un punto negativo, ad esempio $x = -3$:
   $$f(-3) = \frac{-3}{1 + (-3)^2} = -\frac{3}{10} \le 0$$
   Poiche' $f(-3) < 0$, **il minimo esiste**.

2. **Esiste il massimo?** Dobbiamo verificare se $\exists x_1 \text{ t.c. } f(x_1) \ge \max\{0, 2\} = 2$.
   Verifichiamo se l'equazione $f(x) \ge 2$ ha soluzioni per $x \ge 0$:
   $$\frac{2x^2 + x}{1+x^2} \ge 2 \implies 2x^2 + x \ge 2(1+x^2) \implies 2x^2 + x \ge 2 + 2x^2 \implies x \ge 2$$
   Esistono punti (es. $x = 2$ dove $f(2) = 2$, oppure $x = 3$ dove $f(3) > 2$) in cui $f(x) \ge 2$. Quindi **il massimo esiste**.

---

# Simboli di Landau: O-piccolo ($o$)

### Definizione
Siano $A \subset \mathbb{R}$, $x_0 \in \text{Acc}(A)$ e $f, g: A \to \mathbb{R}$.
Si dice che $f$ e' **o-piccolo di $g$ per $x \to x_0$**, e si scrive:
$$f = o(g) \quad \text{per } x \to x_0$$  

> Ovvero $f(x)$ va a $x_0$ molto piu' velocemente di $g(x)$  
> 
se esiste una funzione $\omega(x)$ tale che:
$$\lim_{x \to x_0} \omega(x) = 0 \quad \text{e} \quad f(x) = g(x) \cdot \omega(x)$$

*Osservazione:* Se $g(x) \neq 0$ in un intorno di $x_0$, la definizione e' equivalente a:
$$\lim_{x \to x_0} \frac{f(x)}{g(x)} = 0$$
Infatti: $\frac{f(x)}{g(x)} = \frac{g(x) \cdot \omega(x)}{g(x)} = \omega(x) \to 0$.

*Esempio:*
Siano $f(x) = x^5$ e $g(x) = x^3$ per $x \to 0$:
$$\lim_{x \to 0} \frac{f(x)}{g(x)} = \lim_{x \to 0} \frac{x^5}{x^3} = \lim_{x \to 0} x^2 = 0 \implies x^5 = o(x^3)$$


> **Nota**: Nel contesto degli o-piccoli dire $x^5 = o(x^3)$ non significa dire che sono uguali, e' in realta' un abuso di notazione. Piu' precisamente stiamo dicendo che $x^5 \in o(x^3)$ ovvero appartiene a una famiglia infinita di funzioni che tendono a zero piu' velocemente di $x^3$.  

### Interpretazione (per $x \to 0$)

Il simbolo $o(g(x))$ indica **"qualcosa che va a zero piu' velocemente di $g(x)$"** ovvero una quantita' trascurabile rispetto a $g(x)$.

* **$o(1)$**: un termine che tende a $0$.
* **$o(x)$**: un termine più piccolo di $x$ (es. $x^2, x^3$).
* **$o(x^2)$**: un termine più piccolo di $x^2$ (es. $x^3, x^4$).

### A cosa servono ?  

Servono a **semplificare i calcoli** approssimando funzioni complesse e isolando l'errore trascurabile. Ad esempio, come dimostreremo a breve, lo sviluppo al primo ordine di $\sin x$ e':

$$\sin x = x + o(x)$$  


Geometricamente rappresenta la retta tangente alla curva nel punto $x = 0$. Funziona bene solo se ti trovi vicinissimo a zero.  

### Proprieta' degli o-piccoli

* $f(x) \cdot o(g(x)) = o(f(x) \cdot g(x))$
* Se $k \in \mathbb{R}, k \neq 0 \implies o(k \cdot g) = o(g)$
* $o(g) + o(g) = o(g)$ *(Osservazione: $o(g) - o(g) = o(g)$)*
* Se $\lim_{x \to x_0} f(x) = 0 \implies f(x) \cdot g(x) = o(g(x))$
* Se $\lim_{x \to x_0} f(x) = 0 \implies o(g) + o(f \cdot g) = o(g)$
* $o(o(g)) = o(g)$
* $o(f + g) = o(f) + o(g)$

#### Confronto di potenze per $x \to 0$:
Se $\alpha > \beta > 0$, allora per $x \to 0$:  

$$x^\alpha = o(x^\beta)$$  

*Dimostrazione:*  

$$\lim_{x \to 0} \frac{x^\alpha}{x^\beta} = \lim_{x \to 0} x^{\alpha - \beta} = 0 \quad (\text{poiche' } \alpha - \beta > 0)$$  

---

### Esempio di verifica

Verificare che per $x \to 0$, $f(x) = \tan x \cdot \sin x = o(x)$:  

$$\lim_{x \to 0} \frac{f(x)}{x} = \lim_{x \to 0} \frac{\tan x \cdot \sin x}{x} = \lim_{x \to 0} \tan x \cdot \lim_{x \to 0} \frac{\sin x}{x} = 0 \cdot 1 = 0 \implies f(x) = o(x)$$

---

## Sviluppi al "primo" ordine

A partire dai limiti notevoli per $x \to 0$, possiamo ricavare le approssimazioni locali con $o$-piccolo:

1. **Seno:**  
   $$\lim_{x \to 0} \frac{\sin x}{x} = 1 \iff \lim_{x \to 0} \left(\frac{\sin x}{x} - 1\right) = 0 \iff \lim_{x \to 0} \frac{\sin x - x}{x} = 0$$  

   $$\implies \sin x - x = o(x) \implies \mathbf{\sin x = x + o(x)}$$  

2. **Coseno:**  
   $$\lim_{x \to 0} \frac{1 - \cos x}{x^2} = \frac{1}{2} \implies \mathbf{\cos x = 1 - \frac{x^2}{2} + o(x^2)}$$  

3. **Tangente:**  
   $$\mathbf{\tan x = x + o(x)}$$  

4. **Esponenziale:**  
   $$\lim_{x \to 0} \frac{e^x - 1}{x} = 1 \implies \mathbf{e^x = 1 + x + o(x)}$$  

5. **Logaritmo:**  
   $$\lim_{x \to 0} \frac{\log(1+x)}{x} = 1 \implies \mathbf{\log(1+x) = x + o(x)}$$  

---

### Calcolo con le potenze di sviluppi

Calcoliamo $\sin^2 x$ per $x \to 0$:
$$\sin x = x + o(x)$$  

$$\sin^2 x = (\sin x)^2 = (x + o(x))^2 = x^2 + 2x \cdot o(x) + (o(x))^2$$  

$$= x^2 + o(2x \cdot x) + o(x^2) = x^2 + o(2x^2) + o(x^2) = x^2 + o(x^2) + o(x^2) = \mathbf{x^2 + o(x^2)}$$  

---

### Significato di $o(1)$

Cosa vuol dire $o(1)$ per $x \to x_0$?  

$$f(x) = o(1) \iff \lim_{x \to x_0} \frac{f(x)}{1} = 0 \iff \lim_{x \to x_0} f(x) = 0$$  

In sintesi, **$o(1)$ rappresenta un qualsiasi infinitesimo** che tende a $0$.

---

## Esempio Completo di Calcolo Limite con $o$-piccolo

Calcolare il limite:  

$$\lim_{x \to 0} \frac{\cos(\sin^2 x) - 1}{x^4}$$  

### Passaggio 1: Sostituzione delle componenti interne
Sappiamo che $\sin^2 x = x^2 + o(x^2)$.
Poniamo $t = \sin^2 x$. Quando $x \to 0$, anche $t \to 0$.  

Dallo sviluppo del coseno:

$$\cos t = 1 - \frac{t^2}{2} + o(t^2)$$  

### Passaggio 2: Sviluppo di $\cos(\sin^2 x)$  

Sostituiamo $t = x^2 + o(x^2)$:  

$$\cos(\sin^2 x) = 1 - \frac{(x^2 + o(x^2))^2}{2} + o\left((x^2 + o(x^2))^2\right)$$  

Sviluppiamo il quadrato del binomio sfruttando $o(1)$:  

$$(x^2 + o(x^2))^2 = \left[x^2(1 + o(1))\right]^2 = x^4 (1 + o(1))^2 = x^4 (1 + o(1))$$  

$$o\left((x^2 + o(x^2))^2\right) = o\left(x^4(1 + o(1))\right) = o(x^4)$$  

Sostituendo indietro:  

$$\cos(\sin^2 x) = 1 - \frac{x^4 (1 + o(1))}{2} + o(x^4) = 1 - \frac{x^4}{2} + o(x^4) + o(x^4) = \mathbf{1 - \frac{x^4}{2} + o(x^4)}$$  

### Passaggio 3: Calcolo del Limite Finale  

$$\lim_{x \to 0} \frac{\cos(\sin^2 x) - 1}{x^4} = \lim_{x \to 0} \frac{\left(1 - \frac{x^4}{2} + o(x^4)\right) - 1}{x^4}$$  

$$= \lim_{x \to 0} \frac{-\frac{x^4}{2} + o(x^4)}{x^4} = \lim_{x \to 0} \frac{x^4 \left(-\frac{1}{2} + o(1)\right)}{x^4} = -\frac{1}{2} + 0 = \mathbf{-\frac{1}{2}}$$  
