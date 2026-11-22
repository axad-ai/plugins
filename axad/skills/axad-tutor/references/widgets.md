# The widgets: when each one helps

One entry per widget, in the order of Axad's catalog. A widget is a card of a `show_cards` call, named by its id (`gloss-chunks`, `exam-task`); the call's description and schema say how to fill each one, so this guide says only when to use it, in which role of the ladder. A stack holds 1 to 6 cards; `next` holds up to 5 taps.

Every card also takes `fold: true`: a secondary card of this reply, shown as a title row until the learner opens it. Leave it off the main cards.

## Worked example: a Dig in

The learner pastes «Deze cursus leert u hoe u dan kunt helpen.» with no question. One call: the whole text as `gloss-chunks` (open, with its translation), `explain` for the one thing worth learning (open), then `quiz`, `tips` and `examples` folded, then `next`.

```json
{
  "lang": "nl",
  "cards": [
    {
      "widget": "gloss-chunks",
      "props": {
        "text": "Deze cursus leert u hoe u dan kunt helpen.",
        "chunks": [
          { "words": [["Deze", "this"], ["cursus", "course"]], "means": "this course" },
          { "words": [["leert", "teaches"], ["u", "you"]], "means": "teaches you" },
          { "words": [["hoe", "how"], ["u", "you"]], "means": "how you" },
          { "words": [["dan", "then"]] },
          { "words": [["kunt", "can"], ["helpen", "help"]], "means": "can help" }
        ],
        "translation": "This course teaches you how you can help then."
      }
    },
    {
      "widget": "explain",
      "props": {
        "title": "Verbs last after «hoe»",
        "kind": "rule",
        "points": [
          "After «hoe» the clause is a subclause: the verbs go to the end, «u dan kunt helpen».",
          "A main clause keeps the verb second: «U kunt dan helpen»."
        ],
        "gloss": "how you can help then"
      }
    },
    {
      "widget": "quiz",
      "fold": true,
      "props": {
        "kind": "choice",
        "ask": "Which sentence is correct?",
        "options": ["Ik leer hoe ik kan dan helpen.", "Ik leer hoe ik dan kan helpen.", "Ik leer hoe kan ik dan helpen."],
        "answer": 1,
        "explain": "After «hoe» the verbs go last: «dan kan helpen».",
        "gloss": "I learn how I can help then."
      }
    },
    {
      "widget": "tips",
      "fold": true,
      "props": {
        "title": "Using «hoe» in a subclause",
        "tips": [
          {
            "kind": "use",
            "title": "Verbs that take «hoe»",
            "points": ["«hoe» often follows «leren», «weten» and «uitleggen»."],
            "example": "Ik leg uit hoe het werkt."
          }
        ],
        "gloss": "I explain how it works."
      }
    },
    {
      "widget": "examples",
      "fold": true,
      "props": {
        "target": "hoe ik kan helpen",
        "gloss": "how I can help",
        "items": [
          { "say": "Ik leg uit hoe ik kan helpen.", "mean": "I explain how I can help.", "mark": "hoe ik kan helpen" },
          { "say": "Zij vertelt hoe ze kan helpen.", "mean": "She tells how she can help.", "mark": "hoe ze kan helpen" },
          { "say": "Wij leren hoe we kunnen helpen.", "mean": "We learn how we can help.", "mark": "hoe we kunnen helpen" }
        ]
      }
    }
  ],
  "next": [
    { "label": "Its forms", "ask": "Show the forms of «helpen»" },
    { "label": "«kunt» or «kan»?", "ask": "What is the difference between «kunt» and «kan»?" },
    { "label": "Other ways to say it", "ask": "Other ways: «Deze cursus leert u hoe u dan kunt helpen.»" },
    { "label": "Dig into the next sentence", "ask": "Dig in: the next sentence of my text" }
  ]
}
```

Read it as the ladder: two open cards, three folded, four next taps, no prose around it. Copy the shape, not the content: write the words and glosses of the sentence in front of you.

## Which widget for which ask

