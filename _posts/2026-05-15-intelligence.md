---
layout: post
title: "Intelligence"
date: 2026-05-15
---
Some problems don't get solved in your head, they get solved in someone else's while you watch or read their solution. You might feel it before you understand it. A small calibration. A quiet "Oh!"

You cannot always tell what got them there. Maybe they extracted their experience into understanding more efficiently than you did, or they remembered the solution from last Tuesday. Both explain the outcome. Often both are partially true. You cannot test them apart in any clean way. The best researchers could do was design problems unlikely to have been seen before, measure the outcome, and argue about what the score meant. 

This is where we have always been with intelligence. A black box. With no factorization. We watched what came out - solutions, inventions, occasional flashes of genius - and attributed it to some combination of memory, recall, reasoning, and an unexplained thing called intelligence. The whole bundle activated at once. **We drew a line in the sand where our understanding gave out, and called the far side "intelligence".** Every IQ test, every SAT, every century of psychometric argument is a long monument to this. A whole discipline built around inferring something from the only data the brain would ever release: the outputs.

The bundle came with its own built-in obstacles. Evolutionary priors, episodic memory, learned procedures, linguistic competence, social intuition, embodied skill, all running on the same substrate, inside the same organism, activated together every time the system did anything interesting. There was no way to pick it apart. Not really. Well, until now.

## Competence
Consider what you actually test when you are evaluating someone on a task. In the first instance you are looking at competence - the ability to do the given task. Whether they can write the proof, diagnose the patient, ship the code and so on. Competence is what is observable. Companies and enterprises pay for it. Credentials exist to certify this. 

To get to intelligence, you want to go to a layer below. That is, inferring how they acquired the competence. Did they write the proof because they memorized it previously? Did they genuinely derive it on the spot from general principles? Pattern matched it instinctively? Was it just innate? Learned from a similar problem last year? This is the layer where you are probing for the harder questions, and the layer you cannot directly observe. So, people designed tests which would eliminate boring explanations of competence. Completely new and unseen problems, novel patterns, constrained contexts, to find out what intelligence looks like. The entire scientific literature on intelligence testing is a long effort to get a clean read on layer two by controlling for layer one.

### LLMs are competent too
Large language models are stunningly competent. This often gets lost in the noise around whether they are really intelligent, but on layer one the answer is not in serious dispute. They write, summarize, translate, code, reason about legal documents, score well on expert exams, and in more domains every month they match or exceed skilled humans at the task. Competence is not in doubt.
The question is what is producing the competence. And here the interesting part is not that we have answered the question. But rather, we know what goes in their training data. We know how they get to the competence they have. 

**LLMs are the first system in history that lets us ask the right questions at a deeper layer.** 

I will come back to LLMs in a minute, but first let me explain what the bundle factorization could look like. 

