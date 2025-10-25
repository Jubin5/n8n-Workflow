# 🏨 Hotel Review Sentiment Analysis Workflow (n8n + Gemini + Google Sheets)

This project is an **automated sentiment analysis workflow** built in **n8n**, designed to help hotel owners analyze customer feedback in real-time.  
The workflow uses **Google Gemini** (via an LLM Chain) to classify reviews as **Positive**, **Neutral**, or **Negative**, notifies the hotel owner via **email**, and logs all data into **Google Sheets** with timestamps.

---

## 🚀 Overview

Customer reviews are crucial for understanding service quality and customer satisfaction.  
This workflow automates the entire process of analyzing customer feedback, reducing manual work and ensuring timely insights for the hotel management team.

**Main functions:**
1. Collect customer reviews through a submission form.
2. Process the review using a **Gemini Chat Model** (LLM Chain) to analyze the sentiment.
3. Email the hotel owner about the review and its detected sentiment.
4. Merge workflow branches using a **Merge Node** for unified processing.
5. Record each review and its sentiment in a **Google Sheet** using the Google Sheets API.
6. Store a **timestamp** for every new review entry.

---

## 🧩 Workflow Architecture

The workflow consists of the following key nodes:

| Node | Function |
|------|-----------|
| **Form Trigger Node** | Captures incoming hotel customer reviews. |
| **LLM Chain (Gemini Chat Model)** | Processes the review text and determines sentiment (Positive / Neutral / Negative). |
| **Email Node** | Sends an automated email to the hotel owner summarizing the review and sentiment. |
| **Merge Node** | Merges all branches of the workflow before final data logging. |
| **Google Sheets Node (via API)** | Records each review, sentiment, and timestamp in a connected Google Sheet for tracking. |

---

## ⚙️ Technologies Used

- **n8n** (Workflow Automation Platform)  
- **Google Gemini Chat Model** (via LLM Chain integration)  
- **Google Sheets API**  
- **Email API (SMTP / Gmail)**
- **Google Cloud Console**

---

## 📊 Data Logged in Google Sheets

Each new review entry in the Google Sheet includes the following fields:

| Column | Description |
|---------|--------------|
| **Timestamp** | Date and time when the review was processed. |
| **Customer Review** | The review text submitted by the customer. |
| **Sentiment** | Output from Gemini model: Positive / Neutral / Negative. |
| **Email Sent** | Confirmation that notification was sent to the hotel owner. |

---

## 📬 Email Notification Format

When a new review is processed, the hotel owner receives an email like:

> **Subject:** New Customer Review Received  
> **Body:**  
> Hello,  
>  
> A new review has been submitted by a guest:  
> _"The room was clean and the staff were very helpful."_  
>  
> **Detected Sentiment:** Positive ✅  
>  
> This review has been logged in your Google Sheet dashboard.  

---

## 🧠 Workflow Logic (Simplified)

```plaintext
Form Submission → Gemini LLM Chain (Sentiment Analysis)
               ↘→ Email Node (Notify Hotel Owner)
                 ↘→ Merge Node → Google Sheets (Record Data)
