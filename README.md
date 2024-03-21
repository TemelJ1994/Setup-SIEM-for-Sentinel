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
<b>Create Virtual Machine:<b> <br/>
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
<b>Create Log Analytics Workspace:<b> <br/>
<img src="create_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
<b></b>
<br />
<br />
<p align="center">
<b>Enable server settings and data gathering in Microsoft Cloud Defender:<b> <br/>
<img src="defender_plan.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<img src="data_collection_setting.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<p/>
<br />
<br />
<p align="center">
<b>Connect Log Analytics to VM:<b> <br/>
<img src="connect_law_to_vm.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
<br />
<p align="center">
<b>Setup Microsoft Sentinel:<b> <br/>
<img src="Add_sentinel_to_law.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
</p>
-Added Sentinel (SIEM) to workspace in able to visualize attack data
<br />
<br />
<p align="center">
<b>Connect to VM with Remote Desktop:<b> <br/>
<img src="connect_remotedesktop.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
<br />
<br />
</p>
<br />
<p align="center">
<b>Observed Event Viewer Logs in VM:<b> <br/>
<img src="observe_event_viwer.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
- Focused on event 4625 for for failed account logons (brute-force) attacks
<br />
<br />
<p align="center">
<b>Turn off firewall and Ping VM from my home machine:<b> <br/>
<img src="ping_vm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
- Turned off honeyport firewall to receive ICMP echo request
<br />
<br />
<p align="center">
<b>Get Geolocation.io API Key:<b> <br/>
<img src="Ipgeolocation_api.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
-Used this site to get an API key to lookup attackers geodata
<br />
-Latitude, longitude, State, Country, Ip address, etc
<br />
<br />
<p align="center">
<b>Run Script To get Geo Data from attackers across the globe:<b> <br/>
<img src="Run_script_geodata_of_attackers.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-Used a custom PowerShell script to log event viewer security logs of failed logon attemps.
<br />
-Script takes log attemps geo data and creates a log file which was used to train my analytics workspace.
<br />
[Get PowerShell Script here](https://github.com/TemelJ1994/Setup-SIEM-for-Sentinel/blob/main/Custom_Security_Log_Exporter.ps1)
<br />
<br />
<p align="center">
<b>Failed Logon attempted logged:<b> <br/>
<img src="failed_self_logon.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-Here I purposely failed to loggon to test the script
<br />
<br />
<br />
<p align="center">
<b>Bruteforce attacks being logged:<b> <br/>
<img src="attack_log_powershell.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-After some time attemps were being made
<br />
<br />
<br />
<p align="center">
<b>Created custom log in Log Analytics Workspace (LAW) to import in our custom log:<b> <br/>
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
<b>Extract fields from raw custom log data with custom script:<b> <br/>
<img src="extracted_data_LAW.png" height="100%" width="100%" alt="Disk Sanitization Steps"/>
</p>
-Used a custom  Kql script to extract the raw data needed to create custom fields for queries <br />
[Get custom script here](https://github.com/TemelJ1994/Setup-SIEM-for-Sentinel/blob/main/custom%20script%20Sentinel)
<br />
<br />
<p align="center">
<b>Setup map in Sentinel and connect to workspace:<b> <br/>
<img src="Add_sentinel_to_law.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<b>Run custom script in Sentinel workbooks and plot map:<b> <br/>
<img src="run_queryscript_plotmap2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
- I ran the same custom script in my Microsoft Sentinel to query the extracted fields and create a visual map of the brute force attacks
<br />
<br />
<p align="center">
<b>View map in Sentinel:<b> <br/>
<img src="Final_failed_RDP_MAP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<br />
<br />
<b>Final check on the map:<b> <br/>
<img src="Final_worldmap_failed.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
- I let the SIEM run until the next morning and checked on the map for a final time.
<br />
- This concludes my lab. Thank you!
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
