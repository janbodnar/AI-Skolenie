# Microsoft Copilot Ecosystem

When someone says "Copilot" today, most people imagine Microsoft's chatbot.  
That is true, but only partially. With its "Copilot" branding strategy,  
Microsoft unified all its artificial intelligence tools under one roof. For a  
beginner in the field of AI, however, it is important to know that **not every  
Copilot is the same**.

Different Copilot versions have different capabilities, work with different  
data, and are intended for different user groups. In this chapter, we will  
discuss the main products from the Copilot family so that you know which tool  
to use for a specific task.

> 📖 **Brief history:** Originally, Microsoft launched "Bing Chat" (February  
> 2023) as an AI chat assistant in the search engine. In November 2023, it was  
> renamed to **Microsoft Copilot** and the brand began to expand across its  
> entire portfolio. Today, Copilot is a unified AI platform across the entire  
> Microsoft 365 ecosystem.

## Overview of Copilot products

The following table provides a quick orientation overview of where to find  
individual tools and what they are used for:

| Product | Where it is used | Purpose |
| :--- | :--- | :--- |
| **Copilot** | web, mobile, Windows | general AI assistant |
| **Copilot for Microsoft 365** | Word, Excel, Outlook, Teams, Loop | working with documents and company data |
| **GitHub Copilot** | VS Code, JetBrains, GitHub.com, CLI | code generation, chat, agent mode, code review |
| **Copilot in Windows** | Windows 11 | PC control and window summarization |
| **Copilot Studio** | web | creating custom AI agents and Copilot extensions |
| **Copilot for Security** | SOC tools | security analysis and incident response |
| **Copilot for Sales / Service** | Dynamics 365, Salesforce | sales and customer support |
| **Copilot for Azure** | Azure Portal | cloud infrastructure management |
| **Copilot for Fabric** | Microsoft Fabric | data analysis and BI |
| **Microsoft 365 Copilot Chat** | web, Teams | enterprise AI chat with data protection (replacement for old Bing Chat Enterprise) |

## Detailed look at individual tools

To help you better understand the differences, let's look at each product in  
more detail:

### 1. Copilot (General Assistant)
This is the version known to most of the public.  
It is available for free (with the option of a paid Pro version) via web  
browser, mobile application, or as a standalone application in Windows.

*   **Purpose:** Answers questions, helps with writing texts, generates images
    (via DALL-E 3), and searches for information on the web.
*   **Advanced features (Copilot Pro):**
    *   **Copilot Voice** – voice interaction with the assistant
    *   **Copilot Vision** – the model sees and analyzes web pages you are on
    *   **Think Deeper** – deeper reasoning on complex problems (chain-of-thought)
    *   **Copilot Pages** – shared workspace for collaboration between people and AI
    *   **GPT-5 and model selection** – ability to switch between different AI models
*   **Data context:** Works primarily with public information from the internet.
    It does not see your company emails or private documents (unless you explicitly
    provide them in the chat).

### 2. Copilot for Microsoft 365 (Enterprise Assistant)
This is a premium version intended for businesses and organizations that use  
the Microsoft 365 suite. It requires a separate license (Copilot for M365).

*   **Purpose:** It is integrated directly into the applications you already know.
    In **Word**, it writes a document draft; in **Excel**, it analyzes spreadsheets;
    in **Outlook**, it summarizes long email threads; and in **Teams**, it creates
    meeting minutes.

*   **Copilot Pages** – a new concept (2025) of a shared "infinite canvas,"
    where you can create content with Copilot and colleagues in real time.

