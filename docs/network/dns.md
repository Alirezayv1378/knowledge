# DNS
- It's kind of a distributed data base that stores IPs associated with hostnames, and takes hostname(like `www.example.com`) and returns host IP.
- The reason we use DNS servers is because people prefer the more mnemonic hostnames while routers prefer fixed-length, hierarchically structured IP addresses.
- Th DNS protocol runs over [[tcp_udp|UDP]] and uses port 53.

## DNS services:
1. **Host aliasing:** A host may have two or three names. for example `relay1.west-coast.enter-prise.com` could have `enterprise.com` and `www.enterprise.com` and it's **canonical hostname**(main name.) is `relay1.west-coast.enter-prise.com`. and DNS server can handle these sites.
2. **Mail server aliasing**
3. **Load Distribution**
## Three classes of DNS servers:
1. **Root DNS servers:**
2. **TLD (top-level domain DNS):** Responsible for top-level domains such as `com`, `org`, `edu`, `net`, and all the country top-level domains such as `ir`, `uk`, `fr`.
3. **Authoritative DNS servers:** Every organization with publicly accessible hosts(such as web servers and mail servers) on the Internet must provide publicly accessible DNS records that map the names of those hosts to IP addresses.
4. **Local DNS servers:** Each ISP- such as university, an academic department, a company, or a residential ISP-- has a local DNS server. A host local DNS server is typically "close to" host.
## DNS Queries type
![[dns_query.png]]
## DNS Records 
`(Name, Value Type TTL)`