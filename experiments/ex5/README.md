# Ex. 5: Create Forensic Case in Autopsy & Import Evidence

**Lab:** Digital Forensics | **Tool:** Autopsy 4.21.0 | **Evidence:** E01/E02 disk image

## Quick Reference
- **Objective:** Create case, import split E01 evidence, process ingest modules, generate report
- **Evidence Files:** 4Dell Latitude CPi.E01 + 4Dell Latitude CPi.E02
- **Time Zone:** GMT+05:30 (Asia/Calcutta)
- **Case Type:** Single-user

## Procedure Overview

### Step 1: Create New Case
```
Case Name: EX05_<EXAMINER>
Case Number: 01
Examiner: <NAME>
Type: Single-User
Storage: Ex. 5 case directory
```

### Step 2: Add Evidence Source
- **Source Type:** Disk Image or VM File
- **Evidence Path:** `D:\df\Evidence\4Dell Latitude CPi.E01`
- **Associated:** E02 file in same directory
- **Time Zone:** GMT+5:30 (Asia/Calcutta)
- **Sector Size:** Auto Detect

### Step 3: Configure Ingest Modules
Selected modules for analysis:
- ✓ Recent Activity
- ✓ Hash Lookup
- ✓ File Type Identification
- ✓ Extension Mismatch Detector
- ✓ Embedded File Extractor
- ✓ Picture Analyzer
- ✓ Keyword Search
- ✓ E-mail Parser
- ✓ Encryption Detection
- ✓ Interesting Files Identifier

### Step 4: Processing & Analysis
Autopsy processes image → Files analyzed → Artifacts extracted → Results displayed

### Step 5: Examine Results
**Tree view categories:**
- File Types (images, videos, audio, archives, docs, DBs, executables)
- Deleted Files
- File Size
- Data Artifacts (emails, accounts, programs, USB devices, bookmarks, cookies, history)
- Operating System Information
- Recent Documents
- Run Programs
- Web activity

**File metadata displayed:**
- Name, path, type, size, timestamps
- Allocation status
- MD5 & SHA-256 hashes
- Hash lookup results
- Image preview

### Step 6: Generate Report
1. Select **Generate Report**
2. Choose report type (HTML/PDF)
3. Select result types to include
4. Choose report modules
5. Configure save location
6. Report generation completes

**Report includes:**
- Case summary & image info
- File analysis results
- Data artifacts
- Authentication results
- Metadata summary

---

## Key Artifacts Extracted
| Category | Examples |
|----------|----------|
| **Communications** | E-mail messages, accounts, chat history |
| **System Info** | OS details, installed programs, user accounts |
| **Web Activity** | Bookmarks, cookies, history, search queries |
| **Files** | Recent documents, deleted files, thumbnails |
| **Devices** | USB devices, external storage, network info |

---

## Observations
✓ E01 image imported successfully  
✓ E02 segment located in evidence directory  
✓ File-type categorization complete  
✓ Deleted files identified  
✓ Metadata & hashes displayed  
✓ HTML forensic report generated  

**⚠️ Note:** If report generated during analysis, regenerate after ingest completes.

---
**Result:** Forensic case created, evidence processed, artifacts extracted, report generated.
