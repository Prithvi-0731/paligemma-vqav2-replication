# Paligemma-vqav2-replication

This repository contains a complete reproduction and analysis of Google DeepMind’s PaliGemma-3B model on the VQAv2 visual question answering benchmark, using the publicly released fine-tuned checkpoint.

The project includes:
• Model inference and evaluation
• Official VQA soft-accuracy metric implementation
• Replicated performance results for 224px and 448px
• Ablation studies and decoding/ prompting variants
• A fully documented notebook for reproducibility

⸻

Overview

PaliGemma-3B is a modern vision-language model achieving strong results across multiple visual reasoning tasks.
This project focuses on evaluating its performance specifically on the VQAv2 dataset.

Model checkpoint used: google/paligemma-3b-ft-vqav2-224
Dataset used: lmms-lab/VQAv2 (validation split)

⸻

Replicated Results on VQAv2

Main results:

224px resolution, 20k validation set → 92.15%
224px resolution, 2k subset → 92.82%
448px resolution, 2k subset → 93.27%

Metric used: official VQA soft-accuracy (agreement over 10 human answers).

⸻

Ablation Studies

The following controlled variations were evaluated on a 500-example subset:

Baseline greedy decoding → 93.27%
Beam search (beam = 3) → 92.73%
Prompt engineering (“Question: … Answer:”) → 93.27%
Short-answer constrained decoding → 82.40%
Sampling + majority vote (n = 3) → 92.13%
High-resolution 448px model → 93.13%
224px + 448px ensemble → 93.13%

Full ablation table available in: results/ablation_table.csv

⸻

Repository Structure

results/
• accuracy_224_val20k.txt
• accuracy_448_2k.txt
• ablation_table.csv

notebook/
• paligemma_vqav2_replication.ipynb

README.md

⸻

Environment Requirements

Evaluation was performed on a Google Colab A100 environment.

Dependencies include:
transformers, datasets, pillow, huggingface_hub, torch.

⸻

Usage

The notebook contains everything needed to run inference, compute VQA accuracy, and reproduce all figures and tables.

⸻

Notes

• All results use the official VQA evaluation metric.
• No model training was performed — this is a replication using publicly released checkpoints.
• Everything is fully reproducible with the included notebook.

⸻

Author

Prithvi Pandaala

