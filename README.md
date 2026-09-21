# Cisco IOS - Life of a Packet DNS Lookup and ARP Behavior
In this lab, I have built and configured from scratch a simple network in Cisco Packet Tracer to demonstrate how the Domain Name System and Address Resolution Protocol work together across different subnets.

## Network Topology:
<img width="1560" height="563" alt="imagen" src="https://github.com/user-attachments/assets/52bc1270-cf45-417e-8b81-1476ce94dd93" />

The topology above shows a very simple interconnected network that is actually divided into three subnets, without counting the point-to-point link between the routers. 

My goal here is to show how DNS and ARP work together across these networks when Host A wants to send a packet to the web servers's FQDN in the top right, and also how the packet is held and forwarded by the devices until it reaches the server.
This lab is very useful to understand the life of a packet and see how MAC addresses change with every hop, while IP addresses remain the same.

Please find the CLI configuration of each device below. 
