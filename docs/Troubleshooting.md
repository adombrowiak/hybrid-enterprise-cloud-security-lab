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