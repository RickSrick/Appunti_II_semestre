# GRAFO DI PRECEDENZA
==GRAFO DI PRECEDENZA==: grafo diretto aciclico dove ogni arco rappresenta una relazione di precedenza tra i nodi.
Definizioni utili:
- $\text{P}_{j} \space \bullet$ : ==ISTANTE FINALE== di $\text{P}_{j}$
- $\bullet \space \text{P}_{j}$ : ==ISTANTE INIZIALE== di $\text{P}_{j}$
- $< \bullet$ : precede nel tempo
- $\text{P}_{i} < \bullet \text{P}_{j} \longrightarrow \text{P}_{i} \bullet < \bullet \text{P}_{j}$
Proprietà:
- _transitiva_: $\text{P}_{i} < \bullet \text{P}_{j}, \space \text{P}_{j} < \bullet \text{P}_{k} \longrightarrow \text{P}_{i} \bullet < \bullet \text{P}_{k}$
- _non simmetrica_: $\text{P}_{i} < \bullet \text{P}_{j} \neq \text{P}_{j} < \bullet \text{P}_{i}$ 
- _non riflessiva_: $\neg (\text{P}_{i} < \bullet \text{P}_{i})$
![400](grafo_precedenza.png)

==SISTEMA CHIUSO==: esiste un singolo processo iniziale e un singolo processo finale.
Se il sistema è aperto, è possibile renderlo chiuso aggiungendo dei processi dummy.
![500](grafo_precedenza2.png)

Due insieme di processi $\text{C}_{a}$ e $\text{C}_{b}$ possono essere combinati ==IN SERIE== ($\text{C}_{a} *\text{C}_{b}$) o ==IN PARALLELO== ($\text{C}_{a}+\text{C}_{b}$). Questa formalizzazione permetterà di capire i tempi di calcoli in base al ==PARALLELISMO== del sistema. Da notare che in genere, nelle CPU in vendita, aumentando il numero di core cala la frequenza massima.
![400](grafo_precedenza3.png)

## ==MASSIMO GRADO DI PARALLELISMO==
Cardinalità del più grande sottoinsieme di processi (ovvero nodi del grafo) tale per cui, dati due nodi qualsiasi del sottoinsieme preso, non esiste un percorso orientato che li connette.
Indica quanti sottoprocessi indipendenti potrebbero essere parallelizzati. Per ridurre il massimo grado di parallelismo (i.e. ottimizzare il sistema per hardware con un [[Multiprocessore_multicore#SISTEMI MULTICORE|numero prefissato di core]]) si può agire sui vari insiemi che hanno un massimo grado di parallelismo maggiore del numero di core.

## INTERFERENZA E DETERMINATEZZA
==SISTEMA DETERMINATO==: quando più processi cooperano, le loro diverse velocità e l'ordine d'esecuzione non influenzano il risultato finale.
Ad ogni processo possiamo associare:
- _dominio_: dati su cui il processo lavora
- _codominio_: risultati del processo
- _funzione mappa_: trasforma i dati di input in quelli di output
==PROCESSI NON INTERFERENTI==: almeno una di queste osservazioni è valida:
- uno è il successore dell'altro
- i codomini non si intersecano tra loro, e neppure i domini con i codomini
Un sistema è determinato se e solo se è composto da processi non intereferenti.
==SISTEMI EQUIVALENTI DI PROCESSI==: sono costituiti dallo stesso insieme di processi, sono determinati e partendo dallo stesso input producono lo stesso output