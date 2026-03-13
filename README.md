# Agent UX and Interaction
**Session Time:** 120 minutes  
**Format:** Instructor-Led  

---

## Prerequisites

- Completion of Sessions 1–11  
- Understanding of how system prompts define agent behavior and communication tone (Session 6)  
- Familiarity with human-in-the-loop patterns and escalation points (Session 7)  
- Understanding of automated workflow design and the agent's interaction with users (Session 11)  

---

## Learning Objectives

By the end of this session, students will be able to:

1. **Design** conversational interfaces that promote clear, efficient, and natural communication between users and agents.
2. **Test** agent interactions to ensure they are user-friendly, intuitive, and easy to navigate.
3. **Refine** agent prompts based on user feedback to improve user experience and satisfaction.

> Building an agent that works technically is only half the job. If users find it confusing, frustrating, or untrustworthy, they will stop using it — regardless of how well it performs under the hood. This session is about designing the experience of interacting with an agent, not just the logic behind it.

---

## Session Breakdown

| # | Segment | Duration |
|---|---------|----------|
| 1 | Designing for the User, Not the System | 20 min |
| 2 | Conversational Interface Patterns | 20 min |
| 3 | Testing and Refining Agent Interactions | 15 min |
| 4 | Break | 10 min |
| 5 | Lab | 60 min |
| 6 | Wrap-Up & Reflection | 5 min |
|   | **Total** | **120 min** |

---

## 1. Designing for the User, Not the System (20 min)

### The Gap Between "Works" and "Works Well"

An agent can execute every step of a workflow correctly and still fail completely — because the person using it couldn't understand what it was asking, didn't trust what it was saying, or gave up before the task was complete.

This gap between technical performance and user experience is one of the most underestimated problems in AI deployment. Teams spend weeks getting the logic right, then ship an interaction that confuses or alienates the people it was built for.

Agent UX is the discipline of closing that gap. It asks a different set of questions than the ones we've focused on so far:

<img width="935" height="256" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/d8d54c73-8481-430b-ac6c-44de807ab0f8" />


Both sets of questions matter. A technically correct agent with poor UX fails just as surely as a well-designed agent with broken tools.

---

### Three Foundational UX Principles for Agents

<img width="922" height="424" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/4d117862-7d7e-4df4-be3b-a6a125dac155" />


#### Principle 1: Clarity Over Cleverness

The agent's job is not to impress — it is to help. Every message the agent sends should have one purpose: moving the user one step closer to completing their task or understanding the outcome.

Agents that try to be too sophisticated — offering every possible option, explaining their full reasoning, using technical vocabulary — create cognitive load. Users have to work harder to extract the information they need.

```
❌ Clever but unclear:
"I've analyzed your request in the context of our current inventory 
management parameters and identified three potential resolution pathways 
that each carry different trade-off profiles across delivery speed, 
cost optimization, and customer satisfaction metrics."

✅ Clear and direct:
"I found three options for your order:
1. Standard shipping — arrives Friday, no extra cost
2. Express shipping — arrives tomorrow, +$12
3. Store pickup — available today, free

Which would you prefer?"
```

**The test:** after reading the agent's message, can the user immediately answer: *"What is this telling me?"* and *"What should I do next?"* If they have to re-read it to figure that out, it needs to be simpler.

#### Principle 2: Transparency Without Oversharing

Users need to understand what the agent is doing — but they don't need a running commentary on every step. The right level of transparency depends on the action being taken.

```
Low-stakes action (no explanation needed):
  Agent: "Here's your order status: shipped, arriving Thursday."

Medium-stakes action (brief explanation helpful):
  Agent: "I've updated your shipping address. Your confirmation email 
          will reflect the new address within a few minutes."

High-stakes action (full explanation required):
  Agent: "I'm about to process a refund of $340 to your original 
          payment method. This will take 3–5 business days to appear.
          
          Shall I go ahead?"
```

The rule of thumb: **the higher the stakes, the more the user needs to understand before the agent acts**. For actions that are irreversible or financially significant, transparency is not just good UX — it is a governance requirement.

#### Principle 3: The User Is Always in Control

An agent that makes users feel like passengers — watching decisions being made without their input — erodes trust, even when those decisions are correct. Users need to feel that they can redirect, correct, or stop the agent at any point.

