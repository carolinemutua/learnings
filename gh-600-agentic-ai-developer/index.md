---
title: GH-600 Agentic AI Developer
layout: default
nav_order: 2
has_children: true
---

# GH-600: GitHub Certified Agentic AI Developer

A two-week, practice-first study kit for Exam GH-600, the exam behind the GitHub Certified: Agentic AI Developer credential. The kit is built for someone who already works with coding agents, custom instructions, MCP servers, and Copilot setup steps, and who wants to convert that hands-on experience into a passing score quickly.

## Exam facts at a glance

| Attribute | Detail |
| --- | --- |
| Exam code | GH-600 |
| Credential | GitHub Certified: Agentic AI Developer |
| Level | Intermediate |
| Maintained by | GitHub, delivered by Microsoft through Pearson VUE |
| Format | Proctored, may include interactive components |
| Duration | 120 minutes |
| Passing score | 700 (a score of 700 or greater passes) |
| Status | Generally available (not beta), so scores return immediately |
| Language | English |
| Scheduling | Personal Microsoft account (MSA) strongly recommended, so records survive a job change |

## What the exam measures

The exam is split into six domains. The percentages are the share of scored questions, which drives how the two-week plan allocates time.

```mermaid
pie showData
    title GH-600 scored weight by domain
    "D2 Tool use and environment (20-25%)" : 22
    "D1 Architecture and SDLC (15-20%)" : 18
    "D4 Evaluation and tuning (15-20%)" : 18
    "D5 Multi-agent coordination (15-20%)" : 18
    "D3 Memory, state, execution (10-15%)" : 12
    "D6 Guardrails and accountability (10-15%)" : 12
```

The mental model that ties all six domains together is a single agent lifecycle running inside GitHub as the control plane.

```mermaid
flowchart LR
    subgraph Plane["GitHub as system of record and control plane"]
        direction LR
        A["Plan<br/>structured, inspectable"] --> B["Act<br/>tools, MCP, environment"]
        B --> C["Evaluate<br/>scans, logs, artifacts"]
        C --> D["Tune<br/>instructions, memory, tools"]
        D --> A
    end
    G["Guardrails and human-in-the-loop"] -.governs.-> B
    M["Memory and state"] -.persists across.-> B
```

Read the plan next, then work through the domain deep-dives.

## Pages in this kit

| Page | Purpose |
| --- | --- |
| [Two-week plan]({{ site.baseurl }}/gh-600-agentic-ai-developer/plan/) | Day-by-day sprint, weighted to the scored domains |
| [Domain deep-dives]({{ site.baseurl }}/gh-600-agentic-ai-developer/domains/) | Each of the six domains explained with a diagram and the key skills |
| [Resources]({{ site.baseurl }}/gh-600-agentic-ai-developer/resources/) | Official study guide, training modules, and supporting documentation |
