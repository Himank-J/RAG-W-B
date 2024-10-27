# Advanced RAG by Weights & Biasis

## Basic RAG Pipeline
<img width="1206" alt="image" src="https://github.com/user-attachments/assets/c69c0595-124d-4ed0-9766-d86eb98eceaa">

It's like a simple question-and-answer system:

- **Query**: A user asks a question.
- **Retrieval**: We search our knowledge base for relevant info.
- **Generation**: A language model uses the retrieved info and the query to create an answer.
- **Response**: The answer is given back to the user.
<br>

## Advanced RAG Pipeline
<img width="1268" alt="image" src="https://github.com/user-attachments/assets/9a303f4c-e2bf-4491-98a6-8398afd76417">

- **Query**: A user asks a question.
- **Query Enhancement**: We'll make the user's question even better before searching for information. This helps us find more relevant results.
- **Retrieval** (same as before): We still search for relevant information.
- **Re-ranking**: We don't just want any relevant info, we want the most relevant info. This step helps us prioritize the best results.
- **Generation** (same as before): Our language model creates an answer using the prioritized information and the enhanced query.
- **Response** **Validation**: Before giving the answer to the user, we double-check it. Is it accurate? Does it make sense? Does it answer the question?
- **Response** (same as before): Finally, the answer is given to the user.

## 80/20 Rule

