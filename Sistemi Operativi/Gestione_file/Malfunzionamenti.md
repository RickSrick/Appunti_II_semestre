# MALFUNZIONAMENTI
Poichè i file e le directory sono mantenuti sia in RAM (parzialmente) sia nei dischi, è necessario assicurarsi che eventuali malfunzionamenti del sistema non comportino la perdita di dati o la loro incoerenza.
Esempio:
	creazione di un file:
	- modifica dell'elemento di directory
	- allocazione blocchi di dati e [[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|FCB]]
	- aggiornamentio delle informazioni sui blocchi liberi e FCB liberi
	Se si ha un crollo del sistema si possono avere incoerenze fra le strutture: il contatore degli FCB liberi potrebbe indicare un FCB allocato, ma la directory non contiene un puntatore all'elemento.

## ==VERIFICATORE DI COERENZA==
Confronta i dati nella struttura di directory con i blocchi di dati sul disco e tenta di fissare le eventuali incoerenze. Su UNIX viene indicato con _fsck_, mentre su DOS / Windows viene indicato con _chkdsk_.
Esempio: se si perde un elemento di directory, si può ricostruire un file con [[Allocazione#ALLOCAZIONE CONCATENATA|allocazione concatenata]], ma non uno [[Allocazione#ALLOCAZIONE INDICIZZATA|allocato tramite indice]].
Si impiegano programmi di sistema per copiare dati dal disco ad un altro dispostivo di memorizzazione (e.g. altri dischi magnetici, supporti ottici): ==BACK-UP==. Si possono poi recuperare file persi o il contenuto di dischi danneggiati ricaricandoli dal back-up.

## ==ACCANTONAMENTO DEI SETTORI==
Per gestire i blocchi difettosi, durante la [[Formattazione#FORMATTAZIONE FISICA DI BASSO LIVELLO|formattazione fisica]] si mantiene un gruppo di riserva non visibili al SO. Il controllore è istruito per sostituire, dal punto di vista logico, un settore difettoso con uno dei settori di riserva inutilizzati.
![650](accantonamento_settori.png)

## ==DISTANZA DI HAMMING==
Le memorie elettroniche, o magnetiche come i [[Hard_disk_drive|dischi]], memorizzano bit usando meccanismi che possono occasionalmente generare errori. Si può formalizzare il concetto di errore con una codifica a _n_ bit, chiamando _C_ la codifica corretta e _C'_ la codifica errata.
_Distanza di Hamming_ tra le codifiche: _H(C, C')_, numero di cifre binarie differenti a parità di posizione:
- H(C, C') = 0: C e C' sono uguali
- H(C, C') = _n_: C e C' differiscono per _n_ bit

Per scoprire gli errori singoli, ovvero le situazioni in cui H(C, C') = 1, aggiungiamo un ==BIT DI PARITÀ== alla codifica, posto a 1 o a 0 in modo che il numero di bit uguali a 1 nelle varie codifiche sia necessariamente o pari o dispari. Se si verifica un errore singolo in C', allora il numero di bit 1 non sarà più pari o dispari. Tuttavia, con un singolo bit di parità, non scopriremo mai un numero di errori pari.
In verità, usare un bit di parità significa usare una codifica non minimale nella rappresentazione dell'informazione: si usano solo la metà dei codici permessi su _n+1_ bit, e la distanza minima di Hamming tra coppie di codifiche permesse è 2.

Per scoprire fino a _d_ errori su singoli bit è necessario che la distanza di Hamming della codifica sia _d+1_. Supponiamo di avere una codifica siffatta, e supponiamo che C' sia una codifica erronea di C tale che $1<\mathrm{H}\left(\mathrm{C}, \mathrm{C}^{\prime}\right) \leq d$. C' non può essere scambiato per una codifica valida, perché in questo caso dovrebbe essere vero che $H\left(C, C^{\prime}\right) \geq d+1$

Per correggere fino a _d_ errori su singoli bit è necessario che la distanza di Hamming della codifica sia _2d+1_. Supponiamo di avere una codifica siffatta, e supponiamo che C' sia una codifica erronea di C tale che $1<H\left(C, C^{\prime}\right) \leq d$. C' non può essere scambiato per una codifica valida, perché in questo caso dovrebbe essere vero che $H\left(C_{1}, C^{\prime}\right) \geq 2 d+1$. Poiché C è la codifica valida più vicina a C', possiamo pensare che C sia la codifica corretta e correggere l'errore.