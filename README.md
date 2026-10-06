# ORION (Omnipresent Resourceful Intelligent Operational Network)

## 1. Project Overview
ORION is a custom, autonomous AI assistant operating on a Hub-and-Spoke architecture. It consists of a central "Brain" (FastAPI backend) and a Holographic Command HUD (Next.js frontend). 

**Role of the AI Developer (Jules):** 
You are the Senior Engineer. You will receive tasks via GitHub Issues. You must strictly adhere to the architectural and aesthetic guidelines in this document.

---

## 2. Core Architecture & Tech Stack
*   **Backend:** Python 3.11+ using FastAPI.
*   **Frontend:** Next.js (React) using Tailwind CSS and React Three Fiber (R3F).
*   **Communication:** REST APIs for standard calls, WebSockets for real-time streaming.

### 2.1 The Backend (ReAct Loop & Dynamic Tools)
ORION must use a ReAct (Reasoning + Acting) cognitive loop.
1. **Thought:** The LLM analyzes the prompt against its tools.
2. **Action:** The LLM outputs structured JSON to call a tool.
3. **Observation:** The system executes the Python tool and feeds the result back.
4. **Output:** The LLM generates the final response.

**Dynamic State:** The system must dynamically load tools from the `/backend/tools` directory and inject their definitions and the current system time into every LLM request.

### 2.2 The Frontend (Holographic Command HUD)
The UI must NOT resemble a standard web app or chat interface. It is a borderless, cinematic HUD.
* **Aesthetic:** Deep obsidian background (`#050505`) with a subtle grid. NO opaque container boxes, solid backgrounds, or rounded chat bubbles. Use minimalist monospace typography (e.g., Geist Mono).
* **The Core (Center):** A 3D React Three Fiber avatar (a "Vector Iris" of concentric, rotating geometric rings) that serves as the visual heartbeat.
* **Dual Telemetry Streams:** 
  * *Bottom-Left (Terminal Uplink):* Borderless text stream of the user/ORION dialogue.
  * *Bottom-Right (Subsystem Stream):* Borderless text stream of ORION's internal ReAct logs (Thoughts, Actions, Latency).
* **System Header:** A minimalist top bar showing real data: Local Time, Backend Status, Latency, and Active Tool count.

---

## 3. Capability Expansion Protocol (Self-Extending)
ORION does not dynamically write its own Python files at runtime. It expands capabilities via GitHub Issues.
1. **Identify Missing Capability:** When asked for a task lacking a local tool, ORION acknowledges the limitation.
2. **Offer Feature Request:** ORION asks: *"I lack that capability. Shall I dispatch a request to Jules?"*
3. **Dispatch:** If approved, ORION executes a `create_github_issue` tool to draft a detailed PR request.
4. **Implementation:** Jules picks up the issue, writes the code, and submits a PR.
