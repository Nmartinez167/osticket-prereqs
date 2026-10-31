
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>

# osTicket Help Desk Deployment on Microsoft Azure

## Project Overview

This project documents a hands-on deployment of **osTicket**, an open-source help desk and ticketing platform, on a Microsoft Azure virtual machine.

The lab covers provisioning a Windows virtual machine, preparing IIS and PHP, installing MySQL, configuring osTicket, and verifying that the application loads in a browser. It demonstrates foundational tasks relevant to an entry-level **Help Desk / IT Support Technician** role, including system setup, web application deployment, database configuration, and basic troubleshooting.

## Technologies Used

- **Microsoft Azure** — virtual machine hosting
- **Windows 11** — lab operating system
- **Remote Desktop Protocol (RDP)** — remote administration
- **Internet Information Services (IIS)** — web server
- **PHP** — application runtime
- **MySQL** — relational database
- **HeidiSQL** — database administration
- **osTicket** — help desk ticketing platform

## Lab Environment

| Component | Lab configuration |
|---|---|
| Cloud provider | Microsoft Azure |
| Virtual machine | `osticket-vm` |
| Operating system | Windows 11 21H2 |
| CPU | 4 vCPUs *(verify against the deployed VM)* |
| Web server | IIS |
| PHP | 7.3.8 |
| Database | MySQL 5.5.62 |
| osTicket | 1.15.8 |

<img width="50%" height="50%" alt="mermaid-diagram" src="https://github.com/user-attachments/assets/9bdfd374-d8aa-4654-b7c8-9beb7670dcb2" />

> **Legacy lab notice:** This README documents the software versions used in the original learning environment. PHP 7.3.8, osTicket 1.15.8, and Windows 11 21H2 are legacy versions and should not be treated as a current production deployment. Keep the historical setup documented accurately; use currently supported releases and dependencies for a new deployment.

## Prerequisites

- An Azure subscription and resource group
- A Windows virtual machine
- Remote Desktop client
- IIS with CGI enabled
- PHP installation package and required Visual C++ runtime
- MySQL installation package
- osTicket installation package
- HeidiSQL
- IIS URL Rewrite module
- PHP Manager for IIS (if used in this lab)

## Deployment Steps

### 1. Create and configure the Azure virtual machine

