 
   
   
   9. **Username wordlist** — [https://portswigger.net/web-security/authentication/auth-lab-usernames](https://portswigger.net/web-security/authentication/auth-lab-usernames)
    
10. **Password wordlist** — [https://portswigger.net/web-security/authentication/auth-lab-passwords](https://portswigger.net/web-security/authentication/auth-lab-passwords)
    
11. **XSS Cheatsheet** — [https://portswigger.net/web-security/cross-site-scripting/cheat-sheet](https://portswigger.net/web-security/cross-site-scripting/cheat-sheet)
    
12. **SQLi Cheatsheet** — [https://portswigger.net/web-security/sql-injection/cheat-sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
    
13. **ParamMiner Headers (params)** — [https://github.com/PortSwigger/param-miner/blob/master/resources/params](https://github.com/PortSwigger/param-miner/blob/master/resources/params)
    
14. **Directory Bursting Wordlist** — [https://github.com/PortSwigger/param-miner/blob/master/resources/words](https://github.com/PortSwigger/param-miner/blob/master/resources/words)
    
15. **JWT Weak Keys Wordlist** — [https://github.com/wallarm/jwt-secrets/blob/master/jwt.secrets.list](https://github.com/wallarm/jwt-secrets/blob/master/jwt.secrets.list)
    
16. **Guide & Everything on exam** — [https://bscp.guide/](https://bscp.guide/)  
    **Guide Wordlist** — [https://github.com/botesjuan/Burp-Suite-Certified-Practitioner-Exam-Study/tree/main/wordlists](https://github.com/botesjuan/Burp-Suite-Certified-Practitioner-Exam-Study/tree/main/wordlists)
    

# Burp Extensions

- JWT scanner
    
- Param Miner
    
- JWT Editor
    
- Active scan++
    
- Java Deserialization Scanner
    
- HTTP Request Smuggler
    
- Server-Side Prototype Pollution Scanner
    
- InQL - GraphQL Scanner




Exp-1 8:18 am 

Two test applications
**Application No 1**
Standard burp blog website with **exploit server, my account page and admin panel**
Exploit server has email to client function
Using DOM invader trying for DOM based XSS over all input fields
Trying on GET request that contains **referer header** 
remove all the headers of request (get) only the http method and cookie left still requests response was 200 ok 
Intruding the same modified get request (removed content) through intruder using payload list ________________
__ ?

Checking the exploit server for the POST request of /new_password 

Scanning the same original home page GET request through BURP scanner (active scanning)
Again working on App1
On blog post comment section part 
It also has a refresh_password functn that takes username as input and send the email for refreshing the password 


**Switched to Application 2**
This application contains Admin panel, my account and advanced search tabs and again it is a regular burp suite lab app.
Doing the same actitvity of modifying home page GET request and here only modified the host name and it says in-valid in the response 
similary fuzzed this request using intruder with payload count of (4k approx)
Adding the X-forwarded-host header into the same GET request getting response as 400 bad request 
Checking the exam notes (----out)
Working with the exploit server for app no 2 
Sending alert(1) as payload to the victim of application no 2
Burp suite flagged for Cross domain script  include

~~after seeing the repeater and browser I am also not able to define ki bhai app 1 exploit ho rha h ya app 2 bda confusion h while shadowing for documentation

 Application 2 was detected with SQLi now using SQL Map with req.sqli, account access in application 2 is Carlos
 
Post this logged in as admin and got the API key.
Admin  account has the API key and a feature to import user using file upload (user import xml file)(XML is uploading here) which hints to XXE 
Going to look for XXE injection payloads on PCSB guide repo

Making the exploit payload and using the exploit server to send it to the victim
Now we have done chatgpt inside the same machine from which we are giving the exam......(heart beat skipped !!!!)

making the xml payload to send to the exploit server using the burp request also chnaging the content type:text/xml
Doing active scan on the the same burp request taking the email filed as selected parameter 
""<email>>jsjhjfjh@fjdh <</emai>""