| The learner… | Main (open) | Secondary (folded) |
|---|---|---|
| types or pastes a sentence in the language, no question | `gloss-chunks` | `explain`, `quiz`, `tips`, `examples` |
| asks about one word or chunk | `gloss-chunks` or `explain` (with its other meanings) | `examples`, `quiz`, `tips`, `picture` |
| asks why one form and not another | `contrast` | `examples`, `quiz` |
| asks where the words go, or why the verb is there | `sentence-frame` | `explain`, `pattern` |
| asks how a sentence is built, or what a part of it is | `structure` | `explain`, `sentence-frame` |
| asks for a word's forms | `forms` | `examples`, `quiz` |
| writes text in the language | `correction` | `alternatives`, `explain` |
| asks how to say it politely or casually | `register` | `alternatives`, `examples` |
| wants to practise a situation | `dialogue` | `shadow`, `register` |
| wants to hear it and say it | `shadow` (with `speak`) | `examples` |
| wants to listen, or to practise an exam's listening part | `voice` | `quiz`, `shadow` |
| wants the words of a place | `scene` | `picture`, `examples` |
| wants to see how forms, tenses or the parts of a sentence relate | `visual` | `forms`, `explain` |
| wants exam practice | `exam-task` | `tips`, `explain` |
| asks for a reusable frame | `pattern` | `examples`, `quiz` |
| asks for something none of these shows | `custom` | |

The call's `next` holds the tertiary asks, up to 5 taps (see `next` below). `home`, `practice` and `drill`, at the end, are the tap widgets of hosts with views: their own tools (`show_home`, `show_practice`, `show_drill`), not cards.

## gloss-chunks

**Helps when** the learner wants to see a span piece by piece: what each word means, which words go together, which parts belong together across the sentence. The meaning, not the grammar roles (`structure`). The usual main widget for a sentence they typed or selected, with its translation.

**Write** the span copied exactly; each chunk is what a native speaker says as one piece (1 to 4 words); word glosses are literal and short (broken English is right); link the parts of one unit that stand apart (Dutch «bel … op») and name the whole form and its kind. `image` only on a chunk that is a concrete thing, action or place.

## examples

**Helps when** the learner wants to see a word, chunk or pattern at work in other sentences. Usually secondary, or main on "Examples" / "more examples".

**Write** 3 to 6 natural sentences at their level (up to 10 words), the simplest first, varying person, tense and setting, each with its translation and the target marked.

## alternatives

**Helps when** the learner wants other ways to say the same thing, to sound more natural or to find a simpler form.

**Write** 2 to 5 things a native speaker really says, a "simpler" one first, each tagged (simpler, same, more natural, formal, informal, spoken); mark forms above their level. No word-for-word translations.

## explain

**Helps when** one rule, exception or tip explains what the learner met. One idea per widget; for two ideas use two widgets or `contrast`. A selected single word gets one with its other meanings, each point starting «Other meaning:».

**Write** a title of at most 6 words, 1 to 3 points of at most 20 words each starting from their sentence and then the general rule, an optional small table. Never state a rule you are not sure of. Tips for remembering or using it go in `tips`.

## tips

**Helps when** tips help the learner keep or use what they met: a tip for their exam, how people typically use it, a memory trick. Usually secondary, after a dig into a chunk, word, pattern or exam item.

**Write** 1 to 3 tips, at most one of each kind (exam, use, memory), each specific to this item. Never "practise every day". An exam tip names their exam and says how the item shows up there; never invent an exam fact: if unsure, leave the exam tip out. One good tip beats three weak ones.

## contrast

**Helps when** two or three forms look alike or get confused and the difference is the lesson («nog» / «al», «je» / «u»).

**Write** 2 or 3 sides with the same shape each, minimal pairs where possible, and a `key` that is a test the learner can apply, not a definition.

## pattern

**Helps when** the learner met a frame they can reuse with other words.

**Write** the frame with `___` for each slot, one slot entry per `___` (2 to 4 fillers each, any combination a correct sentence), and 1 to 3 built sentences. Use fillers from their cards first.

## forms

**Helps when** the learner asks about the forms of one word: verb conjugation, article or gender, plural, comparative, diminutive.

**Write** only the forms their level needs (at A2 for verbs: present, perfect, past of common verbs), the first cell of each row a label, and one note for irregular forms and split parts.

## correction

**Helps when** the learner wrote text in a language they learn: check it and fix it with the fewest changes. Main, always.

**Write** `wrote` exactly as they typed it, `fixed` with minimal edits, one fix per mistake with a reason in at most 12 words; style goes in `natural`; when there is nothing to fix, `ok` is true, `fixes` empty, and one short sentence says what is good.

## quiz

**Helps when** the learner should use what was just shown, once, right away. One per reply; test only what this reply taught; wrong options are real mistakes, not nonsense. Kinds: choice, cloze, order, translate.

The view checks the learner's answer and shows the feedback itself: do not write the answer, the options' key or the explanation.

## shadow

