# Vietnamese Sarcasm and Irony Annotation Guidelines

**Version:** 3.0 — revised after Pilot 3 (November 2026)  
**Project:** Sarcasm and Irony Detection in Vietnamese Social Media  
**Unit of annotation:** One Vietnamese comment, with the **same standardized context** made available to both annotators  
**Annotation labels:** `Sincere`, `Sarcasm/Irony`, `Uncertain`  
**Final model classes:** `0 = Sincere`, `1 = Sarcasm/Irony`; `Uncertain` is an annotation-only option.

**What changed in Version 3.0:** The rules for distinguishing ordinary humour from sarcasm and for using `Uncertain` have been made more explicit. Notes are now required for selected difficult decisions because Pilot 3's notes fields were left blank, which meant the annotators' reasons for disagreement could not be checked afterwards. The original Pilot 3 labels must remain unchanged; these revised rules apply to the next fresh validation sample and subsequent annotation.

## 1. Purpose

Decide whether a comment communicates **sarcasm or irony** rather than a sincere meaning. Sarcasm and irony are **combined into one class**; annotators do not need to distinguish them.

**Core question:** Is there reasonably supported evidence that the author's **intended meaning contrasts with the literal wording or expectations**, such as mock praise, ironic criticism, or ridicule?

A comment may be funny, negative, exaggerated, informal, playful, or full of emojis without being sarcastic. **Do not infer hidden sarcasm simply because a comment sounds funny, unusual, or potentially mocking.**

### Main decision rule

- Choose `Sarcasm/Irony` only when the comment and/or shared permitted context provide evidence of a non-literal or ironic meaning.
- Choose `Sincere` when the comment appears to mean what it says, including ordinary humour, jokes, playful exaggeration, direct praise, and direct criticism, with no supported ironic meaning.
- Choose `Uncertain` only when two interpretations (sincere and sarcastic/ironic) remain genuinely plausible from the allowed evidence, or when essential context needed to decide is unavailable.

The mere possibility that a comment *could* be sarcastic is not enough to choose `Uncertain` or `Sarcasm/Irony`.

## 2. Annotation labels

### `Sincere`

Use when the commenter appears to mean what they say. This includes:

- direct praise or criticism;
- factual statements and genuine questions;
- ordinary jokes, playful comments, wordplay, and expressions of amusement;
- humorous exaggeration that does not communicate a supported opposite or ironic meaning.

Examples:

- *“Cảm ơn bạn đã chia sẻ video, rất hữu ích.”* — genuine appreciation.
- *“Mình không đồng ý với quyết định này.”* — direct criticism, not sarcasm.
- *“Xem đoạn này cười xỉu 😂.”* — expresses amusement; laughter alone is not sarcasm.

**Rule:** A humorous comment is **not automatically** `Sarcasm/Irony`. If you cannot identify evidence of an ironic meaning, do not invent one.

### `Sarcasm/Irony`

Use when the text and any **shared permitted context** provide clear, defensible evidence of ironic or sarcastic intent. Common patterns include:

- **Mock praise:** positive words used to criticise an evidently negative situation.
- **Ironic contrast:** the literal wording conflicts with the event, situation, or clearly implied meaning.
- **Ironic ridicule:** a statement, joke, or rhetorical question communicates criticism through an evident non-literal meaning.

Examples:

- *“Nhanh ghê, đợi có mỗi ba tiếng.”* — mock praise of a very long wait.
- *“Tuyệt vời, lại mất điện ngay lúc nộp bài.”* — positive wording conflicts with the negative event.
- *“Thông minh thật, vượt đèn đỏ ngay trước mặt cảnh sát.”* — praise is used ironically to criticise a poor decision.

**Required check:** Be able to point to the wording or context that supports the ironic meaning. Identify the target or subject of the irony (a person, action, event, or situation) where possible. Do not use `Sarcasm/Irony` based only on a feeling that the comment is funny, rude, exaggerated, or unusual.

### `Uncertain`

Use when:

1. both a sincere reading and a sarcastic/ironic reading are reasonably supported, and neither is clearly stronger after the context procedure; or
2. essential context is unavailable, and that context could materially change the interpretation; or
3. a cultural reference, phrase, or language feature cannot be interpreted reliably using the permitted evidence.

Examples:

- *“Đỉnh thật.”* — may be genuine admiration or mock praise if the surrounding situation supports either reading and the available context does not resolve it.
- *“Hay quá.”* — may be genuine feedback or ironic criticism when the surrounding event provides conflicting clues that cannot be resolved.

