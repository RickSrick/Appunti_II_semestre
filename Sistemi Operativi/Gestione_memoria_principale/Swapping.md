# SWAPPING
==SWAPPING==: spostare tutte le pagine di un processo tra la memoria principale e un dispositivo di memoria secondaria
==SWAPPER PIGRO==: si sposta una pagina in memoria solo quando è necessario
Richiesta di una pagina = riferimento alla pagina
- riferimento non valido: _abort_
- pagina non presente in memoria: _trasferimento in memoria_
![550](swapping.png)
A seconda del SO si possono avere:
- _file di swap_, che risiedono nel file system (e.g. Windows)
- _partizioni di swap_, sezioni del disco interamente dedicate allo swapping e inizializzate con un proprio tipo di file system (e.g. Linux)
L'uso della partizione è generalmente migliore dal punto vista delle prestazioni, perché evita che lo swap vada soggetto alla frammentazione tipica di alcuni file system.

![[Introduzione_memoria_principale#SWAPPING OUT]]