This means:

- **Ask before acting on high-stakes tasks,** not after
- **Acknowledge when the user changes direction** rather than continuing the previous task
- **Make it easy to undo or escalate** — the user should always know how to reach a human if they want one
- **Don't assume** — when something is ambiguous, ask, don't guess

```
❌ Agent assumes and acts:
  User: "Can you reschedule my meeting?"
  Agent: [Cancels the meeting and books a new one for next week]
  
✅ Agent clarifies before acting:
  User: "Can you reschedule my meeting?"
  Agent: "I can do that. Which meeting are you referring to — 
          the 2 PM with the design team, or the 4 PM client call?
          And what date would work better for you?"
```

---

### Understanding Your User Before You Design

Before designing any agent interaction, answer three questions about the people who will use it:

**Who are they?**  
Not just their job title — their relationship with technology. Are they comfortable with chatbots? Do they expect formal or informal language? Are they using this on a phone, in a Slack channel, or in a dedicated web interface?

**What are they trying to accomplish?**  
Not what the agent is designed to do — what the *user* is actually trying to achieve. These are sometimes different. A user asking "where's my order?" might actually be trying to decide whether to cancel it. Understanding the underlying goal leads to better responses than addressing only the literal question.

**What do they already know?**  
About the topic, about the system, about the agent itself. An agent designed for experienced sales reps can use CRM terminology. An agent designed for retail customers must assume no technical knowledge whatsoever.

```
Same task, two very different users:

Internal tool for HR team:
  Agent: "No active HRIS record found for employee ID 4821. 
          Check the offboarding log or escalate to IT."

Customer-facing tool for employees:
  Agent: "It looks like we don't have your information on file yet. 
          This sometimes happens when accounts are being set up. 
          Can you give us a call at 0800-XXX-XXXX and we'll sort it out right away?"
```

---

## 2. Conversational Interface Patterns (20 min)

### Conversations Have Structure

Human conversations follow patterns — opening, establishing context, exchanging information, resolving, closing. Agent conversations work the same way, but the pattern needs to be designed deliberately, because the agent doesn't intuitively know how to navigate a conversation the way a person does.

Understanding and designing for common conversational patterns prevents the most frequent UX failures: agents that ask too many questions at once, agents that answer the wrong question, and agents that leave users unsure what to do next.

---

### Pattern 1: Progressive Disclosure

Don't give users everything at once. Lead with the most important information, then offer more detail if they want it.

```
❌ Information dump:
"Your order #48291 was placed on March 8th for a Sony WH-1000XM5 
headphone in black, size N/A, at a total of $349 including tax. 
It is currently in transit with carrier DHL, tracking number 
1Z999AA10123456784, last scanned at the São Paulo distribution 
center at 11:42 AM on March 11th, with an estimated delivery 
date of March 14th between 8 AM and 6 PM."

✅ Progressive disclosure:
"Your order is on its way — estimated delivery is Thursday, March 14th.

Want the tracking details or carrier information?"
```

Progressive disclosure reduces cognitive load, respects the user's time, and lets them ask for more only when they need it.

---

### Pattern 2: Clarify Before Acting, Not After

When a user's request is ambiguous, the worst response is to guess and act. The second worst is to ask too many clarifying questions at once. The best is to ask one targeted question that resolves the most critical ambiguity.

```
❌ Acts without clarifying:
  User: "Cancel my subscription."
  Agent: [Cancels immediately]
  User: "Wait, I meant the free trial, not my paid plan!"

❌ Asks too many questions:
  User: "Cancel my subscription."
  Agent: "Which subscription? When did you sign up? What's your 
          reason for canceling? Have you tried pausing instead? 
          Are you sure you want to cancel?"

✅ One targeted clarifying question:
  User: "Cancel my subscription."
  Agent: "I can help with that. Just to confirm — are you looking 
          to cancel the free trial or your paid Professional plan?"
```

**Rule:** One clarifying question at a time. If you need to resolve multiple ambiguities, resolve the most critical one first — the answer may make the others irrelevant.

---

### Pattern 3: Confirm Before Irreversible Actions

Any action the agent takes that cannot be undone requires explicit user confirmation. This is both a UX principle and a governance requirement — users need the opportunity to catch errors before they become problems.

