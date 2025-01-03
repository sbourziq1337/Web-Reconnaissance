# Web Reconnaissance
-------------------------------
The tasks of this room cover the following topics:

- Types of reconnaissance activities
- WHOIS and DNS-based reconnaissance
- Advanced searching
- Searching by image
- Google Hacking
- Specialized search engines

![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/66c311960c9ad71cbda3709d1c9804e2.png)
### *What is Web Reconnaissance?
----------------------------------------

* Web reconnaissance is the process of gathering information about a website or web application before attempting to exploit vulnerabilities or launch an attack. It involves systematically collecting details about the target system's structure, technologies, and potential weaknesses
* It forms a critical part of the "`Information Gathering`" phase of the Penetration Testing Process.

![](https://academy.hackthebox.com/storage/modules/144/PT-process.png)
## Types of Reconnaissance
-----------------------------
* Web reconnaissance encompasses two fundamental methodologies: `active` and `passive` reconnaissance. Each approach offers distinct advantages and challenges, and understanding their differences is crucial for adequate information gathering.

 <h3 style="color: Orange;">1. Active Reconnaissance</h3>
--------------------------------
![active](https://github.com/sbourziq1337/Web-Reconnaissance/blob/main/cddef8bc0ee2d177a96ea62f680ad28f.png)

* In active reconnaissance, the attacker `directly interacts with the target system` to gather information. This interaction can take various forms:

|Technique|Description|Example|Tools|Risk of Detection|
|---|---|---|---|---|
|`Port Scanning`|Identifying open ports and services running on the target.|Using Nmap to scan a web server for open ports like 80 (HTTP) and 443 (HTTPS).|Nmap, Masscan, Unicornscan|High: Direct interaction with the target can trigger intrusion detection systems (IDS) and firewalls.|
|`Vulnerability Scanning`|Probing the target for known vulnerabilities, such as outdated software or misconfigurations.|Running Nessus against a web application to check for SQL injection flaws or cross-site scripting (XSS) vulnerabilities.|Nessus, OpenVAS, Nikto|High: Vulnerability scanners send exploit payloads that security solutions can detect.|
|`Network Mapping`|Mapping the target's network topology, including connected devices and their relationships.|Using traceroute to determine the path packets take to reach the target server, revealing potential network hops and infrastructure.|Traceroute, Nmap|Medium to High: Excessive or unusual network traffic can raise suspicion.|
|`Banner Grabbing`|Retrieving information from banners displayed by services running on the target.|Connecting to a web server on port 80 and examining the HTTP banner to identify the web server software and version.|Netcat, curl|Low: Banner grabbing typically involves minimal interaction but can still be logged.|
|`OS Fingerprinting`|Identifying the operating system running on the target.|Using Nmap's OS detection capabilities (`-O`) to determine if the target is running Windows, Linux, or another OS.|Nmap, Xprobe2|Low: OS fingerprinting is usually passive, but some advanced techniques can be detected.|
|`Service Enumeration`|Determining the specific versions of services running on open ports.|Using Nmap's service version detection (`-sV`) to determine if a web server is running Apache 2.4.50 or Nginx 1.18.0.|Nmap|Low: Similar to banner grabbing, service enumeration can be logged but is less likely to trigger alerts.|
|`Web Spidering`|Crawling the target website to identify web pages, directories, and files.|Running a web crawler like Burp Suite Spider or OWASP ZAP Spider to map out the structure of a website and discover hidden resources.|Burp Suite Spider, OWASP ZAP Spider, Scrapy (customisable)|Low to Medium: Can be detected if the crawler's behaviour is not carefully configured to mimic legitimate traffic.|

* Active reconnaissance provides a direct and often more comprehensive view of the target's infrastructure and security posture. However, it also carries a higher risk of detection, as the interactions with the target can trigger alerts or raise suspicion.

### <h3 style="color: Orange;">2. Passive Reconnaissance</h3>
-----------------------------------
![](https://tryhackme-images.s3.amazonaws.com/user-uploads/5f04259cf9bf5b57aed2c476/room-content/f8b6de84195f6ce2a517b8985497e80f.png)
* In contrast, passive reconnaissance involves gathering information about the target **`without directly interacting`** with it. This relies on analysing publicly available information and resources, such as:

|Technique|Description|Example|Tools|Risk of Detection|
|---|---|---|---|---|
|`Search Engine Queries`|Utilising search engines to uncover information about the target, including websites, social media profiles, and news articles.|Searching Google for "`[Target Name] employees`" to find employee information or social media profiles.|Google, DuckDuckGo, Bing, and specialised search engines (e.g., Shodan)|Very Low: Search engine queries are normal internet activity and unlikely to trigger alerts.|
|`WHOIS Lookups`|Querying WHOIS databases to retrieve domain registration details.|Performing a WHOIS lookup on a target domain to find the registrant's name, contact information, and name servers.|whois command-line tool, online WHOIS lookup services|Very Low: WHOIS queries are legitimate and do not raise suspicion.|
|`DNS`|Analysing DNS records to identify subdomains, mail servers, and other infrastructure.|Using `dig` to enumerate subdomains of a target domain.|dig, nslookup, host, dnsenum, fierce, dnsrecon|Very Low: DNS queries are essential for internet browsing and are not typically flagged as suspicious.|
|`Web Archive Analysis`|Examining historical snapshots of the target's website to identify changes, vulnerabilities, or hidden information.|Using the Wayback Machine to view past versions of a target website to see how it has changed over time.|Wayback Machine|Very Low: Accessing archived versions of websites is a normal activity.|
|`Social Media Analysis`|Gathering information from social media platforms like LinkedIn, Twitter, or Facebook.|Searching LinkedIn for employees of a target organisation to learn about their roles, responsibilities, and potential social engineering targets.|LinkedIn, Twitter, Facebook, specialised OSINT tools|Very Low: Accessing public social media profiles is not considered intrusive.|
|`Code Repositories`|Analysing publicly accessible code repositories like GitHub for exposed credentials or vulnerabilities.|Searching GitHub for code snippets or repositories related to the target that might contain sensitive information or code vulnerabilities.|GitHub, GitLab|Very Low: Code repositories are meant for public access, and searching them is not suspicious.|

* Passive reconnaissance is generally considered stealthier and less likely to trigger alarms than active reconnaissance. However, it may yield less comprehensive information, as it relies on what's already publicly accessible.

### Techniques of Footprinting
-------------------------------------

![Web Reconnaissance](https://raw.githubusercontent.com/sbourziq1337/Web-Reconnaissance/refs/heads/main/Web%20Reconnaissance.png.webp)
**The various techniques of Reconnaissance include**

* [Whois Footprinting](https://github.com/sbourziq1337/Web-Reconnaissance/blob/main/Whois%20Footprinting.md)
* [DNS Footprinting](https://github.com/sbourziq1337/Web-Reconnaissance/blob/main/DNS%20Footprinting.md)
* [ Search Engine Discovery](https://github.com/sbourziq1337/Web-Reconnaissance/blob/main/Search%20Engine%20Discovery.md)

Web reconnaissance lays the foundation for identifying vulnerabilities and ensuring effective penetration testing. By understanding and applying both active and passive methodologies, you can maximize your information-gathering efforts while minimizing the risk of detection.


