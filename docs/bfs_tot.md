# Breadth-First Search (BFS) ToT

## Overview
Breadth-First Search (BFS) in Tree-of-Thoughts explores all potential reasoning thoughts at the current layer depth before moving deeper down the reasoning tree.

## Architecture & Flow
```mermaid
graph TD
    Root[Initial State] --> L1_A[Thought L1-A]
    Root --> L1_B[Thought L1-B]
    L1_A --> L2_A1[Thought L2-A1]
    L1_A --> L2_A2[Thought L2-A2]
    L1_B --> L2_B1[Thought L2-B1]
    L1_B --> L2_B2[Thought L2-B2]
    style Root fill:#f9f,stroke:#333,stroke-width:2px
    style L1_A fill:#bbf,stroke:#333,stroke-width:2px
    style L1_B fill:#bbf,stroke:#333,stroke-width:2px
```

## Key Attributes
- **Layer-by-Layer Evaluation**: Assesses all options at depth $d$ before proceeding to $d+1$.
- **Beam Search Integration**: Typically uses a beam width to keep only the top-$k$ thoughts per layer.
- **Global Planning**: Suitable for tasks where global horizon decisions matter (e.g., creative writing, scheduling).

## Limitations
- **High Initial Latency**: Must wait for all nodes at the current level to be generated and evaluated.
