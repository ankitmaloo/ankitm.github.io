---
layout: post
title: "When AI Breaks Its Own Patterns: Understanding Anti-Inductive Domains"
date: 2025-06-02
---
From Scott Alexander's [post](https://slatestarcodex.com/2015/01/11/the-phatic-and-the-anti-inductive/)

> Douglas Adams once said there was a theory that if anyone ever understood the Universe, it would disappear and be replaced by something even more incomprehensible. He added that there was another theory that this had already happened.

> These sorts of things – things such that if you understand them, they get more complicated until you don’t – are called “anti-inductive”. [^1]

That is, systems where understanding a pattern (and then using it) causes that very tactic to stop working. As AI reshapes our world, understanding anti inductive systems is crucial for calibrating where AI will thrive and where it might just make things worse.

Just to recap, at a fundamental level generative AI models work via identifying patterns. These models learn from data, improve with usage, and get better through real-world examples included in training. We have seen this in action with the evolution of AI-generated code: Sonnet 3.5 released in June 24, making Cursor / Windsurf and AI coding a viable usecase. Three iterations of Claude later, each markedly better at coding than the last, the pattern is clear: more usage leads to better models for everyone. Within a year, we have newer models maxxing the benchmarks, cursor at $10B valuation, and Windsurf was acquired by OpenAI for $3B. In a way, these models are induction engines [^2]. If they work for nth user, they are likely to work equally as well if not more for (n + k)th user. 

But what happens when success destroys the very patterns that created it?

## The Pattern That Eats Itself

That's what anti-inductive domains are all about: when exploiting a pattern causes the pattern to break. Stock trading is the classic example. Once a strategy becomes known, it stops working because too many people jump on it. Job interviews show this too; "I want to help people" was once a sincere answer. Now it's generic. The same happens with blogging formulas or storytelling techniques.

With AI positioned to be ubiquitous across every domain, this is the weird terrain it must navigate. Understanding anti-inductive patterns are crucial for using AI for the right usecases. 

## AI in Inductive Lands: Where More Means Better

In inductive domains, patterns strengthen with use. Incidently, where AI has a PMF[^3]:

* **Coding:** Every chunk of code AI processes refines its understanding. It learns from billions of repositories, absorbing patterns in architecture, best practices, and debugging techniques. Any failure modes are likely included in next training run, making the models smarter and outputs better. Outcome is a more standardized, maintainable code that benefits everyone (we are getting there based on trajectory). 

* **Customer Service:** Support tickets follow patterns. Common issues get standard solutions. Each interaction teaches AI systems more about user problems and effective responses. It's still a discrete improvement given the training complexities, though it results in a continuously learning system. 

These domains are converging ecosystems where AI creates a virtuous cycle. Each user adds value, and everyone benefits from the accumulated knowledge[^4]. 

## AI in Anti-Inductive Domains: Where Success Breeds Failure

But then there are domains where success carries the seeds of failure:

* **Marketing:** The first emotional brand ad campaign moved audiences. The hundredth felt manufactured. By the thousandth, viewers had developed immunity. Every successful pattern becomes a cliché. We're already seeing this in social media, where AI-generated content increasingly blends into a homogeneous mass. Every new cold email from an AI SDR decreases the effectiveness of next cold email written with same pattern of personalization. When you have a model relying on identifying patterns from what worked in the past, they are more likely to suggest overused ideas which worked at a point in time, and is saturated today.

* **Creative Writing:** When everyone uses AI to craft "unique" stories or dating profiles, the results converge. What was once clever becomes common. A profile that stood out yesterday becomes tomorrow's template. The more AI optimizes for engagement, the more it creates a sea of sameness.

The pattern is apparent: in these domains, being first matters more than being best. These are zero-sum games of novelty. AI's success leads to saturation.

## The Mental Model: AI as Mirror and Megaphone

A way to think about it is:

* In *inductive domains*, AI is like building a library. Every user adds another layer of knowledge (that is later integrated via training). It gets larger, faster, better and benefits the (n+1)th user more than preceding users. 

* In *anti-inductive domains*, AI is like yelling into a crowded room. If you’re first, people hear you. If you are last, you’re noise.

A key product question to ask is: Does AI help by repeating patterns? Or hurt by making everyone sound the same?

## The Future: More libraries and Noisy Rooms

If we continue down this path, we'll see AI getting used in every inductive space. Code will become abstracted. Interfaces will simplify (security issues will be fixed through feedback). Most people won't need to write code — they'll describe what they want, and AI will translate intent into implementation.

But in anti-inductive areas, AI may accelerate the race to mediocrity. Marketing messages will blur into an indistinguishable mass. Creative content will flatten into formulaic templates. The bar for "original" will keep rising, pushing humans to reclaim the edge AI can't reach - not knowledge, but *surprise*.

This isn't to say AI has no place in anti-inductive domains. But timing matters critically: in inductive spaces, latecomers can still win by building on accumulated knowledge. In anti-inductive spaces, first movers capture most of the value before patterns become stale.

## Final Thought: Choose Your Domain Wisely

The most powerful applications of AI will be found where patterns compound rather than collapse. Using AI to:
- Build infrastructure
- Create clarity
- Enhance systems instead of gaming them


The future splits into two paths: one where AI builds upon the world's knowledge, another where it amplifies until everything becomes noise. 


**Notes:**

[^1]: Notice the em-dashes. No specific point, just that they existed - and people used them - before LLMs came into existence. 

[^2]: While there's debate about classifying generative AI models as pure induction engines, the model serves as a useful approximation for understanding their behavior and limitations.

[^3]: There are more domains that are similar but without a PMF yet. It's interesting the domains where PMF is established is where convergence and standardization are highly desired characteristics. 

[^4]: Network effects present an interesting parallel case study – while similar to inductive patterns, they follow their own unique dynamics that deserve separate analysis.
