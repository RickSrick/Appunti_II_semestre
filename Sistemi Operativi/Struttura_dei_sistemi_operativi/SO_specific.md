# SO-SPECIFIC
Le applicazioni compilate su un SO di solito non sono eseguibili sugli altri, in quanto ogni SO offre le proprie [[Chiamate_di_sistema|system call]] uniche, i propri formati di file eseguibili, etc. Tuttavia, le applicazioni possono essere multi-SO se sono scritte in:
- linguaggio interpretato, con inteprete disponibile su più SO (e.g. Python)
- linguaggio che include una VM contenente il programma in esecuzione (e.g. Java)
- linguaggio standard compilato separatamente su ogni SO (e.g. C)

==APPLICATION BINARY INTERFACE (ABI)==: analogo all'[[Chiamate_di_sistema|API]], definisce in che modo i diversi componenti del codice binario possono interfacciarsi per un dato SO con una data architettura, CPU, etc.; vincolano il codice binario, a differenza delle API che vincolano il codice sorgente.