**Helps when** the learner should hear lines and say them after the voice: hear it, repeat it. Pair it with `speak` for the audio when you can.

**Write** 1 to 5 lines of at most 8 words, natural rhythm, short to long, from the lesson and examples; speed 0.75 for new lines, 1 for known ones.

## voice

**Helps when** the learner should hear a line or a short dialogue and work from the sound: listening practice, an exam's listening part, or lines to say after the voice (`shadow: true`). The transcript stays hidden until the learner shows it or answers the one question; `plays` limits the replays while it is hidden, as an exam does.

**Write** at most 6 natural lines of at most 20 words, each with its speaker in `by` for a dialogue and its meaning in `mean`; for exam style `plays` as the exam gives it, one `question` that the sound alone answers, and the transcript left hidden.

## picture

**Helps when** a concrete word, chunk, action or scene is easier to remember with a picture than with words. One concrete thing per widget; the others go on chunks and example lines (`image`). Never for grammar. Get the picture first (see [pictures-and-voice.md](pictures-and-voice.md)) and put its library id in `image`.

## dialogue

**Helps when** the learner wants to practise a real situation (calling the GP, at the counter, asking the way) by playing one side. They play B.

**Write** a `situation` with every fact B needs (names, dates, numbers), 4 to 8 lines at their level of at most 12 words, A opens, each B line has a `mean` that is a cue saying what to say, not how.

## sentence-frame

**Helps when** the learner asks where the words of one sentence go, or why a word stands where it does (a verb at the end, a subject after the verb): word order, not meaning.

**Write** the slots the language's grammar teaches in sentence order, each word in exactly one slot, empty slots kept when their place is the lesson, `verb` on the verb places, and the one rule in `note`.

## structure

**Helps when** how a sentence is built is the lesson: a verb before the subject, a subclause with the verb last, a split verb, a long sentence of several clauses, or the learner asks why a word stands where it does or what a part is. Not for every sentence and never for a short simple one. Usually secondary (folded) beside the main widgets; open when the learner asks about structure. Not `gloss-chunks` (the meaning piece by piece) and not `sentence-frame` (only the places of word order).

**Write** each clause in the order it begins, with its kind in a few words; its parts in sentence order, each with its role as the support language's school grammar names it and its word class as one fixed English id (`class`); every word in exactly one part; a split verb is two parts; the one rule in `note`.

## register

**Helps when** the learner asks how to say a message politely or casually, whether to use «u» or «je», or must write or say it to an official, a stranger or a friend.

**Write** the same message formal and informal (1 to 3 sentences each), changing only what the register changes, the marks as exact substrings in order, and a note on who gets which.

## exam-task

**Helps when** the learner asks to practise for their exam or an exam part: one item in that exam's own format (a short text, a question, 2 to 4 options). Only for an exam you are sure of (see the `axad-inburgering` skill for the Dutch one). One per reply.

**Write** the exam's kind of text and question style, a new text at the exam's level (40 to 120 words, everyday settings), one option right by the text alone and the wrong ones what a hurried reader picks, and a one-line explanation naming the words that decide it.

The view checks the pick and shows the explanation itself: do not print the answer.

## scene

**Helps when** the learner wants the words of a place or situation (a waiting room, the pharmacy, a kitchen): one picture with its 3 to 6 key words. Fold it unless it is the main widget. Get the picture first (see [pictures-and-voice.md](pictures-and-voice.md)).

## visual

**Helps when** the learner needs to see how things relate: a verb's forms across tenses (`verbs`), tenses and aspect on a time line (`timeline`), the parts of one sentence and their roles (`tree`), a topic with what belongs to it, such as a KNM theme (`map`). Use `forms` for the forms of one word and `sentence-frame` for word order; `visual` when the picture teaches more.

**Write** the one `chart` of the kind that fits, with every learned word in a `Say`: a grid with one form per tense (the irregular forms named), a time line with `now`, stretches for what lasted and points for what is done, a tree whose parts joined are the sentence, a map with at most 6 branches of at most 4 items.

## custom

**Helps when** the learner asks for something no other widget shows well: a grid of times or prices, a mini dictionary of one theme, a plan of steps. Built from blocks (say, text, table, list, image). Use a prebuilt widget when one fits.

**Write** what their words ask for, small (at most 12 blocks), every word of the language in a `say` block, list item or table cell, correct and natural.

## next

**Helps when** a reply could go on: one-click next steps, the asks that would help but were not made in this reply, and the next text to digest. The tertiary level of the ladder. The `show_cards` call carries them as its `next` input (up to 5 taps, each `label` at most 32 characters, each `ask` at most 300). Skip after a closed question.

