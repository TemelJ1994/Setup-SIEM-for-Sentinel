<h1>Setup SIEM for Sentinel</h1>



<h2>Description</h2>
In this project, I setup Microsoft Sentinel (SIEM) and connect it to a live virtual machine acting as a honey pot. I observe brute force attacks in real-time from across the globe. I used a custom PowerShell script to find the attackers Geo Data information and plot it on the Microsoft Sentinel Map.
<br />


<h2>Languages, Utilities, Enviorments </h2>

- <b>PowerShell</b> 
- <b>Azure subscription </b>
- <b>Windows 10 ISO</b>



<h2>Lab walk-through:</h2>

<p align="center">
Create Virtual Machine: <br/>
<img src="create_virtualmachine.png" height="80%" width="80%" alt="Setup-SIEM-for-Sentinel"/>
</p>
-  Created a resource group named honepotlab
<br />
-  Named the virtual machine
<br />
-  Selected Windows 10 as the Image
<br />
<br />
<br />
<br />
<p align="center">
Create Log Analytics Workspace: <br/>
<img src="create_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<b></b>
<br />
<br />
<p align="center">
Enable server settings and data gathering in Microsoft Cloud Defender: <br/>
<img src="defender_plan.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="data_collection_setting.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p/>
<br />
<br />
<p align="center">
Connect Log Analytics to VM: <br/>
<img src="connect_law_to_vm.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
<br />
<p align="center">
Setup Microsoft Sentinel: <br/>
<img src="Add_sentinel_to_law.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
</p>
- <b> Added Sentinel (SIEM) to workspace in able to visualize attack data </b>
<br />
<br />
<p align="center">
Connect to VM with Remote Desktop: <br/>
<img src="connect_remotedesktop.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
<br />
<p align="center">
Observed Event Viewer Logs in VM: <br/>
<img src="observe_event_viwer.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
- Focused on event 4625 for for failed account logons (brute-force) attacks
<br />
<br />
<p align="center">
Turn off firewall and Ping VM from my home machine: <br/>
<img src="ping_vm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
- Turned off honeyport firewall to receive ICMP echo request
<br />
<br />
<p align="center">
Get Geolocation.io API Key: <br/>
<img src="Ipgeolocation_api.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
-Used this site to get an API key to lookup attackers geodata
<br />
-Latitude, longitude, State, Country, Ip address, etc
<br />
<br />
<p align="center">
Run Script To get Geo Data from attackers across the globe: <br/>
<img src="Run_script_geodata_of_attackers.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-Used a custom PowerShell script to log event viewer security logs of failed logon attemps.
<br />
-Script takes log attemps geo data and creates a log file which was used to train my analytics workspace.
<br />
<br />
<br />
<p align="center">
Failed Logon attempted logged: <br/>
<img src="failed_self_logon.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-Here I purposely failed to loggon to test the script
<br />
<br />
<br />
<p align="center">
Bruteforce attacks being logged: <br/>
<img src="attack_log_powershell.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-After some time attemps were being made
<br />
<br />
<br />
<p align="center">
Created custom log in Log Analytics Workspace (LAW) to import in our custom log: <br/>
<img src="create_custom_log_sample.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="failedRDPlog_notepad.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
- The custom powershell script created a txt file that I needed to import in LAW
<br/>
<br/>
<p align="center">
<img src="create_custom_log_path.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
-The original path for log file in ProgramData folder
<br />
<br />
<p align="center">
Extract fields from raw custom log data with custom script: <br/>
<img src="extracted_data_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-Used a custom  Kql/Sql script to extract the raw data needed to create custom fields for queries
<br />
<br />
<p align="center">
Setup map in Sentinel and connect to workspace: <br/>
<img src="Add_sentinel_to_law.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run custom script in Sentinel workbooks and plot map: <br/>
<img src="run_queryscript_plotmap2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
- I ran the same custom script in my Microsoft Sentinel to query the extracted fields and create a visual map of the brute force attacks
<br />
<br />
<p align="center">
View map in Sentinel: <br/>
<img src="Final_failed_RDP_MAP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Final check on the map <br/>
<img src="Final_worldmap_failed.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
- I let the SIEM run until the next morning and checked on the map for a final time.
<br />
<br />

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
