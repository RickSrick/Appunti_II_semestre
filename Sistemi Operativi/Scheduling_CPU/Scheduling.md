# SCHEDULING
==SCHEDULING==: meccanismo messo in atto per massimizzare l'utilizzo della CPU, che consiste nel passare rapidamente dall'esecuzione di un [[Processo|processo]] al successivo, garantendo il [[Multiprogrammazione|timesharing]].
Si utilizzano tre code per lo scheduling:
- ==JOB QUEUE==: insieme dei processi presenti nel sistema
- ==READY QUEUE==: insieme dei processi pronti e in attesa di essere eseguiti, che risiedono in [[Memoria_principale_processi|memoria centrale]]
- ==CODE DEI DISPOSITIVI==: insieme dei processi in attesa per un dispositivo di I/O