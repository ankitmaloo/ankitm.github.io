---
layout: post
title: "Small Bets about AI"
date: 2025-03-05
---
AI is everywhere and the space is moving so fast, no one knows where all this is headed. Seeing this unfold, here is an idea of small bets. You may know a few things about research, or perhaps you have intuitions, let's have some fun guessing. The process is simple. Use github pages, and put out a post with AI related predictions. Could be as small as "AI will be ubiquitous in all interfaces with an input box." to as bold as "AI would replace humans everywhere". Every bet you make stay recorded and visible. And the changes trackable. I don't mind you changing your prediction, to each his own. So when the future arrives, we'll know exactly what I saw coming vs what I missed. With the commit history as a clear enough proof. So, let's dive in. 

# Prediction #1 (March 2025)
**Claim:** Open AI and other closed (*intential*) model labs would stop providing access to their frontier models via APIs in the coming three years. 

**Date:** 5th March, 2025

**Why:**Models are commoditized today, yes. But the experience is not. In 2023, with the launch of ChatGPT, everyone else more or less copied the chat experience, calling it the most natural way to interact. Then, many startups and incumbents built on top of the same paradigm, essentially showing us better ux that was also adopted by model builders, and ended up in a place where they were competing with the same users for the same commodity. One key factor here was that all the frontier model labs needed this usage data - via API or via User Interface - so that they could power the next generation of their models. With the launch of o1, and then subsequently other reasoning models, things have changed tremendously. 

One, training has become a positive feedback loop, where pruned outputs from one model result in a paradigm that a new model is smarter and better. (hence the clear path to AGI or AlphaGo moment). This has implications: AI labs dont need human mechanical turks anymore. AI labs also fear their advancements can easily be used to train better models via their competition. ergo: only release the model when the curve flattens. Example: It looks like o3 is not going to be released publically. Another implication is how distillation with current techniques is uniquely effective (why o3-mini scores better than o1-pro on benchmarks). A caveat here is open source foundational model developers - who would continue to release the models.

Two, these labs are competing for the same users, and at this stage, controlling the user experience could mean a better LTV. At $20 per user, it's okay if Open AI cannot serve everyone and they gravitate to third party. At the promise of $200 or even $2000, any company should make foremost attempt to make sure they don't explicitly allow for alternatives for what they offer. They may have exclusive agreements with companies at a high usage level, eg: Apple's integration with ChatGPT, but I am pessimistic any new developer would be able to access the latest models in the same way they do today. 

Over the recent weeks, openai and Anthropic have released products like Operator, Deep Research (far better than any of its clones), Claude code, which all point to the attempts to capture the segment directly without a wrapper in the middle. There is a case to be made here that startups like cursor,perplexity figured out the product fit, and now the foundational companies want to eliminate the middlemen especially for the use cases they know has value. 

**Caveats:** I am specifically pointing to the leading models. Older models may still be available on API, but the best ones would not be. 

### Some supporting opinions
- Sama's [tweet](https://x.com/sama/status/1897036361506689206) about converting the subscription to credits
- Naveen Rao, Databricks' VP of Gen AI, [tweeted](https://x.com/NaveenGRao/status/1886544584588619840) this a month back so not really a contrarian/novel prediction on my end. 

### Resolution (June 2026): Directionally right, a year early, one residual.

