# TABELLA DEI [[File|FILE]] APERTI
Quando si richiede un'operazione su file si ricercano le informazioni relative reperendole, tramite un puntatore, nella ==TABELLLA DEI FILE APERTI==. Questa tabella contiene una copia dell'[[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|FCB]] per ogni file aperto nel sistema. Quando il file non è più attivo, dev'essere chiuso e il SO rimuove l'elemento relativo nella tabella.
Le [[Chiamate_di_sistema|chiamate di sistema]] per aprire e chiudere i file sono:
- $open(\text{F}_{i})$: ricerca nella [[Struttura_directory|struttura di directory]] sul disco l'elemento $\text{F}_{i}$ e ne copia il contenuto nella tabella dei file aperti in memoria centrale, riporta un puntatore all'elemento della tabella
- $close(\text{F}_{i})$: copia il contenuto dell'elemento $\text{F}_{i}$, attualmente residente in memoria principale, nella struttura di directory sul disco e lo rimuove

Nei sistemi multiutente, sono presenti due livelli di tabelle:
- ==TABELLE DI SISTEMA==:
	- riferimenti a tutti i file aperti nel sistema
	- posizione del file nel disco
	- dimensione del file
	- data di ultimo accesso / ultima modifica
	- contatore di aperture
- ==TABELLA ASSOCIATA AL PROCESSO==:
	- riferimenti a tutti i file aperti dal processo (sotto forma di puntatori all'elemento nella tabella di sistema, più informazioni di accesso specifiche del processo)
	- puntatore alla posizione corrente nel file
	- diritti di accesso

In particolare:
- ==CONTATORE DI APERTURE==: conta il numero di processi che hanno aperto il file, per rimuovere opportunamente i dati dalla tabella dei file aperti alla chiusura del file da parte dell'ultimo processo (tabella di sistema)
- ==LOCAZIONE DEL FILE SU DISCO==: cache delle informazioni di accesso ai dati permanenti (tabella di sistema)
- ==PUNTATORE ALLA POSIZIONE CORRENTE NEL FILE==: puntatore alI'ultima locazione dove è stata realizzata un'operazione di lettura/scrittura per ogni processo che ha aperto il file (tabella associata al processo)
- ==DIRITTI DI ACCESSO==: controllati dal SO per permettere o negare le operazioni di I/O richieste (tabella associata al processo)