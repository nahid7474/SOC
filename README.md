Project: Build Security Operations Center (SOC) with Microsoft
____________________________________________________________________________________
In this mini Security Operations Center (SOC) building project, I'll use Microsoft solutions leveraging a combination of tools and services designed to monitor, detect, and respond to security incidents. 

Activities involve:


- **Infrastructure Setup** :
    - Install and configure Windows Server 2019 with Active Directory, DHCP, DNS
    - Create Organizational Unit (OU) for domain users (both admin and standard users), and configure NAT
    - Utilize PowerShell scripts to create domain users in Active Directory and machine onboarding

- **Deploy and Connect Microsoft Defender XDR to cover:**

    - Microsoft Defender for Identity
    - Microsoft Defender for Endpoints
    - Microsoft Defender for Cloud Apps
    - Microsoft Defender Office365
    - Microsoft Defender Alerts

- **Monitoring and Logging**

    - Will deploy and leverage Microsoft Sentinel SIEM
    - Create data cikkections rule, deploy agent to collect and forward security Event logs from endpoints
    - Will integrate Microsoft and third-party produts/services with sentinel, collect and analyze security data using connectors

- **Incident Response:** 
    - Create/deploy logic app/playbook in Sentinel.
    - Automate threat response using Playbook and Automation Rules.

- **Azure Firewall:**
    - Deploy Azure Firewall to protect my virtual networks and control traffic flows

_______________________________________________________________________________________

**Infrastructure Setup**
This has been completed here https://github.com/nahid7474/AD


Tenaant Setup: 


**Deploy and Connect Microsoft Defender XDR to cover:**
