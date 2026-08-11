---
title: Practice and flashcards
layout: default
parent: GH-600 Agentic AI Developer
nav_order: 4
---

# Practice questions and flashcards

A self-test bank organised by domain, followed by rapid-recall flashcards. Answers sit inside collapsible blocks, so each question can be attempted before the answer is revealed. Use this bank on the review days and after the day-12 mock to drill weak areas.

How to use it: read the question, answer out loud or in writing, then expand the answer. Track every miss by domain and feed those into the remediation day.

---

## Domain 1: Architecture and SDLC

**Q1.** An agent is asked to refactor a module. What must it produce before it is allowed to change any file, and why?

<details markdown="1"><summary>Answer</summary>

A structured, inspectable plan. Separating planning from execution lets the plan be validated and, where risk warrants, approved by a human before any action is taken. Blocking action until the plan is checked is the core control in this domain.
</details>

**Q2.** Name three things that must be defined for an agent task to be considered well-formed.

<details markdown="1"><summary>Answer</summary>

Inputs, outputs, and success criteria. Without explicit success criteria the agent cannot be evaluated and is prone to anti-patterns such as scope drift.
</details>

**Q3.** What is the purpose of an "inspectable artifact" in an autonomous agent workflow?

<details markdown="1"><summary>Answer</summary>

It records the agent's plan, reasoning, or output inside standard development tooling (for example a pull request description or a plan file) so a human can review the work without slowing delivery, and so the action is traceable and auditable.
</details>

**Q4.** Give one common agent anti-pattern and how to mitigate it.

<details markdown="1"><summary>Answer</summary>

Acting before planning (taking irreversible action without a validated plan). Mitigate by configuring planning distinct from execution and blocking action until the plan is approved. Other acceptable answers: unbounded autonomy (mitigate with risk-based autonomy levels), or missing success criteria (mitigate by defining them up front).
</details>

---

## Domain 2: Tool use and environment interaction

**Q5.** What principle should govern the permissions granted to each agent tool?

<details markdown="1"><summary>Answer</summary>

Least privilege. Each tool receives only the permissions the task requires, no more, to limit blast radius if the agent misbehaves.
</details>

**Q6.** What does an MCP allow list control, and why does it matter for a remote MCP server?

<details markdown="1"><summary>Answer</summary>

An allow list restricts which MCP servers or tools an agent may use. For a remote MCP server it prevents the agent from reaching unapproved external tools, which is both a security and a governance control.
</details>

**Q7.** List the four safe-execution mechanisms an agent should have when acting on a repository.

<details markdown="1"><summary>Answer</summary>

Error handling, retries, rollbacks, and escalation paths, all backed by traceability of the agent's actions.
</details>

**Q8.** How is an agent scoped so it can only affect one repository and one branch, and why is that useful?

<details markdown="1"><summary>Answer</summary>

Through repository scope and branch-based scope configuration. It contains the agent's reach, so autonomous branch and pull request creation cannot touch protected or unrelated code, and every change flows through review.
</details>

---

## Domain 3: Memory, state, and execution

**Q9.** Distinguish short-term, long-term, and external memory for an agent.

<details markdown="1"><summary>Answer</summary>

Short-term holds the current task context. Long-term persists knowledge across tasks. External memory is retrieved on demand from an outside store (for example a vector store or knowledge base). Memory should be scoped to task-relevant information only.
</details>

**Q10.** What is context drift, and how is it handled during a long agent run?

<details markdown="1"><summary>Answer</summary>

Context drift is the gradual divergence of the agent from its original goal or prior decisions during an extended run. It is handled by detecting the drift and correcting or re-anchoring the agent, often by capturing progress and decisions as durable artifacts that can be reloaded.
</details>

**Q11.** Why persist agent state as durable artifacts rather than only in memory?

<details markdown="1"><summary>Answer</summary>

So the agent can resume work without repeating steps or diverging from prior decisions, and so state survives across tools and environments without conflicting or stale context.
</details>

---

## Domain 4: Evaluation, error analysis, and tuning

**Q12.** An agent failed a task. Name the three broad root-cause categories to classify the failure into.

<details markdown="1"><summary>Answer</summary>

Reasoning errors, tool misuse, and context or environment issues.
</details>

