# Native Inference-Time Compute Era

## Overview
The Native Inference-Time Compute Era represents the internalization of search and self-correction directly within the model's parameters and reinforcement learning loops. Popularized by models like OpenAI's o1/o3 and DeepSeek-R1, search happens natively in hidden reasoning tokens.

## Architecture & Flow
```mermaid
graph TD
    Query[User Query] --> InternalRL[Hidden RL Search Loop]
    subgraph Model Internals (RL)
        InternalRL --> Policy[Generate Reason Tokens]
        Policy --> Value[Evaluate Reasoning Path]
        Value -->|Self-Correction| Policy
    end
    InternalRL --> FinalOutput[Final User-Facing Output]
```

## Key Attributes
- **Hidden Reasoning Tokens**: Backtracking and self-correction occur within the model before outputting the final answer.
- **Reinforcement Learning**: Trained via RL to optimize test-time compute.
- **Zero API Overhead**: No external program is needed to guide the search.

## Limitations
- **Invisible Reasoning**: The exact search trace is often hidden from users.
- **High Resource Requirements**: Training and running inference-time search is computationally expensive.
