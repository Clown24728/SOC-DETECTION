# SOC-DETECTION
Detection, Investigation, and Response to modern ransomware attacks in a Hybrid Enterprise     
JUNE COHORT PLURACODE   
DATE : OCTOBER 14th 2026    
# Background & Problem   
Ransomware continues to rank among the most destructive cyber threats in 2026.Modern campaigns frequently combine double or triple extortion ,AI generated phishing, living-off-the-land techniques, and rapid encryption of both on-premises and cloud assets.  
Many organizations still struggles to detect these attacks early enough, resulting in prolonged downtime ,dataloss ,significant financial costs, and reputational damage .traditional antivirus and basic monitoring alone no longer provide adequate visibility or response speed .  
Security Operation Center (SOC) teams therefore require robust detection methods ,structured investigation processes ,and clear response plans to effectively manage ransomware incidents.     
# The lab is built entirely on a single physical host using VMware Workstation. The Windows 11 virtual machine represents the monitored endpoint, while Splunk Enterprise runs directly on the host machine and plays the role of the central SIEM.This document covers Phase 1 only: getting visibility working. Later phases will build on this foundation.  
## Table of Contents

- [Project Overview](#project-overview)
- [General Objectives](#general-objectives)
- [Phase 1 Objective](#objective)
- [Tools Used](#tools-used)
- [Lab Architecture](#lab-architecture)
- [Walkthrough](#walkthrough)
- [Results (So Far)](#results-so-far)
- [Skills Demonstrated](#skills-demonstrated)
- [Next Steps](#next-steps)
# General Objective   
- Design a realistic lab architecture representing the victim organization.
- Simulate a ransomware incident in the lab and collect relevant digital evidence.
- identify the document key indicators of compromise.
- Map observation attack stages to the MITRE ATT&CK framework.
- Create practical detection rules,such as sigma rule or SIEM queries to identify relevant activity earlier.
- Develop an actionable incidence response plan.
- Present the findings in a professional final presentation.
  # Phase 1 objective
- Set up a Windows 11 virtual machine in VMware Workstation to serve as the monitored endpoint.
- Install and configure Splunk Enterprise on the host machine to act as the central SIEM.
- Install the Splunk Universal Forwarder on the Windows VM to transmit log data to Splunk.
- Install Sysmon on the Windows VM with the SwiftOnSecurity configuration for high-quality, low-noise event logging.
- Configure log forwarding between the VM and Splunk Enterprise over the standard Splunk-to-Splunk port (9997).
- Verify that logs are actually being generated, forwarded, and searchable — not just that services report as running.
- Diagnose and document any issues encountered along the way, rather than only presenting a clean end result.
  ## Tools Used

## Tools Used
| Component                  | Technology                              |
|----------------------------|-----------------------------------------|
| Monitored Endpoint         | Windows 10 (VMware Workstation)         |
| SIEM Platform              | Splunk Enterprise (host machine)        |
| Log Forwarding Agent       | Splunk Universal Forwarder              |
| Endpoint Telemetry         | Sysmon (SwiftOnSecurity configuration)  |
| Future Attack Simulation   | Kali Linux                              |  
| Phishing Attack            | Apache (Ransomware equivalent)
# lab architecture  
The diagram below shows how the components in this lab relate to one another. The Windows 11 VM sits inside VMware Workstation and runs two things side by side: Sysmon, which watches the operating system and generates detailed telemetry (process creation, file creation, network connections, and more), and the Splunk Universal Forwarder, which is responsible for reading both Sysmon's event log and the standard Windows Event Logs (Security, System, Application) and shipping that data off the VM. The Forwarder sends everything over TCP port 9997 to Splunk Enterprise, which runs on the host machine outside the VM and is responsible for indexing the data and making it searchable.
<img width="1580" height="819" alt="image" src="https://github.com/user-attachments/assets/ec28a9b7-ff5e-4bca-9986-c407b1aad13a" />    
Figure 1. Log flow from the Windows 11 VM to Splunk Enterprise on the host machine.  

# SOC Home Lab – Phase 1

**Windows 10 Endpoint → Splunk Enterprise Pipeline**

![Figure 1](images/log-flow-diagram.png)  
*Figure 1. Log flow from the Windows 10 VM to Splunk Enterprise on the host machine.*

# Walkthrough

This project is documented as a set of linked, focused write-ups rather than one long file. Each one covers a single stage of the pipeline in full detail, with screenshots.
  
1. [Splunk Enterprise Installation](docs/01-splunk-enterprise-installation.md) — standing up the SIEM on the host machine  
3. [Splunk Universal Forwarder Installation & Configuration](docs/02-universal-forwarder-config.md) — connecting the VM to Splunk Enterprise  
3. [Sysmon Installation & Configuration](docs/03-sysmon-installation.md) — adding high-quality endpoint telemetry with the SwiftOnSecurity config  
4. [Troubleshooting: Event view Issue](docs/04-troubleshooting-event-forwarding.md) — a real configuration issue found and worked through during validation

# Results (So Far)

- General Windows Event Log data (Security, System) is confirmed flowing into Splunk and is fully searchable
- Sysmon is confirmed to be correctly installed and actively generating detailed local telemetry (Event ID 1 and others), using the SwiftOnSecurity configuration
- event view is used for logs; forwarding to Splunk is in progress / resolved (update this bullet as needed)
