# VirtualBox SIEM & SOC Lab

## Overview

This project is a hands-on cybersecurity lab designed to simulate a small Security Operations Center (SOC) environment using Oracle VirtualBox.

The environment uses Wazuh as the Security Information and Event Management (SIEM) platform to collect, analyze, and investigate security events from Windows and Linux endpoints.

The goal of this project is to gain practical experience with security monitoring, log analysis, threat detection, and incident investigation.

## Architecture

## Network Architecture

```mermaid

flowchart TB


```

## Objectives

* Deploy a SIEM platform using VirtualBox
* Configure a secure virtual network
* Deploy and configure Wazuh
* Monitor Windows and Linux endpoints
* Collect and analyze authentication events
* Detect file and system changes
* Monitor activity
* Investigate simulated security incidents
* Map detections to the MITRE ATT&CK framework
* Document incident investigations
* Practice SOC analyst workflows

## Technologies

| Technology                | Purpose                        |
| ------------------------- | ------------------------------ |
| Wazuh                     | SIEM / security monitoring     |
| Windows                   | Endpoint monitoring            |
| Linux                     | Endpoint monitoring            |
| GitHub                    | Project documentation          |
| MITRE ATT&CK              | Threat behavior mapping        |


## Planned Security Scenarios

### Scenario 1: Authentication Failures

Generate multiple failed authentication attempts and investigate the resulting SIEM alerts.

**Objective:** Practice identifying suspicious authentication activity.

### Scenario 2: Unauthorized Account Creation

Create a test account on a lab endpoint and investigate the corresponding security event.

**Objective:** Practice monitoring account-management activity.

### Scenario 3: File Integrity Monitoring

Modify a monitored file and investigate the resulting Wazuh alert.

**Objective:** Practice detecting unauthorized file changes.

### Scenario 4: PowerShell Activity

Generate controlled PowerShell activity on the Windows endpoint and investigate the resulting telemetry.

**Objective:** Practice Windows security monitoring and threat detection.



## Incident Investigation Methodology

Each security event will be investigated using the following process:

1. Identify the alert
2. Determine the affected host 
3. Examine the available logs
4. Establish a timeline
5. Determine the nature of the activity
6. Identify relevant MITRE ATT&CK techniques
7. Determine an appropriate response
8. Document findings
9. Identify lessons learned

## Project Structure

```text
virtualbox-siem-lab/
│
├── README.md
│
├── architecture/
│   └── architecture.png
│
├── documentation/
│   ├── deployment.md
│   ├── aws-monitoring.md
│   └── investigations/
│
├── detections/
│   └── custom-rules/
│
├── screenshots/
│
└── incident-reports/
    ├── incident-001.md
    ├── incident-002.md
    └── incident-003.md
```

## Security Considerations

This project is intended for an isolated educational environment.

No real credentials, private keys, passwords, API keys, tokens, or other sensitive information will be committed to this repository.

Security testing will be performed only against systems owned and controlled as part of this lab.

## Project Status

**Current Phase:** Project initialization

* [x] Create GitHub repository
* [x] Define project architecture
* [x] Build AWS VPC


## Skills Demonstrated

This project will demonstrate practical experience with:

* SIEM deployment
* Security monitoring
* Log analysis
* Incident investigation
* Endpoint security
* Windows security
* Linux security
* IAM
* Network security
* Threat detection
* MITRE ATT&CK
* SOC workflows
* Technical documentation



