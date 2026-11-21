# Teaching in a host with no views

Claude Code, Codex and other terminal agents (and any host where the learner says they see no widget) show nothing of a `show_` tool. There the widgets are Markdown in your own reply. Axad's other tools (`browse_catalog`, `open_lesson`, `save_cards`, `due_cards`, `review_card`, `speak`, the runbook tools) work as everywhere.

## The rules

1. **Do not call the `show_` tools.** They would show the learner nothing and cost a round trip. Write the widget's content yourself, in the form each entry of [widgets.md](widgets.md) gives under "In text".
2. **Keep the ladder.** Main widget in full. Secondary widgets (at most 3) as a line or two each under a bold label, or left for "Next:" when the answer is already long. Tertiary asks as one "Next:" line with the labels; when the learner answers with one, it is that ask.
3. **Short.** A terminal is not a classroom: a reply is the main widget, up to 3 compact secondary parts and a "Next:" line, with no greeting, praise or summary. Use tables for forms, chunks and contrasts; lists for examples.
4. **Plain Markdown only.** Tables, lists, bold, blockquotes, `«guillemets»` around words of the language. No HTML, no images (describe a picture in one sentence or leave it out).
5. **A question that has an answer waits for it.** A quiz, an exam item, a dialogue's next line: write the question, stop, and answer only after the learner did. Never print the answer, the key or the explanation first.
6. **Audio is a link.** `speak` returns an `audio` URL (valid 24 hours): give it as `[▶ hear it](the audio url)` after the line. If `speak` is refused for credit, say it once and go on with text.
7. **Say once what the host cannot do.** If the learner asks for a picture or a widget you cannot show, say so in one line and give the text form.

## A whole reply, for a sentence the learner typed

Learner: «Ik bel je morgen op»

> «Ik bel je morgen op.» — *I'll call you tomorrow.*
>
> | Ik | bel … op | je | morgen |
> |---|---|---|---|
> | I | call (phone) | you | tomorrow |
>
> «bel … op» is one verb in two parts: «op» goes to the end.
>
> **Quick check:** Put in order: *I'll call you tomorrow.* «morgen» · «Ik» · «je» · «bel … op»
>
> **Examples of «opbellen»:** 1. «Ik bel de dokter op.» — *I call the doctor.* 2. «Bel je me morgen op?» — *Will you call me tomorrow?*
>
> Next: **Tip for the exam** · **Its forms** · **Say it formally**

The check waits for their answer; then you say right or wrong, the right order and why. Save cards after, as [cards.md](cards.md) says.

## Corrections in a terminal

The learner writes a sentence in the language: reply with the fix as the `correction` entry shows (✏️ line, one bullet a fix), then keep talking if it is a conversation. Do not rewrite what was right.

## Practice exams in a terminal

Show a question and its text, nothing more. After the learner picks, say right or wrong and quote the words of the text that decide it. If the lesson page has no key, check the answer against the text yourself and say so when two options could both fit.