Do **not** use `Uncertain` merely because:

- the comment is short;
- the comment contains slang, laughter, emojis, or informal spelling;
- the comment is a joke or seems funny;
- you are not completely certain but one interpretation is better supported;
- you personally do not like or understand the comment.

If there is no supported evidence of an ironic reading, choose `Sincere` rather than assuming that an unseen context might make it sarcastic. If both readings are genuinely supported but cannot be distinguished, choose `Uncertain`.

## 3. Shared video context — mandatory procedure for both annotators

Pilot 2 identified unequal familiarity with source-video context as a possible source of inconsistent decisions. **Both annotators must have the same opportunity to use context and follow the same procedure.**

Each annotation item should provide:

- `ID`: a stable identifier.
- `text`: the original comment, including emojis and punctuation.
- `video_link`: a clickable link to the source YouTube video (or a shared `source_link` for future news comments).
- `label`, `confidence`, and `notes`: the annotator's independent responses.
- The same neutral context material for both annotators whenever context is needed to interpret the comment.

**Context-review steps:**

1. **Read the comment first**, without guessing from personal familiarity with the video or creator.
2. If the meaning is clear from the comment itself, annotate it without seeking extra context.
3. If the intended meaning may depend on the video's subject or a particular event, use the supplied shared context material. This should be the same neutral video description or the same relevant segment for both annotators.
4. If further review is needed and permitted, open the provided `video_link` and inspect the same available material in the same order (at minimum the title/description; view the relevant segment if necessary and feasible).
5. Use **only the comment and shared, accessible source context**. Do not rely on private knowledge, memories of the video, hidden discussions, or unrelated comment threads that the other annotator has not been instructed to review.
6. If essential context is inaccessible, insufficient, or impractical to establish consistently, and the label depends on it, choose `Uncertain` and explain briefly in `notes`.
7. When context affects the decision, note the **source of the context**, e.g. `Context used: video title/description` or `Context used: segment 01:20–01:40`. Record the relevant information, not a suggested label.

For annotation rounds where video context may affect interpretation, the project owner should provide the **same neutral, one- or two-sentence video description or relevant timestamped segment** to both annotators. Do not describe the video as “sarcastic” or hint at the expected label. If no shared context has been prepared, both annotators must follow the same agreed review procedure rather than relying on personal familiarity.

**Important:** Giving both annotators the same URL does not prove that they reviewed the same context. Record when context was used and what source was checked.

## 4. Distinguishing ordinary humour from sarcasm

Pilot 3 contained **six direct `Sincere` versus `Sarcasm/Irony` disagreements**. This is consistent with the project's identified difficulty of separating ordinary humour from sarcastic meaning. However, the Pilot 3 notes fields were blank, so the exact reasoning behind each disagreement was not recorded. Do not assume that all six disagreements were necessarily caused by humour being mistaken for sarcasm.

Apply the following test in order:

1. **Literal meaning:** What do the words literally say?
2. **Likely intended meaning:** What does the commenter appear to communicate, based only on the comment and permitted context?
3. **Contrast:** Is there a supported difference between the literal wording and the likely intended meaning, or between the wording and the situation?
4. **Target:** Who or what is being praised, criticised, mocked, or ridiculed? The target may be a person, action, event, or situation.
5. **Humour check:** Could this simply be a joke, playful exaggeration, teasing, wordplay, or expression of amusement without an ironic contrast?
6. **Final decision:** If a clear ironic meaning and supporting evidence can be identified, choose `Sarcasm/Irony`. If the comment is humorous but has no supported ironic meaning, choose `Sincere`. If both readings remain reasonably supported and cannot be resolved, choose `Uncertain`.

| Example comment | Recommended label | Reason |
| --- | --- | --- |
| “Xem tới đây cười muốn rớt điện thoại 😂” | `Sincere` | Genuine amusement; no ironic reversal. |
| “Mạng khỏe ghê, năm phút rớt một lần.” | `Sarcasm/Irony` | Mock praise conflicts with repeated disconnections. |
| “Dở quá, không thích.” | `Sincere` | Direct negative opinion, not irony. |
| “Đỉnh thật.” | Depends on supported context | Genuine praise is possible; use `Uncertain` only if an ironic reading is also supported and the available context cannot resolve it. |
| “Tuyệt vời, lại kẹt xe hai tiếng nữa rồi 🙃” | `Sarcasm/Irony` | Clear positive–negative contrast; the emoji is secondary evidence. |

