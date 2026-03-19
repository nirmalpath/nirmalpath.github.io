# GenAI Notes

## Topics
- What
- Model Types
- Transformer Architecture
- Training Pipeline
- Key Techniques
- Inference Controls
- Hallucination
- Evaluation
- Cost Optimization
- Risks
- Enterprise GenAI Architecture
- Advanced Topics
- When not to use

### What
- New content
- Learn P(data) or P(O/input)
  
### Model Types
- Auto regressive (text)
    - Next token sequentially
    - Exmaples
      - GPT
      - LLaMA
      - Claude
    - Uses
      - Chatbots
      - Codegen
      - QnA
      - Agents
- Diffusion (image/video)
    - Gradually de-noise into structure image
    - Examples
      - Stable diffusion
      - DALL-E
    - Uses
      - Text to image
      - Image editing
      - Design gen
- GANs (older GenAI)
    - Generator vs discriminator
    - Example
      - Adversarial network
    - Uses
      - Synthetic data
      - Deep fake
- VAEs
    - Probabilistic latent variable
    - Uses
      - Representational learning
      - Controlled generation

### Transformer Architecture (text gen core)
- Components
    - Self attention
    - Multi head
    - Feed forward layer
    - Layer norm
    - Residual connections

### Training Pipeline
- Pre-training
    - Internet scale data
    - Self-supervised learning
- Fine tuning
    - Instruction
    - Domain
- Alignment
    - RLHF
    - Constitutional AI
### Key Techniques
- Prompt
    - Zero shot
    - Few shot
    - Chain of thought
    - Role prompting
    - Structure output prompting
- RAG
    - External knowledge via vector db
- Tool calling
    - Query API's
    - Run code
    - Access databases
- Agents
    - Iterative reasoning + action loop
### Inference Controls
- Temp
    - Creativity
- Top-k
    - Limit candidates
- Top-p
    - Nucleus sampling
- Max Tokens
    - Lenght
- Presence Penalty
    - Reduce repetition
      
### Hallucination
- Why
    - Probabilistic gen
    - Weak context
    - Ambigous prompts
      
- Mitigation
    - RAG
    - Guardrails
    - Output validation
    - Lower temp
    - Constrained decoding
      
### Evaluation
- Automatic
    - BLEU
    - ROUGE
    - Perplexity
    - Exact match
- Human
    - Helpfullness
    - Coherence
    - Safety
    - Factuality
- Enterprise
    - Cost per request
    - Latency
    - Task completion rate
  
### Cost Optimization
- Smaller Models
- Prompt compressor
- Cache embeddings
- Batch inference
- Quantization

### Risks
- Hallucination
- Prompt Injection
- Data Leakage
- Bias
- Copyright Risk
- Over Automation

### Enterprise GenAI Architecture
- User
- API gateway
- Orchestrator
- LLM
- Tool Layer
- Data systems
- Controls
    - RBAC
    - Audit logging
    - Cost Monitoring
    - Rate limiting
    - Human in loop
      
### Advanced Topics
- Mix of experts
- Long context model
- Multi-modal LLM
- Speculative Decoding
- Self-improvement agents
- Synthetic Data Gen

### When not to use
- Deterministic
- Strict compliance
- Real-time
- Tranditional ML works better