```
Agent: "I'm ready to permanently delete the 847 contacts 
        marked as inactive in your CRM. 

        ⚠️ This cannot be undone.

        Type 'confirm' to proceed, or 'cancel' to stop."
```

The confirmation message should:
- State exactly what will happen
- Flag that it cannot be undone (when true)
- Make the confirmation action explicit and intentional (not just "click OK")

---

### Pattern 4: Graceful Failure

When the agent can't complete a task — because of a tool failure, a permission issue, or something it doesn't understand — the response should leave the user informed and with a clear next step. Never leave a user stranded.

```
❌ Unhelpful failure:
  "An error occurred. Please try again."

❌ Over-technical failure:
  "Tool call failed: ConnectionError — HTTPSConnectionPool host='api.crm.internal' 
   max retries exceeded with url: /v2/contacts/48291"

✅ Graceful failure:
  "I wasn't able to reach the order system right now — 
   it looks like there may be a temporary connection issue.

   You can check your order status directly at [link], 
   or I can try again in a few minutes. Which would you prefer?"
```

A graceful failure message answers three questions: *What happened?* *Why?* (briefly) *What can the user do now?*

---

### Pattern 5: Closing the Loop

Every completed interaction should end with a clear signal that the task is done and a summary of what was accomplished. Users should never have to wonder: *"Did that actually work?"*

```
❌ No closure:
  Agent: [Processes the return]
  [Conversation ends]

✅ Closes the loop:
  Agent: "Done — I've processed your return for order #48291.

  Here's what happens next:
  • Drop off your package at any DHL location by March 18th
  • Your refund of $349 will appear within 5–7 business days
  • You'll receive a confirmation email at maria@email.com

  Is there anything else I can help with?"
```

The summary serves a second purpose: it gives the user something to reference later if they have questions about what was done.

---

### Matching Tone to Context

The way an agent communicates should match the context in which it is being used. A support agent for a luxury hotel brand should sound very different from an internal operations bot for a logistics company.

Three dimensions to define:

**Formality:** How formal or casual is the language?
```
Formal:   "Your request has been processed. A confirmation will be 
           sent to your registered email address."
Casual:   "Done! You'll get a confirmation email shortly."
```

**Warmth:** How much does the agent acknowledge the human on the other side?
```
Neutral:  "Refund processed."
Warm:     "I'm sorry for the trouble with your order. 
           Your refund has been processed — I hope this makes things right."
```

**Brevity:** How much does the agent say?
```
Verbose:  "I've completed my review of your account and have determined
           that based on your current subscription tier and usage patterns,
           you are eligible for..."
Brief:    "You're eligible. Here's what you get:"
```

Define these three dimensions explicitly in the system prompt — don't leave them to chance.

---

## 3. Testing and Refining Agent Interactions (15 min)

### Why Testing UX Is Different From Testing Logic

Testing whether an agent's logic is correct is relatively straightforward: you give it inputs, check the outputs, and verify the tools were called correctly. Testing whether an agent's *interaction* is good requires a different approach — because "good" depends on how a real user experiences it, not just whether the output matches a specification.

UX testing asks: *Does this make sense to a real person? Do they know what to do? Do they trust the result? Would they use this again?*

---

### Three Levels of UX Testing

#### Level 1: Desk Testing (Solo Review)

Before involving anyone else, review every interaction path yourself — not as the designer, but as a user seeing it for the first time.

For each response the agent produces, ask:
- Can I understand this in one reading?
- Is it clear what I should do next?
- Would I trust this response if I didn't know how the agent worked?
- Is there anything here that could confuse or alarm someone?

This catches the most obvious problems before they reach a real user.

**The "fresh eyes" trick:** Write an agent response, wait 24 hours, then re-read it. You'll notice problems that were invisible when you wrote it.

---

#### Level 2: Colleague Testing (Observed Use)

Ask someone who was not involved in building the agent to use it while you watch — without explaining how it works first. Give them a realistic task to complete and observe without intervening.

What to look for:
- **Confusion moments:** Where do they hesitate, re-read, or ask "what does this mean?"
- **Wrong assumptions:** Do they interpret a message differently than you intended?
- **Drop-off points:** Where do they give up or lose confidence?
- **Unexpected paths:** What do they do that you didn't design for?

