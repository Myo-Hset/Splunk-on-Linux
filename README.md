# Splunk-on-Linux

## Objective

This project provides a step‑by‑step guide for installing Splunk Enterprise (60‑Day Trial) on Ubuntu Server (Linux)

### Skills Learned
- Splunk Deployment: Learned how to install Splunk Enterprise from a .deb package and verify its installation on Linux.

### Tools Used

- Splunk Enterprise (60‑Day Trial) – SIEM platform installed for monitoring and analysis
- Ubuntu Server (22.04.5) – Operating system for hosting Splunk.
____________________________________________________________________________________________
#### Step 1:  SSH into Ubuntu
After installing Ubuntu Server in a virtual machine, I established an SSH connection using PowerShell. This setup makes it easier to copy and paste commands.
##### Note
- I use **VMware Virtual Machine**  
- I use **Ubuntu Server version 22.04.5**  
- For the Splunk server, I allocated **4 GB of RAM** and **50 GB of storage**
#### Step 2: Update Packages
Run the following command to update your system:**sudo apt-get update && sudo apt-get upgrade -y**
#### Step 3: Download Splunk Trial
Log in to Splunk’s website and download the Enterprise Free Trial (you’ll get 60 days free) : **wget...amd64.deb"**
https://www.splunk.com/en_us/download.html.
<img width="1113" height="552" alt="image" src="https://github.com/user-attachments/assets/82fb45b8-8e5e-4c2b-9981-b11ef4fc52f5" />

#### Step 4 : Install the downloaded Splunk package
After downloading the .deb file, install it using the following command: **sudo dpkg -i splunk-10.0.2-e2d18b4767e9-linux-amd64.deb**
<img width="831" height="241" alt="image" src="https://github.com/user-attachments/assets/41aec6c5-333c-4ccc-8729-be6988d2b94c" />
#### Step 5: Verify Installation Directory
After installation, Splunk should be located in the following directory: **/opt/splunk/**
<img width="1749" height="44" alt="image" src="https://github.com/user-attachments/assets/556ea3aa-9c7b-48fe-8692-0e440dd5f53b" />
If you run the command: **ls -la /opt/splunk**
You will notice that the account and group ownership are set to splunk. This is a good security practice because it limits permissions to the Splunk user, helping to protect the system.
<img width="1749" height="382" alt="image" src="https://github.com/user-attachments/assets/32d64c19-7b68-4fa9-bbf9-1396eb08cc29" />
#### Step 6: Switch to the Splunk User
Change to the splunk user account: **sudo -u splunk bash**. After switching, navigate to the Splunk bin directory, which contains all the Splunk binaries: **cd /opt/splunk/bin**
<img width="1749" height="382" alt="image" src="https://github.com/user-attachments/assets/79239879-c005-4e50-bf93-c38b446dbad5" />
#### Step 7: Start Splunk
From the  directory, start Splunk with the following command:**./splunk start**
This will initialize Splunk for the first time. During this process, you’ll be prompted to create an admin username and password. These credentials will be used to log in to the Splunk web interface.
<img width="417" height="22" alt="image" src="https://github.com/user-attachments/assets/a1c8777d-b2dd-426a-b8ea-f78f4b9ff072" />
<img width="959" height="184" alt="image" src="https://github.com/user-attachments/assets/af8c4524-0481-40c4-a999-256dfdaf84f1" />
#### Step 8: Enable Splunk to Auto-Start on Boot
To ensure Splunk runs automatically every time the VM reboots:
###### 1. 	Exit from the splunk user: **exit**
###### 2. 	Navigate back to the Splunk  directory: **cd /opt/splunk/bin**
###### 3. 	Run the following command to enable auto-start: **sudo ./splunk enable boot-start -user splunk**
This will configure Splunk to start automatically whenever the system restarts.
<img width="927" height="187" alt="image" src="https://github.com/user-attachments/assets/a04ca35a-38fd-425f-a12d-88df0d81c378" />
#### Step 9: Access Splunk Web UI
Now Splunk is configured to run automatically at boot. 
You can access Splunk from your web browser at: **http://<host-ip>:8000**
<img width="1886" height="925" alt="image" src="https://github.com/user-attachments/assets/298de5ce-34a6-46a5-bb1d-088d5a5c264a" />
#### Final Step: Splunk is now fully installed and accessible on Ubuntu.
















