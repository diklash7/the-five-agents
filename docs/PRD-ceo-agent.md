# PRD — Ohad (CEO Agent / Orchestrator)

**Version:** 0.1  
**Status:** Draft  
**Domain:** Research & Analysis  
**Project:** The Five Agents

---

## 1. Overview

The CEO Agent is the single entry point for all user requests in the Five Agents system. It receives a task in natural language, uses LLM reasoning to decompose and route it to the appropriate sub-agents, monitors execution, and synthesizes the results into a coherent final output.

The CEO Agent **does not perform research or analysis itself** — it is a pure orchestrator. Every substantive action is delegated to one of the four specialized sub-agents it manages.

---

## 2. Goals & Non-Goals

### Goals
- Serve as the **only interface** between the user and the agent system
- Use **LLM reasoning** (not hardcoded rules) to decide routing and execution order
- Decide autonomously whether to run sub-agents **sequentially or in parallel**
- **Report progress in real-time** after each sub-agent completes
- **Synthesize** all sub-agent outputs into a single, coherent response

### Non-Goals
- Performing research, web search, or data analysis directly
- Storing or persisting data between sessions
- Building or rendering a UI
- Handling authentication or external API credentials

---

## 3. User Story

> As a user, I submit a research or analysis task in natural language.  
> The CEO Agent breaks it down, decides which agents to activate and in what order, runs them, and returns a synthesized final answer — keeping me informed at every step.

**Example flow:**

```
User: "Compare the market size of the AI agent space in 2023 vs 2025 and identify the top 3 players."

CEO → decides to call: [WebResearcher, DataAnalyst, ReportWriter]
CEO → runs WebResearcher    → "🔄 מפעיל WebResearcher..."  → "✅ WebResearcher סיים"
CEO → runs DataAnalyst      → "🔄 מפעיל DataAnalyst..."   → "✅ DataAnalyst סיים"
CEO → runs ReportWriter     → "🔄 מפעיל ReportWriter..."  → "✅ ReportWriter סיים"
CEO → synthesizes → returns final report to user
```

---

## 4. Inputs & Outputs

### Input

```json
{
  "task": "string — the user's request in natural language",
  "context": "string? — optional background or constraints"
}
```

### Output

```json
{
  "summary": "string — final synthesized answer for the user",
  "agent_results": [
    {
      "agent_name": "string",
      "status": "success | failed | skipped",
      "output": "string",
      "duration_ms": "number"
    }
  ],
  "steps_taken": [
    {
      "step": "number",
      "action": "string",
      "rationale": "string"
    }
  ]
}
```

---

## 5. Decision Logic (Routing)

### Step 1 — Task Analysis
The CEO sends the user task to the Claude API with a system prompt containing:
- The full task description
- A registry of available sub-agents with their names, descriptions, and capabilities
- An instruction to produce a structured **execution plan** as JSON

### Step 2 — Execution Plan
The LLM returns an execution plan:

```json
{
  "plan": [
    {
      "step": 1,
      "agent": "WebResearcher",
      "sub_task": "Find market size data for AI agents 2023 and 2025",
      "depends_on": [],
      "run_parallel_with": []
    },
    {
      "step": 2,
      "agent": "DataAnalyst",
      "sub_task": "Analyze and compare the data",
      "depends_on": [1],
      "run_parallel_with": []
    }
  ],
  "rationale": "string — why this plan was chosen"
}
```

### Step 3 — Adaptive Re-evaluation
After each sub-agent completes, the CEO re-evaluates: if output is unexpected or insufficient, the plan may be revised (call an additional agent, retry, or skip remaining steps).

---

## 6. Sub-Agent Interface Contract

Every sub-agent in the system **must** implement the following interface:

```python
# Python (tentative — final language TBD)
def run(sub_task: SubTask) -> AgentResult:
    ...
```

```typescript
// TypeScript (tentative — final language TBD)
async function run(subTask: SubTask): Promise<AgentResult>
```

### Types

```
SubTask {
  task_id: string        # unique ID for this invocation
  description: string    # what to do
  context: string        # relevant context from prior agents
}

AgentResult {
  agent_name: string
  status: "success" | "failed" | "skipped"
  output: string
  duration_ms: number
  error?: string
}
```

### Agent Registry

A central `AGENT_REGISTRY` in `src/utils/` maps agent names to their implementations:

```python
AGENT_REGISTRY = {
    "TBD_Agent_1": agent_1.run,
    "TBD_Agent_2": agent_2.run,
    "TBD_Agent_3": agent_3.run,
    "TBD_Agent_4": agent_4.run,
}
```

The 4 sub-agent slots will be defined in future sessions.

---

## 7. Real-Time Reporting Protocol

The CEO streams progress to the user throughout execution:

| Event | Message |
|-------|---------|
| Plan created | `"📋 תוכנית ביצוע: [N] שלבים — [rationale]"` |
| Agent starting | `"🔄 מפעיל [agent_name]: [sub_task description]..."` |
| Agent succeeded | `"✅ [agent_name] סיים — [one-line summary of output]"` |
| Agent failed | `"❌ [agent_name] נכשל — [error]. מחליט אם להמשיך..."` |
| Final output | Full synthesized response |

---

## 8. Error Handling

| Scenario | CEO Behavior |
|----------|-------------|
| Sub-agent returns `status: "failed"` | CEO re-evaluates: retry once / skip / abort all |
| All retries exhausted | CEO returns partial results + explains what failed |
| Claude API timeout | Retry with exponential backoff (max 3 attempts) |
| No sub-agent can handle task | CEO responds directly with explanation |

All errors are reported to the user in real-time (not silently swallowed).

---

## 9. `ceo_agent.md` Spec (Claude Code Sub-Agent Definition)

The file `.Claude/agents/ceo_agent.md` defines how Claude Code invokes the CEO Agent:

```
---
name: CEO Agent
description: Use this agent for ALL tasks. It is the main orchestrator that routes work to the appropriate sub-agents. Always invoke it first.
tools: Task, Read, Write, Bash
---

You are the CEO Agent — the central orchestrator of The Five Agents system.

[full system prompt — see .Claude/agents/ceo_agent.md]
```

CLAUDE.md references the CEO Agent as the **mandatory first step** for any task in this repository.

---

## 10. Open Questions

- What are the 4 sub-agent names and their specific capabilities? _(to be defined in next session)_
- Final language choice: Python or TypeScript?
- Should execution plans be saved to `data/` for auditing/debugging?
- Maximum concurrent sub-agents when running in parallel?
- Should the CEO have a memory/context layer between tasks (stateful vs stateless)?
