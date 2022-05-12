# SERVIZI DI UN SO
In fase di progettazione, il SO può essere definito o valutato in base a:
- i servizi che dovrà offrire
- l'interfaccia messa a disposizione di programmatori e utenti
- la complessità di realizzazione

## SERVIZI USER-ORIENTED
- ==INTERFACCIA UTENTE==: tutti i SO attuali sono dotati di un'interfaccia utente, [[CLI|a riga di comando]] e/o [[GUI|grafica]]
- ==ESECUZIONE DI PROGRAMMI==: capacità di caricare un programma in [[Memoria_principale_processi|memoria principale]] ed eseguirlo, eventualmente rilevando e gestendo situazioni di errore
- ==OPERAZIONI DI I/O==
- ==GESTIONE DEL FILE SYSTEM==: capacità dei programmi di creare, leggere, scrivere e cancellare file e di muoversi nella struttura delle directory
- ==[[Processi#COMUNICAZIONE TRA PROCESSI|COMUNICAZIONI]]==: scambio di informazioni tra processi in esecuzione sullo stesso elaboratore o su sistemi indipendenti connessi in rete
- ==RILEVAMENTO DI ERRORI==: il SO deve tenere il sistema di calcolo sotto controllo costante per rilevare errori, che possono verificarsi nella CPU, nella memoria, nei dispositivi di I/O o durante l'esecuzione di programmi utente

## ALTRI SERVIZI
Servizi per assicurare l'efficienza del sistema, non esplicitamente rivolti all'utente:
- ==ALLOCAZIONE DI RISORSE==: quando due o più processi vengono serviti in concorrenza, le risorse disponibili devono essere allocate equamente in ognuno di essi
- ==ACCOUNTING E CONTABILIZZAZIONE DELL'USO DI RISORSE==: tenere traccia di quali utenti usano quali e quante risorse del sistema
- ==PROTEZIONE E SICUREZZA==: i possessori di informazioni memorizzate su un sistema multiutente o distribuito devono essere garantiti da accessi indesiderati ai propri dati, e processi concorrenti non devono interferire tra loro:
	- ==PROTEZIONE==: assicurare che tutti gli accessi alle risorse di sistema siano controllati
	- ==SICUREZZA==: si basa sull'obbligo di identificazione tramite _password_ e si estende alla difesa dei dispositivi di I/O esterni (e.g. router, adattatori di rete, etc.) da accessi illegali