---
title: Domain deep-dives
layout: default
parent: GH-600 Agentic AI Developer
nav_order: 2
---

# Domain deep-dives

Each of the six domains is summarised below with the skills the study guide lists and a diagram that shows the flow. The weighting shows how many scored questions to expect, and therefore how much attention each domain earns in the sprint plan.

---

## Domain 1: Prepare agent architecture and SDLC processes (15-20%)

The foundation domain. It is about placing an agent correctly inside the software development lifecycle, and above all separating planning from action so a plan can be inspected and approved before anything happens.

```mermaid
flowchart TD
    G["Goal and success criteria"] --> P["Agent produces a structured plan"]
    P --> V{"Plan validated?"}
    V -- No --> P
    V -- Yes --> H{"Human approval<br/>needed for this risk level?"}
    H -- Yes --> HA["Human reviews inspectable artifact"]
    H -- No --> ACT["Agent acts"]
    HA --> ACT
    ACT --> OBS["Inspectable artifacts and observability"]
```

Skills to master:

| Skill area | What it covers |
| --- | --- |
| Integrate agents into the SDLC | Identify the steps an agent performs, define inputs, outputs, and success criteria, and mitigate common anti-patterns |
| Separate planning from action | Configure planning distinct from execution, output a structured plan, validate plans, and block action until a plan is checked and approved |
| Observability and control | Set the degree of autonomy with guardrails, produce inspectable artifacts in standard tooling, and add human intervention that does not slow delivery |

---

## Domain 2: Implement tool use and environment interaction (20-25%)

The heaviest-scored domain. It covers giving an agent the right tools with the right permissions, wiring up MCP servers, scoping the agent to a repository and branch, and handling failure safely.

```mermaid
flowchart LR
    subgraph Tools["Tool ecosystem"]
        T1["Built-in tools"]
        T2["MCP server tools"]
    end
    A["Agent"] -->|least-privilege permissions| Tools
    T2 --- REG["MCP registries and allow lists"]
    A --> ENV["Environment scope:<br/>repo, branch, CI"]
    ENV --> ACT["Autonomous branch<br/>and pull request creation"]
    ACT --> SAFE["Safe execution:<br/>retries, rollback, escalation, traceability"]
```

Skills to master:

| Skill area | What it covers |
| --- | --- |
| Select and configure tools | Identify required tools, configure them, and set tool permissions |
| Configure MCP servers | Add an MCP server as a tool, configure a GitHub remote MCP server, configure MCP registries, and manage allow lists |
| Integrate into dev environments | Scope to a repository and branch, invoke an agent in a CI workflow, and enable autonomous branch and pull request creation |
| Safe execution and error handling | Implement error handling, retries, rollbacks, escalation paths, and traceability for agent actions |

---

## Domain 3: Manage memory, state, and execution (10-15%)

How an agent remembers, what it persists, and how it avoids drifting off course during long runs.

```mermaid
flowchart LR
    subgraph Mem["Memory types"]
        S["Short-term<br/>(current task)"]
        L["Long-term<br/>(across tasks)"]
        X["External<br/>(retrieved on demand)"]
    end
    Mem --> SCOPE["Scoped to task-relevant<br/>information only"]
    SCOPE --> RULES["Expiration, pruning, reset rules"]
    RULES --> ART["State persisted as durable artifacts"]
    ART --> DRIFT{"Context drift detected?"}
    DRIFT -- Yes --> CORRECT["Correct and re-anchor"]
    DRIFT -- No --> RESUME["Resume without repeating steps"]
```

Skills to master:

| Skill area | What it covers |
| --- | --- |
| Memory strategies | Choose between short-term, long-term, and external memory, and scope memory to task-relevant information with expiration, pruning, and reset rules |
| State and drift | Capture progress and decisions as durable artifacts, resume work without repeating steps, and detect and correct drift during long runs |
| Continuity across tools | Share state, and prevent conflicting or stale context across tools and environments |

---

## Domain 4: Perform evaluation, error analysis, and tuning (15-20%)

