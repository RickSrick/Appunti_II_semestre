# RECORD LOGICI
==RECORD FISICI==: blocchi del disco (dimensione fissata).
Occorre risolvere il problema della corrispondenza tra ==RECORD LOGICI== e record fisici: ==PACKING==. Anche con i file, parte dell'ultimo blocco contenente il file può rimanere inutilizzata, causando una [[Frammentazione#FRAMMENTAZIONE INTERNA|frammentazione interna]].

# METODI DI ACCESSO AI [[File|FILE]]
## ==ACCESSO DIRETTO==
Modello di accesso che si ispira al [[Hard_disk_drive|disco]]: si può accedere a record di dati posti in qualunque posizione nel file, determinata rispetto ad un offset. In questo modo si può scrivere o leggere record in ordine casuale oppure sovrascrivere un singolo record.
![350](accesso_diretto.png)

## ==ACCESSO SEQUENZIALE==
Modello di accesso che si ispira al [[Nastro|nastro]]:
- viene trattato un gruppo di byte o un record alla volta
- un puntatore indirizza il gruppo o record corrente e avanza a ogni lettura o scrittura
- la lettura può avvenire in qualunque posizione del file, che deve però essere raggiunta sequenzialmente, e non può avvenire oltre l'ultima posizione scritta
- la scrittura può avvenire solo in coda al file (append)
![300](accesso_sequenziale.png)
![450](accesso_sequenziale2.png)

## ==ACCESSO INDICIZZATO==
Modello di accesso che si ispira ai database che può essere realizzato sulla base del modello ad accesso diretto:
- implica la costruzione di un ==FILE INDICE== per l'accesso al file, che viene mantenuto in memoria centrale
- l'indice contiene puntatori ai blocchi del file
- per reperire un elemento del file bisogna prima cercare nell'indice il puntatore corrispondente e poi utilizzare il puntatore per accedere ai dati
- per file molto lunghi, il file indice può diventare troppo grande per risiedere in memoria, e viene quindi creato un indice per il file indice
![450](accesso_indicizzato.png)
Esempio di accesso indicizzato:
	Si consideri un file composto da record di 16 byte: un codice UPC (Universal Product Code) a 10 cifre ed un prezzo a 6 cifre. Consideriamo blocchi fisici da 1024 byte, contenenti 64 record. $\Rightarrow$ Un file da 120000 record occupa circa 2000 blocchi.
	Ordinando il file secondo i codici UPC, si può definire un indice composto dal primo codice UPC di ogni blocco $\Rightarrow$ 2000 elementi di 10 byte ciascuno (circa 20KB): I'indice può essere mantenuto in memoria centrale.