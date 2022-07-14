# FORMATTAZIONE
## ==FORMATTAZIONE FISICA / DI BASSO LIVELLO==
Si suddivide il [[Hard_disk_drive|disco]] in [[Hard_disk_drive|settori]] che possono essere letti e scritti dal [[Connessione_dispositivi_memoria|controllore]] sul disco. Viene salvata su disco una struttura dati per ogni settore, contenente intestazione, coda e _Error Correcting Code (ECC)_. Hanno una dimensione standard pari a 512 byte.

## ==FORMATTAZIONE LOGICA==
Per poter impiegare un disco per memorizzare [[File|file]], il SO deve mantenere le proprie strutture dati sul disco. Si effettua quindi la _formattazione logica_: si [[Struttura_disco|partiziona]] il disco in uno o più gruppi di cilindri, ognuno dei quali rappresenta un "disco logico" su cui creare un [[File_system|file system]]. Per migliorare le prestazioni, la maggior parte dei file system accorpa i blocchi in gruppi detti ==CLUSTER==.