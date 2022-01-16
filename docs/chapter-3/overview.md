# Lab 3  

## Security Features
Lab time: ~45 minutes  

In this lab, we are going to explore some of the security features that Aviatrix provides. Currently we have open and unlimited communication between all VPC’s and VNET’s and Site2Cloud connection. We rely on security groups/NSG’s to secure the workloads. But what if we need more deliberate segmentation? Aviatrix provides the concept of Security Domains. Let’s see how these work and what they can do for us.

## Lab 3.1 - Enable Segmentation on Transit Gateways
### Description
Until now we have set up a relatively flat any to any network.  Now let's see how we can segment our network by using Aviatrix Multi-Cloud Network Segmentation.
### Validate
Go to **_Multi-Cloud Transit -> Segmentation_**. First we need to enable segmentation for all 3 transit gateways.  
![Lab Overview](../images/enable-segmentation.png)
_Fig. Enable Segmentation_   

Select the gateway and click enable. **Make sure to do this for all 3 transit gateways**.

### Expected Results
Now that segmentation is enabled on the transits, we can continue and build out Security Domains.

## Lab 3.2 - Create Security Domains
### Description
Now we are going to create some security domains, which we can use for segmentation.

### Validate
Go to **_Multi-Cloud Transit -> Segmentation -> step 2_** , create the following security domains: _Red_, _Blue_, _Shared_ and _Onprem_.  

![Lab Overview](../images/sec-domains.png)
_Fig. Create Security Domains_  

### Expected Results
The 4 security domains should now be created.

## Lab 3.3 - Create Connection Policies
### Description
In order to specify allowed Security Domain to Security Domain communication, we need to set up some Connection Policies.
### Validate
Go to **_Multi-Cloud Transit -> Segmentation -> step 3_** and modify the _Shared_ security domain so it is connected to _Red_ and _Blue_. Also connect security domain _Onprem_ to _Red_.  

![Lab Overview](../images/connection-policies.png)
_Fig. Connection Policies_  

### Expected Results
The above connection policies should now be created.

## Lab 3.4 - Add VPC’s/VNET’s/S2C to Security Domains
### Description
Now we will add each of the Spokes and On-Prem connection to the security domains.
### Validate
Go to **_Multi-Cloud Transit -> Segmentation_** and on the tabs on the top of the page, go to **_Build_**. Create the following associations:

| Transit Gateway Name | Attachment Name | Security Domain Name |
| ------ | ----------- | ---------- |
| aws-transit   | aws-spoke1 | Red |
| aws-transit   | aws-spoke2 | Blue |
| aws-transit   | shared-service | Shared |
| gcp-transit   | gcp-spoke1 | Red |
| azure-transit   | azure-spoke1 | Blue |
| gcp-transit   | MyOnPrem | Onprem |
		
![Lab Overview](../images/sec-domain-attachments.png)
_Fig. Security Domain Attachments_  

### Expected Results
Once you have done this, have a look at the Security Domain overview in CoPilot. You will find it by clicking **_Security_** in the menu. This should help you clearly understand the Security Domains and the Connection Policies.

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
