# Mona's Project Pulse agent team

I will use GitHub Copilot CLI in a Codespace to orchestrate this custom agent team and build the Project Pulse dashboard.

| Agent | Model | Responsibility | Definition |
|---|---|---|---|
| Orchestrator | Claude Opus 5.5 (copilot) | Coordinates the work, delegates tasks to specialists with clear file scopes, integrates their results, and reports the outcome. | `.github/agents/orchestrator.agent.md` |
| Planner | Claude Opus 5.5 (copilot) | Researches the project and creates an implementation plan with ordered steps, file assignments, dependencies, parallel work, edge cases, and validation expectations. | `.github/agents/planner.agent.md` |
| Designer | Gemini 3.7 Flash (copilot) | Guides the dashboard's usability, accessibility, information hierarchy, responsive behavior, and visual design. | `.github/agents/designer.agent.md` |
| Coder | GPT-5.5 (copilot) | Implements the assigned app files and support configuration, keeping the result clear, deterministic, and validated. | `.github/agents/coder.agent.md` |

The Orchestrator will first ask the Planner for an implementation plan. It will then coordinate the Designer and Coder, assigning non-overlapping work that can proceed in parallel and sequencing work with dependencies. Finally, the Orchestrator will verify the integrated Project Pulse dashboard and report the result.
