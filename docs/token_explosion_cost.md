# Token Explosion & Cost Multiplier

## Overview
One of the primary challenges in Tree-of-Thoughts is the exponential growth of token usage. Generating and evaluating multiple branches causes API billing and rate limits to saturate quickly.

## Architecture & Flow
```mermaid
graph TD
    Start[Query] --> Root[Root]
    Root --> Branch1[Branch 1]
    Root --> Branch2[Branch 2]
    Branch1 --> B1_1[Sub-branch]
    Branch1 --> B1_2[Sub-branch]
    Branch2 --> B2_1[Sub-branch]
    Branch2 --> B2_2[Sub-branch]
    style Branch1 fill:#ffb3b3
    style Branch2 fill:#ffb3b3
    style B1_1 fill:#ff8080
    style B1_2 fill:#ff8080
    style B2_1 fill:#ff8080
    style B2_2 fill:#ff8080
```

## Mitigations
- **Pruning Rules**: Drop unpromising nodes early (e.g., Alpha-Beta pruning).
- **Beam Width Limits**: Limit search width strictly to the top-$k$ nodes.
- **Caching**: Reuse previous prompt prefixes to save prompt evaluation tokens.
