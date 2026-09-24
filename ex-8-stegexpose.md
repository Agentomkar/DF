# 🔐 StegExpose: Steganography Detection & Analysis

> **Experiment 8** | Digital Forensics Lab  
> *Detecting hidden data in images using statistical steganography analysis*

---

## 📋 Table of Contents
- [✅ Prerequisites](#prerequisites)
- [🎯 Single Image Analysis](#single-image-analysis)
- [📁 Batch Folder Analysis](#batch-folder-analysis)
- [📊 Score Interpretation](#score-interpretation)
- [📝 Results Recording](#results-recording)

---

## ✅ Prerequisites

<img src="https://img.shields.io/badge/Requirements-Met-green?style=flat-square" alt="Ready">

### Verify Java Installation

```cmd
java -version
```

**Expected Output:**
```
java version "25"
Java(TM) SE Runtime Environment
```

### Folder Structure

```
Documents
└── DF
    └── StegExpose-master
        ├── StegExpose.jar
        └── testFolder
            ├── suspect_image.png
            ├── image1.png
            └── image2.png
```

---

## 🎯 Single Image Analysis

### Step 1️⃣ Navigate to StegExpose Directory

```cmd
cd Documents\DF\StegExpose-master
```

---

### Step 2️⃣ Analyze Individual Image

```cmd
java -jar StegExpose.jar testFolder\suspect_image.png
```

**Process:**
- Analyzes statistical properties
- Computes suspect score (0 to 1)
- Returns confidence of steganographic content
- Execution time: 2-5 seconds per image

---

### Step 3️⃣ Record the Score

| Element | Value |
|---------|-------|
| **Command** | `java -jar StegExpose.jar testFolder\suspect_image.png` |
| **Output** | Suspect Score: [0.0 - 1.0] |
| **Required** | Actual score from Command Prompt |

> ⚠️ **Important:** Use actual output score, do NOT invent values.

---

## 📁 Batch Folder Analysis

### Analyze All Images at Once

```cmd
java -jar StegExpose.jar testFolder
```

**Results:**
- Processes all images in `testFolder`
- Generates score for each file
- Comparative analysis across multiple images

---

## 📊 Score Interpretation

<img src="https://img.shields.io/badge/Suspect_Score-Detection-red?style=flat-square" alt="Score">

| Score Range | Status | Interpretation |
|-------------|--------|-----------------|
| **< 0.2** | 🟢 Clean | No steganographic data detected |
| **0.2 - 0.3** | 🟡 Suspicious | Hidden data may be present |
| **> 0.3** | 🔴 Likely | Steganography probably present |

### Example Scoring

```
If Score = 0.4:
→ Steganography is likely present
→ Suspect image may contain hidden data

If Score = 0.15:
→ Image is considered clean
→ No steganographic indicators detected

If Score = 0.25:
→ Hidden data may possibly be present
→ Further investigation recommended
```

---

## 📝 Results Recording

### Observation Table Template

| S.No | Image Name | StegExpose Score | Observation |
|---:|---|---:|---|
| 1 | suspect_image.png | **[Actual Score]** | Based on score interpretation |
| 2 | image1.png | **[Actual Score]** | Based on score interpretation |
| 3 | image2.png | **[Actual Score]** | Based on score interpretation |

### Example Completed Table

| S.No | Image Name | StegExpose Score | Observation |
|---:|---|---:|---|
| 1 | suspect_image.png | **0.42** | Steganography likely present |
| 2 | clean_image.png | **0.15** | Image is clean |
| 3 | suspicious.png | **0.28** | Hidden data may possibly be present |

---

## 🔧 Advanced Options

### View Help Menu

```cmd
java -jar StegExpose.jar --help
```

**Optional Parameters:**
- Verbose output modes
- Detailed analysis options
- Filter configurations

---

## 📋 Report Format

**Observations:**
```
1. suspect_image.png
   - Score: [value]
   - Interpretation: [clean/suspicious/likely]
   - Notes: [additional findings]

2. Other images analyzed
   - Summary of scores
   - Patterns identified
```

**Result:**

```
StegExpose was successfully used to analyze images and 
detect steganographic content based on statistical analysis 
and suspect scoring methodology.

Key Findings:
- [Images with steganography detected]
- [Clean images]
- [Suspicious candidates for further analysis]
```

---

## ✅ Checklist

- [ ] Java verified and working
- [ ] StegExpose.jar located
- [ ] Test images accessible
- [ ] Single image analysis completed
- [ ] Score recorded (actual value)
- [ ] Batch analysis performed
- [ ] Results table filled
- [ ] Report generated

---

## 📚 References

- 🔗 [StegExpose GitHub](https://github.com/b3dk7/StegExpose)
- 📖 [Steganography Detection Guide](https://en.wikipedia.org/wiki/Steganography)
- 🎓 [NIST Digital Forensics](https://www.nist.gov/publications/guidelines-evidence-preservation-and-examination-digital-evidence)

---

<div align="center">

**📌 Lab:** Digital Forensics | **Ex. No:** 8  
**Tool:** StegExpose (Java) | **Date:** 2026

</div>
