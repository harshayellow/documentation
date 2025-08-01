---
title: Agent assist bot 
sidebar_label: Agent assist bot
---

:::note
Contact the support team to get Agent assist bot configured/enabled. 
:::


## Introduction to agent assist bot

Support agents often find themselves repeatedly performing actions such as retrieving or updating customer information in external tools like CRM systems. Additionally, agents often need to execute tasks on behalf of customers, like canceling orders or initiating service requests, which often involve navigating through multiple tools or tabs.

This constant tool-switching disrupts the agents' workflow, reduces their productivity, and can lead to frustration. It also increases the average handling time for customer inquiries, especially when these repetitive tasks are essential for every chat/ticket session.

A viable solution to this problem is to centralize all these operations within the support inbox using an assist bot. Think of the assist bot as a virtual assistant for agents, where you can configure various workflows. For instance, you can provide buttons within the inbox to create tickets or process refunds.

By implementing this solution, agents would no longer need to perform these manual tasks. Instead, they can efficiently complete their tasks directly within the inbox. This not only streamlines their work but also allows them to concentrate on addressing high-priority customer issues, ultimately enhancing overall support efficiency.

Agent assist bot helps agents efficiently complete their tasks directly within the inbox. This not only streamlines their work but also allows them to concentrate on addressing high-priority customer issues, ultimately enhancing overall support efficiency.


### Use cases of agent assist bot

1. **Customer service**: Assist bots help address customer inquiries, troubleshoot issues, track orders, and handle returns/refunds, improving customer satisfaction.
2. **Sales and lead generation**: Bots assist in recommending products, qualifying leads, and scheduling sales appointments, enhancing sales and lead conversion.
3. **HR and employee services**: These bots aid in onboarding, answer HR-related queries, and recommend training and development resources for employees.
4. **IT support**: Assist bots help with IT-related tasks like password resets, software installation, and network issue troubleshooting, reducing IT support workload.

### Assist bot vs @bot



| Assist bot | @bot |
| -------- | -------- |
| This is a feature that allows the agent to interact with another customized bot from within their inbox to enable quick and seamless resolution. It's for the agent's use during the conversation and doesn't involve the bot communicating with the customer at all. | This is a command used by the agent to initiate a conversation flow directly with the customer, essentially asking the bot to take over the conversation on behalf of the agent. Read more [here](https://docs.yellow.ai/docs/platform_concepts/inbox/chats/chatscreen#initiate-studio-flow-with-bot). |



------

## Steps to use the agent assist bot 


### Configure assist bot in Automation

> Bot admins, bot developers, or administrators have the necessary permissions to create a new bot.

