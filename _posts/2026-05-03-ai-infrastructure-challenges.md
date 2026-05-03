---
layout: post
title: "AI as a Solution for Physical Infrastructure Challenges"
subtitle: "What the automobile teaches us about predicting transformative technology — and where AI might actually move the needle on energy infrastructure"
date: 2026-05-03
tags: [AI, Energy, Infrastructure, Policy, Grid]
excerpt: "AI is a transformative technology, but we're probably focused on the wrong limitations when trying to predict its impact. From someone who works with energy engineers every day, here's where I think it will actually matter — and where it won't."
---

AI is a transformative technology, but there's a lot of hype and uncertainty about where and how it will be transformative. Some of the more promising claims are around drug discovery and commercial efficiency gains. Some people claim it will solve all of the world's problems. Others argue that the "efficiency gains" are an illusion driven by an endless hype cycle. The truth is that it's hard to imagine what changes in a world where many of the fundamental rules that have acted as guardrails and barriers are suddenly eliminated.

In her keynote at NeurIPS in December 2025, Professor Zeynep Tufekci from Princeton laid out how technology doesn't have to have superhuman intelligence to cause massive societal change and destabilization. She pointed out that systems develop within the context of their limitations, and that it's difficult to predict the consequences of eliminating those limitations. More importantly, we often focus on the *wrong* limitations when trying to predict the impact of a new technology.

At the turn of the 20th century, people were obsessed with whether cars could travel faster than horses — identifying speed as the primary limitation of traditional transportation. While cars ultimately beat horses in the speed race, the limitation they largely eliminated was the need to be fed, stabled, and cared for that prevented people from living in the suburbs and riding into the city to work. LA traffic likely moves slower than a horse, but the automobile transformed the structure of American civilization in ways that were difficult to predict when they first showed up on the scene around 1908.

Similarly, the only problems we know how to solve are the ones in front of us. Early infrastructure planners didn't anticipate teenage loneliness and helicopter parenting as products of car-centric societies. The limitation of having to share limited communal space near city centers was suddenly eliminated. People could own their own small home away from city smog and drive in when they needed to. The problem they were currently facing could be solved — so they solved it, without awareness of the problems it would create down the line.

This feels incredibly similar to where we are with AI right now. We have hypotheses about what it can accomplish, but chances are we're focused on the highly salient things in front of us, and the more important impact will be something more subtle that emerges from the breaking of constraints we pay little heed to. AI may very well help us discover drugs faster or format spreadsheets, but what limitations does it actually eliminate — and which ones remain?

## The Policy Bottleneck Problem

Hank Green has raised the point that many of our biggest problems are not technological. They remain unsolved not because we lack the means, but because people push back and policy maintains a status quo that advantages those in power. How will AI solve the housing crisis? We know how to build houses. How will AI eradicate TB? We have effective drugs. These aren't technological problems — they're human ones.

I'm not a policy person, but I do have a somewhat niche perspective on how AI can be used to accelerate the highly policy-constrained domain of energy infrastructure development. There are areas where AI can help us do what isn't yet possible. But it also has potential in the construction of infrastructure we know very well how to build — infrastructure that primarily suffers from the same challenges facing all major construction: local opposition, regulation, and budget.

## Energy Infrastructure Is Genuinely Broken

Energy infrastructure has been disinvested in for over half a century. Most of our transmission lines were built in the 1960s and 1970s. Many hydropower facilities are almost a hundred years old. Only three new reactors have come online in roughly the last thirty years: Watts Bar Unit 2 in 2016, and Vogtle Units 3 and 4 in 2023 and 2024 — the latter taking over 14 years and more than $35 billion to build.

While there's been a recent surge in clean solar, wind, and natural gas generation, connecting these generators to the grid requires substations and transmission lines. The backlog for interconnection studies that approve construction of that infrastructure stretches to a median of five years from request to commercial operation. Bill Gates has called transmission construction the number one bottleneck to clean energy adoption in the US.

So why is it so hard to build? No single answer covers it.

One obvious factor is NIMBYism. No one wants a high-voltage transmission line near their property, regardless of whether it connects a solar farm or a coal plant. There's an entire coalition — [Stop B2H](https://stopb2h.org/) — that fought a 290-mile Idaho Power transmission line all the way to the Oregon Supreme Court, which ultimately affirmed construction approval after roughly 17 years of permitting battles.

Grassroots movements against new infrastructure can be incredibly powerful. In *Abundance*, Ezra Klein and Derek Thompson trace how public-interest law firms and advocacy organizations transformed local opposition into layers and layers of policy that limits new construction of any infrastructure — with the Chokecherry and Sierra Madre wind project in Wyoming, stuck in permitting limbo for roughly 18 years, as a prime example.

