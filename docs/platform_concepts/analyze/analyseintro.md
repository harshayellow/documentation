---
title: Introduction to analyze
sidebar_label: Analyze
---

## Analyze overview

Analyze is an advanced AI Analyst that helps brands monitor and enhance AI-agent performance over time through self-learning mechanisms. It improves your **contained resolution rate** by leveraging an in-house LLM model to evaluate each conversation, measure resolution quality and user sentiment, and create topic clusters.

Business owners can then focus on the topics with the greatest opportunity to improve contained resolution.

> **Contained resolution rate** refers to the share of conversations resolved by the AI-agent without a handover to the human support agent.

![image](https://imgur.com/tSJcj17.png)

### Use cases

Analyze is ideal for Customer Success Managers, Brand Owners, Customer Support Leaders, and Customer Support Managers. It empowers them to:

- Understand the topics end users are discussing
- Evaluate the AI-agent's effectiveness in resolving user queries
- Assess user satisfaction
- Identify opportunities to enhance the AI-agent’s resolution capabilities
- Analyze how well human agents resolve user queries and how the AI-agent can learn from these interactions

### Advantages 

1. Increase automation efficiency
2. Boost agent productivity
3. Enhance customer satisfaction
4. Improve the quality of conversations

-------

## Access analyze

To access the Analyze module you must have **any one** of the following permissions: 
- Super admin
- Admin 
- Insights admin

:::note

Refer to [Manage your bot users](https://docs.yellow.ai/docs/platform_concepts/Getting%20Started/add-bot-collaborators#share-bot-access) article to understand how to request or provide access to use Analyze module in a bot.   
    
:::




-----

## Key features 

| **Feature**                      | **Description**                                                                                                             |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| **Topic Clustering**              | Enables brands to understand user conversations, facilitating better analysis, AI-agent improvements, and simplified debugging |
| **Resolution Status Check**      | Assesses whether user queries are being effectively resolved, enhancing overall customer support efficiency               |
| **Sentiment Tagging**            | Analyzes user sentiment, allowing for improved customer satisfaction through appropriate responses                        |
| **Knowledge Base Article Creation** | Learns from human support interactions to improve AI-agent automation, positioned as a self-learning capability, leading to reduced support tickets and increased customer retention |

## Inside look into analyze 

### Chat metrics

The Analyze section within the Automation module offers a detailed view of various metrics related to user interactions through chat, providing valuable insights for improvement.

### Conversation logs

For conversations where the model has no knowledge base improvement suggestions, brands can review these interactions in the conversation logs. Here, they can view model-generated tags and provide feedback on the analysis to further refine the model.

### Message view

Message View evaluates how well the AI-agent is trained to understand and respond to user input in a conversational context, particularly focusing on its ability to generate accurate and relevant responses to unseen input.

### Topics

For each conversation, the in-house LLM model generates the following insights:

- **Topic**: The main subject of multiple conversations. After selecting a topic of your choice, you can view all the associated metrics.
- **Topic Description**: A detailed explanation of the topic.
- **User Query**: A summary of the user’s question.
- **Resolution**: A summary of the resolution provided, either by the bot or the AI-agent.
- **Resolution Status**: Indicates whether the user’s query was resolved.
- **Sentiment**: The user's sentiment (positive, neutral, or negative).
- **Containment**: Indicates if the issue was resolved by the AI-agent (True) or handed over to a human agent (False).
- **Automation**: For conversations handed over to a human agent, this metric determines if the resolution can be replicated by an article in the knowledge base, aiding future automation.



> Read the following articles to learn more. 