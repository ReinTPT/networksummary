# Networking summary

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
**Packet** - a block of data transmitted across a network complete with a sender and recipient address.
**Network media** -  communication channels used to interconnect nodes on a computer network.(cable - wired, wifi - wireless)
**Port number** - A port number is a way to identify a specific process to which an Internet or other network message is to be forwarded when it arrives at a server. Different services use different port numbers for example some well known common ones are HTTP - 80, SMTP - 25, FTP - 20, HTTPS - 443
**Socket** - A socket is one endpoint of a two-way communication link between two programs running on the network.(IP address + port)


## Commands
**ping** *x.x.x.x* - command to test whether your computer and send and recieve traffic from a specified address. Response comes from operating system.
**printf** - shell command for printing formatted strings. Can be used to form HTTP requests
**nc** - used to manually talk to internet services. example command - *printf "GET / HTTP/1.1\r\nHost: www.example.com\r\n\r\n" | nc www.example.com 80*
**lsof** - lists open files and also network sockets lsof -i
