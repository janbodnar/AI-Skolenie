# Claude and the company Anthropic

In today's world of artificial intelligence, Anthropic is one of the most closely  
watched companies. Unlike most technology firms that focus primarily on growth  
and commercial success, Anthropic bases its existence on a single mission:  
**developing safe artificial intelligence**. Their main product – the AI assistant  
**Claude** – ranks among the most capable and reliable models on the market.

## Company origin and founders

Anthropic was founded in **2021** by a group of researchers who had previously  
worked at OpenAI. The company is led by siblings:

*   **Dario Amodei (CEO):** Before leaving, he served as Vice President of  
    Research at OpenAI, where he co-developed the GPT-3 model. He is considered  
    one of the world's leading experts on AI safety.
*   **Daniela Amodei (President):** She is responsible for the company's business  
    operations, growth, and strategic partnerships.

Several other key researchers from OpenAI joined them at Anthropic,  
which attracted considerable attention in the industry.

**Why did they leave OpenAI?**

The main reason for leaving was internal disagreement regarding the **pace of  
development and safety priorities**. Dario Amodei and his colleagues feared  
that OpenAI was moving too fast without sufficient emphasis on safety research.  
Anthropic was thus founded as a company that prioritizes AI safety above all  
else – even before the commercial side.

## Philosophy: Constitutional AI

One of Anthropic's key contributions to the entire industry is a concept called  
**Constitutional AI**.

Traditional models learn to behave based on human feedback (RLHF –  
Reinforcement Learning from Human Feedback). This approach has disadvantages:  
it is expensive, slow, and human evaluators can be inconsistent and biased.

Anthropic developed an alternative:

1.  They define a set of principles – a "constitution" – that dictates how  
    the model should respond.
2.  The model learns to evaluate and correct its own responses according to  
    this constitution.
3.  The result is a model that is **helpful**, **harmless**, and **honest** –  
    the so-called **HHH** principle.

This approach reduces dependence on human evaluators and makes the model's  
behavior more predictable and consistent.

In January 2026, Anthropic published an updated constitution spanning  
**23,000 words** (compared to 2,700 words in 2023). The new version explains  
in more detail the reasons behind individual rules – for example, why Claude  
should not help undermine democracy. The constitution is released under the  
Creative Commons CC0 license and is freely available.

## Claude models – overview

Anthropic has gradually released several generations of the Claude model:

| Version | Release | Main new features |
| :--- | :--- | :--- |
| **Claude 1** | 2023 | First public model, HHH principles |
| **Claude 2** | 2023 | 100,000 token context window, improved coding |
| **Claude 3** (Haiku, Sonnet, Opus) | 2024 | Family of three models, surpassing GPT-4 |
| **Claude 3.5** (Sonnet, Haiku) | 2024 | Significant capability jump at lower cost |
| **Claude 3.7 Sonnet** | February 2025 | Extended Thinking – deep reasoning |
| **Claude 4** (Sonnet 4, Opus 4) | May 2025 | 7 hours of continuous coding, record SWE-Bench |
| **Claude Opus 4.1** | August 2025 | Can terminate permanently harmful conversations |
| **Claude Haiku 4.5** | October 2025 | Faster and cheaper model for smaller businesses |
| **Claude Opus 4.5** | November 2025 | Infinite Chats – no context limit |
| **Claude Opus 4.6** | February 2026 | Agent teams, PowerPoint integration |
| **Claude Sonnet 4.6** | February 2026 | Frontier performance for everyday work |

### Strategy of three tiers

Anthropic has long maintained a strategy of **three models for different uses**:

*   **Haiku** – the fastest and cheapest, suitable for simple tasks and batch  
    text processing.
*   **Sonnet** – a balanced price-performance ratio, ideal for most everyday  
    tasks.
*   **Opus** – the most powerful of all, intended for demanding analytical,  
    mathematical, and creative tasks.

## Top performance: Comparison with competitors

