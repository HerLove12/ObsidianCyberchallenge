
## #Requests:
r diventa un oggetto response di cui si puo sapere: .status_code e .text
ex.
```
import requests
r = requests.get("url")
print(r.text)
```
si possono passare anche parametri:
```
r = requests.get("url", params={'key1':'value1'})
print(r.url)
```
e headers:
