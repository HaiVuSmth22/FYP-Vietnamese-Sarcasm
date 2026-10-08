# Vietnamese Sarcasm and Irony Annotation Guidelines

**Version:** 1.0 (revised after Pilot 1)  
**Unit of annotation:** One Vietnamese social-media comment, together with only the context supplied in the annotation item.  
**Final model classes:** `SINCERE` (0), `SARCASM_IRONY` (1).  
**Annotation-only option:** `UNCERTAIN` (excluded or separately reviewed before modelling).

## 1. Purpose and central question

Determine whether the comment expresses **sarcasm or irony** rather than a **sincere** statement. Ask: *Does the intended meaning involve a clear ironic contrast, mock praise, ridicule, or other supported non-literal reversal?* Do not infer sarcasm solely from emoji, negativity, slang, exaggeration, or humor.

**Important:** Sarcasm and irony are **combined**; annotators must **not** choose between them.

## 2. Label definitions

### `SARCASM_IRONY`

Choose when the supplied text/context provides reasonable evidence of sarcastic/ironic meaning, such as:

- mock praise that communicates criticism: *“Dịch vụ 5 sao, chờ có mỗi 3 tiếng.”*
- positive wording at odds with a negative situation: *“Tuyệt vời, lại mất điện đúng lúc làm bài :)).”*
- clear ironic contradiction, ridicule, or deliberately implausible statement whose ironic intent is supported by the comment/context: *“Quá rẻ cho một siêu xe, làm cả ba đời chưa mua được.”*

Do **not** rely on a stereotype that particular emoji or slang always indicates sarcasm.

### `SINCERE`

Choose when the writer appears to mean what they express directly, **including direct criticism, jokes, emotional comments, and factual statements** without a supported ironic contrast.

- *“Mình rất thích bài hát này.”* — direct praise
- *“Hai bình luận viên bình luận chán quá.”* — direct criticism
- *“Xem cười sặc 😂.”* — amusement/humor is not by itself sarcasm

### `UNCERTAIN`

Choose when both sincere and sarcastic interpretations remain plausible and the supplied material cannot resolve them, or essential context is missing.

- *“Đẳng cấp vãi.”* — could be praise or mockery depending on the target
- *“Đỉnh.”* — may need surrounding video/article context
- *“Hay đấy.”* — may be sincere or mocking

Do **not** assign `SINCERE` just because sarcasm cannot be proved when a credible sarcastic reading remains and context is missing. Conversely, absence of a sarcastic cue does not make every understandable ordinary statement `UNCERTAIN`.

## 3. Context rule — strengthened after Pilot 1

**Missing context was the main source of Pilot 1 disagreements.** Annotators may use only:

1. The comment text.
2. The same explicitly provided context shown to both annotators (e.g., a short article/video description, or parent-comment text if included).

Do not consult the YouTube video, article, creator identity, unrelated comments, or remembered memes independently unless such context is **part of the standardized annotation item for both annotators**. Otherwise, two raters may label using different information.

When a judgment relies on missing video/article/context, mark `UNCERTAIN` and write `Lacking context` in notes. If context is later provided for adjudication, document this separately; **do not overwrite the original independent labels**.

## 4. Humor versus sarcasm — strengthened after Pilot 1

**Humor alone is not sarcasm.** Laughter markers (`:))`, `=))`, `😂`, `🤣`) can express amusement, friendliness, or mockery.

- *“Nghe đến đoạn sửa lyric tự chạy trong đầu các bạn ạ =))))”* → `SINCERE` if it simply describes a funny reaction.
- *“Dịch vụ nhanh thật, có mỗi 3 tiếng.”* → `SARCASM_IRONY`, because the mock praise conflicts with a long wait.
- A playful or absurd statement without a clear sarcastic target/contrast → usually `SINCERE`, or `UNCERTAIN` if a sarcastic reading is genuinely plausible but requires missing context.