*   **Copilot Agents** – in selected M365 applications, you can create your own
    AI agents that automate repetitive tasks (e.g., "Process all incoming invoices
    and save them to SharePoint").

*   **Data context:** This is the key difference.
    This Copilot "sees" your company data (emails, files on OneDrive, calendar,
    Teams meetings, SharePoint sites). Therefore, it is strictly secured and
    complies with company data protection policies and adheres to the **Microsoft
    365 boundary** – your company data never leaves your organization.

### 3. GitHub Copilot (Assistant for Programmers)
A tool specifically designed for software developers.  
It is owned by Microsoft (via GitHub), but operates independently from office  
suites. Since its launch in 2021, it has undergone massive development – from a  
simple autocomplete tool to a full-fledged AI programming assistant.

#### 🔧 Operating modes

GitHub Copilot today offers several modes that complement each other:

| Mode | Description |
| :--- | :--- |
| **Code completion** | Inline code suggestions while typing – the original and fastest function |
| **Copilot Chat** | Conversation with AI directly in the editor – ask about code, explanations, refactoring |
| **Agent Mode** | Copilot independently executes commands, edits multiple files, runs the terminal |
| **Edit Mode** | Select a block of code and say what you want changed – Copilot applies edits directly |
| **Code Review** | Automatic code review for Pull Requests on GitHub.com |
| **Copilot in the CLI** | Assistant directly in the command line – explains and fixes commands |
| **Batch Processing** | Mass processing of multiple files at once |

#### 🤖 Agent Mode (the most significant new feature)

Agent Mode is a mode in which Copilot **autonomously performs tasks** – it does  
not just recommend code, but also:
* Creates and edits files
* Runs commands in the terminal
* Installs packages
* Searches for and fixes bugs
* Decides for itself which tools to use

> 💡 **Example:** Say "Create a REST API server with Express and connect to PostgreSQL"
> and Copilot will create the files, install dependencies, and explain the structure itself.

#### 🧩 Copilot Extensions

GitHub Copilot is extensible via **Copilot Extensions** – third parties (or you  
yourselves) can add custom tools and APIs:

* **Database connections** – query the schema directly from the chat
* **Integration with cloud services** – manage Azure, AWS, GCP
* **Enterprise APIs** – connection to internal microservices and documentation
* **Custom skills** – define specific commands for your project

#### 📝 Custom Instructions

Teams can define their own instructions for Copilot in the file  
`.github/copilot-instructions.md` in the repository:

```markdown
## Project rules

- We use TypeScript, not JavaScript
- We write tests in Vitest
- Architecture: Feature-Sliced Design
- Commit messages according to Conventional Commits
- Every new feature must have unit tests
```

Copilot automatically respects these rules in all suggestions and in the chat.

#### 🎯 Model selection

GitHub Copilot is not tied to a single model. In the settings (or via the  
editor), you can choose which model Copilot should use:

| Model | Suitable for |
| :--- | :--- |
| **GPT-5 / GPT-5.4** | general tasks, explanations, documentation |
| **Claude 4.6 Sonnet** | coding, debugging, refactoring |
| **Gemini 3.1 Pro** | analysis, comparisons, multi-file edits |
| **DeepSeek V4 Flash** | fast responses, simpler tasks |

> 💡 Copilot automatically selects the optimal model according to the task – you
> do not need to worry about it, but you can always switch the model manually.

#### 🛠️ Supported editors

* **VS Code** – full functionality including Agent Mode
* **Visual Studio** – complete integration
* **JetBrains IDE** (IntelliJ, PyCharm, WebStorm...) – Chat and Completion
* **GitHub.com** – Code Review, Copilot Chat in the web interface
* **Terminal** – Copilot in the CLI (gh copilot)

#### 🔒 Data context

* Learns from public repositories on GitHub
* Works with the context of your current project
* Open files serve as context for suggestions
* Copilot Chat takes into account the entire workspace, not just the current file
* Enterprise customers are guaranteed that their code **is not used for model training**

### 4. Copilot in Windows (Part of the operating system)
This tool is deeply integrated directly into the Windows 11 operating system.

*   **Purpose:** Helps change system settings (e.g., "turn on dark mode"),
    takes screenshots, or summarizes the content of open windows.
*   **Data context:** It has access to the context of your desktop and open
    applications so it can respond to what you are currently doing on your PC.

### 5. Copilot Studio (Creator of custom agents)
A low-code platform for more advanced users and businesses that are not  
satisfied with the standard Copilot. It allows the creation of **autonomous AI  
agents** without the need for programming.

*   **Purpose:**
    * Creating an agent that answers customer questions on a website
    * Automating approval processes (requests, invoices, HR)
    * Connecting with external systems (SAP, Salesforce, ServiceNow)
    * Custom Copilot extensions for M365
*   **Data context:** You define it yourself – you can connect:
    * Internal databases and APIs
    * SharePoint, OneDrive, Dataverse
    * External sources (web, REST API, SQL)
    * Custom knowledge bases (PDF, Word, web scraping)

### 6. Copilot for Security (Security Analyst)
A specialized tool for cybersecurity teams (SOC – Security Operations Center).

*   **Purpose:**
    * Analyzes security incidents in natural language
    * Creates threat reports and summaries
    * Assists with malware reverse engineering
    * Generates KQL (Kusto Query Language) queries for Microsoft Sentinel
    * Automates incident responses
*   **Data context:** Works with security logs and data from the company's
    protection systems (Microsoft Sentinel, Defender XDR, Intune, Purview).

### 7. Microsoft 365 Copilot Chat (Enterprise Chat)

This is the successor to the original **Bing Chat Enterprise**. It is a chat  
assistant with enterprise data protection that does not require a full Copilot  
for M365 license.

*   **Purpose:** Secure AI chat for businesses where data does not leave the
    organization
*   **Availability:** Part of selected M365 plans (E3, E5, Business Premium)
*   **Limitations:** It does not have direct integration into Office applications
    (Word, Excel) – it is a standalone chat tool

## Key differences: Why does this matter?

Why do we need to distinguish between these versions?  
The main reason is **data and context**.

1.  **Privacy:** Regular Copilot (web) should not use your company secrets for
    training.
    Copilot for M365 guarantees that your company data remains inside the company
    and adheres to the so-called **data boundary**.
2.  **Capabilities:** Copilot in Word cannot write code as well as GitHub Copilot.
    GitHub Copilot, on the other hand, cannot summarize your email in Outlook.
    Each tool is optimized for a different domain.
3.  **Price:** While the basic Copilot is often free, enterprise versions
    (M365, Security, Studio) require specific licenses from $30/month.
4.  **Models:** Different Copilots may use different AI models –
    GitHub Copilot offers a selection (GPT, Claude, Gemini), Copilot for M365 uses
    primarily GPT-5, Copilot in Windows combines multiple models according to the task.
5.  **Agent capabilities:** GitHub Copilot (Agent Mode) and Copilot Studio support
    autonomous task execution. Regular Copilot is more reactive – it answers,
    it does not act independently.

## Chapter summary

*   **Copilot** is not one product, but an entire family of artificial intelligence
    tools from Microsoft with more than 10 different variants.
*   **General Copilot** serves for common questions and content creation from
    public sources.
*   **Copilot for Microsoft 365** works with your private documents and emails.
*   **Microsoft 365 Copilot Chat** is a secure enterprise chat with data protection.
*   **GitHub Copilot** has evolved from autocomplete to a full-fledged agent mode –
    today it can autonomously create files, run commands, and fix bugs.
*   **Copilot Studio** allows building custom AI agents without programming.
*   **Copilot Pages** is a new concept of a shared canvas between people and AI.
*   Always be aware of **what data** the given Copilot works with to prevent
    information leakage.
*   **Model selection** – different Copilots use different AI models (GPT-5,
    Claude, Gemini, DeepSeek) according to the task type.

## Questions & discussion
