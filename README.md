# SOC-DETECTION
Detection, Investigation, and Response to modern ransomware attacks in a Hybrid Enterprise     
AUTHOR : ALATISHE IDRIS OLAYIWOLA   
DATE : OCTOBER 14 2026    
# Background & Problem   
Ransomware continues to rank among the most destructive cyber threats in 2026.Modern campaigns frequently combine double or triple extortion ,AI generated phishing, living-off-the-land techniques, and rapid encryption of both on-premises and cloud assets.  
Many organizations still struggles to detect these attacks early enough, resulting in prolonged downtime ,dataloss ,significant financial costs, and reputational damage .traditional antivirus and basic monitoring alone no longer provide adequate visibility or response speed .  
Security Operation Center (SOC) teams therefore require robust detection methods ,structured investigation processes ,and clear response plans to effectively manage ransomware incidents.     
# The lab is built entirely on a single physical host using VMware Workstation. The Windows 11 virtual machine represents the monitored endpoint, while Splunk Enterprise runs directly on the host machine and plays the role of the central SIEM.This document covers Phase 1 only: getting visibility working. Later phases will build on this foundation.  
## Table of Contents

- [Project Overview](#project-overview)
- [General Objectives](#general-objectives)
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

  
  


