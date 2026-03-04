# Agent UX and Interaction  
**Instructor Guide**  
**Module Time:** 120 minutes  
**Format:** Instructor-Led  

---

## What This Module Is About

This module shifts focus from:

> How the agent works  
to  
> How the agent feels to use.

A technically correct agent can still fail if users find it confusing, frustrating, or untrustworthy.

Agent UX is about:

- Clarity  
- Trust  
- Control  
- Conversational structure  
- Iterative refinement  

---

## Core Objectives

By the end of this module, learners should be able to:

- Design clear conversational flows  
- Apply interaction patterns intentionally  
- Test agent interactions with real users  
- Identify friction points in conversations  
- Translate UX feedback into prompt improvements  
- Build trust through transparency and confirmation  

---

# 1. Designing for the User, Not the System (20 min)

## Technical Design vs UX Design

| Technical Design Asks | UX Design Asks |
|-----------------------|----------------|
| Does the tool call succeed? | Does the user understand what happened? |
| Is the output correct? | Is the output clear and actionable? |
| Did the workflow complete? | Does the user feel in control? |
| Did the agent retrieve the right data? | Does the user trust the result? |

Both dimensions must succeed.

---

## Three Foundational UX Principles

### 1. Clarity Over Cleverness

The agent exists to help — not impress.

**Bad (too complex):**

"I've analyzed your request in the context of our parameters..."

**Better (clear and actionable):**

Here are your options:
1. Standard shipping — Friday, free  
2. Express shipping — Tomorrow, +$12  
3. Store pickup — Today, free  

Which do you prefer?

**Test:** Can the user understand it in one reading? Is the next step obvious?

---

### 2. Transparency Without Oversharing

Transparency should scale with risk.

| Action Type | Transparency Level |
|-------------|-------------------|
| Low stakes | Minimal |
| Medium stakes | Brief explanation |
| High stakes | Full explanation + confirmation |

Higher stakes → more explicit explanation.

---

### 3. The User Is Always in Control

Users must be able to:

- Redirect  
- Clarify  
- Stop  
- Escalate  

Never assume when ambiguity exists.

**Bad:**

User: "Reschedule my meeting."  
Agent: Cancels and rebooks automatically.

**Better:**

Agent: "Which meeting — 2 PM or 4 PM? And for what date?"

---

## Know Your User

Before designing:

- Who is the user?
- What are they trying to accomplish?
- What do they already know?
- What platform are they using?

Internal tool ≠ customer-facing assistant.

---

# 2. Conversational Interface Patterns (20 min)

## Pattern 1: Progressive Disclosure

Lead with key information.

**Bad:** Information dump.

**Better:**

Your order arrives Thursday.  
Want tracking details?

Reduce cognitive load.

---

## Pattern 2: Clarify Before Acting

Ask one targeted question at a time.

Resolve the highest-risk ambiguity first.

---

## Pattern 3: Confirm Irreversible Actions

Before deleting, charging, refunding, or mass messaging:

```
I'm about to permanently delete 847 contacts.
This cannot be undone.

Type "CONFIRM" to proceed.
```

Clear, explicit confirmation required.

---

## Pattern 4: Graceful Failure

A good failure message answers:

1. What happened?
2. Why? (briefly)
3. What now?

**Bad:**  
"An error occurred."

**Better:**  
"I couldn't reach the order system right now.  
You can check here [link], or I can retry."

---

## Pattern 5: Close the Loop

Always confirm completion.

```
Done — your refund of $349 has been processed.
It will appear in 5–7 business days.
You'll receive confirmation at maria@email.com.
```

Closure builds trust.

---

## Tone Dimensions

Define explicitly in the system prompt:

- Formality  
- Warmth  
- Brevity  

Tone should match context.

---

# 3. Testing and Refining Agent Interactions (15 min)

UX testing is different from logic testing.

Logic testing asks: Is it correct?  
UX testing asks: Does it make sense to a human?

---

## Level 1: Desk Testing

Ask:

- Is it clear?
- Is the next step obvious?
- Would I trust this?

---

## Level 2: Colleague Testing

Observe someone using the agent without explaining it.

Look for:

- Hesitation  
- Confusion  
- Drop-off  
- Wrong assumptions  

---

## Level 3: Log Analysis

| Pattern in Logs | Meaning | Likely Fix |
|-----------------|----------|------------|
| Users repeat question | Response unclear | Rewrite message |
| Frequent "help" | Onboarding weak | Improve intro |
| Drop-off mid-task | Friction point | Simplify flow |
| High escalation | Capability gap | Adjust scope |

---

## The Refinement Cycle

```
OBSERVE
↓
IDENTIFY
↓
HYPOTHESIZE
↓
ADJUST
↓
MEASURE
↓
REPEAT
```

Change one variable at a time.

---

## Prompt Refinement Template

```
Problem observed:
Root cause:
Prompt change:
Expected result:
Metric to watch:
```

---

## Break (10 min)

---

## Lab (60 min)


## Wrap-Up & Reflection (5 min)


### Key Takeaways

- Technical success ≠ UX success  
- Clarity beats sophistication  
- Transparency scales with risk  
- Users must feel in control  
- Refinement is continuous  

> Trust is designed — not assumed.

---

## Next Session

**Risks and Security**
