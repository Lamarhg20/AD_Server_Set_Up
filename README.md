# AD_Server_Set_Up
Step 1 
download oracle virtualbox which is what you're going to use to run your virtual machines(VMs). Navigate to microsoft evaluation center in your web browser and download the 64bit english version of windows 10 and the windows server 2019 isos these are the operating systems you are going to be using on are VMs. They automatically save to your downloads folder. You may want to rename them to easily tell them apart. Install virtualbox and set up your first VM.

Step 2
 You're going to be using the first VM as your domain controller. This is where your going to have your active directory. Setting up the VM is mostly straight forward. Name your domain controller, select the windows server iso and check skip unattended guest. Next you're going to be allocating some of your computers resouces for the VM. If you don't have a very good processor you can leave it at one core. Things may go a little slower but its fine. Then allocate some ram 2GBs is good enough. If the computer your using is on the higher end, then allocating more will make this process run a little faster. Lastly, you allocate some storage space and the VM will be created. Right click on that VM once its created and you are going select settings. Under general you're going to select the advanced tab. If you select bidirectional for shared clipboard and Drag'n'Drop, this will allow you to move files from your computer onto the VM. This step is also optional. Give this virtual machine two network adapters one NAT to connect to the outside internet and the second Internal Network to connect to the local network within virtual box  

Step 3
Start your VM select the server 19 desktop experience which will give a regular windows desktop and user interface as opposed to doing everything through command. Then select custom install then click next. Once set up is complete it will have you create a password for the Admistrator account. Make it something easy to remember. Then it will prompt press ctrl, alt, del to login select it from the VirtualBox's input drop down menu. Then log in with the password you just created. Next you're going to install guest editions for a smoother experience select "insert guest editions CD image" from VirtualBox's Devices drop down image. Navigate to the cd drive from the file manager and run the amd64 version of guest addition. Click next through the prompts until the install starts. The select reboot later once the install completes. Shutdown your VM from the start menu.
