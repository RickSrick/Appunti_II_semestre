# LOCK SU FILE APERTI
==LOCK SU FILE APERTI==: offre una mediazione per l'accesso condiviso a file; garantito da alcuni SO e realizzazioni del [[File_system|file system]].
Può essere:
- _shared_ o _exclusive_:
	- ==SHARED==: più processi possono acquisirlo contemporaneamente
	- ==EXCLUSIVE==: solo un processo alla volta può acquisirlo
- _obbligatorio_ o _consigliato_:
	- ==OBBLIGATORIO==: l'accesso al file viene negato se il lock è già stato acquisito da un altro processo; il SO assicura l'integrità dei dati soggetti a lock
	- ==CONSIGLIATO==: i processi trovano che lo stato di un dato file è "bloccato" e decidono sul da farsi; il programmatore deve garantire la corretta acquisizione e cessione dei lock
