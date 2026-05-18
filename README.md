SOC/SIEM Detection Lab: Wazuh, Sysmon, Windows Event Logs, and Microsoft Defender
Overview
This project is a hands-on SOC/SIEM detection lab built to simulate endpoint monitoring, alert investigation, Windows log analysis, detection validation, and incident response documentation.
The lab was built using Microsoft Hyper-V, an Ubuntu Server running Wazuh, and a Windows 11 endpoint monitored with the Wazuh Agent. Additional telemetry sources included Sysmon, Windows Security logs, PowerShell Operational logs, TaskScheduler Operational logs, and Microsoft Defender logs.
The goal of this project was to develop and demonstrate practical skills relevant to entry-level SOC Analyst, Security Analyst, and IT Security roles.
---
Lab Architecture
```text
Host Machine
└── Windows 11 Pro
    └── Microsoft Hyper-V

Virtual Machines
├── Wazuh-SIEM
│   ├── Ubuntu Server
│   ├── Wazuh Manager
│   ├── Wazuh Dashboard
│   ├── Wazuh Indexer
│   └── Static Lab IP: 192.168.56.10
│
└── WIN11-ENDPOINT
    ├── Windows 11 Enterprise Evaluation
    ├── Wazuh Agent
    ├── Sysmon
    ├── Microsoft Defender
    └── Static Lab IP: 192.168.56.20
```
The lab used a private internal Hyper-V network for communication between the Wazuh server and the monitored Windows endpoint.
---
Tools and Technologies
Microsoft Hyper-V
Ubuntu Server
Wazuh SIEM
Wazuh Agent
Windows 11 Enterprise Evaluation
Sysmon
Windows Event Viewer
Windows Security Logs
PowerShell Operational Logs
TaskScheduler Operational Logs
Microsoft Defender Operational Logs
PowerShell
MITRE ATT&CK
---
Skills Demonstrated
SIEM deployment and configuration
Windows endpoint monitoring
Wazuh agent onboarding
Sysmon configuration
Windows Event ID analysis
Alert triage and investigation
Detection validation
Log source tuning
MITRE ATT&CK mapping
Remediation and cleanup
Incident report documentation
---
Detection Scenarios
1. Local Admin Account Creation and Group Modification
A local user account named `labtest` was created and added to the local `Administrators` group. This simulated suspicious account creation, privilege escalation, and possible persistence behavior.
Key evidence collected:
Windows Security Event ID `4720` — user account created
Windows Security Event ID `4732` — user added to local Administrators group
Wazuh alerts for account creation and administrator group modification
Cleanup verification showing the test account was removed
Skills demonstrated:
Windows account monitoring
Local privilege escalation detection
Windows Security log analysis
Wazuh alert investigation
Remediation verification
Incident report:
Local Admin Account Creation Incident Report
---
2. Scheduled Task Persistence Detection
A scheduled task named `LabPersistenceTest` was created to simulate persistence-style behavior. Initially, the activity was not clearly visible in Wazuh, so TaskScheduler Operational logging was enabled and added to the Wazuh Agent configuration. After retesting, Wazuh successfully ingested the event and mapped it to MITRE ATT&CK `T1053.005`.
Key evidence collected:
TaskScheduler Event ID `106` — scheduled task registered
Wazuh event showing `LabPersistenceTest`
MITRE ATT&CK mapping to `T1053.005` — Scheduled Task
Cleanup verification showing the scheduled task was deleted
Skills demonstrated:
Persistence detection
Log source tuning
Wazuh Agent configuration
Detection validation
MITRE ATT&CK mapping
Troubleshooting SIEM visibility gaps
Incident report:
Scheduled Task Persistence Incident Report
---
3. Failed Login Detection
A test user named `failedloginuser` was created, and multiple failed login attempts were generated using incorrect credentials. The failed logons were validated locally and then investigated in Wazuh.
Key evidence collected:
Windows Security Event ID `4625` — failed logon
Wazuh alert: `Logon Failure - Unknown user or bad password`
Event details showing the target account `failedloginuser`
Cleanup verification showing the test user was deleted
Skills demonstrated:
Authentication monitoring
Failed logon investigation
Windows Security Event ID analysis
Wazuh alert review
Account cleanup and validation
Incident report:
Failed Login Detection Incident Report
---
4. Microsoft Defender EICAR Detection
The safe EICAR antivirus test file was created to validate Microsoft Defender detection and Wazuh ingestion. Defender detected and quarantined the file, Windows logged the detection, and Wazuh collected the Defender event.
Key evidence collected:
Microsoft Defender Event ID `1117` — threat detected and action taken
Threat name: `Virus:DOS/EICAR_Test_File`
Detection source: Real-Time Protection
Action: Quarantine
Wazuh event showing Defender detection details
Cleanup verification confirming the test file was removed
Skills demonstrated:
Endpoint protection monitoring
Microsoft Defender log analysis
Malware-test detection validation
Wazuh Defender event ingestion
Quarantine and remediation verification
Incident report:
Microsoft Defender EICAR Detection Incident Report
---
Project Outcomes
By completing this lab, I demonstrated the ability to:
Build a functional SOC/SIEM lab from scratch
Deploy and configure Wazuh in a virtualized environment
Onboard a Windows endpoint into Wazuh
Configure Sysmon and multiple Windows event channels
Generate and investigate realistic security events
Validate detections using both local Windows logs and Wazuh alerts
Identify and fix a SIEM visibility gap
Map activity to MITRE ATT&CK techniques
Perform cleanup and remediation
Write professional incident-style reports
---
Incident Reports
This project includes four polished incident reports:
Scenario	Report
Local Admin Account Creation / Group Modification	View Report
Scheduled Task Persistence Detection	View Report
Failed Login Detection	View Report
Microsoft Defender EICAR Detection	View Report
---
Portfolio Summary
This SOC/SIEM lab demonstrates practical experience with endpoint monitoring, Windows event log analysis, Wazuh alert investigation, Sysmon telemetry, Microsoft Defender logging, detection validation, remediation, and incident documentation.
The project was designed to reflect skills commonly used in SOC Analyst, Security Analyst, IT Security, and entry-level cybersecurity roles.
---
Disclaimer
This lab was performed in an isolated virtual environment for educational and portfolio purposes. No real malware was used. The EICAR file is a safe antivirus test file used to validate antivirus and detection workflows.
