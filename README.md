Project: Build Security Operations Center (SOC) with Microsoft
____________________________________________________________________________________
In this Security Operations Center (SOC) building project, I'll use Microsoft solutions leveraging a combination of tools and services designed to monitor, detect, and respond to security incidents. 

Activities involve:

- **Infrastructure Setup** :
    - Install and configure Windows Server 2019 with Active Directory, DHCP, DNS
    - Create Organizational Unit (OU), domain users, and configure NAT and routing
    - Utilize PowerShell scripts to create domain users in Active Directory and machine onboarding

- **Microsoft Tenant and Azure Subscription** set up:
    - Configure Microsoft 365 admin center
    - Microsoft Defender Security Center
    - Microsoft Azure Portal

- **Configure Defender for Endpoint (MDE)**
    - Onboard device to Microsoft Defender for Endpoint (MDE) using powershel script

- **Configure Defender for Identity**
    - Install Identity Senson on Domain Controler
    - Create MDE account to sync with the portal 

- **Deploy and Connect Microsoft Defender XDR to cover:**
    - Microsoft Defender for Identity
    - Microsoft Defender for Endpoints
    - Microsoft Defender for Cloud Apps
    - Microsoft Defender Office365
    - Microsoft Defender Alerts

- **Monitoring and Logging**
    - Will deploy and leverage Microsoft Sentinel SIEM
    - Create data collections rule, deploy agent to collect and forward security Event logs from endpoints
    - Will integrate Microsoft and third-party produts/services with sentinel, collect and analyze security data using connectors

- **Threat Detection and Incident Response:** 
    - Deploy Out of Box Sentinel Analytics rule, create custom detection rule based on Mitre TTP 
    - Create/deploy logic app/playbook in Sentinel.
    - Automate threat response using Playbook and Automation Rules.

- **Deploy and Configure Azure Firewall, ingest logs in Microsoft Sentinel:**
    - Deploy Azure Firewall to protect my virtual networks and control traffic flows
    - Ingest firewall logs to Microsoft Sentinel for security analysis, alerts and and incident investigation.

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


Will now activate all my required licenses so I can perform all my administrative tasks covering this project.

