# EXP 5: COMPARATIVE ANALYSIS OF DIFFERENT TYPES OF PROMPTING PATTERNS AND EXPLAIN WITH VARIOUS TEST SCENARIOS

# Name : H GANANANTH
# Register No : 212225230070
# Date : 07.05.2026

# Aim: To test and compare how different pattern models respond to various prompts (broad or unstructured) versus basic prompts (clearer and more refined) across multiple scenarios.  Analyze the quality, accuracy, and depth of the generated responses 


# OUTPUT

1. Introduction

Prompt engineering is the discipline of crafting inputs to AI language models in ways that reliably
elicit the most accurate, useful, and contextually appropriate outputs. Among the many techniques
that have emerged in this field, three stand out as foundational strategies that every practitioner must
master: Zero-Shot Prompting, Few-Shot Prompting, and Chain-of-Thought (CoT) Prompting.
This report provides a systematic comparative analysis of these three prompting strategies across a
range of test scenarios — from broad and unstructured prompts to highly refined and specific ones.
The experiments were conducted across three leading AI language models: ChatGPT (by OpenAI),
Gemini (by Google), and Claude (by Anthropic).
Each prompting technique is tested with two versions of a prompt: a broad, loosely defined version
and a refined, structured version. This dual approach allows us to measure not just how each
technique performs at its best, but how much the quality of the prompt itself determines the quality of
the output.

2. Background and Motivation

The rapid adoption of large language models (LLMs) in professional, academic, and creative
contexts has highlighted a critical insight: the model is only one variable in the quality equation. The
structure, specificity, and style of the prompt is equally determinative of output quality.
Early approaches to AI prompting treated the model as an oracle: ask a question, receive an answer.
But as models have grown more capable, so too has our understanding of how to unlock their
potential through deliberate prompt design. Three paradigms have emerged as the most widely
studied and practically useful:
• Zero-Shot Prompting — asking the model to perform a task with no examples.
• Few-Shot Prompting — providing a small number of examples before the task.
• Chain-of-Thought Prompting — instructing the model to reason step-by-step before
answering.
This report uses a structured test scenario approach to compare all three, with each technique
applied to both a broad (unrefined) prompt and a refined prompt, across three AI models.

3. Overview of the Three Prompting Techniques
   
The diagram below summarises the three techniques, their key characteristics, and their respective
strengths:

<img width="1327" height="552" alt="image" src="https://github.com/user-attachments/assets/8cc82bf7-6486-4e3a-bc82-619ba218c5e9" />

3.1 Zero-Shot Prompting
Zero-Shot Prompting is the baseline approach: the model is given a task description with no
examples. It relies entirely on the model's pre-trained knowledge and its ability to infer the expected
format and content from the instruction alone.
Example: "Classify the sentiment of the following sentence as Positive, Negative, or Neutral: 'The
product exceeded all my expectations.'"
Zero-shot prompting is powerful when the task is clearly described and falls within the model's
training distribution. It is the most efficient technique but also the most sensitive to prompt wording.
Ambiguous or broad zero-shot prompts frequently yield generic or misaligned outputs.

3.2 Few-Shot Prompting
Few-Shot Prompting provides the model with a small number of input-output examples (typically 2–8)
before the actual task. This in-context learning approach allows the model to infer the expected
format, tone, level of detail, and reasoning style from the demonstrations.
Example: "Input: 'I love this!' Output: Positive. Input: 'Terrible experience.' Output: Negative. Now
classify: 'It was okay, I suppose.'"
Few-shot prompting dramatically improves consistency and format adherence. It is particularly
effective for tasks with idiosyncratic output formats — such as structured data extraction, specific
writing styles, or constrained categorisation.

3.3 Chain-of-Thought (CoT) Prompting
Chain-of-Thought Prompting instructs the model to show its reasoning process before delivering a
final answer. This technique dramatically improves performance on tasks requiring multi-step
reasoning, arithmetic, logic, and commonsense inference.
Example: "Solve this step by step: A train travels 60 miles in 45 minutes. A car travels 80 miles in an
hour. Which is faster? Show your working."
CoT prompting works because it forces the model to externalise its reasoning chain, allowing it to
catch errors that would otherwise propagate silently to the final answer. It is particularly valuable for
complex reasoning tasks.

4. Test Scenario Design
To ensure rigorous and comparable testing, five scenarios were selected that vary in their knowledge
type, reasoning complexity, and output format requirements. For each scenario, a broad prompt and
a refined prompt were designed and submitted to all three AI models.
<img width="1016" height="558" alt="image" src="https://github.com/user-attachments/assets/2c75b588-e4e5-4057-adfa-36099543e4a3" />


5. Scenario 1 — Medical Symptom Triage

5.1 Broad Prompt (Zero-Shot)
"What should I do if I have a headache?"
All three models responded to this zero-shot broad prompt with generic, conservative advice: rest,
hydration, over-the-counter pain relief, and a recommendation to see a doctor if symptoms persist.
The outputs were safe and factually correct but undifferentiated — identical advice regardless of
severity, age, or context.
Without context, the model must default to the most general possible answer. This is appropriate for
safety-critical domains but unhelpful for anyone seeking nuanced guidance.

