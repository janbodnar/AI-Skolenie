# Large Language Models (LLM)

Language models (LMs) are artificial intelligence systems that learn from patterns in
text. Their primary task is to **predict the next word** (or part of a word) in a
sequence, producing statistically probable and meaningful output.

**Large Language Models (LLMs)** are the modern evolution of these systems. Thanks
to vast amounts of data and computational power, they can:

*   Generate fluent text in natural language.
*   Answer questions and explain complex concepts.
*   Summarize long documents and translate between languages.
*   Write and debug computer code.
*   Solve logical tasks and analyze sentiment.

> **Core concept:** LLMs are not databases of facts, but **probability generators**.
> They do not know "truth" in the human sense, but they can very accurately predict
> which word should follow in a given context.

## How LLMs Work (Simplified Overview)

Although technically complex, their working principle can be broken down into four
steps:

1.  **Tokenization:** Input text is split into smaller units called *tokens*
    (e.g., whole words, word roots, or sub-word parts).

2.  **Embedding:** Each token is converted into a numeric vector that captures its
    meaning and relationships to other words.

3.  **Processing (Transformer & Attention):** The model's core is the *Transformer*
    architecture. It uses the *Attention* mechanism, which allows the model to focus
    on important parts of the sentence regardless of their position, helping it
    understand context and word relationships.

4.  **Prediction:** The model calculates the probability for every possible next
    token and selects the most suitable one. This process repeats until the response
    is complete.

### Glossary of Key Terms

| Term           | Description |
| :------------- | :----------------------------------------------------------------- |
| **Token**      | The basic unit of text for the model (e.g., "umelá", "inteligencia", "-cia"). |
| **Parameter**  | Internal variable the model learns during training. Modern models have billions to trillions of parameters. |
| **Context Window** | The maximum length of text (in tokens) the model can process at once (input + output). |
| **Hallucination**  | When the model generates content that appears convincing but is factually incorrect or made up. |

---

## Classification of Language Models

LLMs can be categorized by several criteria. Understanding these categories is
essential for navigating the ecosystem:

### A. By Architecture
*   **Decoder-only (e.g., GPT, LLaMA):** The most common type today. Optimized for text generation (autoregressive models).
*   **Encoder-Decoder (e.g., T5, BART):** Better suited for transformation tasks like translation or summarization.
*   **Mixture-of-Experts (MoE) (e.g., Mixtral, Gemini 1.5):** An architecture where only part of the network ("experts") is activated per task, increasing efficiency and speed.

### B. By Openness / Accessibility
*   **Open Weights / Open Source (e.g., LLaMA, Mistral):** Model weights are publicly available. Researchers and companies can download, run on their own servers, and modify them.
*   **Closed Source / Proprietary (e.g., GPT-4, Claude, Gemini):** Models are accessible only via API or web interface from the provider. Their internal structure and training data are proprietary.

### C. By Size (Number of Parameters)
*   **Small LLM (1B – 8B):** Fast, suitable for local use and simple tasks.
*   **Medium LLM (8B – 70B):** Good balance between performance and hardware requirements.
*   **Large LLM (70B+):** Most powerful models for complex reasoning, demanding to operate.

---

## Key Concept: Model Reasoning Approach

This is one of the most important distinctions for understanding the current
technology landscape.

### Classical (Generative) LLMs
These models generate responses **directly and linearly**, word by word.
*   **Principle:** Instant prediction of the next token based on the context so far.
*   **Strengths:** Fast, inexpensive, and excellent for creative writing, translation, or general conversation.
*   **Weaknesses:** Can fail on complex logic, math, or planning because they don't
    "think ahead," they just react based on pattern recognition.
*   **Examples:** LLaMA 3 (base), Mistral 7B, GPT-3.5.

### Reasoning LLMs

These models have an additional mechanism allowing them to **plan and review**
their process.
*   **Principle:** Before generating the final answer, the model creates a "thought
    process" (*Chain-of-Thought*), verifies facts, or breaks the task into subtasks.
