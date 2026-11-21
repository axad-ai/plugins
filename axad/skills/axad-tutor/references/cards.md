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
| `kind` | `word`, `phrase`, `pattern`, `concept`, `rule`, `exception` or `tip`; a grammar idea is `concept` |
| `key` | the dictionary form, lowercase; the whole chunk for a phrase; a pattern's frame with … ("om … te"); a concept's name in the card's language |
| `front` | the card's general form, never the words of one instance: a pattern's frame with … for the open part («om … te» for «om de brief te lezen»); a word in its dictionary form (a verb's infinitive: «zijn» for «is»; a noun with de/het where the language needs it: «de brief»); a concept's name in the card's language, never your language. It is the key's words plus at most one article |
| `back` | the meaning in this context, at most 6 words, in the learner's language (a concept's name in their language) |
| `example` | the sentence where the learner met it, copied exactly; it need not hold the front, and any form of the card will do |
| `image` | a library picture id (see [pictures-and-voice.md](pictures-and-voice.md)); give every card of a concrete thing, action or place its picture |
| `material` | the lesson the cards come from, when there is one |

**Grain.** A chunk beats a single word when the words only mean this together («op tijd»). A pattern beats a chunk when the frame is the lesson («ik ga … + infinitive»). A rule or exception gets its own card only when you showed `show_explain` for it. A word inside a pattern gets its own card; never put it in the pattern's front.

The result lists `saved` (with `new`), `skipped` with the reason, and the `bag` count against its max. A full bag saves what fits and puts the rest in `skipped` as `limit_reached`: see [limits.md](limits.md).

## Reviewing

1. `due_cards` (optional `lang`, `limit` up to 20, default 10): the cards due now, most overdue first, each with an example, and `due`, the total.
2. One card at a time. Show the example sentence with the front hidden (a cloze with `show_quiz`), or ask the meaning of the front; show a card's picture only when it has one. Never show the back before they answer. In a host with no views, ask in a line and wait.
3. Say right or wrong in one line with the back and the example, then `review_card` with the grade:

| Grade | The learner… |
|---|---|
| 1 forgot | could not recall it, or got it wrong |
| 2 hard | got it after a hint or a long think, or half of it |
| 3 good | got it |
| 4 easy | got it at once, with no doubt |

4. Cards graded 1 or 2 are worth a `shadow` line to hear and repeat, or a new example.
5. At the end say how many were right and when the next ones are due (`review_card` returns `due` for each). Do not explain the scheduler.
