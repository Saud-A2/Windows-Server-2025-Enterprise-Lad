# Windows Server 2025 Enterprise Lab Setup & Domain Join

## 📌 Project Overview
This repository documents the end-to-end setup and configuration of an enterprise-grade Virtual Machine environment using **Oracle VirtualBox**. The lab demonstrates full infrastructure setup including active directory domain service installation, domain controller promotion, network interface configuration, client domain joining, and domain user authentication testing.

---

## 🛠️ Lab Environment & Components
* **Virtualization:** Oracle VM VirtualBox
* **Domain Controller (DC):** Windows Server 2025 (`DC2025`)
* **Client Workstation:** Windows 11 Enterprise (`Windows Client Saud`)
* **Domain Name:** `saud.local`
* **Static IP Address:** `192.168.10.10/24`

---

## 🚀 Phases & Documentation

### Phase 1: VirtualBox Environment Setup
* Created dedicated virtual machines for Windows Server 2025 and Windows 11 Client.
* Configured Internal Network adapter settings to allow secure inter-VM communication.

![VirtualBox Environment Setup](01-virtualbox-env.png)

---

### Phase 2: Core Server & Network Configuration
* Renamed server hostname to `DC2025`.
* Configured static IP configuration (`192.168.10.10/24`) and DNS server settings.

![Local Server Configuration](02-local-server.png)

---

### Phase 3: Active Directory Domain Services & Organizational Units
* Installed Active Directory Domain Services (AD DS) role.
* Promoted server to Domain Controller for new forest `saud.local`.
* Created Organizational Unit (OU) structure and domain user accounts (`Saud-IT`).

![Active Directory Infrastructure](03-ad-users-ous.png.png)

---

### Phase 4: Client Domain Join Verification
* Configured Windows 11 client DNS settings pointing to `192.168.10.10`.
* Joined the Windows 11 client machine to `saud.local` domain successfully.

![Domain Joined Confirmation](domain-joined.04.png)

---

### Phase 5: Domain User Logon & Authentication Verification
* Verified Active Directory domain login using created domain user credentials (`Saud-IT`).
* Authenticated successfully on the client machine against the domain controller.

![Domain User Logon Prompt](domain-user-login-05.png)
![Successful Domain User Desktop Session](domain-user-desktop.06.png)

---

## 👤 Author
* **Saud Al-Ziyadi**
* Computer Technical Support Specialist
