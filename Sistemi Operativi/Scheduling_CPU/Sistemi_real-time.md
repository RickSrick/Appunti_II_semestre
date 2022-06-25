# SISTEMI REAL-TIME
==SISTEMA REAL-TIME==: si attende che un evento avvenga per reagirvi in tempo reale.
Due tipi di sistemi real-time:
- ==SISTEMA HARD REAL-TIME==: richiede il completamento dei processi critici entro un intervallo di tempo predeterminato e garantito
- ==SISTEMA SOFT REAL-TIME==: richiede che ai processi critici venga assegnata una priorità maggiore rispetto ai processi routine (nessuna garanzia sui tempi di completamento)

==LATENZA DELL'EVENTO==: tempo che intercorre tra l'occorrenza dell'evento e il momento in cui il sistema ne effettua la gestione.
Esistono requisiti di latenza diversi per eventi diversi:
- ==LATENZA RELATIVA ALLE INTERRUZIONI==: tempo tra la notifica di un'[[Interrupt|interruzione]] alla CPU e l'avvio della routine che la gestisce
	è fondamentale minimizzare l'intervallo di tempo in cui le interruzioni vengono disabilitate per aggiornare i dati del [[Sistema_operativo#STRUTTURA DEL SISTEMA DI CALCOLO|kernel]]
- ==LATENZA DI DISPATCH==: tempo necessario al [[Dispatcher|dispatcher]] per interrompere un processo ed avviarne un altro
	la ==FASE DI CONFLITTO== nella latenza di dispatch è formata da:
	- [[Risorse#PREEMPTION PRELAZIONE|prelazione]] di ogni processo in esecuzione nel kernel
	- cessione, da parte dei processi a bassa priorità, delle risorse richieste dal processo ad alta priorità
![450](latenza_dispatch.png)