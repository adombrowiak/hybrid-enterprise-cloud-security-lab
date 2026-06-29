# Lessons Learned

This document captures key engineering lessons learned throughout the Hybrid Enterprise & Cloud Security Lab. Unlike the session documentation, this page consolidates concepts and best practices that remain relevant across the project.

---

# Active Directory

- Active Directory is highly dependent on DNS for authentication and service discovery.
- DNS should always be verified before troubleshooting authentication issues.
- Domain Controllers should provide authoritative DNS while forwarding external requests to trusted public DNS servers.

---

# Windows Administration

- Windows Defender Firewall can block ICMP traffic even when network configuration is correct.
- Group Policy changes should always be validated using `gpupdate` and `gpresult`.
- Administrative tasks should always be performed using dedicated administrative accounts.

---

# Linux Administration

- Proper DNS configuration is required before joining Linux systems to Active Directory.
- SSSD relies on Kerberos and LDAP to provide centralized authentication.
- PAM can automatically create user home directories during first-time logins.

---

# Hyper-V

- Ubuntu Generation 2 virtual machines require the Microsoft UEFI Certificate Authority Secure Boot template.
- External Virtual Switches place virtual machines directly on the physical network.

---

# Security

- Least privilege should be implemented from the beginning.
- Role-Based Access Control simplifies long-term administration.
- Separate administrative accounts reduce unnecessary exposure of privileged credentials.

---

# Documentation

- Version control should be established before infrastructure deployment.
- Incremental documentation significantly improves reproducibility.
- Validation should accompany every major configuration change.