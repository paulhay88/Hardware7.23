# LAB 1 – BACKUP AND RECOVERY SYSTEMS
## Session 1
## Introduction The lab focuses on Backup and Recovery systems for the enterprise
Details The lab work must be completed and handed in at the end of each session. 
The first session will be an evaluation of the current state of enterprise backup software. The second session will be an investigation into system backup and recovery methods. 
Required Document the activities and observations for the following sessions. 
Session 1 
1. Use the Internet to locate and document, with suitable sources, software used for enterprise grade system backups and recovery – e.g Works with servers and “live” systems.
2. Compare the features of the above software. Comment on the features that sets this type of software apart from consumer grade software
3. Discuss the type of hardware used or required to facilitate the system backup software

### Suitable live system recovery tools
1.	Quest – Rapid / Live Recovery system
a.	Out of the four I found this one seems to be the best; it has a lot of live recovery features and is cloud based
b.	Can be taking recovery snap shots incrementally of your whole system every 5 minutes
c.	Has DRaaS in Azure
d.	Has universal recovery from single files to whole machines
2.	BackupAsssist
a.	Does BareMetal recovery
b.	Hyper-V, SQL and Exchange compatible
c.	 Cloud and onsite recovery
d.	Email reports & Alerts
3.	Acronis Backup 12.5 
a.	Has a single integrated solution for all backup and recovery
b.	Uses Acronis AnyData Engine
c.	Web based recovery console
d.	Automated testing to regularly test the protected data 
4.	EaseUS
a.	Does recovery – website is quite vague on detail
b.	Lost Partition recovery 
c.	Scans storage devices deeply for lost data 

Over all Quest Rapid seems to be the best mainly because of it’s easy to understand video that leads their website and is direct and to the point. Whereas other sites I had to dive for information that was essentially the same the only major notable feature from either of the other three was Automated testing of backed up data, was a good idea and should be adopted.

### Hardware
From my understanding these companies above all have onsite management servers that backup the data to either Cloud services or Local Drives. Each site has software requirements that tell you what you need to run their software in case you don’t wish to purchase their server. 

#### The Server Backup Manager (SBM) 5.12 release windows back up servers the requirements are:
##### Physical Memory
1 GB per open Disk Safe (concurrent backup/restores) with an additional 2 GB per terabyte of backups
##### CPU
2 cores minimum plus 1 core per concurrent backup/restore task
##### Free Disk Space
Minimum 10 GB (100 GB+ recommended)
##### Primary Storage Types
Directly Attached Storage, Network Attached Storage including: 
IDE, SATA, SCSI, SAS, ISCSI, Fibre Channel, Dynamic Disks (Software RAID), Hardware RAID, Solid State Drives (SSD), Windows Network Shares, CIFS
##### Disk Safe Storage
Minimum 1x Primary Storage* (Recommended 2-4x Primary Storage of Servers) *with compression enabled

#### Vaem is a company I’m not too familiar with at all but they have Windows based servers as well:
##### Physical Memory
4 GB RAM plus 500 MB RAM for each concurrent job.
1. 1.5 GB RAM for file to tape backup for each 1,000,000 files
2. 2.6 GB RAM for file restore for each 1,000,000 files
3. 1.3 GB RAM for catalog jobs for each 1,000,000 files
##### CPU
x86-64 processor (is all it says nothing more specific)
##### Primary Storage
2 GB for product installation and 4.5 GB for Microsoft .NET Framework 4.5.2 installation. 10 GB per 100 VM for guest file system catalogue folder. 

