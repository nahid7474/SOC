Project: Build Security Operations Center (SOC) with Microsoft
____________________________________________________________________________________
High level summary:

In this mini Security Operations Center (SOC) building project, I'll use Microsoft solutions leveraging a combination of tools and services designed to monitor, detect, and respond to security incidents. 

Activities involve:

**Infrastructure Setup**

Windows Servers: Utilize Windows Server operating systems (Windows Server 2019) for hosting necessary services and tools.
Active Directory (AD): Set up an Active Directory domain to manage user accounts, groups,  policies etc.

**Deploy and Connect Microsoft Defender XDR to cover:**

Microsoft Defender for Endpoint
Microsoft Defender for Office 365
Microsoft Defender for Cloud Apps
Microsoft Defender for Identity
Microsoft Defender Alerts

**Monitoring and Logging**

SIEM and Log Management: Microsoft Sentinel: 
Will use Microsoft's cloud-native SIEM and SOAR (Security Orchestration, Automation, and Response) solution.
Deploy agent to collect and forward Windows Event logs from endpoints, enhancing visibility into potential threats. 
Will integrates with various Microsoft and third-party services to collect and analyze security data using various 
Connectors: Will Use built-in connectors to ingest data from different services (e.g., Azure AD, Office 365 etc) and on-premises sources.

**Incident Response:** 

Leverage automation and orchestration capabilities within Azure Sentinel for efficient incident response workflows.
Automate threat response using Playbook and Automation Rules.


**Azure Firewall:**
Deploy Azure Firewall to protect my virtual networks and control traffic flows.
_______________________________________________________________________________________

**Infrastructure Setup**
This has been completed here https://github.com/nahid7474/AD


Tenaant Setup: 


**Deploy and Connect Microsoft Defender XDR to cover:**
