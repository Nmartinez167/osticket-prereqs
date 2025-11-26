# osticket-prereqs<p align="center">
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

<li><strong>MySQL:</strong> Configured and maintained the database backend for osTicket, ensuring efficient data storage and retrieval.



<li><strong>HeidiSQL:</strong> Utilized as a graphical interface to manage and interact with the MySQL database, enabling streamlined administration and query execution.


<li><strong>PHP:</strong> Implemented server-side scripting using PHP to support dynamic content generation and backend logic for osTicket's web interface.


<li><strong>PHP Manager:</strong> Employed PHP Manager within the IIS Management Console to configure and manage PHP settings for improved performance and compatibility.


<li><strong>Visual C++ Redistributable (VC Redist):</strong> Installed and configured necessary runtime components to support PHP and other IIS-related dependencies.


<li><strong>URL Rewrite Module (IIS):</strong> Applied URL rewriting and redirection rules to enhance user navigation and ensure compatibility with osTicket's routing requirements.


<h2>1. Prepare The Windows 10 OS by turning it into a web server</h2>
<p>Install & Enable IIS (Internet Information Services) on the Windows computer, including application features and IIS Management Console.</p>

<h2>2. Install Prerequisite Programs</h2>

<h3>Installation Steps</h3>
<ol>
  <li>Install PHP Manager.</li>
  <li>Install VC Redist.</li>
  <li>Install Rewrite.</li>
  <li>Install PHP:
    <ul>
      <li>Create the directory C:\PHP.</li>
      <li>Extract PHP files into C:\PHP directory.</li>
      <li>Register PHP from within IIS.</li>
      <li>Reload IIS (Open IIS, Stop and Start the server).</li>
    </ul>
  </li>
  <li>Install mySQL:
    <ul>
      <li>Typical Setup -> Launch Configuration Wizard -> Standard Configuration -> (create_secret_password).</li>
    </ul>
  </li>
  <li>Install HeidiSQL:
    <ul>
      <li>Open HeidiSQL.</li>
      <li>Create a new session, root/secret_password.</li>
      <li>Connect to the session.</li>
      <li>Create a database called "osTicket".</li>
    </ul>
  </li>
</ol>

<h2>3. Install osTicket and configure it as a website running on this web server</h2>
<ol>
  <li>Install osTicket v1.15.8:</li>
  <ul>
    <li>Download osTicket.</li>
    <li>Extract and copy “upload” folder to C:\inetpub\wwwroot.</li>
    <li>Within C:\inetpub\wwwroot, rename “upload” to “osTicket”.</li>
    <li>Reload IIS (Open IIS, Stop and Start the server).</li>
  </ul>
  <li>Confirm osTicket is running through web server:</li>
  <ul>
    <li>Go to Sites -> Default -> osTicket -> “Browse *:80”.</li>
  </ul>
</ol>

<h2>4. Enable Features and assign permissions to osTicket</h2>
<ol>
  <li>Enable Extensions in PHP Manager:</li>
  <ul>
    <li>Enable: php_imap.dll</li>
    <li>Enable: php_intl.dll</li>
    <li>Enable: php_opcache.dll</li>
  </ul>
  <li>Rename ost-config.php:</li>
  <ul>
    <li>From: C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php</li>
    <li>To: C:\inetpub\wwwroot\osTicket\include\ost-config.php</li>
  </ul>
  <li>Assign Permissions: ost-config.php</li>
  <ul>
    <li>Disable inheritance -> Remove All.</li>
    <li>New Permissions -> Everyone -> All.</li>
  </ul>
</ol>

<h2>5. Complete installation by registering email and mySQL database</h2>
<ol>
  <li>Continue setting up osTicket in the browser (click Continue).</li>
  <li>Name Helpdesk.</li>
  <li>Default email (receives email from customers).</li>
  <li>MySQL Database: osTicket.</li>
  <li>MySQL Username: root.</li>
  <li>MySQL Password: (**********).</li>
  <li>Click “Install Now!”.</li>
</ol>

<h2>6. Confirm osTicket can be reached by users on LocalHost</h2>
<ol>
  <li>Test link for agents and end-users:</li>
  <ul>
    <li>Agents URL: <a href="http://localhost/osTicket/scp/login.php">http://localhost/osTicket/scp/login.php</a></li>
    <li>End Users URL: <a href="http://localhost/osTicket/">http://localhost/osTicket/</a></li>
  </ul>
</ol>

<h2>7. Clean up files that pose a security risk</h2>
<ol>
  <li>Delete: C:\inetpub\wwwroot\osTicket\setup.</li>
  <li>Set Permissions to “Read” only: C:\inetpub\wwwroot\osTicket\include\ost-config.php.</li>
</ol>


