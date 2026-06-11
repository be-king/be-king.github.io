---
layout: post
title: "Better Software Through Hybrid Agentic Systems"
subtitle: "A practitioner's manifesto on where software, AI, and humans should each be doing the work"
date: 2026-05-06
tags: [AI, Software Engineering, Agentic AI, MCP, Product]
excerpt: "The place where AI has had the swiftest, most widespread transformational impact is in software engineering. And we're mostly blowing it by building the same chatbot over and over."
---

*I tried to generate this with AI and it was utter garbage, so this one might look like an unpolished manifesto rather than a white paper, but alas, it is what I have time for.*

---

The place where AI has had the swiftest, most widespread transformational impact by far is in the realm of software engineering. Most of the focus of this transformation to date has been around using AI to write code and the creation of seven billion AI chatbots that all have small variations of the same interfaces and models with minimal changes to what tools and data are available to them. Many AI applications people build essentially use agents to execute the same disorganized workflows that were operated by humans before them — grabbing information out of Word documents and filling out Excel spreadsheets to be emailed over to someone who will use it to fill out a form, etc.

This all feels largely unimaginative at best, but the opposite camp whose solution is to just make everything AI also feels unimaginative and somewhat more dangerous. Do we need AI to perform deterministic calculations and queries that could be done with 3 lines of Python? Do we need to replace all of our one-click buttons with lengthy prompts? It feels like we're barreling towards a software revolution in which we can expect more from our software, and yet we're just treating the chatbot as the end-all-be-all of AI tools.

We want to imagine the future and determine what we need to learn in order to make that future without wasting all of our resources. This requires us to think outside the box, understand the pitfalls, and tease apart the strengths and weaknesses of the human–AI–software collaboration.

## Software – Humans – AI, Oh My!

At the end of the day, AI isn't just a human replacement, and it's not just a software replacement. Each brings specific strengths and weaknesses to the table, and in order to create something of value, we need to understand and leverage each of the strengths while countering the weaknesses.

| | **Software** | **Agentic AI** | **Humans** |
|---|---|---|---|
| **Strengths** | Deterministic · Interpretable · Good at math execution · Human designed · Traceable · Fast · Cheap to run · Automated | Flexible · Can handle various inputs · Easy for user to direct output · Can reference external knowledge · Can reason in new scenarios · Quick to deploy new features · Automated | Flexible · Domain knowledge · Intuition · Experience · Can reason in new scenarios · Judgement · Common sense · Accountable · Fluid intelligence + complex reasoning |
| **Weaknesses** | Inflexible · Takes time to build and deploy new features · Requires a software engineer middleman to produce changes · Breaks when it encounters something unanticipated | Non-deterministic · Hallucinates · Cost per token · Spikey intelligence · Requires context · Limited interpretability · Complex accountability · Slow | Slow · Can make errors · Can be wrong · Can be inconsistent · Needs sleep · Gets bored · Very expensive |

Our challenge is to figure out what capabilities should be contained in software (either in the harness for the agent or in MCP tools), what capabilities should be allowed to the agents, and where to put humans in the loop. While we like to think of humans as thoughtful validators who will carefully review every "is it okay if I overwrite this file?" pop-up, realistically, that's a lot to expect. Where and when to put humans in the loop matters and depends as much on their strengths and weaknesses as AI's.

## The AI Layer

### Where the Context Lives

The way we currently think of AI agents is as general purpose reasoning machines with access to context to guide them in the right direction. For most purposes, this looks like a set of constraints for the task, an input state, clear objectives of what is to be accomplished, and possible procedural guidance if multiple steps need to be performed.

Where that context lives and how the agent accesses it is currently a matter of investigation. It can live in the prompt, a document called a skill, mega-skills we call playbooks, or in an external RAG database.

| | **Prompts** | **Skills** | **Playbooks** | **RAG** |
|---|---|---|---|---|
| **Level** | Low | Mid | High (strategic) | Mid |
| **Purpose** | Execute single action | Complete a task | Decide how to solve a problem | Find relevant context for a query |
| **Logic** | None | Encapsulated steps, calls tools and sometimes agents | Decision making, branching, calls skills, tools, agents | None |
| **Reusability** | Low | High (task level) | Medium (context specific) | Low |

Especially as the amount of context required for a given task or operation grows, the challenge of storing that context in a way that is easily retrievable by the agent when it needs it grows as well.

### How Many Agents Do You (Really) Need?

Some people (AWS) might suggest that you have systems with hundreds of agents and to give each of your agents meta-agents and give each of your meta-agents their own agents. However, just as a business takes on more overhead the more people it has, the more agents you have, the more difficult it is to isolate any one failure point and the more information has a chance to be lost or miscommunicated.

However, just having a single agent to do it all also poses challenges, particularly with serial tasking and context hygiene as it tries to keep the whole problem in memory. When and how to split an agent feels like as much a challenge of administrative expertise as software engineering. Our current philosophy is to keep a minimum number of agents while providing each with a clear singular purpose. Essentially, an agent's context should only contain as much as is needed to execute its purpose. It also seems generally beneficial to separate out a judge agent and an execution agent, and often to have a separate orchestration agent or planner as well.

