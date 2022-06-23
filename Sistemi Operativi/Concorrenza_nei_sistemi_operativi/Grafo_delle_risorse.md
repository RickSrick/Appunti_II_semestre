# GRAFO DI ASSEGNAZIONE DELLE RISORSE / GRAFO DI HOLT
==GRAFO DI ASSEGNAZIONE DELLE RISORSE / GRAFO DI HOLT==:
- l'insieme dei vertici è partizionato in due sottoinsiemi:
	- $T = \{ \text{T}_{1}, \text{T}_{2}, ..., \text{T}_{n} \}$: insieme costituito da tutti i [[Thread|thread]] attivi nel sistema
	- $R = \{ \text{R}_{1}, \text{R}_{2}, ..., \text{R}_{n} \}$: insieme costituito da tutte le risorse presenti nel sistema
- ci sono tre tipi di arco:
	- ==ARCO DI RICHIESTA==: $\text{T}_{i} \rightarrow \text{R}_{j}$
	- ==ARCO DI ASSEGNAZIONE==: $\text{R}_{j} \rightarrow \text{T}_{i}$
	- ==ARCO DI RECLAMO== $\text{T}_{i} \rightarrow \text{R}_{j}$: $\text{T}_{i}$ può richiedere $\text{R}_{j}$ in futuro (linea tratteggiata)
![300](grafo_risorse.png)

Ciclo di evoluzione degli archi:
- un arco di reclamo diventa un arco di richiesta quando il thread richiede effettivamente la risorsa
- un arco di richiesta diventa un arco di assegnazione quando la risorsa viene allocata al thread
- un arco di assegnazione diventa un arco di reclamo quando la risorsa viene rilasciata dal thread
Le risorse devono essere reclamate a priori dal sistema: prima che un thread inizi la sua esecuzione, tutti i suoi thread di reclamo devono essere presenti nel grafo di assegnazione delle risorse.

## INDIVIDUAZIONE DELLO STALLO
Se il grafo non contiene cicli, non ci sono [[Deadlock|deadlock]]; se contiene cicli:
- se vi è una sola istanza per ogni risorsa, allora è presente un deadlock
- se vi sono più istanze per risorsa, allora il deadlock è possibile, ma non certo
Esempio:
![350](grafo_risorse2.png)
	È presente un ciclo ma il sistema non è in stallo. Infatti, la risorsa ha molteplicità 2 e una delle istanze è fuori dal ciclo: $\text{T}_{3}$ può terminare e rilasciare la sua istanza di $\text{R}_{1}$, che viene richiesta da $\text{T}_{2}$

Si può applicare un algoritmo chiamato ==INDIVIDUAZIONE DEL BLOCCO CRITICO==:
- una ==RIDUZIONE== è possibile se un processo può vedersi assegnate le risorse in modo da soddisfare la sua richiesta; in tal caso, può terminare
- un grafo di Holt è ==COMPLETAMENTE RIDUCIBILE== se esiste una serie di riduzioni che elimina tutti gli archi del grafo
- un sistema non è in stallo se e solo se il suo grafo di Holt è completamente riducibile, ovvero tutti i processi possono terminare
Questo algoritmo può essere ritrovato nell'[[Prevenzione_deadlock#ALGORITMO DEL BANCHIERE|algoritmo del banchiere]].