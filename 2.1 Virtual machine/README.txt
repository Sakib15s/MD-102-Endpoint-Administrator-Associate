#  Creating and Connecting a Virtual Machine in Microsoft Azure

##  Overview
This lab demonstrates the process of creating and configuring a **Virtual Machine (VM)** in Microsoft Azure.  
The goal was to provision a VM from scratch, configure secure RDP access, and successfully connect to it remotely.

---

##  Steps Performed

###  Check the Subscription
Before starting, verified that an **active Azure subscription** was available to create and manage resources.

- Navigated to **Azure Portal → Subscriptions**
- Ensured the subscription was active and ready for deployments

---

###  Create a Resource Group
Created a dedicated **Resource Group** to organize all related resources.

- **Portal:** Azure Portal → *Resource Groups* → *Create*
- **Example:**  
  - Name: `IntuneTest`  
  - Region: `Australia East`

---

###  Create the Virtual Machine
Provisioned a new VM under the resource group.

- **Portal Path:** Azure Portal → *Virtual Machines* → *Create*
- Specified:
  - **Image:** Windows 10
  - **Size:** Standard B2s
  - **Authentication:** Password
  - **Inbound ports:** RDP (TCP 3389)
- Reviewed configuration → Clicked **Review + Create**
- After validation → Clicked **Create**

 Deployment began and completed successfully.

---

###  Configure Network Settings for RDP
After deployment, configured **Network Security Group (NSG)** rules to allow RDP only from my IP address.

- **Portal Path:** VM → *Networking*
- Edited inbound rule:
  - **Destination port:** 3389  
  - **Source:** My IP address  
  - **Priority:** 1000  
  - **Action:** Allow

This step ensures secure remote access to the VM.

---

###  Connect via RDP
Once the rule was applied:
- Clicked **Connect → RDP**
- Downloaded the `.rdp` file
- Used the assigned credentials to connect from the local machine

 **Result:** Successfully connected to the Azure VM through Remote Desktop.

---

##  Outcome
- Created and deployed an Azure Virtual Machine  
- Configured network access securely via NSG rules  
- Successfully connected using Remote Desktop Protocol (RDP)

---

##  Key Learnings
- Importance of organizing resources in a resource group  
- NSG configuration and network security best practices  
- Basic VM provisioning workflow in Azure

---

##  Tools Used
- **Microsoft Azure Portal**  
- **Remote Desktop Connection (RDP)**  
- **Windows 10/11 VM Image**