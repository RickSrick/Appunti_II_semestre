# DEADLOCK
==DEADLOCK / STALLO==: insieme di [[Thread|thread]] bloccati, dove ognuno dei quali possiede delle [[Risorse|risorse]] e attende di acquisirne altre allocate ad altri thread dell'insieme.
In un [[Multiprogrammazione|ambiente multiprogrammato]], gli stalli si verificano più frequentemente, poichè più thread possono competere per un insieme limitato di risorse.
In presenza di uno stallo è necessario eliminare i processi bloccati e a loro volta i processi che dipendono da quelli bloccati, e così via.

Condizioni necessarie (ma non sufficienti) per il verificarsi di uno stallo:
- ==MUTUA ESCLUSIONE==: risorse utilizzate da un solo processo alla volta
- ==ALLOCAZIONE PARZIALE==: processo richiede diverse risorse durante la sua evoluzione
- ==NON SOTTRABILITÀ==: solo il processo che possiede la risorsa può rilasciarla
- ==ATTESA CIRCOLARE==: ci sono $n$ processi dove ognuno aspetta una risorsa che non verrà rilasciata

==LIVELOCK / STALLO ATTIVO==: situazione simile al deadlock, dove i thread non sono effettivamente bloccati, ma di fatto non progrediscono.
In pratica, si ha un livelock quando un thread tenta continuamente un'azione che non ha successo.