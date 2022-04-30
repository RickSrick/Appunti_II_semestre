# PROGETTAZIONE DI UN SO
Per progettare e realizzare un SO è necessario separare due aspetti fondamentali:
- ==POLITICHE==: quali sono i compiti e i [[Servizi|servizi]] che il SO dovrà fornire e svolgere? (cosa bisogna fare?)
- ==MECCANISMI==: come realizzare tali compiti e servizi? (come fare?)
Esempio: i problemi di assegnazione delle risorse impongono decisioni politiche, mentre i meccanismi servono a implementarne l'accesso controllato.

# SVILUPPO DI UN SO
Tradizionalmente i SO venivano scritti in linguaggio _assembly_; successivamente, furono utilizzati linguaggi specifici per la programmazione di sistema, quali _Algol_ e _PL/1_; attualmente vengono invece sviluppati in linguaggi di alto livello, particolarmente orientati al sistema, come C o C++.
In realtà, normalmente, si utilizza un mix di linguaggi:
- componenti di basso livello sviluppate in assembly (e.g. driver dei dispositivi)
- kernel in C (link a kernel?)
- [[Programmi_di_sistema|programmi di sistema]] realizzati tramite C, C++ e linguaggi di scripting, quali PERL, Python, shell script
	caratteristiche:
	- veloci da codificare
	- codice compatto, di facile comprensione, messa a punto e manutenzione
	- portabilità