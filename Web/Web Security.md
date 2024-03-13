### #HTTP
Uno dei protocolli fondamentali su cui si basa il web è HTTP che lavora su TCP e solitamente sulla porta 80, l'HTTPS con TLS sulla porta 443.

Il protocollo HTTP gestisce delle risorse che sono
- file
- immagini
- informazioni
- ...

Risorse per headers: [MDN - manuale HTTP](https://developer.mozilla.org/en-US/docs/Web/HTTP)
#### #URL
la prima parte indica il protocollo utilizzato (es: http, https, ftp, ssh) dopo ci sono host e porta (hostname.com:port) e a questo segue il path (es. /index.html).
si possono aggiungere anche informazioni nella query (es. var1=val1&var2=val2) e si utilizza una **codifica** (URL encoding) -> (%{valore hex del carattere}, lo spazio sarebebe %20)

schema generale ->`protocol://hostname:port/<directory>/<file>?<query>#<fragment>`
es -> `http://foobar.com:8080/pagina.html?id=1`

si possono anche specificare delle credenziali prima dell'hostname (Basic Auth)
es -> `http://admin:password@foobar.com/`

#### Requests and Response
ogni riga della request e della responce terminano con un `\r\n` e per separare il body se ne usano 2.

Metodi principali:
- GET -> ottiene una risorsa
- POST -> richiesta con un body
- HEAD -> ottiene gli headers
- OPTIONS -> metodi disponibili

Headers obbligatori:
- Host: {hostname}

Headers importanti:
- Content-Type:
	- application/json
	- application/
- Date: data della risposta

Status code:
- 1xx -> informational
- 2xx -> successful
- 3xx -> redirect
- 4xx -> client error
- 5xx -> server error
##### #Request
Inizia con una request line a cui seguono gli headers e poi il body

```http
METODO /PERCORSO HTTP/{versione}
Host: hostname.com
User-Agent: ...
\r\n
\r\n
<body>
```


##### #Response
L'unica differenza è la prima riga che inizia con il protocollo, status code e messaggio
```http
HTTP/{versione} STATUS_CODE MSG
Host:{chi invia la risposta}
Date:{quando è stata ricevuta la risposta}
Comtent-Type:{formato contenuto della risposta}
headers:....
\r\n
\r\n
<body>
```

#### #Cookies
I cookie servono a rendere il protocollo HTTP stateful e sono informazioni testuali inviate nell header -> Cookie: ...
Se il server ha bisogno di mandarli lo farà nell'header -> Set-Cookie: token= ...
hanno dei metadati che sono:
- sito di origine -> Origin: sito di provenienza
- expire date
- policy di sicurezza
	- Secure -> il cookie viene mandato solo se HTTPS
	- HTTPOnly -> il cookie inviato è accessibile solo in eventuali nuove richieste, non è accessibile lato JS
	- SameSite -> Definisce quando il cookie può essere inviato 
		- none ->sempre inviati
		- strict -> solo a se stesso
		- lax -> manda solo a se stesso ma anche alla prima richiesta fatta

references: [MDN - manuale HTTP Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
#### Architettura web server PHP
 Ogni browser ha un engine per eseguire il js -> chromium:JS engine v8. la web app invia poi le richieste al web server.



