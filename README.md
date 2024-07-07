Project: Build Security Operations Center (SOC) with Microsoft
____________________________________________________________________________________
In this mini Security Operations Center (SOC) building project, I'll use Microsoft solutions leveraging a combination of tools and services designed to monitor, detect, and respond to security incidents. 

Activities involve:


- **Infrastructure Setup** :
    - Install and configure Windows Server 2019 with Active Directory, DHCP, DNS
    - Create Organizational Unit (OU), domain users, and configure NAT and routing
    - Utilize PowerShell scripts to create domain users in Active Directory and machine onboarding

- **Microsoft Tenant and Azure Subscription** set up:
    - Configure Microsoft 365 admin center
    - Microsoft Defender Security Center
    - Microsoft Azure Portal

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

I have documented all my infrastructure related activities here in a seperate project: https://github.com/nahid7474/AD

**Microsoft Tenant and Azure Subscription set up** :

To achieve this, I will start from the scratch, by creating my Microsoft 365 tenant and Azure subscription. 

Microsoft 365 tenant: 
Go to the Microsoft 365 E5 product portal and select Free trial.
Complete the registration process with my personal email account. 
Set the custom domain name for my tenant which is trialsc200lab.onmicrosoft.com in this case. 

My Microsoft365 admin centre/portal is ready here now https://admin.microsoft.com

![image](https://github.com/nahid7474/SOC/assets/170605912/39fcd788-f327-4ca4-b15b-ce1cd249f943)


Will now activate all my required licenses so I can perform all the tasks covering this project.

![image](https://github.com/nahid7474/SOC/assets/170605912/39e3f6ee-fe96-499e-a223-e4579047f90d)

Assign these licenses to my Global Admin account from the user's blade.

![image](https://github.com/nahid7474/SOC/assets/170605912/b814decf-4f1d-486c-8236-0a750bd940b9)

My Azure portal is ready here at https://portal.azure.com/
My Defender security portal is ready here at https://security.microsoft.com/

To verify that I have licenced my admin account NNN@trialsc200lab.onmicrosoft.com correctly, and all components and settings within Microsoft's security ecosystem are ready to use, I will navigate to the settings menu on the botton left and locate all the components.
They are all here, and I am good to go. 

![image](https://github.com/nahid7474/SOC/assets/170605912/39195f97-5451-409f-842d-5870dc0696b8)


**Deploy and Connect Microsoft Defender XDR to cover:**






