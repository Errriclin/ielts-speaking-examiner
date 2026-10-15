# Shared practice history and freshness

Use this reference for both modes when tracking source exposure, saving practice history, reviewing weaknesses, or avoiding questions from earlier sessions. The corpus is shared; candidate records are separate personal data and must never be placed in the skill's `corpora/`, ZIP, or public release copy.

## Session tracking and optional storage

Track the current session in conversation context by default. If the user asks to save learning records or has already enabled that behavior, use their chosen history location. Otherwise the suggested local location, only when saving is requested, is `practice-data/history.jsonl` under the current project root. Resolve it from the actual project, not from this reference or the installed skill. Do not hard-code a machine path. Do not create an empty history file just for installing the skill.

At the start of either mode, consult a user-designated history file, or an existing `practice-data/history.jsonl` in the current project. Its existence does not authorize a new write. Honor an earlier save preference in the current task. Do not search other projects, user folders, or other people's logs for practice records. If two locations are possible, prefer the one explicitly selected by the user rather than silently merging them.

Read before appending, preserve existing entries, and avoid duplicate `event_id` values on retries. Confirm a successful write before saying the session was saved. Never overwrite or truncate history to repair malformed entries; retain good records and report unreadable coverage. Respect host file permissions. If access fails, keep the session usable with an in-conversation checkpoint and state that cross-session history was not updated. An approval restriction is not permission to redirect personal records elsewhere silently.

Different projects or devices do not automatically share this file. Cross-project review requires the same explicitly accessible history; cross-device review requires the user to carry or connect the record. Installed question banks travel with the ZIP; personal practice history does not. A file not found here is not proof that the learner has never practised a question.

## Source identity and events

Use stable source keys: corpus ID + Part + group/pair ID + original one-based question position. Use the pair ID alone for a full Part 2 card, with `question_position: null`. Preserve the source edition and content fingerprint when available so a changed edition is not confused with the same numeric position. Do not invent source IDs for generated drills.

Each newline-delimited JSON record describes one source-item exposure or learning update:

| Field | Meaning |
| --- | --- |
| `schema_version`, `event_id`, `session_id` | Version 1, unique event identity, and the current practice/mock session. |
| `date`, `mode`, `corpus_id`, `scope` | Actual local date when known; `COACH` or `MOCK`; selected bank and scope. Do not invent a date. |
| `part`, `group_id`, `question_position` | Original source item; retain the linked pair ID for Parts 2/3. |
| `activity` | `first_answer`, `retry`, `transfer`, `review`, or `mock`. |
| `status` | `asked`, `answered`, `rejected`, or `user_reported_seen`. Prepared but unspoken questions are not exposure events. |
| `focus`, `issues`, `review_next` | Compact supported learning notes, not a full transcript or fabricated mistakes. |
| `evidence` | `audio`, `transcript`, or `attributed_voice_observation`; never promote text to audio. |
| `outcome` | `not_checked`, `retry_improved`, `transferred`, `needs_review`, or `skipped`, based on actual answers. |

The mock's `bundle_generation`, accepted-answer ledger, targets, and completion gates stay authoritative for that attempt; saved history is not a substitute or a source of exam credits. Rejected answers can remain as exposure records without contributing to a score. Do not store names, identity documents, raw audio, or complete answer transcripts in this compact log by default. A request for a separate report is a separate output operation.

## Choose questions for the current purpose

- **MOCK:** Exclude current-attempt rejected/exposed items and visible earlier sets as required by [exam.md](exam.md). Prefer source questions and pairs not exposed in readable prior history. When the user expressly requires unseen material, treat the available history and their reports as exclusions. If there is not enough fresh material for a complete set, explain and ask whether to reuse older material or change the bank/scope; do not silently weaken freshness or mock quotas.
- **COACH:** Repeating the current question for a retry is expected. Review items with unresolved issues deliberately; identify them as review. Use a different eligible source item for transfer. A user request for a new topic or a report that an item is unwanted takes priority over the review plan.
- **Both:** A user saying an item was already practised is authoritative even if no record exists. No readable history means only in-conversation deduplication can be verified; state this when cross-session freshness matters, without requesting another upload of the question bank. Avoid overclaiming that every item is globally unseen.
