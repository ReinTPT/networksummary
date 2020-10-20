# Networking summary

## Addresses

IPv4 - xxx.xxx.xxx.xxx - consists of 4 octets seprarated by dots. Each octet is 8 bits. 

## DNS

The Domain Name System (DNS) is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. Example hierarchy: an "A" record for www.example.com  will be found in the "authorative" name server for example.com whose "NS" record is held in the .com name server which is a global top level domain whose "NS" record is held by a root name server. The client looking for an "A" type address will usually first look for it in a caching server and if not found the cache server performs a recursive search fowarding it to the appropriate server : root server -> top level domain server -> lower level domain server, until it gets an awnser. The response is also stored in the cache with a TLL(time to live - time of how long the result is kept in the cache until it is deleted and a new query is issued to make sure the info is fresh.)

## The TCP/IP model layers

### Application

  Sample protocols: HTTP, SSH
  Concepts: URL, passwords
  
### Transport

  Sample protocols: UDP, TCP
  Concepts: port numbers, sessions
  
### Internet

  Sample protocols: IP
  Concepts: IP addresses, routes
  
### Network access

  Sample protocols: ethernet, wifi, DSL
  Concepts: signal strength, access points



## Terms

**Host** - a machine on the internet (computer, server, etc)

**Packet** - a block of data transmitted across a network complete with a sender and recipient address.

**Network media** -  communication channels used to interconnect nodes on a computer network.(cable - wired, wifi - wireless)

**Port number** - A port number is a way to identify a specific process to which an Internet or other network message is to be forwarded when it arrives at a server. Port numbers are represented in binary as 16-bit numbers. Different services use different port numbers for example some well known common ones are HTTP - 80, SMTP - 25, FTP - 20, HTTPS - 443

**Socket** - A socket is one endpoint of a two-way communication link between two programs running on the network.(IP address + port)

**DNS** - Domain Name System, worldwide distributed directory of network information. Used to map ip addresses to domain names. There are many different types of DNS records for example: CNAME - Canonical Name record which maps an alias name to a true domain name example: company.hostname.com (alias) -> hostname.com (true domain) , A - type A address(IPv4) , AAAA - quad-A type address(IPv6)  , NS - NS stands for 'nameserver,' and the nameserver record indicates which DNS server is authoritative for that domain (i.e. which server contains the actual DNS records)

**SSL** - Secure socket layer - encrypts the data sent between the host so the traffic couldn't be read in between.


## Commands

**ping** *x.x.x.x* - command to test whether your computer and send and recieve traffic from a specified address. Response comes from operating system. Modifiers:
[-cX (X as athe number of times it should send the ping message)]

**printf** - shell command for printing formatted strings. Can be used to form HTTP requests

**nc** - netcat, used to manually talk to internet services. example command - *printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80* Modifiers:
[-l X (listen to the port X)]

**lsof** - lists open files Modifiers:
[-i (lists files opened by network connections)]

**host** *hostname* - basic utility command to look up records in DNS. More human readable. Modifiers:
[-t A(lists an A type address(IPv4 address for a host))]

**dig** *hostname* - command to get info from a DNS server that is more technical than the **host** command.

