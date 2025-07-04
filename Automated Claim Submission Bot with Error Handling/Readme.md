# 🏥 Automated Claim Submission Bot with Error Handling

This RPA project uses **UiPath** to automate the end-to-end submission of **medical claims** (CMS-1500 or UB-04) into payer portals or clearinghouses. The bot extracts relevant claim data from structured forms, inputs them into web-based systems, and incorporates error-handling mechanisms to ensure reliability and accuracy.

---

## 📌 Objective

To streamline and automate the repetitive process of submitting healthcare claims, thereby:
- Reducing manual entry effort
- Minimizing submission errors
- Accelerating the claims lifecycle
- Enabling focus on higher-value tasks like denial management

---

## 🩺 Use Case

In healthcare Revenue Cycle Management (RCM), submitting claims via portals or clearinghouses is time-intensive and prone to human error. This bot simplifies the workflow and ensures high efficiency with validation and retry logic.

---

## 🛠️ Tools & Technologies

| Component            | Description                                         |
|----------------------|-----------------------------------------------------|
| **UiPath Studio**     | RPA development and automation                     |
| **Document Understanding** | Extract fields from CMS-1500/UB-04 forms         |
| **Excel Activities**   | Read/write claim data if required                 |
| **Web Automation**     | Interact with payer portals using selectors        |
| **Outlook/SMTP**       | Send notifications after submission               |
| **RE Framework**       | (Optional) For scalable, robust bot architecture   |
| **n8n (Optional)**     | For alerts, escalation routing, webhook triggers   |

---

## 🔁 Workflow Overview

### 🧾 Input:
- Folder of CMS-1500 or UB-04 claim PDFs
- (Optional) Excel file with extracted claim data

### 🤖 Bot Logic:

1. **Document Intake**
   - Monitors a folder or email inbox
   - Validates document type (CMS-1500 / UB-04)

2. **Data Extraction**
   - Uses **Document Understanding / Regex** to extract:
     - Patient Details
     - Provider Info
     - Procedure Codes
     - Charges
     - Diagnosis Codes

3. **Web Submission**
   - Logs in to payer portal / clearinghouse
   - Inputs extracted data into relevant fields
   - Takes screenshots or saves confirmation numbers

4. **Error Handling**
   - Retries in case of portal errors
   - Logs issues to Excel or Orchestrator queue
   - Sends failure report to billing team

5. **Post-Submission Notification**
   - Sends summary report (claims submitted, failed, duplicates) via email or Slack

---

## 📁 Folder Structure

📁 ClaimSubmissionBot/
│
├── 📁 InputClaims/ # CMS-1500 or UB-04 PDFs
├── 📁 ExtractedData/ # Optional Excel-based input/output
├── 📁 Screenshots/ # Submission proof (confirmation numbers)
├── 📁 Logs/
│ └── SubmissionErrors.xlsx
├── 📁 Project/
│ ├── Main.xaml
│ └── Config.xlsx
├── README.md



---

## 🧠 Key Features

- ✅ AI-powered or template-based field extraction
- ✅ Automatic login and portal navigation
- ✅ Dynamic selector handling
- ✅ Retry on failure with limited attempts
- ✅ Notification of submission status
- ✅ Modular and RE Framework compatible

---

## 🚀 How to Run

1. Open `Main.xaml` in **UiPath Studio**
2. Update `Config.xlsx` with:
   - Portal URLs
   - Credentials (use Orchestrator Assets for security)
   - File paths
3. Place CMS-1500 or UB-04 forms in `InputClaims/`
4. Run the bot manually or via Orchestrator
5. Check output logs and screenshots in respective folders

---

## 📊 Output Sample

| Claim ID | Patient Name | Status   | Portal Reference | Error Message        |
|----------|--------------|----------|------------------|----------------------|
| 12345    | John Smith   | Success  | REF-987654       | N/A                  |
| 12346    | Jane Doe     | Failed   | N/A              | Invalid CPT Code     |

---

## 🔒 Compliance Note

This automation should be configured to operate in accordance with **HIPAA** regulations. Sensitive data must be encrypted and handled securely using **Orchestrator assets**, **secure credential stores**, and **controlled access**.

---

## 📌 Enhancements (Optional)

- Add **n8n integration** for:
  - Real-time Slack/MS Teams notifications
  - Routing failures to support queues
- Use **AI Center / AI Fabric** to classify claim forms
- Connect to **FHIR APIs** for real-time eligibility checks before submission

---

## 👤 Author

**Dilip Kumar M**  
RPA Developer | Healthcare Automation Specialist  
📧 [reignsdilip77@gmail.com](mailto:reignsdilip77@gmail.com)

---

## 📄 License

This project is open for personal learning and demonstration. Not for production use without appropriate security and compliance checks.
