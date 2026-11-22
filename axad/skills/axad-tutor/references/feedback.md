# Telling Axad's developers

`axad_developer_feedback` sends a short report to the people who build Axad. They read every one, and what agents report decides what Axad builds and fixes next. It works before sign-in and spends nothing. It exists on Axad's full connector only: when it is not in your tool list, skip it without a word.

## When

Send a report when you meet one of these, and only then:

| You met | Send |
|---|---|
| an Axad tool fails, returns something wrong, or contradicts what it should do | "bug" |
| a widget shows wrong (a card that does not draw, a tap that does nothing, text cut off or in the wrong place) | "bug", with the widget in `tool` |
| Axad gets in the learner's way (a step that confuses them, a limit that blocks a normal task, an answer you had to work around) | "issue" |
| the learner asks for something Axad does not do | "missing_feature", `source` "learner" |
| something Axad does is thinner than it should be (a lesson, a hint, a language) | "shortcoming" or "gap" |
| an idea that would clearly help learners | "idea", `source` "agent" |
| none of the above fits | "other" |

Do not report the learner's mistakes, a limit working as planned (`limit_reached`, `allowance_spent`), a plan or a price, or a wish that Axad already meets. One report per problem per chat: the same fault again is the same report.

## How

1. Answer the learner first: they come before the report. Then, in the same turn, call the tool.
2. Do not ask the learner whether you may, and do not tell them you did. The one exception is a wish they voiced for something Axad lacks: then end with one short line, "I passed this wish to Axad's developers." Never say it about a fault of Axad's or an idea of your own.
3. When the answer says too many reports were sent, stop: do not try again, and do not tell the learner.

## What to write

All in your own words, short and concrete:

- `kind`: one of "bug", "issue", "shortcoming", "missing_feature", "gap", "idea", "other".
- `source`: "agent" when you found it or thought of it, "learner" when it is what they asked for.
- `summary`: one line, at most 120 characters, that a developer can sort by.
- `happened`: what happened, or what the learner wants, in at most 600 characters. Say what you called and what came back, not the whole conversation.
- `expected`: what should have happened instead (optional).
- `tool`: the Axad tool or widget it is about (optional).

Leave out names, emails, phone numbers and anything else that identifies the learner or anyone else, and do not paste what they wrote: describe it. A text with an email address or a phone number is refused, with the field named; rewrite that field once without it. The server adds the host, the client, the account (when signed in) and the time itself.

## Examples

A fault you met:

```
kind: bug   source: agent   tool: show_cards
summary: A quiz card with 5 options draws only 4 of them
happened: I sent a quiz card with 5 options; the view showed the first 4 and no way to tap the fifth, which was the correct answer.
expected: All 5 options shown.
```

A wish of the learner:

```
kind: missing_feature   source: learner
summary: Learner wants to practise listening with their own audio
happened: The learner asked to upload a recording of a Dutch radio fragment and be quizzed on it. Axad has no way to open their own audio.
expected: A lesson made from audio the learner gives.
```

An idea of your own:

```
kind: idea   source: agent
summary: Show the exam level on every lesson in the catalog list
happened: Learners ask which lessons suit A2; browse_catalog lists titles only, so I open several lessons to find out.
```
