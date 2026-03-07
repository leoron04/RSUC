# PARALLAX NERVE — Roadmap

## Vision

PARALLAX NERVE is a portable tactical node (pocket cyberdeck) running a custom Linux environment. It acts as a personal assistant for network analysis, authorized defensive auditing, and digital environment monitoring.

**Core Architecture**: Agentic (local LLM + Tool Calling). The user interacts in natural language; the AI agent translates intent, orchestrates system tools, collects raw output, interprets it, and returns a contextualized synthetic report.

**Constraints**:
- 100% Local Execution (Ollama / llama.cpp, no cloud APIs)
- Security & Guardrails (pre-approved wrapper scripts only, no free shell access)
- Limited Resources (RAM optimization, thermal management, battery-powered edge hardware)

---

## Phase 1 — The Brain: Agent Cognitive Loop

Build the core **Perceive → Reason → Act → Synthesize** cycle:

- Select and optimize a quantized SLM (e.g. Q4_K_M) for the target hardware
- Implement the core agentic loop: user intent parsing, tool selection via function calling, execution, output collection, response generation
- Define the local Tool Calling protocol (JSON schema describing available tools, their parameters, and security constraints)

## Phase 2 — The Hands: Tool Sandbox & Secure Wrappers

Create the controlled execution layer between the agent and the OS:

- Define the Tool Registry: declarative catalog of every authorized tool (Nmap, Airodump-ng, Kismet, tcpdump, etc.) with allowed parameters and execution limits
- Implement wrapper scripts with input validation, timeouts, resource limits (cgroups/namespaces), and output sanitization
- Guardrails layer: command whitelist, rate limiting, kill switch, immutable action logging

## Phase 3 — The Senses: Sensor Integration & Passive Monitoring

Connect the agent to the device's "sensors" for digital environment perception:

- Wi-Fi interface integration in monitor mode (passive spectrum scanning)
- Optional SDR (Software Defined Radio) integration for broader RF monitoring
- Data ingestion pipeline: sensors produce raw data → wrappers pre-process → agent interprets and correlates

## Phase 4 — The Face: User Interface & Edge Resource Management

Make the system usable and sustainable on portable hardware:

- Minimal user interface (TUI or local micro-web) for natural language interaction
- Resource Manager: temperature monitoring, dynamic background process management, intelligent scheduling of heavy tasks (e.g. scans) to prevent overheating
- Operational profiles (e.g. "stealth/low-power" vs "full-scan") that the agent can autonomously select based on context
