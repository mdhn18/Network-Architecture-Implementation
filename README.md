# Network-Architecture-Implementation
#Architecture
I have done my architecture with star topology for medium business network it’s working every point. I have completed it department by department. I have done my design part by part engineering staff, build box, store server connected them into a router. After that this router connected to main switch. Similarly, sales department I am going to explain the ip address, subnet, bandwidth, growth, routing, VPN and tunneling every part under title of department.

![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/3b9890e6-2668-489d-9077-c2f77daf59f8)


#Engineering department:
In this department staff (200), build box people (50) and 10 are in the storage data.
1. In this section assigned network 192.168.0.0/23 and netmask are 255.255.254.0.
2. For this netmask we can used 510 valid addresses
3. Its B class IP address.
4. In future we can increase the computer then we can used from 192.168.0.2 to 192.168.0.510 ip addresses.
SPU also in engineering department but we can take it out side with different router.

#Sales department:
Two people work in office and 4 people are technical writers working on documentation and adaption of documentation are together in one router total 30 for visiting sales. Sale department some time use SME network from out site in that case we can use a VPN server for sale group.
1. For sales people I take IP 12.0.1.0 and netmask 255.255.255.192.
2. We can used 62 valid IP address.
3. I take customer support team another router with network 20.0.1.0 255.255.255.248 because its only 4 computers.
4. I also take the VPN in different router for remote access.
