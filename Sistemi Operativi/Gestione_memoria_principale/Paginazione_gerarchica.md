# [[Paginazione|PAGINAZIONE]] GERARCHICA
Per accedere alla [[Tabella_delle_pagine|tabella delle pagine]] usiamo un solo offset; serve quindi una zona di memoria contigua.
==PAGINAZIONE GERARCHICA==: dividere lo spazio degli indirizzi logici in più tabelle delle pagine contigue.
Queste "sotto-tabelle" sono più piccole della tabella originale, e vengono paginate anch'esse.
![400](gerarchica.png)

## ==PAGINAZIONE A DUE LIVELLI / TABELLA DELLE PAGINE AD ASSOCIAZIONE DIRETTA==
Forma più semplice di paginazione gerarchica.

Esempio:
	indirizzi logici a 32 bit, pagine da 4 KB:
	- numero di pagina a 20 bit
	- offset a 12 bit
	numero di pagina diviso:
	- numero di pagina (nella tabella esterna) da 10 bit
	- offset (per ricavare la tabella delle pagine) da 10 bit
	![300](2_livelli.png)

La traduzione [[Indirizzi_logici_fisici|da indirizzo fisico a indirizzo logico]] può richiedere tre accessi in memoria; tuttavia, la presenza di [[Dispositivi_di_memoria#CACHING|cache]] consente di mantenere prestazioni ragionevoli.

## ==PAGINAZIONE A PIÙ LIVELLI==
La paginazione a due livelli non è più adatte in architetture a 64 bit, si adoperano più livelli (da 3 a 7). Tuttavia, nelle architetture a 64 bit la paginazione gerarchica è inadeguata a causa dei costi proibitivi in termini di accessi in memoria in caso di [[Tabella_delle_pagine#REGISTRI ASSOCIATIVI TRANSLATION LOOK-ASIDE BUFFER TLB|TLB-miss]].

Esempio:
![400](più_livelli.png)
	paginazione a 3 livelli: 4 accessi in memoria