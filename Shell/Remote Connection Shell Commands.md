- #nc `[options] <host> <port>` Connessione remota, ricevere e inviare dati
	- -l `<n>` Servizio in ascolto su una deteminata porta n
	
- #ssh `[-p <port>|options] username@hostname`
	- -i `<file>` Specificare un file con RSA private key da usare invece della password
	- -t Cambiare shell | ex. `ssh -p xxx username@hostname -t sh`
	- "`<comando>`" esegue all'avvio | ex. `ssh -p xxx username@hostname "cat readme"`
	
- #scp `[-P <port>|options] username@hostname:/path/to/file /path/local/pc`
	- -r recursive
	- send files->`scp [-P]user@localhost:file1 user@hostname:/location`
	
- #ssl `openssl s_client -connect hostname:<port>`
- #curl `[options|method][URL]`
	- -x permette di usare un proxy
	- -u`[username]:[password]` autenticazione proxy
	- -d mandare dati con un metodo POST
