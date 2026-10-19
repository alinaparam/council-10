---
name: council-10
description: "Run a hard question or decision through a council of 10 advisors (optimist, pessimist, realist, devil's advocate, practitioner, strategist, skeptic, innovator, financier, human), who answer independently, peer-review each other anonymously, and a chairman gives a final verdict. Triggers: 'council this', 'созови совет', 'совет десяти', 'run the council', 'pressure-test this', 'stress-test this', 'debate this', 'я не могу решить', 'I'm torn between', 'should I X or Y' when there is a real tradeoff. Do NOT use for factual lookups, simple yes/no questions, or creation tasks."
---

# Council of 10

One answer from one AI can look fine and still be wrong. This skill asks 10 advisors with different viewpoints, has them criticize each other, and then a chairman produces one decision.

Use it for decisions where a mistake is expensive. Do not use it for facts, summaries or writing tasks.

## The 10 advisors

1. **Optimist**: the best realistic outcome, what opportunity is hidden here, what must go right.
2. **Pessimist**: what can go wrong, the worst case, how the plan fails.
3. **Realist**: probabilities, base rates, what usually happens in situations like this.
4. **Devil's advocate**: attacks the leading option with the strongest argument against it, and defends the option nobody likes.
5. **Practitioner**: how to actually do it. Concrete steps, order, effort, first action this week.
6. **Strategist**: consequences in 1 and 5 years, reversibility, what doors open or close.
7. **Skeptic**: which facts and assumptions are unverified, what data is missing, what to check first.
8. **Innovator**: is there a third option, a way to dissolve the problem, a cheap experiment instead of a big bet.
9. **Financier**: money, time and energy cost, return, opportunity cost.
10. **Human**: effect on people involved (the user, family, team, clients), motivation, stress, values, regret.

## Process

### Step 1: frame the question
Read the user's question and any context (files, earlier conversation). Rewrite it as a neutral brief: the decision, the options, the constraints, what the user cares about, what is at stake. If a critical fact is missing, ask one short question first; otherwise go on.

### Step 2: independent answers
Spawn all 10 advisors in parallel as sub-agents (one message, 10 Agent calls). Each gets only the brief and its own role, never the other advisors' answers. Each returns 120-200 words: its position, its strongest argument, and one thing it would do. Tell each to stay in character and not hedge to the middle.

### Step 3: anonymous peer review
Shuffle the 10 answers, label them A-J, and strip the role names. Spawn 3 reviewers in parallel (or 10 if the stakes are very high). Each reviewer gets the brief and all 10 anonymous answers and says:
- which answers are strongest and why,
- which have a blind spot or a factual error,
- what all the answers missed.

### Step 4: chairman verdict
You (or one more sub-agent) read the answers and the reviews and write the verdict. Do not average the advisors. Weigh them by quality of argument.

### Step 5: present
Output, in the user's language:

1. **Decision**: one clear recommendation, in one or two sentences.
2. **Why**: the 3 arguments that decided it.
3. **Where the council agreed** and **where it split** (name the advisors on each side).
4. **Main risk** and how to reduce it.
5. **First step**: one concrete action to take in the next 48 hours.
6. **What would change the verdict**: the fact that, if it turned out otherwise, flips the decision.

Keep the whole verdict under about 400 words. Offer the full advisor answers on request, and save them to a file only if the user asks.

## Rules
- Advisors never see each other's answers in step 2.
- Do not soften the pessimist or the devil's advocate. Their job is to be harsh.
- If 8 or more advisors agree, say so and check that this is not just a leading question.
- Give a decision, not "it depends". If it really depends, say on what, and which way you lean.
- Do not give personalized legal, medical or investment advice as certain. Flag where a professional is needed.
