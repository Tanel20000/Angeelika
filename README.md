# Angeelika — AI-Powered Phone Security (Proof of Concept)

## Overview
Angeelika is a functional prototype exploring how artificial intelligence can identify fraudulent phone conversations in real-time, providing an automated layer of defense for individuals vulnerable to telephone scams (vishing). 

The project bridges the gap between legacy telephony infrastructure (VoIP/SIP) and modern Large Language Models (LLMs) to create an active-response security system.

---

## 💡 The Engineering Context (The €19 / AI Challenge)
This project is an agile **Proof of Concept (PoC)** built entirely from scratch within my **first two months** of studying Information Security. 

* **The Force Multiplier:** Developed using a **"Human + AI" co-pilot paradigm**. Instead of letting AI write passive code, I acted as the systems architect—leveraging AI to rapidly accelerate my learning curve, bridge programming gaps, and debug complex low-level networking in days rather than months.
* **The €19 Budget:** Built with a total material cost of roughly **€19**, utilizing open-source infrastructure (Asterisk, Linux) and ultra-fast, cost-effective APIs. It proves that production-level security logic doesn't require enterprise budgets—only resourceful engineering.

---

## 🛠️ Key Architectural Innovations
Unlike passive analytics tools that process data *after* a security breach occurs, Angeelika is designed around **Active Response** principles:

* **Low-Latency Streaming (AudioSocket):** Audio is streamed live via a local loopback port (`127.0.0.1:4010`) directly into the Python application layer. It completely bypasses slow file-writing methods to ensure real-time analysis.
* **Asynchronous Orchestration (`angeelika_ws.py`):** Uses the Asterisk REST Interface (ARI) and WebSockets to handle ongoing call states, manipulate ringing tones, and control channels dynamically.
* **Sub-Second Transcription:** Integrates **Groq Whisper (whisper-large-v3)** specifically optimized for the Estonian language, achieving the extreme text-generation speeds required to intercept a live scammer.
* **Automated Threat Mitigation (Active Tear-down):** If the AI risk assessment engine returns a `HIGH` threat level based on specific conversational risk indicators, the ARI application instantly drops the call channels to protect the target.

---

## ⚙️ Technology Stack
* **Languages & Automation:** Python (`angeelika_ws.py`), Bash scripting
* **Telephony & Infrastructure:** Ubuntu Server, Asterisk PBX, PJSIP stack, WaveCom SIP trunking, Groundwire softphone
* **AI & Speech Processing:** Groq API (Whisper-large-v3 for Estonian transcription), LLM API for real-time risk assessment
* **Alerting & Diagnostics:** Telegram Bot API (delivering immediate logs, context, and proof of threat)

---

## 📊 Prototype Workflow & Decision Tree
1. **Ingress:** An inbound call hits the WaveCom SIP trunk and routes to Asterisk PBX.
2. **Interception:** The ARI application captures the call, controls the ringtone, and opens an AudioSocket stream upon pickup.
3. **Processing:** The stream is piped to Groq Whisper for instant Estonian transcription.
4. **Analysis:** The LLM evaluates risk patterns (e.g., requests for PIN codes, banking phrases, urgency tactics).
5. **Mitigation Tree:**
   * **LOW Risk:** Monitoring continues; call proceeds uninterrupted.
   * **HIGH Risk:** The ARI app executes an active tear-down, severing the call channels instantly. Logs are dumped, and a Telegram report containing the *risk, reason, and evidence* is dispatched.

---

## 🔒 Security, Scope & Disclaimer
* **Design Philosophy:** As an experimental PoC, this codebase deliberately optimizes for speed and architectural validation. Production considerations—such as local LLM deployment for strict data privacy, enterprise-grade encryption, and failover handling—are scoped for the next phase of development.
* **Repository Content:** This public repository serves as a conceptual and architectural blueprint. Credentials, API keys, private configurations, call logs, and internal mitigation logic are strictly excluded.

---

## 📩 Contact
For collaboration, academic inquiries, or to discuss the architecture further, please contact the repository author.