**Important distinction:** Sarcasm can be humorous, but humour does not automatically indicate sarcasm. The annotator must identify evidence of ironic meaning, not merely the presence of a joke or a funny tone.

Do not equate sarcasm with joking, trolling, slang, memes, laughter markers (`:))`, `=))`, `😂`), or negativity.

## 5. Other decision rules

| Situation | Rule |
| --- | --- |
| Emoji or emoticon | Supporting cue only; never sufficient on its own. Preserve it in `text`. |
| Laughing markers (`:))`, `=))`, `😂`) | Usually show amusement or tone; they do not prove that the comment is sarcastic. |
| Eye-roll or other reaction emoji | May support an interpretation but cannot determine the label alone. Check the wording and context. |
| Exaggeration | Not necessarily sarcasm; ordinary humorous exaggeration is `Sincere` unless ironic meaning is supported. |
| Direct insults or criticism | Usually `Sincere` unless clearly delivered through an ironic/non-literal meaning. |
| Strong or informal praise | May be genuine or mock praise; decide from the wording and context, not intensity or slang alone. |
| Rhetorical questions | Label as `Sarcasm/Irony` only if the ironic target and meaning are supported. |
| Cultural references, memes, slang | Interpret only if permitted shared evidence supports the meaning; use `Uncertain` if an essential reference cannot be resolved. |
| Very short comments | Do not automatically label `Uncertain`; apply the same evidence test. |
| Mixed or contradictory cues | Use `Uncertain` if sincere and ironic interpretations both remain reasonable after context review. |
| Context contradicts literal wording | May support `Sarcasm/Irony`; record the context source in `notes`. |
| No identifiable ironic meaning | Choose `Sincere` when the comment appears to mean what it says, even if it is funny or negative. |

## 6. How to fill in the annotation sheet

**Keep the original column names generated by `01_data_collection.ipynb`:**

| Column | What to enter |
| --- | --- |
| `ID` | Pre-generated; do not edit. |
| `text` | Original comment; do not rewrite, translate, or remove emojis. |
| `video_link` | Provided source link; open when context is needed. Do not edit. |
| `label` | Select `Sincere`, `Sarcasm/Irony`, or `Uncertain`. |
| `confidence` | Select `1 - Low`, `2 - Medium`, or `3 - High`. |
| `notes` | Required for `Uncertain`, `1 - Low` confidence, use of video context, and difficult humour-versus-sarcasm decisions. For `Sarcasm/Irony`, briefly identify the ironic cue and target when they are not obvious from the comment. |

### What to record in `notes`

Use a short reason rather than a long explanation. Examples:

- `Humour only; no ironic contrast.`
- `Direct praise; no evidence of mock praise.`
- `Mock praise; target: repeated disconnections.`
- `Ironic contrast; target: the decision described in the video.`
- `Uncertain: genuine praise and mock praise both plausible.`
- `Uncertain: relevant video segment unavailable.`
- `Context used: video title/description.`
- `Context used: segment 01:20–01:40.`
- `Cultural reference not resolved.`

For `Uncertain`, state **which two readings remain plausible** or what essential information is missing. For a context-dependent decision, state what context was checked. Do not write only `not sure`, `funny`, or `ambiguous` without a brief reason.

### Confidence scale

- **`3 - High`**: The selected label is clearly supported by the comment and permitted context. For `Uncertain`, this means you are confident that both readings remain plausible or that essential evidence is unavailable.
- **`2 - Medium`**: One label is better supported, but some credible ambiguity remains. If both readings are equally plausible and cannot be resolved, choose `Uncertain`.
- **`1 - Low`**: The decision is tentative because the evidence is weak, conflicting, or incomplete. A brief explanation in `notes` is required. If no reading is reasonably favoured and both remain plausible, choose `Uncertain`.

Confidence is the annotator's subjective assessment of how well the **chosen label is supported**, not a model probability and not a measure of how funny or negative the comment sounds. It is possible to have high confidence in `Uncertain` when the evidence clearly cannot distinguish the two readings.

## 7. Independent annotation and consistency

