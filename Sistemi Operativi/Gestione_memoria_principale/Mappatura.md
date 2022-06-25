# MAPPATURA
## ==MAPPATURA DI [[File|FILE]]==
La mappatura di file in memoria permette il trattamento dell'accesso a file in memoria come un normale accesso in memoria. Si realizza associando un blocco del disco ad una o più pagine residenti in memoria.
L'accesso iniziale al file avviene tramite una richiesta di [[Paginazione|paginazione]] che genera un [[Paginazione#PAGE FAULT|page fault]]: una porzione del file, pari ad una pagina, viene caricata dal sistema in una pagina fisica. Ogni successiva letttura/scrittura del file viene gestita come un ordinario accesso alla memoria.
Si alleggerisce il lavoro del sistema di I/O e del sistema operativo in generale, dato che non si effettuano le [[Chiamate_di_sistema|system call]] $read()$/$write()$. Alcuni SO prevedono un'apposita chiamata di sistema per la mappatura dei file in memoria.

Più processi possono mappare contemporaneamente lo stesso file, garantendo la condivisione di pagine in memoria e rendendo le modifiche al file immediatamente visibili a tutti i file che lo condividono. Tuttavia, l'accesso al contenuto del file mappato in memoria deve essere controllato con un meccanismo di gestione della concorrenza, per garantire l'intergrità dei dati.
Esempio: quando il SO carica un processo per l'esecuzione, esegue una mappatura in memoria del file che ne contiene il codice eseguibile.
![500](mappatura_file.png)

Problema: quando aggiornare il contenuto del file su disco?
- periodicamente e/o all'atto della chiusura del file con la chiamata a $close()$
- quando il [[Paginazione_a_richiesta#PAGER|pager]] scandisce le pagine per controllarne il [[Paginazione_a_richiesta#SOVRALLOCAZIONE|dirty bit]]

## ==MAPPATURA IN MEMORIA DELL'I/O==
Ogni [[Connessione_dispositivi_memoria|controllore di I/O]] è dotato di registri contenenti istruzioni e dati in via di trasferimento.
Con la mappatura in memoria dell'I/O, indirizzi di memoria compresi in certi intervalli vengono riservati alla mappatura dei registri dei dispositivi. Questo metodo è adatto per dispositivi con tempi di risposta rapidi, come i controllori video.
Esempio:
	- a ciascuna posizione sullo schermo corrisponde una locazione mappata in memoria
	- visualizzare testo sullo schermo è quasi altrettanto veloce che scriverlo nelle relative locazioni mappate in memoria

In casi come questo, occorre permettere ad alcune pagine di rimanere ==BLOCCATE/PINNED== in memoria.
Esempio:	le pagine utilizzate per copiare un file da un dispositivo di I/O devono essere bloccate, per non essere selezionate come vittime dagli [[Algoritmi_sostituzione_pagina|algoritmi di sostituzione]].