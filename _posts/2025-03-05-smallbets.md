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

# Prediction #2 (March 2025)
**Claim:** People espousing "App layer would win" have gotten it wrong in a major way. 

**Date:** March 7, 2025

**What:** In this case, I need to clarify the what first. Over the last two years, there is a big debate outside of the AI community, but in the software community whether or not people should train their own models. Initially finetune was a way to go, but that hype died down too. That led people to the conclusion (not unjustifiably) that the layer at which products would win and create most value would be the application layer as opposed to model layer (foundational model builders) or the infra layer (semis, gpus)

This by no means is a consenses argument, but I see this pushed through everywhere, especially when I talk to early stage founders, investors, or just builders. World's leading acclerator has been actively pushing this narrative and accepting startups on this theme in the last two years. 

Breaking it down is important, because I have a feeling the vagueness of the current argument might see proponents claiming a win when they  got it wrong. Their thesis is (some may disagree) that builders need not focus on customizing models at all (with the assumption that models are commoditized) and instead focus on integrations, user experience, and understanding of a company's process. Both are not mutually exclusive ideally, but in this scenario when I see proponents talking about it, they implicitly mean you call the model API, and then build the tooling and framework around it. Hence, you see so many RAG based startups which are not looking to alter model behavior at all but instead building in a manner that gets them to integrate the latest models as soon as they are released. 

The caveat I want to make clear is eventually there are some products which would win and have app layer components. The bet is that they would have found ways to modify the model behavior in a specific way via finetuning, knowledge expansion (how we are doing it at Clio AI), or some new novel method. If that happens, the original megaphones talking about "app layer would win" i.e. the "tooling around an llm" would win would have gotten this wrong in a massive way. 

Yes, this follows from first prediction. 

**Why**: My thought process here is basic. In probablistic Deep Learning models, you capture the most value the closer you can get to a 100% accuracy. Eg: Recommendation engines. The better your recommendations, the more viral the product is. At this stage of LLMs, original models are ~70-75% accurate (highly accurate in marketing and code, not so much elsewhere). With tooling, right prompting techniques, and RAG with so many hacks, you got them to about 80%-85% accurate. At the user experience level, you managed to highlight the errors early, establish guardrails, and that made them easy to catch the errors, but not the accuracy. The models improved and that increased the quality of cases the setup worked for, just that accuracy did not improve as much. Indeed, the major use cases for AI are where it's quick to catch and fix the error (code) or places where it's okay to be approximately right. Not many companies are using LLMs for high stakes tasks where a mistake is not immediately obvious or very costly. 

To get to a 90%-95% accuracy, you have to address the fundamental issues with how a model generates output. That is, changing the model behavior at the weights level instead of just prompting. Thats the bet. Whoever does it would capture more value since people would move to the company which increases reliability. 

**Caveats:** A couple of players would win on the app layer - only because they got adopted so fast that they could then customize models to deliver performance almost as good as the products which feature a customize product. You are seeing this play out in real time when Perplexity is competing with Openai's Deep Research.  