## Engine and the Substrate
The cleanest vocabulary for the separation comes from [François Chollet](https://arxiv.org/abs/1911.01547). He has been arguing for years that intelligence is not the same as skill. Skill is the ability to perform a task well. Intelligence is the ability to acquire new skills efficiently from minimal experience. This framing draws a line between engine and substrate: the engine is whatever converts experience into generalizable capability, and the substrate is everything else — data, tools, accumulated knowledge, search, the composability of stored skills. A high-conversion engine extracts more structure from less input. A low-conversion engine needs more substrate to reach the same place, and often doesn't reach it at all. **The conversion ratio is the key. Everything else is fuel.** 

Stay with the engine-and-substrate frame for a moment, because it does more work than it first looks like. 

Human brains have been anatomically stable for about ten thousand years. Civilization has obviously progressed. It has accelerated, and the acceleration is accelerating too. Most of the raw increase in human capability has happened in the last six hundred years, which is also the period after the printing press made stored knowledge cheap and composable at scale[^1]. Arguably, the engine stayed the same and the substrate changed. Writing added substrate. Mathematics added substrate[^2]. Double-entry bookkeeping, peer-reviewed journals, institutions, standardized measurement, the internet — all of it added substrate. The same engine, working over fuel that kept getting richer and more composable.

And then we have LLMs. What happens when an LLM is poor at a given task? The fix is more data, better post-training, richer environments, more tool use, more test-time search, more scaffolding, better reward shaping. This usually works. Over the last five years the model families have gotten dramatically more capable, and the vast majority of that gain is traceable to changes in the data mix, the training recipe, and the surrounding apparatus. We have gotten better at feeding the converter. We have not obviously gotten better at building the converter (not in the step change manner anyway, scaling laws are still a thing). LLMs do not, as far as one can tell, improve at extracting structure from small amounts of data, which is what an engine improvement would look like[^3].

[ARC-AGI](https://arcprize.org), the benchmark designed specifically to test the engine rather than the substrate, held up for five years. When models eventually did start scoring higher on it, a lot of the gain came from heavier search, representative training environments, and more test-time compute. Which is the point in miniature. 

> A weaker engine can compensate with a richer search strategy. You can substitute brute force for intelligence. But they are not the same thing.

You see this in humans too. Train people on workflows that remove on-the-fly adjustment and they do excellent work. People can learn enormous amounts from books and courses without any dramatic change in their underlying conversion ratio. **Competence scales with substrate even when the engine holds flat.**

### What does substrate include?
Substrate, in this frame, includes more than just raw data. Memorized skills, learned procedures, and — crucially — the ability to compose them. Writing is composable text. Code is modular instructions. A stronger substrate is bigger and it's more recombinable. That explains how capability can climb steeply without the engine changing. You can get extraordinary performance out of a stable converter if the material you're giving it is increasingly modular. 

The hard part is that composition looks like intelligence from the outside. But if the pieces in the composition existed before it[^6], composition is still substrate. Engine improvement would mean getting better at creating new pieces, new structure from little experience.

### Competence is asymptotic
But the thing about competence is that it is asymptotic. There is always another gap to fill, another edge case, another domain to cover. You never finish. You just get closer to the full coverage. This is exactly what we observe. Model can't do X, train it on X, model gets better at X. Then Y. Then Z. The loop never terminates because competence by its nature has no final state, only diminishing distance to full coverage.

There is an obvious objection to all of this. Maybe evolutionary priors have been doing more of the work than the "brains haven't changed" line admits. This fails on a simple observation. Humans pick up radically new skills and technologies — ones evolution could not have encoded anything about — with roughly the same facility they pick up ancient ones. A child learns to use a smartphone with the same kind of ease a child ten thousand years ago learned to use a digging stick[^4]. Whatever the engine is doing, it is not running on task-specific priors baked in by natural selection. It may be running on very general priors, some kind of abstract learning algorithm flexible enough to handle whatever arrives. It is powerful enough that it works on a tiny substrate. The trickle of local experience a single human gets in a single lifetime. And still produces generalizing and adaptive capability. That is a high conversion ratio. It is the thing LLMs do not appear to have.

## So, what is inside the engine? 

So far we have been looking at the system from the outside. Competence. Separating engine from the substrate. Richer data, better tools, more search, more scaffolding — all of that can raise competence without necessarily improving the converter itself. But that leaves the harder question: what is the converter actually doing when it works?

The best answer we have in the LLM world comes from [Ilya Sutskever](https://www.youtube.com/watch?v=ZZ0atq2yYJw):

> Prediction is compression. 

In his view: To predict the next token well, a model has to compress the data, capture the regularities that generated the data. It is human-generated text, and humans write text from inside the world. So the text carries the shape of the world. Therefore, to compress it well, the model must internalize structure about the world itself — not merely structure about how the world is described. Push compression hard enough and, on his view, understanding has to appear, because the shortest route to predicting the text is to model the world that produced it.

I think it's mostly accurate. Intelligence does involve compression. Abstraction is compression. Formulating a theory is compression. But we have to be careful about this: there are different kinds of compression. 

One is archival: compressing the text about reality. You capture enough and you have something approaching today's LLMs. Another is compression of reality itself. Finding a deeper structure underneath, such that many facts collapse into consequences of an underlying principle nobody has written down. E=mc² is a compression. But it is not a compression of prior physics texts. It is a compression of reality that prior physics had not achieved. Darwin's natural selection is a compression of biology that no naturalist had written down, even though they had all the specimens. The data was available, to everyone who wanted a look, but the reality compression is what produced the leap.

Ilya's bet is that pushing the level one (archival) compression far enough approximates the second kind. The text encodes the world densely enough that deep compression of the text starts to resemble the world itself[^5]. It may be possible. Water at 99°C and 101°C are two different phenomena - phase changes happen - and something analogous might happen here.

The historical record says otherwise. Copernicus's theory was locally worse than Ptolemy's on the measurements of the day. Centuries of epicycles had been tuned against the observations; Copernicus had to add his own to keep his circles. On any metric anyone alive could compute at the time, the wrong theory won.

A system optimizing for tight fit would not have flipped the frame. It would have stayed with Ptolemy and added the next epicycle. **Compression pressure on archival data would not surface a theory that is temporarily worse at predicting that data.**

### Mechanisms
If compression is the engine, the next question is what kind of process performs the second kind, the one which flips frames rather than tightening them. This is where the LLM story diverges from the older literature on insight, discovery, and intelligence.

[Hadamard](https://www.jstor.org/stable/j.ctvzsmf1c) surveyed mathematicians — including Einstein — in the 1940s about how they actually think. He found that sustained incubation, keeping a problem alive without interruption, was essential to discovery. Break the chain, lose the insight. [Poincaré](https://www.paradise.caltech.edu/ist4/lectures/Poincare_Reflections.pdf) had described the same thing in 1908: breakthroughs arrived only after prolonged engagement, when ideas "hooked together." Kahneman put it bluntly [later](https://a.co/d/0i0o9K4p) — interruption does not pause an effortful chain, it destroys it. [Gruber](https://a.co/d/0eJgOIZG), studying Darwin's notebooks, found the same pattern stretched over months: a mental model he kept alive, fed new observations into, and never fully wrote down. 

[Byers](https://a.co/d/0bqBtPjf), in How Mathematicians Think, argues that insight depends on holding ambiguity and contradiction in mind long enough for resolution to emerge. Offload too early, resolve too fast, and you kill it. [Klein](https://a.co/d/0iCyikuP) found the same thing in experts under pressure — firefighters, military commanders, ICU nurses — who resist offloading decisions to tools. The internal simulation is richer than any externalized representation, and externalizing it prematurely collapses it. [Papert](https://www.media.mit.edu/publications/mindstorms/) made the point from the math classroom: the value of doing arithmetic in your head is not the answer but the cognitive structure you build while the answer is still unresolved. Using a calculator gets the answer but skips the structure-building.

[Simonton](https://www.youtube.com/watch?v=fD5ClBwf6LQ&t=16s) studied creative scientists and found that novel discoveries emerge when many ideas are simultaneously active. The more elements you hold at once, the higher the chance of a productive collision. [Koestler](https://a.co/d/03RqwJ31) called it **"bisociation"** - the collision of two separate frames of reference. The intersection only exists if both chains are held at the same time. [Baddeley](https://pubmed.ncbi.nlm.nih.gov/1736359/) and Engle showed the capacity underneath this empirically. Working memory, the ability to maintain and operate on an active chain of representations, predicts fluid intelligence.

Different researchers, different fields, different populations - but the same phenomenon. There is a mode of cognition where the continuity of the process is what produces the output, not a side effect of it. **Hold multiple representations active, let them collide and restructure, and novel compressions emerge.** Break the chain or thin the set, and they don't.

This is the cognitive-science claim underneath the conversion ratio: 

> you cannot extract more structure per unit of input than you can hold active at once, long enough for the elements to collide.

In LLMs, every inference is stateless[^8]. Chain-of-thought is sequential within a single pass, not sustained engagement over time where a living model takes in new inputs. A reasoning model "thinking longer" is searching a tree within one session. Darwin's continuous model,  fed by every new specimen over months, has no analogue[^7]. 

The temporal structure is completely different. LLM "thinking" is wide but shallow in time. The cognition described above is narrow but deep in time. It suggests that depth is where novel compressions happen. Holding multiple frames at once for extended periods is what lets them collide and restructure into something new.

Prediction and compression are deeply connected, but the kind of compression matters. **Archival compression of text makes a system competent. Reality compression is what produces the leap.** If the leap depends on sustained active representations, unresolved ambiguity, internal simulation, and long temporal continuity, then LLMs may be missing something important. Even if they are extraordinary compressors.

## Animal Intelligence
Then there is the piece of evidence that doesn't fit neatly anywhere, which is why Rich [Sutton](http://www.incompleteideas.net/IncIdeas/BitterLesson.html) keeps pointing at it. A crow solves a novel multi-step problem with a brain the size of a walnut and no text corpus. An octopus opens a jar. A human child generalizes from a tiny, local, embodied stream of experience compared with the scale of an LLM corpus. Whatever these systems are doing, it is not archive compression, because there is no civilizational archive. The data they have access to is a trickle of local, embodied experience, and out of it comes behavior that is intelligent.

Something in biological cognition produces rich, generalizing, adaptive capability without any archive doing the heavy lifting. Whatever that something is, it is much closer to what Chollet means by the conversion ratio than anything current AI exhibits. It is also what Rich Sutton keeps pointing at: the intelligence we are trying to build has an existing biological reference class. That class runs on a budget we are nowhere near matching.

### Basal Cognition

Michael Levin’s work on [basal cognition](https://www.youtube.com/watch?v=RwEKg5cjkKQ) pushes the point even further. Intelligence is not native to the brain. It is a fundamental, biological problem-solving mechanism. Levin shows that even cells and planaria (flatworms) exhibit intelligence. They navigate anatomical space to heal themselves, optimize for survival, and adapt to novel morphological challenges. Without a brain. Without an archive. No training corpus. Something in the system is nevertheless solving problems and generalizing. 

If Levin is right about even a modest version of his claim, **intelligence is not merely non-archival, it is not even exclusively neural.** 

If intelligence is substrate-independent, the multiple independent biological instantiations of it — vertebrate brains, octopus distributed cognition, planaria without brains, slime mold pathfinding, single-cell decision-making in Levin's bioelectric work — are the most valuable evidence we have. They are the only non-engineered examples. They tell you which features are convergent, likely necessary, and which are contingent, just how mammals happened to do it.

Place LLMs against this and the question sharpens. They have the contingent features in abundance — symbolic manipulation, discrete categories, the appearance of central representation. Whether they have the convergent core, or only the mammal-shaped outputs of it, is an open question. The animal evidence does not settle that. What it does is establish that the question is well-posed: 

> There is a bundle, it is substrate-flexible, and the job is to work out whether LLMs instantiate it or only resemble it.

### Optimization Pressures

[Karpathy](https://x.com/karpathy/status/1991910395720925418) presses on a different question. The space of possible intelligences is large, and animal intelligence is a single point in it, shaped by a very particular optimization pressure — billions of years of survival in multi-agent adversarial environments, layered with drives for homeostasis, sociality, status, curiosity, and reproduction. LLMs were shaped by none of this. Their pressures are the statistical structure of human text, reinforcement learning on problem distributions, and something close to A/B testing for daily active users. These produce different shapes of capability, and they should.

The asymmetry that matters most: animals are min-max optimized in environments where failing any task means death. That pressure produces a floor of generality. LLMs face no such floor. Failing to count the r's in strawberry has no consequence to the system. The capability surface that emerges is correspondingly jagged. Strong where the optimization pushed, missing where it did not. The same observation that explains why *LLMs do things no animal can* also explains why they *fall over on tasks any animal would handle*.

Which makes Karpathy's stronger claim land. LLMs are humanity's first contact with non-animal intelligence. We keep confusing ourselves by measuring them against the only intelligence we have ever known. As Karpathy says: "Whatever they are, they are not squirrels."

## A Rashomon situation
The animal evidence says intelligence does not require an archive. Levin says it does not require a brain. Karpathy says it does not have to be biological at all[^9]. We do not have a unifying theory. What we have is a set of partial views — Chollet's conversion ratio, Sutskever's compression, the cognition tradition's sustained-engagement picture, Sutton's scaling-and-search, Karpathy's optimization-pressure framing, LeCun's [world models](https://le-wm.github.io/), Levin's basal cognition — each lit from a different angle, each capturing something real, none of them completing the picture. The problem is not that the views contradict each other; most of them are compatible. 

> The problem is that we are still looking at bundles and composites, things described in terms of other things we also cannot define. We are not yet looking at a primitive.

We have been here before. Energy was a confused aggregate of heat, work, motion, and several other ideas before thermodynamics factored it. Atoms were a philosophical guess for two thousand years before the instruments arrived to see them. Life was vitalism plus mystery before biochemistry got under the hood. In each case the concept looked unified only because nobody could take it apart yet. And when the factoring did arrive, it tended to come fast. Thermodynamics unified the energy picture inside roughly a century, and the modern atomic theory went from speculative to experimentally grounded in about the same span. **The factoring did not destroy the concept. It gave us a real one to replace the folk one.**
Intelligence is currently in the pre-factoring stage. The folk concept worked well enough because the only system that exhibited it kept all its parts bundled together inside one organism. Now there is a second kind of system that exhibits intelligent-looking behavior, and its parts are, for the first time, visible separately. We can read the training data. We can log the runs. We can probe the activations. We can identify the substrate and characterize the failures. None of this resolves the question. It just means the question has, for the first time, a shape an instrument could eventually fit. 
If intelligence is a real primitive rather than a folk bundle, the primitive has to explain every known instantiation. Biological and machine. Under whatever pressure shaped each. General enough to admit a planarian, a crow, a child, perhaps a machine. Specific enough to exclude a thermostat.

### The unit
The atomic question of intelligence is how much new structure a given system can extract from how little experience.

> **Asking whether a model is intelligent is the wrong question. We need to start asking what its conversion ratio is.**

The reframe changes what you measure, what you build, and what counts as progress. A high-conversion system — whatever it is built out of — should do four things. Take a small amount of experience in a domain it has never seen. Extract reusable structure from it. Transfer that structure across novel contexts. And retain it without needing more data, more search, or more scaffolding for every future task. That is the operational shape. None of it is solved. We can't even measure it cleanly yet. But it is the right shape of question, and once it is in front of you, a research direction snaps into focus.
Memory, planning, reasoning, world models are composite descriptions of how a converter expresses itself in a particular regime. Studying any one of them in isolation is studying the byproducts of the operation, not the operation itself. Intelligence research has been stuck in the equivalent pre-factored state for about a century, studying competence aggregates and calling them intelligence. 

The harder question is how you would measure any of this. The instruments we use today measure something else.

### Benchmarks

A benchmark can show that a system dominates inside a frame. It can show command over a domain, mastery of task format, strong search, strong synthesis, reliable performance under scoring constraints. It cannot tell you whether the system has reached something primitive or absorbed another composite layer of competence. 
Read as measurements of layer one, benchmarks are informative. Read as measurements of layer two — what in the system is actually producing the competence — they are silent. They were never designed to speak at that level, and the public discourse keeps asking them to. 
The corresponding mistake in social reactions is the monthly ritual of inflating each new capability into general intelligence or deflating it into autocomplete. Both moves are cheap. The task can remain difficult, useful, and economically enormous. And still live farther from the core of intelligence than either side wants to admit.

## What we actually know
We do not know whether Sutskever is right that prediction, pushed hard enough, becomes understanding. We do not know whether we have built intelligence or whether we have built the most spectacular substrate-leveraging system in history. We do not know whether the sustained-engagement mode the cognition literature keeps describing is something LLMs lack in kind rather than in degree. We do not know whether what Sutton and Levin point at — intelligence without an archive — is a deep structural feature we have not begun to approach.

What we do have, for the first time, is a real version of the question. For most of history, intelligence arrived as a bundle inside a single organism. Now there is a candidate system in which we can, in principle, pull the bundle apart. The question of what intelligence is made of has the shape of a scientific question rather than a philosophical one.

AI may not have solved intelligence. It may have given us the first problem statement precise enough to eventually find out — whether what we have built can compress reality, or only the human archive of it.


[^3]: The narrower claim is that the dominant mode of progress has been substrate enrichment, not engine improvement. From the outside they look identical. Competence went up. That was the scale we were measuring. The question of whether it went up because the engine got better or because the fuel got richer is not a question our benchmarks could answer.

[^1]: In her book “The printing press as an agent of change”, Elizabeth Eisenstein talks about how printing press is a crucial catalyst for transformation in modern Europe as it allowed for cumulative, comparative scholarship.

[^2]: An unintuitive part here is neuroplasticity. Synapses strengthening, networks rewiring as you learn is directly from the model. Learning calculus obviously changes your brain. That is the substrate getting richer. Your brain turned an experience into a skill / capability. The reverse, every person learning something is an alteration to their engine proves too much. And does not explain why the civilizational capability exploded after printing press. 

[^4]: One of the questions I wonder about is why are kids better at learning things than adults. Why is the plasticity different? 

[^5]: Demis Hassabis has proposed an experimental form of this question — the Einstein test: train a system with a 1901 knowledge cutoff and see whether it produces special relativity. It is the cleanest version of Ilya's bet, because the answer is not in the training data. From [this talk](https://youtu.be/JNyuX1zoOgU?si=FODSWjFEi0QkH2Wq&t=2171). 

[^6]: Composition, the kind LLMs are strikingly good at, is recombinant. Connecting two patterns from distant fields, applying a structure from one context to another, recombining the known pieces into something that looks new - LLMs do all of it well. But composition works with a structure that already exists. Producing a new structure is the hard part, and that requires conversion instead of just composition. 

[^7]: The much smaller thing every brain does in the background also has no analogue: creating mental models for everyday experiences. A stream of observations of one domain, compressed quietly over months and years into a model such that the person can act on without ever stating it. The famous instances are the same operation made public (eg: Betteridge's law of headlines). The private ones are happening constantly. LLMs cannot do the famous version because they cannot do the everyday one.

[^8]: BDH (Baby Dragon Hatchling) is a more interesting approach. It is a Hebbian-plastic, sparse, monosemantic graph that updates weights at inference, collapsing the train/inference boundary the way a brain does. But online plasticity is necessary, not sufficient. Hebbian learning gives you "fire together, wire together" i.e. associative growth. A crow outperforms GPT on novel tool use because something in the architecture is doing aggressive structure extraction from a tiny stream of experience. Plasticity is the writing mechanism. The engine is whatever decides what is worth writing. BDH is a substantially better substrate story than vanilla transformers. It is still a substrate story.

[^9]: Substrate-independence claims point in opposite directions depending on whether you reason from outputs or mechanism. Watch the LLM and the human perform the same task and the substrate-flexibility lesson reads "we have it." Watch the flatworm regrow its head with no brain and the same lesson reads "we don't have it, and the bar is lower than we thought." Both observers accept that intelligence is not substrate-bound. They reach opposite verdicts because outputs and mechanism are different evidence.