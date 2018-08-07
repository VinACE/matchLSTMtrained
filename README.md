# Match-LSTM

match LSTM implementation and model files
Forked from : [Match-LSTM](https://github.com/laddie132/Match-LSTM)

## Requirements

- python3
- anaconda
- hdf5
- [spaCy 2.0](https://spacy.io/)
- [pytorch 0.4](https://github.com/pytorch/pytorch/tree/v0.4.0)
- [GloVe word embeddings](https://nlp.stanford.edu/projects/glove/)

## Experiments

The Match-LSTM+ model is a little change from Match-LSTM.

- replace LSTM with GRU
- add gated-attention match like r-net
- add separated char-level encoding
- add additional features like M-Reader
- add aggregation layer with one GRU layer
- initial GRU first state in pointer-net
    - add full-connect layer after match layer

## Usage

```bash
python run.py [preprocess/train/test] [-c config_file] [-o ans_path]
```

- -c config_file: Defined dataset, model, train methods and so on. Default: `config/global_config.yaml`
- -o ans_path: *see in test step*

> there several models you can choose in `config/global_config.yaml`, like 'match-lstm', 'match-lstm+', 'r-net' and 'm-reader'. view and modify. 

### Train

```bash
python run.py train
```

### Test

```bash
python run.py test [-o ans_file]
```

- -o ans_file: Output the answer of question and context with a unique id to ans_file. 

> Note that we use `data/model-weight.pt` as our model weights by default. You can modify the config_file to set model weights file.

### Evaluate

```bash
python helper_run/evaluate-v1.1.py [dataset_file] [prediction_file]
```

- dataset_file: ground truth of dataset. example: `data/SQuAD/dev-v1.1.json`
- prediction_file: your model predict on dataset. you can use the `ans_file` from test step.

### Analysis

```bash
python helper_run/analysis_[*].py
```


## Reference

- [Wang, Shuohang, and Jing Jiang. "Machine comprehension using match-lstm and answer pointer." arXiv preprint arXiv:1608.07905 (2016).](https://arxiv.org/abs/1608.07905)
- [R-NET: MACHINE READING COMPREHENSION WITH SELF-MATCHING NETWORKS](https://www.microsoft.com/en-us/research/wp-content/uploads/2017/05/r-net.pdf)
- [Hu, Minghao, Yuxing Peng, and Xipeng Qiu. "Reinforced mnemonic reader for machine comprehension." CoRR, abs/1705.02798 (2017).](https://arxiv.org/abs/1705.02798)

## License

[MIT](https://github.com/laddie132/MRC-PyTorch/blob/master/LICENSE)

