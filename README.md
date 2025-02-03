<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

- Access to Microsoft Azure 

<h2>Installation Steps</h2>

![image](https://github.com/user-attachments/assets/abcae031-1845-44b9-82f1-7da7e8ae8da7)
<p>
1) Create a resource group named "osTicket"
</p>
<br />

![image](https://github.com/user-attachments/assets/20d5c35d-3a9f-4a2b-a94c-ecababe297f1)
![image](https://github.com/user-attachments/assets/9343066d-7eb3-4259-986e-b95d14a68ee2)
![image](https://github.com/user-attachments/assets/367229d4-a450-4914-8aaf-b3472d2e9633)
<p>
2) Create an Azure Virtual Machine Windows 10, 2 vCPUs
  
Name: osticket-vm 

Username: labuser (Example)

Password: osTicketPassword1! (Example)
</p>
<br />

![image](https://github.com/user-attachments/assets/a4b7dc22-8792-4d54-bc68-7c6ca9a30a8a)
<p>
3) Log into the VM with Remote Desktop
</p>
<br />

![image](https://github.com/user-attachments/assets/3646b257-5123-4192-91a3-10d98d966a2a)

4) Within the VM , download the [osTicket-Installation-Files.zip](https://drive.google.com/uc?export=download&id=1b3RBkXTLNGXbibeMuAynkfzdBC1NnqaD) and unzip it onto your desktop. 

- The folder should be called “osTicket-Installation-Files”
- We will use the files in this folder to install osTicket and some of the dependencies.

<br />

![image](https://github.com/user-attachments/assets/8501b24a-a131-452e-b2c2-423d3f68c76d)
<p>
5) Install / Enable IIS in Windows WITH CGI
  
Control Panel -> Uninstall a Program -> Turn Windows features on or off -> [X] Internet informational Services -> World Wide Web Services -> Application Development Features -> [X] CGI
</p>
<br />

![image](https://github.com/user-attachments/assets/43fa4429-4317-43eb-9c92-a7524752e66e)
<p>
6) From the “osTicket-Installation-Files” folder, install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi)
</p>
<br />

![image](https://github.com/user-attachments/assets/484aef9f-bf16-4052-be35-273ab14b0684)
<p>
7) From the “osTicket-Installation-Files” folder install the Rewrite Module (rewrite_amd64_en-US.msi)
</p>
<br />

![image](https://github.com/user-attachments/assets/9b01b154-8584-4b8e-b3eb-e917378cecb5)
<p>
8) Create the directory C:\PHP
</p>
<br />

![image](https://github.com/user-attachments/assets/3b41a4eb-4fa0-429f-8e00-9552f0d59ebb)
<p>
9) From the “osTicket-Installation-Files” folder, unzip PHP 7.3.8 (php-7.3.8-nts-Win32-VC15-x86.zip) into the “C:\PHP” folder
</p>
<br />

![image](https://github.com/user-attachments/assets/f963770a-7fae-48a2-b9d4-9fca85b02cfa)
<p>
10) From the “osTicket-Installation-Files” folder, install VC_redist.x86.exe.
</p>
<br />

![image](https://github.com/user-attachments/assets/5a576f95-be8a-4804-b456-0aef21e8a202)
<p>
11) From the “osTicket-Installation-Files” folder, install MySQL 5.5.62 (mysql-5.5.62-win32.msi)

Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->
Username: root (Example)
Password: root (Example)
</p>
<br />

![image](https://github.com/user-attachments/assets/cc759018-6411-44ba-b0ec-eeeecd8dba39)
<p>
12) Open IIS as an Admin
</p>
<br />

![image](https://github.com/user-attachments/assets/d6cc5864-69fc-4c48-bcce-3e4ea4655fe9)
<p>
13) Register PHP from within IIS (PHP Manager -> C:\PHP\php-cgi.exe)
</p>
<br />

![image](https://github.com/user-attachments/assets/3ace3153-eeb1-4a4a-9922-264fe3399484)
<p>
14) Reload IIS (Open IIS, Stop and Start the server)
</p>
<br />

![image](https://github.com/user-attachments/assets/a5fb8445-4ceb-4d96-960b-6a27e032d51b)
<p>
15) Install osTicket v1.15.8
From the “osTicket-Installation-Files” folder, unzip “osTicket-v1.15.8.zip” and copy the “upload” folder into “c:\inetpub\wwwroot”
Within “c:\inetpub\wwwroot”, Rename “upload” to “osTicket”
</p>
<br />

![image](https://github.com/user-attachments/assets/3ace3153-eeb1-4a4a-9922-264fe3399484)
<p>
16) Reload IIS (Open IIS, Stop and Start the server)
</p>
<br />

![image](https://github.com/user-attachments/assets/7b1cf93c-bae9-4300-9407-941aab6aca3d)
<p>
17) Inside IIS 
Go to sites -> Default -> osTicket
On the right, click “Browse *:80”
</p>
<br />

![image](https://github.com/user-attachments/assets/83dc428c-86d2-4051-b8eb-7b4f8d2d54e8)
<p>
18) Note that some extensions are not enabled
Go back to IIS, sites -> Default -> osTicket
Double-click PHP Manager
Click “Enable or disable an extension”
Enable: php_imap.dll
Enable: php_intl.dll
Enable: php_opcache.dll
Refresh the osTicket site in your browser, observe the changes
</p>
<br />

![image](https://github.com/user-attachments/assets/48dfda37-0e3c-4310-9a85-7b5a31e90ad2)
<p>
19) Rename: ost-config.php
From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />

![image](https://github.com/user-attachments/assets/23426a08-e5bf-4155-a080-d93357d60f2e)
<p>
20) Assign Permissions: ost-config.php
Disable inheritance -> Remove All
New Permissions -> Everyone -> All
</p>
<br />

![image](https://github.com/user-attachments/assets/d45b7a61-4f4b-46b9-b8f6-4e3c03a9c028)
<p>
21) Continue Setting up osTicket in the browser (click Continue)
Name Helpdesk
Default email (receives email from customers)
</p>
<br />

![image](https://github.com/user-attachments/assets/00be2732-4e5a-49f1-ae52-f14fec25cb98)
<p>
22) From the “osTicket-Installation-Files” folder, install HeidiSQL.
Open Heidi SQL
Create a new session, root/root
Connect to the session
Create a database called “osTicket”
</p>
<br />

![image](https://github.com/user-attachments/assets/414b1819-fb99-4494-851d-6100513a1a4e)
<p>
23) Continue Setting up osTicket in the browser
MySQL Database: osTicket
MySQL Username: root
MySQL Password: root
Click “Install Now!”
</p>
<br />

![image](https://github.com/user-attachments/assets/d3dd3b6a-d75b-4314-9ec0-7aa8a17b785d)
<p>
24) Clean up
Delete: C:\inetpub\wwwroot\osTicket\setup
Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<br />
