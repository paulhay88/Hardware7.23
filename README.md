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

![sysprep](https://user-images.githubusercontent.com/26419649/37391766-12a247f8-27d1-11e8-969a-18ae568876b9.png)

2. then just type Sysprep
3. Select Generalize as it will remove all unique information about this PC so that when it is run on another PC it just coallates the corect information into the right places aso as to avoid Hardware or dependey failure.
4. Select Shutdown otherwise it will restart the OOBE

![sysprep2](https://user-images.githubusercontent.com/26419649/37391783-220c684a-27d1-11e8-9338-b52706bde318.png)

5. Sysprep didn't work.

![sysprepshit](https://user-images.githubusercontent.com/26419649/37391796-3305b55c-27d1-11e8-8844-c6d982f8ac72.png)

What follows is a series of attempts to resolve this issue
  1. I read the log file to see what i could find

![errorlist](https://user-images.githubusercontent.com/26419649/37391696-d1c75b10-27d0-11e8-8b8f-2e6efdad3431.png)

  2. I tried running updates - did nothing
  3. Many forums keep pointing to editing the Registry and deleting the "Upgrade" portion of the HKEY_LOCAL_MACHINE\SYSTEM\Setup\ registry. But alas i did not have this in my registry.
  4. Then I saw this, and thought to myself "Well Mr T-Rex you and your modest arms might just help me yet"

![mtt-rex](https://user-images.githubusercontent.com/26419649/37391965-c8e17656-27d1-11e8-9a23-df15e0a030bc.png)

And then this started happening

![removing apppackages](https://user-images.githubusercontent.com/26419649/37392231-701af62c-27d2-11e8-9c2a-4c5468aa8aaf.png)

......It's taking a while. It seams to have worked

![itworked](https://user-images.githubusercontent.com/26419649/37392652-9e7ace56-27d3-11e8-8b9d-dba853c73b45.png)

.....But now this is taking a while

So it shutdown and i stupidly started it again to only realise it was reset and was at a fresh state, this is apparently where you need to export the iso so that it can be imported to the server. Lesson learned. 
Exporting takes a while. 

![export](https://user-images.githubusercontent.com/26419649/37441188-fac220c4-2864-11e8-826c-2da69a7d1d09.png)

Image expoted to a file then I tired importing it as a .ova file but that didnt work so then i learnt that it had to be extracted, so i used 7-zip and unzipped the file to find a set of .vmdk files obviously one being the current back up and the other being a blank disc.

![extractova](https://user-images.githubusercontent.com/26419649/37441217-1c62722e-2865-11e8-8d0b-de5e69a96318.png)

Now was the challenge of converting it, one way I followed led me to a dead end as it only was usable for a certian set of distrabutions but then I found a forum that said there was a very simple way using CMD to convert the file to a .vdi.

![vmdkcovrsiontovdi](https://user-images.githubusercontent.com/26419649/37441258-646bccf0-2865-11e8-9fdd-9e816380bcb7.png)

What this does is copies the the current drive and reformats it to vdi, it allows you to specify the new name, location and format of the drive.

![looksgood](https://user-images.githubusercontent.com/26419649/37441300-9d89acaa-2865-11e8-829a-57201c349a73.png)

then I loaded the vdi into the server as an alternate harddrive.

![newvdi no warning sign](https://user-images.githubusercontent.com/26419649/37441357-ef274e46-2865-11e8-8a81-a650d4b67b69.png)

It's called new because when I formatted it, it was called new and after you format it if you change thew name the drive doesn't work because the UUID is set to the original name.

![vdi insata](https://user-images.githubusercontent.com/26419649/37441387-109a42a4-2866-11e8-9164-366be89d0f2a.png)

#### Part 2
I installed WDS on installation
1. Dear god how wrong I was to think that was all I needed to do.
2. So i set up ADDS, DHCP, DNS and NTFS
3. In the DHCP i had to set the Scope

![scope](https://user-images.githubusercontent.com/26419649/37810862-893db046-2ebb-11e8-8809-88e8cef5789e.png)

Do not have the server IP in the Scope
4. Inside the 'Server Options' tick '060 PXE Client' and set the String value as the IP address less the last part. eg If your Server's IP is 192.168.1.25, drop the .25. 
5. Also 'Activate' the DHCP
6. In the DNS I set the Server name as "Server".

#### Part 3 
Once the syspreped machine is ready an the Server has been configureed correctly You run the Client machine and hit the boot options for LAN and wait for the PXE to connect and take you to a screen where you have the option to Capture or Boot and Image, Select Capture.
This process can take a while.

![capture](https://user-images.githubusercontent.com/26419649/37810880-a3b9a59c-2ebb-11e8-8f4b-584398d4ef20.png)

#### Part 4
Instead of running Dban, I created a new machine with no image disc, and a black drive then made the connection to the system as internal and loaded the machine and pressed F12 and then waited for the PXE server to connect and ofer me the boot Image to load and then selected it.
So this was there was litterally no trace of any opperating system near this machine and it still boted into PXE and the WDS and went through to the configuration
I ran Dban in the last Lab refer last Lab for screenshots if needed.

#### Part 5
1. The following part didn't work and is mearly my observations on what I was attempting at that time.
I had the image set as a VDI and was able to get the server ready for deployment but i couldn't mount the boot image because i couldn't capture it.
I had the AD DS, DHCP, DNS and an NTFS stroage device ready to go

![wds](https://user-images.githubusercontent.com/26419649/37447634-d6b0601a-2887-11e8-8502-5f9c20a2ed7a.png)

I had the windows deploymwnt system ready I just need help with the DISM and then I can deploy the iso through the server but i cant mount the boot or install images
2. Below is the Image from the WDS installing the Windows configuration onto a completly blank machine.

![captured deployed](https://user-images.githubusercontent.com/26419649/37810845-734df912-2ebb-11e8-8113-8413f993faa7.png)

#### Things I've learnt and had to fix during the deployment.
So one of my problems was that I was mounting the wrong image and couldn't find the boot file nor the install file. but after some help I got the right file in the right place.
1. Side note - If the system is relying on older hardware a boot.wim file from a Windows 7 image will work better as has more of the older drivers installed in it. 
Make sure all your extra drives are formated


# LAB 3 - Powershell
## Session 6
1. Create a script that will scan and parse client machines event logs [1][2][3] for ‘Error’ event types within the last seven days of the current date. Do not used hard-coded information. Save the results to a file then clear the logs

2. Create a script that executes sfc.exe /scannow to generate a log file. Scan and parse the log file for messages such as “Cannot repair member… “,”Repaired file…”, “Repairing corrupted…”, etc. and save them to a new text file


I used the Get-EventLog command
Get-EventLog has a few arguements
   [-LogName] <String>
   [-ComputerName <String[]>]
   [-Newest <Int32>]
   [-After <DateTime>]
   [-Before <DateTime>]
   [-UserName <String[]>]
   [[-InstanceId] <Int64[]>]
   [-Index <Int32[]>]
   [-EntryType <String[]>]
   [-Source <String[]>]
   [-Message <String>]
   [-AsBaseObject]
   [<CommonParameters>]

For the Majority I set them as variables and called them to make the script more dynamic and have more control and have every veriable together.

$logPath = "C:\Users\Administrator\Desktop\log.txt"
$computer = "SERVER2012"
$date = Get-Date
$sevenDays = New-Object System.TimeSpan 7,0,0,0,0
$then = $date.Subtract($sevenDays)
$EventLog = Get-EventLog -LogName System -ComputerName $computer -After $then -Before $date -EntryType Error | Out-File $logPath
Clear-EventLog -LogName System

For the scan I used variables to set the Logs, the Fail / search criteria then scanned the drive in this case it was C;/Windowas\\System32 \sfc.exe
I then created a variable of the CBS file which was an object then ised that object to fill the logs witht he words that are relevant in this case it was "repair" and "fail"

$scanPath = "C:\Users\Administrator\Desktop\scan.txt"
$repairLog = "C:\Users\Administrator\Desktop\repair.txt"
$failLog = "C:\Users\Administrator\Desktop\fail.txt"
$CBSFileLocation = "C:\Windows\Logs\CBS\CBS.log"
$repair = "Repair"
$fail = "fail"
&C:\Windows\System32\sfc.exe /scannow
$ScanX = Get-Content $CBSFileLocation
$ScanX | Out-File $scanPath
Select-String -Path $scanPath -Pattern $repair | Out-File $repairLog
Select-String -Path $scanPath -Pattern $fail | Out-File $failLog

But for fun sakes I built them as one script which looks like this

$logPath = "C:\Users\Administrator\Desktop\log.txt"
$scanPath = "C:\Users\Administrator\Desktop\scan.txt"
$repairLog = "C:\Users\Administrator\Desktop\repair.txt"
$failLog = "C:\Users\Administrator\Desktop\fail.txt"
$computer = "SERVER2012"
$CBSFileLocation = "C:\Windows\Logs\CBS\CBS.log"
$date = Get-Date
$sevenDays = New-Object System.TimeSpan 7,0,0,0,0
$repair = "Repair"
$fail = "fail"
$then = $date.Subtract($sevenDays)
$EventLog = Get-EventLog -LogName System -ComputerName $computer -After $then -Before $date -EntryType Error | Out-File $logPath
Clear-EventLog -LogName System
&C:\Windows\System32\sfc.exe /scannow
$ScanX = Get-Content $CBSFileLocation
$ScanX | Out-File $scanPath
Select-String -Path $scanPath -Pattern $repair | Out-File $repairLog
Select-String -Path $scanPath -Pattern $fail | Out-File $failLog
echo "Done!!"


## Session 7
Create a scheduled task[6][7] that executes a Windows Powershell script as soon as a user logs onto the computer. The script must execute the following : 
ccleaner[9] (with /AUTO) 
cleanmgr (with /sagerun:1. You need to do a /sageset:1 first) 
defraggler[8] (as /QD on C:). 
Once the above tasks have completed, the script must then kill any process identified by a blacklist (you specified) that should not be running. 
Document the details of the scheduled task. 

The first thing you need to do is open up Task Scheduler 


![image](https://user-images.githubusercontent.com/26419649/39668137-7a15676e-5119-11e8-8d46-e0df911ef302.png)
set a new task to run on boot.
Download all the software needed
open up powershell and set the conditional run settings eg. sageset 

I used the following script to achieve the task

#Starts CCleaner, has the SAGESET there as well as the run incase you want to change it, also starts the Defragler Verbosly so you can watch the percentage of the task as its happening, and I wasn't entirely sure about the black list so I explicitly told the system to Get-Process and stop Ccleaner to achieve the goal of the task.
Start-Process "C:\Program Files\CCleaner\CCleaner.exe" -ArgumentList "/AUTO"
#&Cleanmgr.exe /SAGESET:11
&Cleanmgr.exe /SAGERUN:11
Start-Process -FilePath "C:\Program Files\Defraggler\df64.exe" -ArgumentList "c: /qd" -Verbose
Get-Process | Where-Object {$_.FileName -eq "CCleaner" } | Select-Object -First | Stop-Process

## Session 8-9
To download the AD modules run 
Import-Module ActiveDirectory

After which you can use the AD commands
Create a script that contains the following Powershell functions: 
1. Get-Computer-List – returns a list of computers, registered in the Active Directory, by their computer name.  

function GET-COMPUTER-LIST {
param ([str] $filter = "LAB")
$list = Get-ADComputer -Filter $filter -Properties name | Format-List name
return $list
}

2. Get-Computer-MAC – returns the MAC address of the remote computer using a computer name from the Get-Computer-List function. 

function GET-MAC {
param ([str] $filter = "LAB")
GET-COMPUTER-LIST($filter) 
foreach($Computer in $list) {
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName $Computer | Select MACAddress
}
}

3. Get-Computer-IPaddress – returns the IP address of the remote computer using a computer name from the Get-Computer-List function. 

function GET-IP {
param ([str] $filter = "LAB")
GET-COMPUTER-LIST($filter)
foreach($Computer in $list) {
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName $Computer | Select IPAddress
}
}

4. Send-WOL – send a Wake On LAN message to the destination computer using a MAC from the GetComputer-MAC function.  

##NOT MY CODE!!!!!!!!!!!
## THIS is an example of a SEND WOL funtion i could not figure the MAC part of sending WOL but this works fine
function Send-WOL {
    param (
        [parameter(
            mandatory=$true,
            position=0,
            ValueFromPipeline=$true,
            ValueFromPipelineByPropertyName=$true)]
        [ValidateLength(17,17)]
        [ValidatePattern("^([0-9A-F]{2}[:-]){5}([0-9A-F]{2})$")]
        [array]$MACAddress
    )
    foreach ($MAC in $MACAddress) {
        try {
            $MAC = $mac.split(':') | %{ [byte]('0x' + $_) }
            $UDPclient = new-Object System.Net.Sockets.UdpClient
            $UDPclient.Connect(([System.Net.IPAddress]::Broadcast),4000)
            $Packet = [byte[]](,0xFF * 6)
            $Packet += $MAC * 16
            Write-Verbose ([bitconverter]::tostring($Packet))
            [void] $UDPclient.Send($Packet, $Packet.Length)
            Write-Output "WOL command sent to $MAC"
        } catch [system.exception] {
            Write-Output "ERROR: Unable to send WOL command to $MAC"
        }
    }
}

5. Send-Shutdown – send a shutdown request to the remote computer using the computer name from the Get-Computer-List function. 

function SHUTDOWN {
param ([str] $filter = "LAB23")
GET-COMPUTER-LIST($filter)
foreach($Computer in $list) {
Stop-Computer -ComputerName $Computer -Credential -Force -Confirm
}
}

6. Get-Computer-CPU – returns the CPU name/type of the remote computer using a computer name from the Get-Computer-List function.

function GET-CPU {
param ([str] $filter = "LAB")
GET-COMPUTER-LIST($filter)
foreach($Computer in $list) {
Get-WmiObject -Class win32_processor -ComputerName $Computer | select Name
}
}

## Session 10
### e
Create a script that will read in a CSV file and bulk create user accounts in Active Directory. This is a common activity where rooms of computers or machines are refreshed at the end of a defined period (term, semester, year, etc). You can use the Windows server installation prepared during Session 3.  Include at least the following user related information – Name, Firstname, Password, Office, Telephone and Department

$UserList=IMPORT-CSV C:ImportsUsers.csv
FOREACH ($Person in $UserList) {
#Build Username from First name and Last Initial
$Username=$Person.Firstname+$Person.Lastname.substring(0,1)
#Put our Domain name into a Placeholder, who wants all that typing?
$Domain=’Server.local’
#Build the User Principal Name Username with Domain added to it
$UPN=$Username+$Domain
#Create the Displayname
$Name=$Person.Firstname+” “+$Person.Lastname
#Create User in Active Directory
NEW-QADUSER –FirstName $Person.Firstname –Lastname $Person.Lastname –Name $DisplayName $Name –SamAccountName $Username –UserPassword ‘1NewPassword’ –UserPrincipalName $UPN –Name $Name –ParentContainer ‘Blueville.local/Division/Contoso’
}

### f
Create a script that will generate a text file of Active Directory users but not computers that have been inactive for at least 180 days
Get-ADUser –filter * | Where { $_.LastLogOnDate –lt (Get-Date).AddDays(-180) } | Out-File $fileLocation.txt



## Session 13
Choose one of the following candidate solutions to construct a private cloud: 
  Pydio - https://pydio.com/en 
  ownCloud - https://owncloud.org/ 
  Seafile - https://www.seafile.com/en/home/ 
  Cozy - https://cozy.io/en/ 
  Syncthing - https://syncthing.net/ 
  OpenStack - https://www.ubuntu.com/download/cloud 
 
Install the chosen candidate and setup a private cloud between two computers – one acting as the cloud server, the other as the client. Verify the cloud solution works. Describe the type of cloud solution you have created and the rationale for the chosen solution.

I chose Seafile
this is the Server version I downloaded 

![image](https://user-images.githubusercontent.com/26419649/40691321-7cac073c-63ff-11e8-840f-be7450750229.png)

and this was the Client version I downloaded

![image](https://user-images.githubusercontent.com/26419649/40691343-95828c90-63ff-11e8-8860-cbea967b2594.png)

What I have created is much like a personal Github, a space for people to load, download and view their work on any device at anytime.
This can allow for collaberators to work remotely from around the world and have an upto date sync'd version of the current work.

What Seafile allows you to do is install client syncrniose tools to your phone or pc regardless of its OS and be able to share files at anytime.
  This allows the admin to allocate permisions and files to specific groups or individual people. 
  This also alows Time stamps of work to be created so that changes that have been made can be unmade incase some error in the code has occured
  #### Issues I encountered setting it up
 Firstly It needs Python 2.7.11 32 bit to run & requires PATH enviromental variables to be added in the C;\Python 27

###### ServerSide
1) Then a Server File needed to be set up on the C:\ and have the server installed in there
2) click the run.bat file inside the unzipped server file 
3) Choose the disk
4) Add an Admin account by right clicking on the tray icon 

![image](https://user-images.githubusercontent.com/26419649/40694379-64cee0ec-6410-11e8-88b7-3d1df1373e78.png)

5) Open up the conf/ccnet.conf file with notepdd++ and edit the SERVIC URL to have your IP address before the port :8000

![image](https://user-images.githubusercontent.com/26419649/40694405-829557e6-6410-11e8-988d-9f3085657cce.png)

6) restart SeaFile
7) Open a browser and connect using the URL and admin login credentials

###### ClientSide
1) Install the Client tool on the device u wanted in this case its the 6.1.8 version for Windows

![image](https://user-images.githubusercontent.com/26419649/40694015-80187c98-640e-11e8-9169-93c3f0b87bf7.png)

2) Choose File location for folder & accept permissions then install
3) Select User Name and Add an Account 

![image](https://user-images.githubusercontent.com/26419649/40694059-c54a0034-640e-11e8-8128-5951cf9971bd.png)

4) Connect and share 

![image](https://user-images.githubusercontent.com/26419649/40691274-36023310-63ff-11e8-9d46-8565c11fe1ac.png)

I choose Seafile because it had very good independant reviews and wanted to see if it was as easy as I heard.
It was, very easy. using the manual to install and following the simple steps it waas a breeze.

Seaview allows any person on any platform to collaberate thats the main reason I like it and would recomend it. I have created a limited use case for the Cloud system but it can be scalled very easily and managed just as easily.


## Session 14 
Compare the following mostly commercial cloud solutions. 
1) Ubuntu MAAS/openStack  
2) oVirt 
3) Amazon
4) Microsoft Azure 

#####  Ubuntu MAAS/openStack
MaaS - Metal as a Service provided by Ubuntu
Ubuntu's MaaS is a zero touch deployment system that is available for windows and Linux Distros
Ubuntu's MaaS can create an instance of a machine on an actual server as fast and easily as any VM. What this does is allows the user to have all the versatility of the cloud with the raw power of an actual metal service. Once created and used they are just as easily removed and deleted as the yare created.
Essentially MaaS acts as a PXE server that is intergrated with other technologies. The main tool the MaaS uses is Juju.
Juju is an application for the deployment, service and modeling of MaaS servers. This tool helps configuration and scaling of software.
Juju's use Charms, Charms are aplications/software used in the deployed instance. They can be configured and matched to related infrastrutre by using modeling and then relationships are attributed to the Charms and their use creating Bundles.
Budles are whole deployment systems that can be rolled out at a touch of a button, They are matched appliucations for specific reasons that can me matched with other budles to roll out entire infrustruture based or related software. 
eg If you want a Web Server and client database with Finances and Auditing available you can deploy two - three bundles that will instantly work together and have the available infrastruture you require.

#####  oVirt

#####  Amazon

#####  Microsoft Azure

##### Summary
