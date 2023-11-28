---
layout: page
title: Why?
permalink: /why/
nav_order: 2
---

# Why?

Natural Language Oriented Specifications for Enterprise and Software Applications focused on Conversational Design
{: .fs-6 }
{: .fw-300 }
---

## How many vendors!

As a developer, you may come across numerous product solutions for building chatbots when you start searching and navigating the web. 
Many vendors offer fast APIs or SDKs that allow you to integrate and create your chatbot solutions.

Here are some popular vendors in the market:

- [Dialogflow](https://cloud.google.com/dialogflow) (Google): provides a comprehensive platform for building conversational interfaces.
- [AI Bot](https://azure.microsoft.com/en-us/products/ai-services/ai-bot-service) (Microsoft): offers the Bot Framework SDK, which allows developers to create and deploy chatbots across multiple channels.
- [Lex](https://aws.amazon.com/lex/) (Amazon): provides a powerful platform for building conversational interfaces and natural language processing.
- [Watson](https://www.ibm.com/watson) (IBM): offers the Watson Assistant, an AI-powered chatbot platform with advanced natural language understanding capabilities.
- [Wit](https://wit.ai) (Meta/Facebook): provides Wit.ai, a natural language processing platform that allows developers to create chatbots with ease.

There are also [LLMs](https://en.wikipedia.org/wiki/Large_language_model) (Language Model Models) with [LangChain](https://www.langchain.com/) specifications, such as [OpenAI](https://en.wikipedia.org/wiki/Large_language_model) and Google [Vertex AI](https://cloud.google.com/vertex-ai), that provide high-level chatbot capabilities.

While you can certainly build your own chatbot solution from scratch, it is advisable to leverage these existing vendors' offerings to avoid reinventing the wheel.

## Why is a common design approach important for chatbot solutions?

Building a scalable and maintainable product requires a common design approach for chatbot conversations. 
This is because requirements and developers may change over time. By adopting a high-level API that is understood by all vendors using the same framework, you can ensure that your software solution can withstand implementation changes throughout its lifecycle.

Therefore, the main goal of OpenPheme project is to establish a Lingua Franca (common language) for chatbot implementations, 
allowing for seamless integration and interoperability across different vendors' platforms. 
This also aligns with the principle of not depending on specific implementations, known as the Dependency Inversion Principle.

If you check concepts and documentations, you will find that every vendor provides his concepts, and terminology.
Here you can check differences:

Vendors:

- Dialogflow (Google): [https://cloud.google.com/dialogflow/es/docs/intents-overview](https://python.langchain.com/docs/get_started/introduction)
- AI Bot (Microsoft): [https://github.com/Microsoft/botframework-sdk/blob/main/specs/botframework-activity/botframework-activity.md](https://python.langchain.com/docs/get_started/introduction)
- Lex (Amazon): [https://docs.aws.amazon.com/lexv2/latest/dg/add-intents.html](https://python.langchain.com/docs/get_started/introduction)
- Watson (IBM): [https://cloud.ibm.com/docs/assistant?topic=assistant-intents](https://python.langchain.com/docs/get_started/introduction)
- Wit (Meta/Facebook): [https://wit.ai/docs/built-in-intents/20210928/](https://python.langchain.com/docs/get_started/introduction)
- OpenAI: [https://platform.openai.com/docs/assistants/overview](https://python.langchain.com/docs/get_started/introduction)
- LangChain: [https://python.langchain.com/docs/get_started/introduction](https://python.langchain.com/docs/get_started/introduction)


## How to test a chatbot solution?

When testing a chatbot solution, it is important to ensure that it meets your business requirements. One way to do this is by maintaining a good mock that emulates the expected behavior of the chatbot within an integration or staging environment. However, if you require the same production reference as the model, you will need to manage your expenses and operational expenditures (OPEX) accordingly.

It is important to note that some vendors may not offer solutions for integration, staging, or production environments, or they may not give you full control over your data for compliance with specifications such as GDPR. In such cases, you may need to isolate your testing in a VPN network to protect your data.

Using a high-level specification ensures that the chatbot behaves consistently and meets the functional requirements. However, if your startup heavily relies on a language model (LLM) as a service for your business, it is worth considering if this reliance is sustainable in the long term. This is because tools like OpenAI, which LLMs are built upon, can deprecate your tool if they monitor your data and find it in violation of their use case policies.

Therefore, it is important to carefully plan and test your chatbot solution, considering the potential limitations and risks associated with its implementation.














