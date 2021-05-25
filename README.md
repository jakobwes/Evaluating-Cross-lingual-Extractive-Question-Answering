# Evaluating Cross-lingual Extractive Question Answering

This is the GitHub-repo for the project "Evaluating Cross-lingual Extractive Question Answering". From the abstract of the main report:

The standard research in multilingual models usually explores the changes in performance when fine-tuning for specific tasks by probing entire language models. This project digs deep into language model architecture and compares the learning that occurs within layers of two different multilingual models (mBERT and XLM) when tasked to perform Question Answering (QA). The authors probe with a QA-task across the twelve different layers and examine where improvements in performance occur when evaluated on different languages. The authors conclude that QA-abilites seem to congregate in some of the middle-layers and that learning for QA occurs very similarly across multiple languages.

## Some relevant links: 
- The [main report](https://github.com/jakobwes/QA_layer_freeze/blob/main/report.pdf).
- A [demo notebook](https://github.com/jakobwes/QA_layer_freeze/blob/main/demo_notebook.ipynb) showcasing the results.
- The [code used for the experiments](https://github.com/jakobwes/QA_layer_freeze/tree/main/experiment_code) including a [Guide to the code](https://github.com/jakobwes/QA_layer_freeze/blob/main/experiment_code/Guide%20to%20the%20code.md) for anyone interested in replicating them.
- The [results-data](https://github.com/jakobwes/QA_layer_freeze/tree/main/results).
