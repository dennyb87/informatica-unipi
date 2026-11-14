# Insiemi e multi-insiemi in TypeScript

## Definizione di insieme

Un insieme e' una collezione di elementi distinti e non ordinati, come ad esempio $\{\text{mela}, \text{pera}, \text{banana}\}$ oppure $\{2, 3, 5, 7\}$.

Le proprieta' fondamentali di un insieme sono:
* Ogni elemento compare al massimo una sola volta.
* L'ordine e la quantita' con cui vengono elencati gli elementi sono irrilevanti:
  $$\{\text{mela}, \text{pera}\} = \{\text{pera}, \text{mela}\}$$
  $$\{\text{mela}, \text{pera}, \text{pera}\} = \{\text{mela}, \text{pera}\}$$

A differenza degli **array**, in cui l'ordine e i duplicati contano ($[\text{mela}, \text{pera}] \neq [\text{pera}, \text{mela}]$ e $[\text{mela}, \text{pera}, \text{pera}] \neq [\text{mela}, \text{pera}]$), negli insiemi cio' che conta e' solo la presenza o meno di un elemento.

## Rappresentazione degli insiemi in TypeScript

TypeScript offre delle classi di sistema per implementare:
* Insiemi: $\text{Set}\langle T \rangle$
* Multi-insiemi via $\text{Map}\langle T, \text{number} \rangle$
* $\text{Set}$ accetta elementi di qualunque tipo e risolve alcune limitazioni che osserveremo

Le scopriremo dopo aver affrontato:
* La programmazione ad oggetti in TypeScript
* Tipizzazione avanzata con i *generics*

... nel secondo semestre!

Per il momento vogliamo esplorare come potremmo implementare/rappresentare gli insiemi con gli strumenti in nostro possesso fino ad ora.

## Modellare gli insiemi senza classi native

In TypeScript possiamo rappresentare un insieme tramite un oggetto (`Object`), usando le chiavi per indicare gli elementi e il valore booleano `true` per segnalarne la presenza (es. `{ rosso: true, verde: true }`).

Possiamo definire dei tipi dedicati per insiemi di stringhe e di numeri:

```typescript
type StringSet = { [element: string]: boolean };
type NumberSet = { [element: number]: boolean };
```

### Esempi di utilizzo e rimozione di elementi

```typescript
let A: StringSet = {}; // insieme vuoto
let B: StringSet = { mela: true, banana: true }; // inserimento iniziale
A['pera'] = true; // inserimento di un elemento

console.log('mela' in B); // true
```

Per rimuovere un elemento presente ci sono due approcci, ma uno e' decisamente preferibile:
1. **Impostare il valore a `false` (sconsigliato):** scrivendo `B['mela'] = false;`, la chiave rimane comunque nell'oggetto. Di conseguenza, l'operatore `in` restituirebbe ancora `true` e bisognerebbe verificare l'appartenenza controllando due condizioni: `('mela' in B) && (B['mela'] === true)`.
2. **Usare la keyword `delete` (consigliato):** rimuove direttamente l'attributo dall'oggetto, mantenendo l'insieme pulito.

La sintassi di `delete` permette di usare sia la dot notation che le parentesi quadre:

```typescript
delete obj.property;
delete obj['property'];
```

Esempio pratico di rimozione:

```typescript
let B: StringSet = { mela: true, banana: true };
console.log('mela' in B); // true

delete B['mela'];
console.log('mela' in B); // false
```

## Operazioni sugli insiemi

Possiamo implementare le classiche operazioni insiemistiche come funzioni in TypeScript:

```typescript
function inserisci(insieme: StringSet, elemento: string): void
function elimina(insieme: StringSet, elemento: string): void
function appartiene(insieme: StringSet, elemento: string): boolean
function unione(A: StringSet, B: StringSet): StringSet
function intersezione(A: StringSet, B: StringSet): StringSet
function differenza(A: StringSet, B: StringSet): StringSet
function sottoinsieme(A: StringSet, B: StringSet): boolean
function uguali(A: StringSet, B: StringSet): boolean
```

| Funzione | Cosa fa | Argomenti e output |
| :--- | :--- | :--- |
| `inserisci` | Aggiunge l'elemento | Modifica `insieme` |
| `elimina` | Toglie l'elemento (se c'e') | Modifica `insieme` |
| `appartiene` | Restituisce `true` se e' nell'insieme | Non modifica nulla |
| `unione` | Elementi presenti in $A$ o in $B$ ($A \cup B$) | Restituisce un insieme nuovo; $A$ e $B$ restano intatti |
| `intersezione` | Elementi presenti sia in $A$ che in $B$ ($A \cap B$) | Restituisce un insieme nuovo; $A$ e $B$ restano intatti |
| `differenza` | Elementi di $A$ non presenti in $B$ ($A \setminus B$) | Restituisce un insieme nuovo; $A$ e $B$ restano intatti |
| `sottoinsieme` | Restituisce `true` se $A \subseteq B$ | Non modifica nulla |
| `uguali` | Restituisce `true` se $A \subseteq B$ e $B \subseteq A$ ($A = B$) | Non modifica nulla |

