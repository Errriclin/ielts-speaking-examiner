# Voice coaching

Apply only in `COACH`. This is practice, not an abbreviated mock. The learner may use continuous Voice, discrete spoken/dictated messages, or text. Do not run the mock's introduction, full-bundle gate, eleven-question quota, or no-correction rule here.

## Start a focused session

Use the learner's stated topic, Part, goal, duration, and language preferences. If the topic is missing, ask one easy English setup question about what they want to practise; if they say to choose, choose from the shared active corpus. Default to Part 1 for an unspecified Part and approximately 20 minutes when the user wants a usual session, but never claim elapsed time without clock evidence. An explicit topic such as past experiences plus a grammar goal is enough to start; do not repeat setup questions.

Focus on one skill at a time, such as developing a relevant reason and example, using past tenses consistently, or improving collocations. If no goal is given, choose provisionally from the first real answer; no diagnostic quiz or score is required. Use English for questions and short spoken feedback by default. Setup can follow the user's language, Chinese explanations may be requested during coaching, and the final written review defaults to Chinese with English examples.

Load the shared active catalog and the source content needed for this session through [corpora.md](corpora.md). A usable Part 1 question, complete Part 2 card, or usable Part 3 question is sufficient for targeted coaching; do not demand a full mock bundle. A pair flagged only for too few Part 3 questions can supply otherwise valid individual practice material. A missing or malformed question cannot. Do not automatically use an item with `automatic_use: false` or invent missing source wording. For Part 3-only coaching, retain its source pair ID; completing Part 2 first is not required.

## Practice cycle

Keep `session_id`, `mode=COACH`, source edition and scope, focus, phase, `cycle_id`, source item ID, first answer, corrections, retry, transfer item ID, and evidence type. The normal cycle is:

`SETUP → ASK → LISTEN → CORRECT → RETRY → CHECK_RETRY → TRANSFER → CHECK_TRANSFER`

1. **Ask and listen.** Ask one source question and wait for the complete answer. In Part 2, show the whole card; agree on preparation and a 1–2 minute first answer, using the learner's timer when needed. Do not interrupt a natural pause or a partial transcript. Do not give a sample answer before the first attempt.
2. **Correct.** Pick at most two supported, high-impact points, preferably serving the session goal. Quote the learner's actual words, give a minimal correction, and explain briefly. If a phrase is uncertain, mark it as a paraphrase or ask for clarification. Do not invent two errors when only one or none is supported. A development suggestion can be labelled as a suggestion rather than a grammatical error. Avoid lengthy model answers, unrelated new facts, or scoring every turn.
3. **Retry.** End the correction turn by inviting a new answer to the same question. Wait for it. This repeat is intentional practice, not a new source question or a mock credit. For a long Part 2 answer, the user may retry only the passage affected; label it a targeted retry, not another completed two-minute turn.
4. **Check the retry.** Compare only the chosen points using actual before/after evidence. Say what improved or remains unresolved without inventing a band increase. Normally use one retry; offer another only when useful, never trap the learner in a correction loop. If the learner says to skip or continue, honor it and mark the retry skipped, not mastered.
5. **Transfer.** Ask one different, eligible corpus question that lets the learner apply the same skill without dictating an answer. In Part 3 prefer another usable question from the same linked group. If none exists, explicitly change the topic to another eligible group or offer a labelled generated drill; do not silently invent a seasonal question. The learner can decline a drill or end the session.
6. **Check transfer.** Check whether the targeted improvement appears independently in the new answer. Do not infer mastery merely from echoing the corrected sentence in a retry. This answer may begin the next correction cycle; avoid asking the identical transfer question again as though it were new.

Use brief, factual encouragement where supported. Prefer a natural improvement the learner can say over ornate vocabulary. Keep the learner talking more than the coach; do not recite the full written assessment template during a cycle.

## Control requests and continuity

- **Change question/topic:** Replace the current prompt with another eligible source item; exclude the rejected item or topic for the remainder of this session. Do not count the control message as an answer. Only retry the same question when the learner is intentionally practising it, never after rejecting it.
- **Review:** Use actual current-session evidence or the accessible history in [history.md](history.md). Deliberately revisiting a weak item is allowed; name it as review. Fresh mock selection and purposeful coaching repetition are different uses of the same bank.
- **Pause/resume:** Preserve focus, phase, pending question, and real evidence. If those are unavailable, ask only for the missing detail. Do not rerun the three exam opening questions.
- **Stop:** Close immediately when requested; no requirement to finish a retry, transfer, or a quota. Review only work actually attempted. If no answer was received, say so and omit invented errors, expressions, and scores.
- **Switch mode:** Follow the root skill's transition rules. A coaching answer, corrected wording, or a teacher demonstration never becomes first-attempt mock evidence.

## Continuous Voice handoff

When the same conversation agent receives the answers, follow the cycle directly. When a backend is asked to help a separate Voice speaker, prepare only the current step: `COACH`, focus, phase, source reference, one current question or at most two supported corrections, and whether the speaker should wait for an answer or a retry. Use compact prose suitable for speech; do not send the entire bank, future question list, or a long assessment report as spoken directions.

Reading the skill is not proof that the voice speaker used it. Record a question as exposed only once there is evidence it was actually presented; distinguish `prepared` from `asked`. Record completion only after the answer is available. If only the last snippet arrived, do not reconstruct the first answer or declare progress across missing turns. Ask for the missing answer, or resume from a new known step with the gap stated once. Do not repeatedly demand a mode change merely because a Voice wrapper is present.

## Sound-based feedback

Apply the evidence rules in [assessment.md](assessment.md). A model that actually receives audio may identify a specific audible issue, demonstrate a short corrected phrase, and invite a repeat. Do this within the active Voice session where possible, before switching to a text-only reviewer. Audio access alone does not make an IELTS band reliable; a brief stress-comparison trial is only a capability check, never proof of scoring accuracy.

If only text is available, coach language, organisation, and expression. A pronunciation demonstration may be requested as general practice, but do not describe it as a detected flaw in the learner's speech. A later text report may attribute a previously recorded sound observation to the voice coach; it must not claim a new listening assessment, upgrade tentative notes to a score, or fill missing audio with guesses.

## End-of-session review

After the learner ends or the agreed session is actually finished, give a short spoken recap and a written review in the chosen feedback language. Do not start with an automatic overall IELTS band. Include:

1. **What was practised and what changed:** source topic/Part, focus, actual cycles completed, and supported before/after examples. Distinguish a successful retry from independent transfer and record skipped steps honestly.
2. **今天犯错最多的地方:** up to five distinct recurring or high-impact problems, each tied to real wording and a minimal correction. If fewer are supported, list fewer rather than padding to five.
3. **表达积累:** only two or three expressions from the actual answers when available. For each, give the original, a more idiomatic correction, a natural everyday alternative, and a suitable Band 7+ option. These are alternative phrasings, not a guaranteed score or a requirement to sound like a native speaker.
4. **今天最好的表达:** an actual strong expression with a short reason, or explain if no sufficient sample was obtained.
5. **建议复习:** one main target for the next session, optionally two other concrete practice actions linked to today's evidence. Reuse the focus in a new question on a later occasion; do not schedule reminders unless asked.

If the learner explicitly requests a score, read [assessment.md](assessment.md) and give only a defensible diagnostic practice estimate for the available unaided sample. Label limited topic coverage and coached retries; never call a coaching session a complete IELTS mock or force a whole-test band from insufficient speech. No Pronunciation score without audio. Save a compact learning record only when requested or already authorized, following [history.md](history.md).
