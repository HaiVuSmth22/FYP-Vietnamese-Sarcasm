# Vietnamese Sarcasm and Irony Annotation Guidelines

**Version:** 2.0 — updated after Pilot 2 (October 2026)  
**Project:** Sarcasm and Irony Detection in Vietnamese Social Media  
**Unit of annotation:** One Vietnamese comment, with the **same standardized context** made available to both annotators  
**Annotation labels:** `Sincere`, `Sarcasm/Irony`, `Uncertain`  
**Final model classes:** `0 = Sincere`, `1 = Sarcasm/Irony`; `Uncertain` is an annotation-only option.

## 1. Purpose

Decide whether a comment communicates **sarcasm or irony** rather than a sincere meaning. Sarcasm and irony are **combined into one class**; annotators do not need to distinguish them.

**Core question:** Is there reasonably supported evidence that the author's **intended meaning contrasts with the literal wording or expectations**, such as mock praise, ironic criticism, or ridicule?

A comment may be funny, negative, exaggerated, informal, or full of emojis without being sarcastic.

## 2. Annotation labels

### `Sincere`

Use when the commenter appears to mean what they say, including direct praise, criticism, factual statements, genuine questions, and ordinary jokes without supported ironic intent.

Examples:

- *“Cảm ơn bạn đã chia sẻ video, rất hữu ích.”* — genuine appreciation.
- *“Mình không đồng ý với quyết định này.”* — direct criticism, not sarcasm.
- *“Xem đoạn này cười xỉu 😂.”* — expresses amusement; laughter alone is not sarcasm.

**Rule:** A humorous comment is **not automatically** `Sarcasm/Irony`.

### `Sarcasm/Irony`

Use when the text and any **shared permitted context** provide clear, defensible evidence of ironic or sarcastic intent. Common patterns include:

- **Mock praise:** positive words used to criticize an obviously negative situation.
- **Ironic contrast:** literal wording conflicts with the event or implied meaning.
- **Ironic ridicule:** a statement or rhetorical question conveys criticism through an evident non-literal meaning.

Examples:

- *“Nhanh ghê, đợi có mỗi ba tiếng.”* — mock praise of a very long wait.
- *“Tuyệt vời, lại mất điện ngay lúc nộp bài.”* — positive wording contradicts a negative event.
- *“Thông minh thật, vượt đèn đỏ ngay trước mặt cảnh sát.”* — praise used ironically to criticize a poor decision.

**Rule:** Identify the **target** and **evidence of irony**; do not rely only on your impression that something is funny.

### `Uncertain`

Use when both sincere and sarcastic readings remain plausible **after following the shared context procedure**, or the evidence needed to decide is unavailable.

Examples:

- *“Đỉnh thật.”* — may be genuine admiration or mocking praise depending on the situation.
- *“Hay quá.”* — could be positive feedback or irony without further context.

Do not use `Uncertain` merely because the comment is short or the annotator feels slightly unsure. Use it when the **interpretation genuinely cannot be resolved** from the allowed evidence.

## 3. Shared video context — mandatory procedure for both annotators

Pilot 2 showed that the researcher who selected the videos often knew background information that the second annotator did not. **The two annotators must have the same opportunity to use context and follow the same procedure.**

Each annotation item should provide:

- `ID`: a stable identifier.
- `text`: the original comment, including emojis and punctuation.
- `video_link`: a clickable link to the source YouTube video (or a shared `source_link` for future news comments).
- `label`, `confidence`, and `notes`: the annotator's independent responses.

**Context-review steps:**

1. **Read the comment first**, without guessing from personal familiarity with the video or creator.
2. If the intent is clear from the comment itself, label it directly.
3. If intent depends on the video's subject, **open the provided `video_link`** and inspect the relevant available context (at minimum the title/description; view the relevant video segment if necessary and feasible).
4. Use **only the comment and shared, accessible source context**. Do not rely on private knowledge, memories of the video, hidden discussions, or unrelated comment threads that the other annotator has not been instructed to review.
5. If context is inaccessible, insufficient, or impractical to establish consistently, and the label depends on that context, choose `Uncertain` and explain briefly in `notes`.
6. When context changes the interpretation, note the **source of the context**, e.g. `Context used: video topic` or `Context used: segment 01:20–01:40`. Do not record a suggested label in the shared context material.

For large annotation rounds, the project owner should ideally provide **the same neutral, one- or two-sentence video description or relevant segment** to both annotators, in addition to `video_link`, so that contextual review is consistent and time-efficient. Do not describe the video as “sarcastic” or hint at the expected label.

**Important:** Merely giving the same URL does not prove both annotators watched or understood the same material. Follow the same context-review protocol, and record when external context was essential.

## 4. Distinguishing ordinary humour from sarcasm

This was one of the main interpretation difficulties in Pilot 2. Apply the following test:

1. **What is literally being said?**
2. **What does the commenter appear to mean?**
3. **Is there a specific supported contrast, mock praise, ironic target, or ridicule?**
4. **Would the comment still just be a joke or expression of amusement without that contrast?**

| Example comment | Recommended label | Reason |
| --- | --- | --- |
| “Xem tới đây cười muốn rớt điện thoại 😂” | `Sincere` | Genuine amusement; no ironic reversal. |
| “Mạng khỏe ghê, năm phút rớt một lần.” | `Sarcasm/Irony` | Mock praise conflicts with repeated disconnections. |
| “Dở quá, không thích.” | `Sincere` | Direct negative opinion, not irony. |
| “Đỉnh thật.” | `Uncertain` if context cannot resolve it | Could be genuine or mocking. |
| “Tuyệt vời, lại kẹt xe hai tiếng nữa rồi 🙃” | `Sarcasm/Irony` | Clear positive–negative contrast; emoji is secondary evidence. |

