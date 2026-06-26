# Heuristic Value Scoring

## Overview
Heuristic Value Scoring evaluates thoughts in isolation. The LLM acts as an evaluator, assigning a classification (e.g., `[sure]`, `[likely]`, or `[impossible]`) or a scalar score to a single thought node.

## Architecture & Flow
```mermaid
graph TD
    Thought[Thought Node] --> Scorer[LLM Scorer Prompt]
    Scorer --> Classify{Classification}
    Classify -->|sure / high score| Keep[Keep & Explore]
    Classify -->|maybe / mid score| Keep
    Classify -->|impossible / low score| Prune[Prune / Backtrack]
```

## Key Attributes
- **Isolated Evaluation**: Evaluates thoughts independently of other candidates.
- **Early Pruning**: Instantly identifies dead-ends (`[impossible]`) to save compute.

## Limitations
- **Strict Thresholds**: Hard to calibrate scalar thresholds across different domains.
