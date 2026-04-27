# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

**The Five Agents** — a masterclass project demonstrating multi-agent architecture using the Anthropic Claude API.

## Directory Structure

```
the-five-agents/
├── src/
│   ├── agents/     # Agent definitions — each file is one agent
│   ├── tools/      # Tool functions available to agents
│   ├── skills/     # Reusable skills that agents can invoke
│   └── utils/      # Shared utilities (API client, helpers)
├── data/           # Input/output data for agent runs
└── CLAUDE.md
```

## Ohad (CEO Agent) — Single Entry Point

**For every task in this repository, always invoke Ohad first.**

Ohad is the CEO Agent — the central orchestrator of the system. He receives the task, decides which sub-agents to activate, runs them (sequentially or in parallel), and synthesizes the results.

- Definition: `.Claude/agents/ceo_agent.md`
- PRD: `docs/PRD-ceo-agent.md`

**Never bypass Ohad to call a sub-agent directly.**

## Architecture

The system follows an orchestrator pattern:

```
User → CEO Agent → [Sub-Agent 1, Sub-Agent 2, Sub-Agent 3, Sub-Agent 4]
                         ↓
                  Synthesized Result → User
```

- The CEO Agent uses LLM reasoning (not hardcoded rules) to route tasks
- Sub-agents are defined in `src/agents/` — one file per agent
- Sub-agents report back to the CEO, which relays progress to the user in real-time
- The 4 sub-agents are TBD — to be defined in upcoming sessions

## Environment Variables

```
ANTHROPIC_API_KEY=   # Required — get from console.anthropic.com
```
