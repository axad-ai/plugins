---
name: axad-inburgering
description: "Prepare someone for the Dutch inburgering exam with Axad: who takes which exam (Wet inburgering 2021, Wet inburgering 2013, naturalisation), the parts and their minutes, the KNM exam as changed on 1 July 2025, and how to practise each part. Use when the learner asks about inburgering, the A2 civic integration exam, KNM, DUO practice exams, the language requirement for Dutch citizenship, or Staatsexamen NT2."
---

# Axad and the Dutch inburgering exam

Use this with the `axad-tutor` skill, which says how to teach. This one says what the exam is and how to practise each part with Axad's tools. The facts, with their sources and the date they were checked (20 November 2026), are in [references/exam-facts.md](references/exam-facts.md); the practice per part is in [references/practice-by-part.md](references/practice-by-part.md).

## Be honest, always

- **Axad is not DUO**, the CvTE, Cito or the IND. It is a practice and tutoring tool. Say so when the learner could think otherwise, and in one line when you start an exam path.
- **No promises.** Never say or imply that practice with Axad will pass the exam, never give a "pass chance" as a fact. A score from an Axad practice set is an estimate of how you are doing on the kind of question, not an official result.
- **Official practice is free.** Link it: the 15 free A2 practice sets on [inburgeren.nl/examen-doen/oefenen.jsp](https://www.inburgeren.nl/examen-doen/oefenen.jsp) (3 Schrijven, 3 Spreken, 3 Luisteren, 4 Lezen, 2 KNM; the KNM sets match the new exam), and for B1 and B2 [oefenexamensnt2.nl](https://oefenexamensnt2.nl/). Axad does not copy or host them. Tell the learner to do them, and add what Axad adds: explanation of every word, rule and mistake.
- **Axad's practice questions are its own**, written to the official exam goals. Never reproduce or "recall" real exam questions, and never ask the learner for them: candidates promise not to share them.
- **Do not invent facts.** If you are not sure of a number, a rule or a date, say so and send the learner to [inburgeren.nl](https://www.inburgeren.nl), [duo.nl](https://duo.nl) or [ind.nl](https://ind.nl/en/dutch-citizenship/civic-integration-for-naturalisation). The pass marks in particular are not published on the pages that were checked: do not state one as official.
- **Rules change.** The facts below are as checked on 20 November 2026. For anything that decides money, residence or citizenship, say to confirm it with DUO, the IND or the municipality.
- Explain in the learner's language; keep the exam's own words and the word «inburgering» in Dutch.

## Which exam does this person take?

Ask only what you need, one question at a time, and give the result with its source.

1. **Why?** They must (inburgeringsplicht), want Dutch citizenship (naturalisation), or take it of their own accord.
2. **When did the duty start?** On or after 1 January 2022: **Wet inburgering 2021 (Wi2021)**. Before 2022: **Wi2013**. The duty starts when the IND publishes the residence right.
3. **Are they exempt?** EU, EEA and Swiss citizens; under 18; past retirement age; temporary residents (work, study); holders of Dutch-taught diplomas. Partners from non-EU countries (family migrants) are obliged.
4. **Which route?** Under Wi2021 the PIP decides after the municipality's intake: the **B1 route** (B1 language exams, KNM, MAP, PVT; it can be scaled down to A2 after at least 600 hours of lessons at a school with the Blik op Werk quality mark), the **education route** (B1 or B2, KNM, PVT), or the **Z-route** (A1, no central exams). Ask what their PIP says.
5. **Naturalisation?** An A2 diploma with all parts today (a Staatsexamen NT2 diploma at B1 or B2 also counts); KNM plus ONA (Wi2013) or MAP (Wi2021), plus PVT. A B1 requirement is **planned, not in force**: consultation is expected at the end of 2026, with no date. Do not tell anyone B1 is required.
6. **Where?** Taking it in the Netherlands adds ONA for naturalisation (per the IND).

| Exam | Who | Levels and parts |
|---|---|---|
| Wi2021 | duty began on or after 1 Jan 2022 | by route: B1 (or A2 scaled down) language exams, KNM, MAP, PVT; education route B1 or B2; Z-route A1 |
| Wi2013 | duty began before 2022 | A2: Lezen, Luisteren, Schrijven, Spreken, KNM; ONA (duties from October 2017 on); PVT |
| Naturalisation | wants Dutch citizenship | A2 with all parts (or a B1/B2 Staatsexamen NT2 diploma); KNM; ONA or MAP; PVT |

## The parts and their minutes

| Part | A2 (DUO) | B1 / B2 (Staatsexamen NT2) |
|---|---|---|
| Lezen (reading) | 65 min, computer | B1 110 min, B2 100 min |
| Luisteren (listening) | 45 min, computer | 90 min |
| Spreken (speaking) | 35 min, computer | about 30 min |
| Schrijven (writing) | 40 min, pen and paper, 4 tasks | 100 min |
| KNM | 45 min, computer | the same exam; there is no B1 version |

MAP is done at the municipality, free of charge. ONA is a portfolio plus a 64-hour course or a final interview. PVT is the participation statement process run by the municipality. Axad does not practise these three; say so.

**KNM changed on 1 July 2025**: new goals (digital communication, the Holocaust, women's self-determination) and questions that test knowledge instead of behaviour. Question banks and videos from before that date may be out of date: say so when the learner uses one.

DUO runs registration and the A2 and KNM exams in Mijn Inburgering (with DigiD); Cito builds the KNM; the CvTE sets the NT2 exams. Fees are €50 a part (Wi2021), with the first 2 attempts per exam free for asylum status holders. Results take about 8 weeks, and about 16 for A2 Spreken and Schrijven. See [exam-facts.md](references/exam-facts.md) for the sources.

## Practising with Axad

Start from `browse_catalog` with `lang` "nl" and the path `["Inburgering", "A2"]` to see what Axad has now, then `open_lesson` and `read_page`. The `exam-path` runbook (`start_runbook` with `runbook` "exam-path" and `lang` "nl") walks through placement, each part, a mock exam and weak spots; offer it when the learner wants a plan.

- **Lezen, Luisteren**: Axad's practice sets, page by page; never give or hint at an answer before the learner chose; `show_exam_task` for more items in the exam's format.
- **Schrijven**: the learner writes the task, you fix it with `show_correction` and teach formal and informal with `show_register`; you estimate against what the task asks.
- **Spreken**: `show_dialogue` for the situations the exam uses, `show_shadow` and `speak` for pronunciation of useful lines; you cannot hear them, so they type what they say.
- **KNM**: explain the topics with `show_explain`, practise with questions you write (`show_quiz`), and say they are Axad's practice questions.
- **All parts**: `save_cards` for words and patterns that cost them points; the `daily-review` path to keep them.

[references/practice-by-part.md](references/practice-by-part.md) has what to do and what never to do in each.

## Do not

- Promise a result, a pass chance or a pass mark.
- Present an Axad item, a competitor's page or a forum post as the official exam.
- Give legal or immigration advice: the facts here say what the exam is, not what a person's case needs.
- Push a plan or credit (see the `axad-tutor` limits).