*   **Strengths:** Significantly better results in mathematics, programming, scientific reasoning, and logic puzzles.
*   **Weaknesses:** Slower (they must "write" their thoughts) and more computationally expensive.
*   **Examples:** OpenAI o1, DeepSeek R1, Claude 3.5 Sonnet (with enhanced reasoning capabilities).

> **Analogy:** A classical LLM is like a student who answers immediately, intuitively. A reasoning LLM is like a student who takes a piece of paper, jots down notes, works through an example, and then responds.

### Example of a Reasoning Model in Action: DeepSeek R1

**Prompt:**

```
Translate into German:

Все счастливые семьи похожи друг на друга, каждая несчастливая семья несчастлива
по-своему. Все смешалось в доме Облонских. Жена узнала, что муж был в связи с
бывшею в их доме француженкою-гувернанткой, и объявила мужу, что не может жить с
ним в одном доме. Положение это продолжалось уже третий день и мучительно
чувствовалось и самими супругами, и всеми членами семьи, и домочадцами. Все
члены семьи и домочадцы чувствовали, что нет смысла в их сожительстве и что на
каждом постоялом дворе случайно сошедшиеся люди более связаны между собой, чем
они, члены семьи и домочадцы Облонских. Жена не выходила из своих комнат, мужа
третий день не было дома. Дети бегали по всему дому, как потерянные; англичанка
поссорилась с экономкой и написала записку приятельнице, прося приискать ей
новое место; повар ушел вчера со двора, во время самого обеда; черная кухарка и
кучер просили расчета.
```

**AI Thinking Process (Abridged):**

> The user has sent a query in Russian, asking for a translation into German. The
> text is the famous opening of Tolstoy's Anna Karenina. The user likely wants an
> accurate, literary translation that preserves the tone and meaning of the original.
> I need to provide a clean, direct German version, maintaining the paragraph
> structure and the essence of Tolstoy's prose. No explanations are needed unless
> requested; just deliver the requested translation clearly.

**Output:**

```
Alle glücklichen Familien sind einander ähnlich, jede unglückliche Familie ist auf ihre eigene Weise
unglücklich. Im Hause Oblonski war alles durcheinander. Die Frau hatte erfahren, dass der Mann ein Verhältnis
mit der französischen Gouvernante hatte, die früher im Hause war, und erklärte ihrem Mann, dass sie nicht mit
ihm unter einem Dach leben könne. Dieser Zustand dauerte bereits den dritten Tag und wurde schmerzlich empfunden
von den Ehegatten selbst, von allen Familienmitgliedern und vom Hauspersonal. Alle Familienmitglieder und das
Hauspersonal fühlten, dass ihr Zusammenleben sinnlos sei und dass auf jedem beliebigen Gasthof zufällig
zusammengetroffene Menschen mehr miteinander verbunden seien als sie, die Mitglieder der Familie Oblonski
und ihr Gesinde. Die Frau verließ ihre Zimmer nicht, der Mann war den dritten Tag nicht zu Hause.
Die Kinder liefen wie verloren im ganzen Haus umher; die Engländerin hatte sich mit der Wirtschaftlerin
gestritten und schrieb einem Freund einen Brief, sie möge ihr eine neue Stelle suchen; der Koch war gestern
während des Essens vom Hof gegangen; die Küchenmagd und der Kutscher baten um Auszahlung ihres Lohnes.
```

## Overview of Key LLM Models and Their Origins

The LLM landscape is global. It's important to know who develops a model, as this
influences its linguistic nuances, content moderation policies, and legal terms.

