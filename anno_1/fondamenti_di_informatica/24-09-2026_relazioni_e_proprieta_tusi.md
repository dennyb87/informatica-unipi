# Relazione Opposta

Dato $R: A \leftrightarrow B$, la **relazione opposta** $R^{op}: B \leftrightarrow A$ inverte l'ordine di ogni coppia:

$$R^{op} = \{(y, x) \in B \times A \mid (x, y) \in R\}$$

### Esempi

* **Genitore**: $\text{Genitore}^{op} = \text{Figlio/a}$
* **Successore**: $\text{Succ}^{op} = \text{Pred}$ (Predecessore, dove $y = x - 1$)


```mermaid
graph LR
    subgraph N1[N]
        0["0"]
        1["1"]
        2["2"]
        3["..."]
    end
    subgraph N2[n]
        0_c["0"]
        1_c["1"]
        2_c["..."]
    end
    1 -->|Pred| 0_c
    2 -->|Pred| 1_c
