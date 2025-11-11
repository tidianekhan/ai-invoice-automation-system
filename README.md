# Intelligent Invoice Automation (Power Automate + AI Builder)

This project automates invoice handling using **Microsoft Power Automate**, **AI Builder**, and **Excel Online**.  
The flow processes invoice emails, extracts key data, prevents duplicate processing, and routes each invoice based on AI confidence.

---

## 🧩 Overview

When an email with attachments arrives, the flow automatically:
1. Extracts invoice data (e.g., vendor name, invoice number) using **AI Builder**.
2. Generates a **Unique Key** (Vendor + Invoice Number) for duplicate detection.
3. Checks both the **Processed Invoices** and **Review/Exceptions** tables to avoid reprocessing.
4. Uses confidence thresholds to decide:
   - **≥ 0.85:** Auto-process and log in *Processed Invoices*  
   - **0.70–0.85:** Send for manual review with attachment  
   - **< 0.70:** Log as failed extraction
5. Sends a summary email per attachment (success, review required, or failure).

---

## ⚙️ Tech Stack

| Component | Description |
|------------|-------------|
| **Microsoft Power Automate** | Main workflow engine |
| **AI Builder (Form Processing)** | Extracts invoice details |
| **Excel Online (Business)** | Stores processed, review, and duplicate logs |
| **Outlook** | Trigger and email notifications |

---

## 📄 Flow Logic Diagram
*(See included image: `flow-diagram.png`)*

---

## 📧 Example Notifications

- **Success Email:** Confirms correct processing and updates the main invoice log.  
- **Review Email:** Sent for invoices with medium confidence; includes attachment and extraction details.  
- **Failure Log:** Records low-confidence or unreadable invoices for auditing.

---

## 🧠 Key Features
- Duplicate detection across multiple data tables  
- Confidence-based decision branching  
- AI-powered data extraction and normalization  
- Structured exception handling and logging  
- Email summaries for traceability

---

## 🧾 Example Output (Excel)
| Vendor Name | Confidence | Status | Invoice Email | Unique Key |
|--------------|-------------|--------|----------------|-------------|
| Vendor A | 0.94 | Processed | vendorA@invoices.com | VendorA_INV12345 |
| Vendor B | 0.79 | For Review | vendorB@invoices.com | VendorB_INV54210 |
| Vendor C | 0.65 | Failed | vendorC@invoices.com | VendorC_INV90021 |

*(All vendor names and email addresses are fictional for demonstration.)*

---

## 🚀 Setup Instructions
1. Export or recreate the flow in Power Automate.  
2. Connect:
   - **Outlook (V3)** for email triggers  
   - **AI Builder model** for invoice extraction  
   - **Excel Online (Business)** for data tables  
3. Update table references to your files:
   - `Processed Invoices`
   - `Invoices For Review + Exceptions`
4. Adjust confidence thresholds if needed in the condition steps.

---

## 🧩 Possible Improvements
- Add auto-archiving for processed attachments.  
- Log failed extractions to SharePoint for audit trail.  
- Integrate with Power BI for invoice analytics dashboard.  

---

## 🏷 About
Created to demonstrate intelligent document automation with Microsoft’s Power Platform.  
This project highlights AI-assisted workflow design, exception handling, and business logic orchestration.
