<p align="center">
  <img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This project documents the prerequisites and installation of the open-source help desk ticketing system <b>osTicket</b> on a Windows 10 Azure Virtual Machine. By the end, the system is reachable via browser for both end users and staff.<br />

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
- (Optional) HeidiSQL for easy MySQL management

<h2>Installation Steps</h2>

<h3>1) Create a Windows 10 VM in Azure</h3>
Provision a Windows 10 VM (2 vCPUs / 8 GB RAM), place it in a new Resource Group, and ensure RDP is allowed.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Azure VM creation"/></p>
<br />

<h3>2) Connect via RDP</h3>
Use the VM’s public IP and your admin credentials to sign in to the desktop.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="RDP sign-in"/></p>
<br />

<h3>3) Download osTicket Installation Files</h3>
Inside the VM, download the lab’s osTicket bundle and extract to a folder on the Desktop (e.g., <code>osTicket-Installation-Files</code>).
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Download and extract installation files"/></p>
<br />

<h3>4) Enable IIS + CGI</h3>
Control Panel → Programs → “Turn Windows features on or off” → Enable <b>IIS</b> and under “Application Development Features” enable <b>CGI</b>. Browse to <code>http://127.0.0.1</code> to confirm IIS is running.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Enable IIS and CGI"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Default IIS page"/></p>
<br />

<h3>5) Install PHP Manager and URL Rewrite</h3>
From the installation files, install <b>PHP Manager for IIS</b> and the <b>IIS URL Rewrite Module</b>.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Install PHP Manager & URL Rewrite"/></p>
<br />

<h3>6) Configure PHP</h3>
Create <code>C:\PHP</code> and extract the PHP 7.3.x binaries there. In IIS → PHP Manager → “Register new PHP version” and select <code>C:\PHP\php-cgi.exe</code>. Restart IIS.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="C:\PHP contents"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Register PHP in IIS"/></p>
<br />

<h3>7) Install MySQL</h3>
Install MySQL 5.5.62 (lab simplification): set user <code>root</code> / password <code>root</code>. Install <b>HeidiSQL</b> to manage the DB.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="MySQL setup (root/root)"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="HeidiSQL connection"/></p>
<br />

<h3>8) Prepare the osTicket Web Files</h3>
Extract the osTicket package. Copy the <code>upload</code> folder to <code>C:\inetpub\wwwroot</code> and rename it to <b>osTicket</b> (no spaces, lowercase “os”, capital “T”).
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Copy upload/ to wwwroot and rename to osTicket"/></p>
<br />

<h3>9) Load the osTicket Installer</h3>
Restart IIS. In IIS Manager → Sites → Default Web Site → <b>osTicket</b> → “Browse”. You should see the osTicket installer page.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="osTicket installer page"/></p>
<br />

<h3>10) Enable Required PHP Extensions</h3>
IIS → Sites → Default Web Site → <b>osTicket</b> → PHP Manager → “Enable or disable an extension”. Enable:
<ul>
  <li><code>php_imap.dll</code></li>
  <li><code>php_intl.dll</code></li>
  <li><code>php_opcache.dll</code></li>
</ul>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Enable PHP extensions"/></p>
<br />

<h3>11) Configure <code>ost-config.php</code> Permissions</h3>
Navigate to <code>C:\inetpub\wwwroot\osTicket\include</code>. Rename <code>ost-sampleconfig.php</code> to <code>ost-config.php</code>. Set permissions so the web app can write to it (lab simplification: “Everyone → Full control”).
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Rename and set permissions on ost-config.php"/></p>
<br />

<h3>12) Create the Database and Complete Setup</h3>
In HeidiSQL, connect as <code>root/root</code> and create a database named <b>osTicket</b>. Back in the installer, fill:
<ul>
  <li>MySQL Database: <code>osTicket</code></li>
  <li>Username: <code>root</code></li>
  <li>Password: <code>root</code></li>
</ul>
Create your Admin account (e.g., <code>adminuser</code> / <code>Password1</code>) and click <b>Install Now</b>.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Create osTicket DB in HeidiSQL"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Complete osTicket web installer"/></p>
<br />

<h3>13) Verify Admin & End-User Portals</h3>
- Staff/Admin: <code>/osTicket/scp/</code> — log in with the admin credentials created above.
- End-User: <code>/osTicket/</code> — submit a new ticket and confirm it appears in the Staff panel.
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Staff Control Panel"/></p>
<p><img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="End-User Support Center"/></p>
<br />

<h2>Final Notes</h2>
- Installation is complete; configuration (SLAs, departments, help topics) continues in the next lab.
- Optional hardening: remove the <code>setup/</code> directory once you’re done configuring.

<h2>🤳 Connect with me</h2>
<a href="https://www.linkedin.com/in/abdel-b-893256362/">
  <img align="left" alt="Abdel | LinkedIn" width="22px" src="https://img.icons8.com/ios-filled/50/FFFFFF/linkedin.png" />
</a>
<a href="https://www.linkedin.com/in/abdel-b-893256362/">LinkedIn</a>
