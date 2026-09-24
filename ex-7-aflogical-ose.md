# Experiment 7 — Use AFLogical OSE to Extract Data from an Android Device

## Aim / Description

**AFLogical OSE (Open Source Edition)** is a forensic tool used to perform logical extraction of data from Android devices. It connects to an Android device via **Android Debug Bridge (ADB)** and extracts sensitive user data without requiring root access.

The experiment demonstrates:
- Connecting an Android device to a computer using ADB
- Installing AFLogical OSE application on the device
- Performing logical extraction of forensic artifacts
- Transferring extracted data (CSV files) to the computer
- Analyzing extracted contacts, SMS, MMS, and call logs

**Extracted data types:**
- Contacts
- SMS (Short Message Service)
- MMS (Multimedia Messaging Service)
- Call Logs

---

## Requirements

- **Hardware:** Windows/macOS/Linux computer, Android device, USB cable
- **Software:** Java, Android Debug Bridge (ADB), AFLogical OSE
- **Configuration:** USB debugging enabled on Android device

---

## Procedure

### 1. Prepare the Environment

#### 1.1 Install Java

AFLogical OSE requires Java runtime environment.

Verify installation:
```bash
java -version
```

**Expected Output:**
```
java version "X.X.X" XXXX-XX-XX LTS
```

#### 1.2 Install Android Debug Bridge (ADB)

Download and install ADB from the Android SDK platform tools.

Verify installation:
```bash
adb version
```

**Expected Output:**
```
Android Debug Bridge version X.X.X
```

Add ADB directory to system PATH environment variable if needed.

---

### 2. Enable USB Debugging on Android Device

On the target Android device:

1. Open **Settings** → **About Phone**
2. Locate **Build Number** field
3. Tap **Build Number** **7 times** to enable Developer Options
4. Navigate to **Settings** → **Developer Options**
5. Enable **USB Debugging**
6. Grant authorization when prompted on the device

---

### 3. Connect Android Device to Computer

#### 3.1 USB Connection

Connect the Android device to the computer using a USB cable.

When the prompt appears on the device:
```
Allow USB debugging?
```

Review and authorize the connection.

#### 3.2 Verify ADB Connection

Open Command Prompt/Terminal and run:

```bash
adb devices
```

**Expected Output:**
```
List of devices attached
XXXXXXXX    device
```

If the device status shows `device`, the connection is ready.

**Troubleshooting:**
- Verify USB debugging is enabled on the device
- Check USB cable integrity
- Confirm Android USB drivers are installed
- Re-authorize USB debugging if prompted

---

### 4. Download and Prepare AFLogical OSE

#### 4.1 Download AFLogical OSE

Download AFLogical OSE from its GitHub repository or obtain the APK file.

Alternative:
```bash
git clone https://github.com/viaforensics/android-forensics.git
```

#### 4.2 Locate AFLogical APK

Navigate to the directory containing `aflogical.apk`:

```bash
cd path/to/aflogical
```

---

### 5. Install AFLogical OSE on Android Device

Run the following ADB command to install the application:

```bash
adb install aflogical.apk
```

**Expected Output:**
```
Success
```

If installation fails:
- Verify device connection with `adb devices`
- Ensure the APK file path is correct
- Check device storage availability

---

### 6. Launch AFLogical OSE

On the connected Android device:

1. Navigate to **App Drawer**
2. Open the **AFLogical** application
3. Review the available extraction options
4. Select desired data types to extract:
   - ☑ Contacts
   - ☑ SMS
   - ☑ MMS
   - ☑ Call Logs

---

### 7. Execute Data Extraction

1. Verify all required data types are selected
2. Click **Start Extraction** or equivalent button
3. Allow AFLogical OSE to process and extract data
4. Wait for extraction completion (varies by device and data volume)

**Typical completion time:** 1-5 minutes

The extracted data is stored in CSV format in the `aflogical` directory on the device.

---

### 8. Transfer Extracted Data to Computer

#### 8.1 Pull Extracted Files

Use ADB to copy extracted forensic data from the device to the computer:

**Windows:**
```bash
adb pull /sdcard/aflogical C:\Android_Forensics
```

**macOS/Linux:**
```bash
adb pull /sdcard/aflogical ~/Android_Forensics
```

**Expected Output:**
```
pulling from device
aflogical/contacts.csv
aflogical/sms.csv
aflogical/mms.csv
aflogical/call_logs.csv
X files pulled. 0.0s
```

#### 8.2 Verify Extracted Files

Navigate to the destination directory:

```bash
cd C:\Android_Forensics
dir aflogical
```

**Expected directory structure:**
```
Android_Forensics/
└── aflogical/
    ├── contacts.csv
    ├── sms.csv
    ├── mms.csv
    └── call_logs.csv
```

---

## 9. Analyze Extracted Data

### 9.1 Open CSV Files

The extracted files can be viewed using:
- **Microsoft Excel**
- **Google Sheets**
- **LibreOffice Calc**
- **Text Editor** (Notepad, VS Code)