Do not equate sarcasm with joking, trolling, slang, memes, laughter markers (`:))`, `=))`, `😂`), or negativity.

## 5. Other decision rules

| Situation | Rule |
| --- | --- |
| Emoji or emoticon | Supporting cue only; never sufficient on its own. Preserve it in `text`. |
| Exaggeration | Not necessarily sarcasm; look for ironic intent. |
| Direct insults or criticism | Usually `Sincere` unless clearly delivered ironically. |
| Strong praise | May be sincere or mock praise; decide from evidence. |
| Rhetorical questions | Label as sarcastic only if the ironic target/meaning is supported. |
| Cultural references, memes, slang | Interpret only if allowed shared evidence supports the meaning; otherwise `Uncertain` when essential. |
| Very short comments | Do not automatically label `Uncertain`; apply the ordinary evidence test. |
| Mixed or contradictory cues | Use `Uncertain` if competing interpretations remain reasonable after context review. |
| Context contradicts literal wording | May support `Sarcasm/Irony`, but note that video context was needed. |

## 6. How to fill in the annotation sheet

**Keep the original column names generated by `01_data_collection.ipynb`:**

| Column | What to enter |
| --- | --- |
| `ID` | Pre-generated; do not edit. |
| `text` | Original comment; do not rewrite, translate, or remove emojis. |
| `video_link` | Provided source link; open when context is needed. Do not edit. |
| `label` | Select `Sincere`, `Sarcasm/Irony`, or `Uncertain`. |
| `confidence` | Select `1 - Low`, `2 - Medium`, or `3 - High`. |
| `notes` | Brief reasoning when helpful, especially for ambiguity, cultural meaning, or use of video context. |

### Confidence scale

- **`3 - High`**: Clear evidence; very little ambiguity.
- **`2 - Medium`**: A reasonable judgment, but some ambiguity remains.
- **`1 - Low`**: Weak or conflicting evidence; limited context.

Confidence is the annotator's subjective assessment, **not a model probability**. A low-confidence label may still be `Sincere` or `Sarcasm/Irony` when one reading is preferable; choose `Uncertain` when evidence cannot support a defensible choice.

Optional notes examples: `Humour only`, `Mock praise`, `Ironic contrast`, `Context used: video title`, `Context used: 01:20–01:40`, `Insufficient context`, `Cultural reference`, `Mixed interpretation`.

## 7. Independent annotation and consistency

1. Both annotators receive **identical comments, IDs, links, instructions, and available neutral context**.
2. Annotate **independently** without consulting each other or looking at the other person's labels.
3. Use **separate copies** of the workbook or Google Sheets files. Two tabs in a shared workbook do not by themselves prevent visibility of each other's labels.
4. Keep `ID` and row order intact to simplify comparison.
5. Finish and freeze the original labels **before** any comparison or adjudication.
6. Calculate original raw agreement and **Cohen's kappa on the three annotation choices**, and report the number of `Uncertain` labels. If binary-only subset agreement is reported, provide its sample size and note that it uses a selected subset.

## 8. Disagreement handling and final labels

- Preserve both annotators' original judgments.
- Compare and discuss disagreements **after** independent annotation is complete.
- Record one adjudicated final label separately; it must not overwrite either original label.
- If reliable interpretation remains impossible even with shared permitted context, retain `Uncertain` rather than force a binary label.
- Do **not** recalculate inter-annotator agreement using adjudicated labels; kappa measures the **original independent decisions**.

For Pilot 2, all 40 comments were adjudicated. The original independent agreement remained **22/40 (55%)**, with three-category **Cohen's κ ≈ 0.284**. Report this original reliability result separately from the resolved final labels. The review suggested two prominent issues—**different judgments about humour versus sarcasm** and **unequal knowledge of video context**—but these are interpretive findings rather than proven causal effects.

## 9. Preparing the binary model dataset

| Adjudicated annotation | Training label |
| --- | --- |
| `Sincere` | `0` |
| `Sarcasm/Irony` | `1` |
| `Uncertain` | Exclude from the two-class training/evaluation dataset, and report how many were excluded. |

For the planned **text-only classifiers** (TF-IDF + Logistic Regression, PhoBERT, and XLM-R), do not feed `video_link` into the model. Keep source links as private annotation metadata and for qualitative error analysis.

**Potential limitation:** A comment labeled using video-specific knowledge can be ambiguous when a text-only model sees only `text`. Record context-dependent cases in `notes` where feasible, and report/analyze them separately when interpreting model errors. Do not imply that the text-only model had access to the video.

For the emoji-handling ablation, **preserve the original comment text and emojis at collection and annotation time**. Implement any emoji conversion/removal in separate experimental preprocessing, not in the annotation source.

## 10. Data handling and version control

- Store `.env` and YouTube API credentials locally only; `.gitignore` should exclude `.env`.
- Keep raw comment datasets and completed annotation sheets private, in line with the project's ethics approval and platform requirements.
- Avoid including account names or other unnecessary personal identifiers in annotation exports.
- Save this document as `annotation/annotation_guidelines.md` and identify it as **Version 2.0** in the methodology and experiment log.
- Use these rules unchanged for the next independent validation sample; record any later guideline revisions with a new version number.

### Quick decision checklist

Before submitting a label, ask:

- Did I consider the **same permitted context** available to the other annotator?
- Is the comment **sarcastic/ironic**, or merely **funny, negative, or exaggerated**?
- Can I identify the target and evidence for ironic intent?
- If the comment requires missing context, did I choose `Uncertain` rather than guessing?
- Did I preserve the original text and record context use when it mattered?
