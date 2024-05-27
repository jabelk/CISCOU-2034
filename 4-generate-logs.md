
**** show commands
show version
show running-config
show interfaces
show ip route
show processes cpu
show processes memory
show logging
show tech-support





**** config


configure terminal
interface Loopback1337
ip address 192.168.1.1 255.255.255.0
no shutdown
exit



logging console
logging buffered 10000
logging trap debugging

hostname ciscou-2034-router

 
ip routing


router ospf 1
network 192.168.1.0 0.0.0.255 area 0
exit

 
crypto key generate rsa modulus 2048
ip ssh version 2
 
ping 192.168.1.2
show processes cpu
show processes memory
show tech-support
show logging


**** output ****

```
# ip ssh version 2
Command Executed Successfully

# crypto key generate rsa modulus 2048
Command Executed Successfully

# ip domain-name ciscou.com
 ip domain-name ciscou.com
          ^
% Invalid input detected at '^' marker.

# ip routing
Command Executed Successfully

#router ospf 1
Command Executed Successfully

#network 192.168.1.0 0.0.0.255 area 0
Command Executed Successfully

# router ospf 1
IP routing not enabled

#network 192.168.1.0 0.0.0.255 area 0
network 192.168.1.0 0.0.0.255 area 0
        ^
% Invalid input detected at '^' marker.

# hostname ciscou-2034-router
Command Executed Successfully

# logging console
Command Executed Successfully

#logging buffered 10000
Command Executed Successfully

#logging trap debugging
Command Executed Successfully

# interface Loopback1337
Command Executed Successfully

#ip address 192.168.1.1 255.255.255.0
Command Executed Successfully

#no shutdown
Command Executed Successfully

# configure terminal
 configure terminal
         ^
% Invalid input detected at '^' marker.

#interface Loopback1337
Command Executed Successfully

#ip address 192.168.1.1 255.255.255.0
Command Executed Successfully

#no shutdown
Command Executed Successfully

# snmp-server community public RO
Command Executed Successfully

#snmp-server community private RW
Command Executed Successfully


```