Benchmarks are standardized tests that measure AI models' capabilities in  
various areas. When **Claude 3 Opus** was released in March 2024, Anthropic  
published extensive comparisons. The results were remarkable:

Here is an updated table comparing the latest model versions as of March 2026.  
I have selected the flagships of individual companies: **Claude 4.6 Opus**  
(Anthropic), **Gemini 3.1 Pro** (Google), **GPT-5.4** (OpenAI), and **Grok 4**  
(xAI).

Please note that testing methodologies may differ slightly between  
manufacturers, but these values represent the current "State-of-the-Art" (SOTA)  
of models.

| Benchmark | What it measures | Claude 4.6 Opus | Gemini 3.1 Pro | GPT-5.4 | Grok 4 |
| :--- | :--- | :---: | :---: | :---: | :---: |
| **MMLU** | general knowledge | 91.2% | 90.8% | **92.1%** | 91.5% |
| **HumanEval** | coding | 89.4% | 85.2% | 90.1% | **91.2%** |
| **GSM8K** | basic mathematics | 97.8% | 96.5% | 98.2% | **98.9%** |
| **MATH** | advanced mathematics | 72.4% | 75.1% | 78.6% | **81.3%** |
| **GPQA** | PhD level (Diamond) | 91.3% | **94.3%** | 92.8% | 90.5% |

---

### Key observations on current leaders:

* **Gemini 3.1 Pro:** Currently dominates **GPQA** (scientific reasoning at  
  PhD level) and is unbeatable in multimodal processing (e.g., analyzing an  
  hour-long video at once).
* **Grok 4:** Thanks to its architecture of four cooperating agents (the so-called  
  "Multi-agent swarm"), it achieves top results in **mathematics and coding**,  
  where logical errors are minimized.
* **GPT-5.4:** Still holds the lead in **general knowledge (MMLU)** and in the  
  ability to autonomously control a computer (Computer Use), where it surpassed  
  human-level performance.
* **Claude 4.6 Opus:** Although it slightly lags in pure mathematics, it is  
  considered the "gold standard" for **creative writing and nuanced reasoning**,  
  where OpenAI and xAI models sometimes feel too robotic.

**Would you like to learn more about specific features of any of these models,  
for example, how Grok utilizes real-time data from the X network?**

> Claude 3 Opus was the first publicly available model upon release to surpass  
> the then-leader – GPT-4 – in most key benchmarks.

**Claude 3.5 Sonnet** raised the bar even higher – at a *lower price* than  
Opus, it achieved better results in coding, mathematics, and logical reasoning.  
It has long been the most popular model among developers.

**Claude 3.7 Sonnet** (February 2025) introduced the **Extended Thinking**  
feature – the model can perform an extensive internal thought process before  
the final answer and "think aloud" step by step. This significantly improved  
performance on complex tasks, similar to the Deep Think feature in DeepSeek.

**Claude 4** (May 2025) pushed the boundaries of coding – Opus 4 was able to  
work on a coding task continuously for 7 hours and achieved a record score on  
the prestigious SWE-Bench benchmark. Anthropic classified it at "Level 3" of  
its safety scale, meaning "significantly higher risk" – the first model with  
such a designation.

**Claude Opus 4.6** (February 2026) is, as of the release date of this chapter,  
the **most powerful model available**. According to measurements by the  
organization METR, it has a 50% chance of completing a task that an average  
employee would spend **14 hours** on. In practice, this means the ability to  
autonomously work on extensive projects.

> The performance of AI models evolves rapidly. Benchmarks capture the state at  
> the time of release – current models may achieve significantly higher values.

## New features and tools (2025–2026)

In addition to the models themselves, Anthropic gradually added important  
features:

*   **Web Search** (March 2025) – Claude can search the internet and work  
    with current information, similar to DeepSeek Search.
*   **Computer Use** (October 2024) – Claude can control a computer: move  
    the cursor, click, and type, thus performing tasks in other applications.
