# Cisco IOS - Life of a Packet DNS Lookup and ARP Behavior
In this lab, I have built and configured from scratch a simple network in Cisco Packet Tracer to demonstrate how the Domain Name System and Address Resolution Protocol work together across different subnets.

## Network Topology:
<img width="1560" height="563" alt="imagen" src="https://github.com/user-attachments/assets/52bc1270-cf45-417e-8b81-1476ce94dd93" />

The topology above shows a very simple interconnected network that is actually divided into three subnets, without counting the point-to-point link between the routers. 

My goal here is to show how DNS and ARP work together across these networks when Host A wants to send a packet to the web servers's FQDN in the top right, and also how the packet is held and forwarded by the devices until it reaches the server.
This lab is very useful to understand the life of a packet and see how MAC addresses change with every hop, while IP addresses remain the same.

Please find the CLI configuration of each device below:


### Router R1
```
Current configuration : 802 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R1
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX15243954-
!
!
!
!
!
!
!
!
!
!
!
ip name-server 10.10.100.10
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 10.10.10.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 10.10.100.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 ip address 10.10.11.1 255.255.255.252
 duplex auto
 speed auto
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
ip route 10.10.12.0 255.255.255.0 10.10.11.2 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```

### Router R2
```
Current configuration : 761 bytes
!
version 15.1
no service timestamps log datetime msec
no service timestamps debug datetime msec
no service password-encryption
!
hostname R2
!
!
!
!
!
!
!
!
ip cef
no ipv6 cef
!
!
!
!
license udi pid CISCO2911/K9 sn FTX152413YH-
!
!
!
!
!
!
!
!
!
!
!
!
!
spanning-tree mode pvst
!
!
!
!
!
!
interface GigabitEthernet0/0
 ip address 10.10.11.2 255.255.255.252
 duplex auto
 speed auto
!
interface GigabitEthernet0/1
 ip address 10.10.12.1 255.255.255.0
 duplex auto
 speed auto
!
interface GigabitEthernet0/2
 no ip address
 duplex auto
 speed auto
 shutdown
!
interface Vlan1
 no ip address
 shutdown
!
ip classless
ip route 10.10.10.0 255.255.255.0 10.10.11.1 
!
ip flow-export version 9
!
!
!
!
!
!
!
line con 0
!
line aux 0
!
line vty 0 4
 login
!
!
!
end
```

### DNS Server 
<img width="698" height="274" alt="imagen" src="https://github.com/user-attachments/assets/7ebb098e-ef49-4941-a66b-1bb6e8f5e190" />
<img width="692" height="383" alt="imagen" src="https://github.com/user-attachments/assets/e2b0f180-4d53-461e-b9d5-421c1765fe32" />

### Web Server
<img width="705" height="268" alt="imagen" src="https://github.com/user-attachments/assets/8aabb991-45a7-4833-9a72-c855ce7b02b8" />

TCP Ports 80 and 443 for web traffic are listening on the server

<img width="712" height="230" alt="imagen" src="https://github.com/user-attachments/assets/ecb2fdb0-ef99-4170-a91b-c24dd85cc4a6" />

 





