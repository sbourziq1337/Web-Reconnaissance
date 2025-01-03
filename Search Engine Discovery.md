### **Social Engineering Reconnaissance**

---

![](https://github.com/sbourziq1337/Web-Reconnaissance/blob/main/f94dadbbcf2c644230d6eb310e159ed5.png)

Social engineering reconnaissance focuses on gathering information by manipulating people or exploiting human psychology. Unlike technical methods, this approach targets individuals within an organization rather than systems or networks, extracting sensitive information through human interaction.

Common techniques include:

- **Phishing emails**
- **Pretexting (fake phone calls)**
- **Impersonating trusted personnel**

These methods aim to coax employees into revealing details such as:

- Internal processes
- Key personnel names
- Access credentials
- Weaknesses in training or security policies

Social engineering can often be more successful than technical reconnaissance, especially when technical vulnerabilities are difficult to find. By leveraging deception and psychological manipulation, attackers can bypass even the most robust technical defenses.

---
### **Advanced Search Techniques**
--------------------------------------------

Effective use of search engines is a critical skill for reconnaissance. Below is a table of popular search modifiers that work with many search engines:

|Operator|Operator Description|Example|Example Description|
|:--|:--|:--|:--|
|`site:`|Limits results to a specific website or domain.|`site:example.com`|Find all publicly accessible pages on example.com.|
|`inurl:`|Finds pages with a specific term in the URL.|`inurl:login`|Search for login pages on any website.|
|`filetype:`|Searches for files of a particular type.|`filetype:pdf`|Find downloadable PDF documents.|
|`intitle:`|Finds pages with a specific term in the title.|`intitle:"confidential report"`|Look for documents titled "confidential report" or similar variations.|
|`intext:` or `inbody:`|Searches for a term within the body text of pages.|`intext:"password reset"`|Identify webpages containing the term “password reset”.|
|`cache:`|Displays the cached version of a webpage (if available).|`cache:example.com`|View the cached version of example.com to see its previous content.|
|`link:`|Finds pages that link to a specific webpage.|`link:example.com`|Identify websites linking to example.com.|
|`related:`|Finds websites related to a specific webpage.|`related:example.com`|Discover websites similar to example.com.|
|`info:`|Provides a summary of information about a webpage.|`info:example.com`|Get basic details about example.com, such as its title and description.|
|`define:`|Provides definitions of a word or phrase.|`define:phishing`|Get a definition of "phishing" from various sources.|
|`numrange:`|Searches for numbers within a specific range.|`site:example.com numrange:1000-2000`|Find pages on example.com containing numbers between 1000 and 2000.|
|`allintext:`|Finds pages containing all specified words in the body text.|`allintext:admin password reset`|Search for pages containing both "admin" and "password reset" in the body text.|
|`allinurl:`|Finds pages containing all specified words in the URL.|`allinurl:admin panel`|Look for pages with "admin" and "panel" in the URL.|
|`allintitle:`|Finds pages containing all specified words in the title.|`allintitle:confidential report 2023`|Search for pages with "confidential," "report," and "2023" in the title.|
|`AND`|Narrows results by requiring all terms to be present.|`site:example.com AND (inurl:admin OR inurl:login)`|Find admin or login pages specifically on example.com.|
|`OR`|Broadens results by including pages with any of the terms.|`"linux" OR "ubuntu" OR "debian"`|Search for webpages mentioning Linux, Ubuntu, or Debian.|
|`NOT`|Excludes results containing the specified term.|`site:bank.com NOT inurl:login`|Find pages on bank.com excluding login pages.|
|`*` (wildcard)|Represents any character or word.|`site:socialnetwork.com filetype:pdf user* manual`|Search for user manuals (user guide, user handbook) in PDF format on socialnetwork.com.|
|`..` (range search)|Finds results within a specified numerical range.|`site:ecommerce.com "price" 100..500`|Look for products priced between 100 and 500 on an e-commerce website.|
|`" "` (quotation marks)|Searches for exact phrases.|`"information security policy"`|Find documents mentioning the exact phrase "information security policy".|
|`-` (minus sign)|Excludes terms from the search results.|`site:news.com -inurl:sports`|Search for news articles on news.com excluding sports-related content.

Each search engine has its own syntax rules. For more details:

- [Google Advanced Search](https://www.google.com/advanced_search)
- [DuckDuckGo Syntax](https://help.duckduckgo.com/duckduckgo-help-pages/results/syntax/)
- [Bing Advanced Search](https://help.bing.microsoft.com/apex/index/18/en-US/10002)

---

### **Risks of Misindexed Data**

Search engines continuously crawl the web to index pages, sometimes unintentionally exposing sensitive or confidential information. Examples include:

- Internal company documents
- Spreadsheets containing usernames and passwords
- Configuration files revealing service details or vulnerabilities
- Error messages leaking technical information

For example, you can search Google for all PDF files on `bbc.co.uk` using:

`site:bbc.co.uk filetype:pdf`  

![](https://i.imgur.com/xoDtXnA.png)

---

#### For Further Reading:
-------------------------------

- Dive deeper into the world of Google Hacking with [Google Hacking for Beginners – Part 1](https://www.hackercoolmagazine.com/google-hacking-for-beginners/).
- Explore advanced techniques with [Google Dorking for Hackers – Part 2](https://www.hackercoolmagazine.com/google-dorking-for-hackers-part-2/).

### **Social Media**
---------------------------
Social media platforms are rich sources of information for reconnaissance, as users often overshare details about their personal and professional lives. Common platforms to examine include:

- **LinkedIn** (employee names and roles)
- **Twitter** (company updates or technical discussions)
- **Facebook** (personal connections and interests)
- **Instagram** (personal life details or events)

From these platforms, attackers can collect:

- Employee names and positions
- Clues for password recovery or wordlist creation
- Technical details (e.g., certifications hinting at infrastructure)

For instance, a network engineer sharing their recent Juniper certification may indicate the organization uses Juniper networking equipment.

