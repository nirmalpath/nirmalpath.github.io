# LLM Evaluation Framework

## Core Metrics

- Accuracy
- Faithfulness
- Latency
- Cost per 1K tokens
- Test

## Example Code

```python
def evaluate(model, dataset):
    return model.score(dataset)


graph LR
User --> LLM
LLM --> Retriever
Retriever --> VectorDB
VectorDB --> Retriever

