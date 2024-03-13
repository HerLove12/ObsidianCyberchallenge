architettura RISC-V 
capire come:
- cpu memoria e programma meorizzato
- linguaggio assembly
- array e stringhe
- procedure
### Programma Memorizato
Il programma viene trasformato in bit e salvato in un blocco di memoria e la cpu lo esegue interagendo con essa.
### DLL
Java legge un istruzione per volta per compilare il programma che avviene a runtime e dinamicamente usa le librerie.

### Assembly
rappresentazione simbolica della codifica binaria usata dal calcolatore(linguaggio macchina). Va in base all'hardware.
permetti di:
- gestione registri
- caricare dati in memorioa
Assembly non ha costrutti ma solo i salti.

### Instruciton set
Ci sono 2 tipi di instruction set che sono CISC e RISC

##### CISC:
- enfasi su hardware
- istruzioni complesse multi-clock
- istruzioni LOAD e STORE da memoria a memoria
- piccoli codici con molti cicli al secondo
- transistor per salvare struzioni complesse

##### RISC:
- enfasi su software
- istruzioni ridotte su single-clock
- operazioni LOAD e STORE su registri
- pochi cicli al secondo
- transistor per memoria di registri

##### RISC-V a 32bit
standard unix gratuito e adatto a tutti i tipi di sistema ed ha estensioni disponibili.

**Memoria:**
Word -> 4 Byte = 32 bit
il RISC-V indirizza al byte quindi: 
0->indirizzo prima word, 
4-> indirizzo seconda word.

**ordinamento di byte in memoria:**
- Big Endian -> il byte più significativo ha indirizzo più basso
- Little Endian -> il byte più significativo ha indirizzo più alto

**registri:**
ci sono 32 registri e hanno un nome di registro col formato "xN" e dei nomi simbolici per dare un senso.

istruzioni di load e store:
B->byte
H->half
W->word

istruzioni di flusso:
jump
branch

esempio swap due variabili in memoria:
```assembly
.data
a: .word 4
b: .word 5

.text
lw t0, a
lw t1, b
la t3, a       #indirizzo di b nel registro t3
sw t1, 0(t2)   #valore di a si mette nell'indirizzo di b
la t4, b
sw t1, 0(t4)
```
moltiplicazione con somme ricorrenti, numero più grande sommato.
```assembly

```