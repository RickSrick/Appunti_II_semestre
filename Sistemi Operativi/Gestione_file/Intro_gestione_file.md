# INTRODUZIONE ALLA GESTIONE DEI [[File|FILE]]
Il ==SOTTOSISTEMA PER LA GESTIONE DEI FILE== è la parte più visibile del SO: fornisce meccanismi per la registrazione, l'accesso e la protezione di dati e programmmi del SO e degli utenti.
Così come i sottosistemi per la gestione dei processi e della memoria "virtualizzano" rispettivamente la CPU e la memoria centrale, così il [[File_system|file system]] "virtualizza" i dispositivi di memorizzazione permanente, fornendone una visione logica uniforme.

Un sistema di calcolo può infatti utilizzare diversi media per registrare stabilmente le informazioni, ognuno con caratteristiche diverse:
- [[Hard_disk_drive|disco rigido]]
- dischi ottici
- [[Solid_state_drive|dischi a stato solido]]
- [[Solid_state_drive|memorie flash]]
Compito del SO è quindi quello di astrarre la complessità di utilizzo dei diversi mezzi di memorizzazione fornendone una visione logica e metodi d'accesso uniformi.

Sono presenti quindi due livelli:
- _visione utente_ (interfaccia, che dev'essere comune ed efficiente)
- implementazione