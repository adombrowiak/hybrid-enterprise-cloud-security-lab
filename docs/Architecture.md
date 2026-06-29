# Architecture

---

# Overview

The Hybrid Enterprise & Cloud Security Lab is designed to simulate a modern enterprise environment consisting of Windows and Linux infrastructure integrated through centralized identity management.

The lab is being built incrementally to demonstrate enterprise systems administration, cybersecurity engineering, hybrid identity, infrastructure automation, and cloud integration. Each implementation phase is documented and validated to emulate real-world engineering practices.

---

# Design Objectives

The primary objectives of this lab are to:

- Build a realistic enterprise Windows environment
- Integrate Windows and Linux systems through centralized identity management
- Implement enterprise security principles using Role-Based Access Control (RBAC)
- Develop practical experience with infrastructure automation
- Integrate cloud technologies with on-premises infrastructure
- Document each implementation as a professional engineering project

---

# Host Environment

| Component | Configuration |
|----------|---------------|
| Host Operating System | Windows 11 |
| Hypervisor | Hyper-V |
| Virtual Switch | Hybrid-Lab-Switch (External) |

---

# Virtual Machine Inventory

| System | Operating System | Primary Role |
|----------|-----------------|--------------|
| DC01 | Windows Server 2022 Desktop Experience | Active Directory Domain Controller |
| WIN11-01 | Windows 11 Pro for Workstations | Enterprise Workstation |
| UBUNTU01 | Ubuntu Server 26.04 LTS | Enterprise Linux Server |

---

# Network Architecture

## Active Directory Domain

```
corp.local
```

## IP Addressing

| System | IP Address |
|----------|----------------|
| DC01 | 192.168.1.210 |
| WIN11-01 | 192.168.1.220 |
| UBUNTU01 | 192.168.1.230 |

### Gateway

```
192.168.1.1
```

### DNS

Primary DNS

```
192.168.1.210
```

DNS Forwarders

- Google Public DNS (8.8.8.8)
- Cloudflare DNS (1.1.1.1)

---

# Current Infrastructure

```
                    Windows 11 Host
                           │
                    Hyper-V Hypervisor
                           │
                 Hybrid-Lab-Switch (External)
                           │
      ┌────────────────────┼────────────────────┐
      │                    │                    │
      ▼                    ▼                    ▼

   DC01               WIN11-01            UBUNTU01

 Windows Server        Windows 11          Ubuntu Server

 Active Directory      Domain Joined       Domain Joined
 DNS                   Group Policy        Kerberos
 Kerberos                                  LDAP
 LDAP                                      SSSD
 Group Policy                              PAM
```

---

# Active Directory Architecture

## Organizational Unit Structure

```
corp.local
│
├── Admin
├── Computers
├── Groups
├── Servers
├── Service Accounts
├── Users
└── Workstations
```

This structure separates administrative objects by function, simplifying administration and allowing future delegation of permissions and Group Policy management.

---

# Identity Management

Enterprise identity is centrally managed through Active Directory.

Current implementation includes:

- Active Directory Domain Services
- DNS
- Kerberos
- LDAP
- SSSD
- PAM

Windows and Linux systems authenticate against the same centralized directory service.

---

# Role-Based Access Control (RBAC)

Administrative access is managed using dedicated administrative accounts and security groups.

Current security model includes:

- Standard user accounts
- Administrative user accounts
- Enterprise security groups
- Least privilege administration
- Centralized authentication

Security groups currently implemented include:

- GG-DomainAdmins
- GG-ITAdmins
- GG-LinuxAdmins
- GG-ServerAdmins
- GG-WorkstationAdmins

---

# Group Policy

Baseline Group Policy Objects have been implemented to provide centralized management of Windows systems.

Current policies provide:

- Centralized configuration
- Enterprise policy enforcement
- Organizational Unit targeting
- Administrative consistency

---

# Hybrid Identity

Ubuntu Server has been integrated into Active Directory using:

- realmd
- Kerberos
- LDAP
- SSSD
- PAM
- adcli

This allows Windows and Linux systems to share a common identity platform while maintaining native operating system administration.

---

# Current Technologies

## Virtualization

- Hyper-V

## Windows

- Windows Server 2022
- Windows 11 Pro for Workstations
- Active Directory Domain Services
- DNS
- Group Policy

## Linux

- Ubuntu Server 26.04 LTS
- OpenSSH
- SSSD
- Kerberos
- LDAP
- PAM

## Security

- Role-Based Access Control (RBAC)
- Least Privilege Administration
- Security Groups
- Enterprise Authentication

---

# Future Architecture

The following technologies will be integrated as the project progresses.

## Infrastructure Automation

- OpenTofu
- Ansible

## Containerization

- Docker

## Cloud

- Microsoft Entra ID
- Azure CLI
- Azure Virtual Networks
- Azure Virtual Machines
- Azure Key Vault

## Security

- Microsoft Defender
- Microsoft Sentinel
- Windows Event Forwarding (WEF)
- Sysmon

---

# Authentication Flow

```
Windows User
        │
        ▼
Windows 11 Workstation
        │
        ▼
Kerberos Authentication
        │
        ▼
Active Directory
        │
        ├────────► DNS
        │
        ├────────► LDAP
        │
        └────────► Group Policy


Linux User
        │
        ▼
Ubuntu Server
        │
        ▼
SSSD
        │
        ▼
Kerberos
        │
        ▼
Active Directory
```

---

# Current Project Status

| Component | Status |
|----------|:------:|
| Hyper-V Infrastructure | ✅ Complete |
| Active Directory | ✅ Operational |
| Enterprise DNS | ✅ Operational |
| Windows Domain Integration | ✅ Complete |
| Linux Domain Integration | ✅ Complete |
| RBAC | ✅ Complete |
| Group Policy | ✅ Complete |
| Hybrid Identity | ✅ Operational |
| Infrastructure Automation | 🚧 Planned |
| Cloud Integration | 🚧 Planned |
| Security Monitoring | 🚧 Planned |