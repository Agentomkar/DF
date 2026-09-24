# 🔬 Ghidra: Reverse Engineering & Malware Analysis

> **Experiment 10** | Digital Forensics Lab  
> *Disassemble and analyze binaries using Ghidra's reverse-engineering framework*

---

## 📋 Table of Contents
- [📋 Overview](#overview)
- [⚙️ Setup & Requirements](#setup--requirements)
- [🎯 Project Creation](#project-creation)
- [📂 Binary Import & Analysis](#binary-import--analysis)
- [🔍 Code Analysis](#code-analysis)
- [🎓 Advanced Techniques](#advanced-techniques)

---

## 📋 Overview

<img src="https://img.shields.io/badge/Ghidra-Reverse_Engineering-blue?style=flat-square" alt="Ghidra">

**Ghidra** is a software reverse-engineering framework that enables you to:

- **Disassemble** binary files into assembly code
- **Decompile** low-level code into higher-level representations
- **Analyze** functions, strings, and imports
- **Identify** malware characteristics and behavior
- **Examine** network communication, persistence mechanisms, anti-analysis techniques
- **Create** custom analysis scripts and tools

**Key Objectives:**
- Disassemble and analyze binaries
- Recognize malware-related functionality
- Identify persistence mechanisms
- Examine anti-analysis techniques
- Analyze possible network communication

---

## ⚙️ Setup & Requirements

### Prerequisites
- **Ghidra** (latest version)
- **Java Runtime Environment** (JRE 11+)
- Windows / Linux / macOS system
- **Isolated virtual machine** (recommended for malware analysis)
- Benign or controlled sample binary
- GitHub repository for documentation

### Verify Java Installation

```bash
java -version
```

**Expected Output:**
```
openjdk version "11.0.x"
```

### Download & Install Ghidra

1. Visit [NSA Ghidra GitHub](https://github.com/NationalSecurityAgency/ghidra)
2. Download latest release
3. Extract to suitable directory
4. Launch: `ghidraRun` (Linux/macOS) or `ghidraRun.bat` (Windows)

---

## 🎯 Project Creation

### Step 1️⃣ Launch Ghidra

Run the Ghidra launcher:
```bash
./ghidra/bin/ghidraRun
```

### Step 2️⃣ Create New Project

1. File → **New Project**
2. Select project type: **Non-Shared Project**
3. Choose directory path
4. Enter project name (e.g., `Malware-Analysis-Lab`)
5. Click **Finish**

### Step 3️⃣ Project Structure

```
Ghidra-Projects/
├── Malware-Analysis-Lab/
│   ├── .ghidra_scripts/
│   ├── .rep/
│   └── [imported binaries]
```

---

## 📂 Binary Import & Analysis

### Step 1️⃣ Import Binary File

1. Open Ghidra project
2. File → **Import File**
3. Select sample binary
4. Review detected format (PE, ELF, Mach-O, etc.)
5. Configure processor/language if needed
6. Click **OK**

**Supported Formats:**
- PE (Windows executables)
- ELF (Linux executables)
- Mach-O (macOS executables)
- Raw binary files
- Hex dumps

### Step 2️⃣ Start Code Browser

1. Double-click imported program
2. Ghidra opens **CodeBrowser**
3. Analysis dialog appears

**Analysis Options (Keep Enabled):**
- ✅ Decompiler Parameter ID
- ✅ Call Convention ID  
- ✅ Stack
- ✅ Data Reference
- ✅ Stack References
- ✅ Function Start Search
- ✅ Create Address Tables

### Step 3️⃣ Auto-Analysis Completion

- Wait for analysis to finish
- Progress bar shows completion status
- Status messages indicate phases

**Output screenshots go here:**

---

## 🔍 Code Analysis

### Entry Point Analysis

**Purpose:** Identify where program execution begins

1. Window → **Memory Map**
2. Look for `.text` section (code section)
3. Right-click entry point
4. Select **Go To** or **Show References**

**Common Entry Points:**
```
_start (Linux)
main (High-level)
entry (Generic)
WinMain (Windows GUI)
DllMain (Windows DLL)
```

### Function Analysis

#### Symbol Tree View

1. Window → **Symbol Tree**
2. Expand **Functions** node
3. Examine function list:

```
Functions
├── entry
├── main
├── malloc
├── free
├── printf
├── CreateFileA
├── ReadFile
└── [custom functions]
```

#### Analyze Individual Function

1. Click function name
2. CodeBrowser shows:
   - **Listing view:** Assembly code
   - **Decompiler view:** High-level code
   - **References:** Where function is called

**Function Characteristics:**
- Function name
- Parameters passed
- Return value
- Local variables
- Called functions
- Cross-references

### String Analysis

#### Locate Strings

Window → **Defined Strings**

**Suspicious String Indicators:**
```
http://
https://
cmd.exe
powershell.exe
reg.exe
\\Registry
HKLM\
User-Agent
GET /
POST /
```

**Investigation Record:**

| String | Found In | Observation |
|--------|----------|-------------|
| `cmd.exe` | function_001 | Process execution |
| `http://example.com` | function_004 | Network connection |
| `HKLM\Run` | function_007 | Registry persistence |

### Import Analysis

#### Examine Imported Functions

1. Window → **Relocation Table** or **Imports**
2. Review imported DLLs and functions

**Suspicious Import Categories:**

| Category | APIs | Indication |
|----------|------|-----------|
| **File System** | CreateFileA, WriteFile, DeleteFileA | File manipulation |
| **Network** | WSAConnect, send, recv | Network communication |
| **Registry** | RegSetValueEx, RegCreateKey | Persistence/Config |
| **Process** | CreateProcessA, ShellExecuteA | Process creation |
| **Memory** | VirtualAlloc, WriteProcessMemory | Code injection |

---

## 🎓 Advanced Techniques

### Decompiler Analysis

1. Select function in Symbol Tree
2. **Decompiler window** automatically updates
3. Shows C-like pseudocode representation

**Decompiler Benefits:**
- Higher-level understanding
- Variable names and types
- Control flow visibility
- Loop and conditional analysis

**Limitations:**
- May contain inaccuracies
- Always cross-reference with assembly
- Obfuscation confuses decompiler

### Cross-References (XREF)

**Finding where something is used:**

1. Right-click address/function
2. Select **Show References**
3. View calling functions

**Example Flow:**
```
malicious_string
    ↓
XREF → function_001
    ↓
Called by → main
    ↓
Entry point analysis
```

### Control Flow Analysis

**Visualize execution paths:**

1. Right-click function
2. Select **Show Function Graph**
3. Display shows:
   - Basic blocks
   - Conditional branches
   - Loop structure
   - Function calls

### Decompiled Code Example

```c
undefined4 function_001(void)
{
  HANDLE hFile;
  DWORD dwBytesWritten;
  
  hFile = CreateFileA("C:\\temp\\log.txt", 0x40000000, 0, NULL, 2, 0x80, NULL);
  if (hFile == (HANDLE)0xffffffff)
  {
    return 0;
  }
  WriteFile(hFile, "Malware activity log", 20, &dwBytesWritten, NULL);
  CloseHandle(hFile);
  return 1;
}
```

### Persistence Mechanism Detection

**Look for:**
- Registry modifications (`HKLM\Run`, `HKCU\Run`)
- Startup folder access
- Scheduled task creation
- Service installation
- Windows hooks

### Anti-Analysis Techniques

**Common Obfuscation:**
```
- Unusual control flow
- Dead code
- Packed sections
- Debugger checks
- Virtual machine detection
- Junk instructions
```

### Python Scripting

**Automate analysis tasks:**

```python
# Extract all strings
for s in currentProgram.getListing().getDefinedData():
    if s.getDataType().getName() == "string":
        print(s.getValue())

# List all functions
for f in currentProgram.getFunctionManager().getFunctions(True):
    print(f.getName())
```

---

## 📋 Investigation Report

### Observation Table

| S.No | Finding | Type | Location | Risk |
|---:|---|---|---|---|
| 1 | Network string detected | IOC | function_004 | High |
| 2 | Registry modification | Persistence | function_007 | High |
| 3 | Process creation API | Behavior | CreateProcessA | Medium |
| 4 | Suspicious import list | Imports | IAT | High |

### Report Format

**Title:** Ghidra Binary Analysis Report

**Analysis Summary:**
- Binary type and architecture
- Entry point and main function
- Notable functions and strings
- Detected APIs and behaviors

**Findings:**
- Suspicious network indicators
- Persistence mechanisms
- Anti-analysis techniques
- Possible malware classification

**Conclusion:**
- Likely benign or malicious
- Recommended actions
- Further investigation areas

---

## ✅ Best Practices

- [ ] Use **isolated environment** for analysis
- [ ] Document all **suspicious findings**
- [ ] Cross-reference **assembly and decompiler** output
- [ ] **Verify** decompiler assumptions
- [ ] Track **function cross-references**
- [ ] Note **string contexts** carefully
- [ ] Examine **import usage** in functions
- [ ] Create **analysis scripts** for repetitive tasks
- [ ] Preserve **evidence** and documentation
- [ ] **Never execute** unknown malware directly

---

## 📚 References

- 🔗 [Ghidra GitHub Repository](https://github.com/NationalSecurityAgency/ghidra)
- 📖 [Ghidra User Guide](https://ghidra-sre.org/CheatSheet.html)
- 🎓 [Reverse Engineering Guide](https://en.wikibooks.org/wiki/X86_Assembly)
- 🔬 [NIST Malware Analysis Guidelines](https://www.nist.gov/)

---

## 🖼️ Output Screenshots

**Screenshots to be added:**
- Ghidra project creation
- Binary import dialog
- CodeBrowser with assembly
- Decompiler window
- Symbol tree view
- String analysis results
- Import analysis
- Control flow graph
- Analysis completion

---

<div align="center">

**📌 Lab:** Digital Forensics | **Ex. No:** 10  
**Tool:** Ghidra (NSA) | **Date:** 2026

</div>
