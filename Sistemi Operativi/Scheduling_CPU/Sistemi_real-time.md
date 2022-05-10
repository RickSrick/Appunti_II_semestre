# SISTEMI REAL-TIME
==SISTEMI REAL-TIME==: si attende che un evento avvenga per reagirvi in tempo reale
Due tipi di sistemi real-time:
- ==SISTEMI HARD REAL-TIME==: richiedono il completamento dei processi critici entro un intervallo di tempo predeterminato e garantito
- ==SISTEMI SOFT REAL-TIME==: richiedono che ai processi critici venga assegnata una priorità maggiore rispetto ai processi routine (nessuna garanzia sui tempi di completamento)

==LATENZA DELL'EVENTO==: tempo che intercorre tra l'occorrenza dell'evento e il momento in cui il sistema ne effettua la gestione
Esistono requisiti di latenza diversi per eventi diversi:
- ==LATENZA RELATIVA ALLE INTERRUZIONI==: tempo tra la notifica di un'[[Interrupt|interruzione]] alla CPU e l'avvio della routine che la gestisce
	è fondamentale minimizzare l'intervallo di tempo in cui le interruzioni vengono disabilitate per aggiornare i dati del kernel
- ==LATENZA DI DISPATCH==: tempo necessario al dispatcher per interrompere un processo ed avviarne un altro
	la ==FASE DI CONFLITTO== nella latenza di dispatch è formata da:
	- prelazione di ogni processo in esecuzione nel kernel
	- cessione, da parte dei processi a bassa priorità, delle risorse richieste dal processo ad alta priorità
![450](latenza_dispatch.png)