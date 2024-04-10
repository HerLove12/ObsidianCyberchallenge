algoritmi distribuiti che devono avere la sicurezza garantita

protocollo -> insieme di regole che determinano lo scambio di messaggi fra due o piu entità

protocolli:
- Accademici: diffie hellman, Needhan-Schroder, key exchange, pake
-

Needham-Schroeder ->autenticazione mutua degli agenti
	a -> {A,Na}kb
	b -> {Na, Nb}ka
	a -> {Nb}kb
vulnerabile a Man in the Middle e fixato da Lowe che corregge il protocollo aggiungendo l'identita
	c ->{Na, Nb, B}

Needham-Schroeder chiave condivisa -> c'è un key distribution center KDC che genera le chiavi su richiesta di A e B.


tipi di attacchi:
- replay attack -> riutilizzo di messaggi precedenti 
- man in the middle -> uomo in mezzo a due host
- reflection attack -> sfrutta le stesse capacota e protocolli del server
- type flaw attack -> sostituzione il tipo di un campo del messaggio con un altro tipo

