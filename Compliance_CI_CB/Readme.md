# Compliance Settings - Configuration Item (CI) Ideas
## About
I am simply collecting some ideas here for **Configuration Items (CI)** in SCCM. 


## Passive CIs (without remediation)
* BIOS
  * Check BIOS Settings using Powershell & WMI
* Hardware
  * Check battery capacity
* Misc
  * Check free disk space on C:
* Registry
  * Check existance of a key
* Security
  * Check if Bitlocker is enabled
  * Check if SecureBoot is enabled
* Services
  * Check status of service
  * Check startup type of service


## Active CIs (with remediation)
* BIOS
  * Check BIOS Setting using PowerShell & WMI and change if needed
* Registry
  * Check existance of key and create it if needed
* Services
  * Check status of service and adjust it if needed
  * Check startup type of service and adjust it if needed
