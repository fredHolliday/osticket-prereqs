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

- Windows 10</b> (21H2)

<h2>List of Prerequisites</h2>


# **Installing osTicket on Azure: Step-by-Step Guide**

## **1. Set Up a Virtual Machine in Azure**
1. **Log in to the Azure Portal** ([https://portal.azure.com](https://portal.azure.com)).
2. **Create a Resource Group** (if not already created).
3. **Deploy a Virtual Machine (VM):**  
   - Navigate to **Virtual Machines** → Click **"Create"** → Select **"Azure Virtual Machine"**.  
   - Choose **"Windows 10 Virtual Machine (VM) with 2 Virtual CPUs"** as the image.  
   - Complete the configuration and wait for deployment.  
4. **Log into the VM using Remote Desktop (RDP).**

## **2. Install and Configure IIS**
1. Open **Server Manager** → Click **Manage** → **Add Roles and Features**.
2. Select **"Role-based or feature-based installation"** → Choose your server.
3. In **Server Roles**, select **Web Server (IIS)**.
4. Under **IIS Features**, check:
   - **World Wide Web Services**
   - **Application Development Features** → Enable **CGI**
5. Click **Next → Install** and wait for installation to complete.

## **3. Install Required Software**
1. **Install PHP Manager for IIS.**
2. **Install URL Rewrite Module:** `rewrite_amd64.msi`.
3. **Set Up PHP:**
   - Create a directory: `C:\PHP`  
     *(File Explorer → C: Drive → Right-click → New Folder → Name it PHP)*.
   - Download **PHP 7.3.8** (`php-7.3.8-nts-Win32-VC15-x86.zip`).
   - Extract the contents to **C:\PHP**.
4. **Install Additional Dependencies:**
   - Install **VC_redist.x86.exe** (Visual C++ Redistributable).
   - Install **MySQL 5.5.62**:
     - Choose **Typical Installation** → Click **Next** → **Install** → **Finish**.
     - Select **Standard Configuration** → Click **Next**.
     - Set up **Username/Password**.

## **4. Configure IIS for PHP**
1. Open **IIS Manager as Administrator**.
2. Register PHP inside IIS:
   - Open **PHP Manager**.
   - Set PHP path to **C:\PHP**.
3. Reload IIS:
   - **Open IIS** → Click **Stop** → Click **Start**.

## **5. Install osTicket v1.15.8**
1. Download osTicket from the official website or **Installation Files Folder**.
2. Extract and **copy the "upload" folder** to `C:\inetpub\wwwroot`.
3. Rename `upload` to **osTicket**.
4. Restart IIS:
   - **Open IIS** → Click **Stop** → Click **Start**.
5. On the right panel, click **"Browse *:80"** to open the osTicket site.

## **6. Configure PHP Extensions for osTicket**
1. Open **PHP Manager in IIS**.
2. Click **Enable or Disable Extensions**.
3. Enable the following:
   - `php_imap.dll`
   - `php_intl.dll`
   - `php_opcache.dll`
4. Refresh the osTicket site.

## **7. Configure osTicket Configuration File**
1. Rename the configuration file:
   - **From:** `C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php`
   - **To:** `C:\inetpub\wwwroot\osTicket\include\ost-config.php`
2. **Set Permissions for ost-config.php:**
   - Disable **inheritance** → Remove all existing permissions.
   - Add **new permissions**:
     - **User:** Everyone
     - **Permissions:** Full Control

## **8. Complete osTicket Setup in Browser**
1. Open osTicket setup page in a browser.
2. Enter **Helpdesk Name** and **Default Email** (used for customer inquiries).

## **9. Set Up MySQL Database Using HeidiSQL**
1. **Install HeidiSQL** (from the Installation Files folder).
2. Open **HeidiSQL** and create a new session.
3. Use credentials:
   - **Username:** `root`
   - **Password:** `Password1`
4. Connect to the session.
5. **Create the osTicket database:**
   - Name: **osTicket**

## **10. Finalize osTicket Installation**
1. Continue osTicket setup in the browser.
2. Enter **Database Information**:
   - **MySQL Database:** `osTicket`
   - **MySQL Username:** `root`
   - **MySQL Password:** `Password1`
3. Click **"Install Now!"**.

## **11. Access osTicket**
- **Admin Panel:** `http://localhost/osTicket/scp/login.php`
- **Helpdesk Portal:** `http://localhost/osTicket/
🎉 **Congratulations! osTicket is now successfully installed!** 🚀

  
<img src="https://i.imgur.com/hpFYz0e.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<!-- <p>
Osticket has been installed. Next, you will need to go ahead and configure it in the admin panel—login to the help desk page.

</p>
<br />
-->
<p>
<img src="https://i.imgur.com/BRGXE85.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
When you log in your default page will be the admin page this is where you configure your Roles, Departments, and Teams.

</p>
<br />

<p>
<img src="https://i.imgur.com/sMnpC9p.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, you need to set up your SLA. SLA is the response time to a call, I set up SLA A, SLA B, and SLA C.
SAL A- is 1 hour 24/7, SLA B- is 3 hours 24/7, SLA C- 8 hours Business hours.

</p>

<br />

<p>
<img src="https://i.imgur.com/25k0ful.jpeg" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next is the end users page. Where the end users can open a ticket.
</p>
