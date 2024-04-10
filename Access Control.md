algoritmi distribuiti che devono avere la sicurezza garantita

protocollo -> insieme di regole che determinano lo scambio di messaggi fra due o piu entità

protocolli:
- diffie hellman, Needhan-Schroder, key exchange, pake
possono essere simbolici(crittografia perfetta)
o computazionali,lavorano con una serie di bit e vedono l'avversario come una macchina di touring probabilistica.

Needham-Schroeder ->autenticazione mutua degli agenti
	a -> {A,Na}kb
	b -> {Na, Nb}ka
	a -> {Nb}kb
vulnerabile a Man in the Middle e fixato da Lowe che corregge il protocollo aggiungendo l'identita
	c ->{Na, Nb, B}

Needham-Schroeder chiave condivisa -> c'è un key distribution center KDC che genera le chiavi su richiesta di A e B.

vulnerabile a reply attack. Non c'è nessuna garanzia che il messaggio sia stato creato dal KDC nella sessione del protocollo corrente. SI fixa associando un timestamp alla chiave.

Kerberos -> protocollo per le autenticazioni/autorizzazione per applicazioni client server. Usa crittografia a chiave simmetrica. Crea un reame ovvero un environment con un kerberos server, dei client e dei server applicativi.

3 fasi:
- Autenticazione -> singola autenticazione in cui l'utente ottiene un ticket
- Ticket to server -> ticket specifico ottenuto per il servizio richiesto
- Richiesta del servizio

tipi di attacchi:
- replay attack -> riutilizzo di messaggi precedenti 
- man in the middle -> uomo in mezzo a due host
- reflection attack -> sfrutta le stesse capacota e protocolli del server
- type flaw attack -> sostituzione il tipo di un campo del messaggio con un altro tipo

