---
description: "Curated reading paths through the AI Runtime Security framework, organised by role and goal."
---

# Reading Paths

This site covers a lot of ground. These curated paths help you find what matters most, based on your role or what you are trying to achieve. Each path is a suggested sequence, not a strict order. Skip what you already know, dive deeper where you need to.

## By role

### Security leaders and CISOs

Understand the risk landscape, the control model, and how to position AI runtime security within your existing programme.

1. [What is AI Runtime Security?](what-is-ai-runtime-security.md)
2. [Risk Tiers](core/risk-tiers.md)
3. [Controls](core/controls.md)
4. [Security Leaders stakeholder view](stakeholders/security-leaders.md)
5. [Enterprise Day in the Life](strategy/enterprise-day-in-the-life.md)
6. [SOC Integration](extensions/technical/soc-integration.md)

### Risk, governance, and compliance

Map the framework to regulatory requirements and build governance structures that work in practice.

1. [Risk Assessment](core/risk-assessment.md)
2. [Risk & Governance stakeholder view](stakeholders/risk-and-governance.md)
3. [AI Governance Operating Model](extensions/regulatory/ai-governance-operating-model.md)
4. [EU AI Act Crosswalk](extensions/regulatory/eu-ai-act-crosswalk.md)
5. [ISO 42001 Alignment](extensions/regulatory/iso-42001-alignment.md)
6. [NIST IR 8596 Alignment](extensions/regulatory/nist-ir-8596-alignment.md)
7. [Compliance & Legal stakeholder view](stakeholders/compliance-and-legal.md)

### Enterprise architects

Understand the technical architecture, infrastructure patterns, and how runtime controls integrate with your existing platform.

1. [Architecture](ARCHITECTURE.md)
2. [Anatomy of an Agent](agentic-agent-anatomy.md)
3. [Constraining Agents](constraining-agents.md)
4. [Enterprise Architects stakeholder view](stakeholders/enterprise-architects.md)
5. [Infrastructure Controls](infrastructure/)
6. [Platform Patterns: AWS Bedrock](infrastructure/reference/platform-patterns/aws-bedrock.md), [Microsoft Foundry](infrastructure/reference/platform-patterns/microsoft-foundry.md), [Databricks](infrastructure/reference/platform-patterns/databricks.md)

### AI engineers and ML practitioners

Get hands-on with controls, implementation patterns, and technical reference material.

1. [Quick Start](QUICK_START.md)
2. [AI Engineers stakeholder view](stakeholders/ai-engineers.md)
3. [Agentic AI Controls](core/agentic.md)
4. [Judge Assurance](core/judge-assurance.md)
5. [Model-as-Judge Implementation](extensions/technical/model-as-judge-implementation.md)
6. [Sandbox Patterns](infrastructure/agentic/sandbox-patterns.md)
7. [Tool Access Controls](infrastructure/agentic/tool-access-controls.md)
8. [Judge Prompt Examples](extensions/templates/judge-prompt-examples.md)

### Product and business owners

Understand what runtime security means for your AI products, how to scope it, and how to make proportionate decisions.

1. [What is AI Runtime Security?](what-is-ai-runtime-security.md)
2. [Business Owners stakeholder view](stakeholders/business-owners.md)
3. [Product Owners stakeholder view](stakeholders/product-owners.md)
4. [Use Case Filter](strategy/use-case-filter.md)
5. [Business Alignment](strategy/business-alignment.md)
6. [From Idea to Production](strategy/idea-to-production.md)
7. [Security as Enablement](insights/security-as-enablement.md)

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
