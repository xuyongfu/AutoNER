# AutoNER: Learning Named Entity Tagger using Domain-Specific Dictionary


[![Documentation Status](https://readthedocs.org/projects/autoner/badge/?version=latest)](http://autoner.readthedocs.io/en/latest/?badge=latest)
![AutoNER-Framework](docs/AutoNER-Framework.png)

## Publications

Please cite the following two papers if you are using our tool. Thanks!

- Jingbo Shang*, Liyuan Liu*, Xiaotao Gu, Xiang Ren, Teng Ren and Jiawei Han, "Learning Named Entity Tagger using Domain-Specific Dictionary", in Proc. of 2018 Conf. on Empirical Methods in Natural Language Processing (EMNLP'18), Brussels, Belgium, Oct. 2018. (* Equal Contribution)
- Jingbo Shang, Jialu Liu, Meng Jiang, Xiang Ren, Clare R Voss, Jiawei Han, "**[Automated Phrase Mining from Massive Text Corpora](https://arxiv.org/abs/1702.04457)**", accepted by IEEE Transactions on Knowledge and Data Engineering, Feb. 2018.


## Required Inputs

- **Tokenized Raw Texts**
  - Example: ```data/BC5CDR/raw_text.txt```
    - One token per line.
    - An empty line means the end of a sentence.
- **Two Dictionaries**
  - **Core Dictionary w/ Type Info**
    - Example: ```data/BC5CDR/dict_core.txt```
      - Two columns (i.e., Type, Tokenized Surface) per line.
      - Tab separated.
    - How to obtain?
      - From domain-specific dictionaries.
  - **Full Dictionary w/o Type Info**
    - Example: ```data/BC5CDR/dict_full.txt```
      - One tokenized high-quality phrases per line.
    - How to obtain? 
      - From domain-specific dictionaries.
      - Applying the high-quality phrase mining tool on domain-specific corpus.
        - [AutoPhrase](https://github.com/shangjingbo1226/AutoPhrase) 
- **Pre-trained word embeddings**
  - Train your own or download from the web.
  - The example run uses ```embedding/bio_embedding.txt```, which can be downloaded from [our group's server](http://dmserv4.cs.illinois.edu/bio_embedding.txt)
- **[Optional]** Development & Test Sets.
  - Example: ```data/BC5CDR/truth_dev.ck``` and ```data/BC5CDR/truth_test.ck```
    - Three columns (i.e., token, ```Tie or Break``` label, entity type).
    - ```I``` is ```Berak```.
    - ```O``` is ```Tie```.
    - Two special tokens ```<s>``` and ```<eof>``` mean the start and end of the sentence.

## Dependencies

The dependent package for this project is listed as below:
```
numpy==1.13.1
tqdm
torch-scope
pytorch==0.4.1
```

## Command

To train an AutoNER model, please run
```
./autoner_train.sh
```

To apply the trained AutoNER model, please run
```
./autoner_test.sh
```

You can specify the parameters in the bash files. The variables names are self-explained.
