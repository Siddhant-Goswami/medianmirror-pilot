---
mentee_id: arjun
status: draft
version: 2
declared_position:
  background: 3y backend, no ML
  goal: ship an AI agent at work
  hours_per_week: 10
declared_at: '2026-04-24'
milestones:
- id: m1
  title: Working single-agent with tool use and memory
  target_week: 2
  status: not_started
- id: m2
  title: Multi-agent pipeline running on a real use case
  target_week: 4
  status: not_started
- id: m3
  title: Agent with passing evals and guardrails
  target_week: 6
  status: not_started
- id: m4
  title: Shipped agent in a real environment with real user
  target_week: 8
  status: not_started
drafted_at: '2026-04-24'
approved_at: '2026-03-20'
---

# Arjun's AI Agents Roadmap
**Goal:** Ship a production-ready AI agent at work
**Background:** 3 years backend engineering, no ML
**Pace:** 10 hours/week
**Current Week:** 6

---

## Phase 1: Agent Foundations (Weeks 1–2)
*Why before what — understand what makes an agent different from a chatbot.*

### Week 1: What Is an Agent, Really?
- **Concept:** The ReAct loop — Reason, Act, Observe. Why LLMs alone are not agents.
- **Read:** OpenAI Agents SDK overview, LangChain agent docs intro
- **Build:** Run a simple tool-calling agent locally (weather lookup or calculator tool)
- **Reflection prompt:** Where in your current backend system could an agent replace a hardcoded workflow?

### Week 2: Tools, Memory, and State
- **Concept:** Tool calling anatomy (function schemas, JSON responses). Short-term vs long-term memory patterns.
- **Build:** Agent with 2-3 tools + conversation memory (in-memory dict, then Redis)
- **Milestone M1:** Working single-agent with tool use and memory

---

## Phase 2: Multi-Agent Patterns (Weeks 3–4)
*One agent is a prototype. A system of agents is a product.*

### Week 3: Manager Pattern
- **Concept:** Orchestrator-worker architecture. When to split responsibilities.
- **Build:** Manager agent that delegates to specialist sub-agents (e.g. research agent + writer agent)
- **Study:** LangGraph StateGraph for managing agent state across nodes

### Week 4: Handoff Pattern
- **Concept:** Sequential handoff vs parallel fan-out. Tracing and debugging multi-agent flows.
- **Build:** Two-agent pipeline with handoff — agent A produces structured output, agent B consumes it
- **Milestone M2:** Multi-agent pipeline running end-to-end on a real work-adjacent use case

---

## Phase 3: Guardrails, Evals, and Reliability (Weeks 5–6)
*A demo that breaks in prod is not shipped.*

### Week 5: Guardrails
- **Concept:** Input validation, output validation, hallucination containment strategies
- **Build:** Add input/output guardrails to your agent using Pydantic + custom validators
- **Study:** OpenAI's guardrails patterns, Anthropic's responsible scaling approach

### Week 6: Evaluations
- **Concept:** How to eval non-deterministic systems. LLM-as-judge. Unit tests for agents.
- **Build:** Write 5 eval cases for your agent. Automate them in CI.
- **Milestone M3:** Agent with passing evals + guardrails — ready for internal demo

---

## Phase 4: Ship It (Weeks 7–8)
*From demo to deployed.*

### Week 7: Production Packaging
- **Concept:** Async agent execution, streaming responses, cost + latency tracking
- **Build:** Wrap your agent in a FastAPI endpoint. Add logging (LangSmith or simple structured logs).
- **Study:** Deployment patterns — serverless vs persistent worker vs queue-based

### Week 8: Capstone Ship
- **Build:** Deploy your agent to a real environment (internal tool, Slack bot, or API endpoint)
- **Present:** 10-min demo walkthrough — problem, architecture, what broke, what you'd do next
- **Milestone M4 (Final):** Shipped agent running in a real context with at least one real user

---

## Weekly Rhythm
| Day | Activity |
|-----|----------|
| Mon | Read + concept (1.5 hrs) |
| Wed | Build session (3 hrs) |
| Fri | Reflect + log progress (30 min) |
| Weekend | Buffer / catch-up (optional 2 hrs) |

---

## Stack Recommendations (Backend-friendly)
- **Framework:** LangGraph (state machines feel like backend code)
- **LLM:** OpenAI GPT-4o or Anthropic Claude via API
- **Memory:** Redis for short-term, Supabase/Postgres for long-term
- **Evals:** Pytest + LLM-as-judge prompt
- **Deploy:** Railway or Render for quick deploys, AWS Lambda for scale

---

## North Star Check
Before every session, ask: *"Does what I'm building today move me closer to an agent I could demo to my team next week?"* If not, cut scope.
