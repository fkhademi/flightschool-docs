# Lab 2

## Create VPCs/VNets and deploy Aviatrix gateways?
Lab time: ~60 minutes

In this lab, we will begin to build out the multi-cloud network.  We will create VPCs, deploy Aviatrix Transit and Spoke Gateways and create transit peerings to peer the different clouds together.  We will also connect an on-prem Data Center to the cloud.

![Lab Overview](../images/lab-before.png)
_Fig. Lab Overview_

## Lab 2.1 - Deploy the AWS transit VPC
### Description
As the instructor explained in the first lab, we already have a transit VPC/VNET in Azure and GCP. In this lab, we are going to make the preparations to deploy the aviatrix gateways in the AWS environment. In order to do so, we need a VPC. Instead of having to use the CSP’s console to do this, the controller can do this for us.
### Validate
Go to **_Useful Tools -> Create a VPC_**. As you can see, there already are multiple VPC’s here. See if you can identify these VPC’s on the lab diagram.  
  
Now click the add new button. Add a new VPC with the following settings:  
![Create VPC](../images/create-vpc.png)  
_Fig. Create Transit VPC_  
  
For the VPC CIDR, replace “x” with your pod number. For example, if your pod number is 11. “x” should be replaced with 11, so the complete CIDR will become 10.11.40.0/23. Make sure Aviatrix Transit VPC is checked. The add VPC tool will automatically create all the required public and private subnets, IGW and routing tables.  
  
By default, it will use the assigned CIDR to add a private and public subnet to each availability zone in AWS. As of version 6.1, we can modify this behavior in the Advanced settings. Click add new again from the Create a VPC window and have a look at these settings. Try creating and deleting some VPC’s and VNET’s.
### Expected Results
Our environment now looks like this:  
![Topology](../images/topology2.png)  
_Fig. Topology_  

Check out the CoPilot Topology View.  Do you see the newly created Transit VPC?

## Lab 2.2 - Deploy the Aviatrix transit gateway
### Description
In this exercise we are going to launch the Aviatrix transit gateway in the newly created Transit VPC in AWS. 
### Validate
Browse to **_Multi-Cloud Transit -> Setup_** and launch a new transit gateway via step 1 with the settings below.  

The VPC ID will differ from your environment, but we will select the VPC that we just created and named _aws-transit_. For the public subnet, use the one that has _Public-gateway_ in the name and is located in availability zone _a_. You can click on any of the info buttons if you want to understand what the other settings relate to. Click create when you are ready. This will take a few minutes, have a coffee.  
![Create VPC](../images/create-transit-gw.png)  
_Fig. Create Aviatrix Transit Gateway_  
  
Once the gateway has been deployed, take a look at step 2 on this setup page. We are not deploying an HA solution in this workshop, but you can see how easy it is to deploy a second gateway and cluster them in an HA pair.  
### Expected Results
Our environment now looks like this:  
![Toplogy](../images/topology3.png)  
_Fig. Topology with AWS Transit_  

Check out CoPilot Topology.  Why is the AWS Transit cluster now visible?  
![Toplogy](../images/copilot-trans-gw.png)  
_Fig. Copilot Topology_  

## Lab 2.3 - Deploy the spoke gateways
### Description
Now that we have our transit set up, we will deploy the Aviatrix spoke gateways in the *AWS spoke VPC’s* that were already prepared.   

### Validate
Create the spoke gateways for the existing VPC’s using the settings below by using **_step 4_** (scroll down) on the **_Multi-Cloud Transit -> Setup_** page.  
![Toplogy](../images/create-spoke-gw.png)  
_Fig. Create Spoke Gateway_  

Make sure you do this for all 3 AWS spoke VPC’s:  
* _shared-aws_
* _aws-spoke1_
* _aws-spoke2_

### Expected Results
Our environment now looks like this:
![Toplogy](../images/topology4.png)  
_Fig. Topology with Spokes_  

Check out CoPilot Topology.    
![Toplogy](../images/copilot-spoke-gw.png)  
_Fig. Copilot Topology_

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
