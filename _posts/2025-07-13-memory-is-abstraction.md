---
layout: post
title: "Memory is Abstraction + RL: LLMs Need to Learn Like Humans"
date: 2025-07-13
---
*someday i will make a more thorough and better reasoned post around it but at this point these are just notes somewhat structured*

The current discourse around LLM memory feels fundamentally misguided. We're stuck in this paradigm of "how do we stuff more relevant context into the prompt" or "how do we update the system prompt periodically" as if memory is just a set of context and instructions. But this misses what makes human memory so powerful: we don't remember everything - we abstract, we learn what matters, and we build rich associative networks that let us navigate experiences we've never explicitly stored.

## The False Promise of Context Windows

The prevailing wisdom suggests that memory is about retention, accessing the past at present for a specific purpose. This leads us down the path of ever-expanding context windows, retrieval-augmented generation, and prompt updates to use memory as another lever. But watching a human expert at work, and you see something entirely different.

A senior developer doesn't remember every line of code they've ever written. Instead, they've developed abstractions: patterns, principles, heuristics etc. that let them navigate new problems with wisdom gained from past experiences. They recognize that "this feels like that distributed systems issue from 2019" without remembering the specific implementation details. 

This is different from how we're approaching LLM memory today.

## Memory as Learning, Not Storage

What if memory isn't about context at all, but about learning? Not "what happened" but "what did I learn from what happened"?

Consider how humans process a failed project. We extract patterns from the failure, and pretty much forget about the rest. "Teams without clear ownership boundaries tend to ship late." "Technical debt compounds exponentially when you skip testing." These aren't facts we retrieved, they're general abstractions that reshaped how we approach future problems.

This is a completely different architecture for LLM memory:

1. **Abstraction Layer**: Instead of storing interactions verbatim, the system extracts higher-level patterns
2. **Reinforcement Learning**: The system learns which abstractions actually prove useful in future interactions
3. **Graph Neural Networks**: Store not just what happened, but how experiences relate to each other
Expanded below:

## Memory Architecture

### Layer 1: Experience Graph (GNN)

Current memory systems store conversations as sequences. But human memory isn't built that way, it's associative. We remember experiences through their relationships to other experiences, concepts, and outcomes.

A Graph Neural Network approach would:
- Store interactions as nodes with rich feature representations
- Create edges based on conceptual similarity, causal relationships, and outcome patterns
- Allow for complex queries like "show me experiences where UI decisions led to user frustration"

The key insight: Store "what this interaction teaches us about effective communication patterns." not just "So this happened."

### Layer 2: Abstraction

This is where the magic will be. Instead of storing raw interactions, the system continuously abstracts:

- **Pattern Recognition**: "Users asking about discounts are likely to convert if given one."
- **Causal Learning**: "When I provide code examples without context, users ask follow-up questions about edge cases"
- **Meta-Learning**: "The most successful interactions involve me asking clarifying questions before providing solutions"

These abstractions can not be hand-coded rules. That's just for example. They have to be learned representations that capture the essence of what makes interactions successful.

### Layer 3: Reinforcement Learning Loop

The critical piece missing from most memory systems is feedback. Humans don't always remember what happened, we remember what worked (and sometimes revisit even that). RL:

- Tracks which abstractions lead to successful outcomes
- Adjusts the abstraction process based on long-term utility
- Learns to prioritize certain types of memories over others

This creates a virtuous cycle: better abstractions → better interactions → better feedback → better abstractions.

## Why This Matters for AI Agents

The implications go beyond "better chatbots." This approach enables:

**Contextual Adaptation**: Instead of having the same personality across all interactions, the agent learns to adapt its communication style based on what worked with similar users in the past.

**Cumulative Wisdom**: Each interaction makes the agent genuinely smarter, not just more informed. It develops intuitions about problem domains, not just facts.

**Graceful Forgetting**: The system naturally forgets specifics while retaining wisdom - a senior developer doesn't remember every bug, but they remember the patterns that prevent bugs.

## Interaction Memory

This brings us to: we're talking about *interaction memory*, not *user memory*. The system is not about trying to build a comprehensive model of the user. It rather builds a model of effective interaction patterns.

This is subtle. Current approaches try to answer "what does this user care about?" The abstraction+RL approach asks "what communication patterns work best in this context?"

The difference is huge. One leads to creepy surveillance vibes; the other leads to genuine helpfulness that improves over time.

## Implementation Reality Check

Building this isn't trivial. The GNN needs to handle:
- **Temporal dynamics**: How relationships between experiences evolve
- **Multi-scale patterns**: Both immediate feedback and long-term trends
- **Cross-domain transfer**: Lessons learned in one context applying to another

The RL component faces exploration/exploitation tradeoffs: when should the agent try new approaches vs. relying on proven patterns?

These are solvable problems. The bigger challenge is conceptual shift: we need to stop thinking about memory as storage and start thinking about it as learning.

## The Path Forward

This approach suggests that truly useful AI agents won't have perfect recall, but they will learn to be better conversational partners over time. Thats what openai is hoping a companion app would do. 

They'll develop something akin to wisdom: the ability to extract what matters from their experiences and apply it meaningfully to new situations.

This is memory as a moat, yes, but also as a genuine evolution. Each interaction fundamentally changes how the agent approaches future problems. The agent that helps you solve issues today is genuinely different from the one that helped you six months ago because it has learned to be more helpful. This approaches close to continuous learning[^1]. 

In a world where everyone has access to the same base models, this kind of learned wisdom might be the only sustainable advantage. Architectures that abstract, learn, and evolve like we do are the kind of moat you can build in an AI era. 

Hope to come back with an implementation or POC to make this work. 

[^1]: This is more of a discreet learning rather than continuous in the truest sense of the word. But if a system updates over the weekend when you are not using it, for all practical purposes, it's a continuously learing system. 