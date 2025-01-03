#  <h1 style="color: green;">WHOIS</h1>
--------------------------------

![Web Reconnaissance](https://raw.githubusercontent.com/sbourziq1337/Web-Reconnaissance/refs/heads/main/image_whois.webp)


* **WHOIS** is a widely used query and response protocol designed to access databases that store information about registered internet resources. Primarily associated with domain names, **WHOIS** can also provide details about IP address blocks and autonomous systems. Think of it as a giant phonebook for the internet, letting you look up who owns or is responsible for various online assets.

```shell-session
akerashadow@htb[/htb]$ whois inlanefreight.com

[...]
Domain Name: inlanefreight.com
Registry Domain ID: 2420436757_DOMAIN_COM-VRSN
Registrar WHOIS Server: whois.registrar.amazon
Registrar URL: https://registrar.amazon.com
Updated Date: 2023-07-03T01:11:15Z
Creation Date: 2019-08-05T22:43:09Z
[...]
```

###### Each WHOIS record typically contains the following information:
--------------------------------------------------------

- `Domain Name`: The domain name itself (e.g., example.com)
- `Registrar`: The company where the domain was registered (e.g., GoDaddy, Namecheap)
- `Registrant Contact`: The person or organization that registered the domain.
- `Administrative Contact`: The person responsible for managing the domain.
- `Technical Contact`: The person handling technical issues related to the domain.
- `Creation and Expiration Dates`: When the domain was registered and when it's set to expire.
- `Name Servers`: Servers that translate the domain name into an IP address.

#### Given below are some other Whois Lookup tools.
--------------------------------------------------

1. Whois Lookup ([https://www.whois.com](https://www.whois.com/))
2. ICANN Whois ([https://whois.icann.org](https://whois.icann.org/))
3. MxToolBox ([https://www.whois.com/whois/](https://www.whois.com/whois/))
4. Domain Tools ([https://whois.domaintools.com](https://whois.domaintools.com/))
5. Who.is ([https://who.is/](https://who.is/))
6. https://threatintelligenceplatform.com/
7. https://viewdns.info/
