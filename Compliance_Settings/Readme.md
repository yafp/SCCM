# Compliance Settings - Ideas for Configuration Item (CI)
## About
I am simply collecting some ideas here for **Configuration Items (CI)** in SCCM. 


## Configuration Items 
* BIOS
  * Check BIOS Settings using Powershell & WMI
 
* Event Viewer
  * Count amount of specific Event IDs
    * Check
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
    * 
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
    * Check:
      ```powershell
      # Check state of Optional feature IE
      (Get-WindowsOptionalFeature -FeatureName Internet-Explorer-Optional-amd64 -Online).State
      ```
    * Remediation
      ```powershell
      # Disable Optional feature Internet Explorer
      C:\Windows\System32\Dism.exe /online /Disable-Feature /FeatureName:Internet-Explorer-Optional-amd64 /Quiet /NoRestart
      ```
* Services
  * Check status of service
    ```powershell
    # Check status of a service
    (Get-Service "SERVICENAMEDUMMY").Status
    ```
  * Check startup type of service
    ```powershell
    # Check startup type of a service
    (Get-Service "SERVICENAMEDUMMY").StartType
    ```
* Software
  * Check if a particular software is installed
