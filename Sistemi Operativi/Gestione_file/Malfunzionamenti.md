# MALFUNZIONAMENTI
Poichè i file e le directory sono mantenuti sia in RAM (parzialmente) sia nei dischi, è necessario assicurarsi che eventuali malfunzionamenti del sistema non comportino la perdita di dati o la loro incoerenza.
Esempio:
	creazione di un file:
	- modifica dell'elemento di directory
	- allocazione blocchi di dati e [[Strutture_dati_file_system#STRUTTURE DATI DEL FILE SYSTEM RESIDENTI SU DISCO|FCB]]
	- aggiornamentio delle informazioni sui blocchi liberi e FCB liberi
	Se si ha un crollo del sistema si possono avere incoerenze fra le strutture: il contatore degli FCB liberi potrebbe indicare un FCB allocato, ma la directory non contiene un puntatore all'elemento.

==VERIFICATORE DI COERENZA== (_fsck_ in UNIX, _chkdsk_ in DOS / Windows): confronta i dati nella struttura di directory con i blocchi di dati sul disco e tenta di fissare le eventuali incoerenze.
Esempio: se si perde un elemento di directory, si può ricostruire un file con [[Allocazione#ALLOCAZIONE CONCATENATA|allocazione concatenata]], ma non uno [[Allocazione#ALLOCAZIONE INDICIZZATA|allocato tramite indice]].
Si impiegano programmi di sistema per copiare dati dal disco ad un altro dispostivo di memorizzazione (e.g. altri dischi magnetici, supporti ottici): ==BACK-UP==. Si possono poi recuperare file persi o il contenuto di dischi danneggiati ricaricandoli dal back-up.