## Governance, Interpretability, and Evaluation

It is hard to monitor and evaluate agentic systems, especially multi-agent systems. We're largely using CloudWatch to track agent traces and interactions and LLM-as-judge to track metrics on relevance, hallucinations, succinctness, etc.

### Control Mapping

| **Layer** | **Purpose** | **Controls** | **Prod Tooling** | **Common Failure Modes** | **Goal** |
|---|---|---|---|---|---|
| User | Present agent with actions & prompts | MFA, session isolation, explicit consent prompts | IAM, Cognito | Blind approval, confusing prompts | Ensure user accountability and informed approvals |
| Policy Layer | Decides whether an action is allowed | Action classification, risk scoring, deny-by-default rules | AWS Policy Engine between model and tools | Policies bypassed in code, vague action categories | Prevent unauthorized or out-of-scope actions |
| Orchestrator | Manage reasoning, tool selection, and memory | Context isolation, memory segmentation | AWS Guardrails – Contextual Grounding | Prompt injection, memory contamination, tool loops | Reduce unsafe autonomy and context bleed among agents |
| MCP Gateway | Mediate all tool access | Tool validation, schema checks, rate limiting, request logging | AWS AgentCore Gateway, AWS API Gateway | Direct server access, unverified tool descriptions | Centralize governance and enforcement |
| MCP Registry | Stores approved servers and tools | Version pinning, approval workflow, cataloging context | AWS Registry (in preview) | Untracked registry, version drift, blind tool approvals | Ensure only trusted tools are discoverable |
| MCP Servers | Execute narrowly scoped tool actions | Least privilege, input validation, strict allowlists | AgentCore Runtime | Credential reuse, excessive API access | Reduce blast radius per server |
| Observability & Response | Validate results | Audit logs, anomaly detection | AWS CloudTrail, CloudWatch Logs | Missing audit trails, unlabeled events | Enable response tracing |

### Prompt Guardrails

| **Control Type** | **Where** | **Use It For** | **Not Great For** |
|---|---|---|---|
| **Behavioral Guidance:** System Prompt / Markdown File | Inside the agent instructions | Style, tone, step order, response format, process guidance | Hard security decisions, access control, or anything that needs to be reliably enforced |
| **Safety Validation:** Architectural Guardrails | Around model input/output, or before action execution | Detect hallucinations, check grounding, validate rule-based response, decide whether to rewrite, block, or ask for clarification | Granting access to tools or resources |
| **Access Control Layer:** Policy Enforcement | At the gateway / tool access layer | Authorizing whether the agent may call a tool or resource | Response quality checks or hallucination detection |

## The Software Layer

The software layer comprises largely the harness built around agents, MCP tools with deterministic/non-AI implementations, databases, and access/security layers. The assumption here is that for some things, while AI may be capable of doing them, it makes more sense to have an interpretable, reliable, deterministic system. This is particularly relevant where something needs to be done the exact same way every time and requires no flexibility, or where the desired output can be calculated by a known equation or algorithm. It is also where many guardrails and security requirements can be put in place.

There's a large question as to whether this "traditional software" layer will be necessary in the future or if all will be abstracted to agents, but my intuition is that just as students are more likely to score well on a test where they are allowed to use a calculator — regardless of how competent they are at arithmetic — AI will perform best when it can leverage deterministic tools rather than reasoning through everything itself.

### Software Harness

While one method is to provide an orchestrator agent that determines the exact process and allocates tasks to other agents, the flexibility agents offer is often only required at certain points in a process. Often, data loading, initial setup, or certain execution steps will always occur the same way. For instance, in our bulk design effort, every design starts with pulling the design point, extracting relevant features, creating a proposed design template, and running clearance analysis. We could provide an agent with instructions for doing all this, or we can just do it and provide the results to the agent.

### MCP Tools

MCP tools allow agents to execute changes on the world rather than just provide advice. They also enable agents to offload certain tasking to more deterministic processes. If you have a codified flowchart for how a decision should be made each time, you could have an agent reason through it costing a bunch of tokens, or you could have the agent pass the relevant inputs to an algorithm that outputs the correct answer.

In some cases, it's very clear where to draw the line — don't do math yourself, use the calculator. But in most cases the line gets blurry. If you have an agent querying a database, do you give it a set of allowable query tools where it decides the arguments, or do you let it write its own SQL? Do you give an agent plotting tools, or do you let it write its own Python to generate charts? What level of granularity do your tools go down to?

The more strictly you provide tools, the more guardrails you can have. If your AI can write and execute whatever Python it wants, there's an unbounded number of things that could go wrong. But the more you insist on writing the tools yourself, the more effort is required and the less flexible the system becomes. Additionally, the more freedom you give the AI to figure things out on its own, the more likely it is to find an inefficient method that uses far more tokens than required.

