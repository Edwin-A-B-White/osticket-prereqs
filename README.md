<p align="center">
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

- Windows 10 (21H2)

<h2>List of Prerequisites</h2>

- Microsoft Azure account and a Virtual Machine with Windows 10
- Remote Desktop access to the VM
- osTicket-Installation-Files.zip (downloadable from the official osTicket website)
- IIS (Internet Information Services) with CGI enabled
- PHP 7.3.8, PHP Manager for IIS, and Rewrite Module
- MySQL 5.5.62
- HeidiSQL for database management

<h2>Installation Steps</h2>

1. **Create a Virtual Machine on Microsoft Azure**
   - Log into your **Azure** portal.
   - Create a new Virtual Machine with Windows 10 (4 vCPUs).
   - Name the VM `osticket-vm` and set the username to `labuser` with the password `osTicketPassword1!`.

   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Azure VM creation process"/>
   </p>

2. **Remote Desktop Connection**
   - After the VM is created, connect to it using Remote Desktop Protocol (RDP).
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Remote Desktop Connection"/>
   </p>

3. **Download osTicket Installation Files**
   - Download the file `osTicket-Installation-Files.zip` and unzip it onto the desktop. The folder should be called `osTicket-Installation-Files`.
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Unzipping osTicket installation files"/>
   </p>

4. **Install IIS (Internet Information Services) with CGI**
   - Open **Control Panel** > **Programs and Features** > **Turn Windows Features on or off**.
   - Navigate to **World Wide Web Services** > **Application Development Features**, then check **CGI** to enable it.
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Installing IIS with CGI"/>
   </p>

5. **Install PHP Manager for IIS**
   - From the `osTicket-Installation-Files` folder, install the **PHP Manager for IIS** (PHPManagerForIIS_V1.5.0.msi).
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Installing PHP Manager for IIS"/>
   </p>

6. **Install Rewrite Module**
   - From the same folder, install the **Rewrite Module** (rewrite_amd64_en-US.msi).
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Installing IIS Rewrite Module"/>
   </p>

7. **Create PHP Directory**
   - Create a directory `C:\PHP` for PHP installation.
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Creating PHP directory"/>
   </p>

8. **Install PHP 7.3.8**
   - From the `osTicket-Installation-Files` folder, unzip **PHP 7.3.8** (php-7.3.8-nts-Win32-VC15-x86.zip) into the `C:\PHP` directory.
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Unzipping PHP into C:\PHP"/>
   </p>

9. **Install Visual C++ Redistributable**
   - From the installation files folder, install **VC_redist.x86.exe**.
   
   <p>
   <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Installing VC Redist"/>
   </p>

10. **Install MySQL 5.5.62**
    - From the installation files folder, install **MySQL 5.5.62** (mysql-5.5.62-win32.msi).
    - Choose **Typical Setup** and then **Launch Configuration Wizard**.
    - Set MySQL username to **root** and password to **root**.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Installing MySQL"/>
    </p>

11. **Register PHP with IIS**
    - Open IIS as an administrator.
    - In **PHP Manager**, register PHP by navigating to `C:\PHP\php-cgi.exe`.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Registering PHP with IIS"/>
    </p>

12. **Reload IIS**
    - Open IIS Manager, stop the server, and then start it again to reload the settings.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Reloading IIS"/>
    </p>

13. **Install osTicket v1.15.8**
    - Unzip **osTicket v1.15.8** (osTicket-v1.15.8.zip) from the `osTicket-Installation-Files` folder.
    - Copy the `upload` folder to `C:\inetpub\wwwroot` and rename it to `osTicket`.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Unzipping osTicket to wwwroot"/>
    </p>

14. **Reload IIS Again**
    - Open IIS Manager, stop and start the server again to reload the changes.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Reloading IIS Again"/>
    </p>

15. **Verify osTicket Installation**
    - Go to **Sites** > **Default** > **osTicket**, then click **Browse *:80** to verify the installation in the browser.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Verifying osTicket installation"/>
    </p>

16. **Enable PHP Extensions**
    - In IIS, go to **Sites** > **Default** > **osTicket**.
    - Double-click **PHP Manager**, then click **Enable or Disable an Extension**.
    - Enable the following extensions:
      - **php_imap.dll**
      - **php_intl.dll**
      - **php_opcache.dll**

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Enabling PHP Extensions in IIS"/>
    </p>

17. **Rename Configuration File**
    - Rename `ost-sampleconfig.php` to `ost-config.php` in `C:\inetpub\wwwroot\osTicket\include`.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Renaming ost-sampleconfig.php"/>
    </p>

18. **Assign Permissions to ost-config.php**
    - Right-click **ost-config.php** > **Properties**.
    - Disable inheritance, then remove all permissions.
    - Add **Everyone** with **Full Control** permissions.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Setting Permissions for ost-config.php"/>
    </p>

19. **Continue osTicket Setup in Browser**
    - In your browser, continue the osTicket setup.
    - Set up your helpdesk name and default email.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="osTicket setup page"/>
    </p>

20. **Install HeidiSQL**
    - From the installation files, install **HeidiSQL**.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Installing HeidiSQL"/>
    </p>

21. **Create Database in MySQL**
    - Open HeidiSQL and create a new session using the credentials **root/root**.
    - Connect to the session and create a new database called `osTicket`.
   
    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Creating Database in HeidiSQL"/>
    </p>

22. **Complete osTicket Setup**
    - Go back to the osTicket browser setup.
    - Enter the database name `osTicket`, and the MySQL username and password as **root/root**.
    - Click **Install Now!**.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Completing osTicket installation"/>
    </p>

23. **Finish Installation**
    - Once installed, navigate to `http://localhost/osTicket/scp/login.php` to access the admin login page.
    - End users can access the help desk at `http://localhost/osTicket/`.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="osTicket login page"/>
    </p>

24. **Cleanup**
    - Delete the **setup** folder from `C:\inetpub\wwwroot\osTicket\setup`.
    - Set permissions for **ost-config.php** to **Read-only**.

    <p>
    <img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Deleting setup folder"/>
    </p>

Congratulations! osTicket is now installed and ready to use.