| Model          | Developer / Organization      | Country of Origin | Access Type  |
| :------------- | :---------------------------- | :---------------- | :----------- |
| **GPT-4 / ChatGPT** | OpenAI                        | USA               | Closed       |
| **Claude 3.5** | Anthropic                     | USA               | Closed       |
| **Gemini 1.5** | Google DeepMind               | USA               | Closed       |
| **Llama 3**    | Meta (Facebook)               | USA               | Open Weights |
| **Mistral / Mixtral** | Mistral AI                    | France            | Open/Closed  |
| **Grok**       | xAI                           | USA               | Closed       |
| **Qwen 2.5**   | Alibaba Cloud                 | China             | Open Weights |
| **DeepSeek**   | DeepSeek                      | China             | Open Weights |
| **Falcon**     | TII (Technology Innovation Institute) | UAE               | Open Weights |
| **YandexGPT**  | Yandex                        | Russia            | Closed       |

*Note: "Open Weights" means the model is available for download, but the license may
not necessarily be completely unrestricted for commercial use.*

## Model Variants: A Guide to Common Labels

When choosing a large language model, you'll often encounter labels like **Flash,
Pro, Mini, Thinking**, or **Turbo**. While not standardized, these names generally
indicate a trade-off between **performance, quality, speed, and cost**.

| Label                     | Typical Meaning                                                                         | Common Use Cases                                                        |
| :------------------------ | :-------------------------------------------------------------------------------------- | :---------------------------------------------------------------------- |
| **Flash**                 | Fast and efficient, designed for high request volumes                                   | Chatbots, customer support, summarization, everyday text tasks          |
| **Mini**                  | Smaller, more resource-efficient model                                                   | Simple tasks, high-volume automation, applications with large throughput |
| **Nano**                  | Very small, minimal hardware requirements                                               | Mobile & local apps, devices with constrained resources                 |
| **Pro**                   | More powerful for complex tasks                                                         | Analysis, programming, complex professional tasks                       |
| **Ultra**                 | Premium tier in a product line                                                          | Most demanding tasks where quality is the top priority                  |
| **Lite**                  | Lightweight version of a model                                                          | Quick, low-cost processing for routine tasks                            |
| **Fast**                  | Optimized primarily for response speed                                                  | Interactive apps, real-time communication                               |
| **Turbo**                 | Optimized for higher speed and efficient resource use                                   | High-throughput applications                                            |
| **Thinking**              | Model or mode that allocates more compute time to reasoning                             | Complex analysis, math, planning, programming                           |
| **Reasoning**             | Model specifically optimized for multi-step reasoning                                   | Demanding analytical and logical tasks                                  |
| **Instruct**              | Fine-tuned to follow instructions accurately                                            | Automation, text processing, AI assistants                              |
| **Base**                  | Foundation model without significant conversational fine-tuning                         | Developing custom AI solutions & further model fine-tuning              |
| **Chat**                  | Optimized for natural conversation                                                      | Chatbots, virtual assistants, customer communication                    |
| **Vision**                | Capable of working with images                                                          | Document analysis, photo analysis, charts, screenshots                  |
| **Multimodal**            | Works with multiple data types (text, image, audio, video)                              | Advanced AI assistants, multimedia apps                                 |
| **Coder / Code**          | Optimized for programming tasks                                                         | Code generation, review, debugging                                      |
| **Long Context**          | Processes very large amounts of text in one go                                          | Long documents, contracts, extensive analysis, large codebases          |
| **Embedding**             | Converts text/data into numeric vector representations                                  | Search, RAG (Retrieval-Augmented Generation), recommendation systems, similarity comparisons |
| **MoE (Mixture of Experts)** | Architecture where only part of the model is activated per request                    | Efficient compute utilization for large models                          |
| **Quantized / Q4, Q8**    | Lower numerical precision (needs less memory)                                          | Running models locally, hardware-constrained applications               |
| **Small / Medium / Large** | Indication of relative model size and performance                                    | Choosing the right balance of power, cost, and speed                    |

## How to Interpret These Labels

In practice, these labels can be understood along two key axes:

**Speed & Cost:**

`Nano → Mini → Flash / Lite → Standard → Pro → Ultra`

Generally, smaller and faster models are better for simple, repetitive tasks, while
more powerful models justify their cost for complex assignments.

**Reasoning Capability:**

