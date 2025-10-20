---
layout: post
title: Agentic Design Patterns
date: 2025-10-01 11:12:00-0400
description: Design patterns for building agentic AI systems.
tags: AgenticDesign 
categories: AI
---

## Overview 

- In essence, an AI agent represents a significant leap from traditional models, 
functioning as an autonomous system that perceives, plans, and acts to achieve 
specific goals.
  - The evolution of this technology is advancing from single, tool-using 
agents to complex, collaborative multi-agent systems that tackle multifaceted objectives. 
  - Future hypotheses predict the emergence of generalist, personalized, and even 
physically embodied agents that will become active participants in the economy.
  - This ongoing development signals a major paradigm shift towards self-improving, goal-driven systems poised to automate entire workflows and fundamentally redefine our 
relationship with technology.


## pattern #1: lang-chaining

- a pipeline or chained approach can be described as follows: 
  1. Initial Prompt (Summarization): "Summarize the key findings of the following market research report: ." The model's sole focus is summarization, increasing the 
accuracy of this initial step. 
  2. Second Prompt (Trend Identification): "Using the summary, identify the top three 
emerging trends and extract the specific data points that support each trend: [output 
from step 1]." This prompt is now more constrained and builds directly upon a validated 
output. 
  3. Third Prompt (Email Composition): "Draft a concise email to the marketing team that 
outlines the following trends and their supporting data: [output from step 2]."


Prompt chaining's core utility lies in breaking down complex problems into sequential, manageable steps. Each step's output feeds into the next, allowing for more focused and accurate responses from the model at each stage. This method enhances the overall quality of the final output by ensuring that each component is thoroughly addressed. Several practical applications and use cases include:

### Information Processing Workflows
This methodology is applied in domains such as **automated content analysis**, the development 
of **AI-driven research assistants**, and **complex report generation**. 

A prompt chain could be like: 

- Prompt 1: Extract text content from a given URL or document. 
- Prompt 2: Summarize the cleaned text. 
- Prompt 3: Extract specific entities (e.g., names, dates, locations) from the summary or original text. 
- Prompt 4: Use the entities to search an internal knowledge base. 
- Prompt 5: Generate a final report incorporating the summary, entities, and search results. 

### Complex Query Answering

answering **multifaceted** questions that require multiple steps of reasoning or data retrieval is a good example of lang-chain application. For example,  "What were the main causes of the stock market crash in 1929, and how did government policy respond?" 

- Prompt 1: Identify the core sub-questions in the user's query (**causes of crash**, **government response**). 
- Prompt 2: Research or retrieve information specifically about the causes of the 1929 crash. 
- Prompt 3: Research or retrieve information specifically about the government's policy response to the 1929 stock market crash. 
- Prompt 4: Synthesize the information from steps 2 and 3 into a coherent answer to the original query. 

### Data Extraction and Transformation

The conversion of unstructured text into a structured 
format is typically achieved through an iterative process, requiring sequential modifications to 
improve the accuracy and completeness of the output. For example:

- Prompt 1: Attempt to extract specific fields (e.g., name, address, amount) from an invoice document. 
- Processing: Check if all required fields were extracted and if they meet format requirements. 
- Prompt 2 (Conditional): If fields are missing or malformed, craft a new prompt asking the model to specifically find the missing/malformed information, perhaps providing context from the failed attempt. 
- Processing: Validate the results again. Repeat if necessary. 
- Output: Provide the extracted, validated structured data.


### Content Generation with Iterative Refinement

### Conversational Agents with State

### Code Generation and Refinement

### Multimodal and multi-steo reasoning