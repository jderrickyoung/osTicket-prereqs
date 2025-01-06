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

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">Link to osTicket downloads Folder 

<h2>Installation Steps</h2>


### Step 1: Create a New VM

1. **Create a new VM and Resource Group** in the Azure Portal.
   

<p>
<img src="https://i.imgur.com/5nFBmMv.png"/>
</p>
<p>




   - Choose **Windows 10 Pro (22H2)** as the operating system.
   - Select a **Standard Size** with at least **2 vCPUs**.
   <p>
<img src="https://i.imgur.com/laytK5Y.png"/>
</p>
3. **Set up a username and password** for the VM.
<p>
<img src="https://i.imgur.com/jRMfwcY.png"/>
</p>
<p>
4. **Review and Create** the VM.

---

### Step 2: Open the VM Using Remote Desktop

1. On **macOS**, download the **Microsoft Remote Desktop** app from the App Store.

2. Add a PC by copying the **VM’s IP address** from Azure.
<p>
<img src="https://i.imgur.com/45iv4rT.png2" />
</p>
3. Enter your **credentials** and log into the Windows VM.
<p>
<img src="https://i.imgur.com/q0djIFd.png"/>
</p>
---

### Step 3: Install Required Software on the VM

For **osTicket** to work, you need to install a web server (IIS), PHP, and MySQL. Follow these steps:

1. **Download Software**  
   - Extract the contents of the <a href="https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6">**osTicket folder**</a>  and store it on your desktop for easy access.
</p>
<img src="https://i.imgur.com/Kk6hSSB.png"/>
</p>
2. **Enable IIS (Internet Information Services)**  
   - Open the **Control Panel** from the Start menu.
   - Navigate to **Programs** > **Turn Windows features on or off**.
   - Select **Internet Information Services (IIS)**.
   - In the drop-down menu, select **World Wide Web Services > Application Development Features** and enable **CGI**.
</p>
<img src="https://i.imgur.com/aZe8wbF.png"/>
</p>
3. **Install PHP**  
   - From the **osTicket folder** on your desktop, install the **PHP Manager** and **Rewrite Module**.
</p>
<img src="https://i.imgur.com/VSkLwxE.png"/>
</p>
</p>
<img src="https://i.imgur.com/qdpPktY.png"/>
</p>
4. **Install PHP**  
   - Navigate to **C:\** and create a new folder named **PHP**.
   - Extract the **PHP 7.3.8** files from the **osTicket folder** and copy them to the **PHP** folder.
</p>
<img src="https://i.imgur.com/gkygVZm.png"/>
</p>
</p>
<img src="https://i.imgur.com/zcDChZt.png"/>
</p>
5. **Install VC_redist**  
   - Run the **VC_redist** installer from the **osTicket folder**.
</p>
<img src="https://i.imgur.com/5XQZ7aG.png"/>
</p>
6. **Install MySQL**  
</p>
<img src="https://i.imgur.com/aK7G1N6.png"/>
</p>
   - Run the **MySQL installer** from the **osTicket folder**.
   - Select **Typical Setup** and check **Launch Configuration Wizard** after installation.
   - In the **Configuration Wizard**:
     - Select **Standard Configuration**.
     - Enable **Install as Windows Service**.
     - Create a **root password** (make sure to save it securely).
</p>
<img src="https://i.imgur.com/HmeHV9N.png"/>
</p>
7. **Configure IIS for PHP**  
   - From the Start menu, right-click **IIS** and select **Run as Administrator**.
 </p>
<img src="https://i.imgur.com/j3rUUFS.png"/>
</p>
   - Register PHP by opening **PHP Manager** and selecting **Register new PHP version**. Browse to the **PHP folder** on the C: drive and select **php-cgi**.
</p>
<img src="https://i.imgur.com/iey1EEu.png"/>
</p>
</p>
<img src="https://i.imgur.com/wvzW1TH.png"/>
</p>
- Reload IIS by clicking **Stop** and then **Start** the server.
</p>
<img src="https://i.imgur.com/7rsxRVc.png"/>
</p>
---

### Step 4: Install osTicket v1.15.8

1. **Copy osTicket Files**  
   - From the **osTicket folder** on your desktop, extract the **osTicket-Installation-Files** and copy the **upload** folder to `C:\inetpub\wwwroot`.
</p>
<img src="https://i.imgur.com/MttVvja.png"/>
</p>
2. **Rename the Upload Folder**  
   - Rename the **upload** folder to **osTicket**.
</p>
<img src="https://i.imgur.com/QS7Qtco.png"/>
</p>

3. **Reload IIS**  
   - Stop and restart the server in IIS Manager.

4. **Access the osTicket Installer**  
   - In IIS Manager, go to **Sites > Default Web Site > osTicket**.
   - Click **Browse *:80** in the right column to launch the osTicket installer in your web browser.
</p>
<img src="https://i.imgur.com/97Jmwnw.png"/>
</p>
</p>
<img src="https://i.imgur.com/GxpT0Vs.png"/>
</p>
5. **Enable Required PHP Extensions**  
   - Go back to **IIS Manager > Sites > Default Web Site > osTicket**.
</p>
<img src="https://i.imgur.com/mVNW0iq.png"/>
</p>   
   - Double-click **PHP Manager** and enable the following extensions:
     - `php_imap.dll`
     - `php_intl.dll`
     - `php_opcache.dll`
</p>
<img src="https://i.imgur.com/vPoQcNK.png"/>
</p>    
6. **Refresh the Web Browser**  
   - osTicket should now appear in the browser.
</p>
<img src="https://i.imgur.com/ctlhvDL.png"/>
</p>
7. **Rename the Configuration File**  
   - Navigate to `C:\inetpub\wwwroot\osTicket\include` and rename **ost-sampleconfig.php** to **ost-config.php**.
</p>
<img src="https://i.imgur.com/G20nWTS.png"/>
</p>
8. **Set File Permissions**  
   - Right-click **ost-config.php**, go to **Properties > Security > Advanced**.
   - Disable inheritance and remove inherited permissions.
   - Add a new permission for **Everyone** (or the appropriate users).
</p>
<img src="https://i.imgur.com/aqCDqtQ.png"/>
</p>
9. **Continue osTicket Setup**  
   - Go back to the osTicket installer in the web browser and complete the setup:
     - Enter the **Helpdesk Name**, **Support Email**, and **Admin Username** and **Password**.
</p>
<img src="https://i.imgur.com/Gdm512b.png"/>
</p>
---

### Step 5: Finalize the Installation

1. **Install HeidiSQL**  
   - From the **osTicket folder** on your desktop, install **HeidiSQL**.
</p>
<img src="https://i.imgur.com/H592mav.png"/>
</p>
<p>

2. **Set Up Database Connection**  
   - Open HeidiSQL and create a new session using the **root password** from Step 3.
   - Name your session and click **Open**.

3. **Complete Database Setup**  
   - Continue the setup in the web browser and click **Install**.

---

### Congratulations!

You have successfully installed **osTicket Help Desk Software**! 🎉

</p>
<img src="https://i.imgur.com/1Spx6nv.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

