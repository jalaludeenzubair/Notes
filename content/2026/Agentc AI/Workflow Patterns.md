**Orchestrator-Worker Architecture**

Orchestrator: Decides what needs to run, in what order, and which worker handles it.
Workers: Execute tasks (LLM calls, tool calls, validations, post-processing).

```
User Input
↓
Orchestrator
├─ Routing Decision
│      ├─ Worker 1 → Output
│      ├─ Worker 2 → Output
│      └─ Worker 3 → Output
↓
Aggregator / Post-Processor
↓
Final Output
```

**Routing**

A decision layer that determines which model, prompt, tool, or pipeline should handle the request.

```
User Input
↓
Router (LLM or Rule-based)
↓
Decision
↓
Selected Pipeline
↓
Final Output
```

**Parallelization**

Running multiple LLM calls (or reasoning steps) simultaneously instead of sequentially to reduce latency and increase throughput.

```
User Input
↓
Task Decomposition
↓
Parallel LLM Calls
↓
Aggregator / Merger
↓
Final Output
```

**Evaluator–Optimizer Pattern**

A closed-loop system that constantly measures output quality and adjusts prompts, chains, or routing to improve results.

```
User Input
↓
Orchestrator
↓
Workers → Parallel / Chained
↓
Evaluator → Feedback Scores
↓
Optimizer → Adjust Prompts / Chains / Routing
↓
Optional Re-run of Workers
↓
Final Output
```