### 9.2 Contacts Analysis

**File:** `contacts.csv`

Extract and review:
- Contact names
- Phone numbers
- Email addresses
- Other associated contact information

**Example CSV structure:**
```
Name,Phone,Email
John Doe,+1-555-1234,john@example.com
Jane Smith,+1-555-5678,jane@example.com
```

### 9.3 SMS Analysis

**File:** `sms.csv`

Review:
- Sender phone numbers
- Recipient phone numbers
- Message content
- Timestamps (sent/received)
- Read status

**Example CSV structure:**
```
From,To,Message,Date,Time,Type
+1-555-1234,+1-555-5678,"Hello world",2026-09-23,14:30:00,Sent
```

### 9.4 MMS Analysis

**File:** `mms.csv`

Examine:
- MMS metadata
- Sender/recipient information
- Attachment references
- Message timestamps

### 9.5 Call Log Analysis

**File:** `call_logs.csv`

Analyze:
- Phone numbers (incoming/outgoing)
- Call duration (in seconds or minutes)
- Call type (incoming, outgoing, missed, rejected)
- Call date and time

**Example CSV structure:**
```
Number,Type,Duration,Date,Time
+1-555-1234,Outgoing,180,2026-09-23,14:30:00
+1-555-5678,Incoming,65,2026-09-23,15:15:00
+1-555-9999,Missed,0,2026-09-23,16:45:00
```

---

## 10. Document Forensic Findings

After analyzing the extracted data:

1. **Identify key forensic artifacts** — Important contacts, messages, communication patterns
2. **Note timestamps and sequences** — Establish timeline of activities
3. **Preserve CSV files** — Maintain integrity of extracted evidence
4. **Prepare forensic report** — Document findings and methodology
5. **Maintain chain of custody** — Record all handling and analysis steps

**Report template:**
```
Device Information
  - Device Model
  - Android Version
  - Extraction Date/Time

Extraction Method
  - Tool: AFLogical OSE
  - Connection: ADB (USB)
  - Extraction Type: Logical

Extracted Artifacts
  - Total Contacts: X
  - Total SMS Messages: X
  - Total MMS Messages: X
  - Total Call Log Entries: X

Key Findings
  - Relevant contacts
  - Suspicious messages
  - Communication patterns
  - Timeline observations

Conclusion
  - Summary of findings
  - Forensic significance
```

---

## 11. Clean Up

### 11.1 Uninstall AFLogical OSE

After completing the forensic extraction and analysis:

```bash
adb uninstall com.viaforensics.android.aflogical
```

**Expected Output:**
```
Success
```

### 11.2 Disconnect Device

```bash
adb disconnect
```

Or physically disconnect the USB cable.

**Important:** Preserve all extracted CSV files and documentation for the forensic case file.

---

## Result

The Android device was successfully connected to the computer using **Android Debug Bridge (ADB)**. **AFLogical OSE** was installed and executed to perform logical extraction of forensic data from the device. The extracted contacts, SMS, MMS, and call-log information was transferred to the computer as CSV files and analyzed for forensic significance.

**Extracted Artifacts:**
- Contacts database (CSV)
- SMS message history (CSV)
- MMS message history (CSV)
- Call log history (CSV)

**Forensic Value:** Logical extraction via AFLogical OSE allows forensic examiners to recover user communications, contact lists, and call activity without requiring device rooting or physical memory access.

---

## Output Screenshots

**[Screenshots from AFLogical extraction process would be embedded here]**

### Screenshot 1: Java Version Verification
*Screenshot of terminal showing `java -version` output*

### Screenshot 2: ADB Devices Connection
*Screenshot showing `adb devices` listing connected Android device*

### Screenshot 3: AFLogical Installation
*Screenshot showing successful APK installation via ADB*

### Screenshot 4: AFLogical Main Interface
*Screenshot of AFLogical application on Android device showing extraction options*

### Screenshot 5: Data Selection
*Screenshot showing selected checkboxes for Contacts, SMS, MMS, Call Logs*

### Screenshot 6: Extraction In Progress
*Screenshot showing extraction status/progress indicator*

### Screenshot 7: Files Extracted to Computer
*Screenshot of Windows Explorer showing aflogical folder with CSV files*

### Screenshot 8: CSV Files in Destination Directory
*Screenshot showing contacts.csv, sms.csv, mms.csv, call_logs.csv files*

### Screenshot 9: Contacts CSV in Excel
*Screenshot of contacts.csv opened in Excel showing contact data*

### Screenshot 10: SMS CSV in Excel
*Screenshot of sms.csv opened in Excel showing message data*

### Screenshot 11: Call Logs CSV in Excel
*Screenshot of call_logs.csv opened in Excel showing call data*

---

## References

- AFLogical OSE GitHub Repository
- Android Debug Bridge (ADB) Documentation
- NIST Mobile Device Forensics Guide
- Android Forensics Best Practices

---

**Lab Status:** Complete — Ready for screenshots of AFLogical extraction outputs
