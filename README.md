# MikroTik Network Compliance

A Python-based network compliance and security assessment tool for MikroTik RouterOS devices.

## Overview

This project connects to a MikroTik RouterOS device through the RouterOS API and performs a read-only configuration and security compliance assessment.

The tool checks important areas of the router configuration and generates a compliance report with PASS, WARNING, and FAIL results.

## Features

- Router identity and RouterOS version detection
- Hardware model and architecture detection
- Management service security checks
- WinBox and SSH access restriction checks
- FTP, Telnet and HTTP service checks
- RouterOS API security validation
- Firewall configuration assessment
- WAN input and forwarding protection checks
- NAT masquerade validation
- IP address and DHCP configuration checks
- DNS configuration assessment
- L2TP/IPsec VPN validation
- RouterOS user configuration checks
- Automated compliance scoring
- HTML compliance report generation

## Technologies

- Python
- MikroTik RouterOS 7
- RouterOS API
- librouteros
- Network Security
- Firewall
- VLAN
- VPN
- Network Automation

## Project Structure

Mikrotik-Network-Compliance/
│
├── Mikrotik_compliance.py
├── Mikrotik_compliance_HTML.py
├── requirements.txt
├── .gitignore
└── README.md

Usage

Install the required dependency:

pip install -r requirements.txt

Configure the MikroTik connection parameters in the Python script and run:

python Mikrotik_compliance.py

For the HTML report:

python Mikrotik_compliance_HTML.py

Assessment Model

The compliance engine evaluates configuration items using three states:

PASS — Configuration meets the defined requirement.

WARNING — Configuration requires attention but is not necessarily a critical failure.

FAIL — Configuration does not meet the defined security requirement.


A final compliance score is calculated from the assessment results.

Scope

This project is designed as a business-oriented network security and automation use case for MikroTik-based networks.

The assessment is read-only and does not modify the router configuration.

Disclaimer

This project is intended for authorized network administration, testing, and educational purposes.

Always test configuration and security changes in an appropriate environment before applying them to production infrastructure.
