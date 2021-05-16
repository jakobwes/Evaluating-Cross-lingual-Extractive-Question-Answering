# Guide to the code


The source code for this project consists of several components. It makes extensive use of the Hugginface transformers (4.7.0-dev0 at the time) datasets (1.6.2 at the time) libraries

## `QA_layer_probing_experiment.ipynb`

The main component can be found in here. This code allows Question Answering (QA)-layer-probes to be attached after specified layers, trained on [SQuAD v1.1](https://rajpurkar.github.io/SQuAD-explorer/) and evaluated on the [MLQA-dataset](https://github.com/facebookresearch/MLQA). As output the experiment code gives out a big dictionary of results, that can easily be converted to json. 

This code is essentially a "click-and-run-version" of the code explained in the notebook. The user can specify in the first two cells the layers he/she want to probe after, the MLQA-evaluation language-pairs, the Hugginface model-name to do probing on and the batch-size for training. This allows to split up the experiments between different users and only probe certain layers at a time.


## `XLM_finetune.ipynb`

This finetunes an XLM-RoBERTa-base model for QA-answering on squad v1.1 and saves it in the respective GoogleDrive (for running in GoogleColab). We have shared the finetuned model with the NLP-community [here](https://huggingface.co/jakobwes/xlm_roberta_squad_v1.1). The "Hosted inference API" on Hugginface models also provides an easy way to try out the model online.


## `finetune_specific_layers.ipynb`

This finetunes for QA only specified layers + the QA head of a given language model with the squad v1.1 dataset and evaluates on MLQA. It is a small modification of `QA_layer_probing_experiment.ipynb`


## `run_qa.py`

This is a small modification from the [QA-training-interface](https://github.com/huggingface/transformers/tree/master/examples/pytorch/question-answering) provided by Hugginface. It the layers, except for the head, of a given model, before training and deactives the very ambitious standard save-strategy (we ran into some memory issues because of that).

## `visualisations.ipynb`

This contains all the visualisation-functions used for presenting the results. It pulls the results from the GitHub-repo and creates plots. 

In addition to this code we also used a cut-out-version of `QA_layer_probing_experiment.ipynb` for only MLQA-evaluation, for example of the model trained in `XLM_finetune.ipynb`. But since this code is just a cut-out, including it here would be repetitive.


For executing the experiments we used the computing power provided with GoogleColab. Calculating the results amounted to around 40 hours of computation-time.