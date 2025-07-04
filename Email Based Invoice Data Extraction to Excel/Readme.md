# 📨 Email-Based Invoice Data Extraction to Excel

An RPA project built using **UiPath** to automate the extraction of invoice data from PDF attachments received via email and store it in a structured **Excel report** for further billing or reconciliation purposes.

---

## 📌 Project Objective

The primary goal of this project is to eliminate manual data entry from invoices by:
- Automatically fetching invoice emails from a shared inbox
- Downloading PDF attachments
- Extracting invoice details using UiPath's Document Understanding
- Writing structured data to an Excel sheet
- Sending daily summary reports to the billing team

---

## 🎯 Use Case

Healthcare billing and RCM teams often receive a high volume of invoice documents from payers or vendors. Manual entry is time-consuming and error-prone. This bot streamlines the process and ensures accuracy and consistency.

---

## 🛠️ Tools & Technologies

| Tool            | Purpose                              |
|-----------------|--------------------------------------|
| UiPath Studio   | RPA development platform             |
| UiPath RE Framework *(optional)* | Reliable bot structure with retry logic |
| Outlook Activities | For reading and downloading emails |
| Document Understanding | To extract fields from invoices |
| Excel Activities | To write and update structured data |
| (Optional) UiPath Orchestrator | For scheduling and monitoring |

---

## 🧩 Key Components

### 1. **Email Fetching**
- Reads unread emails with subject keywords like `Invoice` or `Payment`
- Downloads PDF attachments to a temporary folder

### 2. **Document Processing**
- Uses **Document Understanding** or **Regex-based extraction** for:
  - Invoice Number
  - Date
  - Payer Name
  - Amount
  - Due Date

### 3. **Excel Report Creation**
- Appends each invoice record to an Excel sheet
- Checks for duplicates using invoice number

### 4. **Summary Email (Optional)**
- Sends a daily email with summary:
  - Total Invoices Processed
  - Errors Encountered
  - Link to Excel report

---

## 📁 Folder Structure

📁 InvoiceExtractorBot/
│
├── 📁 InputMails/
├── 📁 Invoices/
├── 📁 ExtractedData/
│ └── Invoice_Report.xlsx
├── 📁 Project/
│ ├── Main.xaml
│ └── Config.xlsx
├── README.md



---

## ✅ Prerequisites

- UiPath Studio (Community or Enterprise Edition)
- Outlook account with access to target inbox
- Sample invoice PDFs
- (Optional) API key for AI-based Document Understanding models

---

## 🚀 How to Run

1. Open `Main.xaml` in UiPath Studio
2. Update email filter keywords and folder paths in `Config.xlsx`
3. Train Document Understanding (DU) model if using AI-based extraction
4. Run the bot (manual or orchestrator trigger)
5. Check output in `ExtractedData/Invoice_Report.xlsx`

---

## 📊 Sample Output (Excel)

| Invoice Number | Date       | Payer         | Amount | Due Date   |
|----------------|------------|---------------|--------|------------|
| INV-2025-001   | 2025-07-01 | ABC Insurance | $450   | 2025-07-15 |
| INV-2025-002   | 2025-07-02 | XYZ Payer     | $600   | 2025-07-20 |

---

## 📌 Challenges Addressed

- Manual effort in data entry
- Human errors in invoice fields
- Delay in billing reconciliation
- Duplicate entry prevention

---

## 🧠 What You’ll Learn

- Email automation with UiPath Outlook activities
- PDF handling and data extraction
- Document Understanding basics
- Excel operations with structured data
- Logging and exception handling

---

## 📌 Potential Enhancements

- Add **n8n** for:
  - Slack/MS Teams notifications
  - Trigger downstream workflows (e.g., reconciliation)
- Add **Power BI** for visualizing extracted invoice data
- Enable **Orchestrator Queues** for better scalability
- Apply **AI-based invoice classification** for mixed document batches

---

## 👤 Author

**Dilip Kumar M**  
RPA Developer | UiPath | Healthcare RCM Automation  
📧 [reignsdilip77@gmail.com](mailto:reignsdilip77@gmail.com)

---

## 🏁 License

This project is open for educational and demonstration purposes. Please review compliance rules before using in production, especially for PHI or HIPAA-sensitive data.