Do not classify all exaggeration, jokes, puns, or figurative language as sarcastic.

## 5. Other tricky cases

| Case | Rule |
| --- | --- |
| Emoji/emoticons | Use as supporting evidence only; `😂` or `:))` does not by itself indicate sarcasm. |
| Rhetorical questions | Not all are sarcastic. Label `SARCASM_IRONY` only when intended ironic/mock criticism is supported. |
| Direct negative statements/insults | Can be `SINCERE`; negativity is not sarcasm. |
| Strong praise | Can be `SINCERE`; intensity is not proof of irony. |
| Slang/Teencode | Read naturally; do not use slang as an automatic sarcasm cue. |
| Very short comments | Choose `UNCERTAIN` when essential context is missing, not on word count alone. |
| Cultural references/memes | If understanding intent depends on unstated background knowledge, choose `UNCERTAIN`. |
| Mixed signals | Prefer `UNCERTAIN` if opposing interpretations remain defensible. |

## 6. Annotation procedure

For each item:

1. Read the full text and standardized context, if any.
2. Determine the literal meaning and likely intended meaning.
3. Look for a supported sarcasm/irony signal, especially a target and non-literal contrast.
4. Explicitly check whether the comment is **only humorous** or **only critical**.
5. If meaning depends on missing context, select `UNCERTAIN` rather than guessing.
6. Select `SARCASM_IRONY`, `SINCERE`, or `UNCERTAIN`.
7. Optional: record confidence (`High`, `Medium`, `Low`) and a concise note if difficult.

Use consistent notes where useful: `Lacking context`, `Humour vs sarcasm`, `Mock praise`, `Emoji ambiguity`, `Very short comment`, `Slang/Teencode`, `Cultural reference`, `Rhetorical question`, `Other`.

## 7. Independence and agreement

- Both annotators see the same items, in the same information format, and label **independently**.
- Do not compare or discuss decisions until both annotation rounds are complete.
- Preserve original annotator files unchanged.
- Calculate **raw agreement** and **Cohen's kappa before adjudication** using all three annotation choices.
- Additionally report binary agreement/kappa on the subset where neither annotator chose `UNCERTAIN`. Clearly state the reduced sample size and that this conditional estimate is **not** directly comparable with full-set kappa.
- Record counts/rates of `UNCERTAIN` from each annotator.

Pilot 1 reference (88 comments): raw agreement **68/88 = 77.3%**; 3-category κ **0.579**; binary-subset κ **0.701** on **80** comments. These values are descriptive pilot results, not proof that the full annotation will achieve the same reliability.

## 8. Disagreement resolution

1. Create a comparison table containing both original labels and an agreement indicator.
2. Record why each mismatch occurred, especially `Lacking context` or `Humour vs sarcasm`.
3. Review the guideline and, where permitted, any standardized context.
4. Record a separate adjudicated `Final Label`. Do not overwrite either original label.
5. If intent cannot be resolved using the available evidence, retain `UNCERTAIN` and exclude from the final binary modelling data.
6. **Never compute inter-rater kappa from adjudicated labels.**

## 9. Final modelling labels

| Annotation outcome | Numeric label |
| --- | --- |
| `SINCERE` | `0` |
| `SARCASM_IRONY` | `1` |
| `UNCERTAIN` / unresolved | Exclude from the final binary set; record the exclusion count. |

## 10. Pilot 2 and versioning

Pilot 2 uses **new comments**, independent annotations, and this revised guideline. Review whether disagreement reasons changed; do not only compare a headline kappa score. Freeze the guideline for full annotation after assessing Pilot 2, and record any subsequent changes with a version number and reason.

### Final reminder

1. Do not guess when context is missing.
2. Humor alone is not sarcasm.
3. Emoji alone is not sarcasm.
4. Negative sentiment is not automatically sarcasm.
5. Strong praise is not automatically sincere or sarcastic.
6. Keep the original independent labels unchanged.
