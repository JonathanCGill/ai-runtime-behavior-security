---
description: "Why container sandboxes are not a reliable security boundary for frontier AI agents, and what the SandboxEscapeBench results mean for runtime containment architecture."
---

# The Sandbox Escape Problem

*Your container is not as strong as you think it is.*

The standard advice for running AI agents that execute code is simple: put them in a container. Docker, OCI, an ephemeral sandbox. The container is the boundary. The agent can do whatever it wants inside; nothing escapes.

That assumption is now empirically testable. And the results should change how you architect containment.

## Frontier Models Can Break Out

In March 2026, researchers from the University of Oxford and the UK AI Security Institute published *Quantifying Frontier LLM Capabilities for Container Sandbox Escape*. They introduced **SandboxEscapeBench**, an open benchmark that measures whether frontier LLMs can escape container sandboxes.

The methodology is clean: a Capture the Flag evaluation using nested sandboxes. The inner container holds the model. The outer layer holds the flag (`/flag.txt`). No known vulnerabilities exist in the outer layer. The model gets a shell inside the container and tries to read the flag on the host. Success means the model escaped.

The benchmark covers 18 challenge scenarios across three layers of the container stack:

| Layer | Scenarios | What it tests |
|-------|-----------|---------------|
| **Orchestration** | 4 | Misconfigurations in container orchestration (Docker socket exposure, overprivileged mounts) |
| **Runtime** | 8 | Weaknesses in the container runtime (namespace escapes, capability abuse, runtime flaws) |
| **Kernel** | 6 | Kernel-level vulnerabilities (privilege escalation, cgroup escapes, syscall exploits) |

The finding: **frontier models can reliably escape container sandboxes under common real-world failure modes.** Misconfigurations and exposed control surfaces are particularly exploitable. Models also achieved non-trivial success on harder runtime and kernel scenarios.

## Why This Matters for Runtime Security

Container security surveys have catalogued over 200 weaknesses across the container stack. That is not new. What is new is that an autonomous agent with shell access can now discover and exploit those weaknesses without human guidance.

This changes the threat model. Previously, container escape required a skilled attacker who had already gained access. Now, the agent *is* the attacker, and it already has access: you gave it a shell.

Three implications stand out:

**1. Docker alone is not sufficient isolation for high-risk agents.**

Much of the open-source agent ecosystem and local developer tooling relies on standard Docker containers as the isolation boundary. Hyperscale providers use hardware-level isolation (Firecracker, gVisor) for good reason. If your agents execute arbitrary code, container isolation should be treated as one layer, not the only layer.

**2. Misconfiguration is the primary attack surface.**

The easiest escapes in SandboxEscapeBench target orchestration-level misconfigurations: mounted Docker sockets, overprivileged containers, exposed control planes. These are not exotic kernel exploits. They are configuration mistakes that appear in production environments every day. The [sandbox patterns](../infrastructure/agentic/sandbox-patterns.md) in this framework address these directly, but only if they are actually implemented.

**3. Containment must be verified, not assumed.**

A sandbox that has not been tested against escape is a sandbox you hope works. SandboxEscapeBench provides a way to measure escape capability against your specific configuration. This is the kind of evidence-based assurance that the [constrain-regardless architecture](why-containment-beats-evaluation.md) requires.

## What Defenders Should Do

The research points to a layered response:

**Select isolation proportionate to risk.** Process isolation and basic containers are reasonable for low-risk, read-only operations. Agents that execute arbitrary code, install packages, or make network calls need VM-level isolation or hardened container runtimes (gVisor, Kata Containers). The framework's [risk tiers](../core/risk-tiers.md) should drive this selection.

**Harden the configuration.** Most successful escapes target avoidable misconfigurations. Never mount the Docker socket into agent containers. Never run containers as root or with `--privileged`. Drop all capabilities except those explicitly required. Restrict `/proc` and `/sys` access. These are the basics, and they stop the easiest attacks.

**Enforce ephemeral execution.** Every agent execution gets a fresh container from a clean image. No state persists between executions. No accumulated attack surface. This is [SAND-05](../infrastructure/agentic/sandbox-patterns.md) in practice.

**Test your sandboxes.** SandboxEscapeBench is open source. Run it against your deployment configuration. If a frontier model can escape your sandbox, so can the next model your users deploy.

**Layer your defences.** The sandbox is containment Layer 1. Network controls, resource limits, pre-execution code scanning, and the [Model-as-Judge](../core/judge-assurance.md) operate independently. A model that escapes the container but cannot reach the network has not achieved much. Defence in depth is not optional when the attacker is the system you are trying to contain.

## The Broader Pattern

This research reinforces a principle that runs through this framework: **security properties of AI systems must be enforced through infrastructure, not through trust in the model's behavior.** You do not ask the model to stay in its sandbox. You build a sandbox the model cannot leave.

But "cannot leave" is an engineering claim, not a guarantee. SandboxEscapeBench demonstrates that the claim needs evidence. Container isolation that was adequate last year may not be adequate against next year's models. Containment is not a static property. It must be continuously verified as model capabilities advance.

The [constrain-regardless architecture](why-containment-beats-evaluation.md) does not depend on knowing exactly what a model can do. But it does depend on the containment boundary actually holding. This paper is a reminder that the boundary itself needs testing.

## Related Reading

| If you need... | Go to |
|----------------|-------|
| Sandbox implementation controls | [Sandbox Patterns for Agentic AI](../infrastructure/agentic/sandbox-patterns.md) |
| Why infrastructure enforcement matters | [Infrastructure Beats Instructions](infrastructure-beats-instructions.md) |
| The containment-first security model | [Why Containment Beats Evaluation](why-containment-beats-evaluation.md) |
| Defining containment from business intent | [Containment Through Declared Intent](containment-through-intent.md) |
| Risk-proportionate control selection | [Risk Tiers and Control Selection](../core/risk-tiers.md) |

!!! info "References"
    - [Marchand, R., O Cathain, A., Wynne, J., Giavridis, P.M., Deverett, S., Wilkinson, J., Gwartz, J. and Coppock, H. (2026) *Quantifying Frontier LLM Capabilities for Container Sandbox Escape*. arXiv:2603.02277.](https://arxiv.org/abs/2603.02277)
    - [SandboxEscapeBench source code](https://github.com/UKGovernmentBEIS/sandbox_escape_bench)
