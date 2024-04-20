per vedere la fase di preprocessing si puo fare `gcc -E <file>` invece `gcc -s <file>` ritorna il codice in assembly infine di ha il file oggetto .o con `gcc -c <file>`. L'ultima fase è quella di linking che unisce le librerie chiamate al file oggetto in un unico oggetto e crea un eseguibile.

Il linking avviene in 2 modi possibili:
- statico -> un file unico con il contenuto di entrambi i file
- dinamico -> il file binario ha dei riferimenti alla libreria che vengono invocati a runtime

### File EFL
Executable and Linkable Format, formato standard per i sistemi UNIX.
Ci sono 3 tipi di file oggetto:
- Relocatable files -> file oggetto compilati `file.o` che può essere allocato a indirizzi di memoria su richiesta.
- Executable files -> programma eseguibile
- Shared Object files -> con estensione `.so` file che puo essere caricato con un link

Struttura del file ELF
- Header -> descrive il contenuto del file
- Header Table -> informazioni su come creare il programma
- Sezioni -> necessarei per il linking(istruzioni, data, tabella di simboly, relocazioni...)
- Section header table

i valori delle funzioni chiamate vengono salvati nel registro EAX.
Altri due registri importanti sono ESP ovvero lo stack pointer che è un puntatore alla prima riga dello stack mentre EBP punta alla base dello stack

i registri sono di 8(al) o 16(ax) bit, se c'è una 'e' davanti quindi 'eax' sono a 32 bit, se c'è una 'r' sono a 64 bit quindi 'rax'.

operazioni:
- push op1 -> mette op1 in cima allo stack e incrementa lo stack pointer (4 o 8 byte)
- pop op1 -> rimuove l'elemento di dalla cima dello stack e decrementa lo stack pointer
- lea op1, op2 copia l'**indirizzo di memoria** op2 in op1

### Processo a runtime
Della memoria viene allocata al porocesso di un programma per memorizzare dati e codice
la memoria allacata è divisa in segmenti tra cui: codisce(low address sola lettura), .data(dati inizializzati), .bss(dati non inizializzati), heap(dati allocati con malloc o new), spazio che potrebbe essere vuoto, stack(funzioni locali)

### Stack
Lo stack tiene memorizzate tutte le funzioni locali e viene diviso in stack frames per ogni chiamata e deallocata a ogni return.
Se una funzione ricorsiva è in tail si puo allocare e riallocare lo stesso blocco di memoria.

### Debugging
GDB -> gnu project debugger
esegue il programma istruzione per istruzione di assembly 
le opzioni fondamentali sono:
- breakpoint -> indirizzo di un'istruzione a cui si interrompe l'esecuzione
	- breakpoint -> certo punto del codice
	- watchpoint -> si ferma in una certa condizione
	- catchpoint
	`info functions; break [location]; disassemble <function>`
- signal


### Memory corruption
- Buffer overflow -> accesso ad array out of bounds, copia di una stringa in un buffer troppo piccolo, puntatore che punta a una posizione errata.
	- puo essere usato -> cambiare contenuto delle variabili, cambiare i contenuti dello stack
- Variables overriding -> cambiare l'indirizzo di return di una funzione
	- esempio: sovrascrivere buffer e base pointer e cambiare il return address con l'indirizzo della funzione che si vuole chiamare. IL return è un jump.
- 