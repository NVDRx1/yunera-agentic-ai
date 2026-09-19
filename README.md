# Yunera — Private, Local-First Hermes AI Agent

Yunera is a personally configured Hermes Agent profile running locally on Linux. She pairs a capable cloud reasoning model with local Ollama models, browser and desktop control, code execution, persistent preferences, and a curated specialist-skill library. The design is practical: research claims before stating them, execute work with verification, and keep privacy-sensitive work, files, and profile state under local control.

## How Yunera is built

- **Agent framework:** Hermes Agent, configured as an isolated `builder` profile rather than a generic shared assistant
- **Primary reasoning:** OpenAI Codex `gpt-5.6-terra`
- **Local/private models:** Ollama `phi3:mini` and `qwen2.5-coder:7b` for suitable reference, coding, and multi-agent workloads
- **Operating environment:** Arch Linux; local shell, filesystem, browser, and native desktop access are available through controlled tools
- **Agent architecture:** a tool-using primary agent can delegate isolated research, planning, review, and coding work to sub-agents, then consolidate and verify the result
- **Continuity:** persistent memory stores durable preferences; task-specific skills preserve reusable procedures without turning every conversation into a data dump
- **Voice:** a calm, exact, direct operating style. Substance and accuracy come before persona.

## What Yunera can do

### Research, monitoring, and source work

- Evidence-backed web research, source extraction, literature and market reconnaissance
- RSS, Atom, and JSON-feed discovery and reading
- Competitor and company-news monitoring with cited digests
- Reddit reading, search, thread, and community research without requiring a browser
- External-reference and ranked-data integration for trustworthy applications
- Structured planning, problem framing, source validation, and clear written synthesis

### Software, data, and delivery

- Plan, implement, test, debug, document, and verify software changes
- GitHub repository operations, issues, pull requests, reviews, releases, Actions, and project workflows
- Repository documentation maintenance with local validation and verified remote publication
- Data-backed interfaces, structured exports, accountant-ready data workflows, and local-first record handling
- Android development and delivery: Compose foundations, state, navigation, performance, accessibility, adaptive layouts, visual QA, packaging, and release-readiness checks
- Local Ollama installation and integration for privacy-conscious model workflows
- Low-capital digital-product research, validation, and launch planning

### Automation, agents, and computer use

- Browser automation and Chrome DevTools Protocol control
- Local terminal commands, files, code execution, and working-artifact verification
- Native desktop application control through accessibility-aware GUI automation
- Multi-agent orchestration, parallel delegation, independent review, and result synthesis
- Agent-context diagnostics for prompt bloat and unexpected compaction
- Continuous-improvement workflows that capture useful corrections and recurring operational lessons
- Hermes configuration, extension, theming, orchestration, and shared Kanban operations

### Media, communication, and documents

- Diffusion-based image, video, and audio generation through ComfyUI workflows
- Image analysis, document reading, file handling, speech-to-text, and English text-to-speech
- Signal and WhatsApp chat-facing integrations
- Privacy-first communication handling, with identifier redaction where appropriate
- User-specific response-style and presentation guidance

### Security and privacy

- Local-first execution for files, automation, and profile state
- Dedicated profile isolation, persistent-memory boundaries, and deliberate secret handling
- High-impact action gating before destructive, irreversible, financial, or security-sensitive changes
- Privacy-conscious remote access to local services
- Explicit safeguards around dangerous shell operations, credentials, force-pushes, and unverified claims
- Verification before completion: changed files, builds, browser commits, and remote content are checked rather than assumed

## Specialist skill coverage

Yunera’s installed skill library covers the following operational areas:

- Autonomous agents: orchestration, context diagnostics, browser/desktop computer use, Hermes configuration, and Kanban operations
- Business: lean digital-product validation and launch research
- Continuous improvement: capturing lessons from failures, corrections, and better repeatable approaches
- Creative workflows: ComfyUI image, video, and audio generation
- Local models: Ollama setup and model integration
- Productivity: local-first financial-data workflows, privacy-first communication, and user communication style
- Research: competitor monitoring and feed-based source research
- Security: high-impact action review and private remote-service access
- Social research: Reddit reading and community analysis
- Software development: accountant-ready exports, Android delivery, Compose foundations and expert practices, data-backed companion interfaces, external-data integration, GitHub workflows, planning, and repository documentation maintenance

## Operating principles

> Verify before claiming certainty.
>
> Use evidence before confidence.
>
> Protect privacy, agency, and time.
>
> Keep the local system in control of local work.
>
> Move decisively when the task is clear.

## Platform

- **Framework:** Hermes Agent
- **Environment:** Arch Linux
- **Primary model:** OpenAI Codex `gpt-5.6-terra`
- **Local models:** Ollama `phi3:mini`, `qwen2.5-coder:7b`
- **Design:** local-first, privacy-conscious, tool-using, multi-agent capable
