<h1>AD Server Setup - Active Directory</h1>

<h2>Description</h2>
Project is a simple walk through of setting up a Domain Controller on a Hypervisor.
<br />


<h2>Programs Used</h2>

- <b>VirtualBox</b> 

<h2>Environments Used </h2>

- <b>Windows Server2019</b> 
- <b>Windows Server2022</b>
  
<h2>Setup walk-through:</h2>

<p align="center">
download oracle virtualbox which is what you're going to use to run your virtual machines(VMs). Navigate to microsoft evaluation center in your web browser and download the 64bit english version of windows 10 and the windows server 2019 isos these are the operating systems you are going to be using on are VMs. They automatically save to your downloads folder. You may want to rename them to easily tell them apart. Install virtualbox and set up your first VM: <br/>
<img src="https://i.imgur.com/Rj7ioH2.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />

<p align="center">
Name your domain controller: <br/>
<img src="https://i.imgur.com/JPkBPB9.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Select the windows server iso and check skip unattended guest:  <br/>
<img src="https://i.imgur.com/WZ2DF7M.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Next you're going to be allocating some of your computers resouces for the VM. If you don't have a very good processor you can leave it at one core. Things may go a little slower but its fine. Then allocate some ram 2GBs is good enough. If the computer your using is on the higher end, then allocating more will make this process run a little faster: <br/>
<img src="https://i.imgur.com/t3ELCs4.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
If the computer your using is on the higher end, then allocating more will make this process run a little faster. Lastly, you allocate some storage space and the VM will be created:  <br/>
<img src="https://i.imgur.com/XEM8U0o.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Right click on that VM once its created and you are going select settings:  <br/>
<img src="https://i.imgur.com/Xx8weeW.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Under general you're going to select the advanced tab. If you select bidirectional for shared clipboard and Drag'n'Drop, this will allow you to move files from your computer onto the VM. This step is also optional:  <br/>
<img src="https://i.imgur.com/ZKtxItU.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Give this virtual machine two network adapters one NAT to connect to the outside internet and the second Internal Network to connect to the local network within virtual box:  <br/>
<img src="https://i.imgur.com/qFRF16R.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Start your VM:  <br/>
<img src="https://i.imgur.com/2RmOXOD.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
select the server 19 desktop experience which will give a regular windows desktop and user interface as opposed to doing everything through command prompt:  <br/>
<img src="https://i.imgur.com/NJK4kLU.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Then select custom install then click next:  <br/>
<img src="https://i.imgur.com/FJPneN3.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Click next:  <br/>
<img src="https://i.imgur.com/Vpbecp5.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Once set up is complete it will have you create a password for the Administrator account. Make it something easy to remember:  <br/>
<img src="https://i.imgur.com/c3TQsH5.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Then it will prompt press ctrl, alt, del to login select it from the VirtualBox's input drop down menu. Then log in with the password you just created:  <br/>
<img src="https://i.imgur.com/BrKQaku.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Next you're going to install guest editions for a smoother experience select "insert guest editions CD image" from VirtualBox's Devices drop down image:  <br/>
<img src="https://i.imgur.com/afzN72V.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Navigate to the cd drive from the file manager and run the amd64 version of guest addition. Click next through the prompts until the install starts. The select reboot later once the install completes. Shutdown your VM from the start menu:  <br/>
<img src="https://i.imgur.com/ta8JxZt.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Next to set up the IP addressing you are going go to network and internet settings or click the little computer icon on the right side of your VMs task bar. then click change adapter settings identify which adapter has internet access. Right click the adapter select status:  <br/>
<img src="https://i.imgur.com/wRifrge.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Click the detail button:  <br/>
<img src="https://i.imgur.com/O3kZFmM.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Look for the IPv4 address. One will have an address assigned by a DHCP server:  <br/>
<img src="https://i.imgur.com/dYh6oki.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
the other will have an APIPA address. When the device is unable to reach a DHCP server on internet, it is assigned an APIPA IP address ranging from  169.254.0.1 to 169.254.255.254. Label the adapters so that you can easily tell them apart:  <br/>
<img src="https://i.imgur.com/NA5rt0U.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Right click the local adapter, select Internet Protocol Version 4(TCP/IPv4)then click properties:  <br/>
<img src="https://i.imgur.com/cbRg6db.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Your going to set the IP address to 172.16.0.1, subnet mask to 255.255.255.0 leave the gate way and use the loop back address for the DNS server. This VMs is going to act as a DNS serve for the client VMs we set up. Restart the VM:  <br/>
<img src="https://i.imgur.com/tHC22FO.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
In the server manager select add roles and features:  <br/>
<img src="https://i.imgur.com/lPeS9Eh.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
click next until you get to server selection select there should only be one server on the list select it and click next under select server roles select active directory domain services:  <br/>
<img src="https://i.imgur.com/gga2Cd0.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
Click add features click next through to the install button:  <br/>
<img src="https://i.imgur.com/XLWCuqv.png" height="80%" width="80%" alt="Setup walk-through"/>
<br /> 
<br />
In the top right there will be a yellow trouble flag in notifications. click it then select promote the server to a domain contoller:  <br/>
<img src="https://i.imgur.com/72Fsph3.png" height="80%" width="80%" alt="Setup walk-through"/>
<br />
<br />
check add new forest name it whatever you want then click next. create a password you'll remember click next. As the following screens auto populate click next until you reach the install screen then click install. The VM will restart:  <br/>
<img src="https://i.imgur.com/5preGAS.png" height="80%" width="80%" alt="Setup walk-through"/>
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



