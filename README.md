# 🚀 Windows Server 2025 Enterprise File Share & NTFS Permissions Lab

A comprehensive hands-on implementation guide for setting up a secure enterprise File Sharing infrastructure on Windows Server 2025. This project demonstrates Active Directory integration, hybrid access control (Share & NTFS permissions), and end-to-end verification from a domain-joined client following the principle of least privilege (PoLP).

---

## 📌 Project Overview
This repository provides a practical demonstration of designing, configuring, and securing an enterprise file management environment. It covers Active Directory Domain Services (AD DS) setup, Organizational Unit (OU) structure, granular NTFS permission inheritance management, SMB network share configuration, and live access validation.

---

## 🛠️ Lab Environment & Components
| Component | Details |
| :--- | :--- |
| **Virtualization Platform** | Oracle VirtualBox |
| **Domain Controller (DC)** | Windows Server 2025 (`DC2025.saud.local`) |
| **Client Workstation** | Windows 11 Enterprise (`Saud A.`) |
| **Domain Name** | `saud.local` |
| **Target Security Group** | `IT-Group` |
| **Network Share Path** | `\\DC2025\CompanyData\IT-Data` |

---

## 📋 Implementation & Verification Stages

### Stage 1: Active Directory & Group Policy Setup
![Active Directory Group Membership](04-ad-group-membership.png)

* **Configuration Details:**
  * Configured Active Directory Domain Services (AD DS) on domain `saud.local`.
  * Created dedicated Organizational Units (OUs) and initialized the `IT-Group` security group.
  * Populated group membership with authorized domain users (`Saud A.`) to apply Role-Based Access Control (RBAC).

---

### Stage 2: SMB Share, NTFS Security & Live Access Verification
![Network Access and File Creation Verification](Saud_IT_Network_Folder_Test.png)

* **Configuration & Validation:**
  1. Configured SMB Advanced Sharing on `CompanyData` with Share Permissions set to `Everyone: Full Control`.
  2. Enforced strict **NTFS Security Permissions** on `IT-Data` by disabling inheritance and assigning `Modify / Read / Write` rights exclusively to `IT-Group`.
  3. Accessed the share path `\\DC2025\CompanyData\IT-Data` from the Windows 11 client using domain account `Saud A.`.
  4. Created and modified `Saud-IT.txt` with text content:  
     `Testing Access Successful IT Department Access Ok`
  5. Saved changes successfully without permission errors (`Access Denied`), validating 100% operational functionality.

---

## 👤 Author
* **Saud Al-Ziyadi**
* IT Computer Technical Support Specialist
