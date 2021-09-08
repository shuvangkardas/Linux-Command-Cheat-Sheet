# netstat

`netstat` is used to list out all the network(socket) connections of a system. 

**Flags**

- `-a` list all connection
- `-n` disable DNS lookup
- `-t` list only tcp connection
- `-u` listen only UDP connection
- `-l` to view only listening port
- `-p` process details of the connection. Root  privilege is needed for this option
- `-s` print total packet received and transmitted  by protocols
- `-i` interface name
- `-ie` to print human friendly version of the interface

### Example of `netstat` commands

- `netstat -a` List all the connection
- `netstat -at` List only tcp connection
- `netstat -au` List only UDP connection
- `netstat -an` List all connection. `-n` option disable DNS name lookup. So it provide faster output.
- `netstat -an | grep ESTABLISHED` find only established connection
- `netstst -aple | grep ntp` to check any running program like ntp, smtp, http etc.

### Understand  `netstat` output

The netstat output provides four basic columns. Proto, Local Address, Foreign address and State

**Proto**

The name of the protocol (TCP or UDP)

**Local Address**

- `0.0.0.0:566` means the port`(566)` is listening on all network interfaces
- `127.0.0.1` port is only listening for connections from PC itself. PC regularly does connect itself for IPC or administrative task.
- `Public IP(226.178.2.3:4567)` It means the port is only listening for connection from internet
- `Local IP(192.168.0.1)`. Port is only listening for connection from local network

**Foreign Address**

The IP address and port number of the remote computer. 

**State**

- `LISTENING` The port is open and listening for inbound connection
- `ESTABLISHED` The connection is active between the two machines
- `TIMED_WAIT` The connection has recently ended
- `SYN_SEND, SYN_RECEIVED` Appear during initial connection setup
- `FIN_WAIT, CLOSE_WAIT, LAST_ACK` Appear while a connection is being closed

**Wildcards**

Asterisk(`*`) as a wildcard means any

- If the port is yet not established, the port number is shown as asterisk( `*` )
- `*:*` The connection can come from any IP address and originate from any port
- `*.*` All IPv4 addresses
- `[::]` All IPv6 addresses