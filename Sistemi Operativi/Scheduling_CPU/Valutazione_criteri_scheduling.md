# METODI DI VALUTAZIONE DEI [[Criteri_scheduling|CRITERI DI SCHEDULING]]
Come selezionare un algoritmo di scheduling della CPU per un certo SO?
- ==MODELLI DETERMINISTICI==: valutazione analitica: considera un carico di lavoro predeterminato e definisce le prestazioni di ogni algoritmo per quel carico di lavoro (e.g. tempo medio di attesa)
	metodo semplice e veloce, tuttavia richiede una conoscenza sulle dinamiche del sistema normalmente non disponibile
- ==RETI DI CODE==: il sistema di calcolo viene descritto come una rete di server, ognuno con la propria coda d'attesa
	- la CPU è un server con la propria coda di processi in attesa, e il sistema di I/O ha le sue code dei dispositivi; se sono noti l'andamento degli arrivi e dei servizi (sotto forma di distribuzioni di probabilità), si può calcolare l'utilizzo di CPU e dispositivi, la lunghezza media delle code, il tempo medio d'attesa, il throughput medio, etc.
	- problema: difficoltà nell'utilizzo di distribuzioni complicate o metodi matematici appositi
	- siano $n$ la lunghezza media di una coda, $W$ il tempo medio di attesa nella coda, $\lambda$ l'andamento medio di arrivo dei nuovi processi: se il sistema è stabile, il numero di processi che lasciano la coda deve essere uguale al numero di processi che vi arrivano: ==FORMULA DI LITTLE== (valida per qualsiasi algoritmo di scheduling e distribuzione degli arrivi)
$$
\begin{equation}
n=\lambda \times W
\end{equation}
$$
- ==SIMULAZIONE==: si simula l'esecuzione degli algoritmi in un modello del sistema di calcolo, raccogliendo e stampando statistiche che descrivono le loro prestazioni
	- implica la programmazione del modello, dove le strutture dati rappresentano gli elementi principali del sistema
	- il simulatore dispone di una variabile che rappresenta il clock e modifica lo stato del sistema in modo da descrivere le attività dei dispositivi, dei processi e dello scheduler
	- i dati per la simulazione possono essere generati artificialmente, modellati da distribuzioni matematiche o empiriche oppure raccolti da un sistema reale mediante un _trace tape_