I work closely with the electrical engineers who design this infrastructure, and have heard and seen firsthand the pain points they deal with. Transmission engineers' number one concern when planning a route is identifying whether or not a pole placement will trigger a lawsuit. They'll phone local groups, check for cultural heritage sites, wetlands, and other landmarks, design a route, then redesign it — sometimes for years — as locals push back. I've sat with exasperated engineers as they described how months of work evaporated when land approvals fell through and an entire line had to be rerouted.

Another group of engineers performs the independent studies required by regulation for new wind, solar, and gas generation sites. They receive anywhere from a hundred to 10,000 documents from a client — leases, amphibian surveys, electrical design specs — and have to produce the same standardized report for every project. Reviewers spend weeks finding the specific documents they need. Every client structures their data rooms differently.

And then there's the interconnection study backlog itself. As of 2024, about 2,300 GW of generation and storage was actively seeking interconnection in the US — more than the entire existing US power plant fleet. Solar and battery storage make up about 80% of that queue. According to Lawrence Berkeley National Lab's *Queued Up* analysis, 77% of projects that submitted requests from 2000–2019 had been withdrawn by 2024 without ever reaching commercial operation. Engineers working these studies describe the core pain not as running the studies themselves, but as dealing with incomplete information, conflicting data sources, and constant rework when adjacent studies complete and change the grid picture.

"Move fast and break things" is the antithesis of how utilities, engineers, and operators work. They start every meeting with a safety tip. The grid is the most complex physical machine ever built and is genuinely very sensitive to changes.

## Three Things AI Can Actually Do Here

I don't know whether AI will solve these challenges. But I can speak to what I've seen as someone who's spent the past two years talking every day with engineers about what they do and how AI might help them do it better.

There are three concrete things I see AI doing in the energy space.

### 1. Model the world and detect patterns in data

One of the most common AI use cases actually deployed in the field by utilities is machine vision for asset fielding and monitoring. With just the time it takes to snap a picture, you can pull out all relevant information about what equipment is on a utility pole or whether there's rust on a transmission tower. Augmented reality lets field workers go to a physical site and use imagery to model what's there, where it's positioned, and what condition it's in. The mixture of cost and human error makes manually inspecting every bolt on every utility pole both error-prone and expensive. AI removes significant manual effort from that challenge.

Going further, AI-enabled GIS and sensor data can expand this view dramatically. A transmission engineer with access to an accurate GIS system that automatically shows where wetlands are can move much faster than one who has to rework a whole line because the wetland wasn't obvious from satellite imagery.

LLMs add a new layer: being able to ask a system to find all documents in a data room related to environmental studies and highlight mentions of at-risk species or waterways can allow an engineer to move through an independent study far more quickly than digging through thousands of documents manually. AI might miss things — but humans in these conditions miss things too, and AI is improving at document-intensive tasks while human bandwidth stays constant.

Beyond data collection, AI can find patterns and make predictions. Better forecasting of solar irradiance, wind output, and demand is essential for integrating variable renewables into the grid. It also makes the economic case for specific technologies easier to demonstrate — a better cost-benefit analysis of a variable solar farm versus a dispatchable gas plant matters politically, not just technically.

### 2. Optimize

Once you have a digitized model of the world, you can apply optimization algorithms over it. Engineering is an art, not a science — the solution space is vast and it's impossible to test every possibility. Engineers run N-1 studies, testing how the system behaves if any single component fails. N-k studies, considering concurrent failures, are usually out of the question even though failures in one part of the system often cascade to another.

Engineers must use their intuition and experience to explore the most promising parts of the state space and present a solution they're confident will work. With distributed energy resources entering the picture — local solar and batteries as alternatives to pumping more current through overloaded lines — you now need to model a vast solution space with time as a dimension.

AI optimization with engineering validation can help run more studies faster and converge on more defensible solutions. It won't produce one objectively correct answer — the input parameters are too subjective for that. But it will give engineers a set of options from a wider exploration of the search space that are more likely to be close to optimal.

