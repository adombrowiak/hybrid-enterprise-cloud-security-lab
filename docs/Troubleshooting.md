# Troubleshooting Guide

This document records issues encountered throughout the Hybrid Enterprise & Cloud Security Lab along with the steps used to resolve them.

---

# Windows Defender Firewall Blocking Ping

## Symptoms

- Windows systems could not ping one another.
- IP configuration appeared correct.

## Cause

Inbound ICMP Echo Requests were blocked by Windows Defender Firewall.

## Resolution

Enable the appropriate inbound ICMP firewall rules.

---

# Ubuntu Secure Boot Failure

## Symptoms

Ubuntu Server failed to boot under Hyper-V.

## Cause

Incorrect Secure Boot template.

## Resolution

Select the **Microsoft UEFI Certificate Authority** Secure Boot template.

---

# Ubuntu Active Directory Join Failure

## Symptoms

```
No such realm found
```

## Cause

DNS and Kerberos service discovery failed.

## Resolution

- Verify DNS configuration
- Verify domain controller accessibility
- Verify Kerberos configuration
- Restart SSSD after configuration changes

---

# Automatic Home Directory Not Created

## Symptoms

Authentication succeeded but no home directory was created.

## Cause

PAM home directory creation was not enabled.

## Resolution

Run:

```bash
sudo pam-auth-update
```

Enable:

```
Create home directory on login
```

Restart SSSD.

---

# Group Policy Verification Access Denied

## Symptoms

```
gpresult /scope computer /r
```

returned:

```
Access is denied.
```

## Cause

The command requires administrative privileges.

## Resolution

Run the command using an administrative account or an elevated PowerShell session.

## Ubuntu Unable to Resolve Active Directory Users

### Symptoms

- Ubuntu successfully joined the Active Directory domain.
- Active Directory users could authenticate, but additional domain users could not be resolved.
- SSSD reported the domain as **Offline**.
- Domain Controller discovery failed despite the server being reachable.

### Root Cause

Two configuration issues were identified during troubleshooting:

1. Active Directory DNS required validation after the Domain Controller was unable to properly advertise LDAP SRV records.
2. Ubuntu's Netplan configuration specified the correct DNS server but did not include the required Active Directory DNS search domain (`corp.local`).

Without the search domain, Ubuntu's system resolver could not properly locate Active Directory resources, preventing SSSD from discovering the Domain Controller.

### Resolution

- Validated Active Directory DNS health and confirmed LDAP SRV records were present.
- Updated the Ubuntu Netplan configuration to include the `corp.local` DNS search domain.
- Applied the updated network configuration using `netplan apply`.
- Restarted SSSD.
- Verified Domain Controller discovery and Active Directory user resolution.

### Validation

Following the configuration changes:

- SSSD reported an **Online** status.
- Active Directory Domain Controller discovery succeeded.
- Standard and administrative Active Directory users resolved successfully.
- Enterprise DNS and hybrid identity services were fully restored.