In building [Wandbot](https://github.com/wandb/wandbot/), W&B leveraged the 80/20 rule, roughly 80% of user queries can be effectively addressed by focusing on just 20% of the available information. 

Here's how we applied the 80/20 rule:

- **Focus on the essentials**: We prioritized making sure the most important 20% of our documentation was top-notch and easily accessible.

- **Iterate and improve**: We started by tackling the most common problems and gradually expanded from there.

- **Manage technical debt**: We balanced quick fixes with building a system that would be easy to maintain in the long run.

<br>

Building an AI system like Wandbot involves balancing risks and rewards.

**Risks**:

- **Phased rollout**: We didn't launch Wandbot all at once. We started small and gradually expanded its use.
- **Addressing challenges**: We found ways to deal with inaccurate responses (by adding source citations), privacy concerns (by anonymizing data), and the need for human help (by making it easy for users to contact support).

<br>

**Rewards:**

- Happier users: People loved getting instant and accurate answers.
- Reduced support workload: Our support team had more time to focus on complex issues.
- Global reach: Wandbot provided expert assistance to users around the world, 24/7.

## Best Practices

Building a great RAG system like Wandbot involves following some important best practices. Here are some key lessons we learned:

**1. Start with a clear purpose:**

Define exactly what you want your RAG system to do.
Set specific goals and metrics to measure its success. For Wandbot, we wanted to improve how users navigate our documentation, so we tracked metrics like user satisfaction and search success rate.

**2. Ensure high-quality data:**

Your RAG system is only as good as the information it can access.
Make sure your knowledge base is accurate, complete, and up-to-date.

**3. Embrace evaluation and iteration:**

Continuously test and evaluate your system's performance.~
Use the results to identify areas for improvement and make changes accordingly.

**4. Develop a comprehensive evaluation framework:**

Don't just focus on accuracy.`
Consider other factors like relevance, faithfulness to the source material, and user satisfaction.

**5. Involve subject matter experts:**

Even though LLMs are powerful, they can still make mistakes.
Have experts review the system's responses regularly to ensure they are accurate and make sense.

**6. Prioritize user experience:**

Design a user interface that is intuitive and easy to navigate.
Make it easy for users to find the information they need.

**7. Be transparent:**

Let users know they are interacting with a bot.
Provide citations for the information your system provides so users can verify it if they want.

**8. Commit to continuous improvement:**

User needs and information change over time.
Keep your knowledge base up-to-date and make ongoing improvements to your RAG system.

## Challenges & Solutions to evolving RAG pipelines

**1. The Ever-Changing Landscape of LLMs:**

One of the primary challenges we encountered was keeping pace with the rapidly evolving landscape of Large Language Models (LLMs) and their associated APIs. New models and improved APIs are constantly being released, offering enhanced capabilities and performance. To ensure Wandbot remains at the forefront of this technological advancement, we adopted a systematic approach of regular updates and evaluations. This involves carefully integrating new LLM models and APIs into our system while rigorously testing and evaluating their impact on overall performance and stability.

**2. Balancing Feature Development with System Refinement:**

As with any software project, there's a constant tension between developing exciting new features and refining the core functionality of the existing system. We found it crucial to strike a balance between these two competing priorities. Our evaluation-driven framework proved instrumental in making informed decisions about which changes to prioritize. By carefully measuring the impact of both new features and system refinements on key performance indicators, we were able to allocate our development resources effectively and maximize the value delivered to our users.

**3. The Quest for Representative Evaluation Datasets:**

Developing truly representative evaluation datasets is a significant challenge in RAG development. These datasets are essential for accurately assessing the performance of the system in a way that reflects real-world usage patterns. We discovered that a combined approach yielded the most comprehensive insights: automated processes were used to gather large amounts of data, and this data was then supplemented by expert manual analysis of actual user chat logs. This hybrid approach allowed us to capture both the breadth and depth of user interactions, leading to more robust and meaningful evaluations.

**4. Navigating the Latency-Accuracy Trade-off:**

Optimizing the trade-off between response latency and accuracy is an ongoing challenge in RAG system development. Users expect both fast and accurate responses, but these two goals can sometimes be at odds. Reducing latency might involve simplifying the retrieval or generation process, which could potentially impact accuracy. Conversely, striving for higher accuracy might require more complex and time-consuming computations. We address this challenge through continuous fine-tuning of our system, exploring various techniques and configurations to improve both latency and accuracy simultaneously.

**5. Ensuring Continuous RAG System Evolution:**

- Building a RAG system is not a one-time effort. To remain effective and relevant, the system must continuously evolve. This ongoing development is crucial but often overlooked.

- Regular Dataset Updates: Keeping your datasets up-to-date is paramount. This goes beyond simply adding new information to the knowledge base. It also involves ensuring that your evaluation data accurately reflects the current state of your documentation and the types of queries real users are posing.

- Granular Evaluation: Don't just rely on overall system performance metrics. Take a more granular approach by evaluating individual components of your RAG system separately. This allows you to pinpoint specific areas where improvements are needed, leading to more targeted and effective optimizations.

- The Power of User Feedback: Quantitative metrics provide valuable insights, but they don't tell the whole story. Pay close attention to feedback from your users. This qualitative data often reveals nuanced issues and opportunities for improvement that numbers alone cannot capture.

- Fine-tuning the Entire RAG Pipeline: Regularly review and optimize every step of your RAG pipeline, from query processing and retrieval to re-ranking and response generation. This holistic approach ensures that all components of the system are working in harmony to deliver the best possible user experience.


## Evaluation

### The Ideal Evaluation Approach:

The goal is to build a small but highly representative evaluation dataset and leverage LLM judges to evaluate different components of your RAG system. By using techniques like LLM alignment (training LLMs to be better judges), we can push this mode of evaluation towards being both highly correlated with real-world performance and efficient enough for rapid iteration cycles.

### Types of Evaluation:

- **End-to-End (System) Evaluation:**

We start by evaluating the final response generated by the entire RAG pipeline. This is important because the response is often non-deterministic – meaning it can vary even for the same input query. We typically compare the generated response against a "ground truth" or ideal response to assess its quality.

- **Component Evaluation:**

Since RAG systems have multiple parts (retrieval, re-ranking, generation), we also need to evaluate these components individually. This helps us pinpoint areas for improvement. For example, we might evaluate the retrieval system by comparing the retrieved context against a ground truth context or by asking an LLM to judge if the generated response is actually based on the retrieved context.

**Evaluation Without Ground Truth:**

Not all evaluations require ground truth. Here are some cases where we can evaluate without it:

- Direct Evaluation: We can measure specific aspects of a response directly. For example, we can use tools to assess the toxicity or racial bias of a generated response, or we can check if the response is grounded in the source text (e.g., by looking for citations).
- Pairwise Evaluation: We can compare two or more responses generated for the same query and judge which one is better based on criteria like tone, coherence, or informativeness.

**Evaluation with Ground Truth (Reference Evaluation):**

When we have a gold standard reference (a "correct" answer), we can perform reference evaluation. This is often used to evaluate the structure of a response or to check if it includes specific information that is expected.
