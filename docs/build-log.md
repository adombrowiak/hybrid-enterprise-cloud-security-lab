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

# Session 2 - Active Directory Foundation

**Date:** June 25, 2026

## Objectives

- Configure static IP addressing
- Deploy Active Directory Domain Services
- Configure DNS
- Promote DC01 to a Domain Controller
- Join WIN11-01 to the domain
- Validate Active Directory functionality

## Completed

### Networking

Configured static IP addressing for all systems.

| System | IP Address | Status |
|----------|----------------|----------|
| DC01 | 192.168.1.210 | Complete |
| WIN11-01 | 192.168.1.220 | Complete |
| UBUNTU01 | 192.168.1.230 | Complete |

Verified full network connectivity between all virtual machines.

### Ubuntu Server

- Configured Netplan with static IP addressing
- Configured DNS to use DC01
- Verified SSH connectivity
- Verified communication with both Windows hosts

### Windows Networking

- Configured static IP addressing
- Identified Windows Defender Firewall as the source of blocked ICMP traffic
- Enabled required firewall rules
- Verified bidirectional connectivity between all systems
- Configured default gateway for Internet connectivity
- Configured DNS forwarders for external name resolution
- Verified Internet connectivity through the domain controller

### Active Directory

Installed server roles:

- Active Directory Domain Services
- DNS Server

Created the initial Active Directory forest:

- Domain: `corp.local`

Promoted DC01 to the first Domain Controller.
Configured DNS forwarders for external name resolution.

Forwarders:

- Google Public DNS (8.8.8.8)
- Cloudflare DNS (1.1.1.1)

### Domain Validation

Validated the Active Directory deployment using:

- Get-ADDomain
- Get-ADForest
- dcdiag
- Resolve-DnsName
- nltest

Verified:

- Domain Controller health
- DNS resolution
- Kerberos services
- LDAP services
- Global Catalog
- Secure domain communication

### Windows 11 Domain Join

Successfully joined WIN11-01 to:

`corp.local`

Verified:

- Domain authentication
- Domain Controller discovery
- Domain membership
- Secure channel establishment

---

## Challenges

### Windows Defender Firewall

ICMP traffic between Windows systems was initially blocked by Windows Defender Firewall despite correct network configuration.

Connectivity was restored after enabling the appropriate inbound firewall rules.

### Ubuntu Netplan Configuration

Ubuntu Server required manual Netplan configuration for static networking.

Proper YAML indentation was required for successful deployment.

### Network Configuration

The initial lab network was configured on an isolated subnet (192.168.100.0/24), which prevented Internet connectivity while using an External Hyper-V virtual switch.

The environment was migrated to the physical network subnet (192.168.1.0/24), default gateways were configured, and DNS forwarders were added to restore Internet connectivity while maintaining Active Directory functionality.

---

## Lessons Learned

- Active Directory depends heavily on proper DNS configuration.
- Windows Defender Firewall should be one of the first components verified during network troubleshooting.
- Verifying each deployment stage with administrative tools simplifies troubleshooting and confirms successful configuration.
- Building infrastructure incrementally provides a stronger understanding of enterprise environments than using preconfigured lab images.
- Active Directory environments require proper DNS forwarding to resolve external resources.
- Static IP configurations must include a default gateway to provide Internet connectivity.
- Hyper-V External virtual switches bridge virtual machines directly onto the physical network, making subnet planning an important design consideration.
- Domain Controllers require DNS forwarders to resolve external resources while continuing to provide authoritative DNS services for the Active Directory domain.
- Static IP configurations should include a default gateway when Internet connectivity is required.
---

## Next Session

- Create Organizational Units (OUs)
- Create domain users
- Create security groups
- Configure baseline Group Policy Objects (GPOs)
- Join Ubuntu Server to Active Directory
- Begin enterprise security hardening

---

**Project Status:** Active Development