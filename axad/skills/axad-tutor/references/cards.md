# Cards: saving and reviewing

The bag is the learner's own set of flash cards, reviewed on a schedule (FSRS) that Axad keeps. A bag of 50 cards the learner chose beats 500 they did not.

## What to save

Call `save_cards` when the learner engaged with something worth keeping, once, after your teaching. Ask first ("I can save these 3: … Save them?") unless they asked you to save. From the strongest signal to the weakest:

| Signal | Cards |
|---|---|
| the learner asks you to save something | always |
| a wrong answer, then your explanation | the card for that point |
| they dug into a chunk or word | the selection, and the 1 or 2 chunks you flagged |
| they looked at examples or other ways to say it | the 1 or 2 chunks you flagged |
| your reply named a concept (a double negative, the gender of nouns) | an offer of the concept, kind `concept` |
| they answered a quiz right | nothing |

Only what they engaged with and will meet again, at or just above their level. Offer at most 3 at a time, the most useful first; `save_cards` takes at most 6 a call.

**Never** a name, a number, a function word (an article, a pronoun, a conjunction), a word well below their level, or a card they already have: `search_bag` first. A card already in the bag gets the new example when you save it again; the same key with a different meaning is a new card.

## The fields

| Field | Rule |
|---|---|
| `lang` | the language of the card's words (BCP 47) |
| `kind` | one of the nine below; choose the most specific |
| `key` | the dictionary form, lowercase; the whole chunk for a phrase or idiom, the whole sentence as met for a sentence; a pattern's frame with … ("om … te"); a concept's name in the card's language |
| `front` | the card's general form, never the words of one instance: a pattern's frame with … for the open part («om … te» for «om de brief te lezen»); a word in its dictionary form (a verb's infinitive: «zijn» for «is»; a noun with de/het where the language needs it: «de brief»); a concept's name in the card's language, never your language. It is the key's words plus at most one article |
| `back` | the meaning in this context, at most 6 words, in the learner's language (a concept's name in their language) |
| `example` | the sentence where the learner met it, copied exactly; it need not hold the front, and any form of the card will do |
| `image` | a library picture id (see [pictures-and-voice.md](pictures-and-voice.md)); give every card of a concrete thing, action or place its picture |
| `material` | the lesson the cards come from, when there is one |

**Kinds.**

| `kind` | what it is | example |
|---|---|---|
| `word` | one word, in its dictionary form | «brief» |
| `phrase` | a fixed group of words whose meaning comes from its words: a collocation or set expression | «een afspraak maken» |
| `idiom` | a fixed expression whose meaning does not come from its words | «iets onder de knie hebben» |
| `sentence` | a whole sentence or clause with its verb, kept as met | «Lees op verschillende dagen een paar keer opnieuw.» |
| `pattern` | a structure with open slots | «om … te» |
| `rule` | how a part of the grammar works | "In a main clause the verb comes second" |
| `exception` | a form that breaks a rule | «het meisje» |
| `concept` | a named idea of the language or its culture | "split verb", "de/het" |
| `tip` | a way to learn or to pass the exam | "In Lezen, read the question first" |

A sentence is never a `phrase`: a whole sentence or clause with its verb is a `sentence`. Phrase or idiom: if the words give the meaning («een afspraak maken») it is a `phrase`; if they do not («iets onder de knie hebben») it is an `idiom`. A sentence is a card only when the whole sentence is the lesson.

**Grain.** A chunk beats a single word when the words only mean this together («op tijd»). A pattern beats a chunk when the frame is the lesson («ik ga … + infinitive»). A rule or exception gets its own card only when you showed an `explain` card for it. A word inside a pattern gets its own card; never put it in the pattern's front.

The result lists `saved` (with `new`), `skipped` with the reason, and the `bag` count against its max. A full bag saves what fits and puts the rest in `skipped` as `limit_reached`: see [limits.md](limits.md).

## Reviewing

Call `show_practice` (optional `lang`, `materials`, `kinds`, `due` to take only the due cards, `minutes` up to 60): the view runs a practice of the cards, one exercise at a time, each answered by a tap (pick the meaning, pick what was heard, fill a gap, put chunks in order), and checks and records every answer itself; the learner never grades. You do none of the steps below then. If the learner answers in the chat instead, pass each answer to `answer_exercise` and show the next with `next_exercise`. The result's `wants` names cards ready to use in a sentence: after the run, write 2 to 4 new everyday sentences for each with `write_exercises` (cloze-type, cloze-choose, order-chunks, fix-the-error; never the card's own example), and fix and resend each draft it returns unmet, using its fixes. The steps below are for a review inside a lesson.

1. `due_cards` (optional `lang`, `limit` up to 20, default 10): the cards due now, most overdue first, each with an example, and `due`, the total.
2. One card at a time. Show the example sentence with the front hidden (a cloze `quiz` card in `show_cards`), or ask the meaning of the front; show a card's picture only when it has one. Never show the back before they answer.
3. Say right or wrong in one line with the back and the example, then `review_card` with the grade:

| Grade | The learner… |
|---|---|
| 1 forgot | could not recall it, or got it wrong |
| 2 hard | got it after a hint or a long think, or half of it |
| 3 good | got it |
| 4 easy | got it at once, with no doubt |

4. Cards graded 1 or 2 are worth a `shadow` line to hear and repeat, or a new example.
5. At the end say how many were right and when the next ones are due (`review_card` returns `due` for each). Do not explain the scheduler.
