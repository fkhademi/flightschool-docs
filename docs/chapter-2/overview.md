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
![Create VPC](../images/topology2.png)  
_Fig. Create Transit VPC_  

Check out the CoPilot Topology View.  Do you see the newly created Transit VPC?