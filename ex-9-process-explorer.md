# 🔍 Process Explorer: Identify Suspicious Processes

> **Experiment 9** | Digital Forensics Lab  
> *Using Process Explorer to monitor and investigate potentially malicious processes*

---

## 📋 Table of Contents
- [📋 Overview](#overview)
- [⚙️ Setup & Prerequisites](#setup--prerequisites)
- [🎨 Understanding Process Colors](#understanding-process-colors)
- [🔎 Process Analysis](#process-analysis)
- [⚠️ Identifying Suspicious Processes](#identifying-suspicious-processes)
- [🛡️ Response Actions](#response-actions)

---

## 📋 Overview

<img src="https://img.shields.io/badge/Process_Explorer-Sysinternals-blue?style=flat-square" alt="Tool">

**Process Explorer** is a Windows system-monitoring tool from Microsoft Sysinternals that provides detailed information about running processes:

- Process hierarchy (parent-child relationships)
- Process ID (PID)
- CPU & Memory usage
- Digital signatures
- File paths & details
- Network activity
- Company information

---

## ⚙️ Setup & Prerequisites

### Requirements
- Windows operating system
- Administrator privileges
- Process Explorer (64-bit or 32-bit)
- Internet connection for online verification
- Trusted antivirus software

### Download & Extract
1. Download from [Microsoft Sysinternals](https://live.sysinternals.com/)
2. Extract to a folder: `ProcessExplorer/`
3. Run as Administrator:
   - **64-bit:** `procexp64.exe`
   - **32-bit:** `procexp.exe`

---

## 🎨 Understanding Process Colors

| Color | Meaning | Significance |
|-------|---------|--------------|
| **Pink** | Suspended processes | Not currently executing |
| **Light Blue** | User session processes | Running under current user |
| **Dark Blue** | System/Service processes | Running under system accounts |
| **Green** | New processes | Appeared recently (< 1s) |
| **Red** | Exited processes | Just terminated |

> 💡 **Tip:** Rapidly appearing/disappearing green processes warrant investigation.

---

## 🔎 Process Analysis

### Process Information Columns

```
PID (Process ID)
Process Name
CPU Usage
Memory Usage
Description
Company Name
User
Priority
```

### Step 1️⃣ Examine Process Hierarchy

- Processes displayed in **tree structure**
- Parent-child relationships visible
- Legitimate processes follow expected hierarchy
- Unusual parents may indicate injection/compromise

**Example Legitimate:**
```
explorer.exe (Windows Explorer)
├── notepad.exe (launched by user)
└── cmd.exe (command prompt)
```

**Example Suspicious:**
```
svchost.exe (Service)
├── random123.exe (unexpected child)
└── network.exe (unknown process)
```

### Step 2️⃣ Check Process Properties

Right-click process → **Properties** → Examine:

| Tab | Information |
|-----|-------------|
| **General** | Name, PID, Priority |
| **Image** | File path, **Digital signature** |
| **TCP/IP** | Network connections |
| **Memory** | Resource usage details |

---

## ⚠️ Identifying Suspicious Processes

### Red Flags Checklist

- [ ] **Unusual process name** (misspelled system names, random characters)
- [ ] **Unexpected file location** (not in System32, Program Files)
- [ ] **Missing digital signature** (legitimate Windows processes are signed)
- [ ] **Unknown company name** (blank or suspicious publisher)
- [ ] **High CPU/Memory usage** without explanation
- [ ] **Unexpected network activity** (unknown external connections)
- [ ] **Suspicious parent process** (e.g., Notepad spawning explorer.exe)
- [ ] **Running from Temp directory** (AppData\Local\Temp)

### Investigation Workflow

```
1. Identify unfamiliar process
   ↓
2. Check file location
   ↓
3. Verify digital signature
   ↓
4. Review company information
   ↓
5. Monitor network activity
   ↓
6. Search online (VirusTotal, ProcessLibrary)
   ↓
7. Take action if malicious
```

### Example: Suspicious Process "randomname123.exe"

**Observations:**
- CPU Usage: 85%
- Memory: 450 MB
- File Path: `C:\Users\User\AppData\Local\Temp\`
- Digital Signature: None
- Company: Unknown
- TCP/IP: Connections to 192.168.x.x:8080

**Conclusion:** Likely malware → Investigate further

---

## 🛡️ Response Actions

### Verify Process Legitimacy

**Search online for process:**
- [VirusTotal](https://www.virustotal.com)
- [ProcessLibrary](https://www.processlibrary.com)
- Microsoft documentation
- Software vendor sites

### Suspend Process (Temporary)

```
Right-click → Suspend
```
Pauses execution while investigation continues.

### Kill Process (Terminate)

```
Right-click → Kill Process
```
Terminates the process immediately.

> ⚠️ **Warning:** Some malware prevents deletion or restarts automatically.

### Examine Source File

1. Locate file from process properties
2. Check file details & digital signature
3. Scan with antivirus
4. Delete if confirmed malicious (preserve evidence first)

---

## 📋 Investigation Report

### Observation Template

| S.No | Process Name | PID | CPU% | Memory | File Path | Suspicious | Verification |
|---:|---|---:|---:|---:|---|---:|---|
| 1 | suspicious.exe | 1234 | 85 | 450MB | Temp folder | Yes | High resource use, unknown origin |
| 2 | explorer.exe | 5678 | 5 | 120MB | System32 | No | Legitimate Windows process |
| 3 | randomname.exe | 9012 | 60 | 200MB | AppData | Yes | No signature, unusual location |

### Report Format

**Title:** Process Explorer Analysis Report

**Findings:**
- Suspicious processes identified: [count]
- Confirmed malware: [list]
- System processes: [list]

**Conclusion:**
- Actions taken
- Recommendations
- Follow-up required

---

## ✅ Best Practices

- [ ] Run Process Explorer **as Administrator**
- [ ] Analyze on **separate system** from infected device
- [ ] Document **all suspicious findings** with screenshots
- [ ] Verify signatures for **all unknown processes**
- [ ] Cross-reference with **online databases**
- [ ] Preserve **evidence before deletion**
- [ ] Run **full antivirus scan** after investigation
- [ ] Review **Windows Event Logs** for related activity

---

## 📚 References

- 🔗 [Process Explorer Official](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)
- 📖 [Sysinternals Suite Guide](https://learn.microsoft.com/en-us/sysinternals/)
- 🎓 [NIST Malware Analysis](https://www.nist.gov/)
- 🔍 [VirusTotal Malware Scanner](https://www.virustotal.com)

---

## 🖼️ Output Screenshots

**Add your screenshots here:**
- Process Explorer main window
- Suspicious process properties
- Network connections tab
- Digital signature verification
- Analysis results

---

<div align="center">

**📌 Lab:** Digital Forensics | **Ex. No:** 9  
**Tool:** Process Explorer (Sysinternals) | **Date:** 2026

</div>
