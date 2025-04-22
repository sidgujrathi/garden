---
layout: post
title: Understanding RAG (Retrieval-Augmented Generation)
date: 2025-04-22
categories:
  - Today I Learned
  - Seed
  - AI
---
### April 22, 2025

> **_This is a seed, this will be re-visited for cultivation_**

- LLM fundamentally generates response from their training data which has no source as latest and this training data could be out of date
	- This is problematic since LLM can be wrong due to source issue, not having latest source and another problem is you might not get answer at all since the question you might be asking could be answered only with latest data which LLM doesn't have since it is not updated recently with new data
	- For example, as a user if you ask LLM - Name a planet in solar system having most number of moons. In this case if LLM you are using is not re-train on latest data it could give you wrong answer.
- So in RAG - What if we add Retrieval Augmentation in Generation of these responses? That means apart from what LLM knows we will add content store.
	- This content store can be anything, open, internet, database, files etc
- Now with this content LLM can take extra context to answer the prompts
- In RAG framework we add **instruction** to LLM, first retrieve relevant content from content store, combine it with your training data and then generate response with source of your response
- The problem with this framework could be if retriever is not sufficiently good to give LLM best information as context, the query by user might not get addressed and will not have any response

![RAG]({{ site.baseurl }}/assets/images/RAG-intro.png)

### How RAG works

- There are 2 parts to process
	- Offline part / pre-requisite - You ingest and index knowledge
	- Online part - retrieve and answer's the queries
- Offline / Pre-requisite
	- You break down your knowledge in chunks and create vector embeddings for each chunk. This is done using **embedding model**
	- Embedding model creates this embedding chunks and store in **Vector DB**
- Online Part
	- As soon as prompt comes up, we go to RAG retriever, it takes question / prompt creates vector of it and do the similar search in vector DB
		- Question - <mark>Who initiates this? A model is responsible for this or as developer you have to introduce this step to kick in RAG retriever</mark>
	- Vector DB will return top K similar chunks
	- Then these chunks will be added as context with prompt to LLM
		- <mark>Who is responsible to do this step?</mark>
	- LLM uses context and it's training data to response to the prompt


![RAG]({{ site.baseurl }}/assets/images/RAG-working.png)


**Resources:**
- https://www.youtube.com/watch?v=T-D1OfcDW1M
- https://www.youtube.com/watch?v=HdafI0t3sEY