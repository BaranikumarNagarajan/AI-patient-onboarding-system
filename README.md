# **AI Patient Onboarding System (Text + Voice)**

### *Fully Autonomous Healthcare Registration Workflow using n8n, Groq LLaMA-3 & Whisper*

This repository contains a complete **AI-powered patient intake workflow** capable of processing **both text messages and voice notes** through Telegram.
The system uses **Whisper** for speech-to-text conversion and **Groq LLaMA-3** for intelligent reasoning, intent detection, and structured data extraction — all orchestrated through **n8n**.

The workflow creates clean patient records, stores them in Google Sheets, generates a clinical email summary, and sends a confirmation message back to the patient.
Everything runs fully automatically in **1.5–2.5 seconds**.

---

## ⭐ **Features**

### **1. Unified Text + Voice Flow**

* Detects whether incoming input is text or voice
* Voice messages → converted to text using Whisper
* Text messages → processed directly
* Both flows follow the same AI processing pipeline

### **2. Whisper Speech-to-Text (via Groq)**

* High-accuracy transcription
* Supports natural speech, accents, medical terms
* < 400ms transcription latency

### **3. Groq LLaMA-3 AI Processing**

* Detects intent (registration / query)
* Maintains multi-turn conversation memory
* Extracts structured fields:

  * Name
  * Age
  * Phone
  * Email
  * Gender
  * Location
  * Symptoms
  * Appointment date/time (if mentioned)
  * IST timestamp

### **4. Standardize Patient Data Layer**

* Normalizes phone numbers
* Cleans age format
* Fixes inconsistent field values
* Produces clean JSON for storage

### **5. Google Sheets EMR Backend**

* Appends patient record automatically
* Prevents duplicates
* Creates clean data rows ready for EMR or analytics

### **6. Automated Clinical Email Summary**

* Generates a structured patient report
* Sends to admin/clinic inbox
* No manual typing required

### **7. Telegram Confirmation**

* Sends automated “Registration Successful” message
* Works for text and voice registration

---

## ⚡ **Performance**

| Component              | Speed      |
| ---------------------- | ---------- |
| Whisper Transcription  | ~350–400ms |
| Groq LLaMA-3 Reasoning | <150ms     |
| Total Workflow Time    | 1.5–2.5s   |

This system is optimized for **real-time clinical onboarding**.

---

## 📐 **Architecture**

```
Telegram Input (Text / Voice)
        │
        ├── Text → Groq LLaMA-3
        │
        └── Voice → Whisper → Clean Text → Groq LLaMA-3
                    │
            Standardize Patient Data (JS)
                    │
            Google Sheets (EMR)
                    │
          Clinical Email Summary
                    │
          Telegram Confirmation
```

---

## 🧩 **Technology Stack**

* **n8n** (workflow automation)
* **Groq LLaMA-3** (LLM reasoning + intent + extraction)
* **Whisper** (speech-to-text)
* **Telegram Bot API**
* **Google Sheets API**
* **JavaScript Nodes (n8n)**

---

## 📌 **Setup Instructions**

### 1. Clone the repo

```
git clone https://github.com/<your-username>/AI-patient-onboarding-system.git
```

### 2. Install n8n

```
npm install n8n -g
```

### 3. Configure Environment Variables

Create `.env` and add:

```
GROQ_API_KEY=
TELEGRAM_BOT_TOKEN=
GOOGLE_SERVICE_ACCOUNT_JSON=
EMAIL_SMTP_USER=
EMAIL_SMTP_PASS=
```

### 4. Import Workflow

Go to n8n → Import → select the workflow JSON from `/workflow`.

### 5. Start n8n

```
n8n start
```

---

## 📄 **Project Files**

* `/workflow/` → n8n JSON workflow
* `/docs/` → architecture diagrams, data flow charts
* `/examples/` → sample inputs/outputs

---

## 🧪 **Sample Output**

```json
{
  "name": "Priya Dharshini",
  "age": 28,
  "phone": "9876543210",
  "email": "example@mail.com",
  "gender": "Female",
  "symptoms": "fever, throat pain",
  "location": "Trichy",
  "appointment": "Tomorrow 10 AM",
  "timestamp": "2025-11-28T18:41:22+05:30"
}
```

---

## 🤝 **Contributing**

Pull requests are welcome. For major changes, open an issue to discuss what you’d like to improve.

---

## 📬 **Contact**

For collaborations or enhancements:
**[https://www.linkedin.com/in/baranikumarnagarajan](https://www.linkedin.com/in/baranikumarnagarajan)**

---
<img width="1592" height="430" alt="n8n linked" src="https://github.com/user-attachments/assets/fc56f39a-7922-48cc-a870-39e73d515fbd" />
<img width="1735" height="610" alt="n8n link" src="https://github.com/user-attachments/assets/127605b5-223c-4bd0-b111-287cf33de2d2" />