**What happened:** Anthropic shipped its frontier model in two [trims](https://www.anthropic.com/news/claude-fable-5-mythos-5). Fable 5 is generally available with additional safety measures for dual-use capabilities. Mythos 5 - the same underlying model without those measures - is available only to approved organizations. The best version of the frontier model is no longer something you can simply buy access to. You apply, and they decide.

**Score:**
- *Direction:* right. Differential access to frontier capability, with the full variant withheld from general access.
- *Structure:* right, almost clause for clause. The caveat above said "older models may still be available on API, but the best ones would not be." Realized as: the constrained trim is public, the unrestricted trim is approval-gated. And an approved-organizations list is the "exclusive agreements with companies at a high usage level" mechanism, different paperwork.
- *Timing:* early. The window was three years from March 2025. I expected this around 2027. It happened in 2026, inside the window, ahead of my center. Logging it as a timing miss of about a year, in the direction predictions rarely miss.
- *Mechanism:* the residual. I predicted competitive motive - distillation fear, controlling LTV. The stated motive is dual-use safety. The two produce seemingly identical policies (gate the full artifact, meter it through approval), they are not mutually exclusive, and only one of them ever appears in a press release. Watching whether the moat motive surfaces as more capability gets gated.

**What stays open:** Frontier models in constrained form are still on API, so the maximal version of this bet - the best models fully off public APIs - runs until March 2028. The Fable/Mythos split is the structure arriving; whether it tightens further is the live question.

**Bonus:** The pattern runs deeper than one company's trim, so recording the rest of it. Google trained a coding model on its internal codebase that it cannot release at all - the model is a compression of the monorepo, so releasing the model is releasing the data. Anthropic, unable to find good public datasets for frontier problems, trained on its own internal data and restricted the resulting capability over leak concerns. OpenAI now talks about internal models above the public Pro tier as a normal thing. And the Mythos that shipped is not the Mythos they first described: the public version is trimmed down following safety analyses on the original, with the original available through Project [Glasswing](https://www.anthropic.com/glasswing).

Two additions to the scoring:

1. The tiering is a ladder, not a split. Public trim, approved trim, program access, internal only. The "best ones would not be available" clause is realizing as a gradient gated by trust level, not a binary.

2. A mechanism I did not predict. In March 2025 I gave competitive motives - distillation fear, controlling LTV. The labs say safety. What is actually emerging is a third driver: data provenance. Public data ran out for frontier capability, so frontier models are increasingly trained on internal and proprietary data, and a model is a lossy copy of its training set. Release the model, leak the data. This couples capability to unreleasability by construction - the better the model, the more private substrate it embodies, the less of it can ship. If this holds, the maximal version of this bet stops being a strategy the labs might choose and becomes a structural consequence of where frontier training data now comes from.

# Prediction #2 (March 2025)
**Claim:** People espousing "App layer would win" have gotten it wrong in a major way. 

**Date:** March 7, 2025

**What:** In this case, I need to clarify the what first. Over the last two years, there is a big debate outside of the AI community but in the software community whether or not people should train their own models. Initially finetune was a way to go, but that hype died down too. That led people to the conclusion (not unjustifiably) that the layer at which products would win and create most value would be the application layer as opposed to model layer (foundational model builders) or the infra layer (semis, gpus)

This by no means is a consenses argument, but I see this pushed through everywhere, especially when I talk to early stage founders, investors, or just builders. World's leading acclerator has been actively pushing this narrative and accepting startups on this theme in the last two years. 

Breaking it down is important, because I have a feeling the vagueness of the current argument might see proponents claiming a win when they  got it wrong. Their thesis is (some may disagree) that builders need not focus on customizing models at all (with the assumption that models are commoditized) and instead focus on integrations, user experience, and understanding of a company's process. Both are not mutually exclusive ideally, but in this scenario when I see proponents talking about it, they implicitly mean you call the model API, and then build the tooling and framework around it. Hence, you see so many RAG based startups which are not looking to alter model behavior at all but instead building in a manner that gets them to integrate the latest models as soon as they are released. 

The caveat I want to make clear is eventually there are some products which would win and have app layer components. The bet is that they would have found ways to modify the model behavior in a specific way via finetuning, knowledge expansion (how we are doing it at Clio AI), or some new novel method. If that happens, the original megaphones talking about "app layer would win" i.e. the "tooling around an llm" would win would have gotten this wrong in a massive way. 

Yes, this follows from first prediction. 

**Why**: My thought process here is basic. In probablistic Deep Learning models, you capture the most value the closer you can get to a 100% accuracy. Eg: Recommendation engines. The better your recommendations, the more viral the product is. At this stage of LLMs, original models are ~70-75% accurate (highly accurate in marketing and code, not so much elsewhere). With tooling, right prompting techniques, and RAG with so many hacks, you got them to about 80%-85% accurate. At the user experience level, you managed to highlight the errors early, establish guardrails, and that made them easy to catch the errors, but not the accuracy. The models improved and that increased the quality of cases the setup worked for, just that accuracy did not improve as much. Indeed, the major use cases for AI are where it's quick to catch and fix the error (code) or places where it's okay to be approximately right. Not many companies are using LLMs for high stakes tasks where a mistake is not immediately obvious or very costly. 

To get to a 90%-95% accuracy, you have to address the fundamental issues with how a model generates output. That is, changing the model behavior at the weights level instead of just prompting. Thats the bet. Whoever does it would capture more value since people would move to the company which increases reliability. 

**Caveats:** A couple of players would win on the app layer - only because they got adopted so fast that they could then customize models to deliver performance almost as good as the products which feature a customize product. You are seeing this play out in real time when Perplexity is competing with Openai's Deep Research.  

# Prediction #3 (August 2025)
**Claim:** AI progress in the next few iterations is going to look like stalling because AI is improving in areas an average person cannot reliably judge and hence the improvements seem incremental. 

**Date:** August 14, 2025

**What:** This, coming after GPT-5, seems much less of a bet and more of a conclusion. I think I am late in recognizing this, and there are many voices saying the same, but there are even more voices about how the progress has stalled. For me, I have been at this end in 2018, where things seemed to stall in NLP and they actually did. (pity we did not pick up on transformers at that point). 

Coming to what I see: many people found GPT-5 as underwhelming. It's a system of models and not one model. There is a router which means openai could not make it work at scale. The AI curve and progress is stalling. I think you would have heard the usual arguments here. My take - something I felt since the release of o3 and Opus 4 - is that I could not longer feel excitement about a new model simply because I dont have great questions to test the model on. You can only test someone's intelligence when they are at your level, you can only guess if they are smarter than you relatively, not how smart. A controversial claim I believe is that models are already that far ahead that I cannot tell anymore by simply seeing the output. Yes, an expert could tell the difference, thats where models are good at passing the eye test but not the smell test. 
The other side of this is how the axes models are getting good at is not something people would use on a daily basis. Understanding genome structure, proving difficult theorems, hypothesizing new research approaches etc. The thing relevant for them was reduced hallucinations, that too something you only appreciate if you look at things from a reliability pov and not capabilities. Don't get me wrong, it's huge, just not as exciting. 

**Why?** Some very basic reasons:

1. **Reference point poverty:** benchmarks are saturated. Getting from 90% to 91% might be exponentially hard, but to humans it seems a small level of progress. There is no shared intuition of hard, and a progress from 92% on MMLU to 98% feels like an expected curve and not amazing anymore. 

2. **Real world lag:** GPT-5 is very good at agentic tasks as they say. We would only know when used in real world setting and that too by professionals. Ideally, we should see more long horizon agents, agents better at chained tasks, more automation, just by looking at GPT-5's release. There are more to follow - Gemini 3, Claude 4.x for both Sonnet and Opus (Opus 4.1 is released) - all getting better at more agentic tasks and reliability. Reliability shows up in applications not demos. 

3. **Narrative:** This is on Openai because clearly they hyped it up way too much. Anything the model could do they would not have matched it up to the expectations they set for themselves. 

**How to know if the progress has really stalled?** I don't have a very good answer to this. We will need two things here to be true at the same time: 1/ No measurable uptick in unsaturated benchmarks like HLE and Frontier Math, no new awards or increased scores in IMO, IOI, etc. by the newer models. 2/ If you present outputs from this generation of models and a previous generation models on the same prompt, <50% laymen would pick the latest outputs.

**Caveats:** All of this is perceptive. We will probably crack a few things in reasoning space (because we are at 0.3% of compute of what was used to train AlphaGo so a lot of potential there) and the narrative and perception could shift immediately. Same goes with a cool robotics demo, an agentic demo which is predicated on using the models in a unique and creative manner, all these could change the perception.

# Prediction #4 (June 2026)
**Claim:** AI labs' subscription products (ChatGPT Plus/Pro, Claude Pro/Max, and the coding agents on top of them) are individually gross margin positive (low margins) today, because subscriptions monetize spare capacity on the same clusters that serve the API. When the unit economics eventually become public - leaks, filings, disclosures - subs will not show up as a loss leader.

**Date:** June 12, 2026

**Why:** My thought process here is basic. LLM API demand is bursty. With continuous batching, the marginal cost of filling an empty slot in a batch is close to zero - the forward pass runs anyway. What a subscription session actually consumes is KV cache residency, not a pro-rata share of the cluster. So you price the API to be profitable at roughly 40% utilization (because of spiky nature of the demand, you should be able to serve at peak instantly), and everything above that is capacity you get to sell twice. Subscriptions are how you sell it: flat rate, throttleable, deprioritized at peak. The API is the full fare seat. Subs are standby passengers on seats that were flying anyway. This is yield management - airlines, electricity, AWS spot instances. Standard accounting in every capacity business except, apparently, this one. The tell is the priority / service tier parameter. And wait times are low because of continuous batching.

**What everyone gets wrong:** Every public take prices subscription tokens at API-equivalent value and subtracts. First the discourse said labs sell subs at huge losses. Then it became API margins covering sub losses. Now it is high API margins letting labs discount. Three takes, all erroring the same: valuing tokens that fill idle slots as if they displaced API revenue. That is cost accounting done with a transfer price.

**Evidence you can check today:**
- Cache reads are priced at ~10% of input list price. If cost to serve were uniformly ~25% of list (the standard assumption in these analyses), labs would be selling cached tokens below cost, at scale, on their heaviest workload. They are not. The pricing page shows the marginal cost of a cache-resident token is far below the average cost of a fresh one.
- Subscriptions are built as interruptible products: weekly limits, 5-hour windows, model downgrades under load, deprioritization. That is the design signature of yield management, not of a loss leader.
- The commercial-use restrictions on subs are price discrimination fences. You only need to fence two products this aggressively when they share a fleet.

**Predictions that follow:**
1. Sub rate limits tighten in lockstep with API demand peaks (model launches, big releases) and loosen as fleets grow. Watch the timing, not the announcements.
2. Flat-rate products proliferate as clusters outgrow API demand.

**How to know if I am wrong:** Two ways. One, disclosure: if filings or credible leaks show subscriptions gross margin negative as a product line, I am wrong. Two, regime change: this model holds while subs are the filler workload. If agentic coding turns subscription demand into base load - agents running 24/7, capacity bought because of sub growth - then the marginal cost story flips and subs start carrying real capacity costs. The tell is the limits. Labs tightening limits means the model is holding. Labs letting sub demand drive capacity planning without throttling means the spare-capacity story is over, and so is this bet.

**Caveats:** Gross margin, not net. Nothing here says labs are profitable overall - training capex and free tiers are a different conversation. And "individually GM positive" is about marginal cost on a shared fleet, not what an allocating accountant would produce.

**What prompted writing it down:** SemiAnalysis [published](https://x.com/SemiAnalysis_/status/2064815044085318040) subscription margins by utilization, assuming cost to serve = 25% of API-equivalent value. The entire red half of that chart is downstream of that single assumption, and the deepest red cells describe usage levels the rate limits exist to prevent.

# Prediction #5 (June 2026)
**Claim:** AI's impact on GDP stays hard to see. Not because the impact is small, but because of where it lands. In competitive markets, AI adoption is table stakes: every firm has to spend to hold relative position, no firm gains relative position, and competition passes the savings through to prices. The gains are there, but they show up as consumer surplus (which GDP measures badly) and as revenue to the AI suppliers. Measured GDP registers the building of AI - capex, datacenters, lab revenue - far more than the using of it.

**Date:** June 12, 2026

**Why:** Basic game theory. Adopting AI is the dominant strategy: if your competitor adopts and you do not, you cede advantage; if both adopt, neither gains. The equilibrium is everyone spending and nobody moving, an arms race where each firm's decision is individually rational and collectively self-cancelling. And because the underlying tech converges - everyone is renting roughly the same models - adoption cannot differentiate, only non-adoption can hurt. Firms cannot price higher off AI either, unless the industry is concentrated enough to play a coordination game. So the cost savings get competed into prices, the consumer pockets the difference, and the P&L shows a new line item where the advantage was supposed to be.

Buffett had this exact structure. I remember it as two stores and an escalator - one installs it, so the other must, and neither gains a customer. The canonical version is the 1985 Berkshire [letter](https://www.berkshirehathaway.com/letters/1985.html) on the textile mills: every competitor's machinery investment was rational alone and neutralizing together, "just as happens when each person watching a parade decides he can see a little better if he stands on tip-toes". In an arms race, the only party that reliably profits is the arms dealer. (See Prediction #4 for the arms dealer's books.)

**What this predicts:**
1. Adoption statistics diverge from productivity statistics: adoption goes near-universal while total factor productivity barely moves.
2. AI spend becomes a standard cost line, like cloud - present on every income statement, absent from every margin expansion story in competitive sectors. Where AI does expand margins, look for market concentration or a coordination game, not better AI.
3. The AI contribution visible in GDP accounts stays concentrated on the supply side: datacenter capex, semiconductors, lab revenue. 

**How to know if I am wrong:** Broad-based margin expansion in competitive sectors attributable to AI. TFP acceleration that tracks the adoption curve within a couple of years. Firms holding durable pricing power off AI without market concentration. Any of these and the gains are not being competed away.

**Caveats:** Genuinely new categories - products that could not exist before - are not competed away the way efficiency gains in existing competition are. That is where real measured growth would come from, and the claim does not cover it. Same for concentrated industries, where the coordination game pays. The claim is about efficiency gains in competitive markets, which is most of the economy.

# Prediction #6 (June 2026)
**Claim:** AI breakthroughs under the current paradigm come exclusively from the fast-verifier class. The frame-flips whose verification takes years to decades - the Copernicus, Wegener, Darwin class - will not come from AI systems. Not because models cannot generate the claims, but because nothing in how they are trained, deployed, or believed can survive the latency. Corollary, wagered with it: models are already producing correct slow-verifier claims that get discarded as hallucination, and at least one will be vindicated retroactively after a human independently arrives at the same place.

**Date:** June 12, 2026

**Why:** Acceptance of a revolutionary idea tracks verifier latency, not idea quality. The history is the dataset. Copernicus was locally worse than Ptolemy on the measurements of the day - the simplicity payoff arrived with Kepler and Newton, long after. Wegener had continental drift right through fifty years of rejection, until seafloor spreading fired the verifier. Darwin's selection ran weaker than Lamarck on the day's evidence until Mendel was integrated. Einstein is the contrast case that proves the rule: a frame-flip that carried its own verifier. The math was unbeatable on arrival, Mercury's perihelion was already on the books, Eddington fired within four years. Einstein skipped purgatory not because he was more right than others, but because his verifier was faster.

Run current AI through that filter:

1. Training cannot reward what the verifier cannot grade within the episode. A claim whose payout arrives in a decade is invisible to every loop in the pipeline.
2. Compression pressure on archival data actively disfavors theories that are temporarily worse than the incumbent. A model trained to fit the record keeps Ptolemy and adds an epicycle.
3. Provenance. A slow-verifier claim is unverifiable at publication by definition, and unverifiable claims get discounted by the standing of the source. AI is the lowest-standing source there is. Its Wegener-class claims will not be rejected - they will not be evaluated. They get filed as hallucination, which is the name we give to unverifiable claims from sources without standing.

And the structural lock underneath the other three: holding a heresy through its latency requires being the same entity for the whole interval. Wegener needed thirty years of being Wegener - same name, same stake, same memory of every rejection. No model is the same model for thirty weeks. Versioned, frozen, replaced; each generation is a new employee with no memory of the heresies its predecessor filed. Frame-holding across latency requires a continuity that nothing in the deployment paradigm provides.

**The data we already have:** The first major AI result - the unit distance counterexample - was maximum fast-verifier class: a construction that checks mechanically, accepted by the field within weeks. Predictable from the shape of the filter, and predicted by it.

**What this predicts:** Log the verification latency of every AI-attributed scientific milestone. The distribution stays pinned under roughly a year - proofs, code, benchmark physics, anything a machine or a quick experiment can grade. Nothing of the form "AI proposed it, the field rejected it, slow evidence vindicated it a decade later."

**How to know if I am wrong:** The Wegener event: an AI-originated claim, rejected by expert consensus at publication, vindicated years later by slow evidence, with provenance intact. If that happens this bet dies, and I would be glad to bury it, because it would mean the latency locks are breakable. The corollary can resolve much earlier: a human independently arrives at a frame-flip, someone mines old model outputs, and finds the claim pre-stated and laughed off. The day that happens, the hallucination/insight boundary is a going to be a field of study.

**Caveats:** Formal math looks like an exception and is not. A proof assistant collapses verifier latency to zero, so mathematical frame-flips are Einstein-class by construction. They count toward the fast side of the distribution, not against the bet. And none of this says the models lack the ideas. The bet is about the filter. The generator might be fine. The filter is the world.

Fitting that the bet about verifier latency is the one entry on this page that cannot resolve quickly. The corollary can land any year now. The main claim about 30 years.