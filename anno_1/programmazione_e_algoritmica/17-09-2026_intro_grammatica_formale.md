## Linguaggi di programmazione

Programmare significa tradurre un problema o un obbiettivo in una sequenza di istruzioni eseguibili dal computer. Serve allora un linguaggio formale, preciso e non ambiguo. Vogliamo quindi definire formalmente un linguaggio, ma cos'e' un linguaggio ?  

Un linguaggio puo' essere visto come un insieme di frasi ben formate che spesso sono troppe per essere elencate. Per descrivere queste frasi useremo le grammatiche formali, ovvero un sistema di regole che definisce un insieme (solitamente infinito) di sequenze finite di simboli (stringhe) appartenenti ad un alfabeto finito.  

## Sintassi  

La sintassi di un linguaggio definisce le regole per costruire frasi legali del linguaggio.  

## Alfabeto  

Un alfabeto $A$ e' un insieme *finito* di simboli detti *terminali*.  

$A_1 = \lbrace a, b, c, ..., z\rbrace$  alfabeto dei caratteri dell'alfabeto italiano  
$A_2 = \lbrace 0, 1 \rbrace$  alfabeto delle cifre binarie  

## Stringa  

Una stringa $S$ su un alfabeto $A$ e' una sequenza di lunghezza finita di simboli, anche con ripetizioni, dell'alfabeto $A$. Ad esempio *abzfg* e' una stringa sull'alfabeto $A_1 = \lbrace a, b, c, ..., z\rbrace$. Formalmente...  

$a_1a_2...a_n$ con $n \ge 0$ dove ciascun $a_j$ e' un elemento di $A$  

Il numero naturale $n$ e' detto lunghezza della stringa e si denota con $|S|$.  
Se $n = 0$ allora $S$ e' detta stringa vuota ed e' rappresentata dal simbolo $\epsilon$.  

$S_1 = abfgz \implies |S_1| = 5$  
$S_2 = \epsilon \implies |S_2| = 0$  


## Stringhe di lunghezza fissata  

Definiamo $A^n$ come l'insieme di tutte le stringhe sull'alfabeto $A$ che hanno lunghezza $n$. Se $A = \lbrace0, 1\rbrace$ allora...  

$A^0 = \lbrace\epsilon\rbrace$  
$A^1 = \lbrace0, 1\rbrace$  
$A^2 = \lbrace00, 01, 10, 11\rbrace$  
...  

## Stringhe sull'alfabeto  

Definiamo $A^*$ come l'insieme di tutte le stringhe sull'alfabeto $A$. Formalmente...  

$A^* = \bigcup_{n \ge 0} A_n = \lbrace\epsilon\rbrace \cup A^1 \cup A^2 \cup...$  

Se $A$ non e' vuoto allora $A^*$ e' infinito...  

$A = \lbrace0, 1\rbrace \implies A^* = \lbrace\epsilon, 0, 1, 00, 01, ...\rbrace$  


## Linguaggio  

Un linguaggio $L$ su un alfabeto $A$ e' un sottoinsieme di $A^*$, formalmente...  

$L \subseteq A^*$  

Sono linguaggi particolari il linguaggio vuoto $\varnothing$ ed il linguaggio di tutte le possibili stringhe su $A$ ovvero $A^*$. Ad esempio se:  

$A = \lbrace0, 1\rbrace$  

Allora un linguaggio $L$ potrebbe essere...  

$L \subseteq A^* = \lbraceS \in A^* \mid \text{la stringa S contiene un numero pari di 1}\rbrace = \lbrace\epsilon, \rbrace$  

## Grammatica formale  

Descrivere un linguaggio di programmazione significa descrivere l'insieme delle stringhe ben formate del linguaggio, ovvero i programmi (i programmi ammissibili sono infiniti).  

Per identificare l'insieme delle stringhe ben formate utilizzeremo il metodo generativo, ovvero l'insieme delle stringhe generate da una grammatica.  

Una *grammatica formale* e' una tripla $G = (T, N, P)$, dove:

- $T$ e' l'insieme dei simboli *terminali*: costituiscono l'alfabeto di riferimento;
- $N$ e' l'insieme dei simboli *non terminali*, usati per rappresentare le categorie sintattiche che ci interessano;
- indicando con $S = T \cup N$ l'insieme di tutti i simboli della grammatica, $P \subseteq S^* \times S^*$ e' l'insieme delle produzioni.

Ogni produzione ha forma $\alpha ::= \beta$, con $\alpha$ che contiene almeno un simbolo non terminale.

## Linguaggio indicazioni stradali

Un esempio semplice di grammatica formale e' quello usato per esprimere delle indicazioni stradali.

L'insieme dei terminali e':

$T = \lbrace\text{sinistra}, \text{destra}, \text{svolta}, \text{a}, \text{prosegui}, \text{dritto}, \text{","}, \text{poi}\rbrace$

I simboli non terminali sono invece:

$N = \lbrace\text{Direzione}, \text{Consiglio}, \text{Percorso}\rbrace$

Le produzioni della grammatica sono:

$$
\begin{aligned}
\text{Direzione} &::= \text{sinistra} \\
\text{Direzione} &::= \text{destra} \\
\text{Consiglio} &::= \text{svolta a Direzione} \\
\text{Consiglio} &::= \text{prosegui dritto} \\
\text{Percorso} &::= \text{Consiglio} \\
\text{Percorso} &::= \text{Consiglio, poi Percorso}
\end{aligned}
$$

Ad esempio, una frase generata da questa grammatica e': *svolta a sinistra, poi prosegui dritto*.

## Linguaggio delle espressioni aritmetiche

Consideriamo espressioni aritmetiche formate da numeri e dagli operatori binari $+$ e $\times$. L'alfabeto contiene quindi le cifre decimali e gli operatori:

$$
L \subseteq A^* = \lbrace0, 1, 2, 3, 4, 5, 6, 7, 8, 9, \times, +\rbrace^*
$$

Non tutte le stringhe costruite con questi simboli sono espressioni valide: le stringhe ben formate costituiscono un linguaggio, che possiamo descrivere attraverso una grammatica.

### Numeri naturali: primo tentativo

Per generare i numeri naturali possiamo introdurre i non terminali `Cifra` e `Num`:

$$
\begin{aligned}
\text{Cifra} &::= 0 \mid 1 \mid 2 \mid 3 \mid 4 \mid 5 \mid 6 \mid 7 \mid 8 \mid 9 \\
\text{Num} &::= \text{Cifra} \mid \text{Num Cifra}
\end{aligned}
$$

Queste regole permettono di costruire sequenze di una o piu' cifre. Tuttavia generano anche numeri con zeri iniziali, ad esempio `051`, per escluderli servono regole piu' complesse.  
