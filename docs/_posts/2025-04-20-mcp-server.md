---
layout: post
title: Understanding MCP and MCP Server
date: 2025-04-20
categories:
  - Today I Learned
  - AI
---
### April 20, 2025

![MCP Definition]({{ site.baseurl }}/assets/images/mcp-def.png)

From past 2 months in March April of 2025, I have came across this word "MCP" quite few times on all different platforms, Youtube, LinkedIn, Dev.to, Daily dev, blog posts, newsletters etc.

I started looking into this concepts MCP on all possible channels, I started with Yotube to understand what exactly is MCP and MCP servers. 

MCP stands for Model Context Protocol and MCP Servers are the servers which hosts application which support MCP.

To understand MCP and why and how it is useful, it is important to understand how LLM works at least on high level. 

LLM - Large Language Model, does only one thing - They understand the input user have provided by breaking it down in smaller chunk and it generates the output by predicting best possible word based on existing text. 

>"Large Language Models (LLMs) generate the next word in a sequence ==by predicting the most probable word based on the preceding text==. This prediction is made using sophisticated mathematical functions and deep learning techniques. LLMs assign probabilities to all possible next words and then select the most likely one, or a less likely one randomly, to create more natural and coherent text."

Using this primary function of LLM you can built a wide variety of applications around different use cases, for example giving it context of a email or a code by pasting that content asking LLM to review it and generate suggestions or fixes for the same.

### What is MCP

MCP is a open source protocol which helps LLM to communicate with additional resources and tools to get more context from different external sources. But why you will need it?

LLM alone can't do or perform much task without help. For example 
- If you ask LLM to get weather for today for specific location, LLM alone can't do that, because they are trained on fixes set of data. 
- Another example is if you ask LLM to generate report, or analyse any share market stock it won't be able to do it alone, or in other word how LLM will get live or real time data for a stock right?
- One more relevant example I find is, in developers IDE if you asked LLM to re-write any SQL query and execute it to check the data, LLM will be able to only suggest better version of the query by re-writing it, it won't be able to run it. 

Overall, if LLM needs more context or resources to conclude anything, or if LLM needs to perform any action which requires any tools, they won't access to it out of the box, the resources and tools has to configure and develop in a way so that they can work with LLM.

MCP solves this problem in 2 ways
- This protocol provides a way to developers to develop a standard middleware between LLM and Tools and Resources which provides plug and play support
- This protocol provides a way in which LLM can easily communicate to the MCP server to get relevant resources or access to tools to perform any actions.

![MCP Definition]({{ site.baseurl }}/assets/images/MCP-Server-Client.png)

MCP works on client-server architecture, same as REST. Her client is host which supports MCP with LLM.

- The client should be compatible with MCP protocol so that it can provide way to connect to MCP servers. For example Claude Desktop or Windsurf
- Server is any machine which hosts a server written using MCP SDK serving on xxx port.
- While developing this server you can configure the resources and tools you want to expose to LLM.

### Sequence of operation, how it works in action
- First as a pre-requisite, you will configure your MCP client with connection to MCP server.
- Now whenever user will query something, LLM interprets it and make a call to MCP server to get additional resources/context or perform action using tool
- MCP server then performs that action and return back result

#### Resources

- [Model Context Protocol (MCP), clearly explained (why it matters)](https://www.youtube.com/watch?v=7j_NE6Pjv-E)
- [Understand MCP in 15 Straightforward Points](https://www.linkedin.com/posts/curiouslearner_ai-mcp-beginners-activity-7316188820817817600-MRYS/?utm_source=share&utm_medium=member_desktop&rcm=ACoAABB78E8B5ULFTRDNgfviFFZJ5A11eziGocE)
- [What is MCP? Why is everyone talking about it?](https://www.linkedin.com/feed/update/urn:li:activity:7313277172171919362/?utm_source=share&utm_medium=member_desktop&rcm=ACoAABB78E8B5ULFTRDNgfviFFZJ5A11eziGocE)
- [Introducing the Model Context Protocol](https://www.anthropic.com/news/model-context-protocol)
- [modelcontextprotocol.io](https://modelcontextprotocol.io/introduction)
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers)
- [MCP Protocol: a new AI dev tools building block](https://newsletter.pragmaticengineer.com/p/mcp)


