## <h1 style="color: Orange;">The Domain Information Groper</h1>
-----------------------------------------

* The `dig` command (`Domain Information Groper`) is a versatile and powerful utility for querying DNS servers and retrieving various types of DNS records. Its flexibility and detailed and customizable output make it a go-to choice.
#### Common dig Commands

| Command                         | Description                                                                                                                                                                                          |
| ------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `dig domain.com`                | Performs a default A record lookup for the domain.                                                                                                                                                   |
| `dig domain.com A`              | Retrieves the IPv4 address (A record) associated with the domain.                                                                                                                                    |
| `dig domain.com AAAA`           | Retrieves the IPv6 address (AAAA record) associated with the domain.                                                                                                                                 |
| `dig domain.com MX`             | Finds the mail servers (MX records) responsible for the domain.                                                                                                                                      |
| `dig domain.com NS`             | Identifies the authoritative name servers for the domain.                                                                                                                                            |
| `dig domain.com TXT`            | Retrieves any TXT records associated with the domain.                                                                                                                                                |
| `dig domain.com CNAME`          | Retrieves the canonical name (CNAME) record for the domain.                                                                                                                                          |
| `dig domain.com SOA`            | Retrieves the start of authority (SOA) record for the domain.                                                                                                                                        |
| `dig @1.1.1.1 domain.com`       | Specifies a specific name server to query; in this case 1.1.1.1                                                                                                                                      |
| `dig +trace domain.com`         | Shows the full path of DNS resolution.                                                                                                                                                               |
| `dig -x 192.168.1.1`            | Performs a reverse lookup on the IP address 192.168.1.1 to find the associated host name. You may need to specify a name server.                                                                     |
| `dig +short domain.com`         | Provides a short, concise answer to the query.                                                                                                                                                       |
| `dig +noall +answer domain.com` | Displays only the answer section of the query output.                                                                                                                                                |
| `dig domain.com ANY`            | Retrieves all available DNS records for the domain (Note: Many DNS servers ignore `ANY` queries to reduce load and prevent abuse, as per [RFC 8482](https://datatracker.ietf.org/doc/html/rfc8482)). |
#### **For exmple**;

[![DNS Footprinting 78](https://www.hackercoolmagazine.com/wp-content/uploads/2023/07/DNS_Footprinting_78.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/07/DNS_Footprinting_78.jpg)
This tool can also be used to query for a specific type of records as shown below.

[![DNS Footprinting 9](https://www.hackercoolmagazine.com/wp-content/uploads/2023/07/DNS_Footprinting_9.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/07/DNS_Footprinting_9.jpg)
[![DNS Footprinting 1011](https://www.hackercoolmagazine.com/wp-content/uploads/2023/07/DNS_Footprinting_1011.jpg)](https://www.hackercoolmagazine.com/wp-content/uploads/2023/07/DNS_Footprinting_1011.jpg)
* Caution: Some servers can detect and block excessive DNS queries. Use caution and respect rate limits. Always obtain permission before performing extensive DNS reconnaissance on a target.

#### Exploiting Zone Transfers
------------------------------------

You can use the `dig` command to request a zone transfer:

  * DNS Zone Transfers

```shell-session
akerashadow@htb[/htb]$ dig axfr @nsztm1.digi.ninja zonetransfer.me
```

* This command instructs `dig` to request a full zone transfer (`axfr`) from the DNS server responsible for `zonetransfer.me`. If the server is misconfigured and allows the transfer, you'll receive a complete list of DNS records for the domain, including all subdomains.

  * DNS Zone Transfers

```shell-session
akerashadow@htb[/htb]$ dig axfr @nsztm1.digi.ninja zonetransfer.me

; <<>> DiG 9.18.12-1~bpo11+1-Debian <<>> axfr @nsztm1.digi.ninja zonetransfer.me
; (1 server found)
;; global options: +cmd
zonetransfer.me.	7200	IN	SOA	nsztm1.digi.ninja. robin.digi.ninja. 2019100801 172800 900 1209600 3600
zonetransfer.me.	300	IN	HINFO	"Casio fx-700G" "Windows XP"
zonetransfer.me.	301	IN	TXT	"google-site-verification=tyP28J7JAUHA9fw2sHXMgcCC0I6XBmmoVi04VlMewxA"
zonetransfer.me.	7200	IN	MX	0 ASPMX.L.GOOGLE.COM.
...
zonetransfer.me.	7200	IN	A	5.196.105.14
zonetransfer.me.	7200	IN	NS	nsztm1.digi.ninja.
zonetransfer.me.	7200	IN	NS	nsztm2.digi.ninja.
_acme-challenge.zonetransfer.me. 301 IN	TXT	"6Oa05hbUJ9xSsvYy7pApQvwCUSSGgxvrbdizjePEsZI"
_sip._tcp.zonetransfer.me. 14000 IN	SRV	0 0 5060 www.zonetransfer.me.
14.105.196.5.IN-ADDR.ARPA.zonetransfer.me. 7200	IN PTR www.zonetransfer.me.
asfdbauthdns.zonetransfer.me. 7900 IN	AFSDB	1 asfdbbox.zonetransfer.me.
asfdbbox.zonetransfer.me. 7200	IN	A	127.0.0.1
asfdbvolume.zonetransfer.me. 7800 IN	AFSDB	1 asfdbbox.zonetransfer.me.
canberra-office.zonetransfer.me. 7200 IN A	202.14.81.230
...
;; Query time: 10 msec
;; SERVER: 81.4.108.41#53(nsztm1.digi.ninja) (TCP)
;; WHEN: Mon May 27 18:31:35 BST 2024
;; XFR size: 50 records (messages 1, bytes 2085)
```
#  <h2 style="color: Orange;">nslookup</h2>
------------------
* The **`nslookup`** command can be used in two modes: **interactive** and **non-interactive**. To initiate the **`nslookup`** interactive mode, type the command name only:

```
nslookup
```

* The prompt that appears lets you issue multiple server queries.

![Entering the interactive mode.](https://phoenixnap.com/kb/wp-content/uploads/2022/01/output-from-nslookup-interactive-mode.png)

* For example, you can type a domain name and receive information about it.

```
www.google.com
```

* After **`nslookup`** outputs the information, it provides another prompt.

![Querying in the interactive mode.](https://phoenixnap.com/kb/wp-content/uploads/2022/01/output-from-nslookup-interactive-www-google-com.png)

* In interactive mode, specify an option in a separate line before the query. Precede the option with **`set`**:

```
set [option]
```

![Setting options in the interactive mode.](https://phoenixnap.com/kb/wp-content/uploads/2022/01/output-from-nslookup-interactive-mode-set-type.png)

* To exit interactive mode, type:

```
exit
```

* The non-interactive mode lets you use **`nslookup`** to issue single queries. The syntax for the non-interactive mode is:

```
nslookup [options] [domain-name]
```

* The command and the query are written in the same line.

![Viewing basic information about a domain in non-interactive mode.](https://phoenixnap.com/kb/wp-content/uploads/2022/01/output-from-nslookup-www-google-com.png)

### nslookup Options
--------------------------------
Find all the important **`nslookup`** options in the following table.

| nslookup Option             | Description                                                                 |
| --------------------------- | --------------------------------------------------------------------------- |
| **`-domain=[domain-name]`** | Change the default DNS name.                                                |
| **`-debug`**                | Show debugging information.                                                 |
| **`-port=[port-number]`**   | Specify the port for queries. The default port number is 53.                |
| **`-timeout=[seconds]`**    | Specify the time allowed for the server to respond.                         |
| **`-type=a`**               | View information about the DNS A address records.                           |
| **`-type=any`**             | View all available records.                                                 |
| **`-type=hinfo`**           | View hardware-related information about the host.                           |
| **`-type=mx`**              | View Mail Exchange server information.                                      |
| **`-type=ns`**              | View Name Server records.                                                   |
| **`-type=ptr`**             | View Pointer records. Used in reverse DNS lookups.                          |
| **`-type=soa`**             | View [Start of Authority](https://phoenixnap.com/glossary/dns-soa) records. |
|                             |                                                                             |
### For exmple:

![Viewing name server information.](https://phoenixnap.com/kb/wp-content/uploads/2022/01/output-from-nslookup-type-ns-google-com.png)

* Check a domain's MX data by typing:

```
nslookup -type=mx [domain-name]
```

* The output shows the names of mail servers.

![Viewing Mail Exchange server information.](https://phoenixnap.com/kb/wp-content/uploads/2022/01/output-from-nslookup-type-mx-yahoo-com.png)
# <h3 style="color: Orange;">DNSEnum</h3>
----------------------
### *What is DnsNum*

* **`dnsenum`** is a versatile and widely-used command-line tool written in Perl. It is a comprehensive toolkit for DNS reconnaissance, providing various functionalities to gather information about a target domain's DNS infrastructure and potential subdomains. The tool offers several key functions:
### *How DnsNum Work?*

* Let's see `dnsenum` in action by demonstrating how to enumerate subdomains for our target, `inlanefreight.com`. In this demonstration, we'll use the `subdomains-top1million-5000.txt` wordlist from [SecLists](https://github.com/danielmiessler/SecLists), which contains the top 5000 most common subdomains.

```bash
dnsenum --enum inlanefreight.com -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -r
```

In this command:

- `dnsenum --enum inlanefreight.com`: We specify the target domain we want to enumerate, along with a shortcut for some tuning options `--enum`.

- `-f /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt`: We indicate the path to the SecLists wordlist we'll use for brute-forcing. Adjust the path if your SecLists installation is different.
-
- `-r`: This option enables recursive subdomain brute-forcing, meaning that if `dnsenum` finds a subdomain, it will then try to enumerate subdomains of that subdomain.

  **Subdomain Bruteforcing**
-----------------------------

```shell-session
akerashadow@htb[/htb]$ dnsenum --enum inlanefreight.com -f  /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt 

dnsenum VERSION:1.2.6

-----   inlanefreight.com   -----


Host's addresses:
__________________

inlanefreight.com.                       300      IN    A        134.209.24.248

[...]

Brute forcing with /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt:
_______________________________________________________________________________________

www.inlanefreight.com.                   300      IN    A        134.209.24.248
support.inlanefreight.com.               300      IN    A        134.209.24.248
[...]


done.
```

**To avoid such a time-consuming search, one can use an online service that offers detailed answers to DNS queries, such as [DNSDumpster](https://dnsdumpster.com/).**

* if we search DNSDumpster for `exmple.com`, we will discover the subdomain `mail.exmple.com`, which a typical DNS query cannot provide. In addition, DNSDumpster will return the collected DNS information in easy-to-read tables and a graph. DNSDumpster will also provide any collected information about listening servers.

We will search for `exmple.com` on DNSDumpster to give you a glimpse of the expected output

![Tux, the Linux mascot](https://github.com/sbourziq1337/Web-Reconnaissance/blob/main/Pasted%20image%2020241231064519.png)

* DNSDumpster will also represent the collected information graphically. DNSDumpster displayed the data from the table earlier as a graph. You can see the DNS and MX branching to their respective servers and also showing the IP addresses.

[[Pasted image 20241231065429.png]()
## <h3 style="color: Orange">Virtual Host Discovery Tools</h3>
---------------------------------------------
* While manual analysis of `HTTP headers` and reverse `DNS lookups` can be effective, specialised `virtual host discovery tools` automate and streamline the process, making it more efficient and comprehensive. These tools employ various techniques to probe the target server and uncover potential `virtual hosts`.

* Several tools are available to aid in the discovery of virtual hosts:

|Tool|Description|Features|
|---|---|---|
|[gobuster](https://github.com/OJ/gobuster)|A multi-purpose tool often used for directory/file brute-forcing, but also effective for virtual host discovery.|Fast, supports multiple HTTP methods, can use custom wordlists.|
|[Feroxbuster](https://github.com/epi052/feroxbuster)|Similar to Gobuster, but with a Rust-based implementation, known for its speed and flexibility.|Supports recursion, wildcard discovery, and various filters.|
|[ffuf](https://github.com/ffuf/ffuf)|Another fast web fuzzer that can be used for virtual host discovery by fuzzing the `Host` header.|Customizable wordlist input and filtering options.|
## <h3 style="color: Orange;">DNS Tools</h3>
--------------
**Gobuster** is a versatile tool commonly used for directory and file brute-forcing, but it also excels at virtual host discovery. It systematically sends HTTP requests with different `Host` headers to a target IP address and then analyses the responses to identify valid virtual hosts.

There are a couple of things you need to prepare to brute force `Host` headers:

1. `Target Identification`: First, identify the target web server's IP address. This can be done through DNS lookups or other reconnaissance techniques.
2. `Wordlist Preparation`: Prepare a wordlist containing potential virtual host names. You can use a pre-compiled wordlist, such as SecLists, or create a custom one based on your target's industry, naming conventions, or other relevant information.

The `gobuster` command to bruteforce vhosts generally looks like this:

  Virtual Hosts

```shell-session
akerashadow@htb[/htb]$ gobuster vhost -u http://<target_IP_address> -w <wordlist_file> --append-domain
```

- The `-u` flag specifies the target URL (replace `<target_IP_address>` with the actual IP).
- The `-w` flag specifies the wordlist file (replace `<wordlist_file>` with the path to your wordlist).
- The `--append-domain` flag appends the base domain to each word in the wordlist.

*In newer versions of Gobuster, the --append-domain flag is required to append the base domain to each word in the wordlist when performing virtual host discovery. This flag ensures that Gobuster correctly constructs the full virtual hostnames, which is essential for the accurate enumeration of potential subdomains. In older versions of Gobuster, this functionality was handled differently, and the --append-domain flag was not necessary. Users of older versions might not find this flag available or needed, as the tool appended the base domain by default or employed a different mechanism for virtual host generation.

`Gobuster` will output potential virtual hosts as it discovers them. Analyse the results carefully, noting any unusual or interesting findings. Further investigation might be needed to confirm the existence and functionality of the discovered virtual hosts.

There are a couple of other arguments that are worth knowing:

- Consider using the `-t` flag to increase the number of threads for faster scanning.
- The `-k` flag can ignore SSL/TLS certificate errors.
- You can use the `-o` flag to save the output to a file for later analysis.

__First you need to edit hosts file on your machine  
sudo nano /etc/hosts__

[![image](https://europe1.discourse-cdn.com/hackthebox/optimized/3X/7/2/7271216b7c67499c4370b4e57404a962b3a878fd_2_690x464.jpeg)

```shell-session
akerashadow@htb[/htb]$ gobuster vhost -u http://inlanefreight.htb:81 -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt --append-domain
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:             http://inlanefreight.htb:81
[+] Method:          GET
[+] Threads:         10
[+] Wordlist:        /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt
[+] User Agent:      gobuster/3.6
[+] Timeout:         10s
[+] Append Domain:   true
===============================================================
Starting gobuster in VHOST enumeration mode
===============================================================
Found: forum.inlanefreight.htb:81 Status: 200 [Size: 100]
[...]
Progress: 114441 / 114442 (100.00%)
===============================================================
Finished
===============================================================
```

### Conclusion
----------------------------
* Mastering DNS tools and techniques is essential for network reconnaissance and domain management. Tools like `dig`, `nslookup`, and `dnsenum` can provide a wealth of information about a domain's DNS setup, while virtual host discovery tools like Gobuster automate the search for hidden resources. Use these tools wisely, and always respect privacy and rate limits during reconnaissance.
