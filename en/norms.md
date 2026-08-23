# Standards and regulations for AI: GDPR, HIPAA, and others

Legal framework for the development, deployment, and use of AI systems

## Why are regulations important for AI?

AI systems often process large amounts of data, including personal and sensitive
information. Without appropriate rules, the following risks arise:

- **Privacy violations**: Unauthorized collection and use of personal data
- **Discrimination**: Algorithms can amplify biases present in the data
- **Insufficient transparency**: AI "black boxes" make explainability difficult
- **Security threats**: Data leaks, model manipulation, adversarial attacks

> 💡 **Key principle:** *Regulations are not an obstacle to innovation, but a
> framework for responsible and sustainable AI development that protects the
> rights of both individuals and society.*

## General Data Protection Regulation (GDPR) – EU

### Basic information

- **Effective**: Since May 2018 throughout the European Union
- **Goal**: To harmonize personal data protection and strengthen citizens' rights
- **Scope**: Applies to all organizations processing data of EU citizens,
regardless of their location

#### Key principles relevant to AI

| Principle | Significance for AI development |
|-----------|--------------------------------|
| **Lawfulness, fairness, transparency** | AI systems must have a legal basis for processing and be explainable to users |
| **Data minimization** | Collect only data necessary for the specific purpose of the AI model |
| **Accuracy** | Ensure data quality and regular model updates |
| **Storage limitation** | Set time limits for storing training and operational data |
| **Integrity and confidentiality** | Implement encryption, anonymization, and access controls |

### Individual rights with impact on AI

- **Right to information**: Users must know they are interacting with AI and how
  their data is being processed
- **Right of access and portability**: Ability to obtain a copy of their data in
  a structured format
- **Right to rectification and erasure ("right to be forgotten")**: Ability to
  request correction or deletion of data – a challenge for trained models
- **Right to object to automated decision-making**: Citizens can request human
  oversight for decisions with legal or significant impact

> 🎓 **Practical tip:** When developing AI for the EU market, always conduct a
> "Data Protection Impact Assessment" (DPIA).

## HIPAA – Health data protection in the USA

### Basic information

- **Full name**: Health Insurance Portability and Accountability Act (1996)
- **Goal**: To protect the confidentiality and security of patients' health
  information
- **Scope**: Applies to "covered entities" (healthcare providers, insurers) and
their "business associates" (including AI vendors)

### What are "Protected Health Information" (PHI)?

> 🎓 **Definition:** PHI is any individually identifiable health information,
> including: names, dates, insurance numbers, diagnostic codes, images, genetic
> data, and 14 other identifiers.

### Key requirements for AI in healthcare

| Requirement | Application in AI context |
|-------------|---------------------------|
| **Administrative safeguards** | Staff training, data access policies, contracts with AI solution vendors |
| **Physical safeguards** | Secure server locations, access control to data centers |
| **Technical safeguards** | Encryption of data at rest and in transit, audit logs, authentication, automatic logout |
| **Anonymization / De-identification** | Removal of 14 HIPAA identifiers before using data for AI training |

> ⚠️ **Caution:** Even "anonymized" data can be re-identified using AI
> techniques – caution and expert assessment are required.

#### Consequences of non-compliance
- Fines of up to **$1.5 million per year** for each type of violation
- Criminal liability in cases of intentional misuse
- Reputational damage and loss of patient trust

> 💡 **For students:** If you are developing AI for healthcare, always
> collaborate with a legal expert and compliance officer from the early stages
> of the project.

## Other important regulations and initiatives

### AI Act (EU) – The first comprehensive legal framework for AI

- **Status**: Approved in 2024, gradually coming into effect
- **Risk-based approach**:

| Risk category | Examples | Requirements |
|---------------|----------|--------------|
| **Unacceptable risk** | Social scoring, manipulative AI | Prohibited |
| **High risk** | AI in healthcare, transport, recruitment | Mandatory assessment, documentation, human oversight, high accuracy |
| **Limited risk** | Chatbots, deepfakes | Transparency obligation (marking AI-generated content) |
| **Minimal risk** | Spam filters, video games | No additional obligations |

### Sectoral regulations

- **Finance**: MiFID II directive, algorithmic trading regulations – requirements
  for testing, monitoring, and explainability of AI models
- **Transport**: Standards for autonomous vehicles (e.g., ISO 21448 SOTIF) – AI
  safety in the real world
- **Education**: Student data protection (e.g., FERPA in the US) when using AI
  tutors and analytical tools

### International initiatives and standards

- **OECD AI Principles**: International principles for trustworthy AI
- **ISO/IEC 23894**: AI systems risk management
- **NIST AI Risk Management Framework** (USA): Voluntary framework for
identifying and mitigating AI risks

> 🎯 **For students:** Regulations evolve rapidly. Follow official sources
> (European Commission, national data protection authorities) and engage in
> consultations on new proposals.

## Case Study: GDPR and a chatbot in an e-shop

### Scenario

An e-shop in the EU deploys an AI chatbot for customer support, which processes:
- Names and contact details
- Order history
- Preferences and on-site behavior

### Compliance steps

1. **Legal basis**: Contractual relationship (order fulfillment) + legitimate
interest (service improvement) – a record in the Register of Processing
Activities is required
2. **Transparency**: Info banner "This chat uses AI" + link to the privacy policy
3. **Minimization**: The chatbot does not store entire conversations for more
than 30 days, anonymizes logs after 90 days
4. **User rights**: "Export my data" and "Delete history" buttons in account
settings
5. **Security**: Conversation encryption, access only for authorized personnel,
regular penetration tests

> 🤔 **Discussion question:** How would you design the chatbot's architecture to
> enable the "right to be forgotten" without needing to retrain the entire model?

## The future of AI regulation

### Trends to watch

- **Global convergence**: Efforts to harmonize rules between the EU, USA,
Asia – a challenge for international AI projects
- **Regulation of generative AI**: Specific rules for LLMs, deepfakes,
copyright for training data
- **AI certification and audit**: Independent compliance verification similar
to financial audits
- **Liability for damages**: Legal frameworks for determining responsibility in
autonomous system failures

### The role of developers and researchers

> 🎓 **Responsible AI development is not just about complying with laws – it is
> about building trust.** Your role as future professionals:
> - Design systems that respect human dignity and autonomy
> - Actively communicate AI limitations and risks to users
> - Collaborate with legal experts, ethics committees, and the public

> 💡 **Conclusion:** Regulations like GDPR and HIPAA are not a "brake" on
> innovation, but a compass that helps navigate AI development toward
> technologies that serve people – safely, fairly, and transparently.

## Summary

- GDPR and HIPAA set key data protection requirements for AI systems
- Principles such as data minimization, transparency, and human oversight are
  universally good practices
- The AI Act introduces a risk-based approach – higher risk = stricter
  requirements
- Compliance is not a one-time task but an ongoing process throughout the AI
  lifecycle
- The future of regulation will be influenced by global cooperation and the
  development of generative AI

## Additional resources and exercises

### 📚 Official documents and guides
- [GDPR Text](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32016R0679) –
full text of the regulation
- [HHS HIPAA Summary](https://www.hhs.gov/hipaa/for-professionals/privacy/laws-regulations/index.html) –
overview for developers
- [EU AI Act](https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai) –
official materials on the new framework
- [NIST AI RMF](https://www.nist.gov/itl/ai-risk-management-framework) – practical
framework for risk management

> 🌟 **Final tip:** When working with real data, always assume it is subject to
> protection – implement safeguards preventively rather than addressing a breach
> retroactively. Responsibility is part of professionalism.

## Questions & discussion
