# Word2Vec Training and Emotion Classification using GloVe 

## Overview
GoEmotions NLP project comparing custom Word2Vec embeddings, pretrained GloVe, Dense/CNN classifiers, and TF-IDF baselines. Includes multi-label classification and embedding/error analysis.

![Emotion class distribution](graphs/01_class_distribution.png)

## Setup
Install dependencies using `pip install -r requirements.txt`. Place `go_emotions_dataset.csv` in the configured project directory (not inside the submission ZIP). Run `run_project.py` or `notebook.ipynb`. The script downloads Stanford GloVe if no local copy exists; this large asset is intentionally excluded from the ZIP.

## Results
All figures, CSVs, models, and reports are saved locally in `results/`, not submitted.

## Important limitations
The GoEmotions fallback corpus is not an independent domain-specific corpus. External WordSim-353/SimLex-999 benchmarking and 300d GloVe experiments are not implemented.
