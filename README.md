# SPRL-Spacy

This repository implements an easy to use Spatial Role Labeling module trained on
three entities (`TRAJECTOR`, `SPATIAL_INDICATOR`, `LANDMARK`) and the relations appearing
on the SpRL 2013 IAPR TC-12 dataset. 

## Requirements

- `spacy >=2.0.0a18` and the necessary requirements
- `sklearn`
- `scipy`
- `pickle` for python 3.7.0
- `problog` for use with ProbLog.

## Usage

1. Clone this repository where you want to use it. 
2. Download the two models from the [releases](https://github.com/mmxgn/sprl-spacy/releases) page
3. Import `spacy` and `sprl` and use them like the following example:


```
import spacy
from sprl import *

nlp = spacy.load('en_core_web_lg-sprl')

sentence = "An angry big dog is behind us."

rel = sprl(sentence, nlp)
```

If everything went fine you should get something like:

```
[(An angry big dog, behind, us, 'direction')]
```

If you happen to have problog installed, you can see `example.pl` on how to use it from
within problog. **Note:** If you want to use it from within problog you need to append the `sprl` directory to `PYTHONPATH`, e.g:

```
$ PYTHONPATH=sprl problog example.pl
```

## Credits

While the model has been trained by me, the relation extraction part uses features from
the paper for Sprl-CWW (see below), and the dataset from SemEval 2013 Task 3: Spatial Role Labeling.

The features for relation extraction:

```
Nichols, Eric, and Fadi Botros. 
"SpRL-CWW: Spatial relation classification with independent multi-class models." 
Proceedings of the 9th International Workshop on Semantic Evaluation.
```

Semeval 2013 task 3: Spatial Role Labeling

```
Kolomiyets, Oleksandr, et al. 
"Semeval-2013 task 3: Spatial role labeling." 
Second Joint Conference on Lexical and Computational Semantics
```

So please cite the papers above, as well as spacy and ProbLog (if you use it) in your work :)


