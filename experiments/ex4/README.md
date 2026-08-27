# Ex. 4: Analyze Email Headers & Detect Email Spoofing (MHA)

**Lab:** Digital Forensics | **Tool:** Mail Header Analyzer (MHA)

## Quick Reference
- **Objective:** Analyze email headers to detect spoofing/phishing
- **Key Tools:** WHOIS, MXToolbox, G Suite Toolbox
- **Authentication Checks:** SPF, DKIM, DMARC

## Step-by-Step Process

### 1. Access Email Header
| Client | Steps |
|--------|-------|
| **Gmail** | Email → ⋯ (More) → "Show original" |
| **Outlook** | File → Properties → "Internet headers" |
| **Yahoo** | ⋯ (More) → "View raw message" |

### 2. Key Header Fields to Extract
- **From:** Sender's email address
- **To:** Recipient's email address
- **Date:** Timestamp of email
- **Subject:** Email subject
- **Return-Path:** Bounce address
- **Received:** Email path (reverse-ordered servers)
- **Message-ID:** Unique identifier
- **SPF/DKIM/DMARC:** Authentication results

### 3. Critical Analysis Points

#### Received Field Analysis
Trace email path from last server (recipient) to first (sender):
- Check hostname/IP authenticity
- Verify time progression (no backward times)
- Use WHOIS for IP geolocation & ASN verification

#### Authentication Checks
| Protocol | Pass | Fail |
|----------|------|------|
| **SPF** | IP authorized for domain | Possible spoofing |
| **DKIM** | Content unaltered | Potential tampering |
| **DMARC** | SPF/DKIM aligned | Spoofing/tampering |

#### Red Flags
- ⚠️ Domain mismatch (From vs Return-Path vs Message-ID)
- ⚠️ Suspicious IP addresses (check geolocation)
- ⚠️ SPF/DKIM/DMARC failures
- ⚠️ Time discrepancies in Received lines
- ⚠️ Unexpected server hops

### 4. Online Analysis Tools
- **MXToolbox:** Email authentication verification
- **Google G Suite Toolbox:** Header parser & SPF/DKIM checker
- **AbuseIPDB:** Check IP reputation

### 5. Documentation
- Record all suspicious findings
- Screenshot authentication results
- Report to IT/email provider

---
**Result:** Email authenticity verified | Spoofing detected (if applicable)
