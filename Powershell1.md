1.
>>  Add-WindowsCapability -Online -Name "Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0"

## It installs the Active Directory administrative tools

2.
>> Import-Module ActiveDirectory


##  is used to load the Active Directory module into your PowerShell session. This module provides a set of cmdlets that allow you to manage and interact with Active Directory (AD) directly from PowerShell.

##

What is the ActiveDirectory Module?
The ActiveDirectory module is part of the Remote Server Administration Tools (RSAT) and includes cmdlets such as:

Get-ADUser – Retrieve user objects
New-ADUser – Create new users
Set-ADUser – Modify user properties
Get-ADGroup – Retrieve group objects
Add-ADGroupMember – Add users to groups
Get-ADComputer – Retrieve computer objects

3.
>> Install-WindowsFeature RSAT-AD-PowerShell
## is used to install the Active Directory PowerShell module on a Windows Server machine.

4.

>>Import-Module ActiveDirectory

5.
>>Get-Module -ListAvailable ActiveDirectory
## is used to check whether the Active Directory module is installed and available on your system.

6.
>>$logDir = "C:\Logs"
New-Item -Path $logDir -ItemType Directory -Force

## is used to create a new directory (C:\Logs) on your system, and the -Force flag ensures that it overwrites the directory if it already exists.

7.
$serverList | Out-File "$logDir\ServerList.txt"
$serviceName = "Interner Information Services (IIS) Manager"
$failureCount = @{}    
//check login attempt fail 
Get-WinEvent -FilterHashtable @{
      LogName = 'Security'
      ID = 4625
      StartTime = (Get-Date).AddDays(-1)
  } | Select-Object TimeCreated, Message | Out-File "$logDir\FailedLogins.txt"

  8.

foreach ($server in $serverList) {
      try {
          $status = Get-Service -ComputerName $server -Name $serviceName
          $logEntry = "$server - $($status.Status)"
          Add-Content "$logDir\ServiceStatus.txt" $logEntry
 
          if ($status.Status -ne 'Running') {
              $failureCount[$server] = ($failureCount[$server] + 1)
          } else {
              $failureCount[$server] = 0
          }
 
          # Escalate if failed 3 times
          if ($failureCount[$server] -ge 3) {
              Add-Content "$logDir\Escalation.txt" "$server - $serviceName failed to start 3 times"
              # You can add email alert or ticket creation here
          }
      } catch {
          Add-Content "$logDir\ServiceStatus.txt" "$server - Error: $_"
      }
  }

9.

Get-WinEvent -FilterHashtable @{
      LogName = 'Security'
      ID = 4625
      StartTime = (Get-Date).AddDays(-1)
  } | Select-Object TimeCreated, Message | Out-File "$logDir\FailedLogins.txt"




  ????????????????????????????????????????????????????????????????????







  Import-Module ActiveDirectory

Get-ADComputer -Filter 'operatingsystem -like "*server*" -and enable -eq "true"' `
-Properties Name, Operatingsystem,operatingSystemVersion, IPv4Address `
| Sort-Object -Property operatingsystem `
| select-object -Property Name, Operatingsystem, operatingSystemVersion, IPv4Address `
| Export-csv C:\ProgramData\xx.csv


<!-- -->