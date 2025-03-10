---
layout: post
title: "Lessons from Deepseek"
date: 2025-03-09
---
Ballon D'Or, awarded by France Football to the best footballer in the world, used to be a very respected award. There were some disputes but it was by and large agreed that whoever got the award was deserving of being called the best in the world. Then came the Messi - Ronaldo era. Both of them were so above the rest of the players that winning trophies was a tiebreak that determined who would get the award. And even that was not always true (cf 2012). This morphed into a new footballing culture by 2020s, post the decline of the two, where fans (and even voters) started pitching players about how winning trophies should be a precursor to winning the award, placing undue emphasis on team success as a pre-requisite for individual accolades. The narrative flipped from "the best player wins the Ballon d'Or" to "you need trophies to win the Ballon d'Or" - confusing the outcome with the cause.

In business, you see a similar phenomenon. People noticed creativity thrived under scarcity mistaking the scarcity part as the cause of creativity. The underlying reason for success could be anything - they got more shots at it, they were talented, they were lucky, or the shot they took worked. Frequently, capital as a constraint is cited as a good thing because of this reason. 

Which brings us to Deepseek. R1 made a lot of noise, but the real work was done weeks before at the launch of v3. The way they announced the models, published the papers, gave everyone an impression that model was built in equivalent of $4M-$5M worth of gpu time. Subsequent weeks, folks in Europe and India, with few frontier model labs, started questioning as to why a Chinese company could do it for so cheap, but not them. The money may be misleading, but the debate came down to export controls. Chinese firms did not have access to H100s, so they had to train on H800, and thus the creativity came through. Thats pretty much the gist of the story. 

Deepseek was constrained technologically not limited by capital. The lessons you draw are going to fundamentally wrong if you misunderstand this. Constraints could be physical, environmental, social, diplomatic etc. It's not the same as being limited by capital. Both can be used interchangeably in some cases, yes. However, they should not be treated the same way. The positive lessons from Deepseek were that they found a way through technological constraints, pushing out a great model modifying a limited hardware. FP8 was brilliant. The lessons the world drew were very different. Verbally put: "Since a chinese lab could build a model cheaply, this proves that models are not limited by capital. So everyone can build equally cheap models (~$5M), especially in countries like India." This argument fails when you understand how people land on such solutions. 

Let me break down what actually happened at Deepseek:

1. They had money. A lot of it. But couldn't buy H100s.
2. They ran tons of experiments on H800s trying different approaches.
3. Most of these experiments failed - that's normal and expected.
4. Eventually, they cracked FP8 training and other optimizations.
5. The $4M-5M figure? That's just the final successful run.

The real cost includes all the failed experiments, the engineering time, and the infrastructure. It's like saying a hit song only took 3 hours to record, ignoring the months of studio time that went into getting it right.

Here's what you need to actually replicate Deepseek's success:

- Enough compute to run multiple parallel experiments
- Money to burn through failed attempts
- A talented team that can innovate within hardware limits
- Time and patience to iterate until something works

The constraint of not having H100s pushed Deepseek to find creative solutions. But they had everything else they needed. That's very different from being capital-constrained where you can't even afford to try different approaches.

## The Shot Taking Economy

Innovation requires sufficient attempts to find what works. When genuinely capital-constrained:

- Each attempt must be meticulously planned
- Failure becomes existentially threatening
- Risk-taking is severely limited

Conversely, with adequate capital, teams can:

- Run parallel experiments
- Fail productively
- Iterate rapidly toward solutions


## Looking Forward

If you're building AI infrastructure in any country, the lesson isn't "do it cheap." The lesson is "make sure you have enough resources to take multiple shots." You might face different constraints - regulatory, hardware, or talent. But you need the capacity to experiment and fail repeatedly before finding what works.

Success rarely comes from the first attempt. It comes from having enough shots at the goal. Deepseek didn't succeed because they were constrained - they succeeded because they had enough resources to work around their constraints.

