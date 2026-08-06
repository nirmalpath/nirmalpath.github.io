# Mortgages

## Topics

- Architecture
- 
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### Architecture
    That's the architecture — five layers, top to bottom: channels feed an orchestrator that delegates to four specialist agents, backed by a shared data & knowledge layer (document store, vector DB, knowledge graph, rules engine), wired into your core banking/LOS and external APIs, with security and compliance wrapping everything as a cross-cutting concern.
    A few design notes worth calling out:
    •	The orchestrator pattern (vs. a single monolithic agent) matters here because mortgage onboarding has genuinely distinct sub-tasks — document extraction, identity/fraud checks, underwriting math, and regulatory compliance each benefit from focused prompts, different tools, and independent evaluation/monitoring.
    •	The knowledge graph is optional but valuable if you want to model relationships (co-borrowers, property liens, employer verification chains) that a vector DB alone can't capture well — similar to the graph layer in your RAG platform work.
    •	Human-in-the-loop checkpoints aren't drawn explicitly but should sit inside the underwriting and compliance agents — auto-approve within policy bounds, escalate edge cases.
    Now let me put together a detailed project plan as a document you can share with stakeholders.The plan covers the phased build (PoC → pilot in shadow mode → compliance hardening → scaled rollout), team composition, and the key risk that trips up projects like this — over-automating before compliance sign-off catches up.
    Given the RAG/knowledge-graph work you've already built (Pinecone, Neo4j, hybrid retrieval), you're in a good position to reuse a lot of that for the data & knowledge layer here rather than building it from scratch — the policy/guideline vector DB and knowledge graph patterns should transfer almost directly.
    A couple of things worth deciding early, if you want to dig into either:
    •	Whether to run this as build-vs-buy (custom LangGraph-style orchestration vs. a vendor agent platform, given you're in a bank with existing vendor relationships)
    •	What "shadow mode" success criteria should be before you're allowed to flip on any auto-approval, since that's usually the hardest internal sell to compliance/risk



### Typical Architecture
                      +------------------+
                      |   Client Apps    |
                      | Web / Mobile/API |
                      +--------+---------+
                               |
                               v
                      +------------------+
                      |   API Gateway    |
                      +--------+---------+
                               |
          +--------------------+-------------------+
          |                    |                   |
          v                    v                   v
    +---------------+   +---------------+   +---------------+
    | User Service  |   | Order Service |   | Product Svc   |
    +-------+-------+   +-------+-------+   +-------+-------+
            |                   |                   |
            v                   v                   v
     +------------+      +------------+      +------------+
     | User DB    |      | Order DB   |      | Product DB |
     +------------+      +------------+      +------------+

        <---- Event Bus / Message Broker ---->
