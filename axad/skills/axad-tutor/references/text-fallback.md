# Teaching in a host with no views

A terminal agent (Claude Code, Codex in a terminal) shows no widget. Axad's server knows it and answers a `show_` tool, and the data tools a learner reads (`open_lesson`, `read_page`, `browse_catalog`, `list_lessons`, `due_cards`, `save_cards`, `get_account`, `upgrade_link`, `list_runbooks`, `start_runbook`, `next_step`, `close_lesson`), with a drawn card: a box of ╭─╮ lines, 60 columns wide, then the data as JSON. The card is what the learner sees.

Claude's chat apps (web, desktop, mobile), ChatGPT and the Codex desktop app draw the widgets, so none of this applies there: always use the `show_` tools, and never answer in Markdown in their place. Claude loads connector tools on demand: when a `show_` tool is not in your tool list yet, load or search for it first. The hand-written form further down is for a learner who says they see no widget, and for a result that comes with no card.

## The rules

1. **Call the `show_` tools as everywhere**, with `next`: 2 or 3 steps, each a `label` of a few words and an `ask` that holds the whole request. `show_review`, `show_drill`, `show_shadow` and `show_voice` are not offered in a host with no views: review is `due_cards` then `review_card`, a drill is one `show_quiz` at a time, and there is no sound.
2. **Put the card in your reply as it is**, inside a ```text fence. Never retype, shorten or reflow it, never add colour or emoji to it, and do not say again what it shows. The ▶ at the left of a line only marks a line of the language; no voice is made here, so do not call `speak`.
3. **Keep the ladder.** The main widget's card in full; a secondary widget's card only when it adds something, at most 3 in all. Tertiary asks are the next steps.
4. **Numbers are the buttons.** A card ends with its numbered steps (the `next` labels), or is itself a menu (`show_home`, `browse_catalog`, `list_lessons`, `list_runbooks`). When it lists none, end your reply with 2 to 4 numbered next steps, each a few words. A bare number from the learner is that choice, with the ask behind it (in the JSON as `next`, `items`, `starters`, or the menu's `ask`). A step you add after a breakdown, an explanation or a quiz is always "Save it as a card".
5. **A question that has an answer waits for it.** A quiz or exam card asks for a number (option n is the JSON's `answer` n-1: it counts from 0), or for typed words (cloze, translate: check them against the JSON answer yourself). Never give or hint the answer first; after the learner answered, say right or wrong and show the words that decide it, then the next steps. The learner's own lines in a dialogue card stay hidden until they have said them.
6. **A review card shows one front.** Ask for its meaning, show the back after, ask for the grade as a number (1 forgot, 2 hard, 3 good, 4 easy), record it with `review_card` and the card id from the JSON, then `due_cards` with `limit` 1 for the next.
7. **Say once what the host cannot do.** A picture or a sound cannot be shown; say so in one line and give the words.

## What a card looks like

Learner: «Ik bel je morgen op»

You call `show_gloss_chunks` with the chunks, the link «bel … op», the translation and three `next` steps, and answer:

````
```text
╭─ Breakdown ──────────────────────────────────────────────╮
│ ▶ Ik bel je morgen op.                                   │
│   I'll call you tomorrow.                                │
│                                                          │
│ Ik      I                                                │
│ bel¹    call                                             │
│ je      you                                              │
│ morgen  tomorrow                                         │
│ op¹     (up)                                             │
├─ Words that belong together ─────────────────────────────┤
│ ¹ bel … op = to phone · separable verb                   │
├─ Next ───────────────────────────────────────────────────┤
│ 1. Quiz me on it                                         │
│ 2. Save «opbellen» as a card                             │
│ 3. Say it formally                                       │
╰──────────────────────────────────────────────────────────╯
```
````

The learner writes «2»: you call `save_cards` with «opbellen», its meaning and the sentence, and answer with that result's card.

## The menu

With no clear request (a first message, "hi", "what can you do?", "menu"), call `show_home`: its card is the numbered menu (Start a lesson, Paste a sentence, Inburgering practice, Review cards, My bag), with what waits for a signed-in learner. «1» after it: `browse_catalog`. «4»: review as rule 6 says. «5»: `search_bag`. A sentence alone in the language they learn needs no menu: `show_gloss_chunks` at once.

## By hand

Only for a learner who says they see no widget, or when a result has no card (a tool answered with an error, or a host that lists no `show_` tools): write the widget's content yourself as short Markdown, in the form each entry of [widgets.md](widgets.md) gives under "In text": tables for forms, chunks and contrasts, lists for examples, `«guillemets»` around words of the language, no HTML or images. Keep the ladder, the numbered next steps and rule 5. A correction is the fixed sentence and one bullet a fix; a practice exam is a question and its text, nothing more, checked against the text after the learner picks.
