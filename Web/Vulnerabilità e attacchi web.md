### File Disclosure
consiste nella possibilita' di estrarre alcuni file contenenti importanti informazioni da un server web 

Le informazioni sensibili possono essere:
- User uploaded files
- Configuration files es. `(tomcat-users.xml, flask configuration, web.config)`
- Source code

#### Paths101
- Absolute path -> percorso che indica la posizione di un file indipendentemente dalla working directory

   `/etc/passwd`
   
- Relative path -> percorso che indica la posizione di un file iniziando all'interno della working directory

   `foo/passwd`
#### #PathTraversal
E una vulnerabilita' che si verifica negli user input che non sono controllati da una sanitization e si possono injectare dei percorsi in funzioni come `open()` o equivalenti.

ex:
```php
$absolute="/var/www/";
$user_input=$_POST['input']; #entry point
include($absolute . $user_input); #sink
```

possono esserci piu' casi:
	➢ Plain injection `open($input)`
	➢ Prepended injection `open($input + '/foobar')`
	➢ Appended injection `open('/foobar' + $input)`
	➢ Appended and prepended `open('/foo'+$input+'/bar)`

#### #LFI
local file inclusion -> vulnerabilità in cui si può controllare il path di un file che viene passato ad una funziona di include o require.

si può fare in modo che il php includa un file diverso da quello pensato.


#### #Injections
Questa vulnerabilita' avviene spesso quando un'applicazione web usa programmi esterni o esegue il codice dinamicamente.

- **Command Injection** -> avvengono quando una web app passa un dato non sanificato ad una **System Shell**.
	- ex:  `system("ping" . $_GET['hostname']);` input:`example.com;ls` Si possono usare [[Special Characters and Regex in Shell Commands#Concatenatori|operatori logici]] e [[Special Characters and Regex in Shell Commands#BashExpressions|code substitution commands]].
	- un altro modo e' quello di effettuare un pingback per vedere se l'host attaccato riesce a pingare la nostra macchina con tool come wget o [[Remote Connection Shell Commands#curl|curl]] e ngrok
	- E' possibile anche instaurare una connessione **TCP** utilizzando i file speciali. Si puo' mettere dei dati su `/dev/tcp/*host*/*port*` che instaurera' una connessione e mandera' i dati.
	  ex. `echo Hello World > /dev/tcp/localhost/1337
	  
- **Code injection** -> Il codice injectato verra' eseguito dall'interprete dell'applicazione e non dalla shell.
- **SQL Injection** -> injecto codice SQL per trovare vulnerabilità, il payload classico è: `'` ricevendo un errore con questo si possono fare cose come `' OR True # `
#### #SSRF 
basic bypasses -> [link](https://brightsec.com/blog/ssrf-server-side-request-forgery/)
...

#### #XSS 
Cross site scripting -> injection di codice all'interno di un altro client. Il client "vittima" caricherà una pagina web con del docide js mandato dal server però con il nostro codice.

Il caso più basilare è **reflected** che avviene nei form di ricerca:
- controllare se il testo si porta dietro i tag html inserendo nel form input come -> `<b>ciao</b>` se in output riceviamo il testo in **bold** allora è possibile injectare js con il tag script -> `<script>alert(1)</script>`

- Possono esserci delle blacklist ma bisogna ricordare che js è case insensitive e si possono consultare [XSS Cheatsheet](https://cheatsheetseries.owasp.org/cheatsheets/XSS_Filter_Evasion_Cheat_Sheet.html). Un esempio è il tag IMG in cui si puo lanciare funzioni come `onerror()` oppure injectare codice direttamente nell'src 
- Usare Polyglot che con 1 payload trovano le vulnerabilità uscendo dagli scope.

- é possibile anche in PHP in scenari come questo:
```php
  echo 'hello' . $_GET['name'];
```

tuttavia esistono anche casi di XSS di tipo **stored** con cui vengono injectate intere pagine e storate sul server.