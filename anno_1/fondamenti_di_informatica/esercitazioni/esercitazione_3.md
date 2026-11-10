## Esercizio 1
Una sequenza di caratteri (stringa) $a_1 a_2 \dots a_n$ si dice palindroma se
$$a_1 a_2 \dots a_n = a_n a_{n-1} \dots a_1$$
cioe' leggerla da sinistra verso destra e' come leggerla da destra verso sinistra. Ad esempio, le sequenze $bob$, $1010101$ e $AB313BA$ sono palindrome.

Calcolare il numero di targhe di automobile (italiane) palindrome: si ricorda che una targa e' una stringa della forma $XXNNNXX$, dove ogni $X$ e' una di 22 possibili lettere dell'alfabeto inglese, e ogni $N$ e' una cifra in $\{0, \dots, 9\}$.

### Svolgimento

Per la regola del prodotto cartesiano sappiamo che il numero totale di targhe possibili sarebbe:

$22\cdot22\cdot10\cdot10\cdot10\cdot22\cdot22$

Per trovare il numero delle sole targhe palindrome e' sufficiente rendersi conto che una volta fissati alcuni simboli, gli altri devono necessariamente ripetersi riducendo ad 1 le possibili scelte. Questo equivale a dividere il numero totale di targhe possibili per il numero di combinazioni di simboli che dobbiamo escludere, ovvero:

$\frac{22\cdot22\cdot10\cdot10\cdot\cancel{10}\cdot\cancel{22}\cdot\cancel{22}}{\cancel{10}\cdot\cancel{22}\cdot\cancel{22}} = 22\cdot22\cdot10\cdot10\cdot1\cdot1\cdot1 = 48\ 400$

---

## Esercizio 2
Anna, Bob, Chiara e Davide giocano a carte con un mazzo da 52 (non ci sono carte ripetute). All'inizio del gioco ad ognuno dei 4 giocatori vanno 5 carte, cioe' Anna pesca 5 carte, poi Bob 5, poi Chiara 5 e poi Davide 5. L'assegnamento di un insieme di 5 carte ad ognuno dei 4 giocatori determina la configurazione iniziale del gioco. Quante possibili configurazioni iniziali ci sono?

### Svolgimento

Stiamo parlando di un mazzo da gioco, senza ripetizioni e dove l'ordine delle carte delle mani dei giocatori non conta. Allora si utilizza il coefficiente binomiale per trovare il numero di combinazioni di $k$ carte (la mano) scelti da un insieme di $n$ carte (il mazzo) per il primo giocatore:

$\binom{n}{k} = \binom{52}{5} = \frac{52!}{5!\cdot(52-5)!}$

Il secondo giocatore avra' pero' solo $52-5 = 47$ carte disponibili e cosi' via, percio':  

$\binom{52}{5}\cdot\binom{47}{5}\cdot\binom{42}{5}\cdot\binom{37}{5} = \frac{52!}{5!^4\cdot32!} = 1\ 4478\ 262\ ...$

---

## Esercizio 3
Un gruppo di 6 amici decide di cenare assieme al ristorante: per semplicita' identifichiamo i 6 amici con i numeri da 1 a 6, e vediamo idealmente i tavoli come cerchi con i commensali seduti lungo la circonferenza. Per esempio, se i 6 amici siedono in un unico tavolo, disporsi come $345612$ o $561234$ e' equivalente a $123456$ perche' rappresentano la stessa rotazione ciclica: in tal senso, le rotazioni cicliche $123456$, $234561$, $345612$, $456123$, $561234$, $612345$ rappresentano lo stesso modo distinto di disporsi attorno al tavolo e quindi non vanno conteggiate. Chiarito questo punto, passiamo alle domande:

1. Supponiamo che il gruppo trovi un tavolo di 6 posti: in quanti modi distinti i 6 amici possono disporsi attorno al tavolo?

### Svolgimento

Intuitivamente direi che e' come chiedersi quanti cicli Hamiltoniani *distinti* esistono in una cricca di `6` nodi. I cicli hamiltoniani sono $n!$ ma alcuni usano lo stesso insieme di archi quindi togliamo le rotazioni e i cicli inversi $n \cdot 2$. Allora i `6` amici possono disporsi attorno al tavolo in `60` modi distinti.

$\frac{n!}{n\cdot2} = \frac{6!}{6\cdot2} = \frac{1\cdot\cancel{2}\cdot3\cdot4\cdot5\cdot\cancel{6}}{\cancel{6}\cdot\cancel{2}} = 60$