1. Both annotators receive **identical comments, IDs, links, instructions, and available neutral context**.
2. Annotate **independently** without consulting each other or looking at the other person's labels.
3. Use **separate copies** of the workbook or Google Sheets files. Two tabs in a shared workbook do not by themselves prevent visibility of each other's labels.
4. Keep `ID` and row order intact to simplify comparison.
5. Complete and freeze the original labels **before** any comparison or adjudication.
6. For the fresh v3 validation sample, use comments that have not already been discussed or adjudicated during the earlier pilots.
7. Calculate original raw agreement and **Cohen's kappa on the three annotation choices** (`Sincere`, `Sarcasm/Irony`, and `Uncertain`), and report the number of `Uncertain` labels.
8. If either annotator leaves an item blank, do not guess the missing label. Report the number of incomplete pairs and handle those records separately from the valid paired labels used for agreement calculation.
9. If binary-only subset agreement is reported, provide its sample size and explain that `Uncertain` cases were omitted from that calculation.

## 8. Disagreement handling and final labels

- Preserve both annotators' original judgments.
- Compare and discuss disagreements **after** independent annotation is complete.
- During discussion, ask each annotator to explain the literal meaning, intended meaning, ironic cue (if any), target, and context used.
- Record one adjudicated final label separately; it must not overwrite either original label.
- If reliable interpretation remains impossible even with shared permitted context, retain `Uncertain` rather than force a binary label.
- Do **not** recalculate inter-annotator agreement using adjudicated labels; kappa measures the **original independent decisions**.

### Pilot results and implications for Version 3.0

**Pilot 2:** The 40 comments were adjudicated. Original independent agreement was **22/40 (55%)**, with three-category **Cohen's κ ≈ 0.284**. The review identified possible differences in humour-versus-sarcasm decisions and unequal familiarity with video context.

**Pilot 3:** Of 50 records, 47 had paired labels and were included in the reliability calculation. Annotators agreed on **35/47 (74.5%)**; there were 12 disagreements, and three-category **Cohen's κ ≈ 0.430**. The disagreement categories were:

- 6 `Sincere` versus `Sarcasm/Irony`;
- 5 `Sincere` versus `Uncertain`;
- 1 `Sarcasm/Irony` versus `Uncertain`.

The Pilot 3 notes fields were blank. Therefore, the label disagreements can be counted, but the annotators' exact reasons cannot be established retrospectively. The v3 note-taking requirements are intended to make those reasons reviewable in the next sample.

**Do not interpret the difference between the Pilot 2 and Pilot 3 kappa values as proof that agreement improved.** The pilots used different samples, so their results are descriptive pilot outcomes, not a controlled comparison of guideline performance.

## 9. Preparing the binary model dataset

| Adjudicated annotation | Training label |
| --- | --- |
| `Sincere` | `0` |
| `Sarcasm/Irony` | `1` |
| `Uncertain` | Exclude from the two-class training/evaluation dataset, and report how many were excluded. |

For the planned **text-only classifiers** (TF-IDF + Logistic Regression, PhoBERT, and XLM-R), do not feed `video_link` into the model. Keep source links as private annotation metadata and for qualitative error analysis.

**Potential limitation:** A comment labeled using video-specific knowledge can be ambiguous when a text-only model sees only `text`. Record context-dependent cases in `notes`, and report or analyse them separately when interpreting model errors. Do not imply that the text-only model had access to the video.

For the emoji-handling ablation, **preserve the original comment text and emojis at collection and annotation time**. Implement any emoji conversion/removal in separate experimental preprocessing, not in the annotation source.

## 10. Data handling and version control

- Store `.env` and YouTube API credentials locally only; `.gitignore` should exclude `.env`.
- Keep raw comment datasets and completed annotation sheets private, in line with the project's ethics approval and platform requirements.
- Avoid including account names or other unnecessary personal identifiers in annotation exports.
- Keep the current approved guideline at `annotation/annotation_guidelines.md`; archive earlier versions separately so that the rules used for each pilot and annotation round can be identified.
- Identify this document as **Version 3.0** in the methodology and experiment log, and record the date when it is adopted.
- Use Version 3.0 unchanged for the next independent validation sample. If further changes are necessary, create a new version and record what changed and why before using it for another sample.

### Quick decision checklist

Before submitting a label, ask:

- Did I use the **same permitted context** available to the other annotator?
- Is there actual evidence of an ironic meaning, or is the comment merely **funny, playful, negative, exaggerated, or informal**?
- If choosing `Sarcasm/Irony`, can I point to the ironic cue and identify its target or subject?
- If choosing `Uncertain`, are both sincere and ironic readings genuinely plausible, or is essential context unavailable?
- If no ironic meaning is supported, have I avoided guessing hidden sarcasm?
- Have I recorded a brief reason for `Uncertain`, low-confidence, context-dependent, or difficult humour-versus-sarcasm decisions?
- Have I preserved the original text and left both annotators' independent labels unchanged?
