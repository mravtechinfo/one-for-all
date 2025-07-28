```pyodide
import micropip

print("Installing cowsay...")
await micropip.install("cowsay")
print("done!")
```

```pyodide
import cowsay
cowsay.cow("Hello World")
```
```pyodide
from js import XMLHttpRequest, Blob
import json
def request(method,url,data):
    req = XMLHttpRequest.new()
    req.open(method, url, False)
    blob = Blob.new([json.dumps(data)], {type : 'application/json'})
    req.send(blob)
    return req
get = lambda url,data = {}:request("GET",url,data)
post = lambda url,data = {}:request("POST",url,data)


data = {"a": 1}
url= "https://httpbin.org/anything?c=d"
req=get(url,data)
str(req.response)
```



```pyodide
import pyodide
from pyodide.http import pyfetch
print(pyodide)
res = await pyodide.http.pyfetch("https://cdn.jsdelivr.net/pyodide/v0.23.4/full/repodata.json")
data = await res.json()
data
```