1. Sign in to the [Microsoft Azure portal](https://portal.azure.com/).
2. Open **Virtual machines** and select **Create**.
3. Configure the VM name as `osticket-vm`.
4. Select Windows 11 and the appropriate subscription and resource group.
5. Choose the VM size and record the actual CPU and memory configuration.
6. Configure administrator credentials, review the settings, and deploy the VM.
7. After deployment, retrieve the VM's public IP address and connect with Remote Desktop.

<img width="50%" height="50%" alt="Screenshot 2026-01-13 081342" src="https://github.com/user-attachments/assets/efcc6fbc-7d97-4793-b588-61a3777e84f9" />

<img width="50%" height="50%" alt="Screenshot 2026-10-01 095543" src="https://github.com/user-attachments/assets/b3d3f468-9562-4e2c-a0a2-14104fddd4df" />

<img width="50%" height="50%" alt="Screenshot 2026-01-15 090926" src="https://github.com/user-attachments/assets/6108a7ba-bd44-4bb3-8aff-bbe8522593d7" />

<img width="50%" height="50%" alt="Screenshot 2026-01-15 092735" src="https://github.com/user-attachments/assets/cf9dab37-40b3-48bd-9e29-b416922dbafa" />

**Security:** Do not expose RDP (TCP 3389) to the entire internet. Restrict inbound access to a trusted IP address or use Azure Bastion where available. Use a strong, unique administrator password.

### 2. Prepare the virtual machine

1. Connect to the VM using Remote Desktop.
2. Download the installation packages needed for the lab.
3. Create a folder on the desktop named `osTicket-Installation-Files`.
4. Extract or organize the installation files in that folder.

<img width="50%" height="50%" alt="Screenshot 2026-10-01 081531" src="https://github.com/user-attachments/assets/ddf2e3b3-a16d-465c-b860-acc649651137" />

### 3. Install IIS and enable CGI

1. Open **Control Panel**.
2. Select **Programs → Turn Windows features on or off**.
3. Enable **Internet Information Services**.
4. Expand **World Wide Web Services → Application Development Features**.
5. Enable **CGI** and apply the changes.
6. Open IIS Manager and confirm that the web server is available.

IIS hosts the web application. CGI provides the handler support needed for PHP through IIS.

<img width="50%" height="50%" alt="Screenshot 2026-01-15 154456" src="https://github.com/user-attachments/assets/2891c3cf-ade6-4821-8bda-f5a651c4e28b" />

<img width="50%" height="50%" alt="Screenshot 2026-01-15 155008" src="https://github.com/user-attachments/assets/dc9f59f3-9f8b-475b-b894-56a6c4628397" />

<img width="50%" height="50%" alt="Screenshot 2026-01-15 155306" src="https://github.com/user-attachments/assets/01652198-1021-4263-929d-43e00240c22b" />

### 4. Install PHP Manager and URL Rewrite

1. Install PHP Manager for IIS, as used in this lab.
2. Install the IIS URL Rewrite module.
3. Open IIS Manager and confirm that the relevant modules are available.

These tools assist with configuring PHP and URL rewriting in IIS.

<img width="50%" height="50%" alt="day1" src="https://github.com/user-attachments/assets/40a0af56-b5d1-408d-98a3-ef65ef9fdcc7" />

<img width="50%" height="50%" alt="day 2" src="https://github.com/user-attachments/assets/820b9b79-119a-45d8-926e-05459e509aca" />

### 5. Install and configure PHP

1. Create the directory `C:\PHP`.
2. Extract the lab's PHP 7.3.8 package into `C:\PHP`.
3. Install the matching Microsoft Visual C++ Redistributable (`VC_redist.x86.exe` for the package used in this lab).
4. In IIS Manager, open PHP Manager and register `C:\PHP\php-cgi.exe`.
5. Configure the PHP extensions required by osTicket. The original lab enabled:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`
6. Confirm that the required database driver is enabled as well. For MySQL connectivity, verify that **MySQLi** is enabled in the PHP configuration.
7. Restart IIS after making configuration changes.

<img width="50%" height="50%" alt="day3" src="https://github.com/user-attachments/assets/5567e8c3-d65b-4950-8686-d578cc8d91c8" />

<img width="50%" height="50%" alt="day4" src="https://github.com/user-attachments/assets/782376bb-c813-4a6e-9a4c-6828b0b24284" />

<img width="50%" height="50%" alt="DAY5" src="https://github.com/user-attachments/assets/a46e099d-9003-49ef-9711-36f15cabf9db" />

<img width="50%" height="50%" alt="Day6" src="https://github.com/user-attachments/assets/59af6bfc-825f-42a0-bbb3-df07f802fd25" />

<img width="50%" height="50%" alt="day7" src="https://github.com/user-attachments/assets/74265067-733c-4223-bd97-2c9bbbfa2cdd" />

> The screenshots document the original PHP setup. Extension names and configuration can vary by PHP release; verify the extension files and PHP configuration that match the version actually installed.

### 6. Install MySQL

1. Install MySQL 5.5.62 using the installer included with the original lab.
2. Choose **Typical Setup**.
3. Launch the MySQL Configuration Wizard.
4. Select **Standard Configuration** for this lab.
5. Set and securely store the MySQL administrator credentials.

<img width="50%" height="50%" alt="Screenshot 2026-01-29 145223" src="https://github.com/user-attachments/assets/660f5b94-1f5d-4379-bf41-30d4c274016a" />

<img width="50%" height="50%" alt="Screenshot 2026-01-29 145533" src="https://github.com/user-attachments/assets/3b67c008-74be-4eea-9f2c-0229659f9134" />

<img width="50%" height="50%" alt="Screenshot 2026-01-29 145854" src="https://github.com/user-attachments/assets/9e1da928-b1dc-4ebb-bbb0-ae388698ff0e" />

<img width="50%" height="50%" alt="Screenshot 2026-01-29 150206" src="https://github.com/user-attachments/assets/dc4a570c-ea3f-4f13-a223-69d0ae2a8151" />

> **Credential safety:** The original walkthrough showed a simple `root` password. Do not reuse that password or expose administrator credentials in a public repository. Use a strong, unique password for the database administrator. The osTicket application should connect with a separate, dedicated database account—not the MySQL `root` account.

### 7. Verify PHP in IIS

1. Open IIS Manager as an administrator.
2. In PHP Manager, register `C:\PHP\php-cgi.exe` if it has not already been registered.
3. Confirm that IIS is configured to use the intended PHP executable.
4. Restart the IIS site or web server.
5. Test that PHP is being processed by IIS before continuing with the osTicket installer.

<img width="50%" height="50%" alt="qwewert" src="https://github.com/user-attachments/assets/b3fd19d4-5232-4179-b777-ea198223576e" />

<img width="50%" height="50%" alt="assddd" src="https://github.com/user-attachments/assets/dfdadd3d-4001-4da8-b4b4-62f2c588fd4b" />

<img width="50%" height="50%" alt="v" src="https://github.com/user-attachments/assets/f785de48-b9dc-479c-a4fe-d6466c1bdffc" />

<img width="50%" height="50%" alt="r" src="https://github.com/user-attachments/assets/a6aba362-c9eb-43d0-be0c-b20e5c81fbe0" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 153733" src="https://github.com/user-attachments/assets/05c11e74-44f8-49f7-b29f-fdd07bd81678" />

### 8. Install osTicket

1. Extract the osTicket 1.15.8 archive from `osTicket-Installation-Files`.
2. Copy the extracted `upload` folder to `C:\inetpub\wwwroot`.
3. Rename the copied folder to `osTicket`.
4. Restart or refresh IIS.
5. In IIS Manager, navigate to **Sites → Default Web Site → osTicket**.
6. Use **Browse** to open the site.
7. If the installer reports missing PHP extensions, review the PHP configuration and enable the required extensions for the installed PHP version. The original lab enabled `php_imap.dll`, `php_intl.dll`, and `php_opcache.dll`; also verify MySQLi support.
8. Refresh the osTicket installer in the browser.

<img width="50%" height="50%" alt="Screenshot 2026-01-30 161608" src="https://github.com/user-attachments/assets/cf61823d-fbd2-412f-bd94-2b2eed44bb50" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 162152" src="https://github.com/user-attachments/assets/38f91f6f-5c97-4f61-8e4a-5be20f1008e2" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 162536" src="https://github.com/user-attachments/assets/6093108e-8036-42d9-af61-b5bdfeb6610f" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 162706" src="https://github.com/user-attachments/assets/f80926f8-d2d9-40b9-b45c-f42ba8235f38" />

<img width="50%" height="50%" alt="Screenshot 2026-01-30 163758" src="https://github.com/user-attachments/assets/9b499f50-1312-4ac0-892b-ffa091256db2" />

<img width="50%" height="50%" alt="g1" src="https://github.com/user-attachments/assets/bef74b02-7ba9-440a-8266-992560ae105d" />

<img width="50%" height="50%" alt="g2" src="https://github.com/user-attachments/assets/329f504e-93cc-4bc0-9099-e283f7043179" />

<img width="50%" height="50%" alt="g3" src="https://github.com/user-attachments/assets/af5cf434-9d9a-4c55-a441-6dc92145c9c0" />

<img width="50%" height="50%" alt="g4" src="https://github.com/user-attachments/assets/cd6fe3a6-4adb-44ef-8453-6626e29c6f5f" />

<img width="50%" height="50%" alt="g6" src="https://github.com/user-attachments/assets/654f4dac-793e-412a-85a8-d2fe44c48350" />

<img width="50%" height="50%" alt="G7" src="https://github.com/user-attachments/assets/1707671a-9898-43e6-84d6-dce86a47d72f" />

### 9. Configure osTicket

1. In File Explorer, locate:
   `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
2. Create the configuration file expected by the installer by copying or renaming the sample file to:
   `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
3. Grant the IIS application identity only the permissions needed to complete installation. If the installer requires write access to `ost-config.php`, grant that access temporarily.
4. Complete the browser-based setup:
   - Enter a help desk name.
   - Enter the default email address for the help desk.
   - Continue through the installer prompts.

<img width="50%" height="50%" alt="back2it" src="https://github.com/user-attachments/assets/95cf7d6a-f246-492e-ab19-37dc08bc99e5" />

<img width="50%" height="50%" alt="ber" src="https://github.com/user-attachments/assets/1edbe768-b14b-461b-90fb-d1225a356aab" />

<img width="50%" height="50%" alt="mmm" src="https://github.com/user-attachments/assets/3c3a3652-406f-4dff-be7c-34fcd43ad421" />

<img width="50%" height="50%" alt="treee" src="https://github.com/user-attachments/assets/082c9b94-1d13-4bb4-bf49-a40b2f653d66" />

<img width="50%" height="50%" alt="nnnnnnn" src="https://github.com/user-attachments/assets/4e89a436-98ab-4bfa-ac4b-6dbe608d0672" />

<img width="50%" height="50%" alt="vvvvv" src="https://github.com/user-attachments/assets/55935644-2a21-4ee5-974a-4de9c3d35ae6" />

<img width="50%" height="50%" alt="llllllllll" src="https://github.com/user-attachments/assets/148fac7d-3ade-4a9c-bf72-007d292dff2c" />

<img width="50%" height="50%" alt="bbbbbb" src="https://github.com/user-attachments/assets/c6413fdf-d929-4db3-b40e-3070d1701b1b" />

> **Important permissions correction:** The original screenshots show `Everyone → Full Control`. That is overly permissive and is not a safe general recommendation. Do not grant Everyone Full Control. Use the narrowest permissions required for the IIS application identity, then remove installer-time write access after setup. Protect `ost-config.php` from unauthorized access.

### 10. Create the osTicket database and application account

1. Open HeidiSQL and create a session to the local MySQL server.
2. Connect using the MySQL administrator account.
3. Create a database named `osTicket`.
4. Create a dedicated MySQL account for osTicket and grant it privileges only on the `osTicket` database.
5. Return to the osTicket installer and enter:
   - **Database name:** `osTicket`
   - **Database username:** the dedicated application account
   - **Database password:** the strong password assigned to that account
   - **Database host:** `localhost`
6. Select **Install Now** and follow the installer prompts.

Example SQL for creating the database and a dedicated local application account (replace the password placeholder with a strong, unique password before running):

```sql
CREATE DATABASE osTicket;

CREATE USER 'osticket_app'@'localhost'
IDENTIFIED BY 'REPLACE_WITH_A_STRONG_PASSWORD';

GRANT ALL PRIVILEGES ON osTicket.*
TO 'osticket_app'@'localhost';

FLUSH PRIVILEGES;
```

Do not commit real passwords, connection strings, or other secrets to GitHub.

<img width="50%" height="50%" alt="kkkkkk" src="https://github.com/user-attachments/assets/0ee1be17-bf4a-4543-969e-fa5668e8fa7a" />

<img width="50%" height="50%" alt="fffffff" src="https://github.com/user-attachments/assets/40000d11-4b4b-4707-b811-025a57068a3e" />

<img width="50%" height="50%" alt="eeeeeeeeeeeee" src="https://github.com/user-attachments/assets/de13495b-80bb-4a43-931f-d8add5548d0a" />

<img width="50%" height="50%" alt="cccccc" src="https://github.com/user-attachments/assets/8dca788e-35de-4361-89d6-b288f3fa66a4" />

<img width="50%" height="50%" alt="!!!!" src="https://github.com/user-attachments/assets/5321322b-f245-4dad-8a4c-c0f7bbd06a0e" />

<img width="50%" height="50%" alt="!!!!" src="https://github.com/user-attachments/assets/79e6c897-3c7e-40b0-b791-1d072c3f00bf" />

### 11. Verify the installation

1. Confirm that the installer reports a successful installation.
2. Open the end-user portal and confirm that the page loads.
3. Open the staff control panel and confirm that the agent login page loads.
4. Use the VM itself for the `localhost` URLs below:
   - **End-user portal:** `http://localhost/osTicket/`
   - **Staff control panel:** `http://localhost/osTicket/scp/login.php`

`localhost` refers to the computer making the request. These links work from a browser running on the VM; they do not automatically provide remote users access from their own computers. For remote access, use the VM's configured hostname or IP address and configure network access and HTTPS appropriately.

<img width="50%" height="50%" alt="hpn" src="https://github.com/user-attachments/assets/5b719abd-3fe6-4289-b311-b73528628bcc" />

## Security and Cleanup Checklist

- [ ] Restrict RDP access to trusted sources or use Azure Bastion.
- [ ] Use strong, unique administrator and database passwords.
- [ ] Use a dedicated MySQL application account instead of `root`.
- [ ] Do not grant `Everyone` Full Control to application files.
- [ ] Remove temporary write permissions from `ost-config.php` after setup.
- [ ] Remove or disable the osTicket setup directory after installation, as recommended by the installer/documentation.
- [ ] Keep secrets, passwords, and private configuration files out of GitHub.
- [ ] Use supported software versions and HTTPS for any production deployment.

## Skills Demonstrated

- Provisioning and accessing a Windows virtual machine in Microsoft Azure
- Administering Windows through Remote Desktop
- Installing and configuring IIS
- Registering PHP with IIS and checking PHP extensions
- Installing MySQL and administering a database with HeidiSQL
- Deploying and configuring a web-based help desk application
- Reviewing file permissions and basic deployment security
- Documenting installation steps and troubleshooting checkpoints

- Change its priority and status.
- Add an internal note and a public response.
- Resolve and close the ticket.
- Document one troubleshooting scenario, the symptoms, the steps taken, and the resolution.

