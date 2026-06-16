# Cybersecurity Framework for Small Businesses

## Overview

This project focuses on designing and implementing a cost-effective cybersecurity framework for a small IT services company using open-source security tools. The objective is to protect business assets against common cyber threats such as ransomware, phishing attacks, insider threats, brute-force attacks, unauthorized access, data breaches, and denial-of-service (DoS) attacks.

The implementation was performed in a virtualized lab environment consisting of an Ubuntu Server and a Kali Linux machine to simulate real-world business infrastructure and attack scenarios.

---

## Project Objectives

* Identify and analyze cybersecurity threats affecting small businesses.
* Implement practical security controls using open-source tools.
* Apply the Principle of Least Privilege (PoLP) for access management.
* Secure remote access services.
* Protect endpoints from malware.
* Conduct vulnerability assessments.
* Implement firewall and DoS mitigation mechanisms.
* Establish backup, incident response, and business continuity procedures.
* Create a cybersecurity framework suitable for small business environments.

---

## Lab Environment

| Machine       | Operating System   | Purpose               |
| ------------- | ------------------ | --------------------- |
| Kali Linux    | Kali Linux         | Attacker Machine      |
| Ubuntu Server | Ubuntu 22.04.5 LTS | Small Business Server |

### Network Configuration

Both virtual machines were configured on the same network segment and connectivity was verified using ICMP ping tests.

**Ubuntu Server IP:** `192.168.31.138`

---

## Security Controls Implemented

### Access Control & User Management

* Created department-based user accounts.
* Implemented Principle of Least Privilege (PoLP).
* Restricted access to sensitive business data.

#### Users

| User      | Department       |
| --------- | ---------------- |
| manager   | Management       |
| hr        | Human Resources  |
| developer | Development Team |

---

### Secure Remote Access

Configured OpenSSH Server for secure remote administration.

**Features**

* SSH enabled on Ubuntu Server
* Remote login tested successfully from Kali Linux
* Restricted access through firewall policies

---

### Brute Force Protection

Implemented Fail2Ban to monitor SSH authentication failures.

**Configuration**

| Parameter | Value       |
| --------- | ----------- |
| Max Retry | 5           |
| Find Time | 600 Seconds |
| Ban Time  | 600 Seconds |

**Result**

* Multiple failed login attempts automatically triggered an IP ban.
* Successfully mitigated SSH brute-force attacks.

---

### Firewall Hardening

Configured UFW (Uncomplicated Firewall).

#### Default Policies

| Policy   | Action |
| -------- | ------ |
| Incoming | Deny   |
| Outgoing | Allow  |

#### Allowed Services

| Service | Port   |
| ------- | ------ |
| SSH     | 22/TCP |

**Benefits**

* Reduced attack surface
* Blocked unauthorized incoming traffic
* Improved network security posture

---

### DoS/DDoS Mitigation

Implemented connection rate limiting using UFW.

```bash
sudo ufw limit ssh
```

**Benefits**

* Prevents excessive SSH connection attempts
* Mitigates brute-force attacks
* Provides basic DoS protection

---

### Endpoint Security

Implemented ClamAV Antivirus.

#### Features

* Malware signature database updated
* Over 3.6 million virus signatures
* Real-time malware detection capability

#### Validation

The antivirus functionality was verified using the EICAR test file.

| Parameter        | Result     |
| ---------------- | ---------- |
| Files Scanned    | 1          |
| Threats Detected | 1          |
| Detection Status | Successful |

---

### Data Protection

Created a protected directory to simulate confidential business information.

#### Protected Assets

```text
/company-data/salaries.txt
/company-data/clients.txt
```

#### Access Restrictions

| User      | Access  |
| --------- | ------- |
| manager   | Allowed |
| hr        | Allowed |
| developer | Denied  |

---

### Backup & Business Continuity

Implemented backup procedures for critical business data.

```bash
sudo mkdir /backup
sudo cp -r /company-data /backup
```

**Benefits**

* Supports disaster recovery
* Protects critical business information
* Enables data restoration

---

## Vulnerability Assessment

Implemented Greenbone Vulnerability Management (GVM/OpenVAS).

### Components Installed

* GVMD
* OpenVAS Scanner
* OSPD-OpenVAS
* GSAD
* Greenbone Feed Sync
* Notus Scanner

### Vulnerability Scan Process

The Ubuntu Server was scanned using the **Full and Fast** scan configuration.

#### Scan Activities

* Host Discovery
* Service Enumeration
* Port Analysis
* Vulnerability Detection
* Security Assessment

---

## Vulnerability Findings

| Vulnerability                             | Severity |
| ----------------------------------------- | -------- |
| Report Outdated / End-of-Life Scan Engine | High     |
| Weak MAC Algorithms Supported (SSH)       | Low      |

### Recommendations

* Regularly update vulnerability feeds.
* Upgrade outdated software components.
* Harden SSH configuration.
* Conduct periodic vulnerability assessments.

---

## Risk Assessment Matrix

| Threat             | Likelihood | Impact | Risk Level |
| ------------------ | ---------- | ------ | ---------- |
| Phishing           | High       | High   | Critical   |
| Ransomware         | High       | High   | Critical   |
| Insider Threat     | Medium     | High   | High       |
| Brute Force Attack | High       | Medium | High       |
| Data Breach        | Medium     | High   | High       |
| DoS Attack         | Medium     | Medium | Medium     |

---

## Incident Response Plan

1. Detection
2. Containment
3. Eradication
4. Recovery
5. Post-Incident Review

### Example Workflow

```text
Detect Threat
      ↓
Contain Incident
      ↓
Remove Threat
      ↓
Restore Systems
      ↓
Review & Improve
```

---

## Security Awareness Training

Monthly employee awareness sessions covering:

* Phishing Detection
* Password Security
* Safe Browsing Practices
* Incident Reporting Procedures

---

## Technologies Used

| Category                 | Tools                  |
| ------------------------ | ---------------------- |
| Firewall                 | UFW                    |
| DoS Protection           | UFW Rate Limiting      |
| Brute Force Protection   | Fail2Ban               |
| Antivirus                | ClamAV                 |
| Vulnerability Assessment | OpenVAS / Greenbone    |
| Attack Simulation        | Kali Linux             |
| Network Scanning         | Nmap                   |
| Remote Access            | OpenSSH                |
| Backup                   | Linux Backup Utilities |

---

## Project Outcomes

* Successfully implemented a layered cybersecurity framework.
* Improved access control and user security.
* Protected remote services from brute-force attacks.
* Strengthened endpoint security using open-source antivirus solutions.
* Performed vulnerability assessments and remediation planning.
* Established backup and incident response procedures.
* Demonstrated a practical cybersecurity solution suitable for small businesses.

---

## Author

**Subin R**

B.Tech Computer Engineering

