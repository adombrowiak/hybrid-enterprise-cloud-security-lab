# Hybrid Enterprise & Cloud Security Lab

![Status](https://img.shields.io/badge/Status-Active%20Development-blue)
![Windows Server](https://img.shields.io/badge/Windows_Server-2022-0078D6)
![Ubuntu](https://img.shields.io/badge/Ubuntu-26.04-E95420)
![Hyper-V](https://img.shields.io/badge/Hyper--V-Lab-5C2D91)
![License](https://img.shields.io/badge/License-MIT-green)

---

## Overview

The Hybrid Enterprise & Cloud Security Lab is a portfolio project designed to simulate a modern enterprise IT environment spanning Windows and Linux infrastructure. The project focuses on implementing enterprise identity management, systems administration, infrastructure automation, and cloud technologies while documenting every phase as if it were a production engineering project.

The objective is to gain practical experience designing, deploying, securing, and managing hybrid infrastructure using industry-standard tools and best practices.

---

## Project Goals

- Design an enterprise Active Directory environment
- Implement Role-Based Access Control (RBAC)
- Centralize authentication across Windows and Linux
- Deploy and manage enterprise infrastructure
- Automate infrastructure using Infrastructure as Code (IaC)
- Integrate Microsoft Azure services
- Build a professional cybersecurity and systems engineering portfolio

---

## Current Environment

### Virtualization

- Hyper-V

### Operating Systems

- Windows Server 2022 Desktop Experience
- Windows 11 Pro for Workstations
- Ubuntu Server 26.04 LTS

### Identity & Directory Services

- Active Directory Domain Services (AD DS)
- Active Directory Organizational Units (OU)
- Enterprise Role-Based Access Control (RBAC)
- Kerberos
- LDAP
- SSSD
- PAM

### Networking

- DNS
- DNS Forwarders
- Hyper-V External Virtual Switch

### Security

- Group Policy
- Enterprise Security Groups
- Least Privilege Administration

### Linux Services

- OpenSSH
- Git
- curl
- wget
- htop
- tree
- unzip

---

## Lab Architecture

Architecture diagrams and infrastructure documentation are maintained within the `docs` and `diagrams` directories.

Current architecture includes:

- Hyper-V virtualization
- Windows Server Active Directory domain
- Windows 11 domain-joined workstation
- Ubuntu Server integrated with Active Directory
- Enterprise DNS and Kerberos authentication
- Centralized identity management across Windows and Linux

---

## Technologies Planned

### Infrastructure

- Docker
- OpenTofu
- Ansible

### Cloud

- Microsoft Entra ID
- Azure CLI
- Azure Virtual Networks
- Azure Virtual Machines
- Azure Key Vault
- Azure Monitor

### Security

- Microsoft Defender
- Microsoft Sentinel
- Windows Event Forwarding (WEF)
- Sysmon

---

## Skills Demonstrated

- Windows Server Administration
- Linux Administration
- Active Directory
- DNS Administration
- Group Policy Management
- Kerberos Authentication
- LDAP
- Hybrid Identity
- Role-Based Access Control (RBAC)
- Enterprise Troubleshooting
- Infrastructure Documentation
- Security Hardening

---

## Current Status

**Status:** 🚧 Active Development

### Completed

- ✅ Hyper-V virtual infrastructure
- ✅ Windows Server 2022 deployment
- ✅ Active Directory Domain Services (AD DS)
- ✅ Enterprise DNS configuration
- ✅ Windows 11 domain join
- ✅ Enterprise Organizational Unit (OU) hierarchy
- ✅ Standard and administrative user accounts
- ✅ Role-Based Access Control (RBAC)
- ✅ Security group implementation
- ✅ Baseline Group Policy deployment
- ✅ Ubuntu Server integration with Active Directory
- ✅ Kerberos authentication
- ✅ LDAP integration
- ✅ SSSD configuration
- ✅ Automatic home directory provisioning via PAM

### In Progress

- 🚧 Enterprise Linux administration
- 🚧 Active Directory-based SSH authentication
- 🚧 Repository documentation reorganization

### Planned

- 📋 Infrastructure as Code (OpenTofu)
- 📋 Configuration management with Ansible
- 📋 Docker container platform
- 📋 Microsoft Entra ID integration
- 📋 Azure infrastructure deployment
- 📋 Microsoft Sentinel integration
- 📋 Enterprise security monitoring
- 📋 Cloud security automation

---

## Project Documentation

| Session | Focus Area | Status | Documentation |
|----------|------------|:------:|---------------|
| Session 1 | Initial Infrastructure Deployment | ✅ Complete | [Session-01](docs/Session-01.md) |
| Session 2 | Active Directory & Domain Services | ✅ Complete | [Session-02](docs/Session-02.md) |
| Session 3 | Enterprise Identity & Hybrid Linux Integration | ✅ Complete | [Session-03](docs/Session-03.md) |
| Session 4 | Enterprise Linux Administration & Hardening | 🚧 Planned | [Session-04](docs/Session-04.md) |
| Session 5 | Infrastructure Automation | 📋 Planned | [Session-05](docs/Session-05.md) |
| Session 6 | Hybrid Cloud Integration | 📋 Planned | [Session-06](docs/Session-06.md) |
| Session 7 | Enterprise Security Monitoring | 📋 Planned | [Session-07](docs/Session-07.md) |

---

## Project Roadmap

| Milestone | Status |
|------------|:------:|
| Enterprise Active Directory | ✅ |
| Windows Domain Services | ✅ |
| Hybrid Linux Integration | ✅ |
| Enterprise Linux Administration | 🚧 |
| Infrastructure as Code | 📋 |
| Container Platform | 📋 |
| Azure Integration | 📋 |
| Security Monitoring | 📋 |
| SIEM Integration | 📋 |
| Detection Engineering | 📋 |

---

## Repository Structure

```text
hybrid-enterprise-cloud-security-lab/
│
├── README.md
├── build-log.md
│
├── docs/
│   ├── Session-01.md
│   ├── Session-02.md
│   ├── Session-03.md
│   ├── Architecture.md
│   ├── Lessons-Learned.md
│   ├── Troubleshooting.md
│   └── screenshots/
│
├── diagrams/
│
└── scripts/
    ├── linux/
    └── powershell/
```

---

## License

This project is intended for educational and portfolio purposes.