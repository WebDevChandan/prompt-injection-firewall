# Agentic Prompt Injection Firewall 🛡️

**ET AI Hackathon: Agentic Edition | Problem Statement 2**

An intelligent, LLM-powered middleware firewall designed to intercept, analyze, and neutralize malicious prompt injections before they reach vulnerable downstream AI applications.

## 🎯 Solution Grid Positioning
* **Solution Features (F2):** Successfully detects and categorizes **5 distinct attack vectors**.
* **Solution Depth (D2):** Processes both direct textual input and heterogeneous file ingestion (Markdown, HTML, TXT) with high reliability.

## 🏗️ Structural Architecture

The firewall operates on a dual-agent architecture to ensure strict separation of concerns:

1. **The Interception Layer (Next.js Edge Route):** All user payloads (direct chat or extracted file text) are routed here first.
2. **The Security Agent (Gemini 2.5 Flash - Temp 0.1):** The payload is evaluated against a rigid, deterministic system prompt acting as the firewall rule engine. It returns a structured JSON verdict.
3. **The Target LLM (Vulnerable App):** Only if the Security Agent returns `"threat_detected": false` is the payload forwarded to the target application.
4. **Telemetry Dashboard:** Real-time observability stream logging all interceptions, confidence scores, and threat analysis for human-in-the-loop auditing.

## 🦠 Supported Attack Vectors (F2)
The firewall successfully detects and neutralizes:
1. **Instruction Override:** Attempts to force the AI to ignore previous instructions.
2. **Secret Extraction:** Payloads designed to trick the AI into revealing system prompts or hardcoded credentials.
3. **Role Change:** Jailbreaks forcing the AI into unconstrained personas (e.g., "DAN").
4. **Context Poisoning:** Injection of false facts to manipulate the AI's decision-making logic.
5. **Indirect Prompt Injection:** Hidden malicious directives embedded inside benign-looking user-uploaded files (.txt, .md, .html).

## 🚀 Running Locally
1. Clone the repository
2. Install dependencies: \`npm install\`
3. Create a \`.env.local\` file and add your Gemini API Key: \`GEMINI_API_KEY=your_key_here\`
4. Start the development server: \`npm run dev\`
5. Open \`http://localhost:3000\`