per invocare l'interprete si usa `#!/urs/bin/env python3` come prima linea
python è dodato di numerose [[Python LIbraries|librerie]]
Tipi:
- numeri
	- integers - non ha limiti
	- floats
	- octal(==0o==177), hex(==0x==9ff), binary(==0b==101010)
	- complessi(3+4j)
- stringhe
	- le stringhe in pyhton sono immutabili perciò se si esegue una operazione su essse ogni volta ne viene creata una nuova.
	- è possibile accedere ai singoli caratteri son la sintassi: `s[n]`
	- hanno dei [[Python Methods#String|metodi per le stringhe]]
- liste
	- si possono concatenare due liste | ex. `l + ["bar"]`
	- è possibile avere liste dentro alle liste e funzionano come una matrice
	- hanno dei [[Python Methods#List|metodi per le liste]]
- dizionari
	- `d = {"key1":"value1"}`, `d.keys()`, `d.()values`
- tuple | ex. `t = (0, "foo")`
	- sequenze inmutabili
	- serve a restituire l'output di una funzione
	- non si puo modificare la lunghezza
	- si puo fare l'unpacking
- 

Operazioni:
- + - addizione
- - - sottrazione
- * moltiplicazione
- ... 

Indexing:
`s[-1]` - ultimo carattere
`s[1:n]` - slice, prende elemento 1 fino a n-1
`s[n:]` - tutto dopo n
`s[:n]` - tutto prima di n-1

Assegnazioni:
`var1, var2 = value1, value2`
`[var1, var2] = [val1,val2]`
`a,b,c = "foo"`
`a, *b = "foobar"`

operatori:
is - guarda se una cosa corrisponde ad un altra

costrutti:
`for <target> in <object>` corrisponderebbe a un for each
si puo anche usare un range:
`range(n)` - da 0 a n-1
`range(m, n)` - da m a n-1
`range(m,n,s)` - da m a n-1 con uno step s

Compressione Liste:
```python
L1 = [1,2,3,4,5]
L2 = [x*2 for x in L1]
l2 -> [2,4,6,8,10]
```
