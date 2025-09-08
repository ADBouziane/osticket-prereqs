# osTicket - Prerequisites and Installation

This project documents the installation and configuration of the open-source help desk ticketing system **osTicket** on a Windows 10 Azure Virtual Machine.  
By the end of this lab, I had a fully functioning ticketing system accessible through a web browser.

---

## 🎥 Video Demonstration
- [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com/watch?v=...) *(replace with the actual video if you want)*

---

## 🛠️ Environments and Technologies Used
- **Microsoft Azure** (Virtual Machines/Compute)
- **Remote Desktop (RDP)**
- **Internet Information Services (IIS)**
- **PHP & PHP Manager**
- **MySQL Database**
- **HeidiSQL**

---

## 💻 Operating System Used
- **Windows 10 (21H2)**

---

## ✅ Prerequisites
- Azure Subscription
- Resource Group
- Virtual Machine (Windows 10, 2 vCPUs, 8GB RAM)
- Administrative access (username/password)

---

## ⚙️ Installation Steps

### 1. Create Azure Virtual Machine
- Deployed a Windows 10 VM in Azure with 2 vCPUs and 8GB RAM.
- Created a new resource group (`osTicket-RG`).
- Configured RDP access for remote management.  
📸 *Screenshot of VM creation in Azure Portal*

---

### 2. Connect to VM via Remote Desktop
- Used the **public IP address** from Azure.
- Logged in with the `labuser` account.  
📸 *Screenshot of RDP login*

---

### 3. Download osTicket Installation Files
- Downloaded the osTicket installation zip package.  
- Extracted contents to `Desktop\osTicket-Installation-Files`.  
📸 *Screenshot of extracted installation files*

---

### 4. Enable IIS (Internet Information Services) + CGI
- Navigated to **Control Panel → Programs → Turn Windows Features On/Off**.  
- Enabled:
  - **IIS (Web Server)**
  - **CGI** (under Application Development Features).  
📸 *Screenshot of IIS features enabled*

- Verified IIS was running by browsing to `http://127.0.0.1`.  
📸 *Screenshot of default IIS webpage*

---

### 5. Install PHP Manager & Rewrite Module
- Installed **PHP Manager for IIS**.  
- Installed the **IIS URL Rewrite Module** (dependency for osTicket).  
📸 *Screenshot of installations*

---

### 6. Configure PHP
- Created `C:\PHP` directory.  
- Extracted `php-7.3.x` binaries into `C:\PHP`.  
📸 *Screenshot of PHP folder*

- Registered PHP within IIS using PHP Manager.  
- Restarted IIS web server.  
📸 *Screenshot of PHP registered in IIS*

---

### 7. Install MySQL Database
- Installed **MySQL 5.5.62** with the following credentials:
  - **Username:** `root`
  - **Password:** `root`  
📸 *Screenshot of MySQL setup*

- Installed **HeidiSQL** to manage the database.  
📸 *Screenshot of HeidiSQL connection*

- Created a new database named `osTicket`.  
📸 *Screenshot of `osTicket` DB created in HeidiSQL*

---

### 8. Install osTicket
- Extracted the **osTicket** folder.  
- Copied the `upload` folder into `C:\inetpub\wwwroot`.  
- Renamed it to `osTicket` (⚠️ no spaces).  
📸 *Screenshot of `osTicket` folder in IIS root*

- Restarted IIS and browsed to `http://localhost/osTicket`.  
📸 *Screenshot of osTicket installer page*

---

### 9. Configure osTicket
- Renamed `ost-sampleconfig.php` to `ost-config.php`.  
- Set proper file permissions (Full Control for Everyone).  
📸 *Screenshot of renamed file + permissions*

- Completed osTicket setup in browser:
  - Created Admin account (`adminuser / Password1`)
  - Linked to MySQL Database (`osTicket`, `root`, `root`)  
📸 *Screenshot of osTicket setup page*

---

### 🔑 Verification

- **Admin Login:** Confirmed login with admin credentials.  
📸 *Screenshot of Admin Dashboard*

- **End-User Login:** Verified end-users can open tickets.  
📸 *Screenshot of End-User Ticket Portal*

---

## 📝 Notes
- osTicket is now fully installed and ready for further configuration (SLAs, Departments, Ticket Workflows).
- Cleanup step (optional): Delete `setup/` folder to harden the installation.

---

## 🤳 Connect with Me
[<img align="left" alt="Abdel | LinkedIn" width="22px" src="https://img.icons8.com/ios-filled/50/FFFFFF/linkedin.png" />](https://www.linkedin.com/in/abdel-b-893256362/) [**LinkedIn**](https://www.linkedin.com/in/abdel-b-893256362/)