Deciding whether an agent did well, finding out why it failed, and adjusting it. This is the closest domain to product-manager instincts about measurement.

```mermaid
flowchart LR
    SC["Define success criteria<br/>and evaluation signals"] --> SCAN["Generate signals via<br/>automated scanning tools"]
    SCAN --> FAIL["Analyse failures:<br/>logs, plans, traces, outputs"]
    FAIL --> ROOT["Classify root cause:<br/>reasoning, tool misuse, context"]
    ROOT --> TUNE["Tune instructions,<br/>memory, tool access"]
    TUNE --> SC
```

Skills to master:

| Skill area | What it covers |
| --- | --- |
| Success criteria and signals | Specify expected outcomes and constraints, identify qualitative and quantitative signals, and generate signals with automated scanning tools |
| Failure and root-cause analysis | Identify failures from logs, plans, traces, outputs, and workflow artifacts, then classify root causes |
| Tune behaviour | Revise instructions, workflows, or constraints, and refine memory and tool usage from evaluation results |

---

## Domain 5: Orchestrate multi-agent coordination (15-20%)

Running more than one agent at once without letting them collide, and keeping the whole workflow auditable.

```mermaid
flowchart TD
    O["Orchestrator"] --> A1["Agent A<br/>(isolated scope)"]
    O --> A2["Agent B<br/>(isolated scope)"]
    O --> A3["Agent C<br/>(isolated scope)"]
    A1 --> CONF{"Conflict?<br/>overlapping edits,<br/>duplicated effort"}
    A2 --> CONF
    A3 --> CONF
    CONF -- Yes --> RES["Detect and resolve;<br/>rollback or human-in-the-loop"]
    CONF -- No --> AUD["Audit artifacts:<br/>decisions, handoffs, outcomes"]
    RES --> AUD
```

Skills to master:

| Skill area | What it covers |
| --- | --- |
| Operate multi-agent workflows | Apply an orchestration pattern, isolate agents for parallel execution, and detect and resolve conflicts |
| Multi-agent observability | Produce review-and-audit artifacts, document decisions and handoffs, and perform post-hoc analysis |
| Failure response and lifecycle | Identify stalled or partial executions, apply recovery patterns, and add, update, or retire agents without disrupting active workflows |

---

## Domain 6: Implement guardrails and accountability (10-15%)

Deciding which agent actions need a human, and enforcing least privilege and explicit authorisation for anything irreversible.

```mermaid
flowchart TD
    ACT["Proposed agent action"] --> RISK{"Classify risk:<br/>operational, security, compliance"}
    RISK -- Low --> AUTO["Autonomous, preserve velocity"]
    RISK -- Medium --> SCOPE["Least-privilege scope<br/>and controlled path"]
    RISK -- High or irreversible --> HUMAN["Require explicit human authorisation"]
    RISK -- Policy violation --> BLOCK["Block the action"]
```

Skills to master:

| Skill area | What it covers |
| --- | --- |
| Define autonomy levels | Classify actions by operational, security, and compliance risk, and assign autonomy levels that maximise speed while staying compliant |
| Guardrails and human-in-the-loop | Identify actions needing human judgment, block policy-violating actions, scope permissions to least privilege, and require authorisation for irreversible or compliance-sensitive changes |

---

## One picture for all six domains

```mermaid
mindmap
  root((GH-600))
    D1 Architecture and SDLC
      Plan separate from action
      Structured, validated plans
      Inspectable artifacts
    D2 Tool use and environment
      Tools and permissions
      MCP servers and allow lists
      Repo and branch scope
      Retries, rollback, escalation
    D3 Memory and state
      Short, long, external memory
      Durable artifacts
      Drift detection
    D4 Evaluation and tuning
      Success criteria and signals
      Root-cause analysis
      Tune instructions and tools
    D5 Multi-agent coordination
      Orchestration patterns
      Isolation and conflict resolution
      Audit artifacts
    D6 Guardrails and accountability
      Autonomy by risk
      Human-in-the-loop
      Least privilege
```
