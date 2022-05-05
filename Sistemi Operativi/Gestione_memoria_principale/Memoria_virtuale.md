# MEMORIA VIRTUALE
Il codice deve risiedere in memoria principale per essere eseguiti, ma raramente tutto il codice relativo ad un programma è necessario durante l'esecuzione:
- porzioni di codice per la gestione di errori insoliti o percorsi nel flusso raramente seguiti
- array, liste e tabelle sovradimensionate rispetto all'utilizzo reale standard
Mantenere solo porzioni di programmi in memoria ha dei vantaggi:
- i programmi non sono vincolati alla quantità di memoria fisica disponibile
- aumenta il grado di multiprogrammazione e la produttività del sistema senza influenzare i tempi di risposta o di turnaround
![[Definizioni#MISURE]]

==MEMORIA VIRTUALE==: separazione della memoria logica dell'utente dalla memoria fisica:
- solo parte del programma si trova in memoria per l'esecuzione (le parti rimanenti si trovano sulla memoria secondaria)
- lo spazio logico degli indirizzi può essere molto più grande dello spazio fisico
- porzioni di spazio fisico possono essere condivisi da più processi
![550](memoria_virtuale.png)

==SPAZIO DEGLI INDIRIZZI VIRTUALI==: collocazione dei processi in memoria dal punto di vista logico:
- processo inizia in corrispondenza dell'indirizzo 0 e si estende alla memoria contigua fino all'indirizzo _Max_
- la memoria fisica allocata al processo è composta da frame sparsi
- il mapping da indirizzi logici a fisici è effettuato dalla MMU
![[MMU#MMU]]

La memoria virtuale facilita la ==CONDIVISIONE== di file e memoria mediante condivisione delle pagine fisiche.
Esempio:
	- le _librerie di sistema_ sono condivisibili mediante mappature delle pagine logiche di più processi sugli stessi frame
	- ogni processo vede le librerie all'interno del suo spazio di indirizzi virtuali, ma le pagine fisiche che le ospitano sono in condivisione tra tutti i processi che le utilizzano
![[Processi#STRUTTURA DI UN PROCESSO]]