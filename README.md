# System Administration Automation using PowerShell

## Objectives 

``Step 1 : Deploy infrastructure on azure cloud using automation scripts.``

    1 VM – IIS web server(manually) 

    2 VM – Install SQL Datebasse(Manually) 

    3 VM – MYSQL SERVER(Manually) 

    4 VM – DOT Net(Manually) 
    Get-Service *SQL*


``Step 2 : Service reliability & Auto-healing`` 

1. Pull server list from AD 

2. Document service status 

3. Escalate if the service fails to start on 3 consecutive checks. 

4. Failed logins  

``Step 3 : Disk space compliance``

1. Get the disk consumption details  

``Step 4 : Centralize Logging & Reporting``

1. Generate the Daily report  

2. Display the report on the App service 

``Step 5 : Policy Enforment``

Check metadata/tags (owner, Environment, service) 