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
4. I also take the VPN in different router for remote access.<br />

#Management department:<br />
In this section, I take one router, and the network of this section is 11.0.1.0 255.255.255.240. In this IP, we can use valid 14 addresses, so if in the future in the management section need to increase the number of computers, we can add. They can access all the section in the network connected to the cloud also. They can access a dedicated server if they are in out-sourced by VPN.<br />

#Bandwidth Calculations:<br />
For each group’s bandwidth calculation in this table- <br />
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/89a74c7d-81cb-467c-8e68-955148545992)
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/3d7ef715-0be3-4220-972e-4b7088c2bd1e)
Here is the total bandwidth Load In and Load Out <br />
![image](https://github.com/mdhn18/Network-Architecture-Implementation/assets/55639146/213649b1-5cd4-41e5-85fa-12146d979c9e)
> All service groups require bandwidth under 100Mbps; the load-in and load-out bandwidth total is 51.84Mbps and 110.80Mbps. So, we can connect them by CAT5 Copper Straight-Through cable because this can transfer data per second 100Mbps. <br />

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


