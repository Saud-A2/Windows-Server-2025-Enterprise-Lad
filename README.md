# 🚀 Windows Server 2025 Enterprise Infrastructure, AD DS & SMB Share Lab

A comprehensive hands-on technical guide and production-grade documentation for deploying an enterprise-grade Windows Server 2025 environment. This project demonstrates full-stack domain infrastructure initialization, Active Directory Domain Services (AD DS), Organizational Unit (OU) security baselines, client workstation domain join, Kerberos authentication, and granular SMB Share & NTFS permission enforcement following the Principle of Least Privilege (PoLP).

---

## 📌 Executive Summary
This enterprise lab serves as a professional portfolio submission illustrating practical system administration, network security control, and Identity & Access Management (IAM). It systematically documents every implementation phase—from isolated VirtualBox network provisioning to real-time SMB file share access and permission inheritance controls.

---

## 🛠️ Infrastructure Overview & Specifications
| System Parameter | Technical Detail |
| :--- | :--- |
| **Virtualization Hypervisor** | Oracle VirtualBox (Internal Network Mode) |
| **Domain Controller Host** | Windows Server 2025 Enterprise (`DC2025.saud.local`) |
| **Client Workstation** | Windows 11 Enterprise (`Saud A.`) |
| **Network Configuration** | Static IPv4 `192.168.10.10/24` \| DNS: `192.168.10.10` |
| **Active Directory Domain** | `saud.local` |
| **Security Access Group** | `IT-Group` |
| **Network Share Path** | `\\DC2025\CompanyData\IT-Data` |

---

## 📋 Technical Implementation & Stage-by-Stage Verification

### Stage 1: Virtual Hypervisor & Internal Network Provisioning
![VirtualBox Environment Setup](01-virtualbox-env.png.png)

* **Technical Details:**
  * Provisioned dedicated virtual nodes for Windows Server 2025 and Windows 11 Client within Oracle VirtualBox.
  * Configured isolated **Internal Network** adapters across all virtual machines to prevent host interference and enforce zero-trust network segregation.

---

### Stage 2: Domain Controller Baseline & Network Interface Binding
![Local Server Configuration](02-local-server.png)

* **Technical Details:**
  * Initialized core server identity properties by rebinding the hostname to `DC2025`.
  * Assigned a static IPv4 address (`192.168.10.10/24`) and mapped primary DNS resolvers to loopback infrastructure to handle local directory queries.

---

### Stage 3: Active Directory Domain Services (AD DS) & OU Hierarchy
![AD DS OUs and User Management](03-ad-users-ous.png.png)

* **Technical Details:**
  * Installed AD DS roles and promoted `DC2025` as the Forest Root Domain Controller for `saud.local`.
  * Architected structured Organizational Units (OUs) for departmental division and created administrative domain accounts (`Saud A.`).

---

### Stage 4: Role-Based Access Control (RBAC) & Security Group Provisioning
![Active Directory Group Membership](04-ad-group-membership.png)

* **Technical Details:**
  * Created the `IT-Group` security group to implement strict Role-Based Access Control (RBAC).
  * Populated security group memberships with authorized domain identity accounts (`Saud A.`).

---

### Stage 5: Domain Join Operation & DNS Resolver Validation
![Workstation Domain Join](domain-joined.04.png)

* **Technical Details:**
  * Configured network adapter settings on the Windows 11 Client machine to utilize `192.168.10.10` as the primary DNS server.
  * Successfully joined the Windows 11 workstation to `saud.local` domain, verifying mutual Domain Controller trust.

---

### Stage 6: Domain Authentication Flow & Interactive Desktop Session
![Domain User Interactive Login](domain-user-login-05.png)

* **Technical Details:**
  * Verified end-to-end domain identity authentication using `saud.local\Saud-user` / `Saud A.` credentials at the Windows Logon Screen.
  * Confirmed ticket issuing and secure interactive desktop session initialization.

---

### Stage 7: Client Desktop Environment Initialization
![Domain User Desktop Verification](domain-user-desktop.06.png)

* **Technical Details:**
  * Confirmed successful profile creation and group policy application on the domain workstation client desktop.

---

### Stage 8: SMB Share, NTFS Security Enforcement & Access Control Validation
![Network Access Verification](Saud_IT_Network_Folder_Test.png)

* **Technical Details:**
  1. Configured SMB Advanced Sharing on directory `C:\CompanyData` with Share Permissions assigned as `Everyone: Full Control`.
  2. Enforced strict **NTFS Security Permissions** on sub-directory `IT-Data` by breaking permission inheritance and granting `Modify / Read / Write` rights exclusively to `IT-Group`.
  3. Accessed network share via UNC path `\\DC2025\CompanyData\IT-Data` from the domain-joined client as user `Saud A.`.
  4. Created and verified text payload document `Saud-IT.txt`:  
     `Testing Access Successful IT Department Access Ok`
  5. Validated successful file creation and modification with zero `Access Denied` permission errors.

---

## 👤 Author & Maintainer
* **Saud Al-Ziyadi**
* Computer Technical Support & Systems Administration Specialist
