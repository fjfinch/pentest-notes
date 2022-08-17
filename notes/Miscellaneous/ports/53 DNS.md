# DNS
Domain Name System (DNS) is a hierarchical, distributed database that contains mappings of domain names to various types of data, such as IP addresses. These are called records. DNS enables to locate computers and services by user-friendly names, and it also enables the discovery of other information stored in the database. As said DNS in mainly used to resolve the DNS name of a computer to its IP address.

## DNS queries
* Recursive Query: "must" provide an answer. It responds with either a relevant resource record, or an error message if it can't be found. The resolver starts a recursive query process, starting from the DNS Root Server, until it finds the Authoritative Name Server that holds the IP address and other information for the requested hostname.

* Iterative Query: returns the best answer it can give. It refers the DNS client to the Root Server, or another Authoritative Name Server which is nearest to the required DNS zone. The DNS client must then repeat the query directly against the DNS server it was referred to.

* Non-Recursive Query: a query in which the DNS Resolver already knows the answer. A response is immediately returned to the client.

## DNS servers
* DNS Resolver: a recursive resolver, is designed to receive DNS queries, which include a human-readable hostname and is responsible for tracking the IP address for that hostname.

* DNS Root Server: is the first step in the journey from hostname to IP address. The DNS Root Server extracts the TLD nameserver from the user’s query. There are 13 root servers worldwide, indicated by the letters A through M, operated by different organizations and are delegated authority by ICANN (Internet Corporation for Assigned Names and Numbers).

* Top Level Domain (TLD) nameserver: is the next step in the search for a specific IP address, and it hosts the last portion of a hostname (In example.com, the TLD server is “com”). It gives the proper authoritative server back.

* Authoritative DNS Server: Higher level servers in the DNS hierarchy define which DNS server is the “authoritative” name server for a specific hostname, meaning that it holds the up-to-date information for that hostname. The Authoritative Name Server is the last stop in the name server query—it takes the hostname and returns the correct IP address to the DNS Resolver (or if it cannot find the domain, returns the message NXDOMAIN).

![KDC](dns.png)

## DNS records
* A - Maps an IPv4 address to a name
* AAAA - Maps an IPv6 address to a name
* PTR - Maps a name to a IPv4 address (reverse-lookup)
* SRV - Specifies a port/service for specific server
* CNAME - Forwards one domain or subdomain to another domain, does NOT provide an IP address
* MX - Identifies the mail server
* NS - Stores the name server for a DNS entry
* TXT - Lets an admin store text notes in the record
* SOA - Stores admin information about a domain

## DNS zones
DNS has a distributed database which means that information about all the domains, subdomains, and host mappings are not stored on just one DNS server but distributed across multiple servers. The management of the DNS database is made easy by dividing the DNS namespace into multiple zones and assigning the responsibility of a zone to a particular server. A zone contains all the information about a domain except for the parts of the domain delegated to other name servers. The zone files begin with an AD DNS Start of Authority (SOA) resource record that indicates the primary name server for the zone.

DNS enumeration is the act of detecting and enumerating all possible DNS records from a domain name. This includes hostnames, DNS record names, DNS record types, TTLs, IP addresses, etc.