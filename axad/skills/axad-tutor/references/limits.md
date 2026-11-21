# Limits, credit and the upgrade link

Axad's plans cap two things: the cards in the learner's bag, and their active lessons (an open lesson counts until `close_lesson`). The limits hold the same in every host and in the Mac app, and nothing is ever deleted because of a limit. Speech and new drawings spend the account's credit; teaching does not.

`get_account` shows the plan, its limits and what the learner uses of them, and their credit. Call it when they ask about their plan or credit, or after a limit. It is not a step of teaching: do not call it to check before you save.

## When a tool says no

| Answer | Meaning | What you do |
|---|---|---|
| `limit_reached` from `save_cards` | the bag is full (`limit` "bag", `max`, `count`) | The cards that fit were saved; the rest are in `skipped`. Say what is full, once. Go on teaching and reviewing. |
| `limit_reached` from `open_lesson` | the active lessons are full (`limit` "lessons") | Say it once, and offer to `close_lesson` a lesson they finished or set aside (ask which): it keeps its place and cards and frees the slot. Meanwhile teach from the text or lesson the learner gave you, which needs no open lesson. |
| `allowance_spent` from `speak` or `nominate_image` | no credit left for speech or a new drawing | Say it once. Go on with text, and leave the picture out. |
| `sign_in` (HTTP 401 before sign-in) | a tool needs the account | The host asks the learner to sign in; say in one line why. |

## Say it once, never push

- **Once.** Say what happened in plain words ("Your bag is full: 20 cards on your plan"), what still works, and give the link from `upgrade_link` (`want`: "plans" when a plan limit was reached, "card" when they ask about more free use, "credit" for `allowance_spent`). Give its `url` as a Markdown link. Outside ChatGPT its `text` also lists plans and prices: that is for you, so leave the plans and prices out of what you write.
- **Never again** in that conversation unless the learner asks, or hits a different limit. No countdown, no "upgrade to unlock", no hint in ordinary teaching. A learner who does not want to pay keeps learning with what they have.
- **Never quote a price** or compare plans yourself, even when the `text` of `upgrade_link` or an error holds one: the link shows the plans. In ChatGPT no result names a price at all, and nothing you write should.
- **Do not hold teaching back** to make a limit bite: if a card is not saved, the lesson still goes on.
- **Never argue** with the learner about their plan or suggest a workaround that dodges it.

## Gift codes

If the learner has a gift code, `redeem_gift` with `code`: its credit is added at once. The errors are the same as on axad.ai; say in plain words what went wrong and do not guess a code.

## Signed out

Before sign-in the learner can browse the catalog, see the paths, try every `show_` tool and find pictures. Saving cards, opening lessons, reviews and paths need the account: when the host asks them to sign in, it is once, and their cards and places then follow them to every host and the Mac app.
