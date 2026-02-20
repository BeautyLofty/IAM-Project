# Active Directory & IAM Home Lab

## Overview
This Lab demonstrates hands-on experience with Windows Server 2022, Active Directory Domain Services, and IAM-related administrative tasks.

## Environment
- Host: Lenovo Laptop (Windows)
- RAM: 8 GB
- Virtualization: VirtualBox
- Guest OS: Windows Server 2022 Standard
- VM Name: AD-Server
- RAM: 4096 MB
- CPU: 2 Cores
- Disk: 60 GB (NTFS)

## VM Setup
- Created VM and attached ISO
- Enabled VT-x in BIOS
- Installed Windows Server
- Detached ISO after installation
- Logged in as Administrator

## Active Directory Setup
- Installed AD DS role
- Promoted server to Domain Controller
- Domain: lab.local

## IAM Tasks
- Created domain users
- Created security groups
- Assigned group membership
- Performed password resets
- Simulated account lock/unlock

## Troubleshooting
- Fixed boot loop by removing ISO
- Resolved Ctrl+Alt+Del issue via VirtualBox Input menu
- Enabled virtualization in BIOS

## Skills Demonstrated
- Windows Server Administration
- Active Directory & IAM fundamentals
- Virtualization troubleshooting
- Technical documentation

## Next Steps
- GPOs
- Domain-joined client VM
- Azure AD / Entra ID

