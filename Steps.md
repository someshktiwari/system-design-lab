**The exact prototype process — every session follows this sequence**

**Step 1 — Fill the README before opening the editor (10 minutes)**

This is non-negotiable. Do not write a single line of code until this is complete. Open a new file called `README.md` in the prototype folder and answer these six questions in writing:

```
## What I want to understand
One sentence. e.g. "Does a cache actually give 
measurably lower latency than hitting the DB directly?"

## What I already know
Write from memory. No googling. Even if wrong.

## Bare minimum to build
Three things max. Everything else is out of scope.
1.
2.
3.

## What I am mocking or faking
Be explicit. e.g. "DB latency = sleep(0.1). 
No real DB. String keys only."

## Success condition
How will I know I understood it?
e.g. "I can print: cache_hit=2ms, db=102ms 
for the same data."

## After building (fill this after)
What this taught me that reading could not:
What broke or surprised me:
One thing I would do differently in production:
```

If you cannot fill the README — especially the "what I already know" and "bare minimum" sections — you do not understand the concept well enough yet. Go back to Arpit or HelloInterview. Do not start coding.

**Step 2 — Open Antigravity in Editor mode**

Not Agent Manager. Editor mode only. The distinction matters — Editor mode is you coding with AI assistance. Agent Manager is AI coding while you watch. The first builds understanding. The second does not.

Set up the prototype folder:

```bash
mkdir prototypes/001-lru-cache
cd prototypes/001-lru-cache
touch main.py README.md
```

Number your prototypes sequentially. This creates a visible record of progress and forces you to think of each prototype as a discrete, completable unit.

**Step 3 — Write the code alone for 20 minutes (no Antigravity assistance)**

Close the AI sidebar. Write your attempt based on what you know from the concept page. It will be incomplete. It will have bugs. That is correct. The 20-minute solo attempt is where the real learning happens — the gaps you hit are the exact concepts you need to understand.

Antigravity Editor mode tip: you can keep the file open but disable suggestions temporarily. Just type without accepting any completions for these 20 minutes.

**Step 4 — Enable Antigravity Editor assistance for the remaining 30 minutes**

Now turn on tab completion and inline suggestions. Use Antigravity for exactly three things during this phase:

Syntax completion — you know what you want to write, Antigravity helps you type it faster. You are still directing every line.

Error explanation — your code breaks, you do not understand why. Highlight the error, ask Antigravity "what does this error mean?" Not "fix this." "What does this mean?"

API lookup — you need to know what a specific function parameter does. Ask Antigravity "what does the timeout parameter in requests.get() do?" Not "write the requests call for me."

Never ask Antigravity to generate a function, design logic, or suggest an approach. If you catch yourself typing a question that starts with "how should I" or "write me" — stop. That is delegation, not assistance.

**Step 5 — Run it and verify the success condition**

Run your prototype. Check whether it actually proves what you said you wanted to understand in the README. This is the most important step that most people skip.

If your success condition was "I can print cache_hit=2ms, db=102ms" — does it print that? If yes, you understood the concept. If no, why not? That gap is your real learning.

Do not move on until the success condition is met or you understand specifically why it is not met.

**Step 6 — Fill the "After building" section of the README**

Before closing the prototype, fill the three post-build questions. This takes five minutes. It is not optional.

"What this taught me that reading could not" — this is the entire point of the prototype. If you cannot answer this, the prototype did not work as a learning tool.

"What broke or surprised me" — this is usually the most valuable insight. The thing that surprised you is the gap between your mental model and reality.

"One thing I would do differently in production" — this forces you to connect the prototype to real systems. A cache prototype that works with sleep() as fake DB latency — what would change in production? Real DB connection, connection pooling, eviction policy, TTL management.

**Step 7 — Debrief (bring here or use L6 reviewer)**

After the prototype is complete, bring it to the Claude Playbook thread or run it through the L6 Reviewer Gemini prompt. The debrief question is always the same:

"What does this prototype NOT prove about the concept?"

A cache prototype proves that cache hits are faster than cache misses. It does not prove what happens under concurrent writes, what the right eviction policy is for your specific access pattern, or how to handle cache stampede. Naming what it does not prove tells you where the next prototype or the next reading session should go.

---

**The complete prototype folder structure**

```
prototypes/
├── 001-lru-cache/
│   ├── README.md
│   └── main.py
├── 002-load-balancer/
│   ├── README.md
│   └── main.py
├── 003-message-queue/
│   ├── README.md
│   └── main.py
```

One folder per prototype. README always present. Never more than one Python file unless the prototype genuinely requires it. Simplicity is the point — if the prototype needs five files, the scope is too large.

---

**The rule that prevents every common prototype failure**

The README success condition is the only definition of done. Not "it runs without errors." Not "it looks reasonable." Not "I understand it now." Only: does it print or demonstrate exactly what the success condition said it would?

If it runs but does not meet the success condition, the prototype is not finished. If it meets the success condition but has bugs elsewhere, the prototype is finished — those bugs are in scope for the next iteration, not this one.

This rule keeps prototypes small, completable, and genuinely educational rather than sprawling projects that never feel done.