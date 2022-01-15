# Lab 1

## Lab Overview - What's in the lab?
Lab time: ~20 minutes

In this lab, we are going to explore our lab environment. The diagram below shows the current state of the lab environment. You will extend this environment during the exercises. The instructor will briefly explain the lab setup in the diagram. You can find a more complete and detailed diagram here.

![Lab Overview](../images/lab-before.png)  
_Figure 1: Lab Overview_

## Lab 1.1 - Aviatrix Controller

First, we are going to log into the controller. To do so, set up a connection with your browser by browsing to:

<table>
  <tr>
    <td><b>Description</b></td>
    <td>Navigate and login to the Aviatrix Controller</td>
  </tr>
  <tr>
    <td><b>Validate</b></td>
    <td>URL:  <i>https://ctrl.pod(#).aviatrixlab.com</i><br>Username:  admin<br>Password:  Password123!</td>
  </tr>
  <tr>
    <td><b>Expected Results</b></td>
    <td>Explore the Dashboard. As you can see, there are already gateways deployed in different CSP environments. Do they seem connected to each other? Do you think this connection is working? Why do you think so?</td>
  </tr>
</table>

## Lab 1.2 - Access Accounts

<table>
  <tr>
    <td><b>Description</b></td>
    <td>In order for the controller to be able to access the different CSP environments, we need to provide it with accounts with the correct privileges.</td>
  </tr>
  <tr>
    <td><b>Validate</b></td>
    <td>Have a look at the access accounts already set up under Accounts -> Access Accounts</td>
  </tr>
  <tr>
    <td><b>Expected Results</b></td>
    <td>Accounts in GCP, AWS and Azure have already been onboarded and you should see the three accounts in the list.  The accounts should also be green, meaning the permissions in the accounts are correctly configured</td>
  </tr>
</table>

## Lab 1.3 - Connectivity Check

### Description
Each spoke VPC / VNET contains a Linux VM to test connectivity.  The purpose of this exercise is to verify the connectivity between Linux VMs in the spoke VPCs / VNETs in the 3 different clouds
### Validate
In order execute the connectivity tests, we need to log on to the test instances we have deployed throughout the lab. We use a web based SSH tool for this. Browse to:  
  
**URL:** ```https://web.pod[x].aviatrixlab.com```  
**User:** ```admin```  
**Password:** ```Password123!```  

*(replace [x] with your pod ID)*
>If you want to use copy/paste in this Guacamole web console, use CTRL+ALT+SHIFT on a Windows device or CTRL+CMD+SHIFT on a MacOS device.  
1- Connect into **GCP-SRV1** from the *ALL CONNECTIONS* pane. (Tip: use right-click open in new tab)  
2- Run the following commands:
```
ping azure-srv1-priv.pod[x].aviatrixlab.com  
ping aws-srv1-priv.pod[x].aviatrixlab.com  
ping aws-srv2-priv.pod[x].aviatrixlab.com  
ping shared-priv.pod[x].aviatrixlab.com
```  
### Expected Results
Not all of the ping tests will be successful.  Look at the Diagram in the Lab 1 Overview and you will see that only Azure and GCP are connected so far, but AWS is not connected, therefore the connectivity tests from GCP to AWS will not work.


