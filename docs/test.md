
# 🌐 How the Internet Works — From URL to Webpage

This article explains **every small step** that happens when you access the internet — from the moment you type a URL or search query to when the page appears on your screen.

---

## 🖥️ Part 1: Connecting to the Network

When your device connects to Wi-Fi, Ethernet, or mobile data:

- A **DHCP server** assigns:
  - **IP address** to your device (e.g., `192.168.1.10`)
  - **DNS server** (e.g., `8.8.8.8`)
  - **Gateway IP** (e.g., `192.168.1.1`)
  - **Subnet mask** for local routing

This allows your device to communicate on the local network and with the internet.

---

## 🔍 Part 2: You Enter a URL

When you type `https://www.google.com` in your browser:

### DNS Resolution Steps:

1. **Browser cache** is checked.
2. **OS cache** is checked.
3. **Hosts file** is checked.
4. If not found, browser asks the **configured DNS server** (like `8.8.8.8`).

The DNS resolver does:
- Query **root name server** → returns `.com` name server
- Query **TLD (.com) name server** → returns `google.com` name server
- Query **google.com name server** → returns actual IP, e.g. `142.250.183.68`

---

## 🤝 Part 3: Establishing Connection

### TCP 3-Way Handshake

1. Your device → sends `SYN` to Google's server
2. Server → responds `SYN-ACK`
3. Your device → sends back `ACK`

Connection is established over **TCP port 443 (HTTPS)**.

### TLS Handshake (For Secure HTTPS)

- Server sends **TLS certificate**
- Browser verifies certificate
- Both sides perform a **key exchange**
- A **shared encryption key** is derived

All further data is **encrypted** using TLS.

---

## 📤 Part 4: Sending the HTTP Request

Browser sends a secure HTTP request:

```http
GET /search?q=how+internet+works HTTP/1.1
Host: www.google.com
User-Agent: Chrome/114.0
Accept: text/html
```

The request travels:

Your device → Router → ISP → Internet Backbone → Google Data Center

---

## 📥 Part 5: Server Processing

At Google’s side:

- Request hits a **load balancer**
- Routed to the appropriate **application server**
- The server:
  - Queries **databases or caches**
  - Renders the response page (HTML)
- Response is sent back:

```http
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 9283

<html> ... </html>
```

---

## 🖼️ Part 6: Rendering the Page

Browser:
- **Decrypts** the HTML
- Parses it and builds:
  - **DOM Tree** (HTML structure)
  - **CSSOM Tree** (styles)
- Downloads extra assets:
  - CSS files
  - JavaScript files
  - Images
- **Executes JavaScript**
- **Renders** final webpage

---

## ⚡ Part 7: What You See

The search results or webpage is displayed. Every button, image, and link is loaded and styled using:

- **HTML for structure**
- **CSS for design**
- **JavaScript for interactivity**

---

## 📉 Internet Request Flow Diagram (Text Version)

```plaintext
 ┌────────────┐
 │ You (User) │
 └─────┬──────┘
       │
       ▼
  Open Browser & Enter URL
       │
       ▼
   DNS Resolution
       ├── Check Cache
       └── Ask DNS Server → Root → TLD → Authoritative → IP
       │
       ▼
  TCP 3-Way Handshake (SYN → SYN-ACK → ACK)
       │
       ▼
   TLS Handshake & Key Exchange
       │
       ▼
   HTTP Request Sent (GET /index.html)
       │
       ▼
   ISP → Internet Backbone → Server
       │
       ▼
  Web Server (NGINX/Apache etc.)
       └── Load Balancer
             └── App Servers
                   └── Database/API
       ▼
   HTTP Response (200 OK + HTML)
       │
       ▼
   Browser Parses & Renders Page
       ├── More requests (images, CSS, JS)
       └── Runs JS, Renders UI
       ▼
   Web Page Appears on Screen
```

---

## 🔁 Summary

Every time you click a link, search something, or access a page:
- Your device resolves domain names
- Establishes secure connections
- Sends and receives data over the internet
- Browser renders everything live

It all happens in milliseconds!






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