`General → Thinking / Reasoning → Advanced Reasoning`

Models focusing on thinking or reasoning prioritize deep problem-solving over instant
responses.

### Important: Model Names are Not a Standard

Labels like **Flash, Pro**, or **Ultra do not have a consistent meaning** across all
providers. They are primarily product branding.

Therefore, when comparing models, don't rely solely on the name. Pay attention to:

* **Output Quality** – how well the model handles your specific task.
* **Reasoning Ability** – how well it solves complex problems.
* **Speed** – response latency.
* **Cost** – price per request/1M tokens.
* **Context Window** – how much information it can process at once.
* **Multimodal Capabilities** – can it handle images, audio, or video?

### Practical Rule of Thumb

Choosing the "largest" or "most powerful" model isn't always the best option.

For simple, high-volume tasks, a faster, cheaper model is often more cost-effective.
For complex decision-making, analysis, programming, or sophisticated reasoning, a
more powerful model is worth the investment.

In short:

> **Flash = speed and efficiency**
> **Pro = higher performance and quality**
> **Thinking / Reasoning = more deliberate, deeper thinking**
> **Mini / Nano = lower cost and hardware demands**

Choose the AI model based on your specific task and the desired balance of quality,
speed, and price, not just the name.

---

## Lifecycle: How LLMs Are Trained

Developing a model happens in several phases:

1.  **Pre-training:**
    *   The model "reads" terabytes of text from the internet, books, and code
        repositories.
    *   It learns statistical relationships between words and general knowledge about
        the world.
    *   The result is a *Base Model* – it can complete text but doesn't follow
        instructions effectively.

2.  **Fine-tuning & Instruction Tuning:**
    *   The model is trained on datasets in a *Question – Answer* format.
    *   It learns to follow commands: "Explain to me...", "Write code for...",
        "Summarize the text...".

3.  **Alignment (RLHF):**
    *   Using *Reinforcement Learning from Human Feedback* (RLHF), human evaluators
        rate model responses.
    *   The model learns to be helpful, harmless, and honest (e.g., refusing to
        generate illegal instructions).

## Practical Applications and Limitations

### Where are LLMs used?

*   **Assistants & Chatbots:** Customer support, personal assistants.
*   **Programming:** Code generation, debugging, explaining codebases (e.g., Copilot).
*   **Data Analysis:** Information extraction from unstructured text, contract
    summarization.
*   **Education:** Creating quizzes, personalized explanations, language proofreading.

### What to watch out for (Limitations)?

1.  **Hallucinations:** The model can confidently state false information. Always
    verify critical facts.
2.  **Context Window:** The model "sees" only a limited part of the conversation.
    Older information may be forgotten.
3.  **Bias:** Models reflect biases present in their training data (e.g., cultural or
    gender stereotypes).
4.  **Knowledge Cutoff:** The model may lack information about events occurring after
    its training completion (unless it has internet access).

---

## The Future

Development is moving in three main directions:

1.  **Agentic AI:** Models will not just answer, but *act* – autonomously planning
    tasks, using software and the internet to achieve goals.
2.  **Multimodality:** Full integration of text, image, audio, and video into a single
    model, enabling a more comprehensive understanding of the world.
3.  **Efficiency & Edge AI:** Creating smaller models that run locally on phones and
    laptops without internet access, enhancing privacy and reducing costs.

## Questions and Discussion

**Summary: Discuss why it is important for complex tasks to allow the model space
for "reasoning" (e.g., prompting *"Think step by step"*).**

Forcing a model to "think" step-by-step effectively transforms it from a simple
pattern-matcher into a deliberate reasoner. By externalizing its thought process,
we mitigate the risk of intuitive leaps to incorrect answers. This chain-of-thought
approach provides transparency, allowing us to audit the logic and identify where
errors occur. It ensures each logical step builds correctly upon the previous one,
which is crucial for complex tasks like mathematics, coding, or multi-faceted
planning, where providing only the final answer invites high-confidence but
potentially false outputs.
