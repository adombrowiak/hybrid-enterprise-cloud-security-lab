# Session 1 - Environment Foundation

**Date:** June 24, 2026

---

# Overview

The first session established the foundation for the Hybrid Enterprise & Cloud Security Lab by creating a dedicated virtualization environment capable of supporting Windows and Linux enterprise infrastructure. Rather than relying on prebuilt virtual machines, the environment was built from the ground up to provide practical experience with infrastructure deployment, system configuration, and version-controlled documentation.

This foundation will support future implementation of Active Directory, hybrid identity management, infrastructure automation, cloud integration, and enterprise security technologies.

---

# Objectives

- Build the Hyper-V lab environment
- Deploy Windows Server 2022
- Deploy Windows 11 Pro for Workstations
- Deploy Ubuntu Server 26.04 LTS
- Establish a standardized naming convention
- Create a GitHub repository for version control
- Prepare the environment for Active Directory deployment

---

# Environment Before Changes

## Host System

- Windows 11
- Hyper-V enabled

## Virtual Machines

No virtual machines had been deployed.

---

# Implementation

## Hyper-V Infrastructure

A dedicated Hyper-V environment was created to host all systems within the lab. A standardized naming convention was established to simplify administration and maintain consistency as additional services are introduced.

### Virtual Machines

| System | Purpose |
|----------|---------|
| DC01 | Windows Server Domain Controller |
| WIN11-01 | Enterprise Windows workstation |
| UBUNTU01 | Enterprise Linux server |

A dedicated external virtual switch named **Hybrid-Lab-Switch** was created to provide network connectivity for all virtual machines.

---

## Windows Server 2022

Windows Server 2022 Desktop Experience was deployed as the future Domain Controller for the lab environment.

Initial configuration included:

- Operating system installation
- Network verification
- Base operating system updates
- Preparation for Active Directory Domain Services (AD DS)

---

## Windows 11 Pro for Workstations

Windows 11 Pro for Workstations was deployed to simulate an enterprise client workstation.

Configuration included:

- Local administrator account creation
- Git installation
- Visual Studio Code installation
- Git configuration for version control

---

## Ubuntu Server 26.04 LTS

Ubuntu Server 26.04 LTS was deployed to represent enterprise Linux infrastructure within the hybrid environment.

Installed software included:

- OpenSSH Server
- Git
- curl
- wget
- htop
- tree
- unzip

These utilities provide the foundation for Linux administration, automation, and future infrastructure management.

---

## Project Repository

A GitHub repository was created to provide centralized version control for documentation, scripts, and future automation.

Initial repository structure:

```text
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

Version control was established at the beginning of the project to ensure all infrastructure changes could be documented, tracked, and reproduced throughout the lab's development.

---

# Validation

The following items were successfully validated:

- Hyper-V environment operational
- Windows Server 2022 booted successfully
- Windows 11 Pro booted successfully
- Ubuntu Server booted successfully
- OpenSSH operational on Ubuntu Server
- Development utilities installed successfully
- Git repository initialized
- GitHub repository created
- Project directory structure established

---

# Challenges Encountered

## Hyper-V Secure Boot

Ubuntu Server required the **Microsoft UEFI Certificate Authority** Secure Boot template instead of the default Microsoft Windows template before the operating system would boot successfully.

---

## Ubuntu Package Installation

Ubuntu experienced intermittent out-of-memory conditions while Hyper-V Dynamic Memory was enabled during package installation.

Following a reboot, memory utilization stabilized with approximately 3 GB of available memory and an active swap file.

---

## Windows Setup

Windows 11 installation was configured using a local administrator account to better simulate an enterprise deployment and reduce unnecessary dependencies on Microsoft consumer services.

---

# Lessons Learned

- Hyper-V Generation 2 virtual machines require different Secure Boot templates depending on the guest operating system.
- Building infrastructure manually provides a deeper understanding of enterprise environments than relying on preconfigured lab images.
- Establishing documentation and version control at the beginning of a project greatly simplifies future development and troubleshooting.
- Consistent naming conventions improve readability and administration as environments continue to grow.

---

# Environment After Changes

| Component | Status |
|----------|:------:|
| Hyper-V Infrastructure | ✅ Complete |
| Windows Server 2022 | ✅ Deployed |
| Windows 11 Pro for Workstations | ✅ Deployed |
| Ubuntu Server 26.04 LTS | ✅ Deployed |
| GitHub Repository | ✅ Created |
| Project Documentation | ✅ Initialized |

---

# Next Steps

Session 2 will focus on establishing the enterprise identity infrastructure by:

- Configuring static IP addressing
- Deploying Active Directory Domain Services (AD DS)
- Configuring enterprise DNS
- Promoting DC01 to a Domain Controller
- Joining Windows 11 to the Active Directory domain
- Validating enterprise authentication services