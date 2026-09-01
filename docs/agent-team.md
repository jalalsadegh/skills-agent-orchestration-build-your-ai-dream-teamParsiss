# Agent team

For Mona's Project Pulse dashboard, I will use a four-agent custom team orchestrated with GitHub Copilot CLI in a Codespace.

- Planner — Model: Claude Opus 4.7 (copilot). Responsibility: research the codebase and dependencies, identify edge cases, and produce a clear implementation plan. Definition: `.github/agents/planner.agent.md`.
- Orchestrator — Model: Claude Opus 4.7 (copilot). Responsibility: break the plan into phases, delegate work to specialists, manage sequencing, and verify the integrated result. Definition: `.github/agents/orchestrator.agent.md`.
- Designer — Model: Gemini 3.1 Pro (copilot). Responsibility: handle dashboard UX, accessibility, information hierarchy, responsive layout, and visual polish. Definition: `.github/agents/designer.agent.md`.
- Coder — Model: GPT-5.5 (copilot). Responsibility: implement the assigned code, fix bugs, and validate behavior within the orchestrated file scope. Definition: `.github/agents/coder.agent.md`.

The Orchestrator will coordinate the Planner, Designer, and Coder agents through GitHub Copilot CLI in the Codespace so the dashboard work stays structured and parallelized where appropriate.
