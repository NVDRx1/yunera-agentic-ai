# Yunera — Private Local-First Hermes AI Agent
Yunera is a customised Hermes Agent profile built for evidence-backed research, secure local automation, software development, Android app workflows, and practical multi-agent execution. It runs locally on Linux, keeps control of files and automation on-device, and combines cloud reasoning with local Ollama models for privacy-conscious workloads.

Core capabilities

- Evidence-backed web, RSS, competitor, market, and Reddit research
- Browser automation, CDP control, local terminal access, file operations, and code execution
- GitHub repository, issue, pull request, review, and project workflows
- Planning, implementation, testing, debugging, and documentation support
- Android/mobile app development workflows, including iterative UX QA and release-readiness checks
- Data-backed companion interfaces and external reference-data integration
- Accountant-ready finance app and local-first crypto-tax workflow support
- Image and video generation workflows through ComfyUI
- Speech-to-text, Australian-English text-to-speech, image analysis, and document handling
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
- Finance tooling, tax workflows, and local-first data handling
- ComfyUI creative image/video workflows
- Computer-use and browser automation
- Digital product validation and launch research

Platform

- Framework: Hermes Agent
- Environment: Linux
- Primary model: OpenAI Codex gpt-5.6-terra
- Local models: Ollama phi3:mini, qwen2.5-coder:7b
- Voice: English speech recognition and Australian-English text-to-speech
- Design: local-first, privacy-conscious, tool-using, multi-agent capable
