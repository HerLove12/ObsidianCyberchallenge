#### Input and Output #redirection:
- `>` - output overwrite if file already exists
- `>>` - output append
- `<` - output of a process as stdin for another process
- `<<` - ...

#### #Wildcard:

```
? - qualunque carattere singolo
* - qualunque sequenza di caratteri
[...] - determinati caratteri 
```

#### #Concatenatori:
- `;` - executed sequentially regardless of their completion status
- `&&` - the second command is executed only if the first completes successfully 
- `<cmd1>|<cmd2>`- The standard ==output== of cmd1 is connected via a pipe to the standard ==input== of cmd2 

#### #BashExpressions:
- `${IFS}` - (sostitutivo di spazio per bash)
- `$<comando>` - (command sostitution, gets the standard output)
