# Network-Architecture-Implementation
#Architecture <br />
I have done my architecture with star topology for a medium business network, and it’s working at every point. I have completed it department by department. I have done my design part by part engineering staff, build box, store server connected them into a router. After that, this router connected to the main switch. Similarly, sales department I am going to explain the ip address, subnet, bandwidth, growth, routing, VPN and tunneling every part under title of department.

![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/3b9890e6-2668-489d-9077-c2f77daf59f8)


#Engineering department:<br />
In this department, staff (200), build box people (50), and 10 are in the storage data.
1. In this section assigned network 192.168.0.0/23 and netmask are 255.255.254.0.
2. For this netmask, we can use 510 valid addresses
3. Its B class IP address.
4. In the future, we can increase the computer use from 192.168.0.2 to 192.168.0.510 ip addresses.<br />
SPU is also in the engineering department, but we can take it outside with a different router.

#Sales department:<br />
Two people work in an office, and four people are technical writers working on documentation and adaption of documentation. They are together in one router, with a total of 30 visiting sales. The sales department sometimes uses an SME network from our site. In that case, we can use a VPN server for the sales group.<br />
1. For salespeople, I take IP 12.0.1.0 and netmask 255.255.255.192.
2. We can use 62 valid IP addresses.
3. I took the customer support team to another router with network 20.0.1.0 255.255.255.248 because it's only four computers.
4. I also take the VPN in different routers for remote access.<br />

#Management department:<br />
In this section, I take one router, and the network of this section is 11.0.1.0 255.255.255.240. In this IP, we can use valid 14 addresses, so if in the future in the management section need to increase the number of computers, we can add. They can access all the sections in the network connected to the cloud also. They can access a dedicated server if they are in out-sourced by VPN.<br />

#Bandwidth Calculations:<br />
For each group’s bandwidth calculation in this table- <br />
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/89a74c7d-81cb-467c-8e68-955148545992)
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/3d7ef715-0be3-4220-972e-4b7088c2bd1e) <br />

Here is the total bandwidth Load In and Load Out <br />
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/213649b1-5cd4-41e5-85fa-12146d979c9e) <br />

All service groups require bandwidth under 100Mbps; the load-in and load-out bandwidth total is 51.84Mbps and 110.80Mbps. So, we can connect them by CAT5 Copper Straight-Through cable because this can transfer data per second 100Mbps. <br />

#Growth: <br />
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/ca84a287-a33b-4173-ae8e-e5ce20c8e01b)
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/2a871949-67d6-452b-9284-2fe7b34f18a3)

After 6 months A and B service group updated, it will be 20000 customer/h and 15000 customer/h. In that case,<br />
> Load In increase= [51.84Mbps+(Anew load In+ Bnew load In )-(Aold load In + Bold load In)] <br />
                  =51.84Mbps+0.47Mbps+0.70Mbps-0.25Mbps-0.45Mbps<br />
                  =52.31Mbps<br />
> Load Out increase= [110.80Mbps+(Anew load out+ Bnew load out )-(Aold load out + Bold load out)]<br />
                   =110.80Mbps+46.55Mbps+69.96Mbps-22.65Mbps-45.30Mbps <br />
                   = 159.36Mbps. <br />
So, after 6 months, total bandwidth required = Load In + Load Out <br />
                                             =52.31Mbps + 159.36Mps <br />
                                             =211.67Mbps <br />
> After 12 months, two new service groups added I and J, then the total load in and load out is <br />
   Total Load In = 52.31Mbps+23.49Mbps(I)+81.37Mbps(J) <br />
                 = 157.17Mbps <br />
   Total Load Out = 159.36Mbps+0.0023Mbps(I)+162.74Mbps(J) <br />
                  = 322.1023Mbps <br />
> Overall Bandwidth required after increasing the service group <br />
                  = Total Load In + Total Load Out <br />
                  = 157.17Mbps + 322.1023Mbps <br />
                  = 479.27Mbps <br />
                  =480Mbps(round) <br />

So overall, all we can take is a 500Mbps net connection. This bandwidth covers every service group, but the J group needs link aggregation because in this group, load out and load in together 244.11Mbps. Normal CAT5 Copper Straight-Through cable can transfer only 100Mbps. <br />

After 24 months we need to change subnet of engineering section because we need merge into the existing group we need required more usable IP address. In that case, we can replace /23 with/22 so we get 1022 usable IP addresses. <br />

#DHCP:<br />
Dynamic Host Configuration Protocol is a client-server protocol. In this network, every router is in DHCP mode. It will be helpful to add a new computer to this network no need to configure it by static. In a big network, if we configure it manually, it will be difficult to remember other IP addresses. In DHCP mode, we get the host IP by request of DHCP, and the host gets the IP address automatically. <br />

#SPU: <br />
In this architecture, I have actively used two routers to work the load balancer for both routers. These two routers configured a virtual gateway, which helps to send data if one of them is not working or shut down. Configuration of those routers- <br />
R1: G0/0 21.0.1.1/28, G0/1 17.0.1.12/26 <br />
R2: G0/0 21.0.1.5/28, G0/1 17.0.1.11/26 <br />
For both routers, the default router is 21.0.1.10 <br />

Those routers apply the HSRP (Hot standby routing protocol) protocol system to create the virtual default router, which works perfectly. When an active router works with another router, the state is inactive or on standby. If the active router gets any problem, then the standby router works automatically without any notification. <br />

#Link Aggregation: <br />
Link aggregation is established between the main switch 1 and main switch 2, and I also apply the channel port 1 for those links. In those center switches of the network faced more traffic if we use a single link between them it will be risky. In disturbance of the link 1 then other link can be active. So it is very important to activate the network for any odds condition between these switches. <br />

#Cross connection:<br />
The management department is connected to all departments (Engineering, sales, SPU, and printer). The engineering section also connects to the SPU file server printer and customer support section. SPU, management, engineering, and salespeople are connected to the internet. All sections can access the printer. <br />

#Monitoring: <br />
I have used another server with a different router and turned on SYSLOG mode to monitor notifications for any router and switches. I installed the code “logging (IP address of SYSLOG server)” in every server and switched and saved them. My code is “logging 22.0.1.1”. If I disconnect any router, switch, or shut down any port, the text will go to the SYSLOG server. <br />

- My session for monitoring for the SME PRTG monitoring tools will cover the filter's IP address, protocols, total traffic, port sniffer, file transfer traffic remote control, etc.
- After 24 months, if the engineering section has grown by 25-50 people and 5-6 sales staff, there are no issues with the connection because the network's capacity is two times capable.
  
#VPN and tunneling: <br />
I have done the tunneling for remote cell with the main route which is connected to the internet I have used the virtual IP address is 100.0.0.1 for main router and IP address 100.0.0.2 for remote cell section. There are no effects on the other routers and switches for VPN tunneling. If we configure the routers, it is going to be faster. VPN tunneling between the VPN server and the dedicated server is done. <br />

In this network, two VPN tunneling are done <br />
- One Out-site router link to a dedicated server. <br />
- Second VPN server to Out site router link <br />

#Printer:
Management, engineering, and sales groups are connected to the printer router.
