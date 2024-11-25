# Creating-LVM-Disk-Space-
The goal of this lab is to teach you how to create and manage LVM (Logical Volume Manager) disk space on a virtual machine (VM) instance in Google Cloud Platform (GCP). By the end of this lab, you will be able to add additional disks to a VM, set up LVM, and create logical volumes for data storage. 

To understand the use LVM we need to comprehend three main components, they are interconnected and together make what we call a Logical Volume, here are the three components:

Physical Volume: It is simply the physical storage devices, whether it is SSD or HDD drives. 
 

Volume Group: It is a pool which is comprosed of physical volumes.

Logical Volume: When the VG created, we can finally creates a logical volume, you can create one or more logical volumers from a single volume group. 

Here is a diagram for this relationship:


![lvmsetup](https://github.com/user-attachments/assets/8f99d2d1-141e-46f0-b4b1-33b06719b1a1)




For this demonstration purpose, I will use Google Cloud Platform. The concept will apply in any platforms and distributions.

If you need help on how to create a Ubuntu VM, please click [here](https://cloud.google.com/compute/docs/create-linux-vm-instance)

After create a VM, please add an additional disk so we can work on this lagb. Here is a [link](https://cloud.google.com/compute/docs/disks/add-persistent-disk) help you to create a disk for you to use. 


Here are the following steps:

  1. Run the "lsblk" command, the new disk should appear as /dev/sdb (or another name depending on your configuration)

			lsblk

<p align="center"> </p>
<img src="https://imgur.com/L7s1AqT.png" height="80%" width="80%" >
<br /> 

2. Install LVM Tools
   
   Before setting up LVM, you need to install the necessary tools. Run the following command to install LVM utilities:
   
   	     sudo apt update
   	     sudo apt install lvm2
3. Prepare the New Disk for LVM
   
   Create a Physical Volume (PV) on the new disk. Replace /dev/sdb with your disk name if necessary: :
   
   		sudo pvcreate /dev/sdb 
   

		
<p align="center"> </p>
<img src="https://imgur.com/QQyFmwD.png" height="80%" width="80%" >
<br />    


4. Create a Volume Group (VG)
   
  	A volume group pools physical volumes into a single storage space. You can name the volume group as you like (e.g., lvm-vg)  :
   
   		sudo vgcreate lvm-vg /dev/sdb
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/x2pk0k6.png" height="80%" width="80%" >
<br />    


5. Create a Logical Volume (LV)
   
   Logical volumes are the actual partitions you will use. Here, we will create a 5GB logical volume named lvm-lv :
   
   		sudo lvcreate -L 5G -n lvm-lv lvm-vg
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/jCCxAs9.png" height="80%" width="80%" >
<br />    


6. Format the Logical Volume 
   
   Format the logical volume with a ext4 file     :
   
   		sudo mkfs.ext4 /dev/lvm-vg/lvm-lv





7. Mount the Logical Volume
   
   Create a mount point directory :
   
   		sudo mkdir /mnt/lvm-data
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/b1SKBbD.png" height="80%" width="80%" >
<br />    

8. Mount the logical volume to the directory
   

   
   		sudo mount /dev/lvm-vg/lvm-lv /mnt/lvm-data
   
   		

		
  
9. Verify that the logical volume is mounted correctly
   
   
   		df -h 
   
   		

		
<p align="center"> </p>
<img src="https://imgur.com/zRwqfcB.png" height="80%" width="80%" >
<br />    


10. Make the Mount Persistent


    Open the /etc/fstab file
    
		sudo nano /etc/fstab

12. Add the following line at the end of the file:

		/dev/lvm-vg/lvm-lv /mnt/lvm-data ext4 defaults 0 2		