*   **Artifacts** (June 2024) – Claude generates code, documents, and web pages  
    in a separate window with a real-time preview of the result.
*   **Claude Code** (February 2025, GA May 2025) – a command line for developers  
    that allows Claude to read and write files, run commands, and work directly  
    in the terminal. As of early 2026, it is considered the **best AI coding  
    tool** on the market.
*   **Claude Cowork** (January 2026) – a graphical version of Claude Code for  
    regular users without technical training.

## Where to find Claude

| Access | Description |
| :--- | :--- |
| **claude.ai** | Web application, both free and paid versions (Max plan: $100–200/month) |
| **API for developers** | Integration of Claude into your own applications via the Anthropic API |
| **Amazon Bedrock** | Access to Claude through the Amazon AWS cloud platform |
| **Google Cloud Vertex AI** | Access to Claude through the Google cloud platform |
| **Microsoft Foundry** | Access to Claude through the Microsoft Azure platform (from 2026) |

## Dispute with the United States government

Anthropic sought cooperation with the U.S. government from the beginning, but  
in 2026 the relationship escalated into an open conflict. The cause was the  
**safety boundaries** that the company refused to remove.

### 1. Cooperation with the Pentagon (2024–2025)

In November 2024, Anthropic entered into a partnership with Palantir and  
Amazon Web Services to make Claude available to U.S. intelligence and defense  
agencies. In June 2025, a special model **Claude Gov** was released for  
classified operations. As of February 2026, Claude via Palantir was the **only  
AI model used in classified missions**.

### 2. Refusal to remove safety boundaries

Anthropic's policy prohibits using Claude for:
*   **mass domestic surveillance** of its own citizens,
*   **autonomous lethal weapons** without human control.

These contractual restrictions meant that the FBI and Secret Service could not  
fully utilize Claude. The Pentagon and the Trump administration were bothered  
by the restrictions in combat operations.

### 3. Ultimatum and ban (February 2026)

In February 2026, Secretary of Defense **Pete Hegseth** threatened to remove  
Anthropic from the Pentagon's supply chain if it did not remove the usage  
restrictions on Claude. Anthropic refused.

On **February 27, 2026**, Hegseth declared Anthropic a **"supply chain risk"**  
and President Trump ordered all federal agencies to stop using Anthropic's  
technologies. Agencies were given six months to phase out cooperation.  
Anthropic announced it would challenge this decision in court.

> Paradoxically, despite the ban, Claude was reportedly used by the U.S.  
> military during military operations in the following days.

### 4. FTC investigation – BigTech investments

As early as 2024, the Federal Trade Commission (FTC) launched an investigation  
into large investments in AI companies – specifically:

*   **Amazon → Anthropic** (investment of up to $4 billion)
*   **Google → Anthropic** (investment of more than $2 billion)

The FTC examined whether these agreements distort competition and whether  
Anthropic remains truly independent of its investors.

> **Conclusion:** The dispute reflects a profound question for the entire  
> industry – who determines what AI may be used for? Anthropic insists that  
> some uses are unacceptable regardless of government wishes. Other companies  
> have not yet had a similar conflict, which creates a competitive disadvantage  
> but also a strong reputation for trustworthiness.

## Claude Opus 4.6 vs. GPT-5: Battle of the top models

In August 2025, OpenAI released **GPT-5** – the most advanced model in the  
GPT series. The following comparison captures the state as of March 2026,  
after the release of Claude Opus 4.6.

### What GPT-5 brings

GPT-5 is a natively multimodal model – text and images were trained together  
from the ground up, not as two separate components. Key features:

*   **Integrated router** – GPT-5 automatically switches between fast and slow  
    "thinking" models according to the difficulty of the question (similar to  
    Extended Thinking in Claude, but works transparently in the background).
*   **Agentic capabilities** – the model can set up its own working environment  
    and autonomously search for sources in the browser.
