# Lab 4  

## Operations, Visibility and Troubleshooting
Lab time: ~30 minutes  

The focus of this lab will be on using all of the visibility provided by the Aviatrix platform to find that needle in a haystack.  By using Aviatrix, the customer owns the network and is able to have visibility into all traffic flows in the event that troubleshooting is needed.

## Lab 4.1 - Packet Capture
### Description
While operating a cloud environment, there are times where following and capturing packets is necessary.  The Aviatrix Controller allows you to centrally perform and generate packet captures from the Aviatrix Gateways.
### Validate
To start a packet capture, navigate to **_Troubleshoot -> Diagnostics -> Network -> Packet Capture_**.  Select one of the Aviatrix Gateways, the interface (eth0), optionally filter on host and/or port, and click _Start_.  Captured packets will be displayed live - click _Stop_ when finished, download the PCAP and open it in Wireshark.

![Packet Capture](../images/packet-capture.png)  
_Fig. Packet Capture_  
### Expected Results
You should be able to view live captured packets in the UI.  By downloading the PCAP and opening the file in Wireshark, you will see more detailed packet information.

![Packet Capture Details](../images/packet-capture-details.png)  
_Fig. Packet Capture Details_  

## Lab 4.2 - Traceroute, Ping, Telnet
### Description
Using Aviatrix Gateways in the datapath means that you own the datapath.  Another benefit of owning the datapath is having the ability to use some basic but helpful commands such as ```traceroute```, ```tracepath```, ```ping```, ```telnet```, etc.
### Validate
To test this out, open _Co-Pilot_ and navigate to **_Topology_**.  Doubleclick on **_gcp-spoke1_** node (VPC / VNET) that you would like to troubleshoot and click on the orange **Aviatrix Gateway**.  On the right side, click on the **_Diag_** button.  

* Under the **Ping** tab, enter the FQDN ```shared-priv.pod[x].aviatrixlab.com```
* Under the **Traceroute** tab, enter the FQDN ```shared-priv.pod[x].aviatrixlab.com```
* Under the **Test Connectivity** tab, enter the FQDN ```shared-priv.pod[x].aviatrixlab.com``` and Port 22
* Click **Active Sessions** to view the current active sessions running over that Gateway
* Click **Interface Stats** to the gateway interface stats, packet drops, errors, PPS limits, etc

![Gateway Diagnostics](../images/gateway-diag.png)  
_Fig. Gateway Diagnostics_  

### Expected Results
Using the Topology Gateway Diag, you can run pings, traceroutes, etc.  This is helpful when you need to find out why communication to or from a VPC / VNET is not working.

## Lab 4.3 - AppIQ
### Description
**AppIQ** is every cloud operator’s best friend and will always help to find that needle in a haystack.  When a connectivity issue arises between VPCs, regions, clouds, there are many places in the cloud infrastructures that need to be checked.  AppIQ query the cloud providers and show whether Routing at the VPC, Subnet, Gateways, NACLs, and Security Groups are configured correctly at Source and Destination to properly allow the communication.
### Validate
Open CoPilot and navigate to **_AppIQ_**.
* In the **Source Instance** dropdown, select the instance _gcp-srv1_
* In the **Destination Instance** dropdown, select the instance _shared-srv_
* Enter port _443_, select the _Private interface_ and click **Submit**

![AppIQ](../images/appiq-config.png)  
_Fig. AppIQ_  

### Expected Results
AppIQ will show you the path between the selected VMs, will show the latency on each hop, Gateway utilization on each hop and all infrastructure related settings (security groups, route tables, etc).  Scroll through the results - sometimes a simple thing like a missing security group rule can take hours to troubleshoot, but with AppIQ you can get find the issues in seconds or minutes.  

![AppIQ Results](../images/appiq-results.png)  
_Fig. AppIQ Results_  


## Lab 1.4 - Exploring the Aviatrix Gateways
### Description
As you can see from the lab diagram, there are already some Aviatrix gateways deployed. Let’s see where we can find them in the controller.
### Validate
Go to **_Multi-Cloud Transit -> List_**. As you can see, this is where the existing transit gateways are listed. Look at the following fields: Name, VPC CIDR, Spoke List and Transit Peering. Try to derive the existing topology as seen on the lab diagram from this information.  
### Expected Results
You should be able to view the VPC / VNET and Gateway Route Tables for both the Transit Gateways and Spoke Gateways.



## Lab 1.4 - Exploring the Aviatrix Gateways
### Description
As you can see from the lab diagram, there are already some Aviatrix gateways deployed. Let’s see where we can find them in the controller.
### Validate
Go to **_Multi-Cloud Transit -> List_**. As you can see, this is where the existing transit gateways are listed. Look at the following fields: Name, VPC CIDR, Spoke List and Transit Peering. Try to derive the existing topology as seen on the lab diagram from this information.  
### Expected Results
You should be able to view the VPC / VNET and Gateway Route Tables for both the Transit Gateways and Spoke Gateways.



## Lab 1.4 - Exploring the Aviatrix Gateways
### Description
As you can see from the lab diagram, there are already some Aviatrix gateways deployed. Let’s see where we can find them in the controller.
### Validate
Go to **_Multi-Cloud Transit -> List_**. As you can see, this is where the existing transit gateways are listed. Look at the following fields: Name, VPC CIDR, Spoke List and Transit Peering. Try to derive the existing topology as seen on the lab diagram from this information.  
### Expected Results
You should be able to view the VPC / VNET and Gateway Route Tables for both the Transit Gateways and Spoke Gateways.
