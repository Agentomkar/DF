# Digital Forensics Lab

<p align="center">
  <img src="https://img.shields.io/badge/Domain-Digital%20Forensics-0f172a?style=for-the-badge" alt="Digital Forensics">
  <img src="https://img.shields.io/badge/DFIR-Hands--On%20Labs-1e293b?style=for-the-badge" alt="DFIR">
  <img src="https://img.shields.io/badge/Documentation-Markdown-334155?style=for-the-badge" alt="Documentation">
  <img src="https://img.shields.io/github/last-commit/Agentomkar/DF?style=for-the-badge" alt="Last Commit">
</p>

<p align="center">
  <strong>A hands-on Digital Forensics laboratory covering evidence acquisition, disk analysis, network forensics, mobile extraction, steganography, reverse engineering, and forensic investigation workflows.</strong>
</p>

<p align="center">
  <a href="https://github.com/Agentomkar/DF">Repository</a> •
  <a href="#experiments">Experiments</a> •
  <a href="#tools-covered">Tools</a> •
  <a href="#repository-structure">Structure</a> •
  <a href="#learning-outcomes">Learning Outcomes</a>
</p>

---

## About

This repository contains a structured collection of **Digital Forensics and Incident Response (DFIR) laboratory experiments**.

Each experiment documents a practical forensic workflow using industry-relevant tools and techniques. The documentation focuses on **what the tool does, how it is configured, how evidence is examined, and how findings are documented**.

The repository is designed to serve as:

- A practical Digital Forensics laboratory record
- A reference for forensic investigation workflows
- A learning resource for cybersecurity students
- A documented collection of DFIR experiments
- A portfolio demonstrating hands-on security tooling experience

> **Focus:** Acquire → Preserve → Examine → Analyze → Document

---

## What This Repository Covers

The experiments span multiple areas of digital forensics:

| Area | Coverage |
|---|---|
| Evidence Acquisition | RAM and disk acquisition |
| Disk Forensics | Partition, filesystem and disk-image analysis |
| File Recovery | Deleted data and filesystem recovery |
| Network Forensics | Packet capture and HTTP analysis |
| Email Forensics | Header analysis, spoofing and authentication |
| Computer Forensics | Case creation, ingest and artifact analysis |
| Mobile Forensics | Android logical extraction |
| Steganography | Detection of hidden information in images |
| System Analysis | Process and system activity investigation |
| Reverse Engineering | Binary analysis and malware-oriented investigation |

---

# Experiments

## 01 — FTK Imager

**Evidence Acquisition & Memory Forensics**

Learn how to acquire volatile and non-volatile forensic evidence using FTK Imager.

### Topics

- RAM acquisition
- Disk imaging
- Memory dump creation
- Pagefile acquisition
- Evidence preservation
- Forensic image verification
- Evidence documentation

**Tool:** FTK Imager

[View Experiment →](./exp-1-ftk%20imager.md)

---

## 02 — TestDisk

**EFI/GPT Partition Recovery**

Practical investigation of damaged or missing partitions using TestDisk on modern EFI/GPT systems.

### Topics

- EFI/GPT partition structures
- Disk selection
- Partition table analysis
- Quick partition search
- Lost partition recovery
- Filesystem recovery
- Recovery logging

**Tool:** TestDisk

[View Experiment →](./exp-3-testdisk-efi-gpt.md)

---

## 03 — Wireshark

**Network Packet & Credential Analysis**

Analyze captured network traffic and understand how information can be exposed through unencrypted protocols.

### Topics

- Packet capture
- HTTP analysis
- GET/POST requests
- Network filtering
- Credential exposure
- Protocol analysis
- Packet-level investigation

**Tool:** Wireshark

[View Experiment →](./exp-3-wireshark-password.md)

> **Ethical use:** Network traffic interception must only be performed on systems and networks where you have explicit authorization.

---

## 04 — Email Header Analysis

**Spoofing & Phishing Investigation**

Investigate email metadata and identify indicators associated with spoofing, phishing, and authentication failures.

### Topics

- Email header extraction
- `Received` header analysis
- Sender verification
- IP and domain analysis
- SPF
- DKIM
- DMARC
- Phishing indicators
- Header anomalies

**Tools:** Mail Header Analyzer and email clients

[View Experiment →](./exp-4-email-header.md)

---

## 05 — Autopsy

**Digital Evidence Examination**

Create forensic cases, process disk images, analyze artifacts, and generate investigation reports using Autopsy.

### Topics

- Forensic case creation
- E01 evidence processing
- Split disk images
- Ingest modules
- Deleted-file analysis
- Metadata examination
- Timeline analysis
- Keyword searching
- Hash-based filtering
- Report generation

**Tool:** Autopsy

[View Experiment →](./exp-5-autopsy-forensics.md)

---

## 06 — Sleuth Kit

**Filesystem & Digital Evidence Analysis**

Use command-line forensic utilities to inspect disk images and recover digital evidence.

### Topics