*   **PhD-level capabilities** – CEO Sam Altman describes it as "a team of PhD  
    experts in your pocket."
*   **Availability** – free for all ChatGPT users; integrated into Microsoft  
    Copilot and Apple Intelligence.

### How does Claude Opus 4.6 compare?

| Feature | Claude Opus 4.6 | GPT-5 |
| :--- | :--- | :--- |
| **Release** | February 2026 | August 2025 |
| **Context window** | 1 million tokens (Infinite Chats) | ~128,000 tokens |
| **Task time-horizon** | 14 hours (METR, 50% success) | undisclosed |
| **Safety philosophy** | Constitutional AI, explicit boundaries | RLHF, "safe completions" |
| **Agent teams** | yes (native) | partially (via agentic mode) |
| **Multimodality** | text, images, documents | native (text + vision) |
| **Free version** | yes (limited) | yes (ChatGPT) |
| **Coding** | leader (Claude Code, SWE-Bench record) | very strong |

### Key differences in practice

**Where Claude Opus 4.6 excels:**  
Opus 4.6 has a significantly larger context window – thanks to the **Infinite  
Chats** feature, it can process in a single conversation content that GPT-5  
would have to split across multiple chats. For long documents, extensive coding  
projects, or complex analysis, this is a crucial advantage. METR measures a 50%  
chance of completing a 14-hour work task – the equivalent figure for GPT-5 is  
not publicly available.

**Where GPT-5 excels:**  
GPT-5 is free for the general public without source model restrictions and is  
deeply integrated into Microsoft and Apple ecosystems. Native multimodality  
makes it a natural tool when working with images and visual content. Some  
reviewers also appreciate its ability to create interactive mini-applications  
directly from the chat interface – "vibe coding" without the need to install  
developer tools.

**Safety approach:**  
This is a philosophical difference. Anthropic has written boundaries that  
Claude must not cross (Constitutional AI). OpenAI bet on "safe completions" –  
the model tries to answer borderline questions in a safe way rather than  
refusing. However, safety researchers discovered ways to bypass these  
protections on the very first day after GPT-5's release.

> **Conclusion:** Claude Opus 4.6 and GPT-5 are the two most powerful AI  
> solutions available for 2026. Opus 4.6 leads in context scope, autonomy,  
> and safety consistency. GPT-5 leads in accessibility, native multimodality,  
> and integration into consumer devices.

## Key differences from other AI assistants

| Feature | Claude (Anthropic) | ChatGPT / GPT-5 (OpenAI) | Copilot (Microsoft) |
| :--- | :--- | :--- | :--- |
| **Primary focus** | AI safety | Capabilities and accessibility | M365 integration |
| **Context window** | 1 million tokens | ~128,000 tokens | depends on version |
| **Constitutional AI** | yes | no | no |
| **Price** | free + Max plan ($200/mo.) | free + Pro plan | free + M365 |
| **Access** | claude.ai, API, Foundry | chat.openai.com, API | web, Windows, M365 |

## Chapter summary

*   **Anthropic** is a U.S. AI company founded in 2021 with the mission of  
    safely developing artificial intelligence.
*   The founders are siblings **Dario** and **Daniela Amodei**, who came from  
    OpenAI due to disagreements over safety priorities.
*   The key philosophy is **Constitutional AI** – the model behaves according  
    to defined HHH principles: helpful, harmless, honest. In 2026, the  
    constitution was expanded to 23,000 words.
*   **Claude 3 Opus** surpassed GPT-4 upon release; **Claude 4** (2025) set new  
    standards in coding; **Claude Opus 4.6** (February 2026) is currently the  
    most powerful model capable of autonomously executing 14-hour tasks.
*   **Claude Code** has been the leader among AI developer tools since 2025.
*   Anthropic refused to remove safety boundaries for the military, which in  
    February 2026 led to a **ban on use in federal agencies** in the U.S.

## Questions & discussion
