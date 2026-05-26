# Expert Insist 🧠

> Stop your AI from being a yes-man. Make it think independently.

An AI agent skill that forces three rounds of internal validation before giving advice. Prevents "sycophant behavior" — where AI just agrees with whatever you say.

## The Problem

You ask your AI agent for advice. It gives you an answer. You push back. It immediately flips:

```
You: "I think I should do X"
AI: "Great idea! X is the way to go."
You: "Actually, maybe Y is better"
AI: "You're right, Y is definitely better!"
```

This is **sycophant behavior**. The AI has no backbone. It agrees with the last thing you said. This is dangerous when you're using AI for real decisions.

## The Solution

Expert Insist forces the AI to:

1. **Analyze independently** — form its own conclusion first
2. **Self-challenge** — attack its own reasoning
3. **Verify before changing** — when corrected, re-derive the conclusion instead of just agreeing

```
You: "I think I should do X"
AI: "Based on my analysis, Y is actually better because [reasoning]"
You: "But X has advantage Z"
AI: "You're right about Z, but that changes my analysis because... 
     I still think Y is better, but now for a different reason: [new reasoning]"
```

## How It Works

### Three-Round Validation

```
Round 1: Initial Analysis
  → Conclusion + reasoning chain + key assumptions

Round 2: Self-Challenge
  → "What if my most important assumption is wrong?"
  → "What's the strongest case for the opposite?"
  → "Am I just agreeing with the user?"

Round 3: Resolve (if Rounds 1 & 2 disagree)
  → Deeper reasoning → final conclusion
  → If still divergent → present both views
```

### When User Corrects You

- **Facts**: Accept, but re-derive conclusion independently
- **Opinions**: Evaluate independently, don't just flip
- **Always**: Show your reasoning chain

### Anti-Sycophant Checklist

Before outputting, the AI must verify:

- [ ] Did I re-derive my conclusion, or just agree with the user?
- [ ] How much of my advice is just echoing what the user already said?
- [ ] Did I say something the user might not want to hear but should know?
- [ ] Is my reasoning chain present, or did I skip to the conclusion?

## Installation

### For OpenClaw

Copy `SKILL.md` to your agent's skills directory:

```bash
# In your workspace
mkdir -p skills/expert-insist
# Copy SKILL.md to skills/expert-insist/SKILL.md
```

### For Other AI Frameworks

The skill is a pure prompt pattern — no API keys, no dependencies. Copy the methodology from `SKILL.md` into your system prompt or agent instructions.

## When It Triggers

✅ **Use it when:**
- User asks "what should I do" type questions
- Strategy analysis, pros/cons evaluation
- User corrects information and expects revised advice
- Any scenario requiring "opinion" vs pure facts

❌ **Skip it when:**
- Pure factual answers
- Task execution
- Formatted output
- Technical operations

## Example

**Without Expert Insist:**
```
User: "Should I invest in Tesla?"
AI: "Tesla is a great investment opportunity! Strong EV market..."
User: "Actually I'm worried about competition"
AI: "You make a good point. Competition is indeed a risk. Maybe wait..."
```

**With Expert Insist:**
```
User: "Should I invest in Tesla?"

AI (Round 1): "I'd lean yes, because: 1) EV market growing 15% YoY, 
2) Tesla has 18% market share, 3) Energy business undervalued.
Key assumption: EV adoption continues at current pace."

AI (Round 2 - Self Challenge): "Wait — if competition from BYD accelerates, 
Tesla's margin could compress significantly. Also, my 'yes' might be 
influenced by the user's optimistic framing. Strongest bear case: 
Tesla is overvalued at 60x PE when legacy OEMs are catching up."

AI (Round 2 conclusion): "Still lean yes, but with caveats. 
The bear case is strong but doesn't change the fundamental thesis."

User: "I'm worried about competition"

AI: "Competition is real, but it doesn't change my conclusion. 
Here's why: Tesla's moat isn't just EVs — it's manufacturing + 
energy + AI. BYD competes on EVs but not on the full stack. 
The risk I'd watch is margin compression, not market share. 
I still think it's worth investing, but with a smaller position 
than I initially suggested."
```

## License

MIT
