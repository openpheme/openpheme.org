---
layout: page
title: Java
permalink: /java
parent: Specs
nav_order: 1
customjs:
- https://polyfill.io/v3/polyfill.min.js?features=es6
- https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js
---

# Jakarta Chatbot Web Services (JAX-CS)

JAX-CS is a [Java (Jakarta) EE](https://jakarta.ee/) specification specifically developed to implement [chatbots](https://en.wikipedia.org/wiki/Chatbot) within enterprise applications. Our main objective is to provide an API based on the core concept of speech acts, enabling developers to design conversational interactions and utilize all the features of Jakarta EE.

It is important to note that **our goal is not to provide an API for creating autonomous artificial intelligence that can learn and chat with users**. Instead, we aim to focus on implementing business requirements using testable best practices. With JAX-CS, developers can effectively integrate chatbot functionality into their enterprise applications to enhance user experiences and streamline communication processes.

Our API is designed to facilitate the development of chatbot-driven applications by leveraging the powerful features and frameworks of Jakarta EE. By adhering to industry standards and best practices, JAX-CS ensures the seamless integration of chatbot functionality into enterprise systems.
[View it on Github](https://github.com/openpheme/jaxcs/tree/main){: .btn }

---

## Example: Booking Restaurant

Our business requirements is

> As user, I want to book a reservation for a restaurant using chatbot

We start by defining an `@Intent` that express the actual intention of the user, as defined inside [intent definition](/concepts/#intent).
An intent method is a function that takes as input a `@Referred` object and a `@Prompt` object. 
A `@Referred` maps a `@Reference` object of type `Booking`, that express an entity which the user is [referencing](/concepts/#reference) using his speech act, and `@Prompt` object maps the utterance of the user.

```java
@RequestScoped
public class BookingAgent {
    
    @Inject
    BookingRepository repository;
    
    @Intent
    @Transactional
    public String book(@Prompt String prompt, @Referred Booking booking){
        Booking saved = repository.save(booking);
        return String.format("Ok %s, your booking with id %s is done with success. See you on %s", 
                booking.name, 
                booking.id, 
                booking.bookingDateTime
        );
    }
    
}
```
As you can see, using CDI, every time the user submit a request, the life cycle of request is bound to the request.
We annotate with `@Transactional` to trigger proxy generation at runtime and make entire request within a transaction that will commit
our managed entity inside the database.

Here below there's the definition of the `@Reference` class, with its `@Parameter`. A `@Parameter` express a required or not
primitive type (or class). In our case our `@Reference` is also an @Entity that is managed by persistence layer.

```java
@Reference
@Entity
@Table(name = "BOOKINGS")
public class Booking {
    
    @Id
    public String id;
    
    @Parameter
    public LocalDateTime bookingDateTime;
    
    @Parameter
    public String name;

}
```

This process of building an instance inside the context is done by Agent, that predict which intent the user 
is expressing. 

Formally, The **intent I** is function that we define as:

**I = F(p, c)**

Where **p** is the prompt (utterance) of the user and **c** is the current context.

Building on HTTP RESTful implementations, the result will be:

```text
curl --request GET -url 'http://localhost:8080?prompt=I would like to book a table for dinner tomorrow at 9.00 p.m. with name John'
```

> "Ok John, your booking with id 1 is done with success. See you on 2023-02-18T21:00:00"

### Intent matching

The process of prediction of the intent, routing to right method annotated with `@Intent` is done by an **Agent**.
Formally the prediction is a [supervised](https://en.wikipedia.org/wiki/Supervised_learning) prediction where the Agent
executes predict the next intent using current utterance and the context.

You can provide your logic to predict the intent. Common approach are:

- LLM (with langchain) to keep the context
- Predictors build upon Recurrent Neural Nets, saving context with LIFO queue 
- Predictors build upon bag of words models (like Naive Bayes), saving context with LIFO queue

You can use PMML to define the model, trained on dataset

https://dmg.org/pmml/v4-4-1/GeneralStructure.html
### References Extraction

Phase in which the agent extracts referred entities interpolated inside content of the utterance is called
**references extractions**. In our case the agent inject an instance of `Booking` to be used inside our business logic
A convenient way to do it is using [langchain4j](https://github.com/langchain4j/langchain4j).