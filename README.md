
# Website Cloning with SET (Educational Use Only)

## Overview
This repository demonstrates how website cloning works using the Social Engineering Toolkit (SET) on Kali Linux.
Website cloning is a penetration testing technique used to replicate a legitimate site in order to test how users respond to phishing scenarios.

Disclaimer: This project is for educational purposes only. Use it exclusively in controlled environments such as DVWA (Damn Vulnerable Web App) or other authorized lab setups. Do not attempt these techniques on real systems without explicit permission.

## Requirements
* 	Kali Linux
* 	Social Engineering Toolkit (SET)
* 	DVWA or another intentionally vulnerable web application
* 	Root privileges

## Steps 
1. 	Launch SET
   
* Switch to root user
  
  **sudo su**
* 	Start SET
  
  **setoolkit**
  	
2. 	Select Attack Vectors
   SET is launched, you now follow the different options displayed.
*	Choose Social Engineering Attacks
  
  **Option 1**
* 	Select Website Attack Vectors
  
  **Option 2**
* 	Pick Credential Harvester Attack Method
  
  **Option 3**

*	Use Site Cloner
  
  **Option 2**
3. 	Provide Target Information
* 	Enter the IP address of your Kali machine
  
  **10.6.6.1**
* Enter the URL of the site to be cloned
  
  **http://dvwa.vm**
4. Redirect Page Setup
* 	Create a simple HTML file with a meta refresh tag to redirect users to the cloned site.
  
**ladies.html** 

 5.Testing the Clone
 * Open the HTML file in a browser.
 * Enter test credentials
   Username - **ladies@gmail.com**
   
   Password - **1234**
   
 * Observe how SET captures the login attempt in its reports.

 6.Exit SET
 * Use **Ctrl + C** and select **99** to quit.
   
 * Review captured data in the reports directory.

# Website Cloning with SET (Educational Use Only)

## Reports
SET stores captured credentials in XML reports under:  

/root/.set/reports/


Example file:  

2025-12-14 13:34:09.326665.xml

The website cloning exercise with SET (Social Engineering Toolkit) demonstrates how attackers can replicate legitimate sites to harvest credentials. By walking through the process in a controlled lab environment (e.g., DVWA), we gain insight into the mechanics of phishing attacks and the importance of user awareness. This technique underscores why organizations must implement multi‑layered defenses such as SSL/TLS, phishing detection, user training, and monitoring of suspicious login activity.


SMB Enumeration and Interaction with Kali Linux
📖 Overview
This repository demonstrates how to use tools like enum4linux, nmap, and smbclient to enumerate and interact with SMB services in a controlled lab environment.
⚠️ Disclaimer: This project is for educational purposes only. Use it exclusively in controlled environments such as test VMs or intentionally vulnerable machines. Do not attempt these techniques on real systems without explicit permission.

Requirements
- Kali Linux
- enum4linux
- nmap
- smbclient
- A target VM with SMB enabled (e.g., Metasploitable2 or a lab server)

Steps (Conceptual Explanation)
1. Switch to Root
sudo su



2. Explore enum4linux Options
enum4linux -help


Displays available flags and usage.

3. Scan Network with Nmap
nmap -sN 172.17.0.0/24
Performs a TCP NULL scan across the subnet to identify live hosts.

4.Enumerate SMB Information
Run different enum4linux flags against the target IP (172.17.0.2):
enum4linux -U 172.17.0.2   # List users
enum4linux -n 172.17.0.2   # Get NetBIOS info
enum4linux -o 172.17.0.2   # OS information
enum4linux -S 172.17.0.2   # Share enumeration
enum4linux -Sv 172.17.0.2  # Verbose share enumeration
enum4linux -P 172.17.0.2   # Password policy
enum4linux -a 172.17.0.2   # All enumeration options

5. Explore smbclient
smbclient --help
smbclient -L //172.17.0.2/


Lists available shares on the target.

6. Connect to a Share
smbclient //172.17.0.2/tmp


Accesses the tmp share.
Inside smbclient, you can use:
help
dir


7. Create a Test File (Safe Example)
Instead of creating virus.exe, create a harmless text file:
nano testfile.txt


Type:
I am a student of Parocyber

8. Verify File
ls
cat testfile.txt



9. Upload File to SMB Share
    put testfile.txt group_work.txt
dir
quit

This uploads your harmless file into the SMB share

The SMB enumeration exercise using enum4linux, nmap, and smbclient highlights how exposed network shares can reveal sensitive information to unauthorized users. By systematically probing for users, shares, and policies, penetration testers can identify misconfigurations that attackers might exploit. Uploading and retrieving files in a lab environment illustrates the risks of weak access controls. This reinforces the need for proper SMB hardening, including disabling guest access, enforcing strong authentication, and monitoring share activity.

























