# STRUTTURA DELLE [[Directory|DIRECTORY]]
## ==DIRECTORY MONO-LIVELLO==
Una directory unica per tutti gli utenti:
- problemi di nominazione: serve un nome diverso per ogni file
- nessun raggruppamento logico
![550](directory_monolivello.png)

## ==DIRECTORY A DUE LIVELLI==
Directory separate per ogni utente:
- ammessi nomi uguali per file di utenti diversi
- ricerca efficiente
- nessun capacità di raggruppamento logico (se non in base ai proprietari)
- _nome di percorso_: permette ad un utente di vedere i file di altri utenti
- ricerca dei file di sistema: percorso di ricerca
![550](directory_due_livelli.png)
Quando si apre la sessione di lavoro si ricerca nella ==MASTER FILE DIRECTORY (MFD)== l'identificativo dell'utente, che viene ammesso al sistema della propria ==USER FILE DIRECTORY (UFD)==. Ogni riferimento a file da parte dell'utente viene interpretato dal SO come esclusivamente correlato ai file della propria UFD. Per riferirsi a file di altri utenti, se l'accesso è autorizzato, ogni utente deve utilizzare il pathname completo del file (nome utente e nome file). I file di sistema vengono raccolti invece in directory opportune raggiungibili da tutti gli utenti.

## ==DIRECTORY CON STRUTTURA AD ALBERO==
- ricerca efficiente
- capacità di raggruppamento logico
- pathname assoluto o relativo
- creazione / cancellazione di file: effettuata nella directory corrente ($rm <file-name>$)
- creazione di directory: interpretata come creazione di sottodirectory nella cartella corrente
- cancellazione di directory: solo se vuota in MS-DOS, anche se contenente file o sottodirectory in UNIX / Linux
![450](directory_albero.png)

## ==DIRECTORY A GRAFO ACICLICO==
Presenza di file o sottodirectory condivise.
==ALIASING==: due o più nomi diversi possono venire utilizzati per identificare lo stesso oggetto, file o directory.
La condivisione può essere implementata per mezzo di:
- ==SOFT LINK==: link che punta solamente all'elemento nella directory, non al file fisico
- ==HARD LINK==: duplicazione dell'elemento di directory, che crea un nuovo elemento nella struttura directory che punta allo stesso file fisico
![400](directory_grafo.png)
Cancellare un file rende inutilizzabile il soft link ma non influisce sull'hard link. Per risolvere questo problema:
- puntatori all'indietro che permettano il reperimento di tutti i link al file cancellato e la loro eliminazione
- conservazione del file fino a che non esistono più link, mantenendo una lista dei riferimenti al file e permettendo la cancellazione del file quando il contatore di riferimenti vale 0

Mantenere il grafo aciclico garantisce la semplicità degli algoritmi usati per attraversarlo, per esempio in fase di backup. Per assicurare l'assenza di cicli:
- sono ammessi link a file, ma non a sottodirectory
- ogni volta che viene aggiunto un nuovo link si verifica la presenza di cicli, mediante l'uso di un algoritmo di rilevamento, che risulta essere molto dispensioso, soprattutto perchè effettuato sulla memoria di massa

## ==DIRECTORY A GRAFO GENERALE==
Si ammette la presenza di cicli.
![400](directory_grafo_generale.png)
In fase di scansione del file system, occorre marcare ciò che è raggiungibile ed è già stato visitato, per evitare, ad esempio, copie multiple dello stesso elemento in fase di backup. Inoltre, se esistono cicli, il contatore dei riferimenti ad un file può non essere nullo anche se il file non ha più alcun riferimento.
==GARBAGE COLLECTION==: si attraversa il file system marcando ciò che è accessibile; in un secondo passaggio, si sposta nell'elenco dei blocchi liberi quanto non è contrassegnato.