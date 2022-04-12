# Compliance Settings - Ideas for Configuration Item (CI)
## About
I am simply collecting some ideas here for **Configuration Items (CI)** in SCCM. 


## Passive CIs (without remediation)
* BIOS
  * Check BIOS Settings using Powershell & WMI
* Event Viewer
  * Count amount of specific Event IDs 
  ```powershell
  # Get a count of all application log entries with the ID 866 from the last 30 days
  $date = (Get-Date).AddDays(-30)
  $myEventIDs = Get-WinEvent -FilterHashtable @{logname=’application’; id=866; StartTime = $date;} | measure
  return $myEventIDs.Count
  ```

* Hardware
  * Check battery capacity

* Misc
  * Check free disk space on C:
  ```powershell
  # Output free disk space on system drive in bytes
  (Get-WmiObject Win32_LogicalDisk | where-object {$_.deviceid -eq $env:systemdrive} | select freespace).freespace
  ```
  
* Registry
  * Check existance of a key
* Security
  * Check if Bitlocker is enabled
  * Check if SecureBoot is enabled
* Settings
  * Check the installed Windows version
  * Check if optional features are enabled or disabled (i.e. Internet Explorer)
* Services
  * Check status of service
  * Check startup type of service
* Software
  * Check if a particular software is installed

## Active CIs (with remediation)
* BIOS
  * Check BIOS Setting using PowerShell & WMI and change if needed
* Registry
  * Check existance of key and create it if needed
* Settings
  * Check if optional features are enabled or disabled (i.e. Internet Explorer) and then adjust it
* Services
  * Check status of service and adjust it if needed
  * Check startup type of service and adjust it if needed
