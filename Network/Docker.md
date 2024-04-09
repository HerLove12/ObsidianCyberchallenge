Docker utilizza dei **container** ovvero dei contenitori o sandbox che contengono un processo isolato.

serve a:
- limitare l'accesso alle risorse
- limitare accesso all'hardware
- usare una sottorete separata
- evitare conflitti di dipendenze o comportamenti inaspettati
- ...


Funziona grazie a due strumenti del kernel linux:
- namespaces
- cgroups
sono due componenti che permettono di isolare un processo

Docker è una runtime che permette un utilizzo facile da linea di comando dei moduli del kernel elencati precedentemente(basato su runC)

### Immagini
Funziona tramite delle **immagini** che contengono tutte le dipendenze e gli archivi necessari
le immagini hanno questo formato -> `[registry/][user/]name[:tag]`
le immagini sono fatte a layer e sono template immutabili, ogni volta che viene riavviato riparte dallo stato base.

I registry sono come delle repo di github

