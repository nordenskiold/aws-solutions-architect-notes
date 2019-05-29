## Domain Name System (DNS)

### Overview
DNS is used to convert human friendly domain names (e.g. http://google.com) into an IP address (e.g. http://254.123.54.0). Note that computers do not care about human friendly domain names and simply use the converted IP address for communication.

#### IPv4 vs. IPv6
There are two different kinds of IP addresses, IPv4 and IPv6. IPv4 are "old" 32-bit field IP addresses and IPv6 are "new" 128-bit field IP addresses. Since each IP address *must* be unique, IPv6 was created to address the issue of IPv4 addresses running out. Theoretically, IPv6 adresses should never run out because of the larger 128-bit field space.

#### Top Level Domain (TLD)
Simply refers to the last string of characters seperated by dots of a human friendly domain name (e.g. ".com" in "www.google.com"). A second level domain name sometimes exists as well and is simply the second to last string of characters seperated by dots of a human friendly domain name (e.g. ".gov" in "www.whitehouse.gov.com").

Top level domain names are controlled by the Internet Assigned Numbers Authority (IANA) in a database containing all avilable top level domains.

#### Domain Registrars
Since all names in a given TLD need to be unique, domain registrars exist to ensure that domain names aren't duplicated. A domain registrar is an authority that can assign domain names directly under one or more TLDs. These domains are registered by the registrar with InterNIC, a service of ICANN, which enforces uniqueness of domain names across all registrars. To accomplish this, each domain name becomes registered in a central database known as the WhoIS database.

#### DNS Record Types

**A Record**<br>
This record stands for address record and is the most fundamental type of record. This record points a domain to an IP address. 

**CNAME Record**<br>
This record stands for canonical name record, and is used for redirecting one domain to another. For instance a CNAME record will be in place to redirect traffic from "http://m.google.com" to "http://**mobile**.google.com". Note that CNAME records should not be used to map the root domain to multiple domains (e.g. "http://google.com" shouldn't have multiple redirects). CNAME records can also not be used for root domains (zone apex records) for instance "http://google.com".

**ALIAS Record**<br>
An Alias record is a virtual record type that provides CNAME-like behavior. It is very similar to the CNAME record with the exception that it can coexist with other records on that name. So if we needed to map "http://m.google.com" to another domain, we would use an ALIAS. ALIAS can also be used for mapping root domains such as "http://google.com"

**MX Entry**<br>
This record stands for mail exchanger record and defines how email should be routed when sent to an address on a domain.

**AAAA Record**<br>
This record is similar to an A record, but is used to point a domain to an IPv6 address instead of an IPv4. 

**PTR Record**<br>
A pointer record (PTR) resolves an IP address to a fully-qualified domain name. This is the opposite of what an A record does.

**NS Record**<br>
A name server (NS) record delegates a subdomain to a set of name servers. NS are used by TLD servers to direct traffic to the Content DNS server which contains the authoritative DNS records. An example of a NS Record looks like:

`example.com. 184200 IN NS ns.awsdns.com`

**SOA Record**<br>
Every DNS address begins with a Start of Authority Record (SOA). The SOA stores information about the name of the server that supplied the data for the zone, who the administrator for the zone is, the current version of the data file, and the default number of seconds for the time-to-live (TTL) file on resource records.

#### Time-To-Live (TTL)
Time-to-live is a common term which refers to how long an item should be cached for in seconds. In respect to DNS records, this refers to how fast changes in DNS records take to propagate throughout the internet. Most DNS records have a TTL of 48 hours by default.

#### Example DNS resolution
Let's take an example of navigating to http://google.com and how this name gets resolved.

1. **Query to the TLD** ".com" is made to fetch   the authoritative DNS records. The TLD does not contain the IP-address but will return the NS.
2. **Query to the NS** is made to fetch the SOA
3. **Query to the SOA** is made to fetch the DNS records


### Key Take Aways
- Amazon Elastic Load Balancers do not have pre-defined IPv4 addresses; you resolve ot them using a DNS name
- Understand the difference between an Alias Record and a CNAME
- In exam scenarios, always choose an Alias Record over a CNAME