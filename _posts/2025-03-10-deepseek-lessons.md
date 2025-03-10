---
layout: post
title: "Pattern - Principle Fallacy aka learning the wrong lessons from Deepseek"
date: 2025-03-09
---
Ballon D'Or, awarded by France Football to the best footballer in the world, used to be a very respected award. There were some disputes but it was by and large agreed that whoever got the award was deserving of being called the best in the world. Then came the Messi - Ronaldo era. Both of them were so above the rest of the players that winning trophies was a tiebreak that determined who would get the award. And even that was not always true (cf 2012). This morphed into a new footballing culture by 2020s, post the decline of the two, where fans (and even voters) started pitching players about how winning trophies should be a precursor to winning the award, placing undue emphasis on team success as a pre-requisite for individual accolades. The narrative flipped from "the best player wins the Ballon d'Or" to "you need trophies to win the Ballon d'Or" - confusing the outcome with the cause.

In business, you see a similar phenomenon. People noticed creativity thrived under scarcity mistaking the scarcity part as the cause of creativity. The underlying reason for success could be anything - they got more shots at it, they were talented, they were lucky, or the shot they took worked. Frequently, capital as a constraint is cited as a good thing because of this reason. 

Which brings us to Deepseek. R1 made a lot of noise, but the real work was done weeks before at the launch of v3. The way they announced the models, published the papers, gave everyone an impression that model was built in equivalent of $4M-$5M worth of gpu time. Subsequent weeks, folks in Europe and India, with few frontier model labs, started questioning as to why a Chinese company could do it for so cheap, but not them. The money may be misleading, but the debate came down to export controls. Chinese firms did not have access to H100s, so they had to train on H800, and thus the creativity came through. Thats pretty much the gist of the story. 

Deepseek was constrained technologically not limited by capital. The lessons you draw are going to fundamentally wrong if you misunderstand this. Constraints could be physical, environmental, social, diplomatic etc. It's not the same as being limited by capital. Both can be used interchangeably in some cases, yes. However, they should not be treated the same way. The positive lessons from Deepseek were that they found a way through technological constraints, pushing out a great model modifying a limited hardware. FP8 was brilliant. The lessons the world drew were very different. Verbally put: "Since a chinese lab could build a model cheaply, this proves that models are not limited by capital. So everyone can build equally cheap models (~$5M), especially in countries like India." This argument fails when you understand how people land on such solutions. 

- Almost everything new that Deepseek did, seems like a result of different ideas and iterations, where we know what worked. They had
- - Sufficient resources to run multiple experiments. 
- - The technical talent to innovate within hardware limitations (PTX implementation, FP8 training)
- - The formidability to iterate till they land on a scalable solution. 

- They had access to many GPUs they could experiment on. This way, they could take many shots, and figure out which shot eventually worked. 

- For GPU poor units are by default limited by the number of shots, any shot would require careful deliberation, and teams may miss solutions by rejecting a low probablity solution in the analysis phase itself. 

I agree there is a possibilty of trying things at a smaller scale and then scaling them to save on compute, especially for GPU-poor. The only drawback is that these things don't always scale predictably, so you will be making some educated guesses but you have to see what works at the required scale to be sure. 

## The Shot Taking Economy

Innovation requires sufficient attempts to find what works. When genuinely capital-constrained:

- Each attempt must be meticulously planned

- Failure becomes existentially threatening

- Risk-taking is severely limited

Conversely, with adequate capital, teams can:

- Run parallel experiments

- Fail productively

- Iterate rapidly toward solutions

## The Broader Implications

The lesson from Deepseek isn't that capital constraints foster innovation. Rather, it's that technical constraints can be overcome with sufficient capital for experimentation and talented teams who understand how to navigate those constraints. Countries looking to invest in AI shouldn't aim to replicate artificial scarcity – they should ensure their teams have enough resources to take multiple shots at solving difficult problems, even when facing technical or regulatory constraints.