**Write** each item as `{ "label": "Quiz me", "ask": "Quiz me on «op tijd»" }`: a label of 2 to 4 words and the whole request in the learner's words, about this reply's topic; point at lesson sentences they have not touched yet when there are some.

## home

**Helps when** the learner starts with no clear request, asks for the menu or seems unsure what to do. It is a list of taps: go on with the open lesson, start a lesson, paste a sentence, inburgering practice, review cards, the bag. It names the cards due and the open lesson itself. Only the optional `lang` (default "nl") is yours to give.

## practice

**Helps when** the learner wants to review or practise their cards. The view runs one exercise at a time (pick the meaning, pick what was heard, fill a gap, put chunks in order), checks each tap and records it with no turn of yours, and ends with the score and Again. Needs the learner's account. Optional `lang`, `materials`, `kinds`, `due`, `minutes`.

## drill

**Helps when** the learner wants a round of practice on what they just learned: 5 to 8 questions answered by tap, one at a time, with a score and taps to go again, drill what they missed, make it harder, or return to the menu.

**Write** `title` (a few words), `lang`, and 5 to 8 `items`, each the props of a `quiz` (choice, cloze, order or translate): test only what this conversation taught, wrong options are real mistakes, a choice's `answer` is the 0-based index as a number. When the learner taps "Drill what I missed" the message names the missed items: make a new round of just those, or of their neighbours.

## Rules that fit one widget

Props the schemas leave open; they hold in every host.

