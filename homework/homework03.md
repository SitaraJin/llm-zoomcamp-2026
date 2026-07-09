## Homework: AI Orchestration with Kestra

## Prerequisites

Before starting this homework, ensure you have:

1. Completed the [Module 3 lessons](../../../03-orchestration/README.md) — the questions reference flows and concepts covered there
2. Kestra running locally with API keys configured (see the [Setup](../../../03-orchestration/lessons/03-setup.md) lesson) -- this includes the Gemini API key, which is also required for the AI Copilot
3. Imported all flows from the `03-orchestration/flows/` directory (covered in the Setup lesson)

## Question 1: Context Engineering

Try the following experiment:

1. Open ChatGPT in a private browser window: https://chatgpt.com
2. Enter this prompt: "Create a Kestra flow that loads NYC taxi data from CSV to BigQuery"
3. Then, use Kestra's AI Copilot with the same prompt

After trying the same prompt in ChatGPT vs Kestra's AI Copilot, what is the primary reason AI Copilot generates better Kestra flows?

- AI Copilot uses a more powerful model
- <mark>AI Copilot has access to current Kestra plugin documentation</mark>
- AI Copilot uses more tokens
- AI Copilot has internet access

## Question 2: RAG vs No RAG

Run both `1_chat_without_rag.yaml` and `2_chat_with_rag.yaml` in the Kestra UI. Read the execution logs for each.

The non-RAG response about Kestra 1.1 features is best described as:

- Accurate and specific, matching the actual release notes
- <mark>Vague, generic, or fabricated — the model guesses from training data</mark>
- Empty — the model refuses to answer without context
- Identical to the RAG version

## Question 3: Token usage — short summary

Run `4_simple_agent.yaml` with `summary_length = short` (leave the other inputs as defaults).

Open the execution logs and find the token usage logged by the `log_token_usage` task.

What is the approximate **output** token count for `multilingual_agent`?

- 5-15 tokens
- <mark>60-100 tokens</mark>
- 200-400 tokens
- 500+ tokens

Multilingual Agent:

- Input tokens: 282
- Output tokens: 93
- Total tokens: 375

English Brevity Agent:

- Input tokens: 108
- Output tokens: 50
- Total tokens: 158

💡 Tip: Monitor token usage to understand costs and optimize prompts!

## Question 4: Token usage — long summary

Run `4_simple_agent.yaml` again with `summary_length = long`.

Compare the `multilingual_agent` output token count to your result from Question 3. Roughly how many times more output tokens does the long summary use?

- About the same (within 20%)
- <mark>2-5x more</mark>
- 10-20x more
- 50x more

INFO 2026-07-09T15:52:40.097470Z 📊 Token Usage Summary:

Multilingual Agent:

- Input tokens: 282
- Output tokens: 178
- Total tokens: 460

English Brevity Agent:

- Input tokens: 193
- Output tokens: 46
- Total tokens: 239

💡 Tip: Monitor token usage to understand costs and optimize prompts!

## Question 5: Modifying a flow

Open `4_simple_agent.yaml` in the Kestra flow editor. Find the `english_brevity` task and change its prompt from asking for exactly **1 sentence** to asking for exactly **3 sentences**.

Save the flow, then run it with `summary_length = long`.

Compare the `english_brevity` output token count to the original 1-sentence version (also with `summary_length = long`). How do they compare?

- About the same (within 20%)
- <mark>2-4x more</mark>
- 5-10x more
- 10x+ more

INFO 2026-07-09T15:55:14.857714Z 📊 Token Usage Summary:

Multilingual Agent:

- Input tokens: 282
- Output tokens: 178
- Total tokens: 460

English Brevity Agent:

- Input tokens: 193
- Output tokens: 97
- Total tokens: 290

💡 Tip: Monitor token usage to understand costs and optimize prompts!

## Question 6: Best Practices

Based on what you learned in this module, for production workflows requiring deterministic, repeatable results with strict compliance requirements (e.g., financial reporting, workflows in highly regulated industries), which approach is most appropriate?

- Always use AI agents for maximum flexibility and adaptation
- <mark>Use traditional task-based workflows for predictability and auditability</mark>
- Use only RAG without agents for better performance
- Use web search tools exclusively to ensure current data

## ## Submitting the Solutions

* Form for submitting: https://courses.datatalks.club/llm-zoomcamp-2026/homework/hw3
* Check the link above to see the due date
