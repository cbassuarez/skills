---
name: deepen
license: MIT
description: Make a task deeper, not bigger. Names what a top professional in the field would do that the request leaves out, the rawest material they'd start from instead of digested summaries, the specific methods and tools they'd use, and an outside check that would show the result is right — then rewrites the prompt to ask for exactly that, and with --go runs the rewrite immediately. Use when the user types /deepen, asks for a deeper rather than bigger version of a task, asks what a top professional would actually do differently, or pastes the prompt that begins "i want a deeper version of the above task".
---

# deepen

This replays a prompt the user wrote and uses all the time:

> i want a deeper version of the above task, not a bigger one. Before rewriting it: a. say what a top professional in this field would do here that I'm not asking for; b. name the rawest material from where they would start instead of what has already been digested for me; c. name the specific methods and tools they would use; d. say what, other than you or me, would show the result is right. Then rewrite my prompt to ask for exactly that.

That prompt is the spec. The rest of this file is how to do it well.

**Arguments:** $ARGUMENTS

## 1. Find the task

- If the arguments contain task text (anything besides `--go`), that is the task.
- Otherwise the task is the most recent substantive request in this conversation: what the user asked for, not your answer to it. If an answer already exists, keep it in view as evidence of what the shallow version looked like, and point at the places it leaned on digested material.
- If there is neither, ask for the task in one line and stop.
- `--go`, or the argument `go` on its own, means run the rewritten prompt after writing it (step 4).

## 2. Diagnose: deeper, not bigger

"Bigger" adds deliverables, sections, options and coverage. "Deeper" keeps the deliverable about the same and raises the standard behind it: closer to the source, sharper method, and a check that could fail. Test every item in a–d against this question: *does it change how the work is done, or only how much of it there is?* Cut anything that only adds amount.

Name the field as a specific practitioner, such as "a forensic accountant", "a mastering engineer" or "an appellate litigator", rather than "an expert". If the task straddles two fields, pick the one whose standards the result will actually be judged by, and say why.

**a. What they'd do that the user isn't asking for.** These are the moves that separate a top practitioner from a competent one on this exact task: what they check before starting, what they refuse to take on faith, which question they reframe. Each one must be concrete enough that someone could tell whether it was done. "Research thoroughly" fails. "Reconcile the dashboard number against the raw billing export before explaining it" passes.

**b. The rawest material.** Name the actual artifacts: the dataset, the source file, the stems, the statute text, the original paper and its supplementary data, the user's own logs or drafts, the people to interview. For each one, name the digested thing it replaces (a summary, a dashboard, a blog post, a previous AI answer, your own memory of the topic) and say where to get it. If only the user can get it, say so. That is often the most useful line in the whole output.

**c. Methods and tools.** Give named techniques, standards, instruments and software, each with what it is for in this task. Write "cohort retention table by signup month", not "analysis", and "ITU-R BS.1770 loudness meter", not "check levels". Prefer what a practitioner would actually reach for over what sounds impressive.

**d. What would show it's right, other than you or the user.** This has to be something that can come back *no*: a test that runs, a figure that reconciles to an independent source, a prediction that next week's data can falsify, a practitioner or real user who is not in this conversation, a standard with a measurable threshold, or a replication. State the pass condition up front. "It reads well" and "the user is happy" don't count, because those are exactly what the prompt excludes.

## 3. Rewrite the prompt

The rewritten prompt is the deliverable. It should:

- Stand on its own. Don't write "the above"; restate the goal in one sentence.
- Keep the original deliverable or narrow it. If it asks for more *things* than the original did, cut it back.
- Name the raw inputs to use, and tell the reader to ask for any it can't access instead of quietly substituting digested ones.
- Lay out the methods from (c) as steps, in the order a practitioner would do them.
- End with the check from (d) and its pass condition, and require a report of that check's result, including if it fails.
- Speak in the user's voice, written as their next message in the first person, inside a `text` code block so it can be copied as-is.

## 4. Output

Use this shape. Give a few bullets per section and no preamble; the analysis should be as tight as the rewrite asks the work to be.

````markdown
**Field:** <specific practitioner>, <one clause on why this field>

**a. What a top <practitioner> would do that you're not asking for**
- …

**b. Rawest material**
- <raw artifact> instead of <digested thing>. <where to get it, or "only you have this">

**c. Methods and tools**
- <named method or tool>: <what it's for here>

**d. What would show it's right (not you, not me)**
- <check>. Passes if <condition>.

**Rewritten prompt**
```text
…
```
````

Then:

- **Without `--go`:** stop after the rewritten prompt and add one line offering to run it, noting that `/deepen --go` runs it straight away next time.
- **With `--go`:** write "Running it." and carry out the rewritten prompt now, in this turn, as if the user had just sent it.
  - Fetch the raw material yourself wherever your tools allow.
  - Where you can't, say plainly what's missing, then either pause for it or go on with a clearly labelled stand-in. Don't quietly fall back to digested material, because that defeats the point.
  - If the check from (d) can run here, run it and report the result as it came out, pass or fail.
  - If it needs someone or something outside this conversation, end by telling the user exactly what to send to whom, and what result counts as a pass.

## Calibration

These two examples show how fine-grained each item should be. They are not a template, so don't reuse their contents.

**Task: "write up why churn went up last quarter for the board"**
- Field: SaaS revenue analyst, not a writer, because the board will judge the numbers rather than the prose.
- a: Split voluntary from involuntary churn (failed payments) before explaining anything, and check whether the rise is a mix shift toward smaller customers rather than worse retention.
- b: The raw subscription-event export and the cancellation free text, instead of the dashboard's churn percentage.
- c: A cohort retention table by signup month, logo churn vs revenue churn, and hand-coding a sample of 100 cancellation reasons.
- d: Cohort totals reconcile to the billing system's MRR movement within 1%, and the stated cause predicts which cohorts churn next month.

**Task: "make my mix sound more professional"**
- Field: mastering engineer.
- a: Level-match before comparing anything, because louder always sounds better. Check mono compatibility, and choose the release platform's loudness target before touching the limiter.
- b: The unmastered 24-bit WAV bounce or the stems, instead of an MP3 and a description of how it sounds. Only the user has these.
- c: Two or three commercial reference tracks in the same genre, loudness-matched; a BS.1770 meter for integrated LUFS and true peak; spectrum comparison against the references; a mono fold-down.
- d: The meter reads around −14 LUFS integrated with true peak at or below −1 dBTP for streaming. In a level-matched blind A/B, a listener outside this conversation picks the revision more often than not, and the mix holds up on earbuds, in a car and on laptop speakers.
