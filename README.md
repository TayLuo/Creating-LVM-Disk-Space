# Creating-LVM-Disk-Space-
The goal of this lab is to teach you how to create and manage LVM (Logical Volume Manager) disk space on a virtual machine (VM) instance in Google Cloud Platform (GCP). By the end of this lab, you will be able to add additional disks to a VM, set up LVM, and create logical volumes for data storage. 

To understand the use LVM we need to comprehend three main components, they are interconnected and together make what we call a Logical Volume, here are the three components:

Physical Volume: It is simply the physical storage devices, whether it is SSD or HDD drives. 
 

Volume Group: It is a pool which is comprosed of physical volumes.

Logical Volume: When the VG created, we can finally creates a logical volume, you can create one or more logical volumers from a single volume group. 

Here is a diagram for this relationship:


![lvmsetup](https://github.com/user-attachments/assets/8f99d2d1-141e-46f0-b4b1-33b06719b1a1)




For this demonstration purpose, I will use Google Cloud Platform. The concept will apply in any platforms and distributions.



1. Install required Packages
   
   Ensure that the system has essential packages like gcc, glibc, make, wget, and openssl installed, there are more packages need to be installed.    :
   
   		dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/odDHSSA.png" height="80%" width="80%" >
<br />    

1. Install required Packages
   
   Ensure that the system has essential packages like gcc, glibc, make, wget, and openssl installed, there are more packages need to be installed.    :
   
   		dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/odDHSSA.png" height="80%" width="80%" >
<br />    


1. Install required Packages
   
   Ensure that the system has essential packages like gcc, glibc, make, wget, and openssl installed, there are more packages need to be installed.    :
   
   		dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/odDHSSA.png" height="80%" width="80%" >
<br />    


1. Install required Packages
   
   Ensure that the system has essential packages like gcc, glibc, make, wget, and openssl installed, there are more packages need to be installed.    :
   
   		dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/odDHSSA.png" height="80%" width="80%" >
<br />    


1. Install required Packages
   
   Ensure that the system has essential packages like gcc, glibc, make, wget, and openssl installed, there are more packages need to be installed.    :
   
   		dnf install httpd php gcc glibc glibc-common gd gd-devel make net-snmp unzip wget
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/odDHSSA.png" height="80%" width="80%" >
<br />    
