<div align="center">

<img src="assets/banner.svg" alt="WhatsApp AI Sales & Order Agent" width="100%"/>

<br/>

<img src="https://img.shields.io/badge/n8n-EA4B71?style=for-the-badge&logo=n8n&logoColor=white" alt="n8n"/> <img src="https://img.shields.io/badge/OpenAI-412991?style=for-the-badge&logo=openai&logoColor=white" alt="OpenAI"/> <img src="https://img.shields.io/badge/WhatsApp%20API-25D366?style=for-the-badge&logo=whatsapp&logoColor=white" alt="WhatsApp API"/> <img src="https://img.shields.io/badge/Supabase-3FCF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase"/> <img src="https://img.shields.io/badge/Google%20Sheets-34A853?style=for-the-badge&logo=googlesheets&logoColor=white" alt="Google Sheets"/>

<br/>

<img src="https://img.shields.io/badge/n8n%20nodes-34-EA4B71?style=flat-square" alt="nodes"/>
<img src="https://img.shields.io/badge/Status-Delivered%20to%20client-success?style=flat-square" alt="status"/>
<img src="https://img.shields.io/badge/Workflow-Private%20(client%20project)-lightgrey?style=flat-square" alt="source"/>

**[Get this built for your business](https://www.fiverr.com/faizan_develope) · [Rootocloud](https://rootocloud.com) · [More projects](https://github.com/MuhammadFaizan73)**

</div>

---

## 📌 Overview

Two connected workflows that digitise a distributor's field-sales process. Every evening the broadcaster messages each shop about the next salesman visit; the reply handler then runs an AI sales conversation on WhatsApp — reading the product list, answering questions, taking orders, sending the PDF catalog and confirming or cancelling orders.

## ✨ What It Does

- Scheduled broadcast to every shop from a Google Sheet, rate-limited
- Session state seeded per shop (awaiting confirmation)
- AI smart router reads the live product list and decides the next action
- Orders saved to Google Sheets and emailed to the sales team
- PDF catalog sent on request
- Visit confirmation / denial tracking and live-agent mode

## 📈 Business Impact

Shops can confirm visits and place orders without a phone call, and the sales team receives clean, structured orders every day.

## 🔀 How It Works

The diagram below is generated directly from the production n8n workflow.

### Workflow: Salesman Visit Broadcaster — 10 nodes

```mermaid
flowchart TD
  n0(["⏰ Daily 6 PM Trigger"])
  n1(["▶️ Manual Trigger (Test)"])
  n2["📋 Read Shops Sheet"]
  n3["🧹 Prepare Recipients"]
  n4["🔁 Loop Each Shop"]
  n5["✍️ Compose Message"]
  n6["📤 Send WhatsApp"]
  n7["🧠 Seed Session"]
  n8["💾 Save Session (awaiting_confirmation)"]
  n9["⏳ Rate Limit (2s)"]
  n0 --> n2
  n1 --> n2
  n2 --> n3
  n3 --> n4
  n4 --> n5
  n5 --> n6
  n6 --> n7
  n7 --> n8
  n8 --> n9
  n9 --> n4
```

### Workflow: Salesman Reply Handler — 24 nodes

```mermaid
flowchart TD
  n0(["📱 WhatsApp Webhook"])
  n1["✅ Respond to Webhook"]
  n2["📋 Extract Message"]
  n3["🗄️ Load Session"]
  n4["🌉 Parse Session State"]
  n5{"🔀 Live Agent?"}
  n6["📝 Save User Only (Live Agent)"]
  n7["💾 Save (Live Agent)"]
  n8["📦 Read Products"]
  n9["🧺 Bundle Products + Session"]
  n10["🧠 Smart Router (AI)"]
  n11["📝 Update History"]
  n12["💾 Save Session"]
  n13["📤 Send WhatsApp Reply"]
  n14["📦 Prepare Order Row"]
  n15["📊 Save Order to Sheet"]
  n16["📧 Format Order Email"]
  n17["📨 Email Order to Team"]
  n18["📤 Send Order Confirmation"]
  n19["📋 Mark Confirmed"]
  n20["📋 Mark Denied"]
  n21{"🔀 If save_order"}
  n22{"🔀 If mark_confirmed"}
  n23{"🔀 If mark_denied"}
  n0 --> n1
  n0 --> n2
  n2 --> n3
  n3 --> n4
  n4 --> n5
  n5 --> n6
  n5 --> n8
  n6 --> n7
  n8 --> n9
  n9 --> n10
  n10 --> n11
  n11 --> n12
  n12 --> n13
  n13 --> n21
  n13 --> n22
  n13 --> n23
  n14 --> n15
  n15 --> n16
  n16 --> n17
  n17 --> n18
  n21 --> n14
  n22 --> n19
  n23 --> n20
```

<!-- SCREENSHOTS -->
<!-- /SCREENSHOTS -->

## 🔒 About the Workflow File

This automation was built for a client, so the n8n workflow JSON (with prompts, credentials and business logic) is kept private.
**I can build a version tailored to your business** — [contact me on Fiverr](https://www.fiverr.com/faizan_develope) or [email](mailto:faizan.developer9200@gmail.com).

## 👨‍💻 Author

**Muhammad Faizan** — Founder, [Rootocloud](https://rootocloud.com) · n8n & AI Automation Specialist (8+ years)

[![Website](https://img.shields.io/badge/rootocloud.com-0B1220?style=for-the-badge&logo=googlechrome&logoColor=white)](https://rootocloud.com)
[![Fiverr](https://img.shields.io/badge/Fiverr-1DBF73?style=for-the-badge&logo=fiverr&logoColor=white)](https://www.fiverr.com/faizan_develope)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/muhammad-faizan-b7062b7a/)

<div align="center"><sub>© Muhammad Faizan. All rights reserved.</sub></div>
