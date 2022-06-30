# SCHEDULING DEL [[Hard_disk_drive|DISCO]]
Il SO è responsabile dell'uso efficiente dell'hardware: per i dischi ciò significa garantire [[Hard_disk_drive#MISURE|tempi di accesso]] contenuti e ==AMPIEZZE DI BANDA== elevate: numero totale di byte trasferiti, diviso per il tempo trascorso fra la prima richiesta e il completamento dell'ultimo trasferimento.
Scomponendo il tempo di accesso nei suoi componenti, per migliorare le prestazioni si può intervenire solo sul [[Hard_disk_drive#MISURE|seek time]], e si cerca quindi di minimizzarlo. Il seek time è proporzionale alla distanza di posizionamento fra le [[Hard_disk_drive|tracce]].

Quando un processo, utente o di sistema, deve effettuare un'[[Connessione_dispositivi_memoria|operazione di I/O]] relativa ad un'unità a disco, effettua una [[Chiamate_di_sistema|chiamata]] al SO. La richiesta di servizio contiene:
- specifica del tipo di operazione (i.e. immissione o emissione di dati)
- indirizzo su disco relativamente al quale effettuare il trasferimento
- indirizzo nella memoria relativamente al quale effettuare il trasferimento
- numero di byte da trasferire

Una richiesta di accesso al disco può venire soddisfatta immediatamente se unità a disco e [[Input_output|controllore]] sono disponibili, altrimenti la richiesta deve essere aggiunta alla coda delle richieste inevase per quell'unità. Il SO ha l'opportunità di scegliere quale richiesta inevasa completare per prima, usando un [[Algoritmi_scheduling_disco|algoritmo di scheduling del disco]].