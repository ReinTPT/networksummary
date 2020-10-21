# Networking summary

## Addresses

Public address - It is public global addresses that are used in the Internet. A public IP address is an IP address that is used to access the Internet.

Private address - Private internal addresses are not routed on the Internet and no traffic cannot be sent to them from the Internet, they only supposed to work within the local network.Private addresses include IP addresses from the following subnets:

    *Range from 10.0.0.0 to 10.255.255.255 — a 10.0.0.0 network with a 255.0.0.0 or an /8 (8-bit) mask
    *Range from 172.16.0.0 to 172.31.255.255 — a 172.16.0.0 network with a 255.240.0.0 (or a 12-bit) mask
    *A 192.168.0.0 to 192.168.255.255 range, which is a 192.168.0.0 network masked by 255.255.0.0 or /16

IPv4 - xxx.xxx.xxx.xxx - consists of 4 octets seprarated by dots. Each octet is 8 bits. The address is composed of the network part and the host part.
Special addresses - addresses that can't be assigned to hosts. Some of them are used for special applications that use addresses differently. Some of them are reserved for internal private networks. Some of them are for testing or documentation. Example: 224-239 block is used for multicast transmissions.

IPv6 - An IPv6 address is represented as eight groups of four hexadecimal digits, each group representing 16 bits (two octets, a group sometimes also called a hextet). The groups are separated by colons (:). An example of an IPv6 address is: 2001:0db8:85a3:0000:0000:8a2e:0370:7334.

Subnet mask -The subnet mask is used by the TCP/IP protocol to determine whether a host is on the local subnet or on a remote network.

Network interface - A network interface is the point of interconnection between a computer and a private or public network. A network interface is generally a network interface card (NIC), but does not have to have a physical form. Instead, the network interface can be implemented in software. For example, the loopback interface (127.0.0.1 for IPv4 and ::1 for IPv6) is not a physical device but a piece of software simulating a network interface.

Router - a device to connect different IP networks, also known as a default gateway.

NAT - Network Address Translation is designed for IP address conservation. It enables private IP networks that use unregistered IP addresses to connect to the Internet.

## DNS

The Domain Name System (DNS) is a hierarchical and decentralized naming system for computers, services, or other resources connected to the Internet or a private network. Example hierarchy: an "A" record for www.example.com  will be found in the "authorative" name server for example.com whose "NS" record is held in the .com name server which is a global top level domain whose "NS" record is held by a root name server. The client looking for an "A" type address will usually first look for it in a caching server and if not found the cache server performs a recursive search fowarding it to the appropriate server : root server -> top level domain server -> lower level domain server, until it gets an awnser. The response is also stored in the cache with a TLL(time to live - time of how long the result is kept in the cache until it is deleted and a new query is issued to make sure the info is fresh.)

## The TCP/IP model layers

UDP - The User Datagram Protocol, or UDP, is a communication protocol used across the Internet for especially time-sensitive transmissions such as video playback or DNS lookups. It speeds up communications by not formally establishing a connection before data is transferred. This allows data to be transferred very quickly, but it can also cause packets to become lost in transit.

TCP - TCP is a connection-oriented protocol, which means a connection is established and maintained until the application programs at each end have finished exchanging messages. TCP is used for organizing data in a way that ensures the secure transmission between the server and client. It guarantees the integrity of data sent over the network, regardless of the amount. For this reason, it is used to transmit data from other higher-level protocols that require all transmitted data to arrive

The original TCP packet format has six flags. Two more optional flags have since been standardized, but they are much less important to the basic functioning of TCP. For each packet, tcpdump will show you which flags are set on that packet.

    SYN (synchronize) [S] — This packet is opening a new TCP session and contains a new initial sequence number.
    FIN (finish) [F] — This packet is used to close a TCP session normally. The sender is saying that they are finished sending, but they can still receive data from the other endpoint.
    PSH (push) [P] — This packet is the end of a chunk of application data, such as an HTTP request.
    RST (reset) [R] — This packet is a TCP error message; the sender has a problem and wants to reset (abandon) the session.
    ACK (acknowledge) [.] — This packet acknowledges that its sender has received data from the other endpoint. Almost every packet except the first SYN will have the ACK flag set.
    URG (urgent) [U] — This packet contains data that needs to be delivered to the application out-of-order. Not used in HTTP or most other current applications.

### Three-way handshake

The first packet sent to initiate a TCP session always has the SYN flag set. This initial SYN packet is what a client sends to a server to start opening a TCP connection. This is the first packet you see in the sample tcpdump data, with Flags [S]. This packet also contains a new, randomized sequence number (seq in tcpdump output).

If the server accepts the connection, it sends a packet back that has the SYN and ACK flags, and acknowledges the initial SYN. This is the second packet in the sample data, with Flags [S.]. This contains a different initial sequence number.

(If the server doesn't want to accept the connection, it may not send anything at all. Or it may send a packet with the RST flag.)

Finally, the client acknowledges receiving the SYN|ACK packet by sending an ACK packet of its own.

This exchange of three packets is usually called the TCP three-way handshake. In addition to sequence numbers, the two endpoints also exchange other information used to set up the connection.



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



## Some Terms

**Host** - a machine on the internet (computer, server, etc)

**Packet** - a block of data transmitted across a network complete with a sender and recipient address.

**Network media** -  communication channels used to interconnect nodes on a computer network.(cable - wired, wifi - wireless)

**Port number** - A port number is a way to identify a specific process to which an Internet or other network message is to be forwarded when it arrives at a server. Port numbers are represented in binary as 16-bit numbers. Different services use different port numbers for example some well known common ones are HTTP - 80, SMTP - 25, FTP - 20, HTTPS - 443

**Socket** - A socket is one endpoint of a two-way communication link between two programs running on the network.(IP address + port)

**DNS** - Domain Name System, worldwide distributed directory of network information. Used to map ip addresses to domain names. There are many different types of DNS records for example: CNAME - Canonical Name record which maps an alias name to a true domain name example: company.hostname.com (alias) -> hostname.com (true domain) , A - type A address(IPv4) , AAAA - quad-A type address(IPv6)  , NS - NS stands for 'nameserver,' and the nameserver record indicates which DNS server is authoritative for that domain (i.e. which server contains the actual DNS records)

**SSL** - Secure socket layer - encrypts the data sent between the host so the traffic couldn't be read in between.

**Congestion** - Congestion occurs when the number of packets being transmitted through the network approaches the packet handling capacity of the network. TCP protocol has congestion control built into it(will transmit faster if possible or slower when too much traffic on the network).


## Commands
**ip** - The ip command is a Linux net-tool for system and network administrators. IP stands for Internet Protocol and as the name suggests, the tool is used for configuring network interfaces. Example: ip addr show - shows network interfaces

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

**tcpdump** - Tcpdump is a command line utility that allows you to capture and analyze network traffic going through your system. It is often used to help troubleshoot network issues, as well as a security tool. example command: sudo tcpdump -n port 80

**traceroute** *hostname* - used to see identify the route a package takes connecting to a server/host.
