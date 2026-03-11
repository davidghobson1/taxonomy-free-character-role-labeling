# Evaluating Taxonomy Free Character Role Labeling (TF-CRL) in News Stories using Large Language Models

This repository is the official implementation of [Evaluating Taxonomy Free Character Role Labeling (TF-CRL) in News Stories using Large Language Models](https://aclanthology.org/2025.emnlp-main.750/).

It contains the data, codebooks, prompts, and code used in the paper, including materials needed to reproduce our results.

## Overview

**Taxonomy Free Character Role Labeling (TF-CRL)** is a method for characterizing how people and entities are portrayed in news. It assigns an open-ended narrative role labels to characters based on their functional role in the narrative.

## Repo Structure

```
.
├── code/
│   ├── Application.ipynb           # Reproduce Application results
│   └── Label Clustering.ipynb      # Label clustering code
│
├── codebooks/
│   ├── Annotation Guide - Character Role Labeling.pdf          # Human annotation guide
│   ├── AMT_annotation_guide_character_label_assessment.html    # MTurk template (validation)
│   └── AMT_annotation_guide_prompt_selection.html              # MTurk template (prompt selection)
│
├── data/
│   ├── application/                # Data for the Application section
│   │   ├── character_labels_data/  # Per-narrative LLM-labeled character data
│   │   ├── clustered_labels.csv    # Clustered labels across all five narrative domains
│   │   └── character_name_equivalencies.json   # Name standardization mapping
│   │
│   ├── validation/                 # Validation section data
│   │   ├── label_annotations/      # Human and LLM labels for validation texts
│   │   ├── mturk/                  # MTurk validation results
│   │   └── validation_dataset.csv  # Validation texts
│   │
│   └── prompt_selection/           # Prompt Selection section data
│       ├── label_annotations/      # LLM labels under different prompting strategies
│       ├── mturk/                  # MTurk prompt selection results
│       └── prompt_selection_dataset.csv
│
├── outputs/                        # Generated figures and visualizations
│
├── prompts/
│   ├── prompt_tf-crl.txt                    # Main TF-CRL labeling prompt
│   ├── prompt_character_identification.txt  # Character extraction prompt
│   ├── prompt_hvv_classification.txt        # Hero/Villain/Victim classification prompt
│   └── prompt_selection/                    # Prompts for the prompt selection experiments
│       ├── concept_induction/
│       └── char_summ/
│
└── README.md
```

## Getting Started

### 1) Anaconda

```bash
conda create -n tf-crl python=3.10
conda activate tf-crl
conda install -c conda-forge pip
python -m pip install -r requirements.txt
```

### 2) Virtual Environment

```bash
python -m venv tf-crl
source tf-crl/bin/activate
python -m pip install -r requirements.txt
```

## Running the Code

Notebook code in `Application.ipynb` runs as-is using the data in this repo. Note that because of licencing with the Media Frames Corpus, the Immigration, Climate, and SSM datasets are not provided in this repo, and therefore the `Label Clustering.ipynb` notebook will not produce identical results as in the paper. The `cluster_labels.csv` file however provides the labels from all the data used in our paper.

## Prompts

The `/prompts` directory contains the LLM prompt templates used in the paper:

| Prompt | Description |
|---|---|
| `prompt_tf-crl.txt` | Generates open-ended noun phrase role labels for each character |
| `prompt_character_identification.txt` | Identifies the central characters in a news narrative |
| `prompt_hvv_classification.txt` | Classifies each character as Hero, Villain, Victim, or Neither |
| `prompt_selection/concept_induction/` | Two-step prompting: extract quotes, then summarize portrayals |
| `prompt_selection/char_summ/` | Single-step character portrayal summarization |

## Citation

If you use this work, please cite:

```
@inproceedings{hobson2025evaluating,
  title={Evaluating Taxonomy Free Character Role Labeling (TF-CRL) in News Stories using Large Language Models},
  author={Hobson, David G and Ruths, Derek and Piper, Andrew},
  booktitle={Proceedings of the 2025 Conference on Empirical Methods in Natural Language Processing},
  pages={14828--14850},
  year={2025}
}
```
