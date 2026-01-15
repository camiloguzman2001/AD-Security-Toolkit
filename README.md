# 🛡️ AD Security Toolkit

A comprehensive Active Directory security auditing and threat detection toolkit. Designed for security professionals, SOC analysts, and IT administrators to identify misconfigurations, detect attacks, and harden AD environments.

![PowerShell](https://img.shields.io/badge/PowerShell-5.1+-blue?logo=powershell)
![License](https://img.shields.io/badge/License-MIT-green)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-Mapped-red)

## 📋 Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Tools Included](#tools-included)
- [Detection Rules](#detection-rules)
- [Lab Setup Guide](#lab-setup-guide)
- [Screenshots](#screenshots)
- [MITRE ATT&CK Coverage](#mitre-attck-coverage)
- [Contributing](#contributing)

## 🎯 Features

- **AD Enumeration & Auditing** - Discover privileged accounts, stale passwords, misconfigurations
- **Attack Detection** - Splunk/Elastic queries for Kerberoasting, DCSync, Pass-the-Hash, etc.
- **Sysmon Configuration** - Detection-focused config optimized for AD environments
- **Hardening Scripts** - Automated GPO and security baseline deployment
- **Incident Response** - Scripts to quickly gather forensic data during incidents

## 🚀 Quick Start

```powershell
# Clone the repository
git clone https://github.com/CamiloSteez/ad-security-toolkit.git

# Run the AD audit (requires domain-joined machine)
.\scripts\Invoke-ADSecurityAudit.ps1

# Generate HTML report
.\scripts\Invoke-ADSecurityAudit.ps1 -OutputFormat HTML -Path .\reports\
```

## 🔧 Tools Included

### 1. AD Security Auditor (`Invoke-ADSecurityAudit.ps1`)
Comprehensive AD health check that identifies:
- Privileged group membership (Domain Admins, Enterprise Admins, etc.)
- Accounts with non-expiring passwords
- Inactive/stale user and computer accounts
- Kerberoastable service accounts
- AS-REP Roastable accounts (no pre-auth)
- Unconstrained delegation configurations
- AdminSDHolder permission issues
- Password policy weaknesses

### 2. Privileged Account Monitor (`Watch-PrivilegedGroups.ps1`)
Real-time monitoring for changes to sensitive AD groups:
- Alerts on any additions to privileged groups
- Logs all membership changes with timestamps
- Email notification support
- Event log integration

### 3. Kerberoast Detector (`Find-KerberoastTargets.ps1`)
Identifies accounts vulnerable to Kerberoasting:
- Lists all SPNs in the domain
- Highlights service accounts with weak password policies
- Risk scoring based on account privileges
- Remediation recommendations

### 4. Lateral Movement Detector (`Detect-LateralMovement.ps1`)
Analyzes authentication logs for suspicious patterns:
- Unusual login times
- Multiple failed authentications
- Pass-the-Hash indicators
- Credential hopping chains

### 5. Forensic Collector (`Invoke-ADForensics.ps1`)
Rapid data collection during security incidents:
- Recent authentication events
- Group membership changes
- GPO modifications
- Replication metadata
- Trust relationships

## 📊 Detection Rules

### Splunk Queries
Located in `/detection-rules/splunk/`

| Rule | MITRE Technique | Description |
|------|-----------------|-------------|
| `kerberoasting.spl` | T1558.003 | Detects TGS requests with RC4 encryption |
| `dcsync.spl` | T1003.006 | Identifies replication requests from non-DCs |
| `pass-the-hash.spl` | T1550.002 | Detects NTLM auth anomalies |
| `golden-ticket.spl` | T1558.001 | Identifies forged TGT usage |
| `priv-group-change.spl` | T1098 | Alerts on privileged group modifications |
| `password-spray.spl` | T1110.003 | Detects distributed login failures |

### Elastic/KQL Queries
Located in `/detection-rules/elastic/`

Same detection coverage in Elasticsearch/Kibana format.

## 🖥️ Lab Setup Guide

Want to test these tools safely? See our [Lab Setup Guide](docs/LAB_SETUP.md) for:
- VirtualBox/VMware configuration
- Windows Server 2022 DC deployment
- Workstation setup
- Attack simulation with Kali Linux
- Splunk integration

## 📸 Screenshots

### AD Security Audit Report
![Audit Report](docs/images/audit-report.png)

### Splunk Detection Dashboard
![Splunk Dashboard](docs/images/splunk-dashboard.png)

### Kerberoast Risk Assessment
![Kerberoast Scan](docs/images/kerberoast-scan.png)

## ⚔️ MITRE ATT&CK Coverage

| Technique ID | Technique Name | Detection | Prevention |
|--------------|----------------|-----------|------------|
| T1558.003 | Kerberoasting | ✅ | ✅ |
| T1558.001 | Golden Ticket | ✅ | ✅ |
| T1003.006 | DCSync | ✅ | ✅ |
| T1550.002 | Pass-the-Hash | ✅ | ✅ |
| T1087.002 | Domain Account Enumeration | ✅ | ⚠️ |
| T1110.003 | Password Spraying | ✅ | ✅ |
| T1098 | Account Manipulation | ✅ | ✅ |
| T1134 | Access Token Manipulation | ✅ | ⚠️ |

## 🔒 Hardening Resources

- [CIS Benchmark Implementation](docs/CIS_HARDENING.md)
- [GPO Security Templates](hardening/gpo-templates/)
- [Password Policy Recommendations](docs/PASSWORD_POLICY.md)
- [Tiered Administration Model](docs/TIERED_ADMIN.md)

## 📄 License

MIT License - See [LICENSE](LICENSE) for details.

## 🤝 Contributing

Contributions welcome! Please read [CONTRIBUTING.md](CONTRIBUTING.md) first.

## 📬 Contact

**Camilo Guzman**
- LinkedIn: [linkedin.com/in/camiloguzman](https://linkedin.com/in/camiloguzman)
- GitHub: [@CamiloSteez](https://github.com/CamiloSteez)

---

⭐ Star this repo if you find it useful!
