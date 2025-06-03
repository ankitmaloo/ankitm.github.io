---
layout: post
title: "AI in Anti-Inductive Domains"
date: 2025-06-02
---
From Scott Alexander's 2015 [post](https://slatestarcodex.com/2015/01/11/the-phatic-and-the-anti-inductive/)

> Douglas Adams once said there was a theory that if anyone ever understood the Universe, it would disappear and be replaced by something even more incomprehensible. He added that there was another theory that this had already happened.

> These sorts of things – things such that if you understand them, they get more complicated until you don’t – are called “anti-inductive”. [^1]

That is, systems where understanding a pattern (and then using it) causes that very tactic to stop working. As AI reshapes our world, understanding anti inductive systems is crucial for calibrating where AI will thrive and where it might just make things worse.

Just to recap, at a fundamental level generative AI models work via identifying patterns. It looks at tons of data, learns from how people use it, and gets even smarter through real world examples in future training runs. Take AI coding for instance: When Sonnet 3.5 dropped in June '24, it made AI coding actually useful with tools like Cursor and Windsurf. Then Claude came along with three new versions, each one way better at coding than the last. The pattern was clear: the more people used it, the better it got for everyone. Within a year, we had new models crushing benchmarks, Cursor hit $10B in value, and OpenAI bought Windsurf for $3B. These AI models are like inductive engines[^2]: if they work well for the 100th user, they'll probably work even better for the 1000th user.

But what happens when success destroys the very patterns that created it?

## The Pattern That Eats Itself

This is what anti-inductive stuff is all about - when everyone figures out a pattern and starts using it, that pattern stops working. Like stock trading: find a winning strategy, tell everyone about it, and then it stops working because everyone's doing it. Or think about job interviews: saying "I want to help people" used to be a great answer. Now? It's a cliche. Same goes for blog posts and story formats - once everyone knows the formula, it loses its spark.

As AI starts showing up everywhere, it needs to deal with this tricky bifurcation. If we want to use AI right, we need to know where patterns hold up and where they don't work due to the inherent nature of a given domain.

## AI in Inductive Lands: Where More Means Better

In inductive domains, patterns strengthen with use. Incidently, where AI has a PMF[^3]:

*For completeness, I should mention that the improvements below are discreet. Either the AI dev looks at examples and improves systems, or the models include right examples for next training iteration. The general idea still holds though.*

* **Coding:** Every chunk of code AI sees makes it smarter. It's learning from billions of code repositories, picking up patterns in how we build stuff, what works best, and how to fix bugs. When something goes wrong? That gets added to its training data, making the next iterations better for everyone. We're heading towards a world where code is cleaner, easier to maintain, and works well for everyone.

* **Customer Service:** Customer problems tend to follow patterns. Someone's having trouble logging in? There's probably a standard fix for that. Every time AI handles a support ticket, a system learns more about what users need and what solutions work best. Sure, the improvements come in discrete steps (futher training, prompt / pipeline finetuning) rather than continuously, but the system keeps getting better.

These domains are converging ecosystems where AI creates a virtuous cycle. Each user adds value, and everyone benefits from the accumulated knowledge[^4]. 

## AI in Anti-Inductive Domains: Where Success Breeds Failure

But then there are domains where success carries the seeds of failure:

* **Marketing:** The first time I saw an emotional brand ad? It hit me. But by the hundredth one? Meh. By the thousandth? You probably roll your eyes. That's because what works becomes a cliche super fast. Just look at social media today. AI-generated posts all start to look the same. Those AI-written cold emails? Each one makes the next one less likely to work because we've seen it all before. The problem is, AI looks at what worked in the past and suggests those same ideas frameworks - but they're already old news. It's ike how 'The Incredibles' put it: "If everyone is super, no one is".

* **Creative Writing:** It's funny what happens when everyone uses AI for their captions or dating profiles. Something that was super clever yesterday becomes just another template today. Everyone's trying to be unique in exactly the same way. The more AI tries to write stuff that gets attention, the more everything starts to sound the same[^5].

The pattern is apparent: in these domains, being first matters more than being best. These are zero-sum games of novelty. AI's success leads to saturation.

## The Mental Model: AI as Mirror and Megaphone

A way to think about it is:

* In *inductive domains*, AI is like building a library. Every user adds another layer of knowledge (that is later integrated via training). It gets larger, faster, better and benefits the (n+1)th user more than preceding users. 

* In *anti-inductive domains*, AI is like yelling into a crowded room. If you’re first, people hear you. If you are last, you’re noise.

A key product question to ask is: Does AI help by repeating patterns? Or hurt by making everyone sound the same?

## The Future: More libraries and noisy rooms

Keep going down this road, and we'll see AI pop up in every area where identifying patterns help. Writing code will get simpler. Everything will be easier to use (and yeah, those security problems will get fixed as we go). Most folks won't even need to learn coding - they'll just tell AI what they want, and it'll make it happen.

But here's the flip side: in areas where being different matters, AI might actually make things worse. Marketing? It'll all start to look the same. Creative stuff? It'll start feeling like it came from a template factory. Being "original" will get harder and harder, and that's where humans will need to step in - not with knowledge, but with the ability to *surprise* and break patterns.

This isn't to say AI has no place in anti-inductive domains. But timing matters critically: in inductive spaces, latecomers can still win by building on accumulated knowledge. In anti-inductive spaces, first movers capture most of the value before patterns become stale. The success lies in breaking the patterns. 

## Final Thought: What I've Learned

I think the best applications for AI will be where patterns build on each other. 

In inductive domains, I let AI handle the heavy lifting:
- Writing boilerplate code and tests
- Organizing documentation
- Building data pipelines

In anti-inductive domains, it's wiser:
- For marketing: Focus on data mining, analysis, and insights, not writing copies. You can always ask an AI how your lead will react based on a copy you provide to iterate. Works far better. 
- For products, I feel in the long run I want to keep user interfaces fresh and opinionated instead of every website looking the same. Though it will be copied, but like I said, first mover is a distinct advantage here. 

It's not about avoiding AI in anti-inductive spaces but using it to handle the repeatable parts while you focus on what changes. This way, AI amplifies the edge. 


**Notes:**

[^1]: Notice the em-dashes. No specific point, just that they existed - and people used them - before LLMs came into existence. 

[^2]: While there's debate about classifying generative AI models as pure induction engines, the model serves as a useful approximation for understanding their behavior and limitations.

[^3]: There are more domains that are similar but without a PMF yet. It's interesting the domains where PMF is established is where convergence and standardization are highly desired characteristics. 

[^4]: Network effects present an interesting parallel case study – while similar to inductive patterns, they follow their own unique dynamics that deserve separate analysis.

[^5]: There is a lot of meta commentary to be made here about different marketing products over the last two-three years and then the attempts from Meta to increase AI usage in their apps. For now, I will steer clear of that. 