---
layout: post
title: "World Models"
date: 2026-01-05
---
***Some elements here build upon the [RL env](https://ankitmaloo.com/rl-env) post. Also, please read the footnotes, given a lot to cover, I moved many clarifications to the bottom.***

Something is happening across all major labs simultaneously and it's not a coincidence. 

- Yann LeCun [announced](https://www.nasdaq.com/articles/metas-chief-ai-scientist-yann-lecun-depart-and-launch-ai-start-focused-world-models) he is leaving Meta to start a new lab focused entirely on World Models. He also has a technical [lecture](https://www.youtube.com/watch?v=2j78HCv6P5o) on what the world models are and what they do. 
- Ilya Sutskever, on Dwarkesh's podcast, described emotions as value functions, a framing that makes a lot of sense when you are moving away from pattern matching to planning and simulation. 
- Google announced [Genie 3](https://deepmind.google/blog/genie-3-a-new-frontier-for-world-models/), their approach to world simulation. 
- In a probably throwaway line, Demis Hassabis revealed how he is spending most of his research time on World Models. 
- Anthropic's intepretability research [shows](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) [that](https://transformer-circuits.pub/2025/attribution-graphs/biology.html) current models already develop internal world representations, but they are implicit, emergent and unreliable. 
- OpenAI, when launching Sora insisted on it being a world simulator, as opposed to being just a video model. 
- Similarly, Veo3 is also referred to as a physics model or a world model. 
- Meta released a [paper](https://arxiv.org/abs/2510.02387) on code world model (cwm) in September last year, where a 32B model matched or outperformed larger models on execution-dependent benchmarks.

When every major lab converges on the same research direction within the same window, we should pay attention.

## What is a World model?

A [world model](https://www.nvidia.com/en-us/glossary/world-models/) predicts the next state or observation. The objective is to understand the causal laws of the environment where environment can be a videogame, codebase, or a market.

This is distinct from what the current systems do[^1]: 
- A transformer predicts the next token (imitation or pattern matching - what comes next in a sequence)
- A reasoning model (trained via RLVR) is optimizing for a reward from its training (reasoning or what the inference step follows)
- A world model predicts the next state (simulation i.e. what the world looks like after an intervention)

For a code world model, from Meta's paper: 

> (the model) must understand not just what code looks like but what it does when executed

Today's LLMs produce code that looks correct. You still need to run it to know if it works. A Code World Model already predicts (within the limits of its training distribution) what happens when that code executes.

The 32B CWM matches/exceeds larger models on benchmarks like SWE-Bench, Terminal Bench etc. This shows training on state transitions can be more sample-efficient than training on token sequences, even when both access the same underlying information.

## World Models Already Exist

We've been building world models for decades. We just don't call them that.

A recommendation engine does not predict the next post in a sequence. It's answering a counterfactual: "If I intervene by showing this video/post to this user at this moment, what happens to them?" 

That's state → action → next state. It's a world model for human attention[^2].

This is simulation of a human, however crude. It chooses the action that moves the environment into the desired state (High Engagement). These systems have been running learned simulations of human psychology for 15 years. 

We don't use that terminology because recommendation systems emerged from a different research lineage i.e. collaborative filtering, matrix factorization, learning to rank. But functionally, they predict human behavior in response to interventions. They work on noisy, confounded, incomplete data. And billions of dollars flow through these predictions daily. 

The pattern repeats across domains:

- Algorithmic trading systems predict market response to orders. These are world models with adversarial agents. 
- Supply chain solvers model cascading effects of delays and disruptions
- Weather models predict atmospheric state evolution. 
- Game engines maintain consistent physics across state transitions. 

Each is a world model. Domain-specific, expensive to build, but effective because they predict states rather than tokens.

Unquestionably, these world models demonstrably work for a given objective. The question is if this capability can become general-purpose rather than rebuilt for each domain.


## Why Adversarial Domains Need World Models
*In business, finance, geopolitics, the environment fights back.*

Static models fail when opponents adapt. Pattern matching breaks when patterns shift in response to your actions. You can not imitate your way through a domain where the other side is modeling you.

This is why Quant trading is a fascinating usecase. Traders actively model adversarial simulation. "If I place this order, how does the market react?" "If I reveal this signal, who would exploit it?" instead of a naive prediction model. A world model must include agents that are themselves modeling the world. 

Business strategy has the same structure. If I launch a promotion, competitors respond. If I enter a market, incumbents defend. Static analysis fails because the environment is reactive.

**Current LLMs struggle here because they're trained on imitation. They learn what people said about competitive dynamics, not how competition unfolds. They can recite game theory but can't simulate a price war.**

Unless they are trained on causality. A world model trained on actual competitive outcomes - who won, who lost, what happened when — learns dynamics directly. It doesn't need to be told that first-mover advantage exists; it observes that first movers in domain X succeeded Y% of the time under conditions Z[^3].

### Language
Language understanding is what makes this newly tractable. Previously, you couldn't feed a market simulator the sentence "our competitor is reducing pricing in Q4." Humans had to translate context into variables. LLMs dissolve that interface. Now you can ingest earnings calls, internal memos, market signals etc. and output predicted states. (You still need outcome-linked training and a grounded state.)

More importantly, in many cases, this is also why world model doesn't need to be a separate system. It's an LLM trained on state transitions rather than token sequences, one that ingests language and outputs consequences. This is how Meta trained their code world model. 

## Value Functions: Knowing What's Good
*Because simulating the future would be useless if you don't know which future you want*

Conceptually, a [value function](http://incompleteideas.net/book/first/ebook/node34.html) estimates the expected future reward from a given state. A world model tells you what happens next. Add a value function and you know whether what happens next is good. 

This unlocks something critical for multi-step tasks. Consider a workflow with dozens of intermediate steps. Without value functions, you run every trajectory to completion to evaluate. With value functions, you can evaluate mid-stream: did this step improve state quality or degrade it? Bad trajectories get pruned early. Compute flows to promising paths. This has obvious applications in robotics, but I would argue this has applications for non robotics tasks too. 

This helps solve one of RL's oldest problems: credit assignment. When a fifty-step plan fails, you can figure out where it went wrong. Value functions track state quality throughout. You identify exactly where things degraded. The model learns not only the possible actions but also the actions which lead to high-value states.

Ilya's framing of emotions as value functions clicks into place here. As Ilya says, emotions may be humans' heuristic value estimators. Rough approximations that prune bad plans before full simulation. Anxiety is your value function signaling low expected return. Excitement is the opposite. We don't run every life choice to completion; emotions give early reads on trajectory quality, enabling efficient search through impossible action spaces.

## The Feedback Loop Is the Moat

In a previous [post](https://ankitmaloo.com/rl-env) on RL environments, I argued that RL is a composition of three elements: an algorithm, an environment, and priors from a foundation model. 

The environment is where world models become critical infrastructure.

At the simplest level, you have a static harness: a fixed evaluation function, some dataset with ground truth. Better is a learned reward model. Best is a full world model that simulates trajectories before execution.

But: the simulation is not the moat. The feedback loop is.

Consider algorithmic trading. You would build a market simulator to test strategies before deploying capital. The simulation is disposable. Once run, it's consumed. What compounds is the flywheel: strategies survive simulation, get deployed, real outcomes feed back, the model updates, better strategies emerge.

Recommendation systems have this property. Every click, every scroll, every session feeds back into the model. The system improves through use.

This is where domain experts hit a ceiling. An ex-banker can tell you if analysis "looks right." But their judgment is frozen at the point they left, biased by specific experience, cannot update at scale. A world model trained on actual outcomes learns what works - even strategies that violate expert intuition. It can discover approaches that would get a human fired for seeming unconventional, then validates them through execution. 

## The Gap in Current LLMs
If we were to take a concrete example...

Say, you ask a model to generate a business plan. It produces something realistic-looking. Want better? Ask it to reason, generate multiple drafts, select the most coherent. The output improves.

But the model doesn't know if the plan is good.

It knows what business plans sound like. It doesn't know what happens when a plan meets reality[^4]. How customers react, where friction emerges, which assumptions break. **The first job of any plan is to survive contact with the real world.**

Humans do this implicitly. When assessing a plan, we simulate: "If we do X, competitor does Y, customer sees Z." Those who simulate well plan well. It does not matter knowing what good plans look like, it's about anticipating consequences[^5].

**Imitation Model:** "Write a marketing plan that sounds professional based on this context."

**Adversarial World Model:** "If I launch this plan, how will Competitor X react based on their past behavior?"

Current models can't do this because they're trained on what people said, not what happened. They have no loss function on outcomes, only on plausibility.

## Why Now?
The convergence is an expected outcome. Three things are happening.

First, diminishing returns on next-token prediction. Scaling laws hold[^6], but capability gains are flattening for tasks requiring causal understanding rather than pattern recognition.

Second, video models became physics simulators. Sora, Veo aren't primarily about content generation. Teaching a model to predict video frames consistently, physically, across occlusions, is teaching it how objects behave. Like a learned simulator in latent space. These are world models trained on visual state transitions.

Third, interpretability revealed the gap. Models already form internal world representations. But they're accidental, inconsistent, and fail unpredictably. The agenda now is to make world models explicit and trainable rather than emergent and brittle[^7].

All the labs are responding to the same bottleneck from different angles.

## The Arms race

The first company to build reliable world models for high-value domains gets a system that improves with every deployment. Predictions test against reality. Errors become signal. The model updates. The flywheel accelerates.

Imitation-based systems don't have this property. They plateau at training data quality. World models improve through use.

The implications:

- Models that simulate market impact before announcements
- Models that predict competitive response to launches
- Models that trace supply chain cascades before they happen
- Models that evaluate strategies by projected outcomes, not surface plausibility

Because they're trained on the right objective.

And you need a lot more compute for building these models because of these very properties. Training on real world outcome data, running multi-step simulations for planning, and continuously updating models via live feedback loops are all  compute-intensive.

## Conclusion
There's a line I've been circling:

*Predicting what someone would say about X is a local maximum.*

*Predicting what would happen with X is the path forward.*

The imitation era taught us what humans say about the world: extraordinary, but bounded. Discourse alone hits a ceiling for tasks requiring causal understanding. 

The next era requires learning from the world directly: from executions, from physics, from outcomes, from competitive dynamics. Not what people claim works, but what actually does.

## P.S. On Reasoning Models

In my previous [post](https://ankitmaloo.com/rl-env), I talked about how reasoning generalizes from priors to navigate complex problems. When those priors are solely linguistic or symbolic, a typical reasoning search space is constrained to what can be said or written for a given problem. 

World models change this substrate to causal priors. They teach the system about how interventions change states. In practice: reasoning[^8] proposes an action, the world model predicts consequences, and bad trajectories get pruned before execution. The search changes from a "world of words" to a "world of consequences.". 

---
Footnotes:

[^1]: This is a simplification. Not exactly right, but correct in important ways. Next-token models can implicitly learn dynamics; the difference is whether the training objective and evaluation force accurate consequences under intervention.

[^2]: The "world" being modeled is the user's psychology. The "state" is their current context—history, preferences, attention budget, time of day. The "action" is the content surfaced. The "next state" is their response: do they engage, do they leave, do they come back tomorrow, does their preference shift?

[^3]: One question here is you can also train an LLM on that data. The key difference is understanding of causality. LLMs inherently have no sense of that. 

[^4]: Tool-use/Context helps in providing up to date knowledge. But that is still short of having a causal model of "what happens if I do X?"

[^5]: One shorthand if you were to take from this article is to think about causality. LLMs can predict some causal actions especially where every causal action is written down (eg: Math proofs and verifiable rewards), but not all the time. 

[^6]: Scaling still works, but does not give you the kind of step function change that going from GPT-4 to o1 did. 

[^7]: This, combined with other interpretablity research - influencing and removing negative interpretability vectors, golden gate claude, and now soul document - suggests these internal models can be influenced and modified. This is my interpretation, Anthropic has not said anything explicitly about this. 

[^8]: Reasoning models too have a positive feedback loop where it came to maths and verifiable domains. My working theory is that in Math/code/reasoning, the available training data is causally encoded more or less. Nothing is tacit or implicit. 
