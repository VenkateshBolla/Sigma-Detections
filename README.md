# Sigma-Detections
This repo is built based on identification of mitre gaps in multiple client environments and will continuosly update this repo with new detections.
# Sigma Detection Rules — MITRE ATT&CK Gap Coverage

![Rules](https://img.shields.io/badge/Sigma%20Rules-7-blue)
![Status](https://img.shields.io/badge/Status-Actively%20Updated-brightgreen)
![ATT&CK](https://img.shields.io/badge/MITRE%20ATT%26CK-Mapped-red)

## Background

During threat hunting operations across multiple client environments
(banking, insurance, logistics, manufacturing, IT security) in an MSSP
context, I identified recurring MITRE ATT&CK technique coverage gaps —
techniques that attackers were actively using but existing detection rules
were not catching.

This repository is a continuously updated detection library. Every rule
originates from a real gap identified during active threat hunting —
not theoretical exercises. Rules are authored in Sigma format so they
can be deployed across any SIEM without rewriting.

## Rules Authored

| Rule | MITRE Technique | Tactic | Severity | Status |
|------|----------------|--------|----------|--------|
| PowerShell Encoded Command Execution | T1059.001 | Execution / Defense Evasion | High | ✅ Active |
| LSASS Memory Access by Non-System Process | T1003.001 | Credential Access | Critical | ✅ Active |
| Suspicious Scheduled Task Creation | T1053.005 | Persistence | High | ✅ Active |
| Dynamic DNS C2 Communication | T1071.004 / T1568.001 | Command & Control | Medium | ✅ Active |
| Registry Run Key Persistence | T1547.001 | Persistence | Medium | ✅ Active |
| Lateral Movement via PsExec | T1021.002 / T1569.002 | Lateral Movement | High | ✅ Active |
| Base64 Encoded Payload Execution | T1027 | Defense Evasion | High | ✅ Active |

> **Note:** This library is actively maintained. New rules are added as
> additional ATT&CK coverage gaps are identified across client environments.

## Detection Philosophy

- **Gap-driven:** Every rule exists because a real coverage gap was found
- **Behaviour-based:** Rules target adversary TTPs, not IOCs that expire
- **Vendor-agnostic:** Sigma format allows deployment to any SIEM
- **Continuously tuned:** False positive filters are updated as environments evolve

## How to Use

Install sigma-cli, then convert any rule to your SIEM:
```bash
# Install
pip install sigma-cli

# Convert to Microsoft Sentinel (KQL)
sigma convert -t microsoft365defender rules/sigma_rules.yml

# Convert to Splunk
sigma convert -t splunk rules/sigma_rules.yml

# Convert to Elastic
sigma convert -t elasticsearch rules/sigma_rules.yml
```
Or use the browser-based converter at [sigconverter.io](https://sigconverter.io)

## Environment

Rules target Windows endpoints with Sysmon deployed.
Validated against Microsoft Sentinel (KQL) and Splunk (SPL).

## Feedback & Contributions

If you find a false positive or have a tuning suggestion,
open an issue — collaboration is welcome.
