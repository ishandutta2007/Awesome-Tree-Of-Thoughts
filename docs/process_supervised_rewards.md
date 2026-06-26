# Process-Supervised Reward Models (PRMs)

## Overview
Process-Supervised Reward Models (PRMs) score the intermediate steps of a reasoning process rather than just the final outcome. This step-by-step verification significantly reduces logical drift and hallucination.

## Architecture & Flow
```mermaid
graph TD
    Step1[Reasoning Step 1] --> PRM1[PRM Scorer] -->|Score: 0.95| Step2[Reasoning Step 2]
    Step2 --> PRM2[PRM Scorer] -->|Score: 0.88| Step3[Reasoning Step 3]
    Step3 --> PRM3[PRM Scorer] -->|Score: 0.12| Prune[Flag/Prune Step 3]
```

## Key Attributes
- **Fine-Grained Feedback**: Evaluates each logical transition.
- **Reduced Hallucinations**: Catches logical errors immediately when they occur.
- **External Verification**: Often implemented using specialized, highly accurate verifier models.

## Limitations
- **High Labeling Cost**: Training PRMs requires high-quality, step-by-step human annotations.
