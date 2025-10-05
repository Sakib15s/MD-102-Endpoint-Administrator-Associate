#  Windows Automatic Enrollment with Microsoft Entra ID and Intune

##  Overview
This lab demonstrates how to configure and test **Windows Automatic Enrollment** into **Microsoft Intune** through **Microsoft Entra ID Join**.  
The setup ensures that Windows devices automatically enroll in Intune when users from specific groups sign in to Entra ID–joined devices.

---

##  Configuration Steps

###  Set MDM User Scope
In the **Microsoft Intune Admin Center**, the **MDM user scope** was configured to control which users can automatically enroll devices.

- **Path:** Intune Admin Center → Devices → Enroll devices → Automatic Enrollment  
- **MDM user scope:** Selected **Some**
- A specific **Azure AD security group** was assigned for testing  
  ➜ Only users in this group will automatically enroll their devices in Intune

---

###  Verify License Requirements
For automatic enrollment to work, users must:
- Be licensed for **Microsoft Intune**
- Have **Intune service** enabled in the assigned license
- Use a license that includes both **Intune** and **Entra ID Premium P1**

 Assigned license: **Enterprise Mobility + Security E5**

**Path:** Microsoft 365 Admin Center → Users → Active Users → [User] → Licenses and Apps → Intune Enabled 

---

###  Create a Test Virtual Machine
A new **Windows 10 virtual machine** was created in Azure for testing.

- **Portal Path:** Azure Portal → Virtual Machines → Create
- Configured with:
  - Image: Windows 10 Pro
  - Size: Standard B2s
  - Authentication: Username/Password
  - Network: RDP allowed from my IP

Deployment completed successfully.

---

###  Join the VM to Microsoft Entra ID
On the Windows 10 VM:

1. Opened **Settings → Accounts → Access work or school**
2. Clicked **Connect**
3. Selected **Join this device to Azure Active Directory**
4. Signed in with the licensed user credentials  
   (`User2@intuneazure1.onmicrosoft.com`)
5. Verified the prompt:  
   *"Make sure this is your organization"* → Clicked **Join**

 Successfully joined the device to **Microsoft Entra ID**

---

###  Confirm Device Join and Sign-In
After joining:
- Restarted and signed in again with the same Entra ID user
- Verified device registration under:  
  **Settings → Accounts → Access work or school → Connected to [organization].onmicrosoft.com**
- Confirmed the device appeared in:
  - **Microsoft Entra Admin Center → Devices → All Devices**
  - **Intune Admin Center → Devices → All Devices**

---

##  Outcome
- Configured **Windows automatic enrollment** for selected users  
- Verified that a **licensed user** can join a Windows VM to Entra ID  
- Confirmed that the device automatically enrolled into **Microsoft Intune**

---

##  Key Learnings
- Automatic enrollment only applies to users in the defined MDM scope  
- Users must have a valid Intune + Entra Premium license  
- Entra ID Join can trigger Intune enrollment without manual setup on the device

---

##  Tools Used
- **Microsoft Intune Admin Center**  
- **Microsoft Entra Admin Center**  
- **Microsoft 365 Admin Center**  
- **Azure Portal (Virtual Machine)**  
- **Windows 10 Virtual Machine (RDP Access)**