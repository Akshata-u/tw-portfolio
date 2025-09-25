!!! example "About this article "
    This document is an excerpt from a specialized, targeted, 15-page _Prompting guide_ that I created as training collateral for a product webinar. The guide was shared with 1000+ external customers (mostly in senior management and CXO positions).

## Prompting Basics

### Purpose

We’ve introduced **AI Assistants** to help your teams uncover insights and take faster action across customer experience challenges. However, to get the most value from **AI Assistants**, the **quality of your prompt matters**. This guide will teach you how to move from _"getting answers"_ to _"getting the **right** answers"_ — the kind you can actually act on as a manager, leader, or CXO.

## Why prompts matter

Consider a prompt as the question you would ask a trusted analyst on your team. The clearer you are, the more actionable the answer becomes.

* A vague prompt: *“Tell me about customers.”* → Returns broad, generic results.  
* A focused prompt: *“What are the top 5 reasons customers called about billing errors in July?”* → Returns specific, usable insight.


## Quick start guide to prompting

Here are a few, easy-to-follow rules to write high-quality prompts.

1. Start with one clear, specific question.  
2. Add timeframe, product, or channel context.  
3. Use business-friendly action verbs (show, list, compare).  
4. Iterate until the answer feels usable. Don’t worry about always getting it right the first time.  
5. Remember: The AI Assistant is only as good as the data and the prompt!

---

---

## Best practices of prompt writing

| Tip | Why it Works | Example |
| ----- | ----- | ----- |
| **Be specific** | Helps the Assistant target relevant conversations and extract precise insights | *Top reasons for returns or cancellations in last 30 days* |
| **Add timelines** | Helps track trends and provides insights as per your time period of interest | Instead of *Payment issues* Ask→  *Payment issues in the last 7 days* |
| **Use metadata field names** | Increases accuracy by anchoring to structured fields (like agent name, team, campaign, product)  | Instead of  *Top issues  with Northeast growth and Acme 45* Ask → *Top issues  with campaign = Northeast growth and Team = Acme 45* |
| **Break down big asks**  | Avoids vague outputs and enables deeper multi-step investigation | Instead of *Tell me everything about sales* Ask → *What are the top objections raised in sales calls* |

---

---

## Prompt templates

Use these *plug-and-play* templates to get started:

* **Trend Analysis (VOC Assistant)**  
   *“What are the top \[X\] reasons customers contacted support about \[topic\] in \[timeframe\]?”*

* **Performance Insight (Search Assistant):**  
   *“Show me conversations where customers complained about \[specific pain point\].”*

* **Resolution Focus**  
   *“Which issues are most associated with \[low resolution rates / repeat calls / escalations\]?”*

* **Sentiment Tracking**  
   *“What are the top drivers of negative sentiment in \[month/quarter\]?”*

* **Agent Behavior**  
   *“Provide transcripts where agents successfully handled \[objection / escalation\].”*

---

---

## Limitations

**► Data Boundaries:** **AI Assistants** only analyze conversations and metadata available in your **Zumo AI** instance. If the data isn’t captured, the Assistant can’t report on it.

**► Prompt Scope:** Broad prompts may return generalized patterns instead of specific insights.

**► Iteration is Key:** Your second or third attempt at phrasing may unlock the real insight.

**► Responses reflect patterns, not guarantees.** Use **AI Assistant** responses for decision support, not absolute truth.

---


---

## Troubleshooting your prompts {#troubleshooting-your-prompts}

| Problem | Likely Cause | How to Fix It |
| ----- | ----- | ----- |
| **Answer feels too generic** | Prompt was too broad or vague | Add timeframe, product, issue type, or metric. |
| **No clear answer returned** | Data doesn’t exist or prompt too vague | Check if the data exists by asking *“What metadata fields do you have available to analyze?”*. Rephrase your subsequent prompts accordingly **or** check the ‘Thought Process’ |
| **Output not in desired format** | Response style is not specified | Add *“Format the response as a table/concise summary/professional report”* |
| **Insight feels disconnected from action** | No action items requested in the prompt | Re-prompt with *“…and suggest 2 actions managers can take.”* |

---