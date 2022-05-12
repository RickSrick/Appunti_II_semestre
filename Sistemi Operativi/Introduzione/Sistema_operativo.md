# SISTEMA OPERATIVO
==SISTEMA OPERATIVO==: un software che agisce da intermediario tra l'utente e l'hardware del computer. Deve fornire i suoi servizi e le sue caratteristiche a tutti gli utenti, e mantenerli aggiornati nel tempo per adeguarsi ai cambiamenti delle loro esigenze.

Ha i seguenti scopi:
- _eseguire i programmi_, supportando l'utente nel risolvere problemi
- garantire _un'interazione agevole_ tra utente e macchina
- _gestire in modo efficiente le risorse_ hardware e software del sistema di calcolo da parte dei vari [[Programmi_di_sistema|programmi di sistema e applicativi]]
- _prevenire le interferenze_ tra le attività degli utenti (coordinare i processi)
- _protezione_ nell'uso delle [[Risorse|risorse]] e terminazione dei processi che ne abusano 
![SO|300](Images/struttura_so_1.png)
# STRUTTURA DEL SISTEMA DI CALCOLO
- ==SHELL==: parte più esterna del SO che permette l'interazione tra utente e sistema stesso, interpretando comandi e avviando programmi
- ==KERNEL==: unico programma sempre in esecuzione nel SO, che fornisce le sue funzionalità base
- ==MIDDLEWARE==: presente nei SO dei dispositivi mobili, insieme di programmi che fungono da intermediari tra diverse applicazioni e componenti software
![SO|600](Images/struttura_so_2.png)

Il kernel è composto da tre sezioni, implementate direttamente in hardware e scritte almeno in parte in linguaggio Assembly:
- ==FIRST [[Interrupt|INTERRUPT]] HANDLER (FLIH)==: gestione iniziale di tutte le interruzioni
	funzioni del FLIH:
	- determinare l'origine dell'interruzione
	- attivare il segmento di codice specifico per l'interruzione identificata
- ==[[Dispatcher|DISPATCHER]]==: assegna i CPU core ai vari processi
- terza sezione: implementa i costrutti per la sincronizzazione dei processi (e.g. [[Semafori|semafori]])
Ogni sistem è anche dotato di un orologio in tempo reale (==REAL-TIME CLOCK (RTC)==) per misurare gli intervalli di tempo.