# osticket-prereqs<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system osTicket.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How To Install osTicket with Prerequisites](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>

<li><strong>MySQL:</strong> Configured and maintained the database backend for osTicket, ensuring efficient data storage and retrieval.



<li><strong>HeidiSQL:</strong> Utilized as a graphical interface to manage and interact with the MySQL database, enabling streamlined administration and query execution.


<li><strong>PHP:</strong> Implemented server-side scripting using PHP to support dynamic content generation and backend logic for osTicket's web interface.


<li><strong>PHP Manager:</strong> Employed PHP Manager within the IIS Management Console to configure and manage PHP settings for improved performance and compatibility.


<li><strong>Visual C++ Redistributable (VC Redist):</strong> Installed and configured necessary runtime components to support PHP and other IIS-related dependencies.


<li><strong>URL Rewrite Module (IIS):</strong> Applied URL rewriting and redirection rules to enhance user navigation and ensure compatibility with osTicket's routing requirements.



<h2>OVERVIEW</h2>

<li><strong>Configure Windows 10 OS to function as a web server.

<li><strong>Install required prerequisite software: MySQL, HeidiSQL, PHP, PHP Manager, Visual C++ Redistributable, and URL Rewrite.

<li><strong>Install osTicket and verify it is accessible as a website hosted on the local web server.

<li><strong>Enable necessary features and set appropriate permissions for osTicket.

<li><strong>Finalize the installation by configuring email settings and connecting to the MySQL database.

<li><strong>Verify that osTicket is accessible via localhost.

<li><strong>Remove or secure files that may present security vulnerabilities.




2. <h2>Install Required Software</h2>
<img width="616" height="216" alt="image" src="https://github.com/user-attachments/assets/e35cbac9-595e-4bec-aad9-70c262a671d6" /> 

Installation Steps:

-Install PHP Manager

-Install VC Redistributable

-Install URL Rewrite

-Install PHP:

-Create the directory C:\PHP.

-Extract PHP files into the C:\PHP folder.

-Register PHP within IIS.

-Reload IIS (open IIS Manager, stop and start the server).

-Install MySQL:

-Choose Typical Setup.

-Run the Configuration Wizard → select Standard Configuration.

-Set and remember your root password.

-Install HeidiSQL:

-Launch HeidiSQL.

-Create a new session using credentials root/your_password.

-Connect to the session and create a database named osTicket.

<h2>3.Install and Configure osTicket on the Web Server</h2>
<img width="708" height="338" alt="image" src="https://github.com/user-attachments/assets/5166195d-bdc8-48e0-8141-12d7aa466c83" />

-Install osTicket v1.15.8:

-Download osTicket.

-Extract the upload folder and copy it to C:\inetpub\wwwroot.

-Rename the folder from upload to osTicket.

-Reload IIS (stop and start the server again).

-Verify osTicket:

-In IIS, go to Sites → Default Web Site → osTicket.

-Click “Browse *:80” to confirm the installation is accessible.

<h2>4.Enable PHP Features and Set Permissions</h2>
-In PHP Manager, enable the following extensions:

-php_imap.dll

-php_intl.dll

-php_opcache.dll

-Rename the configuration file:

-Rename:
From C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
To C:\inetpub\wwwroot\osTicket\include\ost-config.php

-Set permissions on ost-config.php:

-Disable inheritance and remove all existing permissions.

-Add new permission: Everyone → Full Control.

<h2>5.Finalize Installation in Browser</h2>
-Continue setup via browser.

-Enter helpdesk name and default support email address.

-Use the following database details:

-Database Name: osTicket

-Username: root

-Password: your_password

-Click “Install Now!”

<h2>6.Test osTicket Accessibility on Localhost</h2>
-Verify the URLs:

-Agent Login: http://localhost/osTicket/scp/login.php

-User Portal: http://localhost/osTicket/

<img width="1196" height="433" alt="Screenshot 2025-07-03 033936" src="https://github.com/user-attachments/assets/8f4681e0-6fcc-4c61-b46b-8f0733a2386e" />

<h2>7. Secure Installation</h2>
-Delete the setup directory: C:\inetpub\wwwroot\osTicket\setup

-Set read-only permission on:
C:\inetpub\wwwroot\osTicket\include\ost-config.php
</p>
<p>
