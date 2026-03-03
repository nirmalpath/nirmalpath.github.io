# LLM Evaluation Framework

## Core Metrics

- Accuracy
- Faithfulness
- Latency
- Cost per 1K tokens

## Example Code

```python
def evaluate(model, dataset):
    return model.score(dataset)
