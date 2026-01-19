# 🛡️ AD Security Toolkit

A comprehensive Active Directory security auditing and threat detection toolkit. Designed for security professionals, SOC analysts, and IT administrators to identify misconfigurations, detect attacks, and harden AD environments.

![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-blue?logo=powershell)
![License](https://img.shields.io/badge/License-MIT-green)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-Mapped-red)

## 🎯 Features

- **AD Enumeration & Auditing** - Discover privileged accounts, stale passwords, misconfigurations
- **Attack Detection** - Splunk queries for Kerberoasting, DCSync, Pass-the-Hash, etc.
- **Sysmon Configuration** - Detection-focused config optimized for AD environments
- **Incident Response** - Scripts to quickly gather forensic data during incidents

## 🚀 Quick Start
```powershell
# Clone the repository
git clone https://github.com/camiloguzman2001/AD-Security-Toolkit.git

# Run the AD audit (requires domain-joined machine)
.\scripts\Invoke-ADSecurityAudit.ps1

# Generate HTML report
.\scripts\Invoke-ADSecurityAudit.ps1 -OutputFormat HTML -Path .\reports\
```

## 🔧 Tools Included

| Script | Description |
|--------|-------------|
| `Invoke-ADSecurityAudit.ps1` | Comprehensive AD health check - privileged accounts, Kerberoastable users, password policy issues |
| `Find-KerberoastTargets.ps1` | Identifies accounts vulnerable to Kerberoasting with risk scoring |
| `Watch-PrivilegedGroups.ps1` | Real-time monitoring for changes to sensitive AD groups |

## 📊 Detection Rules

Splunk queries included for:

| Attack | MITRE Technique |
|--------|-----------------|
| Kerberoasting | T1558.003 |
| DCSync | T1003.006 |
| Pass-the-Hash | T1550.002 |
| Golden Ticket | T1558.001 |
| Password Spraying | T1110.003 |
| Privileged Group Changes | T1098 |

## 🖥️ Lab Setup

See [docs/LAB_SETUP.md](docs/LAB_SETUP.md) for a complete guide to building your own AD attack/defense lab.

## ⚔️ MITRE ATT&CK Coverage

| Technique ID | Technique Name | Detection |
|--------------|----------------|-----------|
| T1558.003 | Kerberoasting | ✅ |
| T1558.001 | Golden Ticket | ✅ |
| T1003.006 | DCSync | ✅ |
| T1550.002 | Pass-the-Hash | ✅ |
| T1110.003 | Password Spraying | ✅ |
| T1098 | Account Manipulation | ✅ |

## 📄 License

MIT License - See [LICENSE](LICENSE) for details.

## 📬 Contact

**Camilo Guzman** - [LinkedIn](https://linkedin.com/in/camiloguzman) | [GitHub](https://github.com/CamiloSteez)