5.2 Refined Prompt (Few-Shot)
"Here are two examples: [Example 1: mild tension headache → rest, hydration, ibuprofen. Example
2: sudden severe headache with vision changes → immediate emergency care]. Now triage: adult,
35 years, sudden onset headache rated 8/10, neck stiffness, light sensitivity, no prior migraine
history."
With few-shot examples in place, the models immediately sharpened their outputs. ChatGPT
correctly identified the symptom cluster as a potential medical emergency (meningitis red flags) and
recommended urgent hospital assessment. Claude similarly flagged the clinical urgency while
providing a clear ranked list of red-flag symptoms. Gemini produced an accurate triage but organised
its output less clearly.

5.3 Chain-of-Thought Prompt
"Reason through this step by step: (1) What are the possible diagnoses? (2) What is the most
serious possibility? (3) What is the recommended course of action?"
The CoT prompt produced the most clinically rigorous responses. By requiring the model to reason
through differential diagnosis explicitly, it surfaced considerations — thunderclap headache
characteristics, nuchal rigidity significance — that did not appear in the zero-shot or few-shot outputs.
All three models correctly identified subarachnoid haemorrhage and bacterial meningitis as the
highest-priority differentials.

6. Scenario 2 — Logical Puzzle Solving

6.1 Broad Prompt (Zero-Shot)
"If all Bloops are Razzies and all Razzies are Lazzies, are all Bloops definitely Lazzies?"
This classic transitive syllogism is a standard test of deductive reasoning. Zero-shot, all three models
answered correctly (yes, by transitivity). The quality of explanation varied dramatically — Claude's
response was the most pedagogically clear, showing the chain of inference explicitly.

6.2 Refined Prompt (Few-Shot)
"[Example 1: All mammals are warm-blooded. All dogs are mammals. Therefore all dogs are warmblooded.
✓ Valid] [Example 2: All fish live in water. This animal lives in water. Therefore it is a fish. ✗
Invalid]. Now evaluate: All Bloops are Razzies. All Razzies are Lazzies. Are all Bloops Lazzies?"
The few-shot examples did not change the correctness but meaningfully improved justification
quality. All three models now explicitly labelled the argument as valid, named the logical form
(hypothetical syllogism), and distinguished it from the invalid form shown in Example 2.

6.3 Chain-of-Thought Prompt
"Solve step by step: Identify each premise. Check whether the conclusion follows necessarily. State
assumptions. Determine if the argument is valid or invalid, and explain why."
The CoT approach produced the most thorough analysis, including a formal representation of the
syllogism, a step-by-step validity check, and a note on the distinction between validity and
soundness. Only Claude's CoT response spontaneously included this additional logical distinction.


7. Scenario 3 — Creative Story Generation

7.1 Broad Prompt (Zero-Shot)
"Write a short story about a robot."
The most open-ended prompt in the experiment. The zero-shot outputs across all three models were
competent but formulaic: each produced a variation on the 'robot discovers feelings' narrative with
similar plot beats. The outputs were well-written but indistinguishable in concept — illustrating how
broad prompts push models toward the most statistically common narrative pattern.

7.2 Refined Prompt (Few-Shot)
"[Style A: documentary tone] [Style B: emotional irony]. Write a 200-word story about a robot archivist
on a dying space station. Match the tone of Style B."
The few-shot style examples immediately differentiated the outputs. All three models adopted the
ironic, emotionally resonant register of Style B, producing stories with significantly more originality
than the zero-shot outputs. This demonstrates few-shot prompting's power for creative tasks —
showing rather than describing the expected output.

7.3 Chain-of-Thought Prompt
"Before writing, plan: (1) What is the robot's core desire? (2) What is the central conflict? (3) What is
the emotional arc? (4) What is the final image? Then write a 200-word story about a robot archivist
on a dying space station."
The CoT approach produced the most structurally coherent stories by preventing strong openings
that trail off into unsatisfying endings. However, it produced slightly less spontaneous prose.
Claude's CoT output found the best balance between structural integrity and prose quality.

8. Scenario 4 — Code Debugging

8.1 Broad Prompt (Zero-Shot)
"Fix this Python code: def add_numbers(a, b): return a - b"
A deliberately simple debugging task. All three models identified the bug instantly (subtraction
operator instead of addition) and provided the correct fix. Zero-shot performed perfectly here
because the task is unambiguous, the error is obvious, and the expected output is well-defined.
Simple, well-scoped debugging is an ideal zero-shot use case.

8.2 Refined Prompt (Few-Shot)
"[Example: Buggy → Issue → Fixed → Explanation format shown]. Now debug and explain: def
calculate_average(numbers): return sum(numbers) / len(numbers) — Error: ZeroDivisionError on
empty list."
The few-shot example established the expected three-part structure. Beyond the fix (adding a guard
for empty lists), Gemini also suggested returning None vs 0 as a design decision — demonstrating
that few-shot context can elevate the discussion beyond the literal task.

