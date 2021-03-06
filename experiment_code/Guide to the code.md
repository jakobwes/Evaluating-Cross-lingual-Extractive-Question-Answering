# Guide to the code


The source code for this project consists of several components. It makes extensive use of the Hugginface transformers (4.7.0-dev0 at the time) datasets (1.6.2 at the time) libraries

## `QA_layer_probing_experiment.ipynb`

The main component can be found in here. This code allows Question Answering (QA)-layer-probes to be attached after specified layers, trained on [SQuAD v1.1](https://rajpurkar.github.io/SQuAD-explorer/) and evaluated on the [MLQA-dataset](https://github.com/facebookresearch/MLQA). As output the experiment code gives out a big dictionary of results, that can easily be converted to json. 

The user can specify in the first two cells the layers he/she want to probe after, the MLQA-evaluation language-pairs, the Hugginface model-name to do probing on and the batch-size for training. This allows to split up the experiments between different users and only probe certain layers at a time. Afterwards the code runs the training of the probes, whilst freezing the other layers, using the `run_qa.py`, and evaluates on MLQA for each specified language-pair.


## `XLM_finetune.ipynb`

This finetunes an XLM-RoBERTa-base model for QA-answering on squad v1.1 and saves it in the respective GoogleDrive (for running in GoogleColab). We have shared the finetuned model with the NLP-community [here](https://huggingface.co/jakobwes/xlm_roberta_squad_v1.1). The "Hosted inference API" on Hugginface models also provides an easy way to try out the model online.


## `finetune_specific_layers.ipynb`

This finetunes only specified layers + a QA head of a given language model, using the squad v1.1 dataset and evaluating on MLQA. It is a small modification of `QA_layer_probing_experiment.ipynb`


## `run_qa.py`

This is a small modification from the [QA-training-interface](https://github.com/huggingface/transformers/tree/master/examples/pytorch/question-answering) provided by Hugginface. It does the training for QA. In addition we implemented, that before training it freezes the layers, except for the head, of a given model (see line 546). Also in addition it deactives the very ambitious standard save-strategy (we ran into some memory issues because of that: import in line 43 and line 407). It is used by `QA_layer_probing_experiment.ipynb`.


## `visualisations.ipynb`

This contains all the visualisation-functions used for presenting the results. It pulls the results from the GitHub-repo and creates plots. 

In addition to this code we also used a cut-out-version of `QA_layer_probing_experiment.ipynb` for only MLQA-evaluation, for example of the model trained in `XLM_finetune.ipynb`. But since this code is just a cut-out, including it here would be repetitive.


For executing the experiments we used the computing power provided with GoogleColab. Calculating the results amounted to around 40 hours of computation-time.