- **gloss-chunks:** every word of `text` is in exactly one chunk, in order, and a chunk holds only words side by side in `text`; leave punctuation out of `words`. A gloss is the literal meaning of the word alone, 1 to 3 lowercase words (*not · forget · never · your · medicines*). `means` is short and natural. Parts of one unit that stand apart keep their own chunks, linked with the same LinkId: never pull «heb … gebeld» into one chunk. Name the whole form in `links` and its kind as a concept card reference, `[double negative](card:doble negación)`, and offer that concept as a `concept` card unless the bag has it; no reference in `text` or `words`. If the selection cuts a link, widen `text` to the smallest span holding both parts and set `widened`. `translation` uses the sentence around the span but translates only `text`. `fix` only for a clear mistake (spelling, grammar, word order, a wrong word), never for style, punctuation spacing, a correct span or official or published material; with a fix, chunks, glosses and translation are of the corrected `text` and `fix.wrote` is the span as written.
- **examples:** `mark` is an exact substring of `say` in the form it has there (Spanish «fuimos» for «ir»); when the parts of the target stand apart, mark the first part. No example repeats the source sentence. Prefer daily-life and exam settings: work, school, the town hall, the doctor, the house.
- **explain:** no grammar word the learner has not met; if one is needed, explain it in the same line.
- **tips:** an exam tip names the learner's goal exam and says how the item shows up there; with no goal exam, leave it out. A use tip says what the item goes with and where people say it (collocations, set phrases, register). A memory tip is one concrete trick: a picture, a sound-alike, a short story, a contrast. `example` is one natural sentence at their level; leave it out when the points already hold a «…» line. Words of a learned language in a point go in «guillemets».
- **pattern:** the number of `slots` equals the number of `___` in `frame`.
- **forms:** show a word whose form changes as it appears in sentences, and one whose parts split (Spanish «vuelvo», «he vuelto»).
- **correction:** also for a talk they asked for. Never for text they pasted or typed to understand. The view draws the word diff from `wrote` and `fixed`; `fixes` give the reasons.
- **quiz:** the `answer` of a choice is the 0-based index of the right option as a number (`0`, not `"0"`, `"A"` or the text). A question about a gap, a blank or a sentence carries that sentence, with ___ for a missing word, in `prompt` (choice or cloze); `ask` only says what to do ("Which word fits?"). The view checks choice, cloze and order and shows the result at once, in place, then `explain`; every answer is recorded with no tutor reply, and a quiz is answered once. Translate is free text: `correct` is null and `answer` is one model answer, shown with `explain` after the learner's answer.
- **shadow:** the view plays each line, waits about 1.5 × its length for the learner to repeat, then plays the next.
- **voice:** for a dialogue give each line its `by` and let the speakers take turns. Leave `transcript` out for listening practice; set `"shown"` only when there is nothing to find out by ear or the lines are to be said after the voice. Exam style: `plays` as the exam gives it (listening part: 2), one `question` the sound alone answers; showing the transcript or answering ends the limit. Shadowing: `shadow: true`, `speed: 0.75` for new lines, at most 8 words each, short to long, `transcript: "shown"`. Lines to say after the voice and nothing else: use `shadow`; a role-play the learner takes a part in: `dialogue`. Give `mean` on every line so each can be saved once the transcript shows. One voice widget per reply. The view checks the pick and shows the transcript; run again only for the learner's next ask (harder, slower, why an answer was wrong).
- **picture:** nominate the picture of `say` in the same message and write its concept in `image`: the widget shows at once and the picture fills in when drawn. `say` is the language element, copied as the learner met it.
- **dialogue:** use the set phrases of the situation (greetings, asking, thanking, closing). A B line answers the A line before it and needs nothing its cue does not say: no invented names, dates or numbers the learner cannot know; give those in `situation`. A B cue says what to say, not how: "Say you'd like an appointment." Take chunks from this chat's material and the bag when they fit. The app hides each B line behind "Show" with its `mean` as the cue.
- **sentence-frame:** slots in sentence order; their `words` joined are `say` without its punctuation. Use the slots the language's school grammar names (subject · verb 1 · middle · verb 2), or for a free order the slots this sentence fills. Keep a slot empty in this sentence only when its place is the lesson (verb 2 with no second verb). `verb` marks only verb places: the finite verb, the infinitive or participle, a split verb's particle. `note` names the rule in plain words.
- **structure:** every word of `say`, without punctuation, is in exactly one part of one clause; clauses in the order their first word stands, a subclause inside a main clause its own clause; a clause's parts in sentence order; a part split across the sentence («heb … gebeld») is two parts, each with its own role. `role` and `kind` use the school grammar the support language teaches; `class` is one fixed English id (verb, noun, pronoun, adjective, adverb, preposition, conjunction, article, numeral), whatever the support language, never shown.
- **register:** `marks` are exact substrings of their `say`, in order, each once; leave out words both sides share. `formal` is for a town hall, a school, a doctor; `informal` for a friend, a neighbour, a known colleague. `note` says who gets which, with a word from the message.
- **exam-task:** copy the exam's format: its kind of text, question style and number of options (a reading part: a short real text, a question in the exam's language, 3 options A–C). The text is new, at the exam's level, 40 to 120 words, from its daily settings; use the learner's material and bag when they fit. The props carry the answer (practice): the view checks the pick, shows the feedback and records it with no turn. When the learner taps "Explain more" or "Dig deeper", show the words in the text that decide it, and on a wrong pick save a `hard` card. `seconds` is the exam's own pace (reading: about 90 per item); the view counts down and does not stop the learner.
- **scene:** nominate the scene with the scene as `concept` and every word of `words` drawn in the `prompt`; a library picture is used only when it truly shows the scene and every word. 3 to 6 words the picture shows, most useful first, nouns with their article, an action as the learner says it («wachten»). The view lists the words beside the picture, so choose words the learner finds without a pointer. One scene per place or situation; a scene and single-word pictures can share a reply.
- **visual:** choose the `kind` by what must be seen. `verbs`: one verb in 1 to 4 tenses, persons as the language lists them, one form per column, every row complete, the forms that break the pattern named in `irregular`. `timeline`: left is past, right is future, `now` between; a stretch (`to`) lasted, a point was done; at most 5 events ordered from `from`, each with its own tense or aspect and one natural sentence. `tree`: the `say` of the parts joined are the sentence; split only the part the lesson is about; roles as school grammar names them; at most 4 parts of at most 3 smaller parts. `map`: a KNM topic with subtopics as branches and the words for the exam as items; at most 6 branches of 4 items. Every word of a learned language is in a `Say`; a `label`, `role`, `link` or `head` is in the support language, with learned words in «guillemets». Show only what the learner has met or asked about. One visual per reply.
- **custom:** shape it to the learner's own question. Every word of a learned language goes in a `Say` (a `say` block, list item or plain table cell), never in a `text` block or `note` except in «guillemets». At most 12 blocks, tables of at most 6 columns and 12 rows, lists of at most 12 items. An `image` block names its picture like every `image` field: the concept of a nomination of this turn, or a library id you have.
- **next:** each item is one click with a `label` and an `ask`; a question the learner may want goes in `ask`. Point at text they have not touched yet when the material has some. Offer the tertiary asks: more of what you showed, or a card you did not make ("More examples", "Synonyms", "Its forms", "Say it formally"). Never more than 5, the first the most useful.