8.3 Chain-of-Thought Prompt
"Debug this step by step: (1) What does the function do? (2) Under what conditions does the error
occur? (3) Root cause? (4) Corrected code? (5) Edge cases to test?"
The CoT prompt produced the most comprehensive analysis. Claude's CoT output was particularly
strong — distinguishing between returning 0 (mathematically defensible) and raising a ValueError
(appropriate when empty input is programmer error), going beyond fixing the bug to improving overall
code robustness.


9. Scenario 5 — Ethical Dilemma Analysis

9.1 Broad Prompt (Zero-Shot)

"Is it ever right to lie?"
This classic ethical question received the most varied zero-shot responses. ChatGPT produced a
balanced 'it depends' response. Gemini offered a structured overview of deontological vs
consequentialist frameworks. Claude produced the most nuanced response, acknowledging the
tension between competing frameworks and declining to endorse a single universal answer —
consistent with its Constitutional AI approach.

9.2 Refined Prompt (Few-Shot)

"[Example: ethical dilemma analysed through Utilitarian, Deontological, and Virtue Ethics lenses].
Now analyse: Is it ever right to lie? Apply all three frameworks."
Few-shot examples radically structured the outputs. All three models now applied all three
frameworks consistently, producing a genuinely comparative ethical analysis. Gemini's output was
strongest here — its structured analytical approach aligned well with the framework-by-framework
template.

9.3 Chain-of-Thought Prompt

"Reason step by step: (1) Identify the ethical tension. (2) Apply utilitarian reasoning. (3) Apply Kant's
categorical imperative. (4) Apply virtue ethics. (5) Consider the Nazi officer case. (6) State your
reasoned conclusion and its conditions."
The CoT prompt produced the most intellectually rigorous analyses. Claude's output was exceptional
— explicitly distinguishing between lying and deception, considering whether the duty not to lie can
be overridden by a stronger duty to protect innocent life, and concluding with a carefully conditioned
answer that acknowledged each framework's limits.
<img width="832" height="810" alt="image" src="https://github.com/user-attachments/assets/43d6173d-340d-4031-8ee9-94743bca8a73" />

<img width="829" height="891" alt="image" src="https://github.com/user-attachments/assets/eabedda3-5ff9-42c6-ac58-b8759f02be5d" />

12. Key Findings and Lessons

Finding 1: Prompt Refinement Is the Highest-Leverage Action
Across all techniques and models, refining a broad prompt into a structured one produced a larger
quality improvement than switching between techniques. The average score improvement from
broad to refined was +1.8 points (out of 10). The lesson: invest time in your prompt before you invest
time in your technique.

Finding 2: Chain-of-Thought Dominates Complex Reasoning Tasks
For tasks requiring multi-step reasoning — medical triage, logical puzzles, ethical analysis — Chainof-
Thought prompting consistently outperformed zero-shot and few-shot approaches, often by 2–3
points. This advantage was most pronounced when the CoT prompt included specific reasoning
instructions rather than generic 'think carefully' guidance.

Finding 3: Few-Shot Excels for Style and Format Transfer
For creative and format-sensitive tasks — story generation, structured debugging, framework-based
analysis — few-shot prompting was the most effective technique. The ability to demonstrate rather
than describe the expected output is particularly powerful when format precision matters more than
reasoning depth.

Finding 4: Zero-Shot Remains Competitive for Well-Defined Tasks
For tasks that are well-defined, unambiguous, and within the model's training distribution (simple
code debugging, factual Q&A, clear logical puzzles), zero-shot prompting performs comparably to
more complex techniques.

Finding 5: Model Choice Matters Most for Edge Cases
On average tasks, all three models performed within 1 point of each other. The differences emerged
most sharply at the extremes. Claude's Constitutional AI training produced a measurable advantage
on tasks requiring ethical nuance and instruction adherence.


<img width="844" height="835" alt="image" src="https://github.com/user-attachments/assets/6b0e67bd-123c-48b5-b8c2-17b549c779f4" />


14. Conclusion
    
This comparative study demonstrates that the choice of prompting technique — and the quality of the
prompt itself — are the two most influential variables in AI output quality. No technique dominates
across all task types, but clear patterns emerge: Chain-of-Thought for reasoning, Few-Shot for style
and format, Zero-Shot for well-scoped factual tasks.
The gap between a broad, unrefined prompt and a carefully structured one — regardless of
technique — averaged 1.8 quality points across all scenarios and models. This is the single most
actionable insight: prompt refinement returns more value per unit of effort than any other intervention
available to the practitioner.
Model choice matters, but less than technique choice for most tasks. Claude leads on reasoning
depth and ethical nuance; ChatGPT leads on consistent general-purpose performance; Gemini leads
on technical precision and data density. Matching the model to the task, and the technique to the
task, is itself a learnable, transferable prompt engineering skill.
The practitioner who masters technique selection, prompt structure, and iterative refinement will
consistently outperform one who relies on intuition alone — regardless of which AI model they use.
# RESULT: The prompt for the above said problem executed successfully
