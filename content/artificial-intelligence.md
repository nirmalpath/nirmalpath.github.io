# Artificial Intelligence Notes

## Topics
**1. Definition
2. Hierarchy
3. Infra
4. Risks**
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Definition
    - Simulate human intelligence
    
### Hierarchy
    - ML (Un/supervised, Reinforcement)
    - Deep Learning (NN)
    - Gen AI (LLM. Diffusion Models, GANs)
    
### Infra
    - Data Layer (Lake, warehouse)
    - Model Training (GPUs, Distributed training)
    - Deployment (APIs, Containers, Kubernetes)
    
### Risks
    - Challenges
      - Bias
      - Hallucination
      - Data privacy
      - Model drift: Performance worsens over time because real world data has changed when compared to data on which it was trained. For instance, individual preference changes over time, market conditions shift.
          > Types: 
            - Covariate (input data distribution changes / example: fraud patterns change)
            - Concept (input-output relation changes / example: new key words in spam detection)
            - Label (distribution of output label changes / example: customer churn rate increases due to market changes)
      - Security
      
    - Mitigation
      - Guardrails
      - Human in loop
      - Monitoring
          - Performance (accuracy, precision, recall)
          - Data (compare training vs live data distribution)
          - Retraining (with new data)
          - A/B testing before replacing old ones.
      - Policies
