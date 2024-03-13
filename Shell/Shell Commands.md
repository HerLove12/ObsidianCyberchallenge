`comando <opzioni><argomenti>`
i piu moderni possono avere un sottocomando.
Possiamo individuare diverse categorie di comandi, in questo file sono presenti i comandi generici per muoversi nella bash, filtrare e gestire file.

Guarda: [[Remote Connection Shell Commands]], [[File Compressing Shell Commands]], [[Special Characters and Regex in Shell Commands]]

- #ls List Files
	- -a visualizza anche file nascosti
	- -l informazioni estese
	- -s dimensione file
	- -F aggiunge un carattere finale che denota il tipo
	- -R recursive subdir
	
- #rm Remove FIles
	- -r recurisve
	- -i prompt
	- -f non chiede il permesso
	
- #cat Output FIle
	- -n ogni linea ha un numero
	- -v visualizza caratteri non stampabili
	- -e visualizza un $ a fine di ogni linea(da usare con -n)
	
	more -> visualizza file una pagina alla volta
	less -> scorrere il file
	head -> visualizza le prime righe di un file
	tail -> visualizza le ultime righe di un file
	sort -> ordina le righe di un file
	
- #mkdir Create Directory
	- -p crea dir intermedie esplicitate nei parametri | ex: "mkdir -p documenti/lezioni"
	
- #mktemp Create Temporary DIrectory
	- -d crea una cartella temporanea
	
- #rmdir Remove Directory (only if empty)
	- -p cartelle intermedie
	
- #cp Copy `cp <file><location>`
	- -i prompt
	- -f non chiede il permesso
	
- #mv Move `mv <file><location>`
	- -i prompt
	- -f non chiede il permesso
	
- #man Manual
	- -k `<keyword>` cerca una parola nel manuale
	
- #find `[options]<path>` Cerca file in un path
	- -name condizione del nome | ex. “*.c”
	- -iname no case sensitive
	- -type | ex. `-type d -iname “*loads”` cerca dir il cui nome finisce con ...
	- -size | ex. `-size +100M -size -200M` cerca file che rispetta le dimensioni date
	- -L va alle dir o file puntate dai [[link simbolici]]
	
- #grep `[options]"pattern"<file>` Cerca pattern
	- ex. `grep “pluto” /....`
	- ex. `grep “^password” *` la riga deve iniziare con la parola detta
	- ex. `grep “lines.*empty” testo.txt`
	
- #file Visualizza tipologia di file
- #uniq 
	- -u stampa le righe di un file che hanno una sola ricorrenza