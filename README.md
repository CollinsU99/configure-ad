<p align="center">
<img src="https://i.imgur.com/pmz4rhy.png" alt="img"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial provides a step-by-step guide to implementing Active Directory on Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro (22H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure (DC-1 VM and Client-1 VM)
- Set DC-1 NIC private IP from dynamic to static
- Log into Client-1 VM via Remote Desktop and ping DC-1's IP address
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p align="center">
<img src="https://i.imgur.com/lNFfgp4.png" height="80%" width="80%" alt="img"/>
</p>

Go to https://portal.azure.com/

Search for "virtual machine in the search bar and click "Virtual machines".

<p align="center">
<img src="https://i.imgur.com/vir8b1g.png" height="80%" width="80%" alt="img"/>
</p>

Click "Create", and click "Azure virtual machine".

<p align="center">
<img src="https://i.imgur.com/CIbAwEw.png" height="80%" width="80%" alt="img"/>
</p>

Select your Azure subscription, click "create new, and name your resource group "AD-Lab". Name your virtual machine "DC-1" and select (US) West 3 US for the region. For availability options, select "No infrastructure redundancy required". Select "Standard" for security type, and select "Windows Server 2022 dtatcenter: Azure Edition" for image. For size, select "Standard_E2s_v3 - 2 vcpus, 16 GiB memory". Use "labuser" as your username, and input a unique password. Click "Review + creat".

<p align="center">
<img src="https://i.imgur.com/Wl2u6Ll.png" height="80%" width="80%" alt="img"/>
</p>

We got a "Valiadation passed" message, click the "Create" button in the bottom left.

<p align="center">
<img src="https://i.imgur.com/zYlGl4p.png" height="80%" width="80%" alt="img"/>
</p>

The "Your deployment is complete" message indicates that our DC-1 VM has been created.

Let's go ahead and create "Client-1" VM.

<p align="center">
<img src="https://i.imgur.com/vir8b1g.png" height="80%" width="80%" alt="img"/>
</p>

Go back virtual machine, click "Create", and click "Azure virtual machine".

<p align="center">
<img src="https://i.imgur.com/Z3MrTxB.png" height="80%" width="80%" alt="img"/>
</p>

Select your Azure subsription, select the same resource group as DC-1, name your virtual machine "Client-1", select the same region, availability options, and security type as DC-1. Select "Windows 10 Pro, version 22H2" for image. Select the same size and use the same username and password you used for DC-1. Check the licensing box and click the networking tab at the top.

<p align="center">
<img src="https://i.imgur.com/ZCNkJ5o.png" height="80%" width="80%" alt="img"/>
</p>

Make sure you select the same virtual network as DC-1. A subnet and IP address will automatically be created for you. Click the "Review + create" button in the bottom left.

<p align="center">
<img src="https://i.imgur.com/qZHlkOS.png" height="80%" width="80%" alt="img"/>
</p>

We got a "Valiadation passed" message. Go ahead and click the "Create" button in the bottom left.

<p align="center">
<img src="https://i.imgur.com/pLTETK3.png" height="80%" width="80%" alt="img"/>
</p>

The "Your deployment is complete" message indicates that our Client-1 VM has been created.

<p align="center">
<img src="https://i.imgur.com/9kpDOrS.png" height="80%" width="80%" alt="img"/>
</p>

We will now set DC-1 NIC private IP from dynamic to static. Go back to virtual machine and click "DC-1".

<p align="center">
<img src="https://i.imgur.com/Ko8EfOS.png" height="80%" width="80%" alt="img"/>
</p>

Click "Networking", then click DC-1 Network Interface.

<p align="center">
<img src="https://i.imgur.com/6m9XTCx.png" height="80%" width="80%" alt="img"/>
</p>

Click "Ip Configurations".

<p align="center">
<img src="https://i.imgur.com/nGTecei.png" height="80%" width="80%" alt="img"/>
</p>

Click "ipconfig1".

<p align="center">
<img src="https://i.imgur.com/wo6rDCo.png" height="80%" width="80%" alt="img"/>
</p>

Select "Static", and click the "Save" button. This means that the IP address of DC-1 will not change.

<p align="center">
<img src="https://i.imgur.com/FWvuMXc.png" height="80%" width="80%" alt="img"/>
</p>

Log into Client-1 VM via Remote Desktop and ping DC-1's IP address (perpetual ping).

Go to virtual machine and click "Client-1".

<p align="center">
<img src="https://i.imgur.com/J73jcNu.png" height="80%" width="80%" alt="img"/>
</p>

Copy Client-1's public IP address.

<p align="center">
<img src="https://i.imgur.com/nVjRq04.png" height="80%" width="80%" alt="img"/>
</p>

Open Remote Desktop, paste Client-1's IP address, and click "Connect".

<p align="center">
<img src="https://i.imgur.com/RHIfVY8.png" height="80%" width="80%" alt="img"/>
</p>

Click "More choice" > "Use a different account", type in the username and password we used when we were creating Client-1's VM, and click the "Ok" button.

Minimize Client-1's VM.

<p align="center">
<img src="https://i.imgur.com/EggybQN.png" height="80%" width="80%" alt="img"/>
</p>

In your Azure portal, click DC-1.

<p align="center">
<img src="https://i.imgur.com/tjATsm7.png" height="80%" width="80%" alt="img"/>
</p>

Note down DC-1's Private IP Address.

<p align="center">
<img src="https://i.imgur.com/ypTy31O.png" height="80%" width="80%" alt="img"/>
</p>

Go back to Client-1's VM, select "No" for all the options, and click the "Accept" button.





























































