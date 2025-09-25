---
layout: default
title: "What I am working on"
exclude: true
permalink: /working-on/
---
# What I am working on

> *tl;dr: Autonomy depends on verification. Systems that can detect, explain, and repair their own errors. We are building long horizon agents that learn how to verify (beyond self consistency), and only ship when independent checks pass. 

Richard Sutton [wrote](http://incompleteideas.net/IncIdeas/KeytoAI.html) about the 'Verification Principle' in 2001: 

> An AI system can create and maintain knowledge only to the extent that it can verify that knowledge itself.

This quote is not as popular as the bitter lesson though I believe this is far more prophetic for real world adoption of AI. 

## What I am building

Currently I am fixated on long horizon RL that can autonomously and reliably finish multi step workflows without human intervention. That is, RL systems that can act, verify, and self correct their trajectory in a middle of the workflow to produce a high reliable and accurate output for a given task.

## Why?
Over the last three years, we have been trying to incorporate AI into every workflow possible. Everyone talks about how it is going to increase productivity and be a growth engine for the economy. Yet, the enterprise adoption is still low. Employees who are using AI predominantly also do not report a huge bump in productivity in many cases. This is due to the current modality on how we use it. AI in the current form is probablistic. So, AI models generate an output and human is the QC. There is always a human checking AI's work before passing to the next stage. Thats why we call it augmentation not automation. You still have to double check the work. 

More intelligence was never the bottleneck to automation. It's the reliable, cheap, and autonomous [verification](/_posts/2025-08-20-verification.md) that determines how far we can automate. By definition, any autonomous system cannot have a human in the loop[^1]. The system has to show itself to be reliable and accurate, reaching the outcomes we need autonomously. 

I should clarify that verification here could come from multiple ways: formal verification methods, validation against known constraints, or the agent constructing a task specific verifier (eg: unit test for code, rubrics for certain tasks). This is different from self-consistency (sampling multiple answers and picking the mode) from typical CoT or Constitutional AI from Anthropic, though it's based on similar principles

The important distinction is that this validation step is learned, not hardcoded like today's agents. 

I will posit that: 

> AI Automation will work when a system rarely gets it wrong. And when the system knows it is wrong, and tries to correct itself. 

Rarity brings reliability. Knowability and self awareness brings in trust. 

This is perhaps best reflected in all historical attempts at automation. Factories built in QA checkpoints to confirm everything is in order. If something is amiss, the entire production line stops. Computers are reliable enough with memory protection, error handling, and crash recovery. With Waymo constantly validates sensor readings against expected ranges. When a validation fails, it pulls over. Same goes with autopilots in airplanes too. The abstracted paradigm remains the same. You have a system which flags when something is wrong, humans/machines correct it and the process continues. 

## Long Horizon Tasks

Today most models are very good at fast turnaround and short horizon tasks. We have been making progress with longer duration tasks, as shown in this [METR](https://metr.org/blog/2025-03-19-measuring-ai-ability-to-complete-long-tasks/) report. With long horizon and multi step workflows, it is hard to keep a human in the loop for several reasons. 

- Human QC does not scale: Review costs scales with task complexity. A 20 step workflow requires multiple human checkpoints. This eliminates the productivity gains from using AI in the first place. 
- Intermediate steps often lack clear success criteria that humans can quickly check. Errors often require doing the whole work till that step. Especially for non math or coding use cases. 

You can post train a model on long horizon tasks using RL to make fewer errors, but that is not enough. It is still a probablistic system, prone to making occasional mistakes. The reward is sparse, and the base model does not fully understand where it made the error. 

## Self Verification
In a multi step workflow, a model would drift from its original goal owing to given intermediate context. Model drift, atleast some of it, is useful. You want the model to explore in search of solutions, but you also want model to correct the course every few steps so that the drift is not far from the course. This is where self verification is important. You want a model to detect when the intermediate steps at some checkpoint produces an invalid result, understand why the error, and correct course before continuing. With enough training examples, you could get a model to develop priors about when to verify - instead of every single step. 

In deployment, models can similarly detect their own errors, correct course, and you have systems whose output humans can reliably consume. These RL systems are by design more deterministic because of this verification. The system commits only when the independent verification passes. You can also get these systems to flag low confidence areas which a human can directly review (and add those to the next training run as examples). The goal is to simply bring the residual error down to < 5%[^2] first, and then lower even though the base models are probablistic. Note that it's the error rate, we don't want the system to be robbed of its creativity. Hence, verification needs to be sparse and adaptive. 

In our setup, ‘verify’ is an action with cost. The policy learns when to spend that budget and how to construct the check (tests/rubrics/invariants) to minimize uncaught error under a latency/cost constraint.

## Towards Automation
When a system can reliably complete a multi hour workflow while self correcting any errors, it brings the kind of reliablity and trust lacking in today's AI agents. Humans sets the task and use the final output in downstream tasks. For any flagged areas or exceptions, humans should be able to correct those. Not as a routine quality check, but rare, high signal interventions. This reliability and trust would be hard earned, and it can only happen through verification. 

Having a dependable system unlocks a new lever for progress. Today's AI agents are still novelties, impressive tools but rarely trusted with high stakes tasks. The hope is that they become part of our infra someday. Can only work out if 1/ they can do superhuman things. 2/ They can work in a way to be consistently correct. We are already at the point of asking what we can do next with AI. The real unlock comes when we figure out how we can rely on AI and build on top of it. Reliance at the collective level being the key factor here. 

### Why not let the big labs do it?
This is the debate between a general purpose model which knows how to solve a problem, vs a specialist which knows how to solve your problem. RL is all about exploration, and given the infinite canvas of tasks out there, I think big labs would struggle to cover all of it.  RL has a feedback loop, and the models can self improve. Any path dependent training[^3] will have a compounding effect on the outcomes. 

Moreover, domain specific verification is inherently local. Enterprises have domain specific invariants like compliance rules, schemas etc. These create path-dependent, compounding advantages when your agent learns to construct and reuse them. Then, you can iterate faster with these enterprises, and can train on actual failure modes from deployment. 

*If you would want to know more, happy to talk. Please reach out at ankit@clioapp.ai*

[^1]: Exceptions exist. We call them semi autonomous systems though. 

[^2]: 95% accuracy does not seem ideal at first. I think given where models are today, and the kind of code we all write to make these ensemble systems deterministic, it's a realistic first target to set. Along with highlighting the low confidence areas. There is another metric to look at "uncaught error rate"(UER) which we are striving to drive down to zero. 

[^3]: This sounds like it violates the bitter lesson but it does not. Bitter lesson says that you cannot code lower level modularity when defining tasks at a high level. This is defining high level modularity, and not specifically instructing how the task is to be done. That is being explored the agent in training. 