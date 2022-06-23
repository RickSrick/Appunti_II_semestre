# MODALITÀ
La ==MODALITÀ OPERATIVA DUAL-MODE== permette al SO di proteggersi e di proteggere le varie componenti del sistema di calcolo. È composta da:
- ==MODALITÀ UTENTE / USER MODE==: numero relativamente basso di privilegi verso la memoria, l'hardware e altre risorse.
- ==MODALITÀ KERNEL / KERNEL MODE==: stato di privilegio massimo riservato all'esecuzione del kernel; il codice in linguaggio macchina eseguito in tale modalità ha accesso illimitato alla memoria, all'hardware e alle altre risorse
==MODE BIT==: bit, cablato nell'hardware, il cui valore distingue le situazioni in cui il sistema esegue codice utente o codice kernel.

Ogni [[Chiamate_di_sistema|system call]] effettua il passaggio in modalità kernel, il quale non viene gestito tramite normali istruzioni, per motivi di sicurezza. Il ritorno dalla chiamata riporta il sistema in modalità utente, e questo passaggio viene gestito da _istruzioni privilegiate_, che possono essere eseguite solo in modalità kernel.

Il concetto di modalità può essere esteso oltre il dual mode:
- _virtualizzazione_: modalità distinta per indicare che il gestore della macchina virtuale ha il controllo del sistema, con più privilegi dei processi utente ma meno privilegi del kernel
- modalità distinte per diverse componenti del kernel

## ==ISTRUZIONI PRIVILEGIATE==
Sottoinsieme di istruzioni utilizzabili esclusivamente dal sistema operativo:
- abilitare/disabilitare [[Interrupt|interruzioni]]
- accedere ai registri di protezione della memoria
- gestire [[Interrupt|eccezioni]]
- arrestare la CPU