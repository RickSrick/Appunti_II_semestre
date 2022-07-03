# SWAPPING
==SWAPPING==: spostare tutte o una parte delle pagine di un processo tra la memoria principale e un dispositivo di memoria secondaria.
==SWAPPER PIGRO==: si sposta una pagina in memoria solo quando è necessario.
La richiesta di una pagina corrisponde ad un riferimento alla pagina:
- riferimento non valido: _abort_
- pagina non presente in memoria: _trasferimento in memoria_
![550](swapping.png)
A seconda del SO si possono avere:
- _[[File|file]] di [[Gestione_swap|swap]]_, che risiedono nel [[File_system|file system]] (e.g. Windows)
- _[[Struttura_disco|partizioni]] di swap_, sezioni del disco interamente dedicate allo swapping e inizializzate con un proprio tipo di file system (e.g. Linux)
L'uso della partizione è generalmente migliore dal punto vista delle prestazioni, perché evita che lo swap vada soggetto alla [[Frammentazione|frammentazione]] tipica di alcuni file system.