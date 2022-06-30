# CONDIVISIONE DI FILE
La condivisione di [[File|file]] (_file sharing_) è particolarmente utile negli ambienti multiutente, per permettere la collaborazione tra utenti e per ridurre le [[Risorse|risorse]] richieste per raggiungere un dato obiettivo di calcolo. Tuttavia, la condivisione non può prescindere da uno schema di protezione che garantisca un controllo di accesso ai file mediato dal SO.
Nei sistemi distribuiti, i file vengono condivisi attraverso una rete. Il [[Network_file_system|Network File System (NFS)]] è un metodo molto diffuso per realizzare la condivisione di file distribuiti.

Il modello più diffuso è legato ai concetti di:
- ==PROPRIETARIO== del file: l'utente che ha creato il file e che può cambiare gli attributi del file o della [[Directory|directory]]
- ==GRUPPO== di utenti: sottoinsieme di utenti autorizzati a condividere l'accesso al file, e ai quali il proprietario è "affiliato"
Gli identificatori del gruppo (_GroupID_) e del proprietario (_UserID_) di un dato file o directory sono memorizzati come attributi del file nel relativo elemento di directory.

## ==SEMANTICA DELLA COERENZA==
Specifica quando le modifiche apportate da un utente ai dati contenuti in un file possono essere osservate da altri utenti. È correlata agli [[Race_condition|algoritmi di sincronizzazione fra processi]], anche se tende ad essere meno critica a causa delle lunghe latenze e delle basse velocità di trasferimento dei dischi e della rete.
La semantica UNIX impone:
- che le scritture in un file aperto da un utente siano immediatamente visibili agli altri utenti che hanno aperto contemporaneamente lo stesso file
- la condivisione del puntatore alla posizione corrente nel file: il file ha una singola immagine e tutti gli accessi si alternano, intercalandosi, a prescindere dalla loro origine