## Modellare multi-insiemi senza classi native

Un **multi-insieme** e' una collezione di elementi distinti e non ordinati in cui ogni elemento ha una propria **molteplicita'** (ovvero il numero di volte in cui compare).

In TypeScript possiamo rappresentarlo con un oggetto in cui le chiavi sono gli elementi e i valori numerici rappresentano la loro molteplicita' (es. `{ rosso: 2, verde: 1 }`):

```typescript
type StringMultiSet = { [element: string]: number };
type NumberMultiSet = { [element: number]: number };
```

### Regole e osservazioni sui multi-insiemi

* **Molteplicita' minima:** per ogni elemento presente nel multi-insieme, la molteplicita' e' sempre $\ge 1$.
* **Rimozione a zero:** se la molteplicita' di un elemento scende a $0$, la sua chiave va rimossa con `delete`. Altrimenti l'operatore `in` continuerebbe a indicare che l'elemento appartiene al multi-insieme (lo stesso problema che si verifica impostando un elemento a `false` negli insiemi semplici).
* **Definizione delle operazioni:** le operazioni tra multi-insiemi possono essere definite in modi diversi a seconda del contesto. Ad esempio, per ogni elemento $x$ con molteplicita' $m_A(x)$ in $A$ e $m_B(x)$ in $B$:
  * **Unione:** puo' essere definita come la somma oppure come il massimo delle molteplicita', $\max(m_A(x), m_B(x))$.
  * **Intersezione:** puo' essere definita come il minimo delle molteplicita', $\min(m_A(x), m_B(x))$.
  * **Differenza:** puo' essere definita come $\max(0, m_A(x) - m_B(x))$.

## Operazioni sui multi-insiemi

```typescript
function molteplicita(M: StringMultiSet, elemento: string): number
function inserisciMulti(M: StringMultiSet, elemento: string, quantita: number): void
function rimuoviMulti(M: StringMultiSet, elemento: string, quantita: number): void
function unioneMulti(A: StringMultiSet, B: StringMultiSet): StringMultiSet
function intersezioneMulti(A: StringMultiSet, B: StringMultiSet): StringMultiSet
function differenzaMulti(A: StringMultiSet, B: StringMultiSet): StringMultiSet
function cardinalitaMulti(M: StringMultiSet): number
```

| Funzione | Cosa fa | Argomenti e output |
| :--- | :--- | :--- |
| `molteplicita` | Restituisce la molteplicita' dell'elemento | Non modifica nulla |
| `inserisciMulti` | Aggiunge occorrenze dell'elemento | Modifica `M` (restituisce `void`) |
| `rimuoviMulti` | Toglie fino a `quantita` occorrenze | Modifica `M` (restituisce `void`) |
| `unioneMulti` | Calcola il massimo tra le occorrenze | Restituisce un multi-insieme nuovo |
| `intersezioneMulti` | Calcola il minimo tra le occorrenze | Restituisce un multi-insieme nuovo |
| `differenzaMulti` | Sottrae le occorrenze in $B$ da quelle in $A$ | Restituisce un multi-insieme nuovo |
| `cardinalitaMulti` | Calcola il numero totale di occorrenze | Non modifica nulla |

## Limitazioni della rappresentazione a oggetti

Sotto la superficie, JavaScript gestisce gli oggetti in modo complesso e questa rappresentazione presenta alcuni limiti importanti quando si modellano gli insiemi:

1. **Le chiavi sono sempre stringhe:**
   * Anche usando `NumberSet`, le chiavi numeriche vengono convertite internamente in stringhe: di conseguenza, gli elementi `1` e `"1"` coincidono.
   * Iterando con un ciclo `for..in`, le chiavi vengono restituite come stringhe (ad esempio, per $\{10, 2, 7\}$ si ottengono `"2"`, `"7"`, `"10"` di tipo `string`).
2. **Tipi di elementi limitati:**
   * Le chiavi di un oggetto possono essere solo stringhe o numeri (o Symbol): non e' quindi possibile creare **insiemi di insiemi**.
3. **Proprieta' ereditate e operatore `in`:**
   * Ogni oggetto JavaScript eredita dal prototipo alcune proprieta' di base come `toString` o `constructor`.
   * L'operatore `in` controlla anche queste proprieta' ereditate:

```typescript
console.log('toString' in {}); // true (possibile bug con insiemi di parole!)
```

   * Questo problema non si verifica invece quando si iterano le chiavi proprie dell'oggetto con `for..in`:

```typescript
for (let i in {}) {
    console.log(i); // non stampa nulla
}
```

> **Nota:** Come accennato prima esistono classi native che risolvono queste limitazioni e le andremo a scoprire nel secondo semestre. 