- Filesystem identification
- Partition analysis
- Disk-image examination
- File metadata
- Deleted-file recovery
- Timeline analysis
- Evidence extraction
- Command-line forensic workflows

**Tool:** The Sleuth Kit

[View Experiment →](./ex-6-sleuth-kit.md)

---

## 07 — AFLogical OSE

**Android Mobile Forensics**

Perform logical extraction of forensic artifacts from Android devices using ADB and AFLogical OSE.

### Topics

- Android Debug Bridge
- USB debugging
- Logical extraction
- Contact extraction
- SMS/MMS analysis
- Call-log extraction
- CSV evidence collection
- Mobile artifact examination

**Tools:** AFLogical OSE, ADB, Java

[View Experiment →](./ex-7-aflogical-ose.md)

---

## 08 — StegExpose

**Steganography Detection**

Analyze images for potential hidden information using statistical steganalysis techniques.

### Topics

- Image analysis
- Steganography detection
- Statistical analysis
- Suspect-score interpretation
- Single-image analysis
- Batch analysis
- Evidence recording

**Tool:** StegExpose

[View Experiment →](./ex-8-stegexpose.md)

---

## 09 — Process Explorer

**Windows Process & System Analysis**

Investigate running processes and system activity to understand process behavior and identify potentially suspicious activity.

### Topics

- Process enumeration
- Process properties
- Parent-child relationships
- Resource usage
- System activity
- Process investigation
- Suspicious-process identification

**Tool:** Process Explorer

[View Experiment →](./ex-9-process-explorer.md)

---

## 10 — Ghidra

**Reverse Engineering & Malware Analysis**

Perform static binary analysis using Ghidra's reverse-engineering framework.

### Topics

- Binary importing
- Disassembly
- Decompilation
- Function analysis
- Symbol analysis
- String analysis
- Import analysis
- Cross-references
- Control-flow analysis
- Persistence mechanisms
- Anti-analysis techniques
- Ghidra scripting

**Tool:** Ghidra

[View Experiment →](./ex-10-ghidra.md)

---

# Tools Covered

The repository provides practical exposure to a range of forensic and security tools:

```text
┌──────────────────────────────────────────────────────────┐
│                  DIGITAL FORENSICS LAB                   │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  FTK Imager        → Evidence Acquisition               │
│  TestDisk          → Partition Recovery                 │
│  Wireshark         → Network Forensics                  │
│  Mail Header Tools → Email Forensics                    │
│  Autopsy           → Digital Investigation              │
│  Sleuth Kit        → Filesystem Forensics               │
│  AFLogical OSE     → Android Forensics                  │
│  StegExpose        → Steganalysis                       │
│  Process Explorer  → Windows Analysis                   │
│  Ghidra            → Reverse Engineering                │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

---

# Investigation Workflow

The experiments collectively follow a simplified forensic investigation lifecycle:

```text
                    ┌─────────────────┐
                    │  Digital Event  │
                    └────────┬────────┘
                             │
                             ▼
                 ┌──────────────────────┐
                 │ Evidence Acquisition │
                 │  FTK Imager / ADB    │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Evidence Preservation│
                 │ Hashes / Disk Images │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Evidence Examination │
                 │ Autopsy / Sleuth Kit │
                 └──────────┬───────────┘
                            │
            ┌───────────────┼────────────────┐
            ▼               ▼                ▼
      Network Analysis  Email Analysis   File Analysis
       Wireshark          Headers       Filesystems
            │               │                │
            └───────────────┼────────────────┘
                            ▼
                 ┌──────────────────────┐
                 │   Artifact Analysis  │
                 │ Mobile / Stego / PE  │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Reverse Engineering  │
                 │       Ghidra         │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │ Investigation Report │
                 │ Findings & Evidence  │
                 └──────────────────────┘
```

---

# Repository Structure

```text
DF/
│
├── experiments/
│
├── screenshots/
│
├── exp-1-ftk imager.md
├── exp-3-testdisk-efi-gpt.md
├── exp-3-wireshark-password.md
├── exp-4-email-header.md
├── exp-5-autopsy-forensics.md
├── ex-6-sleuth-kit.md
├── ex-7-aflogical-ose.md
├── ex-8-stegexpose.md
├── ex-9-process-explorer.md
├── ex-10-ghidra.md
│
├── login-page-demo.png
├── memdump-mem-screenshot.png
├── wireshark-capture-start.png
├── wireshark-get-method.png
├── wireshark-http-filter.png
└── wireshark-post-method.png
```

The repository also maintains screenshots and practical evidence alongside the written experiment documentation, making the workflows easier to reproduce and verify.

---

# Learning Outcomes

After completing the experiments in this repository, the following practical skills are covered:

### Evidence Handling

- Understand volatile vs. non-volatile evidence
- Acquire forensic memory and disk images
- Preserve evidence during examination
- Understand basic forensic evidence workflows

### Filesystem & Disk Forensics

- Identify partition structures
- Analyze filesystem metadata
- Examine disk images
- Recover deleted or lost data
- Work with forensic image formats

### Network Forensics

- Capture network traffic
- Apply packet filters
- Analyze HTTP requests
- Identify exposed information
- Understand risks of unencrypted protocols

### Email Forensics

- Extract email headers
- Trace message paths
- Examine sender infrastructure
- Understand SPF, DKIM and DMARC
- Identify suspicious email characteristics

### Mobile Forensics

- Connect Android devices through ADB
- Perform logical extraction
- Collect mobile artifacts
- Analyze contacts, messages and call logs

### Steganalysis

- Detect potential hidden information
- Analyze statistical indicators
- Interpret steganographic detection scores

### Reverse Engineering

- Import and analyze binaries
- Read assembly instructions
- Use decompilers
- Investigate functions and strings
- Follow cross-references
- Analyze imports
- Identify possible persistence and anti-analysis behavior

---

# Evidence & Documentation

A major objective of this repository is not simply running forensic tools, but **documenting the investigation process**.

Each experiment follows a practical structure:

```text
Objective
   ↓
