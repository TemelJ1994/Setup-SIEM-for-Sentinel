<h1>Setup SIEM for Sentinel</h1>



<h2>Description</h2>
This project consist of me setting a basic home lab running Active Directory with Oracle VirtualBox and adding users with PowerShell.
<br />


<h2>Languages, Utilities, Enviorments </h2>

- <b>PowerShell</b> 
- <b>Azure subscription </b>
- <b>Windows 10 ISO</b>
- <b>



<h2>Lab walk-through:</h2>

<p align="center">
Create Virtual Machine: <br/>
<img src="create_virtualmachine.png" height="80%" width="80%" alt="Setup-SIEM-for-Sentinel"/>
<br />
<br />
Create Log Analytics Workspace:  <br/>
<img src="create_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Enable server settings and data gathering in Microsoft Cloud Defender: <br/>
<img src="defender_plan.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="data_collection_setting.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Connect Log Analytics to VM:  <br/>
<img src="connect_law_to_vm.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setup Microsoft Sentinel:  <br/>
<img src="Add_sentinel_to_law.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Observer Event Viewer Logs in VM: <br/>
<img src="observe_event_viwer.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Turn off firewall and Ping VM from your machine:  <br/>
<img src="ping_vm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Download PowerShell script:  <br/>
<img src="https://i.imgur.com/AeZkvFQ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Get Geolocation.io API Key:  <br/>
<img src="Ipgeolocation_api.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run Script To get Geo Data from attackers across the globe:  <br/>
<img src="Run_script_geodata_of_attackers.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br/>
<br/>
Failed Logon attempted logged: <br/>
<img src="failed_self_logon.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Bruteforce attacks being logged: <br/>
<img src="attack_log_powershell.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Create custom log in Log Analytics Workspace (LAW) to import in our custom log:  <br/>
<img src="create_custom_log_path.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Extract fields from raw custom log data with custom script:  <br/>
<img src="extracted_data_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
Setup map in Sentinel and connect to workspace:  <br/>
<img src="Add_sentinel_to_law.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Run custom script in Sentinel workbooks and plot map:  <br/>
<img src="run_queryscript_plotmap2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
View map in Sentinel:  <br/>
<img src="Final_failed_RDP_MAP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
Final check on the map  <br/>
<img src="Final_worldmap_failed.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
