# PROGRAMMI DI SISTEMA
I ==PROGRAMMI DI SISTEMA== forniscono un ambiente conveniente per lo sviluppo e l'esecuzione di ==PROGRAMMI UTENTE== (semplici interfacce alle [[Chiamate_di_sistema|chiamate di sistema]] oppure programmi complesssi). L'aspetto del SO per la maggioranza degli utenti è infatti definito dai programmi di sistema, non dalle chiamate di sistema vere e proprie.
Alcune delle funzioni assolte dai programmi di sistema:
- gestione di file
- informazioni di stato
- editing di file
- supporto a linguaggi di programmazione
- caricamento ed esecuzione di programmi
- comunicazioni
- supporto alla realizzazione di applicativi

Altri tipi di programma:
- ==SERVIZI BACKGROUND==
	- lanciati durante la fase di [[Avviamento_del_SO|boot]] (alcuni utili solo nella fase di startup, altri in esecuzione dal boot allo shutdown)
	- supportano servizi quali controllo del [[Hard_disk_drive|disco]], [[Scheduling|scheduling dei processi]], [[Debugging|logging degli errori]], stampa, connessioni di rete
	- vengono eseguiti in [[Modalità|modalità utente]]
	- noti anche come _servizi_, _sottosistemi_, _daemon_
- ==PROGRAMMI APPLICATIVI==
	- non fanno parte del sistema operativo
	- eseguiti dagli utenti
	- lanciati da linea di comando, dal click del mouse o da pressione sul touchscreen
	- definiscono le modalità di utilizzo delle risorse del sistema per risolvere i problemi di calcolo degli utenti (e.g. word processor, compilatori, web browser, sistemi per database, fogli di calcolo, giochi)