Don't explain or defend while observing — every moment of confusion is useful data. Only after they've completed (or abandoned) the task should you ask what was unclear.

```
Common findings from colleague testing:

"I didn't know if it had actually done it or just acknowledged my message."
→ Fix: Add explicit confirmation with summary of what was done

"I wasn't sure what to type — I didn't know if it understood abbreviations."
→ Fix: Add an example of a valid input in the first message

"When it asked me to 'confirm,' I wasn't sure what to write."
→ Fix: Make the confirmation action more specific: "Reply YES to continue"
```

---

#### Level 3: Iterative Refinement Based on Real Use

Once the agent is live with real users, conversation logs become the most valuable source of UX data. Patterns in the logs reveal the gaps between how you designed the interaction and how people actually use it.

What to look for in logs:

| Pattern in logs | What it signals | Likely fix |
|---|---|---|
| Users repeat the same message multiple times | Agent response was unclear or didn't answer the question | Rewrite the response to be more direct |
| Users frequently type "help" or "what can you do?" | Onboarding message doesn't set expectations | Add a clear welcome message explaining capabilities |
| Many conversations end without task completion | A step in the flow is causing drop-off | Identify and simplify the drop-off point |
| Users escalate to human frequently at the same step | Agent can't handle something it's being asked to do | Either add the capability or set expectations earlier |
| Users express frustration in their messages | Interaction is too slow, confusing, or unhelpful | Review the full conversation path for friction |

---

### The Refinement Cycle

UX improvement is not a one-time fix — it is an ongoing cycle:

<img width="691" height="425" alt="image" src="https://git.generalassemb.ly/user-attachments/assets/282c51be-a18b-47df-b375-bf022bb625c1" />



**The most important rule of refinement:** change one thing at a time. If you update the welcome message, the clarifying question, and the confirmation format all at once and the drop-off rate improves, you have no idea which change made the difference — and you can't reproduce it intentionally.

---

### Prompt Refinement: Translating UX Feedback Into System Prompt Changes

Most UX problems in agent interactions trace back to the system prompt. When testing reveals a problem, the fix is usually a targeted change to how the agent is instructed.

```
Problem observed:
Users frequently ask "did you actually send that?" after the agent 
says it has sent an email — they don't trust that it worked.

Root cause:
The system prompt says "confirm when actions are complete" 
but doesn't specify what confirmation should look like.

Prompt refinement:
Add to system prompt:
"When you complete an action that sends a message or updates a record, 
always confirm with: (1) what was done, (2) where it was sent or saved, 
and (3) what the user should expect to happen next. 
Example: 'Done — I've sent the summary to maria@email.com. 
You should receive it within a few minutes.'"

Expected result:
Users receive specific, verifiable confirmation instead of a vague 
acknowledgment — reducing follow-up questions and increasing trust.
```

Every UX refinement should follow this pattern:
1. **Problem observed** (from testing or logs)
2. **Root cause identified** (what in the prompt or flow caused it?)
3. **Specific change made** (what exactly was updated, and why?)
4. **Expected result** (what should change in the next round of testing?)

---

## 4. Break (10 min)

---

## 5. Lab (60 min)

https://pages.git.generalassemb.ly/Build-AI-Agents/Agent-UX-and-Interaction/

---

## 6. Wrap-Up & Reflection (5 min)

### Key Takeaways
- A Technically Correct Agent Can Still Fail Its Users
- Good UX Is Designed, Not Assumed
- Refinement Is the Process, Not the Exception

---

## Resources

- Nielsen Norman Group — *Conversational Design: UX Principles for Chatbots and AI Assistants* — [nngroup.com](https://www.nngroup.com/articles/chatbots/)
- [Anthropic — Prompt Engineering: Tone and Communication Style](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)
- [Google — People + AI Guidebook (PAIR)](https://pair.withgoogle.com/guidebook/)
- [Microsoft — Conversation Design for Bots](https://learn.microsoft.com/en-us/azure/bot-service/bot-service-design-principles)
- Erika Hall — *Conversational Design* (A Book Apart, 2018)
- [Voiceflow — Conversation Design Best Practices](https://www.voiceflow.com/blog/conversation-design)
