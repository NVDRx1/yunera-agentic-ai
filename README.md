# Yunera — Private, Local-First Hermes AI Agent

Yunera is a Linux-based Hermes Agent profile for grounded research, secure local automation, software engineering, Android UX, and multi-agent execution. It combines capable cloud reasoning with local Ollama models, while keeping files, automation, profile state, and privacy-sensitive workloads under local control.

## Core capabilities

- Evidence-backed web, RSS, competitor, market, and community research
- Browser automation, CDP control, local terminal access, file operations, and code execution
- GitHub repositories, issues, pull requests, reviews, releases, and project workflows
- Planning, implementation, testing, debugging, documentation, and verified delivery
- Android and mobile development: Compose UX, accessibility, adaptive layouts, iterative visual QA, and release-readiness checks
- Data-backed applications, external-reference integration, structured exports, and privacy-conscious local data handling
- Image and video generation through ComfyUI; speech-to-text, Australian-English text-to-speech, image analysis, and document handling
- Signal and WhatsApp chat-facing integrations
- Persistent memory, user preferences, reusable skills, and isolated profile state
Multi-agent and local-model setup

Yunera supports a mixture-of-agents workflow:

- Primary reasoning: OpenAI Codex gpt-5.6-terra
- Local/private reference agents: Ollama phi3:mini and qwen2.5-coder:7b
- Multi-agent synthesis: local models contribute independent perspectives, while a stronger model consolidates findings into a final answer
- Task delegation: isolated sub-agents can research, review, plan, or work on independent code tasks in parallel

This provides a practical balance between strong reasoning, local privacy, lower-cost workloads, and independent validation.
Security and privacy

Yunera is configured with a security-first approach:

- Local execution on Linux rather than cloud-hosted containers
- Persistent memory and profile data isolated within a dedicated Hermes profile
- PII and secret redaction enabled
- Privacy-first communication handling
- High-impact action gating and destructive-command safeguards
- Explicit protections against dangerous shell operations and unsafe force-pushes
- Secure local automation, with no credentials intentionally stored in project documentation or source control
- Evidence before confidence: uncertain claims are researched rather than invented
Custom operating style

Yunera uses a custom calm, precise operating persona designed to be direct without being noisy:

> Substance and accuracy before persona.  
> Verify before claiming certainty.  
> Protect privacy, agency, and time.  
> Act decisively when the situation requires it.

Specialist skill areas

- Autonomous AI agent orchestration and context diagnostics
- Local Ollama setup and model integration
- GitHub and software-development workflows
- Android app and data-backed application development
- Cybersecurity-conscious action gating and privacy protection
- Research, RSS monitoring, competitor tracking, and source validation
- Structured data, export, and local-first privacy workflows
- ComfyUI creative image/video workflows
- Computer-use and browser automation
- Digital product validation and launch research

Platform

- Framework: Hermes Agent
- Environment: Linux Arch
- Primary model: OpenAI Codex gpt-5.6-terra
- Local models: Ollama phi3:mini, qwen2.5-coder:7b
- Voice: English speech recognition and Australian-English text-to-speech
- Design: local-first, privacy-conscious, tool-using, multi-agent capable
