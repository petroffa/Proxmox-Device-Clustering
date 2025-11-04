# Proxmox-Device-Clustering

Diagram:

<img width="975" height="664" alt="image" src="https://github.com/user-attachments/assets/c2024cd5-3aba-4f4a-8060-66b29d27547a" />











Goal: To combine multiple computer resources together, in order to run multiple Virtual Machines or perform website hosting with the resources beyond one PC, all while being accessible from any device on the local network.

Resources used:
•	3 Dell Optiplex 780s (3x 8GB RAM, 256GB HDD, Intel Core 2 Duo CPU E7500 @2.93GHz)
•	1 HP Pavilion g7 (3GB RAM, 256GB HDD, 2 core AMD A6-4400M CPU)
•	5 Ethernet cables
•	NETGEAR 8-Port Gigabit Ethernet Unmanaged Switch(GS308)
•	Xfinity Advanced Gateway (XB8)
•	1 16GB Flash Drive
Setup:
1.	Create bootable USB: 
I first downloaded the Proxmox VE 9.0 ISO from Proxmox’s main website. Once downloaded, I plugged a flash drive into my personal computer, and used the application Rufus to format the flash drive and make the ISO image bootable:

<img width="507" height="595" alt="image" src="https://github.com/user-attachments/assets/d8387014-3196-4d3d-aa8d-658cfb641071" />












2.	Initial image setup: 
Once formatted, I connected the USB to each device, booted them with the ISO, configured the current timezone and keyboard, set a custom root password, and configured the hostname and IP address with the local gateway for my network. Once these steps are completed on each computer, they reboot and broadcast themselves on my home LAN.
3.	Node interaction with gateway:
 This is an optional step, however in this example I want my nodes to all have static IP values, in order to set this I signed in remotely to my local router, went into connected devices, and specified that each node have a reserved IP address I select.

Execution:
1.	Creating the Cluster:
To create a cluster, I connected to my first proxmox node, and enter in my sign in:

<img width="586" height="265" alt="image" src="https://github.com/user-attachments/assets/96356d88-ec4d-4546-aabd-9dfd70dff0a6" />


Once completed, I then Go to Datacenter > Cluster > and select “Create Cluster”. From within that portal, it lets me specify a custom name, and then “Create”.

2.	Adding other nodes:
Now that I have a cluster(which for this project I named “test”), to add my other nodes to the cluster I select the “Join information button” in the cluster menu, copy the created string, 






<img width="975" height="572" alt="image" src="https://github.com/user-attachments/assets/ca9c5a10-05cb-44f8-859e-a5e1dad9897f" />














and then sign into another node, go to Datacenter > Cluster > Join Cluster, and paste in the information along with the root password:





<img width="975" height="394" alt="image" src="https://github.com/user-attachments/assets/46a3391b-b3bb-4809-844c-5d3e57adacdd" />









And with that the node is added! I then completed the steps for the other nodes, until all 4 were added into the cluster:
 <img width="975" height="296" alt="image" src="https://github.com/user-attachments/assets/be195f20-8e95-479a-aafe-261e66314c69" />

With that, all nodes are now sharing resources with each other.

Conclusion: 

With this setup, it allows myself or others to easily create a virtual machine(s), spin it up on a hard drive, and have as many nodes as I can afford share computer resources and processing between each other, as if they were one large computer. This could allow for something as simple as routine VM testing, to creating virtual networks and running cybersecurity red team/blue team scenarios, to even hosting adjustable and expandable online servers.

