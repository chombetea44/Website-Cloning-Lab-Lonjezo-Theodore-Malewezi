
# Website Cloning with SET 

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

  <img width="955" height="910" alt="Screenshot_2026-01-06_13_21_58" src="https://github.com/user-attachments/assets/1784eccf-68db-43ec-bbf0-98d50d92b50e" />
  
  **Option 2**
* 	Pick Credential Harvester Attack Method
  
  <img width="955" height="910" alt="Screenshot_2026-01-06_13_42_50" src="https://github.com/user-attachments/assets/54d1e456-d580-4ef8-9636-4c0d4d704712" />

  **Option 3**

*	Use Site Cloner
  
  **Option 2**
  
  <img width="955" height="910" alt="Screenshot_2026-01-06_14_31_00" src="https://github.com/user-attachments/assets/27a38844-87d3-4e7d-acb1-eef23af2b85f" />

3. 	Provide Target Information
* 	Enter the IP address of your Kali machine
  
  **10.6.6.1**
* Enter the URL of the site to be cloned
  
  **http://dvwa.vm**
4. Redirect Page Setup
* 	Create a simple HTML file with a meta refresh tag to redirect users to the cloned site.
  **ladies.html** 

<img width="1408" height="790" alt="Screenshot (6)" src="https://github.com/user-attachments/assets/c70ec058-d7e1-47a6-a047-cd857d5be5e4" />



 5.Testing the Clone
 * Open the HTML file in a browser.
   
   <img width="1439" height="796" alt="Screenshot (7)" src="https://github.com/user-attachments/assets/f94f9861-ace8-4922-ac36-40b5fbbd6ea5" />
   
 * Enter test credentials
   Username - **ladies@gmail.com**
   
   Password - **1234**
   
 * Observe how SET captures the login attempt in its reports.
   
 <img width="728" height="716" alt="Screenshot (8)" src="https://github.com/user-attachments/assets/cda145cc-0daa-4358-9f5f-78b4b9291d19" />
 

<img width="967" height="541" alt="Screenshot (11)" src="https://github.com/user-attachments/assets/b6607b89-3d2c-443a-9fae-21d6e2622928" />


 6.Exit SET
 * Use **Ctrl + C** and select **99** to quit.
   
 * Review captured data in the reports directory.

* Reports
SET stores captured credentials in XML reports under:  

**/root/.set/reports/**

* Example file:  

**2025-12-14 13:34:09.326665.xml**
## Conclusion

The website cloning exercise with SET (Social Engineering Toolkit) demonstrates how one can replicate legitimate sites to harvest credentials. By walking through the process in a controlled lab environment (e.g., DVWA). with this lab, we gain insight into the mechanics of phishing attacks and the importance of user awareness. This technique underscores why organizations must implement multi‑layered defenses such as SSL/TLS, phishing detection, user training, and monitoring of suspicious login activity.


# SMB Enumeration and Interaction with Kali Linux

## Overview
This repository demonstrates how to use tools like enum4linux, nmap and smbclient to enumerate and interact with SMB services in a controlled lab environment.

## Requirements
* Kali Linux
* enum4linux
* nmap
* smbclient
* A target VM with SMB enabled (e.g., Metasploitable2 or a lab server)

## Steps

1. Switch to Root
   
 **sudo su**



3. Explore enum4linux Options
   
**enum4linux -help**

This command displays available flags and usage of tool.

4. Scan Network with Nmap
   
**nmap -sN 172.17.0.0/24**

Performs a TCP NULL scan across the subnet to identify live hosts.

4.Enumerate SMB Information
Run different enum4linux flags against the target IP (172.17.0.2):

* enum4linux -U 172.17.0.2   # List users

* enum4linux -n 172.17.0.2   # Get NetBIOS info

* enum4linux -o 172.17.0.2   # OS information

* enum4linux -S 172.17.0.2   # Share enumeration

* enum4linux -Sv 172.17.0.2  # Verbose share enumeration

* enum4linux -P 172.17.0.2   # Password policy

* enum4linux -a 172.17.0.2   # All enumeration options


5. Explore smbclient
** smbclient --help**
**smbclient -L //172.17.0.2/**

This command lists available shares on the target.

6. Connect to a Share
   
**smbclient //172.17.0.2/tmp**

7. Create a Test File (Safe Example)
   
Instead of creating virus.exe, create a harmless text file:
nano testfile.txt


Type:
I am a student of Parocyber

8. Verify File
   
**ls**

**cat testfile.txt**



10. Upload File to SMB Share
    **put testfile.txt group_work.txt**
    
**Enter Directory to see uploaded file**

**quit**

This uploads your harmless file into the SMB share

## Conclusion

The SMB enumeration exercise using enum4linux, nmap and smbclient highlights how exposed network shares can reveal sensitive information to unauthorized users. By systematically probing for users, shares and policies, penetration testers can identify misconfigurations that attackers might exploit. Uploading and retrieving files in a lab environment illustrates the risks of weak access controls. This reinforces the need for proper SMB hardening, including disabling guest access, enforcing strong authentication and monitoring share activity.

























