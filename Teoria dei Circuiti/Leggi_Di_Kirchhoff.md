# LEGGI DI KIRCHHOFF
## LEGGE DI KIRCHHOFF DELLE CORRENTI (LKC)
Data una rete di n-poli in regime variabile quasi stazionario, è nulla in ogni istante la somma algebrica delle correnti dei lati di un qualsiasi insieme di taglio:
$$\sum_{insieme~di~taglio}{\pm i(t)}=0$$
## LEGGE DI KIRCHHOFF DELLE TENSIONI (LKT)
Data una rete di n-poli in regime variabile quasi stazionario, è nulla in ogni istante la somma algebrica delle tensioni dei lati appartenenti ad una qualsiasi maglia:
$$\sum_{maglia}{\pm v(t)}=0$$

## EQUAZIONI TOPOLOGICHE DELLA RETE
Le equazioni che esprimono le leggi di Kirchhoff sono dette equazioni topologiche della rete.

Utilizzando la LKT si possono trovare $m=l-n+1$ equazioni indipendenti tra loro con $l$ incognite

Utilizzando la LKC si possono trovare $l_a = n - 1$ equazioni indipendenti tra loro, con $l$ incognite

Una rete ha quindi in tutto $2l$ incognite, le $l$ tensioni e $l$ correnti del circuito, e utilizzando le equazioni topologiche della rete si possono trovare $l$ equazioni.

## CONSERVAZIONE DELLE POTENZE ELETTRICHE
In conseguenza delle LKC e LKT, vale che è nulla in ogni istante la somma delle potenze entranti in tutti i bipoli:
$$\sum_{h=1}^{l}{p_{h,entranti}(t)}=0$$