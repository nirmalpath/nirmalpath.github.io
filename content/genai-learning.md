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
    1. Auto regressive (text): Generates the next piece of data by looking at previously generated data sequentially.
        - Next token sequentially
        - Exmaples
          - GPT / LLaMA / Claude
        - Uses
          - Chatbots / Codegen / QnA / Agents
        - Pros
          - Produces coherent, natural sequences / Handles long context well / flexible (text, code, audio)
        - Cons
          - Slow generation / errors can compound / hard to revise past outputs
    2. Autoencoder: Compress data n then reconstruct it back. For example, zip file to unzip.
        - Parts
          1. Encoder: converts input to compressed representation, captures essence of data
          2. Latent space (bottleneck): small vector representation, forces model to learn meaningful structures
          3. Decoder: Reconstruct original from compressed
        - Types
          1. Basic: (compress n reconstruct / use for feature learning)
          2. Denoising: (input is noisy / image cleanup)
          3. Variation (VAE): most relevant in GenAI, used in combination with Stable Diffusion. Examples: generate new faces, images, text embeddings
              - Probabilistic latent variable
              - Uses: Representational learning / Controlled generation  
    3. Diffusion (image/video): Starts from pure noise and iteratively cleans it.
        - Gradually de-noise into structure image
        - Processes:
          - Forward (training): take real data, gradually add noise till it becomes completely random noise.
          - Reverse (generation): Start with random noise, remove and reconstruct a relistic sample
        - Examples: Stable diffusion / DALL-E
        - Uses: Text to image / Image editing / Design gen / video-audio generation
        - Pros: high quality, realistic output / stable compared to GANs 
        - Cons: Slow generation / expensive computationally / less natural for text compared to autoregressive models
    4. GANs (Generative Adversarial Network generates data thru competition between 2 NN / older GenAI, replaced by diffusion models)
        - Generator (creates fake data) vs discriminator (tries to detect if real or fake). Based on feedback, they improve together. Mathematically, this is minimax game
        - Example
          - Adversarial network
        - Uses: Synthetic data for augmentation / Deep fake / Image gen
        - Pros: sharp n realistic images, fast generation
        - Cons: Training is unstable / mode collapse / hard to tune

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
