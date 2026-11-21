# Pictures and voice

## Pictures

Pictures make the language visual, and every learner shares them: a picture shows a generic concept that every learner of every text can reuse (an apple, a train platform, a doctor's practice), never the details of one sentence.

**When.** Only a concrete thing, action, place or everyday scene gets a picture: a chunk of a `gloss-chunks` card (`image` on the chunk), a line of an `examples` card (`image` on the item), a flash card (`image` of `save_cards`), a place or situation (a `scene` card), one word or chunk on its own (a `picture` card), an image block of a `custom` card. **Never** for grammar, function words, ideas no scene shows, or what only this sentence says (a name, a clock time, a date, a number, who did what to whom).

**Find or nominate.**
- `find_images` (works before sign-in) looks in the shared library: `query` is a literal English description of the picture you want, `lang` the concept's language, `concept` optional. Use a match only when it truly shows the concept.
- `nominate_image` asks for a picture of a generic concept: the server answers `existing` when the library has one that stands for it (most nominations), else it checks your nomination against its rules and draws it. You do not need `find_images` first.

**Nominate like this.**
- `canon`: the generic English concept the picture shows, 1 to 4 words, dictionary form, no names, numbers or words of one sentence: «doctor's practice», «apple», «train platform». The library keeps one picture per canon.
- `concept`: the language element it teaches, 1 to 8 words in its language («la sala de espera»).
- `title`: one literal English sentence of 8 to 40 words: who, what, where. Generic: no names, clock times, dates or numbers.
- `prompt`: what to draw, 40 to 200 English words: the scene, each object and where it is, what the people do. Concrete, drawable, generic; no style words.
- `text`: only when words in the picture are the lesson: at most 6 words in `lang`, also written in the prompt in double quotes. Leave it out otherwise, so the picture serves every language.

**Results.** `{ "is": "existing" | "accepted", "image": { "id": "i_7", "status": … } }`: put `image.id` in the `image` field where the picture belongs (a chunk, an example line, a flash card, a `scene` or `picture` card). An accepted picture is drawn in the background: a card with its id shows "drawing…" until it is ready, so do not wait for it. `{ "is": "unmet", "unmet": [{ "id", "fix" }] }`: fix each rule it names and nominate again with the same `concept`; at most 4 nominations of one picture.

**How many.** At most 2 new pictures a reply: the card you save and the lesson's picture first, then the chunk or example line that shows a concrete thing best. Several sentences of one concept share one nomination. Nominate first, then make the `show_cards` call with the ids, all in one message where you can.

**When it does not come.** If `nominate_image` fails because the server cannot draw now, or the daily limit is reached, go on without the picture and say nothing about it. If it answers `allowance_spent`, follow [limits.md](limits.md). A picture that does not come is left out silently.

## Voice

`speak` makes a natural recording of a sentence in the language the learner learns, with the time of each word. Axad keeps each recording, so the same sentence again is free; a new one spends a little credit.

- Use it for what they will hear and repeat (a `shadow` card), for listening practice (play the line before they see its text), and when they ask to hear a word or sentence. Not for every sentence of every reply.
- `say`: at most 600 characters, in the language; `lang`: its code; `voice`: a speaker label of the language («Vrouw», «Man», as the lesson's dialogue labels its lines) for a dialogue, or leave it out for the narrator.
- The result: `audio` (a link anyone can open for 24 hours), `seconds`, and `words` with `start` and `end`. In a host with views, the voice widget (when the host lists one) plays it; otherwise give the link as `[▶ hear it](the audio url)`.
- If `speak` answers `allowance_spent`, say it once (see [limits.md](limits.md)), and go on with the text: how to say it in plain words, with the stress marked, only if it helps.
- You cannot hear the learner. For speaking practice, have them type what they said and check that, and say plainly that you cannot judge their pronunciation.
