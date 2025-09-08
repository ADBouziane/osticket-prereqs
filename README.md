<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This project documents the prerequisites and installation of the open-source help desk ticketing system <b>osTicket</b> on a Windows 10 Azure Virtual Machine.<br />

<h2>Video Demonstration</h2>

- ### <a href="https://www.youtube.com">YouTube: How To Install osTicket with Prerequisites</a>

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines / Compute)
- Remote Desktop (RDP)
- Internet Information Services (IIS)
- PHP & PHP Manager
- MySQL Database
- HeidiSQL

<h2>Operating Systems Used</h2>

- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- Azure subscription & Resource Group  
- Windows 10 VM (≈2 vCPUs, 8 GB RAM)  
- RDP access to the VM  
- IIS installed with <b>CGI</b> enabled  
- PHP 7.3.x binaries available on the VM  
- MySQL (5.5.x used in this lab)  
- osTicket installation package  
- (Optional) HeidiSQL for DB management  

---

<h2>Installation Steps</h2>

<h3>1) Create a Windows 10 VM in Azure</h3>
Provision a Windows 10 VM (2 vCPUs / 8 GB RAM), place it in a new Resource Group, and allow RDP.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Azure VM creation"/></p>
<br />

<h3>2) Connect via RDP</h3>
Use the VM’s public IP and your credentials to sign in with Remote Desktop.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="RDP sign-in"/></p>
<br />

<h3>3) Download and Extract osTicket Installation Files</h3>
Download the provided installation bundle and extract it on the Desktop into a folder (e.g., <code>osTicket-Installation-Files</code>).
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Download and extract installation files"/></p>
<br />

<h3>4) Enable IIS + CGI</h3>
Control Panel → Programs → “Turn Windows features on or off” → Enable <b>IIS</b> and under “Application Development Features” enable <b>CGI</b>. Test by browsing to <code>http://127.0.0.1</code>.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Enable IIS and CGI"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Default IIS page"/></p>
<br />

<h3>5) Install PHP Manager and URL Rewrite</h3>
From the osTicket installation files, install <b>PHP Manager for IIS</b> and the <b>IIS URL Rewrite Module</b>.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Install PHP Manager & URL Rewrite"/></p>
<br />

<h3>6) Configure PHP</h3>
Create <code>C:\PHP</code> and extract PHP 7.3.x binaries there. In IIS → PHP Manager → “Register new PHP version” and select <code>C:\PHP\php-cgi.exe</code>. Restart IIS.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="C:\PHP contents"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Register PHP in IIS"/></p>
<br />

<h3>7) Install MySQL & HeidiSQL</h3>
Install MySQL 5.5.62 with username <code>root</code> / password <code>root</code>. Install HeidiSQL to manage the database.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="MySQL setup"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="HeidiSQL connection"/></p>
<br />

<h3>8) Prepare osTicket Web Files</h3>
Extract osTicket → copy the <code>upload</code> folder into <code>C:\inetpub\wwwroot</code> → rename it to <b>osTicket</b>. Restart IIS, then browse to the installer page in IIS Manager → Sites → Default Web Site → osTicket → Browse.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Copy upload/ to wwwroot and rename"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="osTicket installer page"/></p>
<br />

<h3>9) Finalize Installation</h3>
- Enable required PHP extensions (<code>imap</code>, <code>intl</code>, <code>opcache</code>) in PHP Manager.  
- Rename <code>ost-sampleconfig.php</code> → <code>ost-config.php</code> and grant write permissions.  
- In HeidiSQL, create a database named <code>osTicket</code>.  
- Complete the web installer with DB info (<code>root/root</code>) and create your Admin account.  
- Verify access to both the Admin portal (<code>/osTicket/scp/</code>) and the End-User portal (<code>/osTicket/</code>).  
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="osTicket config"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Admin & End-User portals"/></p>
<br />

---

<h2>🤳 Connect with me</h2>
<a href="https://www.linkedin.com/in/abdel-b-893256362/">
  <img align="left" alt="Abdel | LinkedIn" width="22px" src="https://img.icons8.com/ios-filled/50/FFFFFF/linkedin.png" />
</a>
<a href="https://www.linkedin.com/in/abdel-b-893256362/">LinkedIn</a>
