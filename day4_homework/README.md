# Day 4 — Agents and Tools
## Step 1 — I moved from search to an agent-based system

In this step, I moved beyond building a search system and started building an AI agent.

Until this point, I had already:

collected the data,
chunked it,
indexed it,
and implemented lexical, vector, and hybrid search.

Now, I used this search capability as a tool for an agent.

## Step 2 — I understood the difference between a plain LLM and an agent

Before building the agent, I first understood the core idea:

A plain LLM can generate answers, but it does not know how to access my project-specific data on its own.

An agent, on the other hand, can use tools.

In my case, the tool was the search function I implemented in the previous step.

## Step 3 — I prepared the search function as a tool

To make my system usable by the agent, I exposed my search logic as a callable tool.

I used my existing text_search(query) function so the agent could retrieve relevant information from my indexed GitHub documentation before answering.

This allowed me to connect retrieval with answer generation.

## Step 4 — I tested the “LLM only” approach

Before using tools, I compared the behavior of a plain LLM with an agent-based approach.

When I asked questions without giving the model access to search, the responses were generic and not grounded in my dataset.

This helped me clearly see why tool use is what makes an agent truly useful.

## Step 5 — I defined the system prompt

I wrote a system prompt to guide the model’s behavior.

My main instruction was simple:

always search before answering,
use the retrieved information when relevant,
and avoid making unsupported claims.

I also improved the prompt when needed to make the agent more consistent.

## Step 6 — I built the agent with Pydantic AI

After understanding the manual function-calling flow, I implemented the actual agent using Pydantic AI.

I connected:

the LLM,
the system prompt,
and my text_search tool

into a single agent structure.

This made the implementation much cleaner and easier to manage.

## Step 7 — I interacted with the agent

After building the agent, I tested it with questions related to my dataset.

I observed that the agent was able to:

call the search tool,
retrieve relevant chunks,
and generate more context-aware answers compared to a plain LLM.

This step helped me validate that my retrieval pipeline could now be used inside an agent workflow.

## Step 8 — I refined the prompt when needed

While interacting with the agent, I noticed that the quality of the final answer was influenced not only by the search results, but also by the system prompt.

Because of this, I adjusted the prompt to make the agent:

* rely more on search,
* answer more clearly,
* and avoid unsupported assumptions.

This showed me how important prompt design is in agent systems.

## Step 9 — Key takeaway

This step helped me understand a very important concept:

An effective AI agent is not just an LLM. It is an LLM that can use tools to access the right information at the right time.

I also learned that:

* search is the backbone of the agent,
* tool use makes the system agentic,
* and prompt design strongly affects agent behavior.

## Final Conclusion

In this step, I built my first tool-using AI agent on top of the search system I created in the previous stage.

By combining:

* indexed documentation,
* search functions,
* a structured system prompt,
* and Pydantic AI,

I turned my project from a simple search pipeline into a context-aware AI agent.
