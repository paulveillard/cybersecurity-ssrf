# Server-Side Request Forgery (SSRF)

## Whar is Server Side Request Forgery (SSRF)?
SSRF stands for the Server Side Request Forgery. SSRF is a server site attack which leads to sensitive information disclosure from the back end server of application. In server site request forgery attacker send malicious packets to any Internet-facing webserver and this webserver sends packet to back end server running on the internal network on behalf of attacker. This vulnerability mostly found in the application those have facility to feed the URL for fetching data from the respective servers , also present in the application in which two or more servers from different hosts communicate with each other for information sharing.

## Types Of SSRF :
### 1. Blind SSRF: 
In a Blind SSRF,  attacker are not able to control the data of  packet B  that are sent to the application in a trusted internal network. Here attacker can control the IP address and ports of server. To exploit this type of SSRF we have to feed URL followed by the colon and port number, by observing responses and error messages from the server we can find the open and close ports of server.We have try this procedure for the different ports to check their status.

> Example :

http://example.com:1337
http://example.com:9923
http://example.com:43
http://example.com:22


### 2. Limited Response / Partial SSRF :
In this type of SSRF we get limited response from the server like title of the page or got access to resources but can’t see the data. We can control only certain parts of packet B that arrive internal application this type of vulnerability can be used to read local system files such as /etc/config, /etc/hosts, etc/passwd and many others. By using file:// protocol we can read file on the system.In some cases  XXE injection ,DDos these type of vulnerability may useful be exploit Partial SSRF Vulnerability.

> Example :

file:///etc/hosts
file:///etc/config
file:///etc/passwd


### 3. Full Response SSRF :
In Full SSRF we have complete control over the Packet B (shown in fig). Now we can access the services running of the internal network and find the vulnerabilities in internal network. In this type of SSRF we can use the protocols like file://, dict://, http://, gopher://, etc. here we have large scope of creating different request and exploit the internal network if any vulnerabilities are present. Full SSRF vulnerability may cause the application crash through buffer overflow, by sending large string in the request causes the buffer overflow.

> Example :

http://192.168.1.8/BBBBBBBBBBBBBBBBBBBBBBBBBBBBBB
BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB


## Potential Blocks During Testing SSRF Vulnerability :

Whitelisting : Server only allows the few domain name to be used in the request , server has a white list of domain if domain name from that list matches with domain name from request then only accept the request otherwise server decline the request.
Blacklisting:-Server discard the all the request containing IP addresses, domain names, keywords from the blacklist of server.
Restricted content:- Server allows to access only particular amount of files to user, it allows only the few file extension types for public access.


## Key Points To Test SSRF Vulnerability :

1. Always make sure that you are making request to back end server on the behalf of public server not from the browser.
2. To fetch the data from server also try http://localhost/xyz/  with the http://127.0.0.1/xyz.
3. Server may have the firewall protection always try to bypass the firewall if possible.
4. Make sure that request is coming from server not from your local host.
