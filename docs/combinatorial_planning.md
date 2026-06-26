# Complex Combinatorial Planning & Scheduling

## Overview
Combinatorial planning and scheduling tasks (e.g., airline fleet routing, shift scheduling) feature huge search spaces where early decisions heavily restrict downstream options. ToT solves these by branching and backtracking when constraints are violated.

## Architecture & Flow
```mermaid
graph TD
    Start[Goal: Route Fleet] --> Assign1[Assign Flight 1]
    Assign1 --> Assign2_A[Assign Flight 2 Option A]
    Assign1 --> Assign2_B[Assign Flight 2 Option B]
    Assign2_A --> Assign3_A[Assign Flight 3 (Constraint Violation!)] -.->|Backtrack| Assign1
    Assign2_B --> Assign3_B[Assign Flight 3 (Success)]
    style Assign3_A fill:#ffb3b3
```

## Key Attributes
- **Constraint Handling**: Evaluates feasibility of intermediate states.
- **Global Optimization**: Navigates non-linear paths to find valid global schedules.