**Q13.** Which artifacts are used to identify and diagnose an agent failure?

<details markdown="1"><summary>Answer</summary>

Logs, plans, traces, outputs, and workflow artifacts.
</details>

**Q14.** After classifying a root cause, what three levers are available to tune the agent?

<details markdown="1"><summary>Answer</summary>

Revise instructions, workflows, or constraints; refine memory usage; and refine tool usage and tool access.
</details>

**Q15.** What is the difference between a qualitative and a quantitative evaluation signal, and where do automated scans fit?

<details markdown="1"><summary>Answer</summary>

Quantitative signals are measurable (for example test pass rate or scan findings count), qualitative signals are judgment-based (for example review comments on reasoning quality). Automated scanning tools generate evaluation signals at scale and feed the analysis loop.
</details>

---

## Domain 5: Multi-agent coordination

**Q16.** Name three kinds of conflict that can arise when multiple agents run in parallel.

<details markdown="1"><summary>Answer</summary>

Overlapping code changes, duplicated effort, and contradictory outputs.
</details>

**Q17.** What is the purpose of agent isolation in parallel execution?

<details markdown="1"><summary>Answer</summary>

It gives each agent a bounded scope so agents do not interfere with one another, which reduces conflicts and makes their work independently reviewable and auditable.
</details>

**Q18.** Two recovery patterns for a stalled or degraded multi-agent workflow are what?

<details markdown="1"><summary>Answer</summary>

Rollback and human-in-the-loop intervention. The workflow should also produce audit artifacts documenting decisions, handoffs, and outcomes for post-hoc analysis.
</details>

**Q19.** How is an agent retired from an active multi-agent workflow without breaking it?

<details markdown="1"><summary>Answer</summary>

Update, reconfigure, or replace it while preserving auditability and workflow continuity, so in-flight work and the audit trail are not disrupted.
</details>

---

## Domain 6: Guardrails and accountability

**Q20.** An agent proposes an irreversible change. What should the guardrail require?

<details markdown="1"><summary>Answer</summary>

Explicit human authorisation, or a controlled path, before the irreversible or compliance-sensitive change proceeds.
</details>

**Q21.** On what basis are autonomy levels assigned to agent actions?

<details markdown="1"><summary>Answer</summary>

By classifying actions by operational, security, and compliance risk, then assigning autonomy that maximises delivery speed while remaining compliant with security and Responsible AI standards.
</details>

**Q22.** What should happen to an action that violates a defined security, compliance, or Responsible AI policy?

<details markdown="1"><summary>Answer</summary>

It should be blocked outright, not merely flagged.
</details>

**Q23.** Why avoid adding human approval to every agent action?

<details markdown="1"><summary>Answer</summary>

Approvals that do not materially reduce risk slow delivery. Guardrails should reserve human judgment for high-risk, irreversible, or policy-sensitive actions and preserve velocity everywhere else.
</details>

---

## Rapid-recall flashcards

Cover the right column, recall it from the left, then check.

| Prompt | Recall |
| --- | --- |
| Passing score | 700 or greater |
| Exam length | 120 minutes, proctored |
| Heaviest domain | Domain 2, tool use and environment (20-25%) |
| Lifecycle loop | Plan, act, evaluate (then tune) |
| Gate before action | Validated, inspectable plan |
| Tool permission rule | Least privilege |
| Controls which MCP tools are reachable | Allow list |
| Four safe-execution mechanisms | Error handling, retries, rollbacks, escalation |
| Three memory types | Short-term, long-term, external |
| Long-run failure of focus | Context drift, corrected by re-anchoring |
| Three failure root causes | Reasoning errors, tool misuse, context or environment |
| Three tuning levers | Instructions and constraints, memory, tool access |
| Three multi-agent conflicts | Overlapping edits, duplicated effort, contradictory outputs |
| Two recovery patterns | Rollback, human-in-the-loop |
| Autonomy assigned by | Operational, security, and compliance risk |
| Policy-violating action | Blocked |
| Account type for scheduling | Personal Microsoft account (MSA) |
| System of record and control plane | GitHub |

## Scoring the mock

On the day-12 full mock, tag every miss with its domain, then re-study only the two lowest-scoring domains on day 13. A miss on a flashcard is a signal to re-read that domain's deep-dive, not to move on.