We are still largely experimenting with where to draw the line here. The biggest factors in that decision are what flexibility is required and what limitations we want to enforce.

### Conditional Logic

The classic limitation of software is that as the complexity of a problem grows, the number of branches required to capture it with conditional logic also grows and becomes unwieldy. There may be workflows where the answer can be achieved through hard-coded conditional logic, but where the complexity of that code becomes difficult to maintain or becomes a full-time job for a software engineer who needs to communicate with subject matter experts to understand the problem. Here is another area where in some cases it is far better to have a few if-else statements that are easy to trace than to hand over reasoning to an artificial agent, while in others, even though the logic is deterministic, the reasoning is complex enough that codifying it is more hassle than it's worth.

## The Human Layer

### UI and UX

The whole world seems to be collapsing down to chat interfaces. On the one hand, this is very much like how humans communicate and act in the real world — they ask each other to do things, they instruct each other on how to do the things, they provide feedback on how the things were done. On the other hand, anyone who has worked with humans knows that we're not all equally gifted at this, and communication takes time and leads to mistakes. Sometimes, being able to press a button or upload a file and know exactly what is going to happen is better and easier than having to specify what you want and how you want it done.

Conversation-based interfaces also offer a challenge when working to edit a visual artifact like an electrical diagram. Being able to click on a specific symbol and make updates is far more natural than having to describe exactly which item in the diagram you care about. Visual humans working on spatial tasks need to be able to directly interact with the thing they are working on. When engineers converse over a drawing, they refer to "this" (points at a breaker) and "that" (points at a transformer) as opposed to "Breaker B99X" and "Transformer delta167." The linear text-based interface of AI needs to find ways to keep up with spatially oriented, multi-dimensional domains.

However, one of the great strengths of AI will be in its ability to bypass the software engineer for specific UI modifications. Today, if an engineer wants to change the colors of a bar chart or add a column to a table in an output, they have to communicate that back to the devs who have to elicit requirements, implement the changes, test and debug them, and deploy them. That whole process takes time, involves communication across domains, and often is not worth something as simple as a quality-of-life upgrade. AI allows the control of the outputs to move closer to the experts and largely reduces the time to deployment for flexible capabilities.

AI can also allow users to dive into QA/QC and evaluate outputs at a deeper level without needing a data science degree. The additional insights that AI can provide to experts without an expensive UI dashboard has enormous potential to help problem solvers solve problems.

Ultimately, we're at another point of trying to identify the balance between the new and old ways of doing things. Just making everything a chat interface often adds complexity to things that could be 3 button clicks with 0 hallucination or miscommunication. Hardcoding everything creates enormous friction to customization and expert-driven outputs. We're trying to figure out the middle ground that is human-centric in its design.

### Human in the Loop

Human in the loop seems to be everyone's solution to AI's unreliability. This to me feels largely like a cop-out — humans have accountability but AI doesn't, regardless of the fact that humans have to be deeply engaged with something in order to verify things accurately. When Claude is asking for permissions, how often do you just say "yeah sure whatever you want, just let me evaluate the code when it's done"? One of the ironies of automation is that just moving humans to the backseat and having them check stuff over without being part of the process makes them disengaged and unreliable as judges.

So the question is: how do you automate the right things so that humans remain engaged and actually in the loop? The answer? No freaking clue. The number one thing people ask us to automate is QA/QC. Instead, we turn around and tell them "AI will do the job and then you just do the QA/QC." So somewhere in this process, if we want to be successful, we need to figure out where in the loop the humans are such that their intelligence, expertise, and interest are engaged while the benefits of AI are still realized.

I am unsure whether there is an answer to this problem at the extreme ends of automation, but on the augmentation and assistance side, AI-enabled software has great potential to allow experts to engage deeper. Any curiosity question or study you might want to run can be done with a few natural language questions. Any what-if scenario can be explored without all the busy work people want to avoid. The opportunity to run bulk experiments and tackle tasks that would never have been worth the pain of manual effort removes a bottleneck to productivity that unleashes user expertise for higher-level thinking as opposed to intern-level drudgery.

### Interpretability

The final role of humans in modern software is to evaluate whether the software is working as intended and identify where something has gone wrong. At present, our best access to this is through cloud traces and linking back to sources for RAG. However, AI reasoning is not human reasoning. AI has spikey intelligence and can outperform humans on some tasks while underperforming them on tasks that appear to require the same skills or knowledge. Ultimately, AI is an excellent pattern matcher, but the patterns it identifies may not be linked to the underlying causality and concepts humans understand. While for now we can do our best at tracing examples, we need AI to be designed in ways that it provides its reasoning, its assumptions, and its biases when providing outputs — rather than just providing disembodied answers for humans to blindly trust.

## Conclusion

The world of software is changing fast. Those who don't change with it will be left behind and outcompeted. Those who follow it blindly will walk into pitfalls and traps that experience up to this point hasn't prepared us to look for. We are doing our best to figure out how to walk this line, but any input, advice, or resources would be appreciated.
