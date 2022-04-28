# KERNEL MONOLITICI
Le funzioni di gestione delle risorse sono tutte realizzate e implementate nel nucleo, e l'intero SO tende a identificarsi col nucleo. Il codice presenta così un'integrazione molto stretta, e ogni modulo opera su un unico spazio di indirizzi.
_Vantaggi_: se l'implementazione è sicura, un buon kernel monolitico è molto efficiente
_Svantaggi_: anche se ogni funzione è separata dal resto, un singolo bug può bloccare l'intero sistema
Usato soprattutto nei sistemi storici (e.g. _MS-DOS_, _UNIX_), attualmente realizzate tramite suddivisione in piccoli componenti, ciascuna delle quali deve essere un modulo ben definito del sistema, con interfacce e funzioni chiaramente stabilite durante la progettazione.

# APPROCCIO STRATIFICATO
In presenza di hardware appropriato, il SO può adottare un approccio stratificato, con la divisione in un certo numero di strati, ciascuno posto sopra quellli inferiori e con un'architettura tale per cui ogni strato utilizza solamente funzionalità e servizi appartenenti a strati di livello inferiore. Gli strati vanno dall'hardware (livello 0) all'interfaccia utente (livello N).
![300](strati.png)
_Vantaggi_: semplicità di realizzazione e messa a punto, operazioni effettuate strato per strato
_Svantaggi_:
- definire in modo appropriato i diversi strati può essere difficile, dato che ogni strato deve essere solamente le funzionalità degli strati inferiori
	esempi:
	- il driver della [[Memoria_virtuale|memoria virtuale]] dovrebbe trovarsi sopra lo [[Scheduler|scheduler della CPU]], perché può accadere che il driver debba attendere un'istruzione di I/O e, in questo periodo, la CPU viene sottoposta a scheduling
	- lo scheduler della CPU deve mantenere più informazioni sui processi attivi di quante ne possono essere contenute in memoria: deve fare uso del driver della memoria ausiliaria
- scarsa efficienza del SO, a causa del tempo di attraversamento degli strati per portare a termine l'esecuzione di una [[Chiamate_di_sistema|system call]]
![300](strati2.png)

# MICROKERNEL
Quasi tutte le funzionalità del kernel vengono spostate in modalità utente, lasciando un ==MICROKERNEL== che offre i servizi minimi di gestione dei processi, gestione della memoria e comunicazione. Lo scopo principale è fornire funzioni di comunicazione fra programmi client e servizi implementati esternamente, che hanno luogo tra moduli utente mediante scambio di messaggi mediati dal kernel.
Esempi: prime versioni di _Windows NT_, _Mach_, _Tru64_, _GNU Hurd_; _Mac OS_, con kernel _Darwin_, parzialmente basato su _Mach_.
_Vantaggi_:
- funzionalità del sistema più semplici da estendere, in quanto essi sono [[Programmi_di_sistema|programmi di sistema]] che si eseguono nello [[Introduzione_scheduling|spazio utente]] e non comportano modifiche al kernel
- facilità di modifica del kernel
- sistema più facile da portare su nuove architetture
- più sicuro e affidabile, in quanto meno codice viene eseguito in [[Introduzione_scheduling|modalità kernel]]
_Svantaggi_: possibile decadimento delle prestazioni, a causa dell'overhead di comunicazione fra spazio utente e spazio kernel

# KERNEL MODULARI
Si utilizza un approccio alla programmazione object-oriented: ciascun modulo:
- implementa una componente base del kernel, con interfacce e funzioni definite con precisione
- comunica con gli altri moduli mediante l'interfaccia comune
- può essere caricato o meno in memoria come parte del kernel, secondo le esigenze
L'architettura a moduli è simile a quella a strati, ma garanetisce SO più flessibili e facili da mantenere ed evolvere.
Approccio utilizzato da molti SO attuali (e.g. Linux, Solaris)

# IBRIDI
La maggior parte dei SO attuali non adotta un modello "puro", ma usano modelli ibridi che combinano diversi approcci implementativi allo scopo di migliorare le performance, la sicurezza e l'usabilità.