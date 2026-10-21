# 🖥️ Enterprise Infrastructure Lab: Windows Server 2025 & Active Directory

![Platform](https://img.shields.io/badge/Hypervisor-Oracle%20VM%20VirtualBox-blue)
![OS](https://img.shields.io/badge/Server%20OS-Windows%20Server%202025-green)
![Client OS](https://img.shields.io/badge/Client%20OS-Windows%2011%20Pro-0078D4)
![Status](https://img.shields.io/badge/Lab%20Status-Completed-brightgreen)

---

## 📌 1. Executive Summary / الملخص التنفيذي

**English:**  
This repository details the end-to-end deployment, configuration, and management of a virtualized enterprise IT infrastructure. The setup features a **Windows Server 2025** Primary Domain Controller (DC) providing core network identity and services (AD DS, DNS, DHCP, GPO) and a **Windows 11 Pro** client endpoint joined to the domain.

**بالعربية:**  
يوثق هذا المستودع خطوات الإنشاء والتكوين والإدارة الكاملة لبنية تحتية افتراضية تقاس على بيئات الشركات. يتضمن اللاب خادم **Windows Server 2025** كـ (Primary Domain Controller) يقدم خدمات الهوية والشبكة الأساسية (AD DS, DNS, DHCP, Group Policy) مع ربط جهاز عميل **Windows 11 Pro** بالنطاق لاختبار السياسات والاتصال.

---

## 📐 2. Architecture & Topologies / المخطط الفني للشبكة

| Item / العنصر | Domain Controller (DC) | Client Endpoint |
| :--- | :--- | :--- |
| **Hostname / اسم الجهاز** | `DC2025` | `WIN11-CL01` |
| **Operating System / نظام التشغيل** | Windows Server 2025 Datacenter | Windows 11 Pro |
| **Role / الدور** | AD DS, DNS, DHCP, GPO Server | Domain Joined Workstation |
| **IP Addressing / عنوان الـ IP** | `192.168.10.10 /24` (Static) | `DHCP Allocated` |
| **DNS Server** | `127.0.0.1` (Self) | `192.168.10.10` |
| **Domain Name / اسم المجال** | `saud.local` | `saud.local` |

---

## 🚀 3. Step-by-Step Implementation / خطوات التنفيذ التفصيلية

### Phase 1: Virtualization & Base Installation / المرحلة الأولى: البيئة الافتراضية والتثبيت
* **Hypervisor Setup:** Configured VirtualBox Internal Network (`LabNet`) to isolate traffic.
* **Server Deployment:** Installed Windows Server 2025 (Desktop Experience).
* **Initial Configurations:**
  * Renamed computer to `DC2025`.
  * Assigned Static IP (`192.168.10.10/24`) and configured loopback DNS.

---

### Phase 2: Active Directory & Core Services / المرحلة الثانية: ترقية السيرفر والخدمات الأساسية
* **AD DS Role:** Installed Active Directory Domain Services role via Server Manager.
* **Forest Deployment:** Promoted server to Domain Controller for new forest `saud.local`.
* **DNS Configuration:** Verified Forward & Reverse Lookup Zones.
* **DHCP Scope Setup:** Created DHCP Scope (`192.168.10.50` - `192.168.10.150`) with Router option (`192.168.10.1`) and DNS option (`192.168.10.10`).

---

### Phase 3: Active Directory Infrastructure & OUs / المرحلة الثالثة: الهيكل التنظيمي والمدراء
* Created Organizational Unit (OU) structure:
  * `SAUD-HQ`
    * `OUs`: `IT`, `HR`, `Finance`, `Operations`
    * `Groups`: `GRP_IT_Admins`, `GRP_HR_Users`
* Provisioned domain users and assigned appropriate RBAC security permissions.

---

### Phase 4: Endpoint Join & Verification / المرحلة الرابعة: ربط جهاز العميل والتحقق
* Deployed Windows 11 Pro virtual machine on `LabNet`.
* Joined `WIN11-CL01` to `saud.local` domain using domain credentials.
* Verified RSAT connection and successful DHCP IP lease acquisition.

---

## 🛠️ 4. Key Skills Demonstrated / المهارات التقنية المكتسبة

* **System Administration:** Windows Server 2025 Deployment, Active Directory Architecture, Domain Services Management.
* **Network Infrastructure:** Static/Dynamic IP Routing, DHCP Scope Design, DNS Resolution.
* **Endpoint Management:** Domain Join Procedures, Workstation Troubleshooting.
* **Documentation & Governance:** Professional IT Lab Documentation, Network Mapping.

---
