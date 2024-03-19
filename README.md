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
- <b> Created a resource group named honepotlab</b>
<br />
- <b> Named the virtual machine</b>
<br />
- <b> Selected Windows 10 as the Image</b>
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
Observer Event Viewer Logs in VM: <br/>
<img src="observe_event_viwer.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
-<b>Focused on event 4625 for for failed account logons (brute-force) attacks</b>
<br />
<p align="center">
Turn off firewall and Ping VM from your machine: <br/>
<img src="ping_vm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
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
<br/>
-Used a custom PowerShell script to log event viewer security logs of failed log attemps.
<br/>
-Script takes failed attempts geo data and creates a log file which was used to train my analytics workspace.
<br/>
<p align="center">
Failed Logon attempted logged: <br/>
<img src="failed_self_logon.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />
-Here I purposely failed to loggon to test the script
<br />
<p align="center">
Bruteforce attacks being logged: <br/>
<img src="attack_log_powershell.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<br />
-After some time attemps were being made
<br />
<p align="center">
Create custom log in Log Analytics Workspace (LAW) to import in our custom log: <br/>
<img src="create_custom_log_sample.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
<img src="create_custom_log_path.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Extract fields from raw custom log data with custom script: <br/>
<img src="extracted_data_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setup map in Sentinel and connect to workspace: <br/>
<img src="Add_sentinel_to_law.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run custom script in Sentinel workbooks and plot map: <br/>
<img src="run_queryscript_plotmap2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
View map in Sentinel: <br/>
<img src="Final_failed_RDP_MAP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Final check on the map <br/>
<img src="Final_worldmap_failed.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
