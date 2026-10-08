# Sarcasm and Irony Detection in Vietnamese Social Media Using Transformer-Based Models

Final Year Project — Data Science and Artificial Intelligence, British University Vietnam / University of Stirling.

## Overview

This research examines whether models can distinguish **sarcastic/ironic** Vietnamese social-media comments from **sincere** comments. Sarcasm and irony are grouped into one positive class; this project **does not** distinguish sarcasm from irony separately.

## Research objectives

1. Collect an ethically approved corpus of Vietnamese public comments from **YouTube** and permitted Vietnamese **news-site comment sections**.
2. Obtain independent annotations from **two annotators**, assess agreement with **Cohen's kappa**, and adjudicate disagreements.
3. Compare **TF-IDF + Logistic Regression** (baseline), **PhoBERT**, and **XLM-RoBERTa**.
4. Run **one ablation** comparing a standard text-only input with text plus **explicit emoji/emoticon handling**, holding other settings consistent.
5. Analyze common errors, ambiguity, and relevant Vietnamese linguistic/cultural patterns.

## Labels

| Model label | Annotation label | Description |
| --- | --- | --- |
| `0` | `SINCERE` | No clear sarcastic or ironic intent; direct praise, criticism, humor, or factual content can all be sincere. |
| `1` | `SARCASM_IRONY` | A reasonably supported sarcastic/ironic contrast, mock praise, or ironic intended meaning. |
| Not trained | `UNCERTAIN` | Insufficient context or unresolved ambiguity; used for annotation/review only. |

Both annotators label the same items independently. Raw agreement and kappa are calculated **before** resolution. See [`annotation/annotation_guidelines.md`](annotation/annotation_guidelines.md).

## Dataset and ethics

Primary sources: public YouTube comments (using the YouTube Data API) and permitted Vietnamese online news comments. Collection must comply with university ethics approval, website/API rules, and data minimization. Avoid usernames and profile URLs in modelling data. Do not publish collected comment text or identifiers unless permission and applicable terms allow it.

Private data and annotation exports are ignored by Git. The repository will contain code, documentation, and shareable aggregate metrics/figures, not raw identifiable comments.

## Models and evaluation

- Baseline: TF-IDF + Logistic Regression.
- Transformers: PhoBERT and XLM-RoBERTa, fine-tuned for binary classification.
- Primary metric: **macro F1**; also report accuracy, precision, recall, class-wise F1, and confusion matrices.
- Ablation: **standard text input** versus **explicit emoji/emoticon mapping/handling** on the selected transformer. Document exactly how the two representations differ. Do not silently remove emoji in the standard condition.
- Split data into training, validation, and held-out test sets; prevent overlap between repeated or near-duplicate comments from the same thread.

## Repository structure

```text
FYP-Vietnamese-Sarcasm/
├── README.md
├── requirements.txt
├── .gitignore
├── .env.example                # optional, no real API key
├── annotation/
│   ├── annotation_guidelines.md
│   ├── pilot_results/         # private
│   └── agreement_results/     # private
├── data/
│   ├── raw/                   # private
│   ├── cleaned/               # private
│   ├── annotated/             # private
│   └── final/                 # private
├── notebooks/
├── src/
├── models/                    # local checkpoints
├── results/
│   ├── metrics/
│   ├── figures/
│   ├── confusion_matrices/
│   └── predictions/           # private
├── demo/
└── docs/
```

## Environment setup (Windows, Miniconda)

```bash
conda create -n fyp-sarcasm python=3.11 -y
conda activate fyp-sarcasm
```

Install a compatible **CUDA-enabled PyTorch** distribution from the [official PyTorch selector](https://pytorch.org/get-started/locally/), then install project dependencies:

```bash
python -m pip install -r requirements.txt
python -m ipykernel install --user --name fyp-sarcasm --display-name "Python (FYP Sarcasm)"
```

Confirm GPU support:

```python
import torch
print(torch.__version__)
print(torch.cuda.is_available())
print(torch.cuda.get_device_name(0) if torch.cuda.is_available() else "CPU only")
```

Create a local `.env` file in the repository root for YouTube access:

```dotenv
YOUTUBE_API_KEY=YOUR_NEW_API_KEY_HERE
```

**Never commit `.env`, API keys, raw identifying data, or saved notebook outputs containing secrets.** If any API key was previously pushed, revoke it; removing a file from the current branch does not erase commit history. Use `.env.example` with a placeholder if you want to document the required setting.

## Status

- [x] Repo and folders created
- [x] Python environment and RTX 3060 CUDA tested
- [x] PhoBERT and XLM-R loading tested
- [x] Annotation guidelines revised after Pilot 1
- [x] Pilot 1 double annotation and disagreement review completed
- [ ] Pilot 2 collection and independent annotation
- [ ] Pilot 2 agreement analysis and guideline freeze
- [ ] Full approved dataset collection and labelling
- [ ] Baseline and transformer experiments
- [ ] Emoji ablation and error analysis
- [ ] Dissertation and optional simple demo

## Reproducibility

Record random seeds, train/validation/test IDs, hyperparameters, software versions, evaluation criteria, and experiment results. Keep private source data outside GitHub unless separately authorized.
