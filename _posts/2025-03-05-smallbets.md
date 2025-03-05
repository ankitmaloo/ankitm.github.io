---
layout: post
title: "Small Bets about AI"
date: 2025-01-01
---
AI is everywhere and the space is moving so fast, no one knows where all this is headed. Seeing this unfold, here is an idea of small bets. You may know a few things about research, or perhaps you have intuitions, let's have some fun guessing. The process is simple. Use github pages, and put out a post with AI related predictions. Could be as small as "AI will be ubiquitous in all interfaces with an input box." to as bold as "AI would replace humans everywhere". Every bet you make stay recorded and visible. And the changes trackable. I don't mind you changing your prediction, to each his own. So when the future arrives, we'll know exactly what I saw coming vs what I missed. With the commit history as a clear enough proof. So, let's dive in. 

# Prediction #1 (March 2025)
**Claim:** Open AI and other closed (*intential*) model labs would stop providing access to their frontier models via APIs in the coming three years. 
**Date:** 5th March, 2025

**Why:**Models are commoditized today, yes. But the experience is not. In 2023, with the launch of ChatGPT, everyone else more or less copied the chat experience, calling it the most natural way to interact. Then, many startups and incumbents built on top of the same paradigm, essentially showing us better ux that was also adopted by model builders, and ended up in a place where they were competing with the same users for the same commodity. One key factor here was that all the frontier model labs needed this usage data - via API or via User Interface - so that they could power the next generation of their models. With the launch of o1, and then subsequently other reasoning models, things have changed tremendously. 

One, training has become a positive feedback loop, where pruned outputs from one model result in a paradigm that a new model is smarter and better. (hence the clear path to AGI or AlphaGo moment). This has implications: AI labs dont need human mechanical turks anymore. AI labs also fear their advancements can easily be used to train better models via their competition. ergo: only release the model when the curve flattens. Example: It looks like o3 is not going to be released publically. Another implication is how distillation with current techniques is uniquely effective (why o3-mini scores better than o1-pro on benchmarks). A caveat here is open source foundational model developers - who would continue to release the models.

Two, these labs are competing for the same users, and at this stage, controlling the user experience could mean a better LTV. At $20 per user, it's okay if Open AI cannot serve everyone and they gravitate to third party. At the promise of $200 or even $2000, any company should make foremost attempt to make sure they don't explicitly allow for alternatives for what they offer. They may have exclusive agreements with companies at a high usage level, eg: Apple's integration with ChatGPT, but I am pessimistic any new developer would be able to access the latest models in the same way they do today. 

Over the recent weeks, openai and Anthropic have released products like Operator, Deep Research (far better than any of its clones), Claude code, which all point to the attempts to capture the segment directly without a wrapper in the middle.