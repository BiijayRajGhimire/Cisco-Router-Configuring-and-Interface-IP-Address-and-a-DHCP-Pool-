# Cisco-Router-Configuring-and-Interface-IP-Address-and-a-DHCP-Pool-
Configuring a LAN interface with a static IP address on a Cisco IOS router and setting up a DHCP pool so that devices on that network automatically receive an IP address, default gateway, and DNS server. 
This guide walks through configuring a LAN interface with a static IP address on a Cisco IOS router, and setting up a DHCP pool so that devices on that network automatically receive an IP address, default gateway, and DNS server. 
Prerequisites 
•	Console, SSH, or Telnet access to the router with an account that has privileged EXEC (enable) access. 
•	The interface name you will configure (e.g., GigabitEthernet0/0, FastEthernet0/1, Vlan1). 
•	The IP address and subnet mask to assign to the router interface (this will be the default gateway for the LAN). 
•	The DHCP address range you want to hand out, plus DNS server and domain information (optional). 
1: Enter Global Configuration Mode 
From privileged EXEC mode, enter global configuration mode
Router> enable
Router# configure terminal
<img width="975" height="197" alt="image" src="https://github.com/user-attachments/assets/c70df36f-1704-4dee-aeec-d0e23fe352bd" />
2: Configure the Interface IP Address 
Select the interface that connects to your LAN and assign it a static IP address
Router(config)# interface GigabitEthernet0/0
<img width="975" height="335" alt="image" src="https://github.com/user-attachments/assets/2c63c45c-6dc6-472b-a39c-6ebdd2085319" />
3: Exclude Reserved Addresses 
Before defining the pool, tell the router which addresses NOT to hand out — typically the router's own address and any static devices (printers, servers, access points): 
<img width="975" height="623" alt="image" src="https://github.com/user-attachments/assets/53525345-5e2e-4d63-878b-17ecd5408608" />
Create the DHCP Pool 
Define a DHCP pool, the network it serves, the default router, and DNS servers: 
Router(config)# ip dhcp pool bijay ghimire
Router(dhcp-config)# network 10.50.10.2 255.255.255.0 
Router(dhcp-config)# default-router 10.50.10.1 
Router(dhcp-config)# dns-server 10.50.10.10 10.50.10.11 
Router(dhcp-config)# exit 
Do write  
<img width="975" height="528" alt="image" src="https://github.com/user-attachments/assets/401e85cf-eda1-42d7-84af-cb2c08cb3efd" />
5: Verify the Configuration
Use the following commands to confirm the interface and DHCP pool are working: 
Router# show ip interface brief 
Router# show running-config interface GigabitEthernet0/0 
Router# show ip dhcp pool 
Router# show ip dhcp binding 
show ip dhcp binding lists every client that has received a lease, along with its assigned IP address and MAC address — useful for confirming that devices are pulling addresses correctly. 
<img width="975" height="108" alt="image" src="https://github.com/user-attachments/assets/d7938ad1-7495-4c4d-8f42-eca996cd1624" />
<img width="975" height="290" alt="image" src="https://github.com/user-attachments/assets/41987c79-8fa4-4a6e-9c16-0d1fe33a9eac" />
<img width="975" height="431" alt="image" src="https://github.com/user-attachments/assets/d867ed7b-b32c-41dd-ba48-65836a2d883b" />
<img width="975" height="622" alt="image" src="https://github.com/user-attachments/assets/ac0327d2-c9f9-4136-9447-102f75fb2376" />

