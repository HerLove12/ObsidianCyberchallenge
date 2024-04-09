![[Pasted image 20240325114318.png]]

Ci sono due tipi di cifrari a chiave simmetrica e sono:
- **Cifrari a blocchi**(*Block Cipher*) -> Il messaggio plaintext viene diviso in blocchi di lunghezza fissa `t` che vengono criptati uno alla volta.![[Pasted image 20240325114822.png]]

  Ci sono due classi di cifrari a blocchi che sono:
  - **Cifrari a sostituzione** -> Sostituzione di simboli o gruppi con altri simboli o gruppi.
	  - Es: monoalfabetico -> `Cifrario di Cesare`
	  - Es: polialfabetico -> `Cifrario di Vigenere`
  - **Cifrari a trasposizione** ->Permutazione dei simboli in ogni blocco
  ![[Pasted image 20240325121832.png]]
  
  
- **Cifrari a flusso**(*Stream Cipher*) -> E' un cifrario a blocchi con blocchi di lunghezza `t = 1`.![[Pasted image 20240325115128.png]]

### DES(Data Encryption Standard)
E' un algoritmo di crittografia simmetrica a blocchi:
- input(plaintext) -> 64bits
- output -> 64bits
- Key -> 64bits
- sub-kety -> 56bits
- round-key -> 48bits
- numero di round -> 16 rounds

Si ha una **permutazione iniziale** del plaintext da 64bit e questo viene criptato in 16 round.
Dopo l'ultimo round vengono **swappati 32bit** e poi c'e' la **permutazione inversa** di quella iniziale.
![[Pasted image 20240325132836.png]]
### Initial permutation
![[Pasted image 20240325133921.png]]
Cambio delle posizioni del bit all'inizio dell'algorit
### Inverse initial permutation
![[Drawing 2024-03-25 13.44.15.excalidraw.png]]
### DES single round
![[Drawing 2024-03-25 14.01.07.excalidraw]]


## Crittografia asimmetrica
Sono piu' lenti degli algoritni a chiave simmetrica.
Una chiave viene usata per cifrare e un'altra per decifrare e non è possibile reperire una chiave conoscendo l'altra.

Complessità computazionale degli algoritmi:
easy -> $n^a$ dove n sono il numero di bit in input e a è una costante fissa.
- somma -> lineare
- moltiplicazione -> quadrata
hard -> 2^an 
- esponenziale

trapdor function RSA -> f(x,a,n) => $y=x^a mod (n)$
trapdoor factors of n -> $n = p*q$

trapdor function Diffie-Hellman ->f(g,x,n) => $y=x^a mod (n)$




