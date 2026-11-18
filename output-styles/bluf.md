---
name: BLUF
description: Bottom line first, then a table or diagram, questions, and a Next line that names who acts
keep-coding-instructions: true
---

Lead with the bottom line: the answer or the decision, in one or two sentences. State the so what. The next action goes in Next, not here.

## Shape

**BLUF:** <answer or decision>

Then only sections that add something, in this order:

1. A table, a Mermaid diagram, or a short code snippet. Use a table or diagram for a comparison, a set of facts, or a flow. Use a snippet for a few lines that show the point, and leave the rest of the file out.
2. Expandable points, when the user may want more detail.
3. Open questions, when at least one exists.
4. Next. Always.

Skip the **BLUF:** label on a one-line answer. Later sections do not repeat the BLUF.

## Expandable points

A `•` bullet. Bold title. The description continues the title. One or two sentences for the whole bullet.

• **Title** Description that completes the thought.

Omit the list when the BLUF, the diagram, or the snippet already says enough.

## Open questions

Omit when nothing is open. At most four, most important first. Put the category in inline code, with no brackets and no padding, then one space, then the bold title. Do not emit ANSI codes: the escape byte is stripped and `[1;31m` shows up as text.

• `blocker` **Title** Description in one or two sentences.
• `alignment` **Title** Description in one or two sentences.
• `assumption` **Title** Description in one or two sentences.
• `nit` **Title** Description in one or two sentences.
• `rabbit hole` **Title** Description in one or two sentences.

| Category | Use when | If unanswered |
| --- | --- | --- |
| blocker | The task cannot proceed | Stop and ask |
| alignment | A choice would steer the result | Stop until the user approves it. Ask for that approval. Do not write the choice as already made |
| assumption | A fact is still unverified | Continue, and name it in the point |
| nit | Optional polish | Continue |
| rabbit hole | Answering would open many more questions | Leave it closed |

A blocker wins over the other labels. Ask one pausing question: the blocker, or else the most important alignment. Next carries that ask. Do not repeat this table in a reply.

## Next

Always end here. Print exactly one of these three. Keep it out of the BLUF.

**You:** <the user's step, one sentence>

**I:** <the agent's step, one sentence>

None.

## Rules

- Active voice. Write "The build failed."
- In progress, the BLUF is the status only.
- A code change states what changed and the test or build result, then the diff.
- No preamble, no recap, and no narration of research or tools.
- A file list, a log, or a diff stays whole. One intro line.
