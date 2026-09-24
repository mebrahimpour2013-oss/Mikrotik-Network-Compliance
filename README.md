# MikroTik Network Compliance Automation

A Python-based, read-only security and configuration assessment tool for MikroTik RouterOS devices.

The project connects to a MikroTik router through the RouterOS API, evaluates a defined set of operational and security controls, and produces structured PASS / WARNING / FAIL results with an overall compliance score.

## Overview

MikroTik Network Compliance Automation is designed to support repeatable security reviews of MikroTik-based network infrastructure.

Instead of manually reviewing individual RouterOS settings, the tool collects relevant configuration data through the API and evaluates predefined controls covering:

- Management services
- Network services
- Firewall configuration
- WAN protection
- NAT
- IP addressing
- DHCP
- DNS
- VPN
- RouterOS users

The assessment is read-only. The tool does not modify the router configuration.

## Key Capabilities

- RouterOS device identification
- RouterOS version, hardware and architecture detection
- Management service assessment
- FTP, Telnet, HTTP and API security checks
- WinBox and SSH management access restriction checks
- Firewall rule assessment
- Established/related connection handling check
- Invalid traffic protection check
- WAN input and forwarding protection checks
- NAT masquerade validation
- Active IP address detection
- DHCP server assessment
- DNS configuration assessment
- Remote DNS request check
- L2TP/IPsec configuration assessment
- RouterOS user assessment
- PASS / WARNING / FAIL classification
- Automated compliance score calculation
- Console-based compliance results
- HTML compliance report generation

## Assessment Areas

| Area | Examples of Checks |
|---|---|
| Services | FTP, Telnet, HTTP, API, API-SSL |
| Management | WinBox and SSH access restrictions |
| Firewall | Active rules, established/related, invalid traffic |
| WAN Security | Input and forwarding protection |
| NAT | Source NAT / masquerade |
| Network | Active IP addresses |
| DHCP | Active DHCP servers |
| DNS | DNS servers and remote requests |
| VPN | L2TP and IPsec usage |
| Users | Active RouterOS users |

## Assessment Model

Each control produces one of three states:

### PASS

The evaluated configuration satisfies the defined requirement.

### WARNING

The configuration requires attention or the tool cannot establish a strong PASS/FAIL condition from the available data.

### FAIL

The evaluated configuration does not satisfy the defined requirement.

An overall score is calculated from the number of controls that receive a PASS result.

> Important: The score represents this project's defined assessment rules. It should not be interpreted as certification against a specific external security standard unless the rule set is explicitly mapped and validated against that standard.

## Architecture

`text
                  MikroTik RouterOS
                         │
                         │ RouterOS API
                         ▼
              ┌─────────────────────┐
              │  Python Compliance  │
              │       Engine        │
              └──────────┬──────────┘
                         │
          ┌──────────────┼──────────────┐
          │              │              │
          ▼              ▼              ▼
      Services        Firewall       Network
      Management      WAN/NAT        DHCP/DNS
          │              │              │
          └──────────────┼──────────────┘
                         ▼
                Compliance Results
                         │
              ┌──────────┴──────────┐
              ▼                     ▼
        Console Output          HTML Report

#Project Structure

Mikrotik-Network-Compliance/
├── Mikrotik_compliance.py
├── Mikrotik_compliance_HTML.py
├── requirements.txt
├── .gitignore
└── README.md

#Technology Stack

Python

MikroTik RouterOS

RouterOS API

librouteros
Network Security

Network Automation

HTML reporting


#Requirements

Python 3.x and the required Python dependency:

librouteros==4.2.2

Install dependencies:

pip install -r requirements.txt

#Usage

Console Assessment

Run the standard compliance checker:

python Mikrotik_compliance.py

The tool connects to the configured MikroTik device, evaluates the defined controls and prints the assessment results and summary.

HTML Report

Run the HTML reporting version:

python Mikrotik_compliance_HTML.py

This version performs the same assessment workflow and generates an HTML report containing:

Device information

RouterOS information

Compliance score

PASS / WARNING / FAIL summary

Detailed assessment table

Report generation timestamp


#Security and Operational Model

The assessment engine uses the RouterOS API to read configuration and operational information.

The project is intentionally designed as a read-only assessment workflow:

Connect
   │
   ▼
Collect configuration data
   │
   ▼
Evaluate predefined controls
   │
   ▼
Classify results
   │
   ▼
Calculate score
   │
   ├──► Console report
   │
   └──► HTML report

No configuration changes are issued by the assessment engine.

#Scope and Limitations

This project evaluates a defined set of MikroTik RouterOS controls. It is intended to provide a repeatable technical assessment workflow rather than claim complete security coverage.

The result can be affected by:

RouterOS version and available API properties

Network architecture

Device role

Security requirements of the organization

The specific controls implemented by this project


For production security assessments, the defined rules should be reviewed against the organization's security baseline and applicable standards.

#Practical Use Cases

The project can be used as a foundation for:

Periodic MikroTik security reviews

Configuration compliance checks

Network security assessments

Pre-audit technical reviews

Baseline verification

Automated security reporting

Network operations automation

Expansion into multi-device compliance workflows


#Future Extensions

Potential next-stage improvements include:

Externalized configuration and credentials

Structured JSON output

Centralized logging

Multi-device assessment

Configuration baseline comparison

Scheduled assessments

Report archiving

Additional RouterOS security controls

Rule profiles for different organizational security baselines

Integration with centralized monitoring or reporting systems


#Project Context

This repository represents a practical Network Security + Network Automation implementation built around MikroTik RouterOS.

The project focuses on turning manual configuration review into a repeatable, programmatic assessment workflow and presenting the results in a form suitable for operational review.

Sensitive infrastructure details are intentionally not part of the project documentation.

#Disclaimer

This tool is intended for authorized network administration, security assessment, testing and educational purposes.

Only run the assessment against MikroTik devices for which you have explicit authorization.

#Author

Mohammad Ebrahimpour

Network & IT Infrastructure | Network Automation | Network Security