# Mathematics and LLMs – Capabilities, Limitations, and the Hybrid Approach

Large language models represent an excellent tool for working with mathematics,  
but their use has its limitations. They function more as **language experts in  
mathematics** than as calculators themselves. They excel at explaining complex  
concepts, solving word problems, and generating practice examples.

The main pitfall, however, remains the fact that LLMs are **probabilistic text  
generators**, not deterministic machines.  
They do not have a calculator's logic circuit built in; instead of computing,  
they try to predict the next most probable "token."  
This leads to so-called **mathematical hallucinations**, where the model  
confidently presents an incorrect result.  
Although new reasoning models mitigate these shortcomings thanks to an internal  
chain of thought, they are still not 100% reliable when it comes to pure  
arithmetic.

---

## Why an LLM is not a calculator

To understand why LLMs sometimes make mistakes with numbers, we must  
understand how they were trained.  
The model learned from a vast amount of text – books, articles, web  
pages.  
It learned patterns of language, including mathematical notation and  
derivations.  
**It never actually learned to calculate** in the sense that a processor does.

When you ask it *"What is 345 × 789?"*, the model does not perform  
multiplication.  
Instead, it taps into its "memory" of patterns and tries to guess  
what characters follow after such an expression.  
For small numbers that appeared frequently in the training texts,  
this works reliably.  
With larger numbers or multi-step calculations, however, errors occur.

> **Key difference:** A calculator *computes* the result deterministically.  
> An LLM *guesses* the result based on probability.  
> For most numbers, the estimate is correct – but not always.

---

## Mathematical hallucinations

The term **hallucination** in the context of AI refers to a situation where  
the model confidently asserts something false.  
In mathematics, this phenomenon is particularly troublesome because:

*   The model answers confidently, without any hint of doubt.
*   The result may look plausible – correct format, correct units,
    logically consistent context – but the number is simply wrong.
*   A reader without independent verification will not detect the error.

**Typical scenarios where hallucinations are likely:**

*   Multi-digit multiplication or division (e.g., 1.2 million × 9.8 million)
*   Compound percentage calculations with multiple steps
*   Numerical integrations and derivatives without symbolic recording
*   Unit conversions with unusual coefficients

---

## Reasoning models: improvement, not perfection

The new generation of **reasoning models** (OpenAI o1/o3, Claude Extended  
Thinking, DeepSeek Deep Think, QwQ) brings significant improvement.  
Before the final answer, these models perform a visible **chain of thought**  
– they break the problem into steps and solve them progressively.

Results on mathematical benchmarks are impressive:

| Benchmark | Standard LLM | Reasoning LLM |
| :--- | :---: | :---: |
| **GSM8K** (basic mathematics) | ~90% | ~97% |
| **MATH** (competition mathematics) | ~50–60% | ~70–85% |
| **AIME** (hard olympiad problems) | ~5–15% | ~50–70% |

Nevertheless, reasoning models **are not 100% reliable** when it comes to  
pure arithmetic.  
They can still make mistakes – especially in long calculations, where a  
small error in one step propagates to subsequent ones.

---

## Comparison table: LLM versus traditional tools

| Task | Standard LLM | Reasoning LLM | Calculator / Wolfram |
| :--- | :---: | :---: | :---: |
| Explaining a concept | Excellent | Excellent | None |
| Simple word problem | Good | Good (often better) | Poor |
| Computing 345 × 789 | Good (occasional errors) | Good | Perfect |
| Computing 1.2M × 9.8M | Unreliable | Good, not 100% | Perfect |
| Complex integral | Frequent errors | Good | Perfect |
| Proof of a new theorem | Useless | In research | Impossible |

---

## Where LLMs truly excel in mathematics

Despite the aforementioned limitations, there are areas where LLMs have  
no competition in mathematics education:

### 1. Explaining concepts

An LLM can explain the same mathematical concept in ten different  
ways – formally, intuitively, through analogy, through a story.  
No textbook or calculator can do this.

*Example:* "Explain to me what a derivative is, as if I were 12 years old."  
→ The model uses the analogy of a car's speed, the slope of a hill, and  
the intuition of instantaneous change. The result is more comprehensible  
than a textbook definition.

### 2. Solving word problems with step-by-step explanations

Word problems require translation from language into mathematical  
notation – precisely what LLMs excel at.  
The model recognizes what type of problem it is, chooses the correct  
procedure, and comments on each step in comprehensible language.

### 3. Generating practice problems

Need 20 exercises on quadratic equations with increasing difficulty?  
The LLM generates them in seconds, including solutions and methodological  
notes.

### 4. Checking and correcting one's own solution

You can show your solution to an LLM and ask for feedback.  
The model identifies an error in the procedure, not just in the numerical  
result – which is pedagogically much more valuable.

### 5. Translating mathematics into code

LLMs are great at translating mathematical formulas into programming  
languages (Python, NumPy, MATLAB).  
This significantly facilitates the work of analysts, scientists, and  
developers.

---

## Hybrid approach: the gold standard for mathematics

Currently, the **hybrid model** appears to be the most suitable approach  
to mathematics. The principle is simple:

> *LLM for thinking, specialized tool for computing.*

**Procedure in practice:**

1.  **LLM for understanding the task** – the model analyzes the problem,
    identifies key quantities, and proposes a solution procedure.
2.  **LLM for designing code or a formula** – the model writes a Python
    script or Wolfram expression that mathematically expresses the problem.
3.  **Specialized tool for computation** – Python, Wolfram Alpha,
    or a scientific calculator performs the computation itself deterministically.
4.  **LLM for interpreting the result** – the model explains what the number
    means in the context of the original assignment.

This approach combines the strengths of both worlds: the linguistic  
intelligence of LLMs and the mathematical precision of traditional tools.

---

## Practical recommendations

*   **For simple rough calculations** (estimates, "round" numbers,
    magnitude comparisons) – an LLM suffices; the result is generally correct.
*   **For calculations where every digit matters** – always verify the result
    with a calculator, Python, or Wolfram Alpha.
*   **For understanding a procedure or concept** – an LLM is an ideal first
    step, better than most textbooks.
*   **For creating practice materials** – LLMs significantly speed up the
    preparation and diversification of tasks.
*   **For research and new mathematical proofs** – reasoning models can
    assist, but results must always be verified by a human mathematician.

---

## Wolfram Alpha and Python: reliable partners for LLMs

The two most frequently recommended tools for computations in combination  
with LLMs:

**Wolfram Alpha** is a computational search engine that understands natural  
language and returns precise mathematical results – from integrals through  
statistics to physical constants.  
It is available for free at [wolframalpha.com](https://www.wolframalpha.com).

**Python** (with libraries such as `sympy`, `numpy`, or `scipy`) offers  
full programmatic control – symbolic mathematics, numerical computations,  
and visualizations.  
An LLM can write the relevant code; you then run the Python code and the  
result is deterministically correct.

> **Tip:** Many LLMs (ChatGPT, Claude, Gemini) have a Python interpreter  
> directly integrated – the model not only writes the code but also runs it  
> and verifies the result. This is the hybrid approach in its pure form.

---

## Chapter summary

*   LLMs are **probabilistic text generators** – they estimate, they do not
    compute. Mathematical hallucinations (confidently incorrect results) are a
    real risk.
*   **Reasoning models** (o1, Claude Extended Thinking, Deep Think) significantly
    improve performance in mathematics, but do not provide 100% reliability.
*   LLMs truly excel at **explaining concepts, solving word problems,
    generating exercises, and translating mathematics into code**.
*   The recommended approach is the **hybrid model**: LLM for understanding
    and designing the procedure, specialized tools (Wolfram Alpha, Python) for
    the computations themselves.
*   Rule of thumb: *if the accuracy of a number matters, verification is
    mandatory.*

## Questions & discussion
