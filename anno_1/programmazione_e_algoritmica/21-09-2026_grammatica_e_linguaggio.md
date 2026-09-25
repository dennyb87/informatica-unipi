# Grammatica e linguaggio

## Grammatica

Si ricorda che una grammatica è una terna:

$$G = (T, N, P)$$

dove:

- $N$ è l'insieme dei simboli non terminali;
- $T$ è l'insieme dei simboli terminali;
- $P$ è l'insieme delle produzioni.

L'insieme delle produzioni e' invece:  

$P \subseteq S^* \times S^*$  

Dove $S = T \cup N$  

Una produzione ha la forma:

$$X ::= \beta$$

dove $X \in N$ è un simbolo non terminale e $\beta$ è una stringa di simboli terminali e non terminali.

## Grammatica per espressioni aritmetiche

```text
Op  ::= + | ×
Exp ::= Num | Exp Op Exp
```

## Derivativo  

Un simbolo $a^\prime$ si dice derivativo se da $a$ e'possibile ottenere $a^\prime$ applicando un numero qualsiasi di produzioni.   

$$\alpha \Rightarrow \alpha_1 \Rightarrow \alpha_2 \Rightarrow \dots \Rightarrow \alpha_n = \alpha'$$

## Derivativo immediato

Date due stringhe $a, a^\prime \in S^*$ si dice che $a^\prime$ e' un derivativo immediato di $a$ se da $a$ e' possibile ottenere $a^\prime$ applicando una singola produzione.  

Si indica con $\alpha \Rightarrow \alpha'$ l'applicazione di una sola produzione.

Esempio:

```text
a = Exp + Exp Op 2  ⇒  a' = Exp + Num Op2
```

## Linguaggio generato

Dato $G = (T, N, P)$ e un simbolo non terminale $X \in N$, il linguaggio di $X$ scritto $\mathcal{L}(X)$ e' l'insieme di tutti e soli i derivativi:

$$\mathcal{L}(X) = \{w \mid w \in T^* \text{ e } X \rightsquigarrow^* w\}$$

> $L(X)$ è l'insieme di tutte le stringhe $\omega$ formate da soli simboli terminali $T$ tali per cui è possibile derivare $\omega$ partendo dal simbolo $X$ in zero o più passaggi di derivazione $\rightsquigarrow$

## Quali stringhe appartengono al linguaggio ?  

Data la grammatica $G$ e una stringa di terminali $\omega \in T^*$ appartiene al linguaggio $\mathcal{L}(X)$ del non terminale $X \in N^*$ se:  

> partendo dal simbolo $X$ e applicando una o piu' regole di produzione, passo dopo passo si ottiene la stringa $\omega \in T^*$ composta solo da terminali.  

### Esempio  

```text
B ::= 1 | 0B | 1B
```

La stringa `1001` appartiene al linguaggio ?

$$B \Rightarrow 1B \Rightarrow 10B \Rightarrow 100B \Rightarrow 1001$$

La stringa `1000` non appartiene al linguaggio, perché ogni derivazione deve terminare con `1`.
