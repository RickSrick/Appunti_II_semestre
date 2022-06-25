# [[Tabella_delle_pagine|TABELLA DELLE PAGINE]] HASH
Comune per spazi di indirizzi a più di 32 bit.
==TABELLA DELLE PAGINE HASH==: viene applicata una funzione hash:
- l'argomento della funzione è il numero della pagina
- per gestire le collisioni, ogni elemento della tabella hash contiene una lista concatenata di elementi
- ciascun elemento della tabella è composto da:
	- numero di pagina
	- indirizzo del frame corrispondente
	- puntatore all'elemento successivo della lista
- il numero di pagina viene confrontato con tutti gli elementi della lista concatenata
Metodo particolarmente utile per spazi di indirizzi sparsi con riferimenti di memoria non contigui (situazione un po' improbabile).
![500](hash.png)

## ==TABELLA DELLE PAGINE A CLUSTER==
- utilizzata in spazi a 64 bit
- simile a tabella hash, ma ogni elemento della tabella contiene riferimenti a frame corrispondenti ad un gruppo di pagine contigue
- si riduce lo spazio di memoria necessario
- aumentano le prestazioni del sistema, dato che lo spazio degli indirizzi dei programmi è naturalmente "contiguo in tempo e spazio" ([[Algoritmi_allocazione_frame#WORKING-SET|località]] negli accessi alla memoria)