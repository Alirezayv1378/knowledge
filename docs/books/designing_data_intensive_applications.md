# Chapter 1: Reliable, Scalable, and Maintainable Applications

- ***Reliability*** means making systems work correctly, even when faults occur. Faults can be in hardware(typically random and uncorrelated), software(bugs are typically systematic and hard to deal with), and humans(who inevitably make mistakes from time to time). Fault-tolerance techniques can hide certain types of faults from the end users.
- ***Scalability*** means having strategies for keeping performance good, even when load increases. In order to discuss scalability, we first need ways of describing load and performance quantities. The book talks about Twitter's home timeline as an example of describing load, and response time percentiles as a way of measuring performance. In scalable systems, you can add processing capacity in order to remain reliable under high load.
- ***Maintainability*** has many facets, but in essence it's about making life better for the engineering and operations teams who need to work with the system. Good abstractions can help reduce complexity and make the system easier to modify and adapt for new use cases. Good operability means having good visibility into the system's health, and having effective ways of managing it.

**Notes:**
1. There are algorithms that can calculate a good approximation of percentiles at minimal CPU and memory cost, such as **forward decay**, **t-digest**, or **HdrHistogram**.

---
# Chapter 2: Data Models and Query Languages

- Historically, data started out being represented as one big tree (the hierarchical model), but that wasn't good for representing many-to-many relationships, so the relational model was invented to solve the problem. More recently, developers found that some applications don't fit well in relational model either. New nonrelational *NoSQL* datastores have diverged in two directions:
	  1. ***Document databases*** target use cases where data comes in self-contained documents and relationships between one document and another are rare.
	2. ***Graph databases*** go in the opposite direction, targeting use cases where anything is potentially related to everything
  All three models (document, relational, and graph) are widely used today, and each is good in its respective domain. One model can be emulated in terms of another model -- for example, graph data can be represented in relational database -- but  the result is often awkward. That's why we have different systems for different purposes, not a single one-size-fits-all solution.
  One thing that document and graph databases have in common is that they typically don't enforce a schema for the data they store, which can make it easier to adapt applications to changing requirements. However, your application most likely still assumes that data has a certain structure; it's just a question of whether the schema is explicit (enforced on write, similar to static/compile-time type checking) or implicit (handled on read, similar to dynamic/runtime type checking)
---

# Chapter 3: Storage and Retrieval