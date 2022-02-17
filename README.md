# Server-Side Request Forgery (SSRF)

## Whar is Server Side Request Forgery (SSRF)?
SSRF stands for the Server Side Request Forgery. SSRF is a server site attack which leads to sensitive information disclosure from the back end server of application. In server site request forgery attacker send malicious packets to any Internet-facing webserver and this webserver sends packet to back end server running on the internal network on behalf of attacker. This vulnerability mostly found in the application those have facility to feed the URL for fetching data from the respective servers , also present in the application in which two or more servers from different hosts communicate with each other for information sharing.
