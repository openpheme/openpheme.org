---
layout: page
title: Concepts
permalink: /concepts/
nav_order: 2
---

# Concepts

---

####  Table of Contents
- [Introduction](#introduction)
- [Intent](#intent)

## Introduction
An essential aspect of conversational design involves understanding the fundamental nature of a conversation. At its core, a conversation is constructed through the exchange of [**speech acts**](https://en.wikipedia.org/wiki/Speech_act), as highlighted by [J.L. Austin](https://it.wikipedia.org/wiki/John_Langshaw_Austin) in his renowned work, "How to Do Things with Words." By delving into the concept of speech acts, we can bring attention to phrases that do not merely serve the purpose of describing or asserting truth.

Not all utterances can be classified as "descriptive" or "reporting" statements, which can be evaluated as either true or false. Instead, certain utterances encompass the performance of an action or play a role in the execution of a particular task, typically not regarded as a straightforward act of communication.

For instance, consider the utterance "I give and bequeath my watch to my brother" within the context of a will. Here, the act of uttering this sentence is not an act of description but an actual act of bequeathing. The statement itself does not possess the quality of being true or false.

Similarly, the utterance 

> "I bet you 5€ it will rain tomorrow" 

signifies an action rather than a mere statement of reality. By uttering this sentence, the speaker engages in the act of placing a bet, involving a financial exchange contingent upon a future event.

Furthermore, the statement 

> "I do (take this woman to be my lawful wedded wife)" 
 
exemplifies the performative nature of language within the context of a marriage ceremony. Uttering these words is not a statement of fact or truth but an integral part of the act of getting married.

In each of these examples, it becomes evident that the act of uttering the sentence, when appropriately situated within the relevant context, extends beyond the boundaries of description. Rather, it constitutes the very act being performed, and the truth value of the utterance becomes irrelevant.

Understanding and appreciating the performative dimensions of language in conversation enables us to grasp the intricacies of communication beyond the mere exchange of factual information. By recognizing and accommodating the diverse functions of speech acts within a conversational system, we can design more nuanced and effective interactive experiences.
## Intent
The core concept of a Speech Act revolves around the notion of an intent. An intent represents the communicative intention of a user that is conveyed through an utterance. It serves as the central building block for understanding and interpreting human language in conversational systems.

A Speech Act design can be likened to an application programming interface (API), which functions as a contract between a client and a server. Just as an API adheres to a formal definition and must be evaluated during compile time, a speech act should also respect the specified contract. Like an API, a speech act can have both a happy flow and various sad flows, depending on the context in which it operates during runtime.

In practical terms, an API implementation aligns with a specific use case and is interconnected with other related APIs. By utilizing a sequence of APIs, a user can construct a series of actions that correspond to a User Story and ultimately fulfill an end-to-end use case. Consequently, a Conversation can be understood as a sequence of intents, each triggering a specific API and contributing to the overall flow of the conversation.

Segmentation, as a design procedure, allows for the decomposition of an intent into sub-intents. Each sub-intent represents a distinct use case that can be further broken down into a sequence of related use cases. This segmentation facilitates more granular and targeted processing of user inputs and enables the system to handle a wide range of user requests effectively.

The expressive capabilities of different languages vary, with some languages offering a more extensive lexical repertoire compared to others. In certain languages, concepts may not be explicitly segmented and can map to the same words or phrases. However, disambiguation is achieved through contextual cues or the relationships between other linguistic components. For example, the phrase "I love you" can be expressed as "Ti amo" or "Ti voglio bene" in Italian, depending on the specific context and the nature of the relationship.

An important aspect of an intent is its performative component. Within this context, a use case is expressed through the will of the user using natural language or even gestures in more complex scenarios. This expressive medium allows for the routing to a specific implementation of the intent, guiding the system towards the intended action or response.

To achieve this, a Language Understanding Model (LLM) or other logical mechanisms are employed to match the user's utterance against the existing context and content, leading to the appropriate routing of the intent's performative logic. This matching process forms the foundation of effective intent understanding and serves as a critical step in enabling accurate and context-aware conversational interactions.