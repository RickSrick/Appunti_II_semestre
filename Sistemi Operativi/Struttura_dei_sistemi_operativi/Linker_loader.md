# LINKER E LOADER
Il codice sorgente di ogni programma viene compilato in file oggetto progettati per essere caricati in qualsiasi posizione di memoria fisica: ==FILE OGGETTO RILOCABILI==. Vengono combinati dal ==LINKER== in un singolo file eseguibile binario in cui vengono incluse anche le funzioni di libreria e che risiedono in memoria secondaria. Questi file vengono poi caricati in memoria centrale dal ==LOADER== per essere eseguiti, e nella fase di rilocazione si assegnano gli indirizzi assoluti alle parti del programma e ai dati.

I moderni sistemi _general purpose_ non collegano le librerie ai file eseguibili; piuttosto, le ==LIBRERIE COLLEGATE DINAMICAMENTE== (e.g. DLL in Windows) vengono caricate secondo necessità e sono condivise da tutti i programmi che utilizzano la stessa versione della libreria.
I file oggetto ed eseguibili hanno formati standard, affinchè il SO sappia come caricarli e avviarli (e.g. ==EXECUTABLE AND LINKABLE FORMAT (ELF)== su sistemi UNIX-like).
![500](linker_loader.png)

Le applicazioni compilate su un SO di solito non sono eseguibili sugli altri, in quanto ogni SO offre le proprie [[Chiamate_di_sistema|system call]] uniche, i propri formati di file eseguibili, etc. Tuttavia, le applicazioni possono essere multi-SO se sono scritte in:
- linguaggio interpretato, con inteprete disponibile su più SO (e.g. Python)
- linguaggio che include una VM contenente il programma in esecuzione (e.g. Java)
- linguaggio standard compilato separatamente su ogni SO (e.g. C)
==APPLICATION BINARY INTERFACE (ABI)==: analogo all'[[Chiamate_di_sistema|API]], definisce in che modo i diversi componenti del codice binario possono interfacciarsi per un dato SO con una data architettura, CPU, etc.; vincolano il codice binario, a differenza delle API che vincolano il codice sorgente.