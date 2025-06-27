Testing Port Connectivity with PowerShell

Objective::
-The goal of this test is to check whether the Telnet (or any service) is accessible and listening on port 23 on the localhost (127.0.0.1 / ::1). This is done using the Test-NetConnection PowerShell command.

Command Used::
Test-NetConnection -ComputerName localhost -Port 23

Meaning of Command:: 
-Test-NetConnection is a built-in PowerShell cmdlet used to test network connectivity.
-The -ComputerName parameter specifies the target system — in this case, localhost, which refers to the same machine the command is run from.
-The -Port parameter specifies the TCP port to check. Here, we are checking port 23, which is traditionally used for the Telnet service.

Explanation Output::
WARNING: TCP connect to (::1 : 23) failed                                  
WARNING: TCP connect to (127.0.0.1 : 23) failed
-These warnings indicate that the system attempted to connect to port 23 on both the IPv6 loopback address (::1) and the IPv4 loopback address (127.0.0.1) but was unsuccessful.

Further output:
ComputerName           : localhost
RemoteAddress          : ::1
RemotePort             : 23
InterfaceAlias         : Loopback Pseudo-Interface 1
SourceAddress          : ::1
PingSucceeded          : True
PingReplyDetails (RTT) : 0 ms
TcpTestSucceeded       : False

 Explaination:
-ComputerName: The host we are testing connectivity to — localhost (our own machine).
-RemoteAddress: The IP address that was resolved from localhost. Here, it’s IPv6 loopback ::1.
-RemotePort: The TCP port tested, which is 23.
-PingSucceeded: True — this means that the machine is reachable via ICMP (ping), so the network stack is functioning.
-TcpTestSucceeded: False — the system could not establish a TCP connection on port 23, meaning no service is currently listening on that port.
