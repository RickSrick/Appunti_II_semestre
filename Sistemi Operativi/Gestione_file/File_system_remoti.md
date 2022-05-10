# FILE SYSTEM REMOTI
==FILE SYSTEM REMOTI==: uso della rete per ottenere l'accesso a [[File|file]] residenti su sistemi remoti:
- trasferimento richiesto esplicitamente, anonimo o autenticato, via protocollo _FTP_
- tramite un _file system distribuito_, che permette la visibilità e l'accesso automatico del calcolatore locale a [[Directory|directory]] remote
- accesso semi-automatico tramite browser attraverso il _World Wide Web_ (l'FTP anonimo non è esplicito, ma nascosto da un _wrapper_, nell'operazione di download)

## ==MODELLO CLIENT-SERVER==
Il _server_ mette a disposizione risorse, sotto forma di directory e file, ai _client_ che ne fanno richiesta.
==MODELLO MOLTI-A-MOLTI==: un server può gestire richieste provenienti da più client, e ogni client può accedere a più server.
Possono verificarsi problemi di autenticazione, come protocolli insicuri che possono condurre a ==SPOOFING==: tipo di attacco informatico che impiega in varie maniere la falsificazione dell'identità. La sicurezza si ottiene mediante autenticazione reciproca di client e server tramite chiavi di cifratura. Sorgono così nuovi problemi:
- compatibilità tra server e client, relativamente all'algoritmo di cifratura
- scambio sicuro delle chiavi

## PROBLEM DEI [[File_system|FILE SYSTEM LOCALI]] E REMOTI
Nei file system locali possono verificarsi [[Malfunzionamenti|malfunzionamenti]] dovuti a:
- problemi hardware dei dischi che li contengono
- alterazioni dei metadati (e.g. informazioni per il reperimento dei file, contenute nella directory)
- problemi ai controllori dei dischi
- problemi ai cavi di connessione
- errori umani

Nei file system remoti, i malfunzionamenti possono avvenire anche per cadute della rete o dei server remoti sui quali risiedono i file. Per il ripristino da malfunzionamenti è necessario mantenere alcune informazioni di stato sia sui client che sui server. Tuttavia, i protocolli attualmente più diffusi, come [[Network_file_system|NFS]], non mantengono informazioni di stato. Ad esempio, NFS v3 trasferisce tutte le informazioni nella singola richiesta, che si suppone legittima, con alta tolleranza ai guasti ma scarsa sicurezza.