# Depth-First Search (DFS) ToT

## Overview
Depth-First Search (DFS) in Tree-of-Thoughts explores a single reasoning branch as deeply as possible. If the path's valuation falls below a threshold, the engine prunes the branch and backtracks to a previous node.

## Architecture & Flow
```mermaid
graph TD
    Root[Root Node] --> Node1[Step 1]
    Node1 --> Node2[Step 2 (Low Score)]
    Node2 -.->|Prune & Backtrack| Node1
    Node1 --> Node3[Step 2 - Alt]
    Node3 --> Node4[Step 3 (Success)]
    style Node2 fill:#ffb3b3,stroke:#ff3333
```

## Key Attributes
- **Deep Exploration**: Prioritizes deep logical paths early.
- **Backtracking**: Returns to parent nodes when an evaluation fails.
- **Memory Efficient**: Only stores the current active branch and its immediate alternatives.

## Limitations
- **Risk of Getting Stuck**: Can waste time exploring deep but ultimately futile paths if heuristics are poor.