#### For a Linux Distribution I found R1Soft:
Which obviously uses Linux distribution which are 
(64-bit distributions only) – RedHat Enterprise Linux 5.5+, CentOS 5.5+, Oracle Enterprise Linux 5.5+, Ubuntu 10.04+, Debian Squeeze, Novell SUSE Enterprise 10SP2+
##### Physical Memory
1 GB of RAM per open Disk Safe (concurrent backup/restores) with an additional 2 GB RAM per terabyte of backups
##### CPU
2 cores minimum plus 1 core per concurrent backup/restore task
##### Primary Storage
Directly Attached Storage Including: IDE, SATA, SCSI, SAS, ISCSI, Fibre Channel, Dynamic Disks (Software RAID), Hardware RAID, Solid State Drives (SSD)
##### Disk Safe Locations
Directly Attached Storage, Network Attached Storage Including: IDE, SATA, SCSI, SAS, ISCSI, Fibre Channel, Dynamic Disks (Software RAID), Hardware RAID, Solid State Drives (SSD), NFS

##### For smaller and personal set ups there are smaller options that are more suited to home/small business.
From scratch you can build a backup server with similar hardware devices 
1. 64bit Quad-Core CPU
2. 4GB DDR3
3. 32GB eMMC “SSD”
4. 3xUSB 3.0 + 1xUSB 3.0 C
5. Graphic
* HDMI + VGA
6. Realtek Gigabit LAN
With some software and you have yourself a small personal backup server.

## Session 2
1. Download a copy of the Winbuilder toolchain from the lab server.  
The distribution should include a copy of; 
  1. BuilderSE with the Win10PESE [3] project.
  2. ADK and DISM tools for the creation of the Win PE image.
  3. Rufus bootable removable media creator.

Steps to follow
1. Download and extract a copy of the MS Windows 10 operating system images with 7-zip – this should be available on the local drive or the Softlab server.
###### Screen Shots below
2. Extract the package and use the BuilderSE.exe to create a Client Recovery toolset. Make a list of the software and tools used for the recovery toolset and provide a rationale for tool selection. 
###### Tools list is below, followed by rational
3. Use the rufus tool to create a bootable USB stick and test it, or use Virtualbox to test the recovery image. 
###### I loaded it as an Image in a Virtual Box
But I did it on EIT's PC so I cant grab the scrrenshot right now. but will Load a running Iso image on Monday morning.

