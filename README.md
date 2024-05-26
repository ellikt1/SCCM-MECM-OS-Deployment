<h1>SCCM/MECM OS Deployment</h1>

 <img src="https://i.imgur.com/Wl8C0vj.png" alt="Microsoft Endpoint Configuration Manager" class="header-image">

<h2>Description</h2>
This project showcases how System Center Configuration Manager (SCCM), also known as Microsoft Endpoint Configuration Manager (MECM), is used to deploy task sequences for setting up client work computers in a simulated environment. The deployment includes the operating systems:
<br />
<br />

 - <b>Windows 10 to WS001 </b>
 - <b>Windows 11 to WS002 </b>
 - <b>Windows Server 2022 to TS01 </b>

 <br />

The task sequences are configured to install Windows 10 Pro and Windows 11 Pro using a KMS key to display as Enterprise editions, avoiding the "evaluation" label. The computers are configured to join the CM.LAB domain:
<br />
- <b>WS001 and WS002 computers are placed in the Clients OU (Organizational Unit).</b>

- <b>Windows Server 2022 is placed in the Members Servers OU.</b>

<br />

The service account (svc.tasksequence) is used within the task sequences to ensure new computers are added to the correct OUs. The task sequences include all available software updates to keep the computers fully patched. Additionally, BitLocker is enabled to mimic real-world security practices. The specific applications included in the task sequences are listed below.
<br />

The task sequence was deployed to all unknown computers and allowed only through media and PXE to enable centralized OS deployment and management. The virtual machine WS001 was created in VMware Workstation Pro 17.5 with the following configuration:

 - <b>1 processor (2 cores) </b>
 - <b>4GB of memory </b>
 - <b>64GB of storage </b>

It operates within the LAN segment "CM Lab" and mimics a client work computer.

The program walk through below shows the successful deployment process of Windows 10 Enterprise (64-bit) 22H2 to WSS01. The same steps were used, with appropriate adjustments, to deploy Windows 11 Enterprise (64-bit) 23H2 to WS002 and Windows Server 2022 (64-bit) 21H2 to TS01.
<br />
<br />

<h2>Environment Used</h2>
<p>
The lab environment consists of three virtual machines: DC01 (Domain Controller), GW01 (Gateway), and CM01 (Configuration Manager).
 <br />
</p>

<b>DC01:</b>
- 1 processor (2 cores)
- 2GB of memory
- 100GB of storage
- Operates within the "CM Lab" LAN segment as the domain controller.

<b>GW01:</b>
- Similar specifications to DC01
- Serves as the gateway, enabling Wi-Fi connections to DC01 via Routing and Remote Access
- Has 2 network adapters: one configured for NAT and the other operating in the "CM Lab" LAN segment.

<b>CM01:</b>
- 1 processor (8 cores) 
- 16GB of memory
- Varying storage capacities totaling to 700GB of storage
- Operates within the "CM Lab" LAN segment and relies on DC01 for internet access.
- DC01 uses DHCP to allocate IP addresses, allowing CM01 to connect to the internet. This setup demonstrates network infrastructure configurations and management using virtualization technology.
<br />

<p> 
CM01 is the focal point of the lab environment, featuring a robust configuration that includes WSUS (Windows Server Update Services), SQL Server 2022, SQL Server Management Studio, and Configuration Manager version 2403.
<br />
</p>

- <b>WSUS:</b> Manages Windows updates across the network, ensuring timely deployment and compliance with security patches and feature upgrades.
- <b>SQL Server 2022 and SQL Server Management Studio:</b> Provide a powerful database management platform, facilitating advanced data storage, retrieval, and manipulation 
- <b>Configuration Manager version 2403:</b> Enhances system capabilities by streamlining configuration tasks, automating software deployment, and enforcing compliance standards.
<br />

<h2>Environment Topology</h2>

<p align="center">
<img src="https://i.imgur.com/2sjgNoV.png" height="80%" width="80%" alt="Disk Sanitization Steps2"/>
</p>


<h2>Operating Systems Deployed</h2>

- <b>Windows 10 Enterprise (64-bit) 22H2:</b> dasfdfsda


- <b>Windows 11 Enterprise (64-bit) 23H2:</b>  asdsadsadsa


- <b>Windows Server 2022 (64-bit) 21H2:</b> adsdsadsa


<h2>Utilities & software Used</h2>

- <b>VMware Workstation Pro 17.5</b>
- <b>SCCM/MECM 2403</b>
- <b>Draw.io 24.4.8</b> 

<h2>Program walk-through:</h2>

<br/>
<br/>

<p align="center">
Creating the Application <br/>
<img src="https://i.imgur.com/aDvw2SQ.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Populated the name, added the correct boot image, and ran as high performance <br/>
<img src="https://i.imgur.com/iPxU4zW.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Populated the correct image package, index, product key was added to bypass the "evaluation" label <br/>
<img src="https://i.imgur.com/AlnuCwp.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Populated the correct Domain, Domain OU, and svc.tasksequence account <br/>
<img src="https://i.imgur.com/yHpURLd.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Package was left default <br/>
<img src="https://i.imgur.com/e0ks1Hf.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Disabled all capture settings <br/>
<img src="https://i.imgur.com/tYBLhHM.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
All software updates to allow patches <br/>
<img src="https://i.imgur.com/iRNUFng.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Added various applications <br/>
<img src="https://i.imgur.com/J2HhGR5.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Task sequence complete <br/>
<img src="https://i.imgur.com/NGbvAUd.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Enabling Bitlocker <br/>
<img src="https://i.imgur.com/oDErYmu.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Deploying the task sequence to all unknown computers <br/>
<img src="https://i.imgur.com/oDErYmu.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Only media and PXE <br/>
<img src="https://i.imgur.com/Fmu6vmM.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Deployment complete <br/>
<img src="https://i.imgur.com/Qx5GEhs.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Creating WS01 virtual machine in Vmware <br/>
<img src="https://i.imgur.com/dFzT0Ln.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Task sequence Executing <br/>
<img src="https://i.imgur.com/F8md7dc.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Inputted password  <br/>
<img src="https://i.imgur.com/MvhIFIC.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Windows 10 Enterprise (64-bit) 22H2 (ignore duplications repeated the process to document) <br/>
<img src="https://i.imgur.com/kY6telB.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Entered the Name of the computer WS001 <br/>
<img src="https://i.imgur.com/w2j9bTs.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Wait for Oprating System to fully install and Task sequence to complete<br/>
<img src="https://i.imgur.com/bJDfXsC.png" height="80%" width="80%" alt="Operating System Deployment"/>

<p align="center">
Windows 10 and the deployed applications successfully installed: <br/>
<img src="https://i.imgur.com/Rp1QkmB.png" height="80%" width="80%" alt="Operating System Deployment"/>


<br />
<br />
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>

