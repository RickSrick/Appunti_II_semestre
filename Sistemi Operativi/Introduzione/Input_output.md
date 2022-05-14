# INPUT/OUTPUT (I/O)
Una percentuale cospicua del codice del SO è dedicata alla gestione dell'==I/O==. L'interazione con i dispositivi di I/O è fondamentale per la progettazione di un SO affidabile ed efficiente.
==CONTRLLORE==: speciale unità di elaborazione che si occupa di un particolare tipo di dispositivo, e che può gestire una o più unità ad esso connesse.
==DEVICE DRIVER==: "SO" del controllore; presente uno per ciascun controllore di device, ne guida le operazioni di I/O e garantisce un'interfaccia comune fra kernel e controllore.

In seguito ad una richiesta di I/O da parte di un processo utente, si verifica un [[Interrupt|interrupt]]. Dopo l'inizio dell'operazione di I/O, il flusso di esecuzione può seguire due percorsi distinti:
- ==I/O SINCRONO==: si restituisce il controllo al processo utente solo dopo il completamento dell'operazione di I/O; la CPU è mantenuta in stato idle dalla [[Chiamate_di_sistema|systemm call]] $wait()$, e ad ogni istante si può avere una sola richiesta di $\mathrm{I} / \mathrm{O}$ in esecuzione
- ==I/O ASINCRONO==: si prevede la restituzione immediata del controllo a un altro processo utente; in questo modo l'I/O può proseguire mentre il sistema esegue altre operazioni

Il sottosistema di I/O è quindi formato da:
- una componente di gestione della memoria che include il ==BUFFERING==: memorizzazione temporanea, durante il trasferimento, di dati in memorie locali alle periferiche
- ==[[Dispositivi_di_memoria#CACHING|CACHING]]==
- ==SPOOLING==: buffer per dispositivi che non supportano _interleaved datastreams_ (e.g. stampanti), per la gestione dell’I/O asincrono
- un’interfaccia generale per i driver dei dispositivi
- i driver per i dispositivi specifici presenti nel sistema di calcolo

## ==DIRECT MEMORY ACCESS (DMA)==
Il controllore di device trasferisce blocchi di dati dal buffer locale direttamente nella memoria principale, senza intervento della CPU. In questo modo viene generato un solo interrupt per regolare il trasferimento di ciascun blocco, invece di un interrupt per byte. Viene utilizzato per dispositivi di I/O ad alte prestazioni, con velocità di trasferimento comparabili alla velocità di accesso alla memoria centrale. È usato da molti sistemi hardware come controller di unità a disco, schede grafiche, schede di rete e schede audio.