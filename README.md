# Advanced RAG by Weights & Biasis

Contents - 

1.) [Basic RAG Pipeline](#basic-rag-pipeline)

2.) [Advanced RAG Pipeline](#advanced-rag-pipeline)

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

## Metrics

# Retrieval Metrics Explanation

The [retrieval_metrics.py](https://github.com/wandb/edu/blob/main/rag-advanced/notebooks/scripts/retrieval_metrics.py) module contains several functions designed to evaluate the performance of retrieval systems using various metrics. Below is a detailed explanation of each metric function, including its purpose, inputs, outputs, and usage.

---

### 1. `compute_hit_rate`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_hit_rate(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **Hit Rate (Precision)** for a single query. This metric measures the proportion of retrieved documents that are relevant.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
  - `'score'`: The relevance score of the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score (non-zero indicates relevance).

### **Output**
- `float`: The hit rate (precision), representing the fraction of retrieved documents that are relevant.

### **Why It Is Used**
Hit Rate provides a straightforward measure of retrieval accuracy by indicating how many of the retrieved documents are actually relevant to the query. It is useful for assessing the effectiveness of the retrieval system in returning pertinent results.

---

### 2. `compute_mrr`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_mrr(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **Mean Reciprocal Rank (MRR)** for a single query. MRR measures the rank of the first relevant document in the retrieved list.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
  - `'score'`: The relevance score of the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score (non-zero indicates relevance).

### **Output**
- `float`: The MRR score, indicating the position of the first relevant document. If no relevant document is found, it returns `0.0`.

### **Why It Is Used**
MRR is particularly useful in scenarios where the user is primarily interested in the first relevant result. It provides insight into how quickly the retrieval system can surface a relevant document, enhancing user satisfaction by minimizing the time to find pertinent information.

---

### 3. `compute_ndcg`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_ndcg(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **Normalized Discounted Cumulative Gain (NDCG)** for a single query. NDCG evaluates the ranking quality of the retrieved documents based on their relevance scores.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score of the document (0, 1, or 2).

### **Output**
- `float`: The NDCG score, which ranges from 0.0 to 1.0. A higher score indicates better ranking quality.

### **Why It Is Used**
NDCG accounts for the position of relevant documents in the ranked list, giving higher importance to relevant documents appearing earlier. It provides a nuanced evaluation of retrieval performance by considering both the relevance and the order of the results, making it valuable for optimizing ranking algorithms.

---

### 4. `compute_map`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_map(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **Mean Average Precision (MAP)** for a single query. MAP measures the average precision across all relevant documents retrieved.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
  - `'score'`: The relevance score of the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score (non-zero indicates relevance).

### **Output**
- `float`: The MAP score, representing the average precision across all relevant documents. If no relevant documents are found, it returns `0.0`.

### **Why It Is Used**
MAP provides a single-figure measure of quality that accounts for both precision and recall across different recall levels. It is especially useful when evaluating systems that need to retrieve all relevant documents, offering a comprehensive assessment of retrieval performance.

---

### 5. `compute_precision`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_precision(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **Precision** for a single query. Precision measures the proportion of retrieved documents that are relevant.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
  - `'score'`: The relevance score of the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score (non-zero indicates relevance).

### **Output**
- `float`: The Precision score, indicating the fraction of retrieved documents that are relevant. If no documents are retrieved, it returns `0.0`.

### **Why It Is Used**
Precision provides a measure of the accuracy of the retrieval system by indicating how many of the retrieved documents are actually relevant. It is essential for understanding the reliability of the system in returning pertinent information.

---

### 6. `compute_recall`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_recall(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **Recall** for a single query. Recall measures the proportion of relevant documents that have been retrieved over the total amount of relevant documents.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
  - `'score'`: The relevance score of the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score (non-zero indicates relevance).

### **Output**
- `float`: The Recall score, indicating the fraction of relevant documents that were retrieved. If there are no relevant documents, it returns `0.0`.

### **Why It Is Used**
Recall is crucial for assessing the ability of the retrieval system to find all relevant documents. High recall ensures that users are unlikely to miss any pertinent information, which is especially important in comprehensive search scenarios.

---

### 7. `compute_f1_score`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
def compute_f1_score(model_output: List[Dict[str, Any]], contexts: List[Dict[str, Any]]) -> float:
```

### **What It Does**
Calculates the **F1-Score** for a single query. The F1-Score is the harmonic mean of Precision and Recall.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): A list of retrieved documents from the model. Each dictionary contains:
  - `'source'`: A unique identifier for the document.
  - `'score'`: The relevance score of the document.
- `contexts` (`List[Dict[str, Any]]`): A list of dictionaries representing the relevant contexts. Each dictionary contains:
  - `'source'`: A unique identifier for the relevant document.
  - `'relevance'`: The relevance score (non-zero indicates relevance).

### **Output**
- `float`: The F1-Score, providing a balance between Precision and Recall. If both Precision and Recall are `0.0`, it returns `0.0`.

### **Why It Is Used**
The F1-Score combines Precision and Recall into a single metric, offering a balanced evaluation of the retrieval system's performance. It is particularly useful when there is a need to balance the trade-off between Precision and Recall, ensuring that the system is both accurate and comprehensive.

---

### Additional Metrics

### `llm_retrieval_scorer`

```python:rag-advanced/notebooks/scripts/retrieval_metrics.py
async def llm_retrieval_scorer(model_output: List[Dict[str, Any]], question: str) -> Dict[str, float]:
```

### **What It Does**
Evaluates the retrieval results using a language model (LLM) and computes relevance scores, including mean relevance and relevance rank score.

### **Input**
- `model_output` (`List[Dict[str, Any]]`): The list of retrieved documents from the model.
- `question` (`str`): The query or question for which the retrieval is being evaluated.

### **Output**
- `Dict[str, float]`: A dictionary containing:
  - `'relevance'`: The mean relevance score.
  - `'relevance_rank_score'`: The relevance rank score based on the position of highly relevant documents.

### **Why It Is Used**
This metric leverages a language model to assess the quality of retrieval results beyond traditional metrics. It provides insights into both the average relevance of retrieved documents and the effectiveness of their ranking, enhancing the evaluation with advanced language understanding.

---

### Direct Evaluation with Heuristics:

Heuristics-based evaluation focuses on direct assessment without relying on ground truth answers. Here are some examples of structural checks you can implement:

- Check for specific elements: Does the response contain bullet points if the user asked for a list? Does it include code snippets if the query was about code?
- Enforce length constraints: Is the response within a reasonable length? Is it too short or too long?
- Validate structured output: If your RAG system is expected to generate structured output (e.g., JSON), you can check if the response is a valid JSON object.

These heuristics help enforce certain expectations about the output format, which can improve the robustness and reliability of your RAG system. They can catch obvious errors or inconsistencies before you move on to more sophisticated evaluation methods.

### Reference-Based Evaluation with Traditional Metrics:

For a more comprehensive evaluation of response quality, we can use reference-based evaluation. This involves comparing the generated response to a ground truth or reference response.

Here are some common metrics used in reference-based evaluation:

- Similarity Ratio: This measures the degree of overlap between the generated response and the reference response, often after normalizing the text (e.g., removing punctuation and converting to lowercase). A higher similarity ratio indicates a closer match.
- Levenshtein Distance: This metric calculates the minimum number of edits (insertions, deletions, substitutions) needed to transform the generated response into the reference response. A lower Levenshtein distance suggests a higher similarity.
- ROUGE and BLEU: These metrics (commonly used in machine translation and text summarization) also assess the overlap between generated text and reference text, but they consider different aspects like word sequences (ROUGE) and precision (BLEU).

---

## Limitations of Traditional Metrics:

While traditional metrics like similarity ratio and Levenshtein distance can be useful for evaluating generated text, they have limitations when it comes to assessing the quality of responses in RAG systems.

- Lack of Semantic Depth: Traditional metrics often focus on surface-level matching of words or phrases. They may not capture the deeper meaning or semantic nuances of the generated response. For example, two responses might have similar wording but convey different meanings, and traditional metrics might not be able to distinguish between them.
- Ignoring Contextual Relevance: Traditional metrics may not adequately consider the relationship between the generated response and the user's original query. A response might be grammatically correct and contain relevant keywords, but it might not actually answer the user's question in a meaningful way.
- Fuzzy Matching: The results of traditional metrics can sometimes be difficult to interpret because they often rely on fuzzy matching techniques. It might not be clear why a particular score was assigned or what aspects of the response contributed to that score.
- Subjectivity: Evaluating the quality of generated text, especially in complex tasks like question answering or dialogue generation, can be inherently subjective. What one person considers a good response, another might not. Traditional metrics may struggle to capture this subjectivity.

---

## LLM Evaluators: A More Nuanced Approach:

To overcome these limitations, we can turn to LLM evaluators. The idea is to leverage the power of LLMs to assess the quality and relevance of generated responses in a more sophisticated way.

How LLM Evaluators Work:

LLM evaluators are based on two key capabilities of large language models:

- Text Comparison: LLMs can effectively compare different pieces of text and identify similarities and differences in meaning and style.
- Instruction Following: LLMs can be trained to follow instructions and perform specific tasks, including evaluation.

The Process:

- Input: We provide the LLM evaluator with several pieces of information:
  - The retrieved context used by the RAG system.
  - The generated response.
  - The user's original query.
- Instructions/Scoring Criteria: We also give the LLM a set of instructions that outline the criteria it should use to evaluate the response. For example, we might tell the LLM to consider factors like relevance to the query, factual accuracy, coherence, and clarity.
- Evaluation: The LLM then uses its learned internal representations of language to compare the response to the context and the query, applying the provided scoring criteria.
- Output: The LLM outputs a score or a judgment (e.g., "good," "bad," "neutral") that reflects its assessment of the response quality.

Important Considerations:

- Determinism: LLM-generated scores might not be perfectly deterministic. Because LLMs are probabilistic models, they might produce slightly different scores for the same input on different runs.

- Evaluating the Evaluator: A key challenge is how to evaluate the LLM evaluator itself. If we're using an LLM to judge the quality of another LLM's output, how do we know if the evaluator is reliable and accurate? We'll address this question later in the chapter.

---

## LLM Evaluators: Limitations & Solutions:

Limitations 1: Non-Determinism:

LLM-generated scores can be non-deterministic. This means that if you run the same evaluation multiple times, you might get slightly different scores each time. This is because LLMs are probabilistic models – their outputs are based on probabilities rather than strict rules.

Solutions: Multiple Trials:

To mitigate the issue of non-determinism, it's recommended to run multiple evaluation trials (e.g., 3-5) for each experiment and then average the scores. This provides a more stable and reliable estimate of the system's performance.

Limitation 2: Evaluating the Evaluator:

A key challenge with using LLMs as judges is determining how to evaluate the evaluator itself. If we're relying on an LLM to assess the quality of another LLM's output, how do we know if the evaluator is making accurate and reliable judgments?

Solution: Dedicated Evaluation Team:

Having a dedicated team or individuals focused on evaluation can significantly improve the quality and consistency of the evaluation process. This team can develop best practices, build and maintain evaluation datasets, and ensure that the LLM evaluator remains aligned with human judgment over time.

---

## Data Ingestion and Preprocessing

<img width="386" alt="image" src="https://github.com/user-attachments/assets/0e9b5dfe-c6c7-46f1-8256-9d69651537bc">

### Why is tokenization important?

- Context Windows: Language models have a limited context window – the maximum number of tokens they can process at once. Accurate tokenization helps manage these windows effectively.
- Computational Costs: The number of tokens directly influences the computational resources required to run the RAG system. Accurate token counts help estimate these costs

### Why Clean the Text? Cleaning the text is vital for:

- Improving Retrieval Accuracy: Removing irrelevant characters or formatting helps the retrieval system focus on the meaningful content.
- Ensuring Smooth Tokenization: Special characters can sometimes disrupt the tokenization process, leading to errors or unexpected results.

### Retrieval Methods

**TF-IDF (Term Frequency-Inverse Document Frequency):** This is a basic retrieval method. It assigns weights to terms in documents based on their frequency within the document and across the entire corpus.

**BM25 (Best Matching 25):** BM25 is a more advanced retrieval method that builds upon TF-IDF. It addresses some of the limitations of TF-IDF by:

- Considering Document Length: BM25 normalizes the term frequency based on the length of the document, preventing longer documents from being unfairly favored.
- Handling Term Frequency Saturation: BM25 uses a saturation function to prevent terms that appear very frequently in a document from having an overly strong influence on the relevance score.
- Probabilistic Model: BM25 employs a probabilistic model to estimate the relevance of documents to a query, making it more robust and accurate.

### The Three Pillars of Data Ingestion:

We can break down the data ingestion process into three core components, or pillars:

**Data Parsing:**

This is the first step, where we handle the variety of formats your data might come in. Whether it's PDFs, Word documents, web pages, or code files, data parsing converts them all into a standardized format that the RAG system can understand.

**Chunking:**

Once we have the data in a consistent format, we need to break it down into smaller, more manageable chunks. This is crucial for efficient retrieval. Instead of searching through entire documents, the RAG system can focus on smaller chunks that are more likely to contain the relevant information.

**Metadata Management:**

Metadata is like adding tags or labels to your data. It provides extra information about the content without requiring the system to read through everything. This can include things like the author, date, source, topic, or keywords associated with a particular chunk of data. Metadata helps the RAG system understand the context and relevance of the information, improving retrieval accuracy.

### Chunking 

**Semantic Chunking (aka Grouping by Meaning) **

Instead of dividing the text into fixed-length chunks, semantic chunking aims to group sentences together based on their meaning or topic.

It helps with: 

- Preserving Context: This method helps maintain the contextual relationships between sentences, ensuring that related information is kept together within a chunk.
- Adaptive Chunk Sizes: Chunk sizes can vary depending on the length of the semantic units in the text, resulting in more meaningful and coherent chunks.
- Semantic chunking can significantly improve the relevance of retrieved information. By keeping related sentences together, the RAG system is more likely to find chunks that contain the complete and relevant context for a given query.

**Hierarchical Chunking:** This involves creating a hierarchy of chunks, where parent chunks provide broader context and child chunks offer more specific details. This can be useful for representing different levels of information within a document.

**Small-to-Big Chunking:** This technique starts with small, focused chunks and then expands to include more context as needed. It can be particularly helpful for handling long sections of text.

### Metadata

Metadata is essentially data about your data. It's like the label on a jar that tells you what's inside without having to open it.

In RAG systems, we typically work with two types of metadata:

- Document Metadata: This provides information about the entire document, such as:
  - Title: The title of the document.
  - Source: Where the document came from (e.g., website, book, internal documentation).
  - Summary: A brief overview of the document's content.

- Chunk Metadata: This gives context to specific segments of text within a document, such as:
  - Structural Information: Is this chunk a header, a paragraph, a code block, etc.?
  - Programming Language (for Code): What programming language is used in this code chunk?
  - Version-Specific Information: Is this chunk relevant to a specific version of a product or software?

---

## Advanced Retrieval and Re-ranking

### Limitations of Simple RAG system

1. Limited Contextual Understanding in Embeddings:

While methods like TF-IDF and BM25 are effective for basic retrieval, they have a limited capacity to capture the different meanings and contexts of the same word. They primarily rely on word frequencies and co-occurrences without a deeper understanding of semantic relationships.

To address this, we need to use embeddings generated by deep neural networks. These models are trained on vast amounts of text data (billions of tokens) and can learn more nuanced representations of words and their various contexts. They can better capture semantic similarities and relationships between words, improving the accuracy of retrieval.

2. Misalignment Between Queries and Documents:

User queries often lack the precise language or structure that aligns perfectly with the wording used in relevant documents. This mismatch can make it difficult for simple retrieval systems to find the best matches.

Example: A user might ask, "How do I track experiments in W&B?" while the relevant document uses the phrase "experiment tracking." A simple keyword-based retrieval system might miss this connection.

3. Query Complexity:

Simple queries, like "What is W&B?", are easier to match to a single relevant document or chunk. However, complex queries, which might involve multiple concepts or sub-questions, often require retrieving information from multiple parts of the knowledge base.

Example: A query like "How can I compare different model versions and visualize their performance metrics?" might require retrieving information about model versioning, performance metric logging, and visualization tools within W&B. A simple retrieval system might only find information about one of these aspects.

4. Position of Relevant Chunks:

The order in which retrieved results are presented is crucial. The most relevant information should be ranked higher to ensure the user can easily find it. Simple retrieval systems might not adequately prioritize the most relevant chunks.

### Retrieve with CoT

For complex question-answering (QA) tasks, especially those that require multi-step reasoning or involve finding information from multiple sources, combining retrieval with chain-of-thought reasoning can be very effective.

This technique differs from simple query decomposition in that the reasoning steps are not generated upfront. Instead, the system iteratively retrieves information and performs reasoning based on the retrieved context.

Process:

- Initial Retrieval: The system first retrieves relevant documents or chunks based on the initial user query.
- CoT Prompting: The LLM is then prompted with the query and the retrieved context, and it's instructed to generate a reasoning sentence (T1) that represents an intermediate step towards finding the answer.
- Retrieval for Reasoning Step: The system retrieves new documents or chunks relevant to the reasoning sentence (T1).
- Loop Continuation: Steps 2 and 3 are repeated, generating new reasoning sentences (T2, T3, etc.) and retrieving corresponding information until a termination condition is met.
- Termination Condition: The loop typically terminates when the system finds the answer to the original query within the retrieved context. This could be determined by checking if the answer is a substring of the retrieved text or by using other criteria.


Example:

User Query: "What are the advantages of using Weights & Biases for experiment tracking compared to using a spreadsheet?"

Steps:

- Initial Retrieval: Retrieve documents related to Weights & Biases and experiment tracking.
- T1 (Reasoning): "Weights & Biases offers automatic logging of experiment data, while spreadsheets require manual entry."
- Retrieve for T1: Find documents about automatic logging and manual data entry.
- T2 (Reasoning): "Automatic logging saves time and reduces errors compared to manual entry."
- Retrieve for T2: Find documents discussing the benefits of automatic logging.
- Termination: The retrieved documents likely contain information about the advantages of Weights & Biases (e.g., time-saving, error reduction), so the loop terminates.


Complexities and Variations:

- Number of Reasoning Steps: The complexity can be adjusted by controlling the number of reasoning steps allowed before termination.
- Types of Reasoning: The reasoning steps can involve different types of logic or inference, depending on the task.
- Retrieval Methods: Different retrieval methods (e.g., dense retrieval, keyword-based retrieval) can be used within the loop.

### Metadata Filtering

The benefits of metadata filtering are:

- Enhanced Retrieval Relevance: By narrowing down the search space based on metadata, we can significantly improve the relevance of the retrieved information.
- More Accurate Responses: Providing the LLM with a more focused and relevant context leads to more accurate and helpful responses.
- Efficient Retrieval: Filtering the vector store before performing the similarity search can also improve retrieval efficiency.

### The "Lost in the Middle" Problem

While retrieving more documents, by increasing the value of 'k', generally leads to higher recall and a greater chance of including all relevant information, we must consider the limitations of LLMs. LLMs have a finite context window, a maximum amount of text they can process at once. As we increase the number of retrieved documents, the context length grows, potentially exceeding the LLM's capacity.  Therefore, we face a trade-off:  retrieving enough documents to ensure high recall while keeping the context length manageable for the LLM to process effectively. 

Research has shown that LLMs tend to struggle with accessing relevant information when it's located in the middle of long contexts. This is known as the "lost in the middle" problem.

The "Lost in the Middle" paper demonstrated this phenomenon through a control study. They varied the position of the most relevant document within a set of retrieved results and observed how it affected the LLM's performance. The LLM performed best when the relevant information was placed at the beginning or the end of the context. Performance significantly degraded when the relevant document was in the middle of a long context.

### Possible Solutions to The "Lost in the Middle" Problem

**Cross-Encoder Transformers for Reranking:**

- Pairwise Comparison: Cross-encoder transformers are specifically designed to compare pairs of text sequences. In the context of reranking, we pass pairs of the user query and each retrieved document to the cross-encoder.
- Training for Relevance: We train the cross-encoder to learn how to assign a relevancy score to each pair. This training often involves using a dataset of query-document pairs labeled with their relevance.
- BERT as a Foundation: Popular transformer models like BERT are often used as the basis for cross-encoders because they are effective at capturing contextual relationships and semantic similarities between text sequences.

Reranking Process:

- Initial Retrieval: We first retrieve a set of documents using a standard retrieval method (e.g., cosine similarity search).
- Cross-Encoder Scoring: For each retrieved document, we create a pair with the user query and pass this pair through the cross-encoder. The cross-encoder assigns a relevance score to each pair.
- Reordering: We then reorder the retrieved documents based on their new relevance scores, with the highest-scoring documents ranked first.

Latency Considerations:

- Reranking with a cross-encoder can be computationally expensive, especially if we're retrieving a large number of documents initially. Therefore, it's important to be mindful of the initial top-k parameter used in the retrieval step.
- Balancing Recall and Speed: A smaller top-k value will result in faster reranking but might sacrifice recall.
- Optimal top-k: Finding the optimal top-k value often involves balancing the need for high recall with the need for reasonable latency.

**Reciprocal Rank Fusion**

How Rank Fusion Works:

- Retrieve from Multiple Sources: The system performs retrieval from multiple data sources, each potentially using different retrieval methods or focusing on different aspects of the knowledge base.
- Identify Unique Documents: The retrieved results from all sources are combined, and any duplicate or redundant documents are identified.
- Aggregate Ranks: For each unique document, the system aggregates its ranks from the different retrieval sources into a unified or fused rank. This aggregation can be done using various methods, such as taking the average rank, the highest rank, or a weighted combination of ranks.
- Order by Fused Rank: The unique documents are then sorted in descending order based on their fused ranks.
- Select Top-N: The top-N documents from this sorted list are selected as the final retrieved results.


Benefits of Rank Fusion:

- Reduced Latency: Rank fusion is generally faster than reranking with a cross-encoder, especially when dealing with a large number of retrieved documents from multiple sources.
- Improved Recall: By considering results from multiple sources, rank fusion can enhance the recall of the system, increasing the chances of finding all relevant information.
- Flexibility: Rank fusion allows for flexibility in how ranks are aggregated, allowing you to prioritize certain sources or retrieval methods based on your specific needs.

---

### Traditional RAG vs. Tool Use:

Traditional RAG typically relies on a vector store of unstructured text data. Retrieval involves finding similar documents or chunks within this vector store. Tool Use in RAG expands the scope of RAG by allowing the system to access information and perform actions using a wide range of external tools. This might include:

- Web search: Querying search engines to retrieve up-to-date information.
- Python interpreter: Executing Python code to perform calculations, data manipulation, or access libraries.
- Structured data: Querying SQL databases or APIs to retrieve specific information.
- Any API: Essentially, any tool that can be interacted with programmatically through code and APIs.

### Response Synthesis and Prompting

**Response Synthesis: The Translator**

Think of response synthesis as the translator in your RAG system. Its job is to take the raw information retrieved from the knowledge base and transform it into a coherent, informative, and easily understandable response for the user.

**Prompting: The Instruction Manual**

Prompting is like giving your large language model (LLM) a detailed instruction manual. It provides the LLM with context, guidelines, and specific instructions on how to generate a response.

**Elements of an Effective Prompt:**

- Role: Define the role you want the LLM to play (e.g., "You are a helpful assistant.")
- Goal: Clearly state the objective of the response (e.g., "Answer the following question.")
- Context: Provide any relevant background information or context that might be helpful.
- Instructions: Give specific instructions on how the LLM should generate the output (e.g., "Use bullet points to list the steps.")

### Advanced Prompt Techniques

**Chain-of-Thought Prompting:**

Step-by-Step Reasoning: Instead of directly asking for an answer, the prompt guides the LLM to generate a series of logical steps or reasoning statements before arriving at the final solution.

Example: "Think step by step: First, ..., Then, ..., Finally, ..."


**Self-Reflection Prompting**

Internal Evaluation: The prompt encourages the LLM to evaluate its own response, identify potential errors or inconsistencies, and make corrections or refinements.

Example: "Review your answer and ensure it is accurate and consistent with the provided information."


**Tree-of-Thought Prompting**

Exploring Multiple Paths: The prompt enables the LLM to explore multiple reasoning paths simultaneously, similar to how a chess player considers different moves.

Finding the Best Solution: This allows the LLM to evaluate different possibilities and choose the most promising approach.


**Benefits of Advanced Prompting:**

- Enhanced Reasoning: These techniques improve the LLM's ability to think logically, break down complex problems, and arrive at well-reasoned solutions.
- Handling Complexity: RAG systems can effectively tackle more intricate queries and tasks that require multi-step reasoning or exploration of multiple solutions.
- Nuanced Responses: The LLM can generate more detailed, context-aware, and insightful responses by incorporating its reasoning process.

**Challenges:**

- Token Limitations: These advanced techniques often involve longer and more complex prompts, which can increase the number of tokens used, potentially exceeding the LLM's context window.
- Prompt Design Complexity: Crafting effective prompts for these advanced techniques requires careful design and consideration to guide the LLM's behavior effectively.

### Troubleshooting RAG system

Even well-designed RAG systems can encounter challenges that affect the quality and consistency of their responses. This section outlines common issues and provides practical solutions to address them.

**1. Incoherent Responses**

- Problem: The LLM generates responses that lack logical flow, jump between topics, or are difficult for users to understand.

- Solution: Structured Prompts
Roadmap for Responses: Use prompts that clearly define the desired structure and organization of the response.
Example: "Provide a step-by-step guide with bullet points for each step."

**2. Struggles with Ambiguous Queries**

- Problem: The LLM has difficulty interpreting unclear or vague user queries, leading to irrelevant or unhelpful responses.

- Solution: Clarification Prompts

Seeking More Information: Design prompts that encourage the LLM to ask clarifying questions when it encounters ambiguous queries.
Example: "If the user's question is unclear, ask for more details about what they are trying to achieve."

**3. Inconsistency Across Topics**

- Problem: The RAG system's performance varies depending on the subject matter. Some topics might have more accurate or coherent responses than others.

- Solution: Regular Knowledge Base Updates

Fresh and Aligned Information: Keep the information in your knowledge base up-to-date, consistent, and well-structured.
Addressing Gaps: Regularly review your knowledge base to identify areas where information is missing or outdated and make necessary updates.

### Optimisation for Speed and Efficiency

Best Practices:

- Minimize Abstractions: While frameworks are helpful for generic tasks, consider writing custom pure Python code for performance-critical sections of your RAG system. This gives you more control over optimization and can significantly improve efficiency.
- Embrace Asynchronous Programming: Asynchronous programming is essential for handling potential bottlenecks in your RAG system, especially if you're dealing with multiple data sources, external API calls, or complex processing steps.

**Choosing a Vector Store**

- For most RAG systems, vector databases like Weaviate offer a good balance of performance, features, and ease of use.
- One of the key advantages of these databases is their ability to efficiently filter vectors based on metadata, which can significantly speed up retrieval, as demonstrated by the performance boost Wandbot experienced after switching from FAISS to Chroma.

**Recall vs. Speed**

- While some vector stores prioritize raw speed, they often achieve this by sacrificing recall—the ability to find all relevant information.
- In many RAG applications, especially those involving question answering or knowledge retrieval, recall is more important than raw retrieval speed. You want to ensure that the system retrieves all the potentially relevant information, even if it takes a bit longer.

**Deployment Strategies**

1. In-Memory Vector Store:

- Lower Latency: Storing the vector store in memory can significantly reduce latency, making retrieval very fast.
- Suitable for Smaller Datasets: This approach is generally suitable for applications with relatively small datasets that can fit comfortably in memory.

2. Dedicated Cloud-Managed Database:

Scalability and Management: Using a dedicated cloud-managed vector database (like Weaviate's cloud offerings) provides better scalability and simplifies management and configuration, especially as your application and dataset grow.

### Parallel LLM calls

**Language Expression Language (LEL)**

LEL provides a framework for managing and orchestrating LLM calls in a structured and efficient way. It allows you to define workflows where some LLM calls are executed sequentially (one after the other) and others in parallel.

Benefits:

- Code Readability: LEL can make your code more readable and easier to understand, especially when dealing with complex LLM call sequences.
- Efficiency: It helps you optimize the execution of LLM calls by parallelizing where possible.
- Flexibility: It often allows you to switch between synchronous and asynchronous modes seamlessly.

Batching User Queries

Grouping Similar Queries: If possible, try to batch similar user queries together. This allows you to process multiple queries in a single LLM call, further improving efficiency.