Requirements
   ↓
Tool Setup
   ↓
Evidence / Input
   ↓
Investigation Procedure
   ↓
Analysis
   ↓
Observations
   ↓
Results
   ↓
Documentation
```

This makes the repository useful as both a laboratory record and a technical reference.

---

# Ethical & Legal Notice

This repository is intended for **educational, laboratory, and authorized forensic investigation purposes only**.

Some experiments involve techniques capable of exposing sensitive information, including network credentials, email metadata, device data, and potentially malicious binaries.

Do not use these techniques against systems, devices, networks, accounts, or data without appropriate authorization.

For malware and reverse-engineering exercises:

- Use isolated laboratory environments.
- Prefer controlled or benign samples.
- Avoid executing unknown malware on production systems.
- Preserve forensic evidence before analysis.
- Document observations accurately.
- Follow applicable laws, institutional policies, and authorization requirements.

---

# Screenshots

Practical screenshots and evidence from the experiments are maintained in the [`screenshots`](./screenshots) directory.

Example evidence includes:

- FTK Imager acquisition
- Memory-dump capture
- Wireshark packet analysis
- HTTP request inspection
- Forensic tool interfaces
- Investigation results

---

# Getting Started

Clone the repository:

```bash
git clone https://github.com/Agentomkar/DF.git
cd DF
```

Browse the experiments:

```text
01  → FTK Imager
02  → TestDisk
03  → Wireshark
04  → Email Header Analysis
05  → Autopsy
06  → Sleuth Kit
07  → AFLogical OSE
08  → StegExpose
09  → Process Explorer
10  → Ghidra
```

Each experiment contains its own requirements and setup instructions.

> **Note:** Several experiments require external forensic software. Refer to the individual experiment documentation before starting.

---

# Recommended Environment

For a controlled Digital Forensics laboratory:

```text
Operating System
├── Windows 10 / 11
│
├── Forensic Tools
│   ├── FTK Imager
│   ├── Autopsy
│   ├── Sleuth Kit
│   ├── TestDisk
│   ├── Wireshark
│   ├── Process Explorer
│   └── Ghidra
│
├── Mobile Forensics
│   ├── Java
│   ├── Android Debug Bridge
│   └── AFLogical OSE
│
└── Analysis Environment
    ├── Isolated VM
    ├── Controlled evidence
    └── Dedicated storage
```

---

# Why This Repository?

Digital forensics is not just about finding files.

A proper investigation requires understanding:

```text
Evidence
   +
Integrity
   +
Context
   +
Analysis
   +
Correlation
   +
Documentation
   =
Reliable Findings
```

This repository brings these concepts together through practical experiments rather than purely theoretical exercises.

---

# Future Scope

Potential extensions to the laboratory include:

- Memory forensics with Volatility
- Windows Registry analysis
- Browser artifact analysis
- Linux filesystem forensics
- USB artifact investigation
- Timeline reconstruction
- Malware triage
- PCAP investigation
- Windows event-log analysis
- Hash-based evidence verification
- YARA-based malware identification
- Automated forensic reporting

---
#Mentor 

**DR. K. VENKATESH**
K. Venkatesh, “Unravelling Digital Crime Scenes: Pedagogical Strategies in Digital Forensics PBL,” Journal of Engineering Education Transformations, vol. 38, Special Issue 1, pp. 146–152, 2024, doi: 10.16920/jeet/2024/v38is1/24224.
# Author

**Omkar Busa**

Computer Science & Engineering  
Cybersecurity & Digital Forensics Enthusiast

<p align="center">
  <a href="https://github.com/Agentomkar">
    <img src="https://img.shields.io/badge/GitHub-Agentomkar-181717?style=for-the-badge&logo=github" alt="GitHub">
  </a>
  <a href="https://github.com/Agentomkar/DF">
    <img src="https://img.shields.io/badge/Repository-Digital%20Forensics-0f172a?style=for-the-badge&logo=github" alt="Repository">
  </a>
</p>

---

<p align="center">
  <sub>Digital Forensics Laboratory • Hands-on DFIR Documentation • 2026</sub>
</p>