Once you have the tool extracted and you also have a copy of the iso ready to go, you have to set the source of the iso in the Source section, it is the second tab on the main right hand screen.
![source](https://user-images.githubusercontent.com/26419649/36832615-0bc9ab64-1d91-11e8-993b-89671519d1af.png)
then press play and it will automatically install a copy of the Recovery image into the projects folder in the WinBuilder folder and if you have Oracle Virtual Box installed when you run click on the image it will load a WinPE version on windows.
If you have the right image and the right mount the end result should look like this
![winpese envioment](https://user-images.githubusercontent.com/26419649/36832811-eff0773c-1d91-11e8-8545-fa62d7000339.png)

### Tools
#### DISM
Deployment Image Servicing and Management Tool
Orginally introduced in Win7 and Server08R2, it iis a tool that performs service tasks on Windows based installation/recover iso'd.  The main funtions are the mounting and unmounting of images and checking devices drivers as well as adding drivers to offline iso's .
#### ADK
Windows Assessment and Deployment Kit - The Tool Kit formally known as WAIK or the Windows Automated Installtion Kit.
Is a tool developed by Microsoft to deploy Windows images onto specific computers and systems, or to be used as a virtual image in VHD.
WAIK is a small build of a Windows Enviroment (Preinstallation) that can be booted from disk, USB or external drive. It's used to query, fix or replace whole desktop enviroments.
#### WinBuilder
This Software is specifically designed to help build customizable boot images from the Windows O/S.
The entire thing runs scripts that build/compile the right components for a basic to a very customizable and specific desktop enviroment.
Maintains "Projets" which are the images of the desktops so that they can be altred and adapted to a changing enviroment.
##### The 'Why'
Well its plainly obvious that Winbuilder is the major software piece here and when intergrated with the DISM and the ADK tools then deployed via Rufus to a USB make deployment of images to networked PC's much easier.
What it will also allow you to do is to create images for testing, so whether or not you are creating a backup image or a restore disc all these tools will halp you achieve this and to a larger cass make those images quite unique to the person/s that are using them. In a very quick and effiecnt manner the scripts rebuild the O/S to a base level with the specified Applications for that specific image.
The combination ov the above tools is really useful in so many ways to administrators that need to push iso's to end users or send disc/usb images to remote loactions or for safty sake (Storing the images offsite for insurance purpases).


## Sesion 3
1. Prepare a virtual machine with Windows Server 2012 (required for Sessions 4 & 5) and ensure the WDS and DHCP roles are included. (Disk 1) 
2. Prepare a second virtual machine with the MS Windows 10 OS. (Disk 2) 
3. Add an additional dynamic drive of 20GB to the MS Windows machine and format it. (Disk 3) 
4. [option 1] Download the live Clonezilla image from the Softlab FTP server.Boot up with the Clonezilla and proceed to capture the Windows 10 drive image and store it onto Disk 3. 
5. [option 2] Download a Macrium Reflect[4]. Use Macrium to capture and restore the Windows 10 drive image onto Disk 3.  
6. Boot the windows VM with dban[3] to wipe the Windows drive and confirm it is now “broken”. 
7. Restore the captured bare metal image and confirm it still works

The first 3 steps can be summed up in the following screenshot
![os disc](https://user-images.githubusercontent.com/26419649/37229846-49a64540-244a-11e8-8e98-6fd5d1bdfe3a.png)
Running CloneZilla had its moments with being slightly dificult at times but mainly because I was missreading the program which lead me to selecting the wrong drives and writing over the user with the blank disc.
![clonezilla2](https://user-images.githubusercontent.com/26419649/37230203-6800a566-244b-11e8-8d37-fc04d98f55fd.png)
And at another time the program was just not happy and did some weird stuff and at another stage it just lost itself in the load and just hung/stalled after 16 seconds.
![clonezilla6](https://user-images.githubusercontent.com/26419649/37230175-527f4738-244b-11e8-8fd5-12271477ccf9.png)
![clonezilla4](https://user-images.githubusercontent.com/26419649/37230127-32ba7e40-244b-11e8-9b20-dac8f29eaa5c.png)
but in the end i got it working 
![clonezilla7](https://user-images.githubusercontent.com/26419649/37230057-0502bc74-244b-11e8-96da-00b19d3969fa.png)
![clonezilla7-seamstobeworking](https://user-images.githubusercontent.com/26419649/37230087-1c95aea0-244b-11e8-9f35-f4506a29d186.png)
Running dban as a live disc in the win10 wasn't that fast wiped the disc at roughly 1GB a min 
After the disc ran and wiped the drive I removed dban and tried running it and there was a fatal error with no loadable media, so I deleted the drive (Mainly beacuse I couldn't figure out on VM how to select one drive over the other and loaded the system and Whalla it worked.
![clonezilla8-blankdiscloaded](https://user-images.githubusercontent.com/26419649/37230397-40c80d6c-244c-11e8-81c2-a958e5915b8a.png)

## Sesion 4 
1. Prepare the Windows client machine for capture using sysprep[1][2].  
2. Prepare the WDS server for receiving the image.  
3. Capture the image from the Windows client and store it onto the blank drive (refer to a) from Session 3).  
4. Boot up with dban[3] to wipe the Windows drive and confirm it is now “broken”.  
5. Deploy the captured Windows client image using the WDS and confirm it still works. 

#### Part 1
1. Bring up CMD and go to C: and then type %SystemRoot%\Syste32\Sysprep
2. then just type Sysprep
3. Select Generalize as it will remove all unique information about this PC so that when it is run on another PC it just coallates the corect information into the right places aso as to avoid Hardware or dependey failure.
4. Select Shutdown otherwise it will restart the OOBE
5. Sysprep Shits the BED

I cant go anyfurther with this iso sysprep isnt working .

#### Part 2
I installed WDS on installation 

#### Part 3 

#### Part 4
Disc cleared

#### Part 5
