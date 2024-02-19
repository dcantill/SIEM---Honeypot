<h1>SIEM - Honeypot</h1>

<h2>Description</h2>
Project consists of a simple PowerShell script that walks the user through "zeroing out" (wiping) any drives that are connected to the system. The utility allows you to select the target disk and choose the number of passes that are performed. The PowerShell script will configure a diskpart script file based on the user's selections and then launch Diskpart to perform the disk sanitization.
<br />


<h2>Languages and Utilities Used</h2>

- <b>PowerShell ISE</b> 
- <b>Remote Desktop Connection</b>
- <b>Microsoft Azure</b>
- <b>Microsoft Sentinel</b>
- <b>IP Geolocation API</b>
- <b>Event Viewer</b>
- <b>Windows Defender Firewall</b>

<h2>Environments Used </h2>

- <b>(RDP) Windows 10 Pro</b> (22H2)
- <b>Windows 11 Pro</b> (23H2)

<h2>Project Walk-Through:</h2>

<p align="center">
Launch Microsoft Azure on Host PC: <br/>
<img src="https://i.imgur.com/AgrPLy5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
 <br />
 <br />
Create Virtual Machine:
<br />
<img src="https://i.imgur.com/LRxlort.png" height="25%" width="25%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure Settings 1: <br/>
<img src="https://i.imgur.com/SVgEBAL.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure Settings 2: <br/>
<img src="https://i.imgur.com/i5SEMA9.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Set Up VM Username and PW: <br/>
<img src="https://i.imgur.com/ltzMA6X.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a New Network Security Group: <br/>
<img src="https://i.imgur.com/tNpLT2v.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Allow Anyone To Ping the VM: <br/>
<img src="https://i.imgur.com/PUHceZR.png" height="75%" width="75%" alt="Disk Sanitization Steps"/>
<br />
<br />
Launch the Windows 10 Pro Image VM: <br/>
<img src="https://i.imgur.com/hgIHINd.png" height="75%" width="75%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open Log Analytics Workspace On Azure on Host PC:  <br/>
<img src="https://i.imgur.com/MdRSGpC.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a New Workspace: <br/>
<img src="https://i.imgur.com/zJRqcyx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open Microsoft Defender for Cloud:  <br/>
<img src="https://i.imgur.com/h4kiTJu.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Configure to Store All Raw Data:  <br/>
<img src="https://i.imgur.com/FE24dYo.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Connect to the VM Workstation:  <br/>
<img src="https://i.imgur.com/DTNmsam.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/NOE48eE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open MS Sentinel on Host PC:  <br/>
<img src="https://i.imgur.com/eXCQuE7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add MS Sentinel to the workspace:  <br/>
<img src="https://i.imgur.com/ar30rRX.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Copy the Public IP Address of the VM Workstation:  <br/>
<img src="https://i.imgur.com/TOxHGDV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/sxk5u7B.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open RDP on Host PC to connect to the VM Workstation w/ Username + PW:  <br/>
<img src="https://i.imgur.com/J2bNE6k.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open Event Viewer to view Windows processes on VM:  <br/>
<img src="https://i.imgur.com/2ntNvkn.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Attempt to login again, however, enter incorrect credentials:  <br/>
<img src="https://i.imgur.com/fLIl7TO.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
These "failed" attempts will identify as "Audit Failure" with the code "4625," future login attempts from brute forcers around the world will register as the same code:  <br/>
<img src="https://i.imgur.com/QIJgBHF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/cmmFYng.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
Disable the Windows Firewall on VM so it can be pinged publicly:  <br/>
<img src="https://i.imgur.com/GmN9oEe.png" height="25%" width="25%" alt="Disk Sanitization Steps"/>
<br />
<br />
Disable the Windows Firewall on VM so it can be pinged publicly:  <br/>
<img src="https://i.imgur.com/GmN9oEe.png" height="25%" width="25%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/JUpsfSq.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/z16kebh.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/Tv1xeTB.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<img src="https://i.imgur.com/FBosipH.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run Powershell ISE on VM Workstation + Add New Script:  <br/>
<img src="https://i.imgur.com/FrqD7HQ.png" height="25%" width="25%" alt="Disk Sanitization Steps"/>
<br />
<br />
Paste the Script "Security_Log_Exporter.ps1":  <br/>
<img src="https://i.imgur.com/Qkhycz1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add in your unique API key into the script:  <br/>
<img src="https://i.imgur.com/hdVlVQD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/Q4gZpXk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Save the Script onto Desktop:  <br/>
<img src="https://i.imgur.com/oUXyydG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run the script and go to C:\ProgramData\$($LOGFILE_NAME) on the VM to access the log file login attempts are pasted to:  <br/>
<img src="https://i.imgur.com/U2ITVaJ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/7wtweCD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/i9sZWYn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Copy the Notepad on the VM and paste it into a Notepad on the Host PC:  <br/>
<img src="https://i.imgur.com/v38roHM.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Save the Notepad on the Host PC to the desktop:  <br/>
<img src="https://i.imgur.com/sZdcjnL.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create a custom log from the notepad note on the Host PC and route it from the log on the VM:  <br/>
<img src="https://i.imgur.com/xPA6sWm.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/bmCgzQN.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Copy and paste the "Query_Log_Organizer" and run:  <br/>
<img src="https://i.imgur.com/CUIfxcV.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Open MS Sentinel and Create a new workbook:  <br/>
<img src="https://i.imgur.com/1jUOPkE.png" height="50%" width="50%" alt="Disk Sanitization Steps"/>
<br />
<br />
Add a new query and run "Query_Log_Organizer":  <br/>
<img src="https://i.imgur.com/FXH9DVk.png" height="15%" width="15%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/Yug7svW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Now wait 24 hours for attackers to attempt to brute force access the VM:  <br/>
<img src="https://i.imgur.com/FXH9DVk.png" height="15%" width="15%" alt="Disk Sanitization Steps"/>
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
