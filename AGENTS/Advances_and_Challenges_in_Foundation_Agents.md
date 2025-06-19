---
created: 2025-04-05 05:31:26
author: Cong Le
version: "1.0"
license(s): MIT, CC BY 4.0
copyright: Copyright (c) 2025 Cong Le. All Rights Reserved.
original source: "https://github.com/FoundationAgents/awesome-foundation-agents/blob/main/assets/Advances%20and%20Challenges%20in%20Foundation%20Agents.pdf"
---



# Advances and Challenges in Foundation Agents
> **Disclaimer:**
>
> This document contains my personal notes on the topic,
> compiled from publicly available documentation and various cited sources.
> The materials are intended for educational purposes, personal study, and reference.
> The content is dual-licensed:
> 1. **MIT License:** Applies to all code implementations (Swift, Mermaid, and other programming languages).
> 2. **Creative Commons Attribution 4.0 International License (CC BY 4.0):** Applies to all non-code content, including text, explanations, diagrams, and illustrations.
---


##  Diagrammatic Guide 



```mermaid
---
title: "Advances and Challenges in Foundation Agents"
author: "Cong Le"
version: "1.0"
license(s): "MIT, CC BY 4.0"
copyright: "Copyright (c) 2025 Cong Le. All Rights Reserved."
config:
  theme: dark
---
%%%%%%%% Mermaid version v11.4.1-b.14
%%{
  init: {
    'themeVariables': {
      'fontSize': '16px',
      'fontFamily': 'Bradley Hand'
    }
  }
}%%
mindmap
  root((Foundation Agents Survey))
    (Introduction - Ch 1)
      ::icon(fa fa-book)
      ("Definition:<br/>AI Agents")
        ("Systems perceiving, deciding, acting autonomously")
        ("Evolution:<br/>Symbolic -> ML -> LLM-based")
        ("LLM Impact:<br/>Enhanced reasoning, adaptability")
      ("Human Brain vs. AI Agents")
        ("Hardware:<br/Bio (20W) vs Silicon (kWs)")
        ("Consciousness/Emotion: <br/Subjective vs Simulated")
        ("Learning: <br/>Continuous/Interactive vs Batch/Static")
        ("Creativity:<br/>Experiential vs Statistical")
        ("Brain Parallels<br/(L1/L2/L3 AI Levels)")
          ("Frontal:<br/>Planning(L2), Self-awareness(L3)")
          ("Parietal:<br/>Spatial(L2), Tactile(L3)")
          ("Occipital:<br/>Vision(L1), Scene Understanding(L2)")
          ("Temporal:<br/>Language(L1), Episodic Memory(L2)")
          ("Cerebellum:<br/Motor(L2), Cognitive Timing(L3)")
          ("Brainstem:<br/>Reflexes(L1), Autonomic(L3)")
          ("Limbic:<br/>Reward(L2), Emotion/Empathy(L3)")
      ("Modular Brain-Inspired Framework")
        ::icon(fa fa-brain)
        ("Perception-Cognition-Action Loop")
          ("Notation:<br/>W, S, O, A, M, L, R, C, T, E")
          ("Mental State (M):<br/>M_mem, M_wm, M_emo, M_goal, M_rew")
          ("Cognition (C):<br/>Learning (L) + Reasoning (R)")
          ("Internal Actions:<br/>Planning, Decision-making")
        ("Foundation Agent Definition")
          ("Pillars:<br/Sustained Autonomy, Adaptive Learning, Purposeful Reasoning")
          ("Capabilities:<br/>Active Perception, Dynamic Cognition, Autonomous Reasoning, Purposeful Action, Collaboration")
        ("Connections:<br/>Society of Mind, Inside-Out, Active Inference, POMDP Generalization")

    ("Part I:<br/>Core Components")
      ::icon(fa fa-cogs)
      ("Cognition - Ch 2")
        ::icon(fa fa-lightbulb)
        (Learning)
          (Learning Space)
            ("Full Mental State (Model θ): Pre-training, SFT, PEFT, RLHF, DPO, ReFT")
            ("Partial Mental State (M components): ICL, Memory updates (Generative Agents, Voyager), Reward/World Model updates (ARMAP, ActRe)")
          (Learning Objective)
            ("Better Perception: Multimodal (CLIP, LLaVA), Retrieval (RAG, R1-Searcher)")
            ("Better Reasoning: Quality Data (LIMO), Feedback (STaR, ReST), RL (DeepSeek R1)")
            ("World Understanding: Experience Accumulation (Inner Monologue, Voyager), Reflection (Self-refine, Critic), Reward Opt. (Text2Reward), World Models (RAP, ActRe)")
        ("Reasoning (R(Mt) -> at)")
          ("Structured Reasoning (Rs)")
            ("Dynamic Structures: Linear (ReAct), Tree (ToT, LATS), Graph (GoT, PoT)")
            ("Static Structures: Ensemble (Self-Consistency), Progressive Improvement (Self-Refine, Reflexion), Error Correction (CoVe, Critic)")
            ("Domain-Specific: Math (MathPrompter), Physics (Physics Reasoner)")
          ("Unstructured Reasoning (Ru)")
            (Prompting-Based: CoT variants, Step-Back, CoK)
            (Reasoning Models: DeepSeek R1, Claude 3.7, o-series)
            ("Implicit Reasoning: Quiet-STaR, Coconut")
          ("Planning (Special Reasoning)")
            ("Generating action sequences: S0 -> {a1..an} -> Sg")
            ("Addressing LLM limits: Task Decomposition, Search, World Knowledge Integration (LLM+P, RAP)")

      (Memory - Ch 3)
        ::icon(fa fa-database)
        (Human Memory Overview)
          ("Types: Sensory, Short-Term/Working, Long-Term (Declarative[Semantic, Episodic], Non-Declarative[Procedural, Priming])")
          (Models: Multi-Store, Working Memory, SPI, GWT/LIDA, ACT-R)
        (Agent Memory Representation)
          ("Sensory Memory: Input encoding, Attention, Transient store (RecAgent)")
          ("Short-Term Memory: Context (MemGPT), Working (Generative Agents, Reflexion)")
          ("Long-Term Memory: Explicit (Semantic/Episodic - Agent S), Implicit (Procedural - AAG, Cradle)")
        ("Memory Lifecycle")
          ("Retention: Acquisition, Encoding (Attention, Fusion), Derivation (Reflection, Summarization, Distillation, Forgetting)")
          ("Retrieval: Matching (Indexing, Similarity), Neural Memory Networks (Hopfield, NTMs, Parameter Integration), Utilization (RAG, Long-Context, Hallucination Mitigation)")

      (World Model - Ch 4)
        ::icon(fa fa-globe)
        ("Human World Model: Predictive, Integrative, Adaptive, Multi-scale mental models")
        ("AI World Model Paradigms")
          ("Implicit: Single NN encodes dynamics<br/>(World Models '18, LLMs as simulators)")
          ("Explicit: Factorized Tθ, Oθ<br/>(MuZero, Dreamer, Diffusion WM)")
          ("Simulator-Based: External simulator/real world<br/>(SAPIEN, Daydreamer)")
          ("Hybrid/Instruction-Driven: Blend approaches, symbolic knowledge<br/>(AutoManual, COAT)")
        ("Relationships: Interacts with Memory, Perception, Action")

      (Reward - Ch 5)
        ::icon(fa fa-trophy)
        ("Human Reward Pathways: Dopamine circuits<br/>(Mesolimbic, Mesocortical)")
        ("AI Reward Paradigms: r(s, a), Maximize Gt")
          ("Extrinsic: Dense (InstructGPT), Sparse (SimPO), Delayed (CPO), Adaptive (SPO)")
          ("Intrinsic: Curiosity, Diversity, Competence, Exploration, Information Gain")
          ("Hybrid: Combine Intrinsic & Extrinsic")
          ("Hierarchical: Layered subgoals (TDPO)")
        ("Interactions: Modulates Perception, Emotion (style), Memory")
        ("Challenges: Sparsity, Hacking, Shaping, Multi-objective, Misspecification")

      (Emotion Modeling - Ch 6)
        ::icon(fa fa-smile)
        ("Psychological Foundations:<br/>Categorical (Ekman), Dimensional (Circumplex), Hybrid (Plutchik), Componential (OCC), Neurocognitive (Damasio, LeDoux)")
        ("Incorporating in AI: EmotionPrompt, Emotion-LLaMA (Multimodal)")
        ("Understanding Human Emotions: Textual (CoT), Multimodal, Specialized frameworks, Benchmarks (EmoBench)")
        ("Analyzing AI Emotions: Personality tests (validity debated), Psychometric methods, Cognitive modeling")
        ("Manipulating AI Emotions: Prompts (personas), Training (fine-tuning), Neuron manipulation")
        ("Challenges: Mimicry vs Experience, Manipulation, Alignment, Ethics")

      (Perception - Ch 7)
        ::icon(fa fa-eye)
        ("Human vs AI:<br/>Diverse human senses vs Engineered sensors, Efficiency difference, Multimodal integration challenge for AI")
        ("Perception Representation Types")
          ("Unimodal:<br/>Text (BERT), Image (ResNet, DETR), Video (ViViT), Audio (wav2vec 2.0)")
          ("Cross-modal:<br/>Text-Image (CLIP), Text-Video (VideoCLIP), Text-Audio (AudioCLIP)")
          ("Multimodal:<br/>VLM (LLaVA), VLA (RT-1), ALM (SpeechGPT), AVLM (PandaGPT), Others (3D - PointLLM)")
        ("Optimizing Perception:<br/>Model-Level (Fine-tuning), System-Level (Collaboration), External Feedback (Human-in-loop)")

      (Action Systems - Ch 8)
        ::icon(fa fa-running)
        ("Human Action: Mental (reasoning) & Physical (movement)")
        ("Agentic Action Paradigms")
          ("Action Space (A): Language (Text, Code, Chat), Digital (Game, Web, GUI, DB/KG), Physical (Robotics)")
          ("Action Learning: ICL (Prompting, Decomposition, Role-play, Refine), Supervised Training (PT/SFT - RT-family), RL (LLM as environment, Hierarchical RL)")
          ("Tool-Based Action: External assistance")
            ("Tool Types: Language (ToolLLM), Digital (HuggingGPT), Physical (RT-2), Scientific (ChemCrow)")
            ("Tool Learning: Discovery (Retrieval/Generative), Creation (PAL, CREATOR), Usage (Specialization, Integration, Embodiment)")
        ("Action vs Perception Debate: Inside-Out vs Outside-In")

    ("Part II: Self-Evolution")
      ::icon(fa fa-sync-alt)
      (Optimization Spaces - Ch 9)
        ("Prompt Optimization:<br/>Objective Eq (9.1), Evaluation (Sources, Methods, Signals), Optimization Functions (Via Eval/Opt Signals), Metrics")
        ("Workflow Optimization:<br/>Formalism K=(N,E), Objective Eq (9.3), Optimizing Edges (Graph, NN, Code), Optimizing Nodes (M, τ, P, F)")
        ("Tool Optimization:<br/>Learning Usage (Demonstrations, Feedback), Creation (ToolMakers, CREATOR), Evaluation (Benchmarks, Metrics)")
        ("Autonomous Agent Optimization:<br/>Holistic system-wide optimization (ADAS)")
      (LLMs as Optimizers - Ch 10)
        ("Paradigms: Gradient-Based, Zeroth-Order, LLM-Based")
        ("Iterative Approaches: Random Search, Gradient Approximations (TextGrad), Surrogate Modeling (BO - MIPRO)")
        ("Hyperparameters & Meta-Optimization")
        ("Optimization Across Depth & Time")
        ("Theoretical Perspective: ICL, Mechanistic Interpretability, Limits under uncertainty")
      ("Online vs Offline Self-Improvement - Ch 11")
        ("Online:<br/>Real-time feedback, dynamic adaptation<br/>(Reflexion, MetaGPT)")
        ("Offline:<br/>Batch-based, curated data, ensures stability<br/>(RAG integration, Meta-Opt)")
        ("Hybrid:<br/>Combines both for robustness and adaptability")
      ("Scientific Discovery - Ch 12")
        ("Agent Intelligence Measure: KL Divergence $D_K(\theta, M_{mem}^t)$, IQ evolution")
        ("Agent-Knowledge Interactions")
          ("Hypothesis Generation & Testing<br/>(AI Scientist, SciAgents)")
          ("Protocol Planning & Tool Innovation<br/>(Modular workflows, Cloud labs)")
          ("Data Analysis & Implication Derivation<br/>(AlphaGeometry, TAIS)")
        ("Challenges:<br/>Real-world interaction APIs, Complex reasoning limits, Prior knowledge integration")

    ("Part III:<br/>Collaborative Systems")
      ::icon(fa fa-users)
      ("Design of MAS - Ch 13")
        ("Collaboration Goals/Norms Categories")
          ("Strategic Learning:<br/>Game theory, Competition/Cooperation<br/>(Econ simulations, Social deduction games)")
          ("Modeling & Simulation:<br/>Independent agents, Emergent phenomena<br/>(Agent Hospital, EconAgents, Social dynamics)")
          ("Collaborative Task Solving:<br/>Shared goals, Structured workflows<br/>(MetaGPT, Agent Laboratory)")
        ("Agent Composition:<br/>Homogeneous vs Heterogeneous<br/>(Personas, Observation, Action spaces)")
        ("Interaction Protocols:<br/>Message Types (Structured vs Unstructured), Interfaces (Agent-Env, Agent-Agent, Human-Agent), Next-Gen Protocols (IoA, MCP, ANP, Agora)")
      ("Communication Topology - Ch 14")
        ("Static Topologies:<br/>Layered, Decentralized, Centralized. Predictable but rigid.")
        ("Dynamic Topologies:<br/>Adaptive connectivity (DyLAN, OPTIMA, GPTSwarm). Methods: Search, LLM-gen, External Params. Crucial for social sim (OASIS, Project Sid).")
        ("Scalability:<br/>Communication explosion challenge. Solutions: DAGs, Distributed platforms (AgentScope), Concurrent processing (PIANO), Hybrid architectures.")
      ("Collaboration Paradigms - Ch 15")
        ("Agent-Agent:<br/>Consensus-oriented (Debate, Voting), Collaborative Learning (Experience sharing), Teaching/Mentoring, Task-oriented (Pipelines)")
        ("Human-AI:<br/>Delegation, Multi-turn interaction, Immersive collaboration")
        ("Collaborative Decision-Making:<br/>Dictatorial vs Collective (Voting, Debate)")
      ("Collective Intelligence & Adaptation - Ch 16")
        ("Collective Intelligence:<br/>Emergent group capabilities, Improved performance, Emergent behaviors (trust, deception), Social evolution (norms, roles)")
        ("Individual Adaptability:<br/>Self-evolution via Memory-based learning (individual/shared) and Parameter-based learning (fine-tuning)")
      ("Evaluating MAS - Ch 17")
        ("Benchmarks for Reasoning Tasks:<br/>Code (HumanEval), Knowledge (HotpotQA), Math (MATH), Societal Sim (SOTOPIA)")
        ("General MAS Capabilities:<br/>Collaboration-focused (Collab-Overcooked), Competition-focused (BattleAgentBench), Adaptive/Resilience (AdaSociety)")
        ("Challenges:<br/>Standardization, Scalability eval, Need for integrated frameworks")

    ("Part IV: Safety & Beneficence")
      ::icon(fa fa-shield-alt)
      ("Intrinsic Safety:<br/>Brain (LLM) Threats - Ch 18")
        ("LLM Vulnerabilities:<br/>Jailbreak (White/Black-box), Prompt Injection (Direct/Indirect), Hallucination (Knowledge/Context-Conflict), Misalignment (Goal/Capability-Misused), Poisoning (Model/Data/Backdoor)")
        ("Privacy Threats:<br/>Training Data Inference (MIA, Extraction), Interaction Data Inference (System/User Prompt Stealing)")
        ("Mitigation (Brain):<br/>Training-free (Filtering, RAG, Uncertainty Est., Guardrails), Proactive (Safe RLHF, Adversarial Training, Privacy-Preserving Methods)")
      ("Intrinsic Safety:<br/>Non-Brain Threats - Ch 19")
        ("Perception Threats:<br/>Adversarial Attacks (Textual, Visual, Auditory, Other), Misperception Issues (Bias, Complexity, Limits)")
        ("Action Threats:<br/>Supply Chain Attacks (Compromised services), Tool Usage Risks (Unauthorized actions, Data leakage, Permissions)")
      ("Extrinsic Safety:<br/>Interaction Risks - Ch 20")
        ("Agent-Memory:<br/>RAG poisoning (AgentPoison, BadRAG)")
        ("Agent-Environment:<br/>Physical (Sensor spoofing, Actuator manipulation), Digital (Code injection, Data manipulation, DoS)")
        ("Agent-Agent:<br/>Competitive (Deception, Exploitation), Cooperative (Leakage, Error propagation)")
        ("Mitigation (Interactions):<br/>Monitoring, Evaluation (AgentMonitor, R-Judge), Domain-specific safeguards (ChemCrow)")
      ("Superalignment & Scaling Law - Ch 21")
        ("Superalignment:<br/>Goal-driven alignment via composite objectives (Safety, Task, Long-term). Overcomes RLHF limits. Challenges: Goal spec, Calibration, Adaptation")
        ("Safety Scaling Law:<br/>Capability vs Risk. Findings: Trade-offs, Commercial vs OS models, Data quality matters. Enhancement: Preference Alignment (Safe-NCA), Controllable Design. Risk Management: AI-45° Rule, Red/Yellow Lines")

    (Conclusion & Future Outlook - Ch 22)
      ::icon(fa fa-flag-checkered)
      ("Summary:<br/>Core components, Evolution, Collaboration, Safety")
      ("Future Milestones")
        ("General-Purpose Agents")
        ("Continuous Environmental Learning & Self-Evolution")
        ("Collective Intelligence Network Effect")
        ("Transformative Human-AI Society")
        
```


DOI:[10.13140/RG.2.2.20976.98564](http://dx.doi.org/10.13140/RG.2.2.20976.98564)





---
**Licenses:**

- **MIT License:**  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE) - Full text in [LICENSE](LICENSE) file.
- **Creative Commons Attribution 4.0 International:** [![License: CC BY 4.0](https://licensebuttons.net/l/by/4.0/88x31.png)](LICENSE-CC-BY) - Legal details in [LICENSE-CC-BY](LICENSE-CC-BY) and at [Creative Commons official site](http://creativecommons.org/licenses/by/4.0/).

---