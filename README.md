# Active Directory Home Lab  

## Overview  

A Windows Server 2022 Active Directory lab environment with centralized authentication,  
DHCP, DNS, file services, NTFS permissions and Group Policy management.

This project demonstrates a small enterprise-style Windows infrastructure with user management, access control 
and policy-based configuration

     
---  
## Environment

- Windows Server 2022  
- Windows 11 Client  
- Active Directory Domain Services  
- Domain: lab.local  

---  
## Network Configuration  

Domain Controller:  


SRV-DC-01  
IP: 192.168.10.10  

Client:  
WIN11-CLIENT-01  
IP: 192.168.10.100  

Network:  
LABNET  
192.168.10.0/24  

---  
# Implemented Features

## Active Directory

Configured:

- Domain Controller
- Users
- Security Groups
- Organizational Units

Users:  

IT_Admins Group:  
georgepap  

Sales_Users Group:  
mariakon  

Domain Users only:  
johnmarkou

Screenshot:  

![Active Directory Users](screenshots/01_ad_users.png)  

---

# DHCP Configuration  

Configured DHCP scope:    
Scope:  
192.168.10.0/24  

Range:  
192.168.10.100 - 192.168.10.200  


Client receives IP automatically from DHCP.  

Screenshots:  

![DHCP Scope](screenshots/03_dhcp_scope.png)  

![DHCP Lease](screenshots/04_dhcp_lease.png)  

---

# DNS Configuration    

Configured internal DNS records for:    
lab.local  
SRV-DC-01  
WIN11-CLIENT-01  

Screenshot:  

![DNS Records](screenshots/05_dns.png)  

---

# File Server   
Created SMB share:  

``` Structure: ``` CompanyData ├── IT └── Sales ``` Screenshot: ![File Share](screenshots/06_file_share.png) --- # NTFS Permissions Access is controlled using Security Groups. ## IT Folder Permissions: ``` SYSTEM Administrators IT_Admins ``` Screenshot: ![IT Permissions](screenshots/07_it_permissions.png) ## Sales Folder Permissions: ``` SYSTEM Administrators Sales_Users ``` Screenshot: ![Sales Permissions](screenshots/08_sales_permissions.png) --- # Group Policy Management Created Group Policies for automatic network drive mapping. ## Sales Users Mapped: ``` S: \\SRV-DC-01\CompanyData\Sales ``` Applied to: ``` Sales_Users ``` Screenshot: ![Sales Drive Mapping](screenshots/09_gpo_sales_drive.png) ## IT Users Mapped: ``` I: \\SRV-DC-01\CompanyData\IT ``` Applied to: ``` IT_Admins ``` Screenshot: ![IT Drive Mapping](screenshots/10_gpo_it_drive.png) --- # Access Testing Validation performed from Windows 11 client. ## georgepap Member of: ``` IT_Admins ``` Result: ``` I: IT drive available Sales access denied ``` Screenshot: ![George IT Drive](screenshots/11_george_it_drive.png) --- ## mariakon Member of: ``` Sales_Users ``` Result: ``` S: Sales drive available IT access denied ``` Screenshot: ![Maria Sales Drive](screenshots/12_maria_sales_drive.png) --- ## johnmarkou Member of: ``` Domain Users only ``` Security test: - No mapped drives - No access to IT share - No access to Sales share Screenshots: ![John No Drives](screenshots/13_john_no_drives.png) ![John Access Denied](screenshots/14_john_access_denied.png) --- # Skills Demonstrated - Windows Server Administration - Active Directory - DNS - DHCP - SMB File Sharing - NTFS Permissions - Group Policy Objects - User and Group Management - Troubleshooting Network Connectivity ```
