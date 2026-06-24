# Build Log

This document tracks the development of the Hybrid Enterprise & Cloud Security Lab from initial infrastructure deployment through identity, automation, containerization, and cloud integration.

---

# Session 1 - Environment Foundation

**Date:** June 24, 2026

## Objectives

- Build the initial Hyper-V environment
- Deploy Windows Server, Windows 11, and Ubuntu Server
- Establish a consistent naming convention
- Configure a version-controlled project workspace

## Completed

### Infrastructure

- Created a dedicated Hyper-V environment
- Configured `Hybrid-Lab-Switch`
- Standardized virtual machine naming

| System | Status |
|----------|----------|
| DC01 | Complete |
| WIN11-01 | Complete |
| UBUNTU01 | Complete |

### Windows Server 2022

- Installed Windows Server 2022 (Desktop Experience)
- Verified networking
- Prepared for Active Directory deployment

### Windows 11

- Installed Windows 11 Pro for Workstations
- Created a local administrator account
- Installed Git
- Installed Visual Studio Code
- Configured Git for development

### Ubuntu Server 26.04 LTS

- Installed Ubuntu Server 26.04 LTS
- Enabled OpenSSH
- Installed development utilities

Installed packages:

- Git
- curl
- wget
- htop
- tree
- unzip

### Project Repository

Created the initial repository structure:

```
hybrid-enterprise-cloud-security-lab/
├── ansible/
├── diagrams/
├── docker/
├── docs/
├── images/
├── opentofu/
├── powershell/
└── scripts/
```

Initialized Git and connected the project to GitHub.

---

## Challenges

### Hyper-V Secure Boot

Ubuntu Server required the Microsoft UEFI Certificate Authority template instead of the default Microsoft Windows template.

### Package Installation

Ubuntu experienced intermittent out-of-memory events during package installation while Dynamic Memory was enabled. After reboot and validation, memory utilization returned to normal with approximately 3 GB available and an active swap file.

### Windows Setup

Windows 11 account requirements were bypassed to create a local administrator account appropriate for a lab environment.

---

## Lessons Learned

- Hyper-V Generation 2 virtual machines require different Secure Boot templates depending on the guest operating system.
- Establishing a consistent project structure and version control from the beginning simplifies documentation and future automation.
- Building infrastructure deliberately provides a stronger understanding than deploying preconfigured lab environments.

---

## Next Session

- Configure static IP addressing
- Deploy Active Directory Domain Services
- Configure DNS
- Promote DC01 to a Domain Controller
- Join WIN11-01 to the domain
- Document the initial enterprise architecture

---

**Project Status:** Active Development