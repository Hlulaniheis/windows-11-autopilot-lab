# Windows 11 Autopilot Deployment Lab

## 📌 Project Overview

This project demonstrates an enterprise-grade Windows 11 deployment using **Microsoft Autopilot**, **Intune**, and **Azure AD (Entra ID)**. The lab was built entirely in Microsoft Azure using a nested Hyper-V environment.

## 🎯 Objectives

- Deploy a Windows 11 VM in Azure using Hyper-V
- Configure Microsoft Intune for device management
- Set up Windows Autopilot for zero-touch deployment
- Automate device enrollment and configuration

## 🏗️ Architecture

```
Azure VM (Hyper-V Host) → Windows 11 Client VM → Entra ID Join → Intune → Autopilot Deployment
```

## 🛠️ Technologies Used

| Technology | Purpose |
|------------|---------|
| Azure Virtual Machines | Host the lab environment |
| Hyper-V | Run nested Windows 11 VM |
| Windows 11 Pro | Client OS |
| Microsoft Entra ID | Identity and device join |
| Microsoft Intune | MDM and policy management |
| Windows Autopilot | Zero-touch deployment |

## 📸 Proof of Deployment

![Autopilot Login Screen](screenshots/pin-login.png)

*The device successfully joined Entra ID and configured Windows Hello PIN.*

## 📋 Step-by-Step Process

### 1. Azure VM Setup
- Created a Windows Server 2022 VM in Azure
- Enabled nested virtualization
- Installed Hyper-V role

### 2. Windows 11 Client VM
- Created a Generation 2 Hyper-V VM
- Installed Windows 11 Pro from ISO
- Configured static IP and NAT for internet access

### 3. Intune & Autopilot Configuration
- Activated Intune free trial
- Assigned licenses to admin account
- Created Autopilot deployment profile
- Enrolled device via "Access work or school"
- Captured and uploaded hardware hash
- Assigned device to Autopilot profile

### 4. Autopilot Deployment Test
- Reset the VM using "Remove everything"
- VM rebooted into Autopilot OOBE
- Signed in with Entra ID credentials
- PIN configured (Windows Hello)

## 🔧 Challenges & Solutions

| Challenge | Solution |
|-----------|----------|
| Secure Boot blocking ISO boot | Disabled Secure Boot in VM settings |
| APIPA (169.254.x.x) IP address | Configured static IP + NAT on host |
| Intune license not assigned | Activated trial and assigned Plan 1 license |
| Device not showing in Intune | Verified user scope and enrollment restrictions |

## 📂 Repository Structure

```
windows-11-autopilot-lab/
├── README.md
├── screenshots/
│   ├── azure-vm-setup.png
│   ├── hyper-v-install.png
│   ├── autopilot-profile.png
│   ├── device-enrolled.png
│   └── pin-login.png
└── scripts/
    └── get-hash.ps1
```

## 🚀 How to Recreate This Lab

1. Deploy a Windows Server 2022 VM in Azure (D4s_v3, Standard security type)
2. Enable nested virtualization and install Hyper-V
3. Create a Gen2 Windows 11 VM with TPM and Secure Boot disabled
4. Install Windows 11 Pro and set a static IP
5. Activate Intune trial and assign licenses
6. Enroll the device via Settings > Accounts > Access work or school
7. Capture hardware hash using Get-WindowsAutoPilotInfo
8. Upload to Intune and create Autopilot profile
9. Reset VM and watch Autopilot deploy

## 📚 Lessons Learned

- Autopilot requires the device to be Entra ID joined
- Intune licenses must be assigned before enrollment
- Nested virtualization in Azure requires a supported VM size (D4s_v3 or larger)
- Network connectivity issues can be resolved with static IP + NAT

## 👨‍💻 Author

Hlulani Chavalala — [(https://github.com/Hlulaniheis)]

## 📅 Date

July 2026
