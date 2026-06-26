# High Time-to-First-Token (TTFT) Latency

## Overview
Running multiple verification passes and parallel thought generations introduces high Time-to-First-Token (TTFT) and completion latencies, impacting the user experience.

## Architecture & Flow
```mermaid
graph TD
    User[User] --> Request[Request]
    subgraph Sequential Search (Slow)
        Request --> Gen1[Generate Thought 1] --> Eval1[Evaluate] --> Gen2[Generate Thought 2] --> Final
    end
    subgraph Speculative & Parallel (Fast)
        Request --> SpecGen[Speculative Draft Generation]
        SpecGen --> Verify[Parallel Verification] --> Final
    end
```

## Mitigations
- **Speculative Decoding**: Use smaller draft models to speculate thoughts and verify them in parallel.
- **Parallel Workers**: Run concurrent node generations on distributed GPUs.
- **Streaming Nodes**: Stream intermediate thoughts to the user as they are generated.