![image](https://github.com/nahid7474/SOC/assets/170605912/39e3f6ee-fe96-499e-a223-e4579047f90d)

Assign these licenses to my Global Admin account from the user's blade.

![image](https://github.com/nahid7474/SOC/assets/170605912/b814decf-4f1d-486c-8236-0a750bd940b9)

My Azure portal is ready here at https://portal.azure.com/

![image](https://github.com/nahid7474/SOC/assets/170605912/ccd6f37c-39d7-49ba-b53c-7d6c77c47a75)

My Defender security portal is ready here at https://security.microsoft.com/

![image](https://github.com/nahid7474/SOC/assets/170605912/521eb0ec-b734-478c-ad0c-f7ae07e22d3d)


To verify that I have licenced my admin account NNN@trialsc200lab.onmicrosoft.com correctly, and all components and settings within Microsoft's security ecosystem are ready to use, I will navigate to the settings menu on the botton left and locate all the components.
They are all here, and I am good to go. 

![image](https://github.com/nahid7474/SOC/assets/170605912/39195f97-5451-409f-842d-5870dc0696b8)


- **Deploy and Connect Microsoft Defender XDR to cover:**

    - Microsoft Defender for Identity
    - Microsoft Defender for Endpoints
    - Microsoft Defender for Cloud Apps
    - Microsoft Defender Office365
    - Microsoft Defender Alerts
 
  First step: onboard a device to Microsoft Defender for Endpoint (MDE) using powershel script.
  To achive this, I'll head to Microsoft Defender admin portal.
  From here will navigate to Settings > Endpoints

  ![image](https://github.com/nahid7474/SOC/assets/170605912/51fe85e4-2b62-47af-8058-e2827184d4c9)

  On the Device Management > click Onboarding, then click Download onboarding package on the target machine

  ![image](https://github.com/nahid7474/SOC/assets/170605912/b6a491f0-78df-4caf-9115-9ba93056a6c1)

  Logged onto my VM and ran the downloaded script that came in the package as an admin.
  
![image](https://github.com/nahid7474/SOC/assets/170605912/87daae6d-0b42-4bdc-ab3d-f69d933088ef)


Script ran suucessfully, device onboarded successfully.

![image](https://github.com/nahid7474/SOC/assets/170605912/8067a2bd-5106-4831-872d-3c6408a7c6e9)

Will now run the sc query sense command to test the device status and confirm device is successfully onboarded

![image](https://github.com/nahid7474/SOC/assets/170605912/4e566ed1-2857-4ce9-b67b-221c9282c691)

Will go back to the MDE portal > Device Inventory, I can locate the newly onboarded device confirming this device onboarded succeefully.

![image](https://github.com/nahid7474/SOC/assets/170605912/13aa324e-51f4-4340-9483-062b5a7b5211)


----------------------------------------------------------------------------------------------------------------------------------------
**Monitoring and Logging** 

- Will deploy and leverage Microsoft Sentinel SIEM
- Create data collections rule, deploy agent to collect and forward security Event logs from endpoints
- Will integrate Microsoft and third-party produts/services with sentinel, collect and analyze security data using connectors
-------------------------------------------------------------------------------------------------------------------------------    
Will start by creating a Resource Group and name it HomeLab.
On the Azure portal, search for resource group and select to create one. 

![image](https://github.com/nahid7474/SOC/assets/170605912/9346a989-7383-4892-a742-1dfbefcd7356)

![image](https://github.com/nahid7474/SOC/assets/170605912/19fe1df9-1db4-47d8-9c63-1c9e238e16f9)


Next, create a log analytics workspace. 
On the Azure portal, search for Log analytics workspace and select to create one. 

![image](https://github.com/nahid7474/SOC/assets/170605912/28ad9af8-3704-444f-b80d-10fa11287789)

Click the newly created log analytic workspace and Create Microsoft Sentinel, add the Sentinel to my HomeLab workspace

![image](https://github.com/nahid7474/SOC/assets/170605912/002255a2-2ff6-4df2-888c-8a6de44d844d)


Sentinel has now been deployed successfully and ready to use.

![image](https://github.com/nahid7474/SOC/assets/170605912/e231436a-103a-4a47-9c4c-e0fe7f4c1250)

I'll now start with Data Connectors and install all the required connectors available from the content hub.


![image](https://github.com/nahid7474/SOC/assets/170605912/beaa0fe7-ef3f-4fc6-ab49-6c9af34c9095)


Once installed, will go to each of the connector page and configure them one by one.
Will start with Microsoft 365, click Open Connector Page

![image](https://github.com/nahid7474/SOC/assets/170605912/ebaa8223-baeb-48a6-beff-ab8c53d772ff)

Prerequisites are met, under COnfiguration check all the boxes and Apply Changes.

![image](https://github.com/nahid7474/SOC/assets/170605912/c7d50cb4-3295-4121-b90f-5720f47b09b4)

Next is Microsoft XDR, Open the connector page


![image](https://github.com/nahid7474/SOC/assets/170605912/cb9a72fe-7020-463c-b520-2fff9840702c)

On the instruction area, check that all prerewuisites are met 

![image](https://github.com/nahid7474/SOC/assets/170605912/d54050b7-fd53-460b-a6bd-371a47ca990a)


Under configuration, click Connect incidents & alerts.


![image](https://github.com/nahid7474/SOC/assets/170605912/0b089c71-4a5f-4ddd-9254-6c7c8f2ef5bb)

This will ingest all logs and create alerts/incidents that faill into Microsoft Defender XDR suite which includes:

Microsoft Defender for Endpoint, Microsoft Defender for Identity, Microsoft Defender for Office 365, Microsoft Defender for Cloud Apps
Microsoft Defender Alerts, Microsoft Defender Vulnerability Management, Microsoft Purview Data Loss Prevention, Microsoft Entra ID Protection

![image](https://github.com/nahid7474/SOC/assets/170605912/09e224bd-0add-4af4-b125-29295a281c9d)


To verify that I have configured the connector correctly, I can data are flowing/ingesting fro all these domain.

![image](https://github.com/nahid7474/SOC/assets/170605912/18bf0e1c-0759-4637-914a-ed91a81f6d24)


Similar way, I'll now configure Microsoft Entra ID data connector and make sure I am getting data from my Active Directory.
I can now see that I have started getting data from Entra ID as well.

![image](https://github.com/nahid7474/SOC/assets/170605912/93006cc6-cc32-4ce6-861b-663d9db2c751)


Next, Collect windows security events via agent.
First I ned a data collection rule, to get a rule go to the Log Analytics Workspace > Setting > Aents> Data Collection Rule.

![image](https://github.com/nahid7474/SOC/assets/170605912/fd6a6e29-2247-40c7-ab35-fc21ddde7f53)

Create a rule under the same subscription and resource group. 

![image](https://github.com/nahid7474/SOC/assets/170605912/1b7245ad-a2dd-40d4-82d7-4cfa9de60dc0)


Add data source, choose the events that need to ingested onto Sentinel, Next: Destination

Add HomeLab Sentinel workspace and click Add data source 

![image](https://github.com/nahid7474/SOC/assets/170605912/64ed45c6-543a-4e13-af9f-f08f95f38760)

Now that I have data collection rule created, I'll go to te connector page for Windows Security Events via AMA and verify I am getting data.

![image](https://github.com/nahid7474/SOC/assets/170605912/b5aa9119-33ec-4044-a66c-f2cb45c003cd)



And I can see my connected VMs where these data are coming from.

![image](https://github.com/nahid7474/SOC/assets/170605912/2ad36d58-3481-494d-b094-3852015f174b)


Next, Threat detection with Microsoft Sentinel analytics using out of box detection rules and custom analytics rule.
To deploy out of box detection rules, navigate to Analytics section, click on 3 dots next to the Rule template and click Create.

![image](https://github.com/nahid7474/SOC/assets/170605912/c6d5f1fb-55b1-4b57-876f-df9eab4700fa)


Check the Name and Description, Severity and MITRE ATT&CK and click Next: Set rule logic.

![image](https://github.com/nahid7474/SOC/assets/170605912/fae2e4ca-d0d5-429c-8e04-0ed7d4fe6f30)


Test the rule logic/query, schedule it as expected, do the entity mapping, click Next: Incident settings


![image](https://github.com/nahid7474/SOC/assets/170605912/e364afee-f116-4ede-b519-d0a3eaa27d4a)
![image](https://github.com/nahid7474/SOC/assets/170605912/779bc339-8f82-4f4f-b723-bacd9854b867)

Enable Incident settings, and alert grouping as appropriate, click Next: Automated response

![image](https://github.com/nahid7474/SOC/assets/170605912/52c8881e-436f-410a-a9a1-9e48a91b749d)

Will leave the automated respose as it is (will do the automation later), click Nest to Review+ Create
Once validation passed, click Save and now I have an active/enabled detection rule.

![image](https://github.com/nahid7474/SOC/assets/170605912/98c8b738-c32d-4b3d-9ac3-0aa28c811a30)


For my Sentinel instance, I've created 15 rules, including 4 highs and 11 mediums.

![image](https://github.com/nahid7474/SOC/assets/170605912/bec5c887-3b10-4f50-81f0-05df5d1bd3f3)

**Next, I'll now test to validate my detection rules are working.**

Now that I have a detection rule to detect Local "Admin Group Changes" related activit, I'll exactly do so; 
I will create a new admin user nahid2

![image](https://github.com/nahid7474/SOC/assets/170605912/5b5cf133-512b-4766-a3df-fe3ff93af811)

Now I'll add this user to Security Administrator group which should trigger an alarm, and it did as expected.

![image](https://github.com/nahid7474/SOC/assets/170605912/af8f3ac5-4990-445a-bf55-923048fa9bcd)

I will now assign one analyst to investigate this incident.

![image](https://github.com/nahid7474/SOC/assets/170605912/832e9c3a-e2e5-4b0b-ab4b-133bec8656da)

This proves that my detection analytics are working correctly. 


**Next: Threat response using Playbook and Automation Rules**




- **Deploy and Configure Azure Firewall, ingest logs in Microsoft Sentinel:**
    - I have completed a dedicated project on firewall deployment and configuration here on another repo: https://github.com/nahid7474/Firewall
