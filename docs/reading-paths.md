---
description: "Curated reading paths through the AI Runtime Security framework, organised by goal."
---

# Reading Paths

This site covers a lot of ground. These curated paths help you find what matters most based on what you are trying to achieve. Each path is a suggested sequence, not a strict order. Skip what you already know, dive deeper where you need to.

!!! tip "Looking for role-based guidance?"
    The [Stakeholder Views](stakeholders/) pages provide tailored entry points for security leaders, risk teams, architects, engineers, product owners, and more. Each one includes a starting path, concrete first actions, and answers to common objections.

## The Golden Thread: Guardrails, Judges, and Why They Work Together

This is the core reading path. It takes you from "why do I need runtime security at all?" through each control layer, how they reinforce each other, and the evidence that the approach works. Each article answers a question the previous one raises.

**Start here if you are new to the framework, or if you want to understand the reasoning behind the architecture before diving into controls and checklists.**

| # | Article | What it argues | What it sets up |
|---|---------|---------------|-----------------|
| 1 | [Why AI Security Is a Runtime Problem](insights/why-ai-security-is-a-runtime-problem.md) | AI is non-deterministic. Pre-deployment testing cannot prove future safety. Security must be continuous. | If testing is insufficient, what does continuous security actually look like? |
| 2 | [Why Your Guardrails Aren't Enough](insights/why-guardrails-arent-enough.md) | Guardrails catch known-bad patterns. Three classes of failure walk past them: novel attacks, semantic violations, emergent behaviour at scale. | If guardrails are necessary but insufficient, what fills the gap? |
| 3 | [Practical Guardrails](insights/practical-guardrails.md) | Guardrails work in two classes (security, data protection) at five pipeline points. They need to be well-built, not dismissed. | Guardrails are solid for what they do. What catches everything else? |
| 4 | [The Judge Detects. It Doesn't Decide.](insights/judge-detects-not-decides.md) | The Judge runs asynchronously, detecting unknown-bad without blocking. It informs human decisions rather than replacing them. | If the Judge is this important, how do we know it actually works? |
| 5 | [Judge Assurance](core/judge-assurance.md) | Validate the Judge against human ground truth. Track agreement, false negatives, drift. Different model family from the generator. Calibrate continuously. | The Judge can be validated, but can it be attacked? |
| 6 | [When the Judge Can Be Fooled](core/when-the-judge-can-be-fooled.md) | The Judge is itself an LLM. It can be manipulated through output crafting, prompt injection, and shared blind spots. Mitigations exist but perfection does not. | If no single layer is reliable, what holds the system together? |
| 7 | [Humans Remain Accountable](insights/humans-remain-accountable.md) | Humans own outcomes. The Judge makes oversight scalable, not optional. Regulation requires it. | Humans can't review everything. What else keeps the system honest? |
| 8 | [Infrastructure Beats Instructions](insights/infrastructure-beats-instructions.md) | Telling agents what not to do fails. Make violations technically impossible through network controls, access restrictions, and action allowlists enforced outside the agent. | We have layers and infrastructure. How do we avoid over-constraining? |
| 9 | [The Constraint Curve](insights/the-constraint-curve.md) | Early constraints deliver outsized security at minimal cost. Late constraints destroy the value that justified using AI. Proportionality is the design principle. | We know how much to constrain. But how does the system improve over time? |
| 10 | [The Feedback Loops That Make It Work](insights/feedback-loops.md) | Four feedback loops at different speeds (judge tightens guardrails, humans calibrate the judge, humans update policy, downstream outcomes validate decisions) create a self-improving system. | The loops improve detection. But what anchors all these layers to the same goal? |
| 11 | [Containment Through Declared Intent](insights/containment-through-intent.md) | Declared intent is the reference point for every layer. Guardrails become purpose-specific. The Judge has alignment criteria. Humans know what to escalate. Without intent, controls are arbitrary. | How does all of this come together as architecture? |
| 12 | [Architecture Overview](ARCHITECTURE.md) | Guardrails prevent. Judge detects. Humans decide. Circuit breakers contain. Single-agent and multi-agent variants with PACE resilience for graceful degradation. | Does it actually work in practice? |
| 13 | [What Works](insights/what-works.md) | Organisations using runtime controls detect breaches 108 days faster. Guardrails block millions of attacks daily. Judges catch hallucination in production. The evidence is clear, but adoption is low. | *You are now ready to implement. Start with the [Quick Start](QUICK_START.md) or [Implementation Checklist](core/checklist.md).* |

!!! tip "Reading time"
    The full path is roughly 90 minutes. Articles 1 through 6 cover the core argument in about 40 minutes. If you stop there, you will understand why the guardrail-plus-judge pattern exists and what keeps it honest.

---

## By goal

### "I need to understand the threat landscape"

1. [Why Guardrails Aren't Enough](insights/why-guardrails-arent-enough.md)
2. [RAG Is Your Biggest Attack Surface](insights/rag-is-your-biggest-attack-surface.md)
3. [The MCP Problem](insights/the-mcp-problem.md)
4. [When Agents Talk to Agents](insights/when-agents-talk-to-agents.md)
5. [You Don't Know What You're Deploying](insights/you-dont-know-what-youre-deploying.md)
6. [State of Reality](insights/state-of-reality.md)

### "I need to secure multi-agent systems"

1. [MASO Framework overview](maso/)
2. [Prompt, Goal & Epistemic Integrity](maso/controls/prompt-goal-and-epistemic-integrity.md)
3. [Identity & Access](maso/controls/identity-and-access.md)
4. [Execution Control](maso/controls/execution-control.md)
5. [Privileged Agent Governance](maso/controls/privileged-agent-governance.md)
6. [Multi-Agent Controls](core/multi-agent-controls.md)
7. [Worked Examples](maso/examples/worked-examples.md)

### "I need templates and practical artefacts"

1. [Implementation Checklist](core/checklist.md)
2. [Threat Model Template](extensions/templates/threat-model-template.md)
3. [AI Incident Playbook](extensions/templates/ai-incident-playbook.md)
4. [Vendor Assessment Questionnaire](extensions/templates/vendor-assessment-questionnaire.md)
5. [Model Card Template](extensions/templates/model-card-template.md)
6. [Use Case Examples](extensions/examples/)

### "I want to see real-world examples"

1. [Customer Service AI](extensions/examples/01-customer-service-ai.md)
2. [Internal Doc Assistant](extensions/examples/02-internal-doc-assistant.md)
3. [Credit Decision Support](extensions/examples/03-credit-decision-support.md)
4. [High-Volume Customer Comms](extensions/examples/04-high-volume-customer-communications.md)
5. [Fraud Analytics](extensions/examples/05-fraud-analytics.md)
6. [Red Team Playbook](maso/red-team/red-team-playbook.md)

!!! tip "Still not sure where to start?"
    The [Quick Start](QUICK_START.md) guide gives you a condensed overview you can read in a few minutes. The [FAQ](FAQ.md) answers common questions about scope, applicability, and how the framework relates to existing standards.

!!! info "References"
    - [What is AI Runtime Security?](what-is-ai-runtime-security.md)
    - [Quick Start](QUICK_START.md)
    - [FAQ](FAQ.md)
