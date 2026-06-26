# Independent Node Voting

## Overview
Independent Node Voting is a thought evaluation strategy where the LLM acts as its own jury. Given a set of generated candidate thoughts, a separate prompt pass is executed to vote on the most logical candidate.

## Architecture & Flow
```mermaid
graph TD
    Candidates[Candidate Thoughts A, B, C] --> Jury[LLM Voter Prompt]
    Jury -->|Vote A: 10%| Result[Discard]
    Jury -->|Vote B: 70%| Best[Selected Candidate]
    Jury -->|Vote C: 20%| Result
```

## Key Attributes
- **Comparative Analysis**: The LLM compares candidate thoughts directly against one another.
- **Democratic Selection**: Aggregates preferences over multiple voting runs to increase stability.

## Limitations
- **Intra-Prompt Bias**: The order in which candidates are listed in the voting prompt can bias the model's choices.
