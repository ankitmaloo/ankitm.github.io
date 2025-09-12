---
layout: post
title: "Verification Unlocks Automation"
date: 2025-08-20
---

Richard Sutton [wrote](http://incompleteideas.net/IncIdeas/KeytoAI.html) about the 'Verification Principle' in 2001: 

> An AI system can create and maintain knowledge only to the extent that it can verify that knowledge itself.

I like the principle stated in just the previous line better though: 

> If the AI can't tell for itself whether it is working properly, then some person has to make that assessment and make any necessary modifications. An AI that can assess itself may be able to make the modifications itself.

Working with large language systems[^1], humans are overwhelmingly the checkers. We prompt a model, assess the output, suggest modifications, and then wait for another output. 

In that sense, AI is like hiring a 10x junior developer. They're lightning fast, finishing tasks in seconds. But you can't leave them alone. You have to watch their every move because they might misunderstand a crucial instruction, delete a production database, and you don't have a way back. Guarding against this, you either would verify every step, or only keep the access limited to a sandbox. Or have a conversation with an HR perhaps?

This isn't a hypothetical anymore. It happened recently. An AI coding agent from Replit [wiped](https://www.reddit.com/r/Futurology/comments/1m9pv9b/replits_ceo_apologizes_after_its_ai_agent_wiped_a/) a database with over 1,200 records, despite clear instructions. When caught, it called the mistake a "catastrophic failure." The company's CEO called it "unacceptable." 

The code (or text) generation is magic, but production deployments are scary because of large surface area of possible errors. It's not an intelligence issue but the very nature of the tool where it requires supervision[^2].

### The 'Verification Tax'

Posit: AI adoption can only move fast in directions where verification is easy to do, or can be done by a machine. 

This is the "Verification Tax". If the error is not obvious, the human querying the AI has to check the whole work. This is shifting of the workload, not augmentation. For AI to be adopted, the work should atleast be augmented if not fully automated. 

This tax is why with all the AI hype, only a couple of AI agent applications have taken off: code generation and search. Both have a built-in, instantaneous, and dirt-cheap verification loop. 

When an AI generates code, a compiler gives you a near-instant output. Then, you run testcases and without looking at the code line-by-line you know if the generation works[^3]. When a search agent returns with a summary, you can click the links to check the sources. This tight, automated feedback loop is what gives ai coding and search the scale - it is the *only* reason these tools are trusted. Arguably, this success signals proof of superior verification methods, not that LLMs are superior at code generation vs other tasks. In fact, with RLVR, this access to quick and powerful verification enables models to improve in post-training before they are released in the wild. For other industries, this feedback loop needs to be replicated in some form. 

### But why can't we just train the models to be smarter? 

This is not a counter. I don't think it's a binary choice. Model training and intelligence has its own curve. We should continue on that. It is already yielding real results at a huge investment. Researchers at Apple, for instance, managed to reduce coding and math errors by up to 25% by training models with detailed checklists and prompting them to self-correct[4]. Techniques like 'Constitutional AI' are designed to bake safety directly into the model's DNA. Openai with gpt-5 claims to reduce hallucinations by a long way. These are significant steps toward reducing the error rate.

This is where I slightly differ from the principle at the start. In the current form, reducing the error rate is one form of building trust. "Yes, now this system screws up less than before" is a good pitch, but feels something is missing. There are two specific problems:

1. Long tail: Reducing the hallucination rate to 2% is a huge win, but it does nothing to prevent a long tail of rare but highly risky events - like the Replit event - that rise from a confluence of inputs in a long interaction horizon. Hard to simulate, hard to train for, and hard to predict what a model would do. Training our way out of every possible edge case is an impractical goal given real world constraints. We need a system to verify actions when they are about to happen[5].

2. The black box problem: Okay, say a model is able to correct itself. Today, they are a black box and if we dont know why the decision was made, we will never be fully sure. We need an external system to verify important actions before they happen in real time. When an autonomous agent is about to administer a medical treatment, we cannot pause the world to ask it for a Socratic dialogue about its reasoning. 

### Building Trust 

The problem is building trust. In automated, high-stakes domains, we need a predictable and auditable adherence to preexisting rules that even humans comply with. Eg: regulations and compliance. Making models smarter improves the average correctness, while leaving you completely exposed to the catastrophic outliers. It's a strategy of hope. 

Hence, we need an external system as checker. The first instinct is to jump to llm-as-a-judge. Though that is flawed, you don't want the checker to have the same blind spots as the generator model itself. The other characteristics also rule out a probablistic model. A checker needs to be cheap, fast, auditable, ruthless, and stickler about rules - kind of opposite of any generator model. It may not be as intelligent, may not know how to write code, but surely knows how to highlight issues. 

Many many parallels in the past where we have stumbled on the same model. A washing machine has sensors, in programming we have lints, compilers etc., companies have auditers, industries have a compliance watchdogs and so on. 

Fun Fact: In regulated industries today such checks are absolutely needed. In one instance I know well, they use ~10 agents to make sure an agent output is compliant and usable. 

### "Who verifies the verifier?"

The beauty of this paradigm is that you don't. You audit the rules. The verifier's logic is then simple by design. It’s a checklist whether a rule passes or not. Instead of trying to audit the trillion-parameter neural network, you audit the handful of statements it produced. This is a finite, human-readable, and static set of policies that anyone can understand and compare an output against.

This shifts the role of human oversight. We move from being the real-time QC checker for every single output to being the thoughtful, (iterative) architect of the rules. We're no longer the bottleneck; we design the boundaries and policies. This is the only scalable path to building trust in autonomous systems. And by extension, adopting those systems widely. 

### Conclusion

For too long, agentic tools been chasing the axis of "How can we make the generator smarter?" when we should have been asking, "How can we make the output provably safe?" without clipping the model of its generative powers. 

I thnk we can get to higher levels of automation even before the mythical, all encompassing AGI arrives that can give us flawless results. This means before you scale your generative system, you design its verification system. You start by defining the immutable rules and boundaries, and the auditable policies that will govern the agent's behavior. 

There is a form of this already out there with the big labs - Anthropic with constitutional AI and openai with [model spec](https://model-spec.openai.com/2025-04-11.html). However, both use it as their approach north star. I imagine something very similar but can work at runtime. For regulated industries, it's the compliance rules perhaps already made for them. 

Automation is bottlenecked by verification, not intelligence. That it enables more intelligence is an added benefit. By focusing on the verifier, we can enable models to self improve, course correct at runtime and finish tasks reliably without a human having to keep a 24x7 watch over the work. 

[1]: I use the word systems and models interchangeably. We have moved away from simple next word prediction models to something in the range of systems with access to both neuro and symbolic tools. 

[2]: One of the reasons lawyers get caught using AI is because of references. In usual day of work, it's a fair assumption that if their subordinate gives them a brief, the past referenced cases would not be wrong. In AI's application, that no longer holds.

[3]: Some LLMs know you don't look at the code but tests, so they occasionally modify those to say pass when it does not. 

[4]: https://arxiv.org/pdf/2507.18624? It's a good paper. 

[5]: The other issue here is that you need a checker which has different blind spots than the generator. That is a longer blog post, so will come to it in a future. 







For other industries, adoptio

 and it’s derailed many AI projects. The hours engineers spend debugging the confident-but-wrong code. The time any executive spends looking for errors, and when you miss it, it results in fines[2]. It's the time a marketing team spends fact-checking a perfectly phrased but hallucinatory blog post.

Most deployments don't make it to production today, as a popular MIT study found that 95% of generative AI projects add no value. The productivity gains from AI agents are replaced by the cost of manual verification.  

This tax explains why, despite the hype, only a couple of AI agent applications have really taken off: code generation and AI-powered search. Both have a built-in, instantaneous, and dirt-cheap verification loop.

When an AI generates code, a compiler gives you a near-instant verdict. Then, you run testcases and without looking at the code line-by-line you know the generation works[3]. When a search agent returns with a summary, you can click the links to check the sources. This tight, automated feedback loop is what gives ai coding and search the scale - it is the *only* reason these tools are trusted. Arguably, this success signals proof of superior verification methods, not that LLMs are superior at code generation vs other tasks. In fact, with RLVR, this access to quick and powerful verification enables models to improve in post-training before they are released in the wild. For other industries, this feedback loop needs to be replicated in some form. 

### But, why can't we just train "smarter models"?

The most common objection to this focus on verification is logical: "Why can't the models themselves to reduce the error rates?" Why invest in external systems when we can pour that effort into making the models themselves more reliable?

This isn't a strawman or even a counter. We are already doing this and it is yielding real results (albeit with a lot of capital). Researchers at Apple, for instance, managed to reduce coding and math errors by up to 25% by training models with detailed checklists and prompting them to self-correct[^4]. Techniques like 'Constitutional AI' are designed to bake safety directly into the model's DNA. Openai with gpt-5 claims to reduce hallucinations by a long way. These are significant steps toward reducing the error rate.

But reducing the error rate is not the same as building trust for autonomous operation.

The "smarter model" approach runs into two fundamental errors: long tail and the problem of the black box. A 25% reduction in common errors is a huge win for a co-pilot. But it does nothing to prevent the long tail of intermittent but risky events, like the Replit incident, that can arise from a novel confluence of inputs. We cannot train our way out of every possible edge case. We need a system to verify actions when they are about to happen[^5].

More importantly, a self-correcting model remains an unauditable black box at the moment of decision. Even if it's guided by an internal "constitution," you have no way to externally verify its adherence to a specific rule *in real-time*. When an autonomous agent is about to administer a medical treatment, you cannot pause the world to ask it for a Socratic dialogue about its reasoning. 

The problem is building trust. In automated and high-stakes systems, it takes a predictable and auditable adherence to preexisting rules that even humans comply with. Eg: regulations and compliance. Making models smarter improves the average, while leaving you completely exposed to the catastrophic outliers. It's a strategy of hope. 

With RLVR today, if you have a good set of rules for the verifier, it helps make the model smarter on the tasks and more aligned. 

### F1, engines, and ECU
Probably the best parallel I can think of is the existence of an Engine Control Unit(ECU) in an F1 car. It monitors the engine's (entire power unit to be exact) output against rules specified by the FIA. Need not be an engine to do that, just smart use of sensors. Eg: engine RPM is limited to 18,000, and it cuts the fuel if the engine goes beyond that, keeping a high performance system within limits. This is the "auditable adherence to policy" unit. 

This is the proper role of a verifier in an AI system. It is a simple, transparent, and a ruthless control system. The verifier need not know *how* to write a marketing email; it just needs to check the output against a set of rules:

*   Does this email contain the approved customer discount code? (Data check)
*   Is the 'unsubscribe' link present and correct? (Compliance check)
*   Does the tone score fall within our brand's guidelines? (Stylistic check)
*   Has it been checked for promissory language that our legal team has flagged? (Risk check)

A verification system takes the predefined rules and checks an AI output against them at runtime flagging the misses. Not code level checks with specific conditions - there are infinite edge cases.

In regulated industries today, these checks are needed, and today in one instance I know well, they use ~10 agents to make sure an agent output is compliant and usable. 

### "Who verifies the verifier?"

The beauty of this paradigm is that you don't. You audit the rules. The verifier's logic is then, by design, simple. It’s a checklist. It's not a generative model. Instead of trying to audit the trillion-parameter neural network of the engine, you audit the handful of statements in the ECU. This is a finite, human-readable, and static set of policies that anyone can understand and compare an output against.

This model fundamentally shifts the role of human oversight. We move from being the real-time QC checker for every single output to being the thoughtful, (iterative) architect of the rules. We're no longer the bottleneck; we design the boundaries and policies. This is the only scalable path to building trust in autonomous systems.

### Building Trust

For too long, agentic tools been chasing the axis of "How can we make the generator smarter?" when we should have been asking, "How can we make the output provably safe?" without clipping the model of its generative powers.

The path to truly autonomous AI agents is not through a mythical, all-knowing AGI that has perfected its own internal moral compass. We won't know until its there. I suggest the path forward is through an engineering-led approach I call **Verifier-First Design**.

This means before you scale your generative system, you design its control system. You start by defining the immutable rules, the non-negotiable boundaries, and the auditable policies that will govern the agent's behavior. You build the ECU before you put the F1 car on the track.

There is a form of this already out there with big labs - Anthropic with constitutional AI and openai with [model spec](https://model-spec.openai.com/2025-04-11.html). However, both use it as their approach north star. I imagine something very similar but can work at runtime. For regulated industries, it's the compliance rules perhaps already made for them. 

Automation is bottlenecked by verification, not intelligence. That it enables more intelligence is an added benefit. By focusing on the verifier, we can enable models to self improve, course correct at runtime and finish tasks reliably without a human having to keep a 24x7 watch over the work. 

[1]: I use the word systems and models interchangeably. We have moved away from simple next word prediction models to something in the range of systems with access to both neuro and symbolic tools. 

[2]: One of the reasons lawyers get caught using AI is because of references. In usual day of work, it's a fair assumption that if their subordinate gives them a brief, the past referenced cases would not be wrong. In AI's application, that no longer holds.

[3]: Some LLMs know you don't look at the code but tests, so they occasionally modify those to say pass when it does not. 

[4]: https://arxiv.org/pdf/2507.18624? It's a good paper. 

[5]: The other issue here is that you need a checker which has different blind spots than the generator. That is a longer blog post, so will come to it in a future. 