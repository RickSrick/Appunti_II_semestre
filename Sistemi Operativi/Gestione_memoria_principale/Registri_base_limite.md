# REGISTRI BASE E LIMITE
- ==REGISTRO BASE==: contiene il più piccolo indirizzo legale della memoria fisica allocata al processo
- ==REGISTRO LIMITE==: determina la dimensione dello spazio di memoria allocato al processo
![300](registri_base_limite_2.png)

# PROTEZIONE
Ogni processo deve avere uno spazio di memoria separato: i registri base e limite definiscono lo spazio degli indirizzi fisici per ogni processo.
Per proteggere gli spazi di memoria del SO o di altri processi utente, la CPU confronta gli indirizzi generati da un processo utente con i valori contenuti nei due registri:
- indirizzo $\geq$ base
- indirizzo $\lt$ base + limite
Solo il SO può caricare i registri base e limite usando istruzioni privilegiate.
Un tentativo di accedere agli spazi di memoria del SO o di altri processi utente effettuato in modalità utente provoca un segnale di eccezione, che trasferisce il controllo al SO, e l'emissione di un messaggio di errore.
![700](registri_base_limite.png)