# INTERFACCIA A RIGA DI COMANDO / COMMAND LINE INTERFACE (CLI)
L'==INTERFACCIA UTENTE A RIGA DI COMANDO / COMMAND LINE INTERFACE (CLI)== permette di impartire comandi direttamente al SO, dette ==ISTRUZIONI DI CONTROLLO==; la sua funzione è di interpretare ed eseguire queste istruzioni di controllo. Funziona quindi come un ==INTERPRETE DEI COMANDI==.
Talvolta viene implementata nel kernel, altrimenti attraverso [[Programmi_di_sistema|programmi di sistema]] (e.g. UNIX / Linux). Può essere parzialmente personalizzabile, ovvero il SO può mettere a disposizione più ambienti diversi (==SHELL==) da cui l'utente può impartire le proprie istruzioni al sistema.

I comandi ricevuti dall'interprete possono essere eseguiti in due modi:
- se il codice relativo al comando fa parte del codice dell'interprete, si salta all'opportuna sezione di codice (il numero di comandi implementati determina la dimensione dell'interprete, dato che ognuno necessita del suo segmento di codice)
- i comandi vengono implementati attraverso programmmi di sistema, che devono essere creati con il nome appropriato e salvati nelle cartelle apposite (così l'interprete non viene modificato)

In molti sistemi solo un sottoinsieme delle funzionalità è disponibile via [[GUI]], mentre le funzioni meno comuni sono disponibili solo via linea di comando.
Le interfacce CLI semplificano l'esecuzione di comandi ripetuti, perchè sono programmabili. In modo simile, un task eseguito di frequente e composto da più comandi può andare a costituire uno ==SHELL-SCRIPT==; molto comuni nei sistemi UNIX-like, non vengono compilati, ma interpretati dalla CLI.
![650](cli.png)