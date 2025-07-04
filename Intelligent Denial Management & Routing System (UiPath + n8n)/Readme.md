# 🧠 Intelligent Denial Management & Routing System (UiPath + n8n)

This is an **advanced RPA + workflow automation project** that integrates **UiPath** and **n8n** to automate the end-to-end process of **claim status checking**, **denial reason extraction**, and **routing to relevant teams** in a healthcare Revenue Cycle Management (RCM) environment.

---

## 🎯 Objective

To build an intelligent system that:
- Automatically checks claim statuses from payer portals or EMRs (like Epic)
- Extracts denial reasons
- Logs outcomes in a database or Excel
- Uses **n8n** to route denied claims to appropriate departments or personnel
- Sends notifications and escalates unresolved cases

---

## 🏥 Problem Statement

In healthcare billing, AR teams spend countless hours manually checking claims and tracking denials. Delays in denial handling lead to lost revenue. This system addresses:

- Late or missed denial follow-ups
- Manual errors in data extraction
- Lack of visibility across denial cases
- Inefficient routing workflows

---

## 🛠️ Tools & Technologies

| Component             | Purpose                                      |
|----------------------|----------------------------------------------|
| **UiPath Studio**     | Core automation platform                     |
| **UiPath Orchestrator** | Bot scheduling, queue handling, assets     |
| **n8n**               | Workflow automation, notifications, routing |
| **Document Understanding** | Extract denial info from PDFs, EOBs      |
| **MySQL / Excel**     | Store claim status data                     |
| **Outlook / Slack / MS Teams** | Notifications and summaries        |
| **REST APIs**         | Integrate UiPath ↔ n8n via webhooks         |

---

## 🔁 Workflow Overview

Trigger (n8n) → UiPath Orchestrator Queue → Payer Portal Automation →
Claim Status Extraction → Denial Reason Parsing →
Result to DB/Excel → n8n Routing Logic → Notify Assigned Teams


### ✔️ Step-by-Step Breakdown

1. **Trigger:**
   - Scheduled run (daily) or webhook from n8n

2. **Claim Lookup (UiPath):**
   - Logs in to EMR or payer portal
   - Searches by claim ID or patient MRN
   - Extracts current claim status

3. **Denial Handling (UiPath):**
   - If denied, extracts denial reason from remittance advice or EOB
   - Stores results in MySQL or Excel
   - Returns output to n8n via webhook

4. **Routing (n8n):**
   - Reads denial code/description
   - Based on rules, assigns to:
     - Coders (e.g., medical necessity denials)
     - Billers (e.g., missing modifier)
     - Compliance (e.g., authorization issues)
   - Sends Slack/email notification
   - Escalates aged denials > 5 days

5. **Summary Dashboard (Optional):**
   - Generates a denial tracker report daily
   - Updates Google Sheet or Power BI dashboard

---

## 📁 Folder Structure

📁 DenialRoutingBot/
│
├── 📁 Input/
│ └── Claim_ID_List.xlsx
├── 📁 Output/
│ ├── Denial_Log.xlsx
│ ├── ProcessedClaims.csv
├── 📁 n8n_Workflows/
│ └── webhook_trigger.json
│
├── 📁 UiPath/
│ ├── Main.xaml
│ ├── Config.xlsx
│ └── Assets.json
├── README.md


---

## 🧠 Key Features

- 🔍 Intelligent denial reason parsing
- 🔄 Bi-directional integration between UiPath & n8n
- 📤 Real-time escalation via Slack/MS Teams
- 🔐 HIPAA-compliant data handling
- 📊 Dashboard-ready reporting

---

## 🚀 How to Run

### 🔧 Pre-requisites:
- UiPath Studio + Orchestrator access
- n8n instance (self-hosted or cloud)
- Valid payer portal credentials
- Sample denial EOBs or PDFs

### ▶️ Execution:
1. Configure claim list in `Claim_ID_List.xlsx`
2. Update `Config.xlsx` and Orchestrator Assets
3. Import n8n workflow and set webhook endpoint
4. Trigger the bot via n8n or Orchestrator schedule
5. Review denial logs and notifications

---

## 📌 Sample Output

| Claim ID | Status   | Denial Reason         | Assigned To | Notified On       |
|----------|----------|------------------------|-------------|-------------------|
| C00123   | Denied   | Procedure not covered  | Coding Team | 2025-07-04 09:30  |
| C00124   | Approved | N/A                    | N/A         | N/A               |

---

## 🔒 Compliance Note

This automation is built with **HIPAA awareness**:
- All patient data is stored securely
- No PHI leaves the environment unless encrypted
- Logs and audit trails are maintained for accountability

---

## 📈 Benefits

- ⏱️ 60–70% reduction in manual denial checks
- 📉 Faster TAT for denied claim reprocessing
- 📬 Real-time communication with relevant teams
- ✅ Higher accuracy, lower revenue leakage

---

## 💡 Future Enhancements

- Integrate with **FHIR APIs** for patient and claim lookup
- Add **AI-based denial reason classification**
- Connect to **ServiceNow / Jira** for ticket-based handling
- Plug in **Power BI dashboard** for denial trends

---

## 👤 Author

**Dilip Kumar M**  
RPA Developer | Healthcare RCM Specialist  
📧 [reignsdilip77@gmail.com](mailto:reignsdilip77@gmail.com)

---

## 📄 License

This project is provided for learning and portfolio purposes. Not intended for production use without appropriate HIPAA compliance and security review.