1. [Create a new bot](https://docs.yellow.ai/docs/platform_concepts/studio/overview) under your subscription, giving it a unique name (example: Mia Support). 
2. Create multiple [custom flows](https://docs.yellow.ai/docs/platform_concepts/studio/build/Flows/journeys) within **Automation** based on your business use cases. 
    > All the data within Inbox (like contacts and custom fields) is accessible in **Automation**.
3. Test and [publish](https://docs.yellow.ai/docs/platform_concepts/studio/test-and-publish-bot/modes) your bot. 
4. Open **Extensions** > **Chat widgets** > **Settings** and enable the option **Show the conversation history** and disable **Create a new session for every new tab**.
    ![](https://cdn.yellowmessenger.com/assets/yellow-docs/chatwidgetenable.png)
5. After completing the above steps, reach out to Yellow.ai's Inbox team to integrate your Assist bot with the chat/ticket screen. 

-------


#### How to use inbox data in Automation while building the assist bot flows?

When agents trigger the assist bot within the Inbox, it receives a complete set of current chat/ticket data as a payload. This chat/ticket data comprises essential information such as the chat/ticket ID, custom fields, and tags. You can design flows to automatically retrieve Inbox information in Automation without manual input. 

**Example**: When an agent clicks on **Cancel order**, the order ID can be automatically captured, and the order can be marked as canceled without the agent needing to search for the order ID and confirm it again.


**Sample payload**: 

```json
{
    "tags": [],
    "responded": true,
    "ticketType": "livechat",
    "ticketCsatScore": null,
    "agentCsatScore": null,
    "comments": [
        "AUTO_TRANSLATE_HARDCODED_USER_LANGUAGE_NOT_FOUND"
    ],
    "assignedByAdmin": true,
    "manualAssignment": false,
    "lastAgentMessageTime": 1695620201345,
    "lastUserMessageTime": null,
    "lastBotMessageTime": null,
    "userActiveStatus": "INACTIVE",
    "agentActiveStatus": "ACTIVE",
    "replyCount": 0,
    "userReplyCount": 0,
    "voiceCall": false,
    "sipCall": false,
    "agentCurrentHandlingTicketsCount": 11,
    "autoStartCall": false,
    "autoTranslate": false,
    "autoDetectLanguage": false,
    "preferredAgent": false,
    "preferredAgentFallback": false,
    "createdFromProactiveNotification": false,
    "unreadCount": 0,
    "cdpId": "",
    "_id": "65111c55c281975d14cac7a5",
    "botId": "x1623067352191",
    "uid": "82570131562126492148356127684",
    "priority": "MEDIUM",
    "severity": "MEDIUM",
    "source": "yellowmessenger",
    "contact": {
        "name": "Kindred Flamingo"
    },
    "assignedTo": "inboxyellowai",
    "xmpp": "user_tYxPsWVbYjXfUhdwxkHuR",
    "ticketId": "100820",
    "isNewTicket": true,
    "logs": [],
    "timestamp": "2023-09-25T05:36:21.550Z",
    "reassignmentLog": [],
    "lastMessageTime": 1695620201345,
    "collaborators": [
        {
            "_id": "65111c55c281979faecac810",
            "username": "inboxyellowai",
            "xmppUsername": "user_tYxPsWVbYjXfUhdwxkHuR",
            "name": "Inbox team 1234"
        }
    ],
    "agentLanguage": "en",
    "status": "ASSIGNED",
    "assignedTime": "2023-09-25T05:36:21.950Z",
    "createdAt": "2023-09-25T05:36:21.956Z",
    "updatedAt": "2023-09-26T05:30:37.865Z",
    "__v": 0,
    "firstResponseTime": "2023-09-25T05:36:41.341Z",
    "updated": "2023-09-25T05:36:41.346Z",
    "isSecondaryEncrypt": true,
    "lastMessage": "hi ther",
    "lastMessageType": "AGENT",
    "customFields": {
        "s6": "",
        "s5": "",
        "s2": ""
    }
}
```

To use the payload details within flows, follow these steps: 

1. Use the [Variable](https://docs.yellow.ai/docs/platform_concepts/studio/build/nodes/action-nodes-overview/variables-node) node to initialize variables. Use this format `{{{profile.payload.Your_Field_Name}}}` to extract data from the payload.
    ![](https://imgur.com/QWF8rCj.png)
2. Add multiple flows/nodes using the payload variables. These flows can be employed for various purposes, such as API calls and other automation tasks.
    ![](https://imgur.com/Qbcvx42.png)

>  To learn more about payload data extraction, click [here](https://docs.yellow.ai/docs/platform_concepts/channelConfiguration/chat-widget-payload#11-pass-payload-data-via-bot-script).

----

### Use the agent assist bot within the inbox screens 

> Inbox agents and inbox admins have access to the assist bot within the chat/ticket screen.

- Inside the Inbox chat/ticket screen, simply press Cmd + K (Ctrl + K on Windows) or click on the assist bot icon within the chat interface to open the assist bot.
- Each chat/ticket session will include a dedicated bot instance, allowing agents to ask questions or perform various operations tailored to the ongoing customer interaction.
    
![](https://imgur.com/9I1LQll.png)          

**Chat screen**: 
![](https://cdn.yellowmessenger.com/assets/yellow-docs/chataibot.png)

**Email screen**: 
![image](https://imgur.com/Iq0AfAt.png)
