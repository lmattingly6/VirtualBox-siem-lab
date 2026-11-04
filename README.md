# VirtualBox SIEM & SOC Lab

## Overview

This project is a hands-on cybersecurity lab designed to simulate a small Security Operations Center (SOC) environment using Oracle VirtualBox.

The environment uses Wazuh as the Security Information and Event Management (SIEM) platform to collect, analyze, and investigate security events from Windows and Linux endpoints.

The goal of this project is to gain practical experience with security monitoring, log analysis, threat detection, and incident investigation.

## Architecture

## Network Architecture

```mermaid

flowchart TB

    %% HOME NETWORK
    Internet(("🌐 Internet"))
    Router["Home Router<br/>192.168.1.0/24"]

    Internet --- Router

    PC["Personal Computer<br/>192.168.1.113"]


    Router --- PC


    %% VIRTUALBOX ENVIRONMENT
    subgraph VB["VirtualBox Environment"]
        direction TB

        FW["pfSense<br/>Virtual Router & Firewall"]

        %% NETWORK INTERFACES
        WAN["WAN<br/>Bridged Paravirtualized<br/>(virtio-net)"]
        LAN["LAN<br/>Internal Network<br/>(virtio-net)"]
        ISO["ISOLATED<br/>Internal Network"]
        AD["AD_LAB<br/>Internal Network"]
        VULN["VULN_EGRESS<br/>Internal Network"]

        %% NETWORK SEGMENTS
        subgraph NET1["WAN / Management Network"]
            direction TB
            MGT["192.168.1.27"]
        end

        subgraph NET2["LAN - 10.0.0.0/24"]
            direction TB
            SW1["L2 Switch"]
            KALI["Kali Linux<br/>10.0.0.2"]
            SW1 --- KALI
        end

        subgraph NET3["ISOLATED - 10.6.6.0/24"]
            direction TB
            SW2["L2 Switch"]
            VH1["VulnHub VM<br/>10.6.6.13"]
            META["Metasploitable2<br/>10.6.6.22"]
            SW2 --- VH1
            SW2 --- META
        end

        subgraph NET4["AD_LAB - 10.80.80.0/24"]
            direction TB
            SW3["L2 Switch"]
            DC["Domain Controller<br/>10.80.80.2"]
            WIN1["Windows 10 Enterprise 1<br/>10.80.80.32"]
            WIN2["Windows 10 Enterprise 2<br/>10.80.80.43"]
            SW3 --- DC
            SW3 --- WIN1
            SW3 --- WIN2
        end

        subgraph NET5["VULN_EGRESS - 10.10.10.0/24"]
            direction TB
            SW4["L2 Switch"]
            VH2["VulnHub VM<br/>10.10.10.11"]
            VH3["VulnHub VM<br/>10.10.10.12"]
            SW4 --- VH2
            SW4 --- VH3
        end

        subgraph NET6["Network Monitoring"]
            direction TB
            NID["NID8"]
            WAZUH["Wazuh OVA<br/>with Suricata<br/>10.0.0.3"]
            NID -->|"Packet Capture"| WAZUH
        end

        %% PFSENSE CONNECTIONS
        FW --- MGT

        FW ---|"10.0.0.1/24"| SW1
        FW ---|"10.6.6.1/24"| SW2
        FW ---|"10.80.80.1/24"| SW3
        FW ---|"10.10.10.1/24"| SW4

        %% NETWORK MONITORING
        SW4 -.->|"Packet Capture / SPAN"| NID

        %% MANAGEMENT CONNECTION
        KALI -.->|"SSH and SIEM Management"| WAZUH
    end

    %% HOST CONNECTION TO VIRTUALBOX
    PC --- VB


    %% STYLING
    classDef firewall fill:#dce6f1,stroke:#4472c4,stroke-width:2px
    classDef endpoint fill:#d9ead3,stroke:#6aa84f
    classDef isolated fill:#f4cccc,stroke:#cc0000
    classDef adlab fill:#cfe2f3,stroke:#3c78d8
    classDef vuln fill:#fce5cd,stroke:#e69138
    classDef monitoring fill:#cfe2f3,stroke:#6d9eeb
    classDef infrastructure fill:#eeeeee,stroke:#666666

    class FW firewall
    class KALI endpoint
    class VH1,META isolated
    class DC,WIN1,WIN2 adlab
    class VH2,VH3 vuln
    class WAZUH,NID monitoring
    class Router,MGT,SW1,SW2,SW3,SW4 infrastructure
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