Leidos, where I work, has developed an optimization platform for transmission line design that leverages GIS to create a land-use-aware routing tool. Previously, it could take electrical engineers 120 hours to design a single mile of transmission line. Now, they can run multiple designs simultaneously with different conductor types and structure families and compare the outputs in a single report. More importantly, engineers can now use their expertise to evaluate and compare multiple optimized routes rather than picking one approach upfront and designing around it. [This video](https://www.youtube.com/watch?v=hKAr-pIYse8) shows the platform in action.

Similar optimization use cases show up in battery management, HVAC control, and economic dispatch. These tools make projects more resource-efficient, faster to complete, more defensible, and — where they open up the capacity to run more studies under different conditions — more reliable.

### 3. Put tools in the hands of experts

This is where I think AI has the most potential, and possibly the most underappreciated potential.

For decades, software has been stuck behind experts — software engineers, data scientists, AI practitioners — who are necessary to create automation. And while they're experts in their own fields, crossing the aisle to create tools that are genuinely useful to domain experts in another field is hard. Engineers need to explain what they want to programmers. Programmers need to explain the limitations of their craft to engineers. The classic joke is that "it depends" — whenever you ask an engineer how to do something, they'll tell you it depends on a lot of things, making it nearly impossible to pin down an exact automatable process. By the time software engineers implement a request, the engineers need something slightly different.

Agentic AI is changing this. An AI system with access to relevant databases and information systems can generate custom reports, run studies, and retrieve information in formats that were tedious at best and impossible at worst with traditional software. "Give me a list of all transformers on the system ranked by voltage." "Now rank them by proximity to the feeder." "Run studies using these three conductor types and generate a cost-vs-losses comparison." These are tasks that previously required a software engineer to build a specific interface for. As long as the AI is provisioned with the right data access and appropriate guardrails, this is possible without a software engineer to interpret what's being asked, spend two weeks debugging it, and push an update that's already out of date.

That said — the history of "domain experts can now skip IT" is mixed. Spreadsheets democratized financial modeling and gave us the London Whale. The story here isn't "AI removes the bottleneck of software engineers." It's that AI shifts the bottleneck to validation, governance, and monitoring. That's a real improvement, but it comes with real responsibilities.

## So Does Any of This Solve the Policy Problem?

My argument is not that AI will change the hearts of NIMBYs or reduce the number of environmental studies that need to be conducted before building a solar farm. But what AI can do is change the pace at which the bureaucracy needed to start building can be completed, and at which rework can be accomplished.

Consider the Biden administration's EV charging infrastructure program: the 2021 Bipartisan Infrastructure Law allocated $7.5 billion for EV charging, with a goal of 500,000 chargers by 2030. By the time the Trump administration suspended new NEVI program obligations in February 2025, only about 56 stations were operational across the country — a freeze the courts later ruled unlawful, with DOT issuing revised guidance and resuming funding in August 2025. Still, the public narrative hardened into "Biden totally failed." When projects take longer to show progress than the terms of the people who funded them, they become easy political targets.

One specific mechanism: when infrastructure projects are slowed by regulation and rework, they create more time for opposition to organize. By the time a transmission line is redesigned around one community's objections, a new group has formed opposing the new route. AI won't change the hearts of people who don't want a transmission tower visible from their property, but it might reduce the number of redesign cycles, which reduces the window for opposition to expand. If a routing study takes months instead of years, there are fewer opportunities for intervening lawsuits or land-ownership changes to force new starts.

Similarly, if infrastructure designs are demonstrably optimized, they're more defensible. "We considered 200 routing alternatives; this one has the lowest capital cost, the smallest environmental footprint, and minimizes line losses" is a harder argument to counter than "our engineers think this is the best route." When investor-owned utilities challenge whether a solution is worth its cost, having run a wider search makes the engineering case more credible before regulators and courts.

Does this solve all policy problems? No. Zoning isn't going to be fixed by AI enabling faster home designs. You're simply not allowed to build multi-family housing in single-family zones. The only fix is changing the policy. And the same AI tools that help route clean energy transmission also help route gas pipelines and data center interconnects. AI that accelerates permitting and construction is agnostic about what's being built — whether that's ultimately good depends on the policy environment determining what gets built, which is still a human problem.

---

Ultimately, I don't think AI is going to solve all of our problems. But like cars, I suspect we're more focused on how it will perform in a single race — can it generate new drugs, pass the bar exam, outperform engineers on benchmarks? — when the larger impact will come from the widespread removal of specific constraints, not the isolated performance of the technology in showcase demos.

In the case of electrical engineering, that constraint may be the need to go through software-engineered interfaces in order to get the benefits of automation. What would the world look like if domain experts in complex fields could directly ask for and receive the information they need in the format they need it? How many specialized domains are bottlenecked by the gap between what domain experts know and what software teams can build for them?

The answer is: I don't know. And I don't know if this will be the most impactful change AI brings — it still could kill us all. But I do suspect that the changes we see because of AI will look much different from what appears at CEO demos and conference keynotes. Circling back to Professor Tufekci's framing, the speed, scale, and accessibility of the simplest capability of a technology can be more impactful than the isolated performance of its most impressive one. Change is coming. My hope is that, at least in the world of the electric grid, it helps us break through the limitations of the past into cleaner, more reliable